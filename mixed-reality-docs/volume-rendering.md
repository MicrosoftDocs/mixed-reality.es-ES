---
title: Representación de volumen
description: Imágenes volumétricas contienen información enriquecida con opacidad y el color en todo el volumen que no se pueden expresar fácilmente como superficies. Obtenga información sobre cómo representar eficazmente volumétricas imágenes dentro de Windows Mixed Reality.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagen volumétrico, representación de volumen, rendimiento, la realidad mixta
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605577"
---
# <a name="volume-rendering"></a>Representación de volumen

RM médica o volúmenes de ingeniería, consulte [volumen de representación en Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering). Estas imágenes volumétricas contienen información enriquecida con opacidad y el color en todo el volumen que no se pueden expresar como superficies como [mallas poligonales](https://en.wikipedia.org/wiki/Polygon_mesh).

Soluciones de claves para mejorar el rendimiento
1. ERRÓNEO: Enfoque ingenuo que: Mostrar todo el volumen, por lo general se ejecuta muy lentamente
2. BIEN: Plano de corte: Mostrar solo un único segmento del volumen
3. BIEN: Corte volumen secundario: Mostrar solo unas pocas capas del volumen
4. BIEN: Disminuir la resolución de la representación de volumen (vea 'Mixto representación de escenas de resolución')

Hay sólo una cierta cantidad de información que se puede transferir desde la aplicación en la pantalla en cualquier marco concreto, esto es el ancho de banda total de memoria. También cualquier procesamiento (o 'sombreado') necesarios para transformar los datos para la presentación también requiere tiempo. Las consideraciones principales cuando se realiza la representación de volumen son como tal:
* Ancho de pantalla * alto de pantalla * número de pantalla * volumen capas-de-que-píxel = Total de ejemplos de volumen por fotograma
* 1028 * 720 * 2 * 256 = 378961920 (100%) (res volúmenes completos: demasiados ejemplos)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% de completo) (fino segmento: 1 ejemplo por píxel, se ejecuta sin problemas)
* 1028 * 720 * 2 * 10 = 14803200 (3.9% del total) (segmento subcarpetas del volumen: 10 muestras por píxel, se ejecuta sin problemas, busca 3d)
* 200 * 200 * 2 * 256 = 20480000 (5% del total) (reducir el volumen de res: menos píxeles, de volúmenes completos, busca blury 3d, pero un poco)

## <a name="representing-3d-textures"></a>Que representa las texturas 3D

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

Cómo sombrear un volumen, por ejemplo, RM, para la visualización útil. El método principal es que una ventana del intensidad (min y max) que desea ver intensidades dentro y simplemente escale en dicho espacio para ver la intensidad en blanco y negro. Un degradado se aplica a los valores dentro de ese intervalo y almacenar como una textura, para que las distintas partes del espectro de intensidad pueda sombreados colores diferentes:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

En muchos nuestras aplicaciones se almacenan en nuestro volumen de un valor de intensidad sin formato y un índice de segmentación' ' (para segmentar las distintas partes, como la máscara y ósea, estos segmentos son generalmente creados por expertos en existen herramientas dedicadas). Esto se puede combinar con el enfoque anterior para colocar un color diferente o vía rápida de color incluso diferente para cada índice del segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Segmentación de un sombreador de volumen

Un magnífico primer paso es crear un "plano segmentación" que puede desplazarse por el volumen, 'segmentación', y cómo el examen de los valores en cada momento. Esto supone que hay un cubo 'VolumeSpace', que representa dónde es el volumen en el espacio global, que puede usarse como referencia para colocar los puntos:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Volumen de seguimientos en los sombreadores

Cómo usar la GPU para realizar el seguimiento volumen secundario (recorre voxels unos niveles de profundidad, a continuación, en los datos desde atrás al frente):

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

Modificar el código de volumen secundario anterior que obtenemos:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Representación de escenas resolución mixto

Cómo representar una parte de la escena con una resolución baja y vuelva a colocarlo en su lugar:
1. Configurar dos cámaras fuera de la pantalla, uno para seguir cada ojo que actualizar cada fotograma
2. Programa de instalación de baja resolución dos objetivos de presentación (por ejemplo 200 x 200 cada), que representan las cámaras en
3. Configurar un cuadrado que mueve delante del usuario

Cada fotograma:
1. Dibuje los objetivos de representación para todos los ojos en baja resolución (volúmenes de datos, sombreadores costosos, etcetera.)
2. Dibujar la escena normalmente como resolución completa (mallas, interfaz de usuario, etcetera.)
3. Dibujar un cuadrado delante del usuario, a través de la escena y proyectar los baja resolución se representan en el.
4. Resultado: combinación visual de elementos de alta resolución con datos del volumen de baja resolución pero alta densidad.
