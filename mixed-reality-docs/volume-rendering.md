---
title: Representación de volumen
description: Las imágenes volumétricas contienen información enriquecida con opacidad y color en todo el volumen que no se puede expresar fácilmente como superficies. Aprenda a representar eficazmente imágenes volumétricas en Windows Mixed Reality.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagen volumétrica, representación por volumen, rendimiento, realidad mixta
ms.openlocfilehash: 6dbb49c31761d4b7b9da5060d15763c3925be754
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277953"
---
# <a name="volume-rendering"></a>Representación de volumen

En el caso de los volúmenes de resonancia médica o de ingeniería, consulte [representación de volumen en Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering). Estas ' imágenes volumétricas ' contienen información enriquecida con opacidad y color en todo el volumen que no se puede expresar fácilmente como superficies como [mallas poligonales](https://en.wikipedia.org/wiki/Polygon_mesh).

Soluciones clave para mejorar el rendimiento
1. BAD: Naive enfoque: Mostrar todo el volumen; por lo general, se ejecuta demasiado lentamente.
2. BUENA: plano de corte: mostrar solo un segmento del volumen
3. BUENO: recortar el Subvolumen: mostrar solo algunas capas del volumen
4. BUENA: reducir la resolución de la representación de volumen (consulte "representación de escenas de resolución mixta")

Solo hay una cierta cantidad de información que se puede transferir desde la aplicación a la pantalla en cualquier fotograma determinado, que es el ancho de banda total de la memoria. Además, cualquier procesamiento (o ' sombreado ') necesario para transformar los datos para la presentación requiere tiempo. Las principales consideraciones a la hora de realizar la representación de volúmenes son las siguientes:
* Screen-width * Screen-height * Screen-Count * Volume-Layers-on-pixel = total-Volume-samples-per-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100%) (volumen de res completo: demasiados ejemplos)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% de Full) (segmento fino: 1 muestra por píxel, se ejecuta sin problemas)
* 1028 * 720 * 2 * 10 = 14803200 (3,9% de Full) (segmento de Subvolumen: 10 muestras por píxel, se ejecuta con bastante suavidad, parece 3D)
* 200 * 200 * 2 * 256 = 20480000 (5% de Full) (volumen de res inferior: menos píxeles, volumen completo, apariencia 3D pero un poco borroso)

## <a name="representing-3d-textures"></a>Representar texturas 3D

En la CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

En la GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Sombreado y degradados

Cómo sombrear un volumen, como resonancia magnética, para una visualización útil. El método principal consiste en tener una ' ventana de intensidad ' (un mínimo y un máximo) en el que desea ver las intensidades y, simplemente, escalar en ese espacio para ver la intensidad de blanco y negro. A continuación, se puede aplicar una "rampa de color" a los valores dentro de ese intervalo y almacenarse como una textura, de modo que las distintas partes del espectro de intensidad pueden sombrear diferentes colores:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

En muchas de nuestras aplicaciones, almacenamos en nuestro volumen un valor de intensidad sin procesar y un "índice de segmentación" (para segmentar partes diferentes, como la piel y el hueso; estos segmentos suelen ser creados por expertos en herramientas dedicadas). Se puede combinar con el enfoque anterior para colocar un color diferente o incluso una rampa de color diferente para cada índice de segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Segmentación de volumen en un sombreador

Un primer paso es crear un "plano de segmentación" que pueda desplazarse por el volumen, ' segmentarlo ' y cómo examinar los valores en cada punto. Se supone que hay un cubo "VolumeSpace", que representa el lugar en el que el volumen está en el espacio universal, que se puede usar como referencia para colocar los puntos:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Seguimiento de volumen en sombreadores

Cómo usar la GPU para realizar el seguimiento de subvolumens (recorra unos pocos voxels y, a continuación, capas en los datos de vuelta al frente):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Representación de todo el volumen

Al modificar el código del Subvolumen anterior, obtenemos lo siguiente:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Representación de escenas de resolución mixta

Cómo representar una parte de la escena con una resolución baja y volver a colocarla en su lugar:
1. Configuración de dos cámaras fuera de pantalla, una para cada ojo que actualice cada fotograma
2. Configuración de dos destinos de representación de baja resolución (es decir, 200 x 200 cada uno) que las cámaras representan en
3. Configurar un cuádruple que se mueva delante del usuario

Cada fotograma:
1. Dibuje los objetivos de representación de cada ojo a baja resolución (datos de volumen, sombreadores costosos, etc.).
2. Dibuje la escena normalmente como resolución completa (mallas, interfaz de usuario, etc.).
3. Dibuje un cuádruple delante del usuario, a través de la escena, y el proyecto de las representaciones de baja res en ese
4. Resultado: combinación visual de elementos de resolución completa con datos de volumen de baja resolución pero de alta densidad
