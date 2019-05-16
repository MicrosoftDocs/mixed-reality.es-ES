---
title: Criterios de calidad de la aplicación
description: Este documento describe los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criterios de calidad de la aplicación, la realidad mixta mixto de aplicación de realidad
ms.openlocfilehash: e9f6cd5a6017e11cd167c8141d29b82f89af08e4
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628990"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="6ce7b-104">Criterios de calidad de la aplicación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-104">App quality criteria</span></span>

<span data-ttu-id="6ce7b-105">Este documento describe los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="6ce7b-106">Para cada factor se proporciona la siguiente información</span><span class="sxs-lookup"><span data-stu-id="6ce7b-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="6ce7b-107">Información general: una breve descripción de factor de calidad y por qué es importante.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="6ce7b-108">Impacto de dispositivo: el tipo de dispositivo de realidad mixta de ventana se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="6ce7b-109">Criterios de calidad: cómo evaluar el factor de calidad.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="6ce7b-110">Cómo medir: métodos para medir el problema (o experiencia).</span><span class="sxs-lookup"><span data-stu-id="6ce7b-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="6ce7b-111">Recomendaciones: resumen de los enfoques para ofrecer una mejor experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="6ce7b-112">Recursos: desarrolladores pertinentes y los recursos de diseño que son útiles para crear mejores experiencias de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="6ce7b-113">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="6ce7b-113">Frame rate</span></span>

<span data-ttu-id="6ce7b-114">Velocidad de fotogramas es el primer pilar de comodidad de holograma estabilidad y el usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="6ce7b-115">Velocidad de fotogramas por debajo de los destinos recomendados puede provocar hologramas aparezcan nerviosos afectan negativamente la believability de la experiencia y que puedan causar fatiga visual.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="6ce7b-116">La velocidad de fotogramas de destino para su experiencia en inmersivos Windows Mixed Reality estará bien 60 o 90Hz dependiendo de qué Mixed Reality compatible con equipos con Windows que desea admitir.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="6ce7b-117">HoloLens la velocidad de fotogramas de destino es de 60Hz.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-118">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-120"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-122">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-123">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-123">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-124">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-124">Best</span></span>  |  <span data-ttu-id="6ce7b-125">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-125">Meets</span></span> |  <span data-ttu-id="6ce7b-126">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="6ce7b-127">La aplicación cumple siempre fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en PCs Ultra; y 60fps en equipos estándar.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="6ce7b-128">La aplicación tiene caídas intermitentes de fotogramas no impide la experiencia principal; o bien FPS es constantemente inferior a objetivo deseado, pero no impida la experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="6ce7b-129">La aplicación está experimentando una disminución en la velocidad de fotogramas en promedio cada diez segundos o menos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-130">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-130">How to measure</span></span>

* <span data-ttu-id="6ce7b-131">Se proporciona un gráfico de velocidad de fotogramas en tiempo real a través mediante el [Windows Device Portal](using-the-windows-device-portal.md#system-performance) bajo "Rendimiento del sistema".</span><span class="sxs-lookup"><span data-stu-id="6ce7b-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="6ce7b-132">Para la depuración de desarrollo, agregar un contador de diagnóstico de velocidad de fotogramas en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="6ce7b-133">Consulte los recursos de un contador de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="6ce7b-134">Caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras se ejecuta la aplicación moviendo la cabeza de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="6ce7b-135">Si muestra en el holograma movimiento nerviosos inesperado, a continuación, de baja velocidad de fotogramas o el plano de estabilidad es probablemente la causa.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-136">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-136">Recommendations</span></span>

* <span data-ttu-id="6ce7b-137">Agregar un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="6ce7b-138">Los cambios que se incurre en un descenso en la velocidad de fotogramas deben ser evaluados y resuelto correctamente como un error de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-140">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-140">Documentation</span></span>

* [<span data-ttu-id="6ce7b-141">Análisis de rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="6ce7b-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="6ce7b-142">Velocidad de fotogramas y la estabilidad de holograma</span><span class="sxs-lookup"><span data-stu-id="6ce7b-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="6ce7b-143">Presupuesto de rendimiento de activos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="6ce7b-144">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-145">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-145">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-146">MRToolkit, para mostrar del contador FPS</span><span class="sxs-lookup"><span data-stu-id="6ce7b-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="6ce7b-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="6ce7b-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="6ce7b-148">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="6ce7b-148">External references</span></span>

* [<span data-ttu-id="6ce7b-149">Unity, optimización de aplicaciones móviles</span><span class="sxs-lookup"><span data-stu-id="6ce7b-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="6ce7b-150">Estabilidad holograma</span><span class="sxs-lookup"><span data-stu-id="6ce7b-150">Hologram stability</span></span>

<span data-ttu-id="6ce7b-151">Hologramas estables aumentará la facilidad de uso y believability de la aplicación y crear una experiencia de visualización más cómoda para el usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="6ce7b-152">La calidad de estabilidad holograma es el resultado de desarrollo de por sí buena aplicación y la capacidad del dispositivo a comprender (pista) su entorno.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="6ce7b-153">Mientras la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar estabilidad incluidos:</span><span class="sxs-lookup"><span data-stu-id="6ce7b-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="6ce7b-154">Uso de la placa de estabilización</span><span class="sxs-lookup"><span data-stu-id="6ce7b-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="6ce7b-155">Distancia delimitadores espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="6ce7b-156">Seguimiento</span><span class="sxs-lookup"><span data-stu-id="6ce7b-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-157">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-159"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-160">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-161">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-161">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-162">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-162">Best</span></span>  |  <span data-ttu-id="6ce7b-163">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-163">Meets</span></span> |  <span data-ttu-id="6ce7b-164">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-165">Hologramas aparecen continuamente estables.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="6ce7b-166">Contenido secundario Exhibe movimiento inesperado; o movimiento inesperado impedir la experiencia de aplicación global.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="6ce7b-167">Contenido principal en el marco exhibe un movimiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-168">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-168">How to measure</span></span>

<span data-ttu-id="6ce7b-169">Aunque utilice el dispositivo y la experiencia de visualización:</span><span class="sxs-lookup"><span data-stu-id="6ce7b-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="6ce7b-170">Mover la cabeza de lado a lado, si el hologramas muestran el movimiento inesperado, a continuación, de baja velocidad de fotogramas o alineación incorrecta de la placa de estabilidad en el plano focal es la causa probable.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="6ce7b-171">Moverse por el entorno y hologramas, Buscar comportamientos como nado y jumpiness.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="6ce7b-172">Este tipo de movimiento es probable que deba por el dispositivo no hace seguimiento el entorno o la distancia con relación al anclaje espacial.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="6ce7b-173">Si es grande o varios hologramas están en el marco, observar el comportamiento de holograma en diversos profundidades al mover su posición principal de lado a lado, si aparece de inestabilidad es probable que esto ha provocado por el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="6ce7b-174">Recomendaciones de</span><span class="sxs-lookup"><span data-stu-id="6ce7b-174">Recomendations</span></span>

* <span data-ttu-id="6ce7b-175">Agregar un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="6ce7b-176">Utilice el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="6ce7b-177">Siempre se representan hologramas delimitados dentro de 3 metros de su delimitador.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="6ce7b-178">Asegúrese de que su entorno está configurado para el seguimiento adecuado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="6ce7b-179">Diseñar su experiencia para evitar hologramas en distintos niveles de profundidad focal dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-180">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-181">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-181">Documentation</span></span>

* [<span data-ttu-id="6ce7b-182">Velocidad de fotogramas y la estabilidad de holograma</span><span class="sxs-lookup"><span data-stu-id="6ce7b-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="6ce7b-183">Caso práctico, con el plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="6ce7b-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="6ce7b-184">Análisis de rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="6ce7b-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="6ce7b-185">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="6ce7b-186">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="6ce7b-187">Seguimiento de control de errores</span><span class="sxs-lookup"><span data-stu-id="6ce7b-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="6ce7b-188">Marco estático de referencia</span><span class="sxs-lookup"><span data-stu-id="6ce7b-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-189">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-189">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-190">El Sr. complementaria Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="6ce7b-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="6ce7b-191">Posición de hologramas en superficies real</span><span class="sxs-lookup"><span data-stu-id="6ce7b-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="6ce7b-192">Desajustes de hologramas con objetos físicos (si está diseñado para colocarse en relación con ellas) es una indicación clara de la unión no son de hologramas y reales.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="6ce7b-193">Precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; Por ejemplo, colocación de superficie general puede usar la asignación espacial, pero más preciso colocación requerirán algún uso de marcadores y calibración.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-194">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-196"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-197">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-198">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-198">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-199">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-199">Best</span></span>  |  <span data-ttu-id="6ce7b-200">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-200">Meets</span></span> |  <span data-ttu-id="6ce7b-201">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="6ce7b-202">Hologramas alinean a la superficie de normalmente en los centímetros al intervalo pulgadas.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="6ce7b-203">Si se requiere mayor precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="6ce7b-204">N/A</span><span class="sxs-lookup"><span data-stu-id="6ce7b-204">NA</span></span> | <span data-ttu-id="6ce7b-205">El hologramas aparecen sin alinear con el objeto de destino físico interrumpir el plano de la superficie o que aparecen a float lejos de la superficie.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="6ce7b-206">Si se requiere la precisión, hologramas deben cumplir la especificación de la proximidad del escenario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-207">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-207">How to measure</span></span>

* <span data-ttu-id="6ce7b-208">No deben aparecer hologramas que se colocan en el mapa espacial drásticamente flotar encima o debajo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="6ce7b-209">Hologramas que requieren una colocación precisa deben tener algún tipo de marcador y calibración del sistema que es preciso hasta los requisitos del escenario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-210">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-210">Recommendations</span></span>

* <span data-ttu-id="6ce7b-211">Asignación espacial es útil para colocar objetos en superficies cuando la precisión no es necesaria.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="6ce7b-212">La mejor precisión, utilizar marcadores o pósters para establecer el hologramas y un controlador Xbox (o algún mecanismo de alineación manual) para la calibración final.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="6ce7b-213">Considere la posibilidad de dividir hologramas muy grandes en partes lógicas y alinear cada parte a la superficie.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="6ce7b-214">Incorrectamente conjunto interpupilary distancia (IPD) también puede afectar la alineación holograma.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="6ce7b-215">Configure siempre HoloLens en IPD del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-216">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-217">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-217">Documentation</span></span>

* [<span data-ttu-id="6ce7b-218">Selección de ubicación de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="6ce7b-219">Espacio de proceso de detección</span><span class="sxs-lookup"><span data-stu-id="6ce7b-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="6ce7b-220">Prácticas recomendadas de delimitadores espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="6ce7b-221">Seguimiento de control de errores</span><span class="sxs-lookup"><span data-stu-id="6ce7b-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="6ce7b-222">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="6ce7b-223">Introducción al desarrollo de Vuforia</span><span class="sxs-lookup"><span data-stu-id="6ce7b-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-224">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-224">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-225">MR Spatial 230: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="6ce7b-226">El Sr. Kit de herramientas, bibliotecas de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="6ce7b-227">MR complementaria Kit, ejemplo de calibración de póster</span><span class="sxs-lookup"><span data-stu-id="6ce7b-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="6ce7b-228">El Sr. complementaria Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="6ce7b-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="6ce7b-229">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="6ce7b-229">External references</span></span>

* [<span data-ttu-id="6ce7b-230">Caso práctico de Lowes, alineación de precisión</span><span class="sxs-lookup"><span data-stu-id="6ce7b-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="6ce7b-231">Visualización de zona de comodidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-231">Viewing zone of comfort</span></span>

<span data-ttu-id="6ce7b-232">Control de los desarrolladores de aplicaciones donde convergen los ojos de los usuarios mediante la colocación de contenido y hologramas en diversos profundidades.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="6ce7b-233">Los usuarios gastando de HoloLens siempre se alojará a m 2.0 para mantener una imagen clara porque muestra de HoloLens se fija en una distancia óptica aproximadamente 2.0m alejándose del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="6ce7b-234">Profundidad de contenido incorrecto puede provocar fatiga ni incomodidad visual.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-235">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-237"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-238">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-239">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="6ce7b-240">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="6ce7b-241">Colocar contenido en 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-241">Place content at 2m.</span></span></li><li><span data-ttu-id="6ce7b-242">Cuando no se puede colocar hologramas en 2 minutos y no se puede evitar conflictos entre la convergencia y alojamiento, es la zona de colocación holograma óptimo entre 1,25 y 5 millones.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="6ce7b-243">En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios interactúen más de 1 m de distancia (por ejemplo, ajustar el tamaño del contenido y predeterminado de los parámetros de colocación).</span><span class="sxs-lookup"><span data-stu-id="6ce7b-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="6ce7b-244">A menos que específicamente no es necesario según el escenario, un plano de recorte debe implementar con fadeout comenzando en 1 millón.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="6ce7b-245">En casos donde se requiere una observación más cerca de un holograma inmóvil, el contenido no debe ser menor que 50cm.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="6ce7b-246">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-246">Meets</span></span></td><td> <span data-ttu-id="6ce7b-247">Está contenido dentro de la Guía de movimiento y de visualización, pero uso incorrecto o no utiliza el plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6ce7b-248">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-248">Fail</span></span> </td><td> <span data-ttu-id="6ce7b-249">El contenido se presenta demasiado cerca (normalmente &lt;1.25 m, o &lt;50 cm para estacionarios hologramas que requieren más cerca de observación.)</span><span class="sxs-lookup"><span data-stu-id="6ce7b-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-250">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-250">How to measure</span></span>

* <span data-ttu-id="6ce7b-251">Contenido deberían normalmente tener 2m ausente, pero no más cerca que más de 5m o 1,25.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="6ce7b-252">Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en .85CM con fadeout empezando por 1m de contenido.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="6ce7b-253">Enfocar el contenido y tenga en cuenta el efecto del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="6ce7b-254">Contenido estático no debe estar más cerca que 50cm ausente.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-255">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-255">Recommendations</span></span>

* <span data-ttu-id="6ce7b-256">Diseñar el contenido de la distancia óptima de 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="6ce7b-257">Establece la distancia de la representación de recorte en 85cm con fadeout empezando por 1m de contenido.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="6ce7b-258">Para hologramas estacionarios que necesitan más cerca de visualización, el plano de recorte debe ser no menos de 30cm y fadeout debe empezar al menos 10cm fuera del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-259">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-259">Resources</span></span>

* [<span data-ttu-id="6ce7b-260">Representar distancia</span><span class="sxs-lookup"><span data-stu-id="6ce7b-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="6ce7b-261">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="6ce7b-262">Experimentar con escala</span><span class="sxs-lookup"><span data-stu-id="6ce7b-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="6ce7b-263">Texto, tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="6ce7b-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="6ce7b-264">Cambio de profundidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-264">Depth switching</span></span>

<span data-ttu-id="6ce7b-265">Independientemente de la zona de visualización de los problemas de comodidad, exige el usuario puede cambiar con frecuencia o rápidamente entre casi y ahora focal objetos (incluidos hologramas y contenido del mundo real) pueden dar lugar a fatiga oculomotor y malestar general.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-266">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-268"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-269">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-270">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-271">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-271">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-272">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-272">Best</span></span>  |  <span data-ttu-id="6ce7b-273">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-273">Meets</span></span> |  <span data-ttu-id="6ce7b-274">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-275">Profundidad natural o limitada de conmutación no hace que se reenfocar al usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="6ce7b-276">Conmutador de profundidad abrupta es el núcleo y diseñadas en la experiencia de aplicación, o conmutador de profundidad abrupta producida por el contenido real-world inesperado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="6ce7b-277">Conmutador de profundidad coherente, o cambio brusco profundidad que no es necesario o core a la experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-278">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-278">How to measure</span></span>

* <span data-ttu-id="6ce7b-279">Si la aplicación requiere que el usuario para constantemente o repentinamente cambiar el foco de profundidad, no hay profundidad cambiar el problema.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-280">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-280">Recommendations</span></span>

* <span data-ttu-id="6ce7b-281">Mantener el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="6ce7b-282">Alivie oculomotor fatiga y movimiento holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-283">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-283">Resources</span></span>

* [<span data-ttu-id="6ce7b-284">Representar distancia</span><span class="sxs-lookup"><span data-stu-id="6ce7b-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="6ce7b-285">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="6ce7b-286">Uso de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-286">Use of spatial sound</span></span>

<span data-ttu-id="6ce7b-287">En Windows Mixed Reality, el motor de audio proporciona el componente de la experiencia de realidad mixta auditiva simulando 3D sonido con simulaciones del entorno, la distancia y dirección.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="6ce7b-288">Usar sonido espacial en una aplicación permite a los desarrolladores colocar convincingly sonidos en un espacio dimensional 3 (esfera) en todo el usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="6ce7b-289">Los sonidos, a continuación, le resultará como si provinieran objetos físicos real o la hologramas realidad mixta en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="6ce7b-290">Sonido espacial es una herramienta eficaz para inmersión, accesibilidad y diseño de la experiencia de usuario en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-291">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-293"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-294">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-295">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-296">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-296">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-297">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-297">Best</span></span>  |  <span data-ttu-id="6ce7b-298">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-298">Meets</span></span> |  <span data-ttu-id="6ce7b-299">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-300">Lógicamente es spatialized sonido y la experiencia de usuario adecuadamente usa sonido para ayudar a los comentarios de usuario y la detección de objeto.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="6ce7b-301">Sonido es natural y relevantes para los objetos y normalizado en el escenario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="6ce7b-302">Audio espacial es usado correctamente para believability pero no se encuentra como medio para facilitar la detectabilidad y comentarios del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="6ce7b-303">No se spatialized sonido según lo esperado, o falta de sonido para ayudar a los usuarios de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="6ce7b-304">O bien, no se considera o se usan en el diseño del escenario de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-305">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-305">How to measure</span></span>

* <span data-ttu-id="6ce7b-306">En general, deben emitir sonidos relevantes de hologramas de destino (ej., sonido corteza procedentes de perro holográfica.)</span><span class="sxs-lookup"><span data-stu-id="6ce7b-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="6ce7b-307">Las indicaciones de sonido deben usarse en toda la experiencia de usuario para ayudar al usuario con comentarios ni el conocimiento de las acciones fuera del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-308">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-308">Recommendations</span></span>

* <span data-ttu-id="6ce7b-309">Utilice audio espacial para ayudar con interfaces de usuario y la detección del objeto.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="6ce7b-310">Sonidos real funcionan mejor que síntesis o sonido no natural.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="6ce7b-311">Debe ser spatialized mayoría de los sonidos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="6ce7b-312">Evite los emisores invisibles.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="6ce7b-313">Evite enmascaramiento espacial.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="6ce7b-314">Normalizar todos los sonidos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-315">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-316">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-316">Documentation</span></span>

* [<span data-ttu-id="6ce7b-317">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="6ce7b-318">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="6ce7b-319">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="6ce7b-320">Caso práctico de sonido para HoloTour espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="6ce7b-321">Caso práctico, usar sonido espacial en RoboRaid</span><span class="sxs-lookup"><span data-stu-id="6ce7b-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-322">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-322">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-323">MR Spatial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="6ce7b-324">MRToolkit, Audio espacial</span><span class="sxs-lookup"><span data-stu-id="6ce7b-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="6ce7b-325">Centrarse en los límites del marco holográfica (FOV)</span><span class="sxs-lookup"><span data-stu-id="6ce7b-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="6ce7b-326">Experiencias de usuario bien diseñada pueden crear y mantener un contexto útil del entorno virtual que se extiende en torno a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="6ce7b-327">Mitigar el efecto de los límites FOV implica un diseño concienzudo de escalado de contenido y el contexto, el uso de audio espacial, sistemas de orientación y la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="6ce7b-328">Si se hace correctamente, el usuario se sentirán como menor afectadas por los límites del campo visual al tiempo que tiene una experiencia de aplicación cómodo.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-329">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-331"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-332">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-333">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-333">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-334">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-334">Best</span></span>  |  <span data-ttu-id="6ce7b-335">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-335">Meets</span></span> |  <span data-ttu-id="6ce7b-336">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-337">Usuario nunca pierde el contexto y se siente cómodo ver.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="6ce7b-338">Se proporciona ayuda contextual para los objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="6ce7b-339">Detectabilidad y ver la guía se proporcionan para los objetos fuera del marco.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="6ce7b-340">En general, el diseño de movimiento y la escala de la hologramas son adecuados para una experiencia de visualización cómoda.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="6ce7b-341">Usuario nunca pierde el contexto, pero es posible que deban movimiento cuello adicional en ciertas situaciones.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="6ce7b-342">En ciertas situaciones escalado hace hologramas para interrumpir en el marco vertical u horizontal, causando ciertos movimientos cuello ver hologramas.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="6ce7b-343">Usuario que puede perder contexto o movimiento cuello coherente se requiere para ver hologramas.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="6ce7b-344">Ninguna instrucción de contexto para objetos holográficas grandes, mover objetos fáciles de perder fuera del marco sin instrucciones de detectabilidad ni hologramas altos requiere movimiento cuello regulares para ver.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-345">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-345">How to measure</span></span>

* <span data-ttu-id="6ce7b-346">Contexto para un holograma (grande) se pierde o no entiende debido a que se recorta por los límites.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="6ce7b-347">Ubicación de hologramas son difíciles de encontrar debido a la falta de directores de atención o contenido que entra y sale rápidamente el marco holográfico.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="6ce7b-348">Escenario requiere repetitivas y reducir verticalmente un movimiento principal para ver por completo un holograma resultante en fatiga cuello y regular.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-349">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-349">Recommendations</span></span>

* <span data-ttu-id="6ce7b-350">La experiencia de inicio con objetos pequeños que ajustar el campo visual y, después, realizar la transición con indicaciones visuales a las versiones más grandes.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="6ce7b-351">Use espaciales directores de audio y atención para la búsqueda de contenido de usuario que está fuera del campo visual.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="6ce7b-352">Cuando sea posible, evite hologramas que recortar verticalmente el campo visual.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="6ce7b-353">Proporcionar al usuario con instrucciones de la aplicación para ver la ubicación de mejor.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-354">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-355">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-355">Documentation</span></span>

* [<span data-ttu-id="6ce7b-356">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="6ce7b-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="6ce7b-357">Caso práctico, HoloStudio UI y conocimientos de diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="6ce7b-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="6ce7b-358">Escalado de objetos y entornos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="6ce7b-359">Cursores, indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="6ce7b-360">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="6ce7b-360">External references</span></span>

* [<span data-ttu-id="6ce7b-361">El campo visual con ado</span><span class="sxs-lookup"><span data-stu-id="6ce7b-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="6ce7b-362">Contenido reacciona a la posición del usuario</span><span class="sxs-lookup"><span data-stu-id="6ce7b-362">Content reacts to user position</span></span>

<span data-ttu-id="6ce7b-363">Hologramas deben reaccionar ante el usuario coloque en aproximadamente la misma forma que los objetos de "real".</span><span class="sxs-lookup"><span data-stu-id="6ce7b-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="6ce7b-364">Una consideración de diseño importantes es elementos de interfaz de usuario que no se pueden suponer necesariamente la posición de un usuario esté parados y adaptar y movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="6ce7b-365">Diseñar una aplicación que correctamente se adapta a la posición del usuario creará una experiencia más solo y que sea más fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-366">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-368"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-369">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-370">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-371">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="6ce7b-372">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-372">Best</span></span> </td><td> <span data-ttu-id="6ce7b-373">Contenido y la interfaz de usuario se adaptan a las posiciones de usuario que permite usuario interactúen de forma natural con contenido dentro del ámbito de movimiento de usuario esperado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6ce7b-374">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-374">Meets</span></span> </td><td> <span data-ttu-id="6ce7b-375">Interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave pedir al usuario que ajustan su posición.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="6ce7b-376">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="6ce7b-377">Elementos de interfaz de usuario se pierde o se bloquea durante el usuario que causan de movimiento que se vuelva a controles (o busque).</span><span class="sxs-lookup"><span data-stu-id="6ce7b-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="6ce7b-378">Elementos de interfaz de usuario limitan la vista de contenido principal.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="6ce7b-379">Movimiento de la interfaz de usuario no está optimizado para la visualización de distancia y momentum especialmente con <a href="billboarding-and-tag-along.md">tag-along</a> elementos de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-380">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-380">How to measure</span></span>

* <span data-ttu-id="6ce7b-381">Todas las mediciones deben realizarse dentro de un ámbito razonable del escenario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="6ce7b-382">Aunque puede variar el movimiento de usuario, no intente engañar a la aplicación con el movimiento de usuario extreme.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="6ce7b-383">Para los elementos de interfaz de usuario, los controles relevantes deben estar disponibles, independientemente del movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="6ce7b-384">Por ejemplo, si el usuario está viendo y caminar alrededor de un mapa 3D con zoom, el control de zoom debe ser estén disponible para el usuario independientemente de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-385">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-385">Recommendations</span></span>

* <span data-ttu-id="6ce7b-386">El usuario es la cámara y controlan el movimiento.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="6ce7b-387">Deje que su unidad.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-387">Let them drive.</span></span>
* <span data-ttu-id="6ce7b-388">Considere la posibilidad de vallas publicitarias para texto y sistemas trabajé que de lo contrario serían bloqueado por el mundo u oculta si un usuario tuviera que desplazarse.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="6ce7b-389">Usar tag-along para el contenido que debe seguir al usuario mientras sigue permitiendo que el usuario ver lo que está delante de ellas.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-390">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-391">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-391">Documentation</span></span>

* [<span data-ttu-id="6ce7b-392">Diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="6ce7b-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="6ce7b-393">Color de luz y material</span><span class="sxs-lookup"><span data-stu-id="6ce7b-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="6ce7b-394">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="6ce7b-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6ce7b-395">Conceptos básicos de la interacción</span><span class="sxs-lookup"><span data-stu-id="6ce7b-395">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6ce7b-396">El movimiento y el desplazamiento del usuario</span><span class="sxs-lookup"><span data-stu-id="6ce7b-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-397">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-397">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-398">MR Input 210: mirada</span><span class="sxs-lookup"><span data-stu-id="6ce7b-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="6ce7b-399">Claridad de interacción de entrada</span><span class="sxs-lookup"><span data-stu-id="6ce7b-399">Input interaction clarity</span></span>

<span data-ttu-id="6ce7b-400">Claridad de interacción de entrada es fundamental para la facilidad de uso de una aplicación e incluye la entrada coherencia, innegables, detectabilidad de los métodos de interacción.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="6ce7b-401">Usuario debería poder usar las interacciones habituales de toda la plataforma sin volver a aprender.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="6ce7b-402">Si la aplicación tiene parámetros de entrada personalizado, se debe claramente comunicar y demostrar.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-403">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-405"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-406">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-407">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-408">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-408">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-409">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-409">Best</span></span>  |  <span data-ttu-id="6ce7b-410">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-410">Meets</span></span> |  <span data-ttu-id="6ce7b-411">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-412">Métodos de entrada de interacción son coherentes con Windows Mixed Reality proporcionado [orientación](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="6ce7b-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="6ce7b-413">Cualquier entrada personalizada no debería ser redundante con la entrada estándar (en su lugar use interacción estándar) y debe claramente comunicar y demostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="6ce7b-414">Es similar a las entradas mejor, pero personalizadas son redundantes con métodos de entrada estándares.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="6ce7b-415">Usuario todavía puede lograr el objetivo y el progreso a través de la experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="6ce7b-416">Difíciles de comprender la asignación de botón o el método de entrada.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="6ce7b-417">Input personalizado en gran medida, no es compatible con la entrada estándar, no hay instrucciones, o puede provocar problemas de fatiga y comodidad.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-418">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-418">How to measure</span></span>

* <span data-ttu-id="6ce7b-419">La aplicación usa coherente [métodos de entrada estándar.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="6ce7b-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="6ce7b-420">Si la aplicación tiene parámetros de entrada personalizados, claramente se comunique a través de:</span><span class="sxs-lookup"><span data-stu-id="6ce7b-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="6ce7b-421">Experiencia de primera ejecución</span><span class="sxs-lookup"><span data-stu-id="6ce7b-421">First-run experience</span></span>
* <span data-ttu-id="6ce7b-422">Pantallas de presentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-422">Introductory screens</span></span>
* <span data-ttu-id="6ce7b-423">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="6ce7b-423">Tooltips</span></span>
* <span data-ttu-id="6ce7b-424">Instructora de mano</span><span class="sxs-lookup"><span data-stu-id="6ce7b-424">Hand coach</span></span>
* <span data-ttu-id="6ce7b-425">Sección de ayuda</span><span class="sxs-lookup"><span data-stu-id="6ce7b-425">Help section</span></span>
* <span data-ttu-id="6ce7b-426">VoiceOver</span><span class="sxs-lookup"><span data-stu-id="6ce7b-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-427">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-427">Recommendations</span></span>

* <span data-ttu-id="6ce7b-428">Utilice los métodos de entrada estándares siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="6ce7b-429">Proporcionar información sobre herramientas, tutoriales y demostraciones para métodos de entrada no estándares.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="6ce7b-430">Usar un modelo de interacción coherente en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-431">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-432">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-432">Documentation</span></span>

* [<span data-ttu-id="6ce7b-433">Aspectos básicos de interacción de Windows MR</span><span class="sxs-lookup"><span data-stu-id="6ce7b-433">Windows MR interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="6ce7b-434">Objetos interactuable</span><span class="sxs-lookup"><span data-stu-id="6ce7b-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="6ce7b-435">Selección de destinos de la mirada</span><span class="sxs-lookup"><span data-stu-id="6ce7b-435">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="6ce7b-436">Cursores</span><span class="sxs-lookup"><span data-stu-id="6ce7b-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6ce7b-437">Comodidad y mirada</span><span class="sxs-lookup"><span data-stu-id="6ce7b-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="6ce7b-438">Gestos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="6ce7b-439">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="6ce7b-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="6ce7b-440">Diseño de la voz</span><span class="sxs-lookup"><span data-stu-id="6ce7b-440">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="6ce7b-441">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="6ce7b-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="6ce7b-442">Guía de portabilidad de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="6ce7b-443">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="6ce7b-444">Mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="6ce7b-445">Gestos y controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="6ce7b-446">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="6ce7b-447">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="6ce7b-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="6ce7b-448">Mirada principal y de ojo de DirectX</span><span class="sxs-lookup"><span data-stu-id="6ce7b-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="6ce7b-449">Las manos y los controladores de movimiento de DirectX</span><span class="sxs-lookup"><span data-stu-id="6ce7b-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="6ce7b-450">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="6ce7b-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-451">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-451">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-452">Caso práctico: La búsqueda de informática más personal</span><span class="sxs-lookup"><span data-stu-id="6ce7b-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="6ce7b-453">Estudio de conversión: HoloStudio UI y conocimientos de diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="6ce7b-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="6ce7b-454">Aplicación de ejemplo: Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="6ce7b-455">Aplicación de ejemplo: Módulo lunar</span><span class="sxs-lookup"><span data-stu-id="6ce7b-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="6ce7b-456">MR Input 210: mirada</span><span class="sxs-lookup"><span data-stu-id="6ce7b-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="6ce7b-457">MR Input 211: Gestos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="6ce7b-458">MR Input 212: voz</span><span class="sxs-lookup"><span data-stu-id="6ce7b-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="6ce7b-459">Objetos interactuable</span><span class="sxs-lookup"><span data-stu-id="6ce7b-459">Interactable objects</span></span>

<span data-ttu-id="6ce7b-460">Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="6ce7b-461">En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="6ce7b-462">Nada puede ser un objeto Interactuable que desencadena un evento.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="6ce7b-463">Un objeto interactuable puede representarse como nada una taza de café en la tabla a un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="6ce7b-464">Independientemente del formulario, objetos interactuable deben ser claramente reconocibles por el usuario a través de las pistas de audio y visuales.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-465">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-467"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-468">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-469">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-470">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-470">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-471">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-471">Best</span></span>  |  <span data-ttu-id="6ce7b-472">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-472">Meets</span></span> |  <span data-ttu-id="6ce7b-473">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-474">Independientemente del formulario, objetos interactuable sean reconocibles a través de las indicaciones visuales y de audio a través de tres estados: inactivo, destinado y seleccionada.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="6ce7b-475">"Vea, diga" claro y coherente sirve a lo largo de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="6ce7b-476">Los objetos se escala y se distribuyen para permitir errores como destino.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="6ce7b-477">Usuario puede reconocer el objeto como interactuable a través de comentarios de audio o el objeto visual y puede tener como destino y activar el objeto.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="6ce7b-478">No dada indicaciones visuales o audio, usuario no puede reconocer un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="6ce7b-479">Las interacciones son propensas a errores debido a la escala del objeto o la distancia entre los objetos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-480">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-480">How to measure</span></span>

* <span data-ttu-id="6ce7b-481">Objetos interactuable son reconocibles como 'interactuable'; incluyendo contenido específico de los botones, menús y la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="6ce7b-482">Como regla general debería haber una pista de audio y visual cuando tenga como destino objetos interactuable.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-483">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-483">Recommendations</span></span>

* <span data-ttu-id="6ce7b-484">Usar comentarios visuales y de audio para las interacciones.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="6ce7b-485">Comentarios visuales es diferente para cada entrada de estado (inactivo, destino, seleccionado)</span><span class="sxs-lookup"><span data-stu-id="6ce7b-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="6ce7b-486">Deben ser escalar y colocan por error libre como destino objetos interactuable.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="6ce7b-487">Los objetos agrupados interactuable (por ejemplo, una barra de menús o lista) deben tener espacio adecuado para dirigirse a.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="6ce7b-488">Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto de la palabra clave de comando ("verlo, diga")</span><span class="sxs-lookup"><span data-stu-id="6ce7b-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-489">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-490">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-490">Documentation</span></span>

* [<span data-ttu-id="6ce7b-491">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="6ce7b-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6ce7b-492">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="6ce7b-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="6ce7b-493">Barra de la aplicación y cuadro delimitador</span><span class="sxs-lookup"><span data-stu-id="6ce7b-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6ce7b-494">Diseño de la voz</span><span class="sxs-lookup"><span data-stu-id="6ce7b-494">Voice design</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-495">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-495">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-496">Kit de herramientas de realidad mixta - UX</span><span class="sxs-lookup"><span data-stu-id="6ce7b-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="6ce7b-497">Sala de análisis</span><span class="sxs-lookup"><span data-stu-id="6ce7b-497">Room scanning</span></span>

<span data-ttu-id="6ce7b-498">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="6ce7b-499">La integridad y la calidad de los datos depende de varios factores como la cantidad de exploración, el usuario ha hecho, ¿cuánto tiempo ha transcurrido desde la exploración y si objetos como muebles y puertas movido desde que el dispositivo había analizado el área.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="6ce7b-500">Muchas aplicaciones analizará los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad de la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="6ce7b-501">Si el usuario es necesario para analizar el entorno, desactive le proporcionará instrucciones durante la experiencia de exploración.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-502">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-504"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-505">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-506">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-506">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-507">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-507">Best</span></span>  |  <span data-ttu-id="6ce7b-508">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-508">Meets</span></span> |  <span data-ttu-id="6ce7b-509">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-510">Visualización de la malla espacial indique a los usuarios análisis está en curso.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="6ce7b-511">Usuario claramente sabe qué hacer y cuando se inicia y detiene el análisis.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="6ce7b-512">Se proporciona la visualización de la malla espacial, pero el usuario puede saber con claridad qué hacer y se proporciona ninguna información de progreso.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="6ce7b-513">No hay ninguna visualización de malla.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-513">No visualization of mesh.</span></span> <span data-ttu-id="6ce7b-514">No se proporciona al usuario sobre dónde buscar o cuando el examen se inicia o detiene la información de orientación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-515">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-515">How to measure</span></span>

* <span data-ttu-id="6ce7b-516">Durante un examen de espacio necesaria, se proporciona orientación de audio y visual que indica dónde buscar y cuándo se debe iniciar y detener análisis.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-517">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-517">Recommendations</span></span>

* <span data-ttu-id="6ce7b-518">Indicar cuánto volumen total, en la proximidad de los usuarios debe formar parte de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="6ce7b-519">Cuando el examen se inicia y detiene como un indicador de progreso se comunican.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="6ce7b-520">Usar una visualización de la malla durante el análisis.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="6ce7b-521">Proporcionar indicaciones visuales y de audio para fomentar que usuario examinar y desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="6ce7b-522">Informar al usuario dónde debe ir para mejorar los datos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="6ce7b-523">En muchos casos, puede ser mejor indicar que el usuario lo que necesitan (por ejemplo, examine el límite superior, busque detrás de muebles), con el fin de obtener la calidad del análisis necesarios.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-524">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="6ce7b-525">Documentación</span><span class="sxs-lookup"><span data-stu-id="6ce7b-525">Documentation</span></span>

* [<span data-ttu-id="6ce7b-526">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="6ce7b-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="6ce7b-527">Caso práctico: Expandir las capacidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="6ce7b-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="6ce7b-528">Caso práctico: Diseño espacial de sonido para HoloTour</span><span class="sxs-lookup"><span data-stu-id="6ce7b-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="6ce7b-529">Caso práctico: Creación de una experiencia realmente cautivadora en fragmentos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="6ce7b-530">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-530">Tools and tutorials</span></span>

* [<span data-ttu-id="6ce7b-531">Kit de herramientas de realidad mixta - UX</span><span class="sxs-lookup"><span data-stu-id="6ce7b-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="6ce7b-532">Indicadores direccionales</span><span class="sxs-lookup"><span data-stu-id="6ce7b-532">Directional indicators</span></span>

<span data-ttu-id="6ce7b-533">En una aplicación de realidad mixta, el contenido puede estar fuera del campo de visión u ocluyeron en objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="6ce7b-534">Una aplicación bien diseñada le resultará más fácil para el usuario buscar el contenido que no sea visible.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="6ce7b-535">Indicadores direccionales alertar a un usuario al contenido importante y asesoramiento sobre el contenido en relación con la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="6ce7b-536">Guía de contenido que no sea visible puede adoptar la forma de los emisores de sonido, flechas direccionales o indicaciones visuales directas.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-537">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-539"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-540">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-541">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-542">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-542">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-543">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-543">Best</span></span>  |  <span data-ttu-id="6ce7b-544">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-544">Meets</span></span> |  <span data-ttu-id="6ce7b-545">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-546">Indicaciones visuales y de audio directamente guiar al usuario al contenido pertinente fuera el campo de visión.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="6ce7b-547">Una flecha o algún indicador que señala al usuario en la dirección general del contenido.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="6ce7b-548">Contenido relevante está fuera del campo de visión y deficiente o ninguna Guía de ubicación se proporciona al usuario.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-549">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-549">How to measure</span></span>

* <span data-ttu-id="6ce7b-550">Contenido relevante fuera del campo de vista de usuario es reconocible a través de las indicaciones visuales o audio.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-551">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-551">Recommendations</span></span>

* <span data-ttu-id="6ce7b-552">Cuando contenido relevante está fuera del campo de visión del usuario, utilice indicadores direccionales y pistas de sonido para guiar al usuario al contenido.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="6ce7b-553">En muchos casos, se prefiere una guía visual directa a través de las flechas direccionales.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="6ce7b-554">Indicadores direccionales no deben generarse en el cursor.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-555">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-555">Resources</span></span>

* [<span data-ttu-id="6ce7b-556">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="6ce7b-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="6ce7b-557">Carga de datos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-557">Data loading</span></span>

<span data-ttu-id="6ce7b-558">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="6ce7b-559">Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto podría ser el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="6ce7b-560">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="6ce7b-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="6ce7b-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6ce7b-562"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6ce7b-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="6ce7b-563">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6ce7b-564">✔️</span><span class="sxs-lookup"><span data-stu-id="6ce7b-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="6ce7b-565">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="6ce7b-565">Quality criteria</span></span>

|  <span data-ttu-id="6ce7b-566">Mejor</span><span class="sxs-lookup"><span data-stu-id="6ce7b-566">Best</span></span>  |  <span data-ttu-id="6ce7b-567">Cumple</span><span class="sxs-lookup"><span data-stu-id="6ce7b-567">Meets</span></span> |  <span data-ttu-id="6ce7b-568">un error</span><span class="sxs-lookup"><span data-stu-id="6ce7b-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="6ce7b-569">Anima el indicador visual, en forma de una barra de progreso o anillo, que muestra el progreso durante cualquier dato cargando o procesando.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="6ce7b-570">El indicador visual proporciona orientación sobre cuánto podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="6ce7b-571">Se informa al usuario que la carga de datos está en curso, pero no hay ninguna indicación de cuánto podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="6ce7b-572">No hay carga de datos o indicadores de proceso de tarea tarda más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="6ce7b-573">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="6ce7b-573">How to measure</span></span>

* <span data-ttu-id="6ce7b-574">Compruebe que no hay ningún estado en blanco durante más de 5 segundos durante la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="6ce7b-575">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="6ce7b-575">Recommendations</span></span>

* <span data-ttu-id="6ce7b-576">Proporcione una animación de la carga de datos muestra el progreso en cualquier situación cuando el usuario puede percibir esta aplicación se ha detenido o se ha bloqueado.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="6ce7b-577">Una regla general razonable es cualquier actividad "Cargando" que podría tardar más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="6ce7b-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="6ce7b-578">Recursos</span><span class="sxs-lookup"><span data-stu-id="6ce7b-578">Resources</span></span>

* [<span data-ttu-id="6ce7b-579">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="6ce7b-579">Displaying progress</span></span>](progress.md)
