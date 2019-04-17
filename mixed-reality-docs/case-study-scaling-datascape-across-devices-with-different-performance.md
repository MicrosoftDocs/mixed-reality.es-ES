---
title: 'Caso práctico: escalado Datascape en todos los dispositivos con distintos del rendimiento'
description: En este caso práctico se ofrece información sobre cómo los desarrolladores de Microsoft optimiza la aplicación Datascape para ofrecer una experiencia convincente en dispositivos con una variedad de capacidades de rendimiento.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: auriculares envolventes, optimización, VR, caso práctico de rendimiento
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605738"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="e179d-104">Caso práctico: escalado Datascape en todos los dispositivos con distintos del rendimiento</span><span class="sxs-lookup"><span data-stu-id="e179d-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="e179d-105">Datascape es una aplicación de Windows Mixed Reality desarrollada internamente en Microsoft que nos hemos centrado en mostrar los datos meteorológicos encima de los datos de terreno.</span><span class="sxs-lookup"><span data-stu-id="e179d-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="e179d-106">La aplicación explora la información única que los usuarios obtienen de detección de datos en mixed reality rodeando el usuario con la visualización de datos holográfica.</span><span class="sxs-lookup"><span data-stu-id="e179d-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="e179d-107">Datascape queríamos una variedad de plataformas de destino con capacidades de hardware diferentes que abarcan desde Microsoft HoloLens a inmersivos Windows Mixed Reality y desde los equipos con tecnología de inferior para los equipos más recientes con GPU de gama alta.</span><span class="sxs-lookup"><span data-stu-id="e179d-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="e179d-108">El desafío principal fue la representación de la escena en cuestión visualmente atractiva en dispositivos con capacidades de gráficos totalmente diferente mientras se ejecuta en una alta velocidad de fotogramas.</span><span class="sxs-lookup"><span data-stu-id="e179d-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="e179d-109">En este caso práctico le guiará a través del proceso y las técnicas utilizadas para crear algunos de nuestros sistemas GPU que consumen muchos más, donde se describen los problemas que se producen y cómo los hemos superado.</span><span class="sxs-lookup"><span data-stu-id="e179d-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="e179d-110">Transparencia y sobredibujan</span><span class="sxs-lookup"><span data-stu-id="e179d-110">Transparency and overdraw</span></span>

<span data-ttu-id="e179d-111">Nuestro dificultades de procesamiento principal tratan con transparencia, ya que la transparencia puede ser costosa en una GPU.</span><span class="sxs-lookup"><span data-stu-id="e179d-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="e179d-112">Se pueden representar geometría sólida delante hacia atrás al escribir en el búfer de profundidad, deteniendo los píxeles futuras detrás de ese píxel desde que se descarte.</span><span class="sxs-lookup"><span data-stu-id="e179d-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="e179d-113">Esto evita que oculta píxeles ejecutando al sombreador de píxeles, acelerar significativamente el proceso.</span><span class="sxs-lookup"><span data-stu-id="e179d-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="e179d-114">Si la geometría se ordena de forma óptima, se dibujará una sola vez cada píxel en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="e179d-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="e179d-115">Geometría transparente debe ordenarse atrás adelante y se basa en la salida del sombreador de píxeles y el píxel actual en la pantalla de fusión.</span><span class="sxs-lookup"><span data-stu-id="e179d-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="e179d-116">Esto puede dar lugar a que cada píxel en la pantalla se dibuja en varias veces por fotograma, conocido como el sobredibujo.</span><span class="sxs-lookup"><span data-stu-id="e179d-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="e179d-117">Para equipos estándar y HoloLens, la pantalla solo se puede rellenar una serie de veces, haciendo que sea transparente representación problemático.</span><span class="sxs-lookup"><span data-stu-id="e179d-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="e179d-118">Introducción a los componentes de escena Datascape</span><span class="sxs-lookup"><span data-stu-id="e179d-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="e179d-119">Tuvimos tres componentes principales que nuestra escena; **la interfaz de usuario, el mapa**, y **la información meteorológica**.</span><span class="sxs-lookup"><span data-stu-id="e179d-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="e179d-120">Desde el principio sabíamos que nuestros efectos meteorológicos requeriría todo el tiempo GPU podría obtener, por lo que hemos diseñado la interfaz de usuario y el terreno de manera que podría reducir cualquier sobredibujo.</span><span class="sxs-lookup"><span data-stu-id="e179d-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="e179d-121">Nos rehacerse la interfaz de usuario varias veces para minimizar la cantidad de sobredibujo se generará.</span><span class="sxs-lookup"><span data-stu-id="e179d-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="e179d-122">Nos equivocamos en el lado de geometría más complejo en lugar de superposición de arte transparente encima de otros para componentes como descripciones de los botones y asignación resplandecientes.</span><span class="sxs-lookup"><span data-stu-id="e179d-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="e179d-123">Para la asignación, se usa a un sombreador personalizado que desea quitar las características estándar de Unity como sombras e iluminación compleja, reemplazarlos con un modelo de iluminación simple sun único y un cálculo personalizado niebla.</span><span class="sxs-lookup"><span data-stu-id="e179d-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="e179d-124">Esto genera un sombreador de píxeles simples y liberar ciclos GPU.</span><span class="sxs-lookup"><span data-stu-id="e179d-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="e179d-125">Se administra obtener la interfaz de usuario y la asignación a la representación en el presupuesto que no necesitábamos los cambios en ellos dependiendo del hardware; Sin embargo, la visualización del tiempo, en particular, la representación en la nube, resultó para ser más complicado!</span><span class="sxs-lookup"><span data-stu-id="e179d-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="e179d-126">En segundo plano de datos en la nube</span><span class="sxs-lookup"><span data-stu-id="e179d-126">Background on cloud data</span></span>

<span data-ttu-id="e179d-127">Nuestros datos en la nube se descargan desde los servidores de la NOAA (http://nomads.ncep.noaa.gov/) y llegó a nosotros en tres capas 2D distintas, cada uno con el alto de la parte superior e inferior de la nube, así como la densidad de la nube para cada celda de la cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="e179d-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="e179d-128">Se obtuvo procesan los datos en una textura de información en la nube donde cada componente se almacenó en el componente rojo, verde y azul de la textura para facilitar el acceso en la GPU.</span><span class="sxs-lookup"><span data-stu-id="e179d-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="e179d-129">Nubes de geometría</span><span class="sxs-lookup"><span data-stu-id="e179d-129">Geometry clouds</span></span>

<span data-ttu-id="e179d-130">Para asegurarse de que nuestros equipos con tecnología inferior se podía mostrar nuestro nubes hemos decidido empezar con un enfoque que utilizaría la geometría sólida para minimizar el sobredibujo.</span><span class="sxs-lookup"><span data-stu-id="e179d-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="e179d-131">En primer lugar, hemos intentado generar nubes generando una malla de mapa de elevación sólido para cada capa con el radio de la textura de información en la nube por cada vértice para generar la forma.</span><span class="sxs-lookup"><span data-stu-id="e179d-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="e179d-132">Se utiliza a un sombreador de geometría para producir los vértices en la parte superior y en la parte inferior de la nube genera formas sólida en la nube.</span><span class="sxs-lookup"><span data-stu-id="e179d-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="e179d-133">Se usará el valor de densidad de la textura a la nube de color con los colores más oscuros para obtener más nubes densas.</span><span class="sxs-lookup"><span data-stu-id="e179d-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="e179d-134">**Sombreador para crear los vértices:**</span><span class="sxs-lookup"><span data-stu-id="e179d-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="e179d-135">Se introdujo un modelo pequeño ruido para obtener más detalles sobre los datos reales.</span><span class="sxs-lookup"><span data-stu-id="e179d-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="e179d-136">Para generar los bordes de redondeo en la nube, se recortan los píxeles en el sombreador de píxeles cuando el valor de radio interpolada alcanza un umbral para descartar los valores de casi cero.</span><span class="sxs-lookup"><span data-stu-id="e179d-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Nubes de geometría](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="e179d-138">Puesto que las nubes son geometría sólida, que se puede procesar antes del terreno para ocultar los píxeles del mapa costoso debajo para mejorar la velocidad de fotogramas.</span><span class="sxs-lookup"><span data-stu-id="e179d-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="e179d-139">Esta solución se ejecutó correctamente en todas las tarjetas gráficas de min-spec las tarjetas de gráficos avanzados, así como en HoloLens, debido al enfoque de representación de geometría sólida.</span><span class="sxs-lookup"><span data-stu-id="e179d-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="e179d-140">Nubes de partícula sólida</span><span class="sxs-lookup"><span data-stu-id="e179d-140">Solid particle clouds</span></span>

<span data-ttu-id="e179d-141">Ahora tenemos una solución de copia de seguridad que genera una representación decente de nuestros datos en la nube, pero fue un poco mediocres en el factor "wow" y no transmitir la idea volumétrico que deseábamos para nuestros equipos de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="e179d-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="e179d-142">El siguiente paso era crear las nubes que se representan con aproximadamente 100.000 objetos para producir una apariencia más orgánica y volumétrica.</span><span class="sxs-lookup"><span data-stu-id="e179d-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="e179d-143">Si partículas permanecen sólidas y ordenación delante hacia atrás, nos podemos aún aprovechar sacrificio de búfer de profundidad de los píxeles detrás de objetos procesados anteriormente, lo que reduce el sobredibujo.</span><span class="sxs-lookup"><span data-stu-id="e179d-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="e179d-144">Además, con una solución basada en partículas, podemos alterar la cantidad de partículas usa en otro hardware de destino.</span><span class="sxs-lookup"><span data-stu-id="e179d-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="e179d-145">Sin embargo, todos los píxeles todavía deben ser probado en profundidad, lo que produce una sobrecarga adicional.</span><span class="sxs-lookup"><span data-stu-id="e179d-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="e179d-146">En primer lugar, creamos las posiciones de partículas alrededor del punto central de la experiencia en el inicio.</span><span class="sxs-lookup"><span data-stu-id="e179d-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="e179d-147">Se distribuyen las partículas más densidad en torno al centro y menos por lo tanto, en la distancia.</span><span class="sxs-lookup"><span data-stu-id="e179d-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="e179d-148">Se ordenan previamente todas las partículas desde el centro hacia atrás por lo que implicaría que primero las partículas más cercano.</span><span class="sxs-lookup"><span data-stu-id="e179d-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="e179d-149">Un sombreador de cálculo sería la textura de información en la nube para colocar cada partícula en un alto correcto y el color que basa en la densidad de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="e179d-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="e179d-150">Hemos usado *DrawProcedural* representar un cuatro por partículas permitir que los datos de la partícula para mantenerse en la GPU en todo momento.</span><span class="sxs-lookup"><span data-stu-id="e179d-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="e179d-151">Cada partícula contenía un alto y un radio.</span><span class="sxs-lookup"><span data-stu-id="e179d-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="e179d-152">El alto se basaba en los datos en la nube muestreados de la textura de información en la nube y el radio se basaba en la distribución inicial donde se calcularán para almacenar la distancia horizontal a su vecino más cercano.</span><span class="sxs-lookup"><span data-stu-id="e179d-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="e179d-153">Los cuadrantes utilizaría estos datos para orientar a sí mismo en el ángulo entre el alto para que cuando los usuarios lo mires horizontalmente, se mostraría el alto y cuando los usuarios consultó arriba a abajo, el área entre sus vecinos sería cubierto.</span><span class="sxs-lookup"><span data-stu-id="e179d-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Forma de partícula](images/particle-shape-700px.png)

<span data-ttu-id="e179d-155">**Código del sombreador que muestra la distribución:**</span><span class="sxs-lookup"><span data-stu-id="e179d-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="e179d-156">Como ordenamos el partículas de delante hacia atrás y todavía se usa a un sombreador de estilo continuo a los píxeles transparentes de clip (blend no), esta técnica controla una cantidad sorprendente de partículas, evitar costosa draw excesiva incluso en las máquinas basadas en la inferior.</span><span class="sxs-lookup"><span data-stu-id="e179d-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="e179d-157">Nubes de partículas transparente</span><span class="sxs-lookup"><span data-stu-id="e179d-157">Transparent particle clouds</span></span>

<span data-ttu-id="e179d-158">Las partículas sólidas proporcionan una buena idea orgánica a la forma de las nubes, pero todavía necesita algo que vender el fluffiness de nubes.</span><span class="sxs-lookup"><span data-stu-id="e179d-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="e179d-159">Hemos decidido intentar una solución personalizada para las tarjetas de gráficos avanzados donde podemos introducir la transparencia.</span><span class="sxs-lookup"><span data-stu-id="e179d-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="e179d-160">Para hacer esto simplemente se cambia el criterio de ordenación inicial de las partículas y cambia el sombreador para usar la versión alfa de texturas.</span><span class="sxs-lookup"><span data-stu-id="e179d-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy nubes](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="e179d-162">Un aspecto excelente, pero ha demostrado para ser demasiado pesada para incluso las máquinas más complicadas, ya que daría como resultado del procesamiento de cada píxel en la pantalla de cientos de veces en!</span><span class="sxs-lookup"><span data-stu-id="e179d-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="e179d-163">Representar fuera de la pantalla con una resolución inferior</span><span class="sxs-lookup"><span data-stu-id="e179d-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="e179d-164">Para reducir el número de píxeles representados por las nubes, comenzamos a procesarlas en el búfer de resolución de un trimestre (en comparación con la pantalla) y ajuste el resultado final copia de seguridad en la pantalla después de que todas las partículas tenían ha dibujado.</span><span class="sxs-lookup"><span data-stu-id="e179d-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="e179d-165">Esto nos dio aproximadamente una velocidad 4 x, pero suministrada con un par de advertencias.</span><span class="sxs-lookup"><span data-stu-id="e179d-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="e179d-166">**Código para representar fuera de la pantalla:**</span><span class="sxs-lookup"><span data-stu-id="e179d-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="e179d-167">En primer lugar, al representar en un búfer fuera de la pantalla, hemos perdido toda la información de profundidad de nuestra escena principal, lo que resulta en partículas detrás montañas representación encima de la montaña.</span><span class="sxs-lookup"><span data-stu-id="e179d-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="e179d-168">En segundo lugar, ajuste el búfer también introdujo los artefactos de los bordes de nuestro nubes donde el cambio de la resolución fue evidente.</span><span class="sxs-lookup"><span data-stu-id="e179d-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="e179d-169">Las dos secciones siguientes se hablan acerca de cómo se resuelven estos problemas.</span><span class="sxs-lookup"><span data-stu-id="e179d-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="e179d-170">Búfer de profundidad de partículas</span><span class="sxs-lookup"><span data-stu-id="e179d-170">Particle depth buffer</span></span>

<span data-ttu-id="e179d-171">Para hacer que los objetos coexistir con la geometría del mundo donde una montaña o un objeto podría abarcar partículas detrás de él, se rellena el búfer fuera de la pantalla con un búfer de profundidad con la geometría de la escena principal.</span><span class="sxs-lookup"><span data-stu-id="e179d-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="e179d-172">Para generar este tipo búfer de profundidad, creamos una segunda cámara, sólo la geometría sólida y la profundidad de la escena de representación.</span><span class="sxs-lookup"><span data-stu-id="e179d-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="e179d-173">A continuación, usamos la textura nuevo en el sombreador de píxeles de las nubes para occlude píxeles.</span><span class="sxs-lookup"><span data-stu-id="e179d-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="e179d-174">Se usa la misma textura para calcular la distancia a la geometría detrás de un píxel en la nube.</span><span class="sxs-lookup"><span data-stu-id="e179d-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="e179d-175">Mediante esa distancia y aplicarlo a la versión alfa del píxel, ahora se tenía el efecto de nubes de difuminación que obtienen cerca de terreno, quitando los cortes de disco duros donde se encuentran las partículas y el terreno.</span><span class="sxs-lookup"><span data-stu-id="e179d-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Nubes combinadas en terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="e179d-177">Enfocar los bordes</span><span class="sxs-lookup"><span data-stu-id="e179d-177">Sharpening the edges</span></span>

<span data-ttu-id="e179d-178">Las nubes arriba ajusta tenía casi idénticas a las nubes de tamaño normal en el centro de las partículas o donde superponen, pero se ha mostrado algunos artefactos en los bordes de la nube.</span><span class="sxs-lookup"><span data-stu-id="e179d-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="e179d-179">En caso contrario, bordes nítidos podría aparecer borrosos y efectos de alias se introdujeron cuando mueve la cámara.</span><span class="sxs-lookup"><span data-stu-id="e179d-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="e179d-180">Resolvimos este problema mediante la ejecución de un sombreador sencillo en el búfer fuera de la pantalla para determinar donde grandes cambios produjeron por el contrario (1).</span><span class="sxs-lookup"><span data-stu-id="e179d-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="e179d-181">Colocamos los píxeles con grandes cambios en un búfer nuevo de la Galería de símbolos (2).</span><span class="sxs-lookup"><span data-stu-id="e179d-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="e179d-182">A continuación, utilizamos el búfer de galería de símbolos para la máscara de estas áreas de alto contraste al aplicar el búfer fuera de la pantalla en la pantalla, lo que resulta en agujeros dentro y alrededor de las nubes (3).</span><span class="sxs-lookup"><span data-stu-id="e179d-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="e179d-183">Se luego se representan todas las partículas nuevo en el modo de pantalla completa, pero esta vez había utilizado el búfer de galería de símbolos para ocultar todo, pero los bordes, lo que resulta en un conjunto mínimo de píxeles tocado (4).</span><span class="sxs-lookup"><span data-stu-id="e179d-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="e179d-184">Dado que el búfer de comandos ya se ha creado las partículas, teníamos simplemente procésela de nuevo a la cámara nuevo.</span><span class="sxs-lookup"><span data-stu-id="e179d-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Progresión de representar los bordes de la nube](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="e179d-186">El resultado final fue bordes nítidos secciones center económico de las nubes.</span><span class="sxs-lookup"><span data-stu-id="e179d-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="e179d-187">Aunque esto era mucho más rápido que la representación de todas las partículas en pantalla completa, no hay todavía un costo asociado con las pruebas de un píxel en el búfer de galería de símbolos, por lo que una enorme cantidad de sobredibujo todavía se suministra con un costo.</span><span class="sxs-lookup"><span data-stu-id="e179d-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="e179d-188">Selección de objetos</span><span class="sxs-lookup"><span data-stu-id="e179d-188">Culling particles</span></span>

<span data-ttu-id="e179d-189">Para nuestro efecto del viento, generamos bandas de triángulo larga en un sombreador de cálculo, crear muchas espirales de viento en el mundo.</span><span class="sxs-lookup"><span data-stu-id="e179d-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="e179d-190">Aunque el efecto del viento no era un gran velocidad de relleno debido a las tiras delgadas generado, genera muchos cientos de miles de vértices, lo que resulta en una carga elevada para el sombreador de vértices.</span><span class="sxs-lookup"><span data-stu-id="e179d-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="e179d-191">Hemos introducido anexar los búferes en el sombreador de cálculo para introducir un subconjunto de las bandas de viento va a dibujar.</span><span class="sxs-lookup"><span data-stu-id="e179d-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="e179d-192">Con alguna vista simple frustum selección lógica en el sombreador de cálculo, podríamos determinar si fue una banda fuera de la vista de la cámara y evitar que se agreguen al búfer de inserción.</span><span class="sxs-lookup"><span data-stu-id="e179d-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="e179d-193">Esto reduce la cantidad de bandas considerablemente, liberando algunos ciclos necesarios en la GPU.</span><span class="sxs-lookup"><span data-stu-id="e179d-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="e179d-194">**Código que muestra un búfer de datos anexados:**</span><span class="sxs-lookup"><span data-stu-id="e179d-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="e179d-195">*Sombreador de cálculo:*</span><span class="sxs-lookup"><span data-stu-id="e179d-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="e179d-196">*C#código:*</span><span class="sxs-lookup"><span data-stu-id="e179d-196">*C# code:*</span></span>

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

<span data-ttu-id="e179d-197">Intentamos usando la misma técnica en las partículas en la nube, donde podría eliminar directamente a ellos en el sombreador de cálculo y solo insertar las partículas visibles va a representar.</span><span class="sxs-lookup"><span data-stu-id="e179d-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="e179d-198">Esta técnica realmente no ha guardado nos mucho en la GPU ya que el cuello de botella más importante era los píxeles de cantidad representados en la pantalla y no el costo de calcular los vértices.</span><span class="sxs-lookup"><span data-stu-id="e179d-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="e179d-199">El otro problema con esta técnica era que rellena el búfer de datos anexados en orden aleatorio debido a su naturaleza de las partículas, causando las partículas ordenadas sea no ordenada, lo que resulta en que parpadean partículas en la nube de informática en paralelo.</span><span class="sxs-lookup"><span data-stu-id="e179d-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="e179d-200">Existen técnicas para ordenar el búfer de inserción, pero la cantidad limitada de ganancia de rendimiento que obtuvimos fuera de partículas de caras traseras probablemente haría desplazamiento con una ordenación adicional, por lo que decidimos no iniciará esta optimización.</span><span class="sxs-lookup"><span data-stu-id="e179d-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="e179d-201">Procesamiento adaptable</span><span class="sxs-lookup"><span data-stu-id="e179d-201">Adaptive rendering</span></span>

<span data-ttu-id="e179d-202">Para garantizar una velocidad de fotogramas constante en una aplicación con distintas condiciones, como un vs nublado de representación de una vista clara, procesamiento adaptable se introdujo a nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="e179d-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="e179d-203">Es el primer paso de procesamiento adaptable medir la GPU.</span><span class="sxs-lookup"><span data-stu-id="e179d-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="e179d-204">Esto es lo hicimos insertando código personalizado en el búfer de comandos GPU al principio y final de un fotograma representado, capturar tanto la izquierda y derecha ocular. hora de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="e179d-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="e179d-205">Midiendo el tiempo dedicado a procesamiento y compararlo con nuestro frecuencia de actualización deseada que obtuvimos una idea de cómo cerrar fuéramos a fotogramas descartados.</span><span class="sxs-lookup"><span data-stu-id="e179d-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="e179d-206">Cuando cerca de fotogramas descartados, adaptamos nuestra presentación para que sea más rápido.</span><span class="sxs-lookup"><span data-stu-id="e179d-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="e179d-207">Una manera sencilla de adaptar está cambiando el tamaño de la ventanilla de la pantalla, que requieren menos píxeles que se procesan.</span><span class="sxs-lookup"><span data-stu-id="e179d-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="e179d-208">Mediante el uso de *UnityEngine.XR.XRSettings.renderViewportScale* el sistema se reduce la ventanilla de destino y se expande automáticamente el resultado de la copia de seguridad en la pantalla de ajuste.</span><span class="sxs-lookup"><span data-stu-id="e179d-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="e179d-209">Un pequeño cambio en la escala es apenas perceptible en la geometría del mundo, y un factor de escala de 0,7 requiere la mitad de la cantidad de píxeles que se va a representar.</span><span class="sxs-lookup"><span data-stu-id="e179d-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![escala de un 70%, la mitad de los píxeles](images/datascape-scaling-700px.jpg)

<span data-ttu-id="e179d-211">Cuando se detecten que se van a elimina fotogramas, reducir el escalado por un número fijo y aumentar nuevo cuando ejecutamos de nuevo con la suficiente rapidez.</span><span class="sxs-lookup"><span data-stu-id="e179d-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="e179d-212">Aunque hemos decidido qué técnica en la nube para utilizarla según gráficos capacidades del hardware en el inicio, es posible basarlo en los datos de la medición de GPU para impedir que el sistema permanece en baja resolución durante mucho tiempo, pero esto es algo que no tuvimos tiempo  para explorar en Datascape.</span><span class="sxs-lookup"><span data-stu-id="e179d-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="e179d-213">Observaciones finales</span><span class="sxs-lookup"><span data-stu-id="e179d-213">Final thoughts</span></span>

<span data-ttu-id="e179d-214">Destinatarios de una variedad de hardware es difícil y requiere cierta planeación.</span><span class="sxs-lookup"><span data-stu-id="e179d-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="e179d-215">Le recomendamos que inicie máquinas con tecnología de inferior para familiarizarse con el espacio del problema y desarrollar una solución de copia de seguridad que se ejecutará en todos los equipos de destino.</span><span class="sxs-lookup"><span data-stu-id="e179d-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="e179d-216">Diseñar la solución con la tasa de relleno en mente, como píxeles estará el recurso más valioso.</span><span class="sxs-lookup"><span data-stu-id="e179d-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="e179d-217">Geometría sólida de destino a través de transparencia.</span><span class="sxs-lookup"><span data-stu-id="e179d-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="e179d-218">Con una solución de copia de seguridad, puede iniciar, a continuación, en capas en la complejidad de las máquinas de gama alta o quizás simplemente mejorar la resolución de la solución de copia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="e179d-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="e179d-219">Diseñar para escenarios más desfavorables y quizás considere el uso de procesamiento adaptable para situaciones pesadas.</span><span class="sxs-lookup"><span data-stu-id="e179d-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="e179d-220">Acerca de los autores</span><span class="sxs-lookup"><span data-stu-id="e179d-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="e179d-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="e179d-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="e179d-222">Ingeniero de software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e179d-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="e179d-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="e179d-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="e179d-224">Ingeniero de software @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e179d-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="e179d-225">Vea también</span><span class="sxs-lookup"><span data-stu-id="e179d-225">See also</span></span>
* [<span data-ttu-id="e179d-226">Análisis de rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="e179d-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="e179d-227">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="e179d-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
