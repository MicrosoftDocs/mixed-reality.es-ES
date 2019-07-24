---
title: 'Caso práctico: escalado de Datascape entre dispositivos con un rendimiento diferente'
description: En este caso práctico se ofrece información sobre cómo los desarrolladores de Microsoft optimizaron la aplicación Datascape para ofrecer una experiencia atractiva en todos los dispositivos con una variedad de capacidades de rendimiento.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: auriculares inmersivo, optimización del rendimiento, VR, caso práctico
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523401"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="74748-104">Caso práctico: escalado de Datascape entre dispositivos con un rendimiento diferente</span><span class="sxs-lookup"><span data-stu-id="74748-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="74748-105">Datascape es una aplicación de Windows Mixed Reality desarrollada internamente en Microsoft donde nos centramos en mostrar los datos meteorológicos sobre los datos de terreno.</span><span class="sxs-lookup"><span data-stu-id="74748-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="74748-106">La aplicación explora la información única que los usuarios obtienen de la detección de datos en realidad mixta rodeando al usuario con la visualización de datos holográfica.</span><span class="sxs-lookup"><span data-stu-id="74748-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="74748-107">En el caso de Datascape, queríamos tener como destino una gran variedad de plataformas con distintas capacidades de hardware que abarcan desde Microsoft HoloLens hasta auriculares mixtos de Windows Mixed Reality y desde equipos con una versión más reciente a los equipos más recientes con GPU de alto nivel.</span><span class="sxs-lookup"><span data-stu-id="74748-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="74748-108">El principal desafío era representar nuestra escena en una cuestión visualmente atractiva en los dispositivos con funcionalidades de gráficos extremadamente diferentes mientras se ejecutaba en una velocidad de fotogramas.</span><span class="sxs-lookup"><span data-stu-id="74748-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="74748-109">Este caso práctico le guiará a través del proceso y las técnicas que se usan para crear algunos de nuestros sistemas más intensivos de GPU, donde se describen los problemas que se han encontrado y cómo se superaron.</span><span class="sxs-lookup"><span data-stu-id="74748-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="74748-110">Transparencia y desdibujando</span><span class="sxs-lookup"><span data-stu-id="74748-110">Transparency and overdraw</span></span>

<span data-ttu-id="74748-111">Nuestra representación principal se enfrenta a la transparencia, ya que la transparencia puede ser costosa en una GPU.</span><span class="sxs-lookup"><span data-stu-id="74748-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="74748-112">La geometría sólida se puede representar de delante a vuelta mientras se escribe en el búfer de profundidad, lo que detiene los píxeles futuros situados detrás de ese píxel para que no se descarten.</span><span class="sxs-lookup"><span data-stu-id="74748-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="74748-113">Esto evita que los píxeles ocultos ejecuten el sombreador de píxeles, lo que acelera considerablemente el proceso.</span><span class="sxs-lookup"><span data-stu-id="74748-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="74748-114">Si Geometry se ordena de forma óptima, cada píxel de la pantalla se dibujará una sola vez.</span><span class="sxs-lookup"><span data-stu-id="74748-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="74748-115">La geometría transparente debe estar ordenada de nuevo al frente y se basa en la mezcla de la salida del sombreador de píxeles con el píxel actual de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="74748-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="74748-116">Esto puede hacer que cada píxel de la pantalla se dibuje varias veces por fotograma, lo que se conoce como sobredibujo.</span><span class="sxs-lookup"><span data-stu-id="74748-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="74748-117">En el caso de los equipos de HoloLens y estándar, la pantalla solo se puede rellenar unas cuantas veces, lo que hace problemáticas la representación transparente.</span><span class="sxs-lookup"><span data-stu-id="74748-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="74748-118">Introducción a los componentes de Datascape Scene</span><span class="sxs-lookup"><span data-stu-id="74748-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="74748-119">Tenemos tres componentes principales en nuestra escena; **la interfaz de usuario, la asignación**y **el tiempo**.</span><span class="sxs-lookup"><span data-stu-id="74748-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="74748-120">Sabíamos pronto que nuestros efectos meteorológicos requerirían todo el tiempo de la GPU que podía obtener, por lo que hemos diseñado específicamente la interfaz de usuario y el terreno de una manera que reduciría cualquier posible desdibujo.</span><span class="sxs-lookup"><span data-stu-id="74748-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="74748-121">La interfaz de usuario se reutiliza varias veces para minimizar la cantidad de sobredibujo que produciría.</span><span class="sxs-lookup"><span data-stu-id="74748-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="74748-122">Nos sentimos en el lateral de geometría más compleja en lugar de superponer un arte transparente encima de otro para componentes como los botones de resplandor y la información general sobre mapas.</span><span class="sxs-lookup"><span data-stu-id="74748-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="74748-123">En el mapa, usamos un sombreador personalizado que descartaría las características estándar de Unity, como sombras e iluminación compleja, y las reemplaza por un modelo simple de iluminación de sol sencillo y un cálculo de niebla personalizado.</span><span class="sxs-lookup"><span data-stu-id="74748-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="74748-124">Esto produjo un sombreador de píxeles simple y libera ciclos de GPU.</span><span class="sxs-lookup"><span data-stu-id="74748-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="74748-125">Nos hemos administrado para obtener tanto la interfaz de usuario como el mapa que se va a representar en el presupuesto en el que no necesitábamos realizar ningún cambio en función del hardware. sin embargo, la visualización meteorológica, en particular la representación en la nube, demostró ser más difícil.</span><span class="sxs-lookup"><span data-stu-id="74748-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="74748-126">Información general sobre los datos en la nube</span><span class="sxs-lookup"><span data-stu-id="74748-126">Background on cloud data</span></span>

<span data-ttu-id="74748-127">Nuestros datos en la nube se han descargado de los servidores de NOAA (http://nomads.ncep.noaa.gov/) y nos venían en tres capas 2D distintas, cada una con la altura superior e inferior de la nube, así como la densidad de la nube para cada celda de la cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="74748-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="74748-128">Los datos se procesaron en una textura de información de la nube donde cada componente estaba almacenado en el componente rojo, verde y azul de la textura para facilitar el acceso a la GPU.</span><span class="sxs-lookup"><span data-stu-id="74748-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="74748-129">Nubes de geometría</span><span class="sxs-lookup"><span data-stu-id="74748-129">Geometry clouds</span></span>

<span data-ttu-id="74748-130">Para asegurarse de que nuestros equipos con las versiones más bajas podrían representar las nubes que decidimos empezar con un enfoque que usaría geometría sólida para minimizar el desdibujado.</span><span class="sxs-lookup"><span data-stu-id="74748-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="74748-131">En primer lugar, hemos intentado generar nubes mediante la generación de una malla de mapa de elevación sólida para cada capa mediante el radio de la textura de información de la nube por vértice para generar la forma.</span><span class="sxs-lookup"><span data-stu-id="74748-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="74748-132">Usamos un sombreador de geometría para generar los vértices en la parte superior y en la parte inferior de la nube que genera las formas de nube sólida.</span><span class="sxs-lookup"><span data-stu-id="74748-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="74748-133">Usamos el valor de densidad de la textura para colorear la nube con colores más oscuros para nubes más densas.</span><span class="sxs-lookup"><span data-stu-id="74748-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="74748-134">**Sombreador para crear los vértices:**</span><span class="sxs-lookup"><span data-stu-id="74748-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="74748-135">Hemos introducido un pequeño patrón de ruido para obtener más detalles sobre los datos reales.</span><span class="sxs-lookup"><span data-stu-id="74748-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="74748-136">Para producir bordes redondos de la nube, se recortan los píxeles del sombreador de píxeles cuando el valor de radio interpolado alcanza un umbral para descartar los valores cercanos a cero.</span><span class="sxs-lookup"><span data-stu-id="74748-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Nubes de geometría](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="74748-138">Dado que las nubes son geometría sólida, se pueden representar antes del terreno para ocultar los píxeles de mapa caros de debajo para mejorar la velocidad de fotogramas.</span><span class="sxs-lookup"><span data-stu-id="74748-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="74748-139">Esta solución se ejecutó correctamente en todas las tarjetas gráficas de las tarjetas de gráficos de alta especificación a las tarjetas gráficas de alto nivel, así como en HoloLens, debido al enfoque de representación de geometría sólida.</span><span class="sxs-lookup"><span data-stu-id="74748-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="74748-140">Nubes de partículas sólidas</span><span class="sxs-lookup"><span data-stu-id="74748-140">Solid particle clouds</span></span>

<span data-ttu-id="74748-141">Ahora tenemos una solución de copia de seguridad que generaba una representación decente de nuestros datos en la nube, pero era un poco Lackluster en el factor "wow" y no transmitió la sensación volumétrica que queríamos para nuestros equipos de alta gama.</span><span class="sxs-lookup"><span data-stu-id="74748-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="74748-142">El siguiente paso fue crear las nubes al representarlas con aproximadamente 100.000 partículas para producir una apariencia más orgánica y volumétrica.</span><span class="sxs-lookup"><span data-stu-id="74748-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="74748-143">Si los objetos siguen siendo sólidos y se ordenan de antemano, se puede beneficiar de la selección del búfer de profundidad de los píxeles que se encuentran en las partículas representadas anteriormente, lo que reduce el desdibujo.</span><span class="sxs-lookup"><span data-stu-id="74748-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="74748-144">Además, con una solución basada en partículas, podemos modificar la cantidad de partículas que se usan para tener como destino un hardware diferente.</span><span class="sxs-lookup"><span data-stu-id="74748-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="74748-145">Sin embargo, todavía es necesario probar en profundidad todos los píxeles, lo que da lugar a una sobrecarga adicional.</span><span class="sxs-lookup"><span data-stu-id="74748-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="74748-146">En primer lugar, creamos posiciones de partículas alrededor del punto central de la experiencia en el inicio.</span><span class="sxs-lookup"><span data-stu-id="74748-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="74748-147">Distribuimos las partículas más densamente en torno al centro y menos en la distancia.</span><span class="sxs-lookup"><span data-stu-id="74748-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="74748-148">Se han ordenado previamente todas las partículas del centro al fondo para que los objetos más cercanos se representen primero.</span><span class="sxs-lookup"><span data-stu-id="74748-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="74748-149">Un sombreador de cálculo muestrearía la textura de información de la nube para colocar cada partícula con un alto y color correctos en función de la densidad.</span><span class="sxs-lookup"><span data-stu-id="74748-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="74748-150">Usamos *DrawProcedural* para representar una cuádruple por partícula, lo que permite que los datos de partículas permanezcan en la GPU en todo momento.</span><span class="sxs-lookup"><span data-stu-id="74748-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="74748-151">Cada partícula contenía un alto y un radio.</span><span class="sxs-lookup"><span data-stu-id="74748-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="74748-152">El alto se basó en los datos en la nube muestreados desde la textura de información de la nube y el radio se basó en la distribución inicial, donde se calcularía para almacenar la distancia horizontal a su vecino más cercano.</span><span class="sxs-lookup"><span data-stu-id="74748-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="74748-153">Los cuádruples usarían estos datos para orientarse horizontalmente con el alto, de modo que cuando los usuarios lo examinen horizontalmente, se muestre el alto y, cuando los usuarios lo examinaran de arriba abajo, se cubrirá el área entre sus vecinos.</span><span class="sxs-lookup"><span data-stu-id="74748-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Forma de partícula](images/particle-shape-700px.png)

<span data-ttu-id="74748-155">**Código del sombreador que muestra la distribución:**</span><span class="sxs-lookup"><span data-stu-id="74748-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="74748-156">Puesto que las partículas se ordenan de antemano y todavía usamos un sombreador de estilo sólido para recortar (no Blend) píxeles transparentes, esta técnica controla una cantidad sorprendente de partículas, evitando el costoso exceso de espacio, incluso en los equipos con menos potencia.</span><span class="sxs-lookup"><span data-stu-id="74748-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="74748-157">Nubes de partículas transparentes</span><span class="sxs-lookup"><span data-stu-id="74748-157">Transparent particle clouds</span></span>

<span data-ttu-id="74748-158">Las partículas sólidas proporcionaban una buena sensación orgánica a la forma de las nubes, pero todavía necesitaba algo para vender el fluffiness de las nubes.</span><span class="sxs-lookup"><span data-stu-id="74748-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="74748-159">Hemos decidido probar una solución personalizada para las tarjetas de gráficos de gama alta en las que se puede introducir transparencia.</span><span class="sxs-lookup"><span data-stu-id="74748-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="74748-160">Para ello, simplemente hemos cambiado el criterio de ordenación inicial de las partículas y hemos cambiado el sombreador para usar las texturas alfa.</span><span class="sxs-lookup"><span data-stu-id="74748-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Nubes Fluffy](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="74748-162">Parecía estupendo pero resultó que era demasiado pesado para incluso las máquinas más complicadas, ya que daría lugar a la representación de cada píxel en la pantalla cientos de veces.</span><span class="sxs-lookup"><span data-stu-id="74748-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="74748-163">Representación fuera de la pantalla con una resolución más baja</span><span class="sxs-lookup"><span data-stu-id="74748-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="74748-164">Para reducir el número de píxeles representados por las nubes, empezamos a representarlos en un búfer de resolución de trimestre (en comparación con la pantalla) y ajustar el resultado final en la pantalla después de dibujar todos los objetos.</span><span class="sxs-lookup"><span data-stu-id="74748-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="74748-165">Esto nos brindó aproximadamente una velocidad 4x, pero se incluía con un par de advertencias.</span><span class="sxs-lookup"><span data-stu-id="74748-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="74748-166">**Código para la representación fuera de la pantalla:**</span><span class="sxs-lookup"><span data-stu-id="74748-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="74748-167">En primer lugar, al representar en un búfer fuera de pantalla, se pierde toda la información de profundidad de la escena principal, lo que da lugar a partículas detrás de las montañas que se representan en la montaña.</span><span class="sxs-lookup"><span data-stu-id="74748-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="74748-168">En segundo lugar, al ajustar el búfer también se presentaron artefactos en los bordes de nuestras nubes donde el cambio de resolución era perceptible.</span><span class="sxs-lookup"><span data-stu-id="74748-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="74748-169">En las dos secciones siguientes se habla sobre cómo se resuelven estos problemas.</span><span class="sxs-lookup"><span data-stu-id="74748-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="74748-170">Búfer de profundidad de partículas</span><span class="sxs-lookup"><span data-stu-id="74748-170">Particle depth buffer</span></span>

<span data-ttu-id="74748-171">Para que las partículas coexistan con la geometría del mundo, donde una montaña o un objeto podrían cubrir partículas detrás de ella, rellenó el búfer fuera de pantalla con un búfer de profundidad que contiene la geometría de la escena principal.</span><span class="sxs-lookup"><span data-stu-id="74748-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="74748-172">Para generar este búfer de profundidad, creamos una segunda cámara y solo representamos la geometría sólida y la profundidad de la escena.</span><span class="sxs-lookup"><span data-stu-id="74748-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="74748-173">Después usamos la nueva textura en el sombreador de píxeles de las nubes para tapaba píxeles.</span><span class="sxs-lookup"><span data-stu-id="74748-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="74748-174">Usamos la misma textura para calcular la distancia a la geometría detrás de un píxel en la nube.</span><span class="sxs-lookup"><span data-stu-id="74748-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="74748-175">Al usar esa distancia y aplicarla al alfa del píxel, ahora se tenía el efecto de que las nubes se atenuaron a medida que se alejan del terreno, lo que elimina cualquier corte duro en el que se cumplan las partículas y el terreno.</span><span class="sxs-lookup"><span data-stu-id="74748-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Nubes mixtas en terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="74748-177">Enfoque de los bordes</span><span class="sxs-lookup"><span data-stu-id="74748-177">Sharpening the edges</span></span>

<span data-ttu-id="74748-178">Las nubes extendidas parecían prácticamente idénticas a las nubes de tamaño normal en el centro de las partículas o donde se superponen, pero mostraban algunos artefactos en los bordes de la nube.</span><span class="sxs-lookup"><span data-stu-id="74748-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="74748-179">De lo contrario, los bordes nítidos aparecerán borrosos y los efectos de alias se presentaron cuando se movía la cámara.</span><span class="sxs-lookup"><span data-stu-id="74748-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="74748-180">Resolvemos este problema mediante la ejecución de un sombreador simple en el búfer fuera de pantalla para determinar dónde se produjeron los grandes cambios en el contraste (1).</span><span class="sxs-lookup"><span data-stu-id="74748-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="74748-181">Se colocan los píxeles con cambios importantes en un nuevo búfer de estarcido (2).</span><span class="sxs-lookup"><span data-stu-id="74748-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="74748-182">Después usamos el búfer de estarcido para enmascarar estas áreas de contraste alto al aplicar el búfer fuera de pantalla a la pantalla, lo que da lugar a huecos en las nubes (3).</span><span class="sxs-lookup"><span data-stu-id="74748-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="74748-183">A continuación, representamos todas las partículas de nuevo en el modo de pantalla completa, pero esta vez usaba el búfer de estarcido para enmascarar todo excepto los bordes, lo que da lugar a un conjunto mínimo de píxeles tocados (4).</span><span class="sxs-lookup"><span data-stu-id="74748-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="74748-184">Puesto que el búfer de comandos ya se creó para las partículas, simplemente tenía que representarlo en la nueva cámara.</span><span class="sxs-lookup"><span data-stu-id="74748-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Progresión de los bordes de la nube de representación](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="74748-186">El resultado final era bordes nítidos con secciones del centro baratas de las nubes.</span><span class="sxs-lookup"><span data-stu-id="74748-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="74748-187">Aunque esto era mucho más rápido que la representación de todos los objetos en la pantalla completa, sigue habiendo un costo asociado a la prueba de un píxel en el búfer de estarcido, por lo que una cantidad masiva de sobredibujo sigue teniendo un costo.</span><span class="sxs-lookup"><span data-stu-id="74748-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="74748-188">Selección de partículas</span><span class="sxs-lookup"><span data-stu-id="74748-188">Culling particles</span></span>

<span data-ttu-id="74748-189">En nuestro efecto de viento, se generaron bandas triangulares largas en un sombreador de cálculo, con lo que se crean muchos WISPs de viento en el mundo.</span><span class="sxs-lookup"><span data-stu-id="74748-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="74748-190">Aunque el efecto de viento no era pesado en la velocidad de relleno debido a que las tiras de la piel se generaron, producía muchos cientos de miles de vértices, lo que produce una carga pesada para el sombreador de vértices.</span><span class="sxs-lookup"><span data-stu-id="74748-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="74748-191">Hemos introducido búferes de anexión en el sombreador de cálculo para alimentar un subconjunto de las franjas de viento que se van a dibujar.</span><span class="sxs-lookup"><span data-stu-id="74748-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="74748-192">Con alguna lógica de selección de frustum de vista simple en el sombreador de cálculo, podríamos determinar si una franja estaba fuera de la vista de cámara e impedir que se agregara al búfer de inserciones.</span><span class="sxs-lookup"><span data-stu-id="74748-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="74748-193">Esto redujo significativamente la cantidad de bandas, liberando algunos ciclos necesarios en la GPU.</span><span class="sxs-lookup"><span data-stu-id="74748-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="74748-194">**Código que muestra un búfer de anexión:**</span><span class="sxs-lookup"><span data-stu-id="74748-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="74748-195">*Sombreador de cálculo:*</span><span class="sxs-lookup"><span data-stu-id="74748-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="74748-196">*C#codifica*</span><span class="sxs-lookup"><span data-stu-id="74748-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="74748-197">Se intentó usar la misma técnica en las partículas de la nube, donde se seleccionarían en el sombreador de cálculo y solo se enviarían los objetos visibles que se van a representar.</span><span class="sxs-lookup"><span data-stu-id="74748-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="74748-198">En realidad, esta técnica no nos ha ahorrado mucho en la GPU, ya que el cuello de botella más importante era la cantidad de píxeles representada en la pantalla y no el costo de calcular los vértices.</span><span class="sxs-lookup"><span data-stu-id="74748-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="74748-199">El otro problema con esta técnica fue que el búfer de anexión se rellenó en orden aleatorio debido a su naturaleza en paralelo de la informática de las partículas, lo que hace que las partículas ordenadas no se ordenen, lo que provoca el parpadeo de los objetos en la nube.</span><span class="sxs-lookup"><span data-stu-id="74748-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="74748-200">Hay técnicas para ordenar el búfer de inserciones, pero la cantidad limitada de ganancia de rendimiento que se obtiene de los objetos de selección probablemente se desplazaría con una ordenación adicional, por lo que hemos decidido no seguir esta optimización.</span><span class="sxs-lookup"><span data-stu-id="74748-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="74748-201">Representación adaptable</span><span class="sxs-lookup"><span data-stu-id="74748-201">Adaptive rendering</span></span>

<span data-ttu-id="74748-202">Para garantizar una velocidad de fotogramas constante en una aplicación con condiciones de representación variables como una vista en la nube y una vista clara, se presentó la representación adaptable a nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="74748-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="74748-203">El primer paso de la representación adaptable es medir GPU.</span><span class="sxs-lookup"><span data-stu-id="74748-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="74748-204">Para ello, se inserta código personalizado en el búfer de comandos de GPU al principio y al final de un fotograma representado, lo que captura el tiempo de la pantalla de ojo izquierdo y derecho.</span><span class="sxs-lookup"><span data-stu-id="74748-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="74748-205">Al medir el tiempo empleado en la representación y compararlo con la tasa de actualización deseada, tenemos una idea de lo cerca que tuvimos que quitar fotogramas.</span><span class="sxs-lookup"><span data-stu-id="74748-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="74748-206">Cuando se acerque a quitar fotogramas, se adapta la representación para que sea más rápida.</span><span class="sxs-lookup"><span data-stu-id="74748-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="74748-207">Una manera sencilla de adaptar es cambiar el tamaño de la ventanilla de la pantalla, lo que requiere menos píxeles para representarlos.</span><span class="sxs-lookup"><span data-stu-id="74748-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="74748-208">Mediante el uso de *UnityEngine. XR. XRSettings. renderViewportScale* , el sistema reduce la ventanilla de destino y ajusta automáticamente el resultado de la copia de seguridad para que se ajuste a la pantalla.</span><span class="sxs-lookup"><span data-stu-id="74748-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="74748-209">Un pequeño cambio en la escala es apenas perceptible en la geometría universal, y un factor de escala de 0,7 requiere la mitad de la cantidad de píxeles que se va a representar.</span><span class="sxs-lookup"><span data-stu-id="74748-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% de la escala, la mitad de los píxeles](images/datascape-scaling-700px.jpg)

<span data-ttu-id="74748-211">Cuando se detecta que estamos a punto de quitar fotogramas, la escala se reduce en un número fijo y se vuelve a aumentar cuando se ejecuta de nuevo lo suficientemente rápido.</span><span class="sxs-lookup"><span data-stu-id="74748-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="74748-212">Aunque decidimos qué técnica de nube usar en función de las capacidades de gráficos del hardware en el inicio, es posible basarla en los datos de la medición de la GPU para evitar que el sistema se quede con poca resolución durante mucho tiempo, pero esto es algo que no teníamos tiempo.  para explorar en Datascape.</span><span class="sxs-lookup"><span data-stu-id="74748-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="74748-213">Opiniones finales</span><span class="sxs-lookup"><span data-stu-id="74748-213">Final thoughts</span></span>

<span data-ttu-id="74748-214">El objetivo de una variedad de hardware es desafiante y requiere cierta planeación.</span><span class="sxs-lookup"><span data-stu-id="74748-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="74748-215">Le recomendamos que empiece a trabajar con máquinas de bajo consumo para familiarizarse con el espacio del problema y desarrollar una solución de copia de seguridad que se ejecutará en todas las máquinas.</span><span class="sxs-lookup"><span data-stu-id="74748-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="74748-216">Diseñe la solución con la velocidad de relleno en mente, ya que los píxeles serán el recurso más valioso.</span><span class="sxs-lookup"><span data-stu-id="74748-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="74748-217">Geometría sólida de destino sobre la transparencia.</span><span class="sxs-lookup"><span data-stu-id="74748-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="74748-218">Con una solución de copia de seguridad, puede empezar a crear niveles en mayor complejidad para máquinas de gama alta o quizás simplemente mejorar la resolución de la solución de copia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="74748-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="74748-219">Diseño para los peores escenarios de casos y quizás considere el uso de la representación adaptable para situaciones pesadas.</span><span class="sxs-lookup"><span data-stu-id="74748-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="74748-220">Acerca de los autores</span><span class="sxs-lookup"><span data-stu-id="74748-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="74748-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="74748-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="74748-222">Ingeniero de software@Microsoft</span><span class="sxs-lookup"><span data-stu-id="74748-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="74748-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="74748-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="74748-224">Ingeniero de software@Microsoft</span><span class="sxs-lookup"><span data-stu-id="74748-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="74748-225">Vea también</span><span class="sxs-lookup"><span data-stu-id="74748-225">See also</span></span>
* [<span data-ttu-id="74748-226">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="74748-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="74748-227">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="74748-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
