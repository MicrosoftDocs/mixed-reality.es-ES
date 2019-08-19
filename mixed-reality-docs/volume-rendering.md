---
title: Representación de volumen
description: Las imágenes volumétricas contienen información enriquecida con opacidad y color en todo el volumen que no se puede expresar fácilmente como superficies. Aprenda a representar eficazmente imágenes volumétricas en Windows Mixed Reality.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: imagen volumétrica, representación por volumen, rendimiento, realidad mixta
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548632"
---
# <a name="volume-rendering"></a><span data-ttu-id="f4500-105">Representación de volumen</span><span class="sxs-lookup"><span data-stu-id="f4500-105">Volume rendering</span></span>

<span data-ttu-id="f4500-106">En el caso de los volúmenes de resonancia médica o de ingeniería, consulte [representación de volumen en Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="f4500-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="f4500-107">Estas ' imágenes volumétricas ' contienen información enriquecida con opacidad y color en todo el volumen que no se puede expresar fácilmente como superficies como [mallas poligonales](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="f4500-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="f4500-108">Soluciones clave para mejorar el rendimiento</span><span class="sxs-lookup"><span data-stu-id="f4500-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="f4500-109">N Enfoque Naive: Mostrar todo el volumen, normalmente se ejecuta demasiado lentamente</span><span class="sxs-lookup"><span data-stu-id="f4500-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="f4500-110">APROPIADO Plano de corte: Mostrar solo un único segmento del volumen</span><span class="sxs-lookup"><span data-stu-id="f4500-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="f4500-111">APROPIADO Corte del Subvolumen: Mostrar solo algunas capas del volumen</span><span class="sxs-lookup"><span data-stu-id="f4500-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="f4500-112">APROPIADO Disminución de la resolución de la representación de volumen (consulte "representación de escenas de resolución mixta")</span><span class="sxs-lookup"><span data-stu-id="f4500-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="f4500-113">Solo hay una cierta cantidad de información que se puede transferir desde la aplicación a la pantalla en cualquier fotograma determinado, es el ancho de banda total de la memoria.</span><span class="sxs-lookup"><span data-stu-id="f4500-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="f4500-114">Además, cualquier procesamiento (o ' sombreado ') necesario para transformar los datos para la presentación también requiere tiempo.</span><span class="sxs-lookup"><span data-stu-id="f4500-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="f4500-115">Las principales consideraciones a la hora de realizar la representación de volúmenes son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="f4500-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="f4500-116">Screen-width \* Screen-height \* Screen-Count \* Volume-Layers-on-pixel = total-Volume-samples-per-Frame</span><span class="sxs-lookup"><span data-stu-id="f4500-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="f4500-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (volumen de res completo: demasiados ejemplos)</span><span class="sxs-lookup"><span data-stu-id="f4500-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="f4500-118">1028 \* 720 \* 2 \* 1 = 1480320 (0,3% de Full) (segmento fino: 1 muestra por píxel y se ejecuta sin problemas)</span><span class="sxs-lookup"><span data-stu-id="f4500-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="f4500-119">1028 \* 720 \* 2 \* 10 = 14803200 (3,9% de Full) (segmento de Subvolumen: 10 muestras por píxel, se ejecuta de forma bastante fluida, parece 3D)</span><span class="sxs-lookup"><span data-stu-id="f4500-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="f4500-120">200 \* 200 \* 2 \* 256 = 20480000 (5% de Full) (volumen de res inferior: menos píxeles, volumen completo, apariencia 3D pero un poco desenfoque)</span><span class="sxs-lookup"><span data-stu-id="f4500-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="f4500-121">Representar texturas 3D</span><span class="sxs-lookup"><span data-stu-id="f4500-121">Representing 3D Textures</span></span>

<span data-ttu-id="f4500-122">En la CPU:</span><span class="sxs-lookup"><span data-stu-id="f4500-122">On the CPU:</span></span>

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

<span data-ttu-id="f4500-123">En la GPU:</span><span class="sxs-lookup"><span data-stu-id="f4500-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="f4500-124">Sombreado y degradados</span><span class="sxs-lookup"><span data-stu-id="f4500-124">Shading and Gradients</span></span>

<span data-ttu-id="f4500-125">Cómo sombrear un volumen, como resonancia magnética, para una visualización útil.</span><span class="sxs-lookup"><span data-stu-id="f4500-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="f4500-126">El método principal consiste en tener una ' ventana de intensidad ' (un mínimo y un máximo) en el que desea ver las intensidades y, simplemente, escalar en ese espacio para ver la intensidad de blanco y negro.</span><span class="sxs-lookup"><span data-stu-id="f4500-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="f4500-127">A continuación, se puede aplicar una "rampa de color" a los valores dentro de ese intervalo y almacenarse como una textura, de modo que las distintas partes del espectro de intensidad pueden sombrear diferentes colores:</span><span class="sxs-lookup"><span data-stu-id="f4500-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="f4500-128">En muchas de nuestras aplicaciones almacenamos en nuestro volumen un valor de intensidad sin procesar y un "índice de segmentación" (para segmentar partes diferentes, como la piel y el hueso, estos segmentos suelen ser creados por expertos en herramientas dedicadas).</span><span class="sxs-lookup"><span data-stu-id="f4500-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="f4500-129">Se puede combinar con el enfoque anterior para colocar un color diferente o incluso una rampa de color diferente para cada índice de segmento:</span><span class="sxs-lookup"><span data-stu-id="f4500-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="f4500-130">Segmentación de volumen en un sombreador</span><span class="sxs-lookup"><span data-stu-id="f4500-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="f4500-131">Un primer paso es crear un "plano de segmentación" que pueda desplazarse por el volumen, ' segmentarlo ' y cómo examinar los valores en cada punto.</span><span class="sxs-lookup"><span data-stu-id="f4500-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="f4500-132">Se supone que hay un cubo "VolumeSpace", que representa el lugar en el que el volumen está en el espacio universal, que se puede usar como referencia para colocar los puntos:</span><span class="sxs-lookup"><span data-stu-id="f4500-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="f4500-133">Seguimiento de volumen en sombreadores</span><span class="sxs-lookup"><span data-stu-id="f4500-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="f4500-134">Cómo usar la GPU para realizar el seguimiento de subvolumens (recorre unos cuantos voxelss en profundidad en los datos de vuelta al frente):</span><span class="sxs-lookup"><span data-stu-id="f4500-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="f4500-135">Representación de todo el volumen</span><span class="sxs-lookup"><span data-stu-id="f4500-135">Whole Volume Rendering</span></span>

<span data-ttu-id="f4500-136">La modificación del código del Subvolumen anterior se obtiene:</span><span class="sxs-lookup"><span data-stu-id="f4500-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="f4500-137">Representación de escenas de resolución mixta</span><span class="sxs-lookup"><span data-stu-id="f4500-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="f4500-138">Cómo representar una parte de la escena con una resolución baja y volver a colocarla en su lugar:</span><span class="sxs-lookup"><span data-stu-id="f4500-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="f4500-139">Configuración de dos cámaras fuera de pantalla, una para cada ojo que actualice cada fotograma</span><span class="sxs-lookup"><span data-stu-id="f4500-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="f4500-140">Configurar dos destinos de representación de baja resolución (por ejemplo, 200 x 200), que las cámaras representan en</span><span class="sxs-lookup"><span data-stu-id="f4500-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="f4500-141">Configurar un cuádruple que se mueva delante del usuario</span><span class="sxs-lookup"><span data-stu-id="f4500-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="f4500-142">Cada fotograma:</span><span class="sxs-lookup"><span data-stu-id="f4500-142">Each Frame:</span></span>
1. <span data-ttu-id="f4500-143">Dibuje los objetivos de representación de cada ojo a baja resolución (datos de volumen, sombreadores costosos, etc.).</span><span class="sxs-lookup"><span data-stu-id="f4500-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="f4500-144">Dibuje la escena normalmente como resolución completa (mallas, interfaz de usuario, etc.).</span><span class="sxs-lookup"><span data-stu-id="f4500-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="f4500-145">Dibuje un cuádruple delante del usuario, a través de la escena, y el proyecto de las representaciones de baja resolución.</span><span class="sxs-lookup"><span data-stu-id="f4500-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="f4500-146">Resultado: combinación visual de elementos de resolución completa con datos de volumen de baja resolución pero de alta densidad.</span><span class="sxs-lookup"><span data-stu-id="f4500-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
