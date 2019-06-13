---
title: Criterios de calidad de la aplicación
description: Este documento describe los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criterios de calidad de la aplicación, la realidad mixta mixto de aplicación de realidad
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024493"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="c5fdf-104">Criterios de calidad de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-104">App quality criteria</span></span>

<span data-ttu-id="c5fdf-105">Este documento describe los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="c5fdf-106">Para cada factor se proporciona la siguiente información</span><span class="sxs-lookup"><span data-stu-id="c5fdf-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="c5fdf-107">Información general: una breve descripción de factor de calidad y por qué es importante.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="c5fdf-108">Impacto de dispositivo: el tipo de dispositivo de realidad mixta de ventana se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="c5fdf-109">Criterios de calidad: cómo evaluar el factor de calidad.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="c5fdf-110">Cómo medir: métodos para medir el problema (o experiencia).</span><span class="sxs-lookup"><span data-stu-id="c5fdf-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="c5fdf-111">Recomendaciones: resumen de los enfoques para ofrecer una mejor experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="c5fdf-112">Recursos: desarrolladores pertinentes y los recursos de diseño que son útiles para crear mejores experiencias de aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="c5fdf-113">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-113">Frame rate</span></span>

<span data-ttu-id="c5fdf-114">Velocidad de fotogramas es el primer pilar de comodidad de holograma estabilidad y el usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="c5fdf-115">Velocidad de fotogramas por debajo de los destinos recomendados puede provocar hologramas aparezcan nerviosos afectan negativamente la believability de la experiencia y que puedan causar fatiga visual.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="c5fdf-116">La velocidad de fotogramas de destino para su experiencia en inmersivos Windows Mixed Reality estará bien 60 o 90Hz dependiendo de qué Mixed Reality compatible con equipos con Windows que desea admitir.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="c5fdf-117">HoloLens la velocidad de fotogramas de destino es de 60Hz.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-118">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-120"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-121">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-121">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-122">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-123">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-123">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-124">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-124">Best</span></span>  |  <span data-ttu-id="c5fdf-125">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-125">Meets</span></span> |  <span data-ttu-id="c5fdf-126">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="c5fdf-127">La aplicación cumple siempre fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en PCs Ultra; y 60fps en equipos estándar.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="c5fdf-128">La aplicación tiene caídas intermitentes de fotogramas no impide la experiencia principal; o bien FPS es constantemente inferior a objetivo deseado, pero no impida la experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="c5fdf-129">La aplicación está experimentando una disminución en la velocidad de fotogramas en promedio cada diez segundos o menos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-130">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-130">How to measure</span></span>

* <span data-ttu-id="c5fdf-131">Se proporciona un gráfico de velocidad de fotogramas en tiempo real a través mediante el [Windows Device Portal](using-the-windows-device-portal.md#system-performance) bajo "Rendimiento del sistema".</span><span class="sxs-lookup"><span data-stu-id="c5fdf-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="c5fdf-132">Para la depuración de desarrollo, agregar un contador de diagnóstico de velocidad de fotogramas en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="c5fdf-133">Consulte los recursos de un contador de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="c5fdf-134">Caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras se ejecuta la aplicación moviendo la cabeza de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="c5fdf-135">Si muestra en el holograma movimiento nerviosos inesperado, a continuación, de baja velocidad de fotogramas o el plano de estabilidad es probablemente la causa.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-136">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-136">Recommendations</span></span>

* <span data-ttu-id="c5fdf-137">Agregar un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="c5fdf-138">Los cambios que se incurre en un descenso en la velocidad de fotogramas deben ser evaluados y resuelto correctamente como un error de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-140">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-140">Documentation</span></span>

* [<span data-ttu-id="c5fdf-141">Análisis de rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c5fdf-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="c5fdf-142">Velocidad de fotogramas y la estabilidad de holograma</span><span class="sxs-lookup"><span data-stu-id="c5fdf-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="c5fdf-143">Presupuesto de rendimiento de activos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="c5fdf-144">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-145">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-145">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-146">MRToolkit, para mostrar del contador FPS</span><span class="sxs-lookup"><span data-stu-id="c5fdf-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="c5fdf-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="c5fdf-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="c5fdf-148">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-148">External references</span></span>

* [<span data-ttu-id="c5fdf-149">Unity, optimización de aplicaciones móviles</span><span class="sxs-lookup"><span data-stu-id="c5fdf-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="c5fdf-150">Estabilidad holograma</span><span class="sxs-lookup"><span data-stu-id="c5fdf-150">Hologram stability</span></span>

<span data-ttu-id="c5fdf-151">Hologramas estables aumentará la facilidad de uso y believability de la aplicación y crear una experiencia de visualización más cómoda para el usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="c5fdf-152">La calidad de estabilidad holograma es el resultado de desarrollo de por sí buena aplicación y la capacidad del dispositivo a comprender (pista) su entorno.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="c5fdf-153">Mientras la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar estabilidad incluidos:</span><span class="sxs-lookup"><span data-stu-id="c5fdf-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="c5fdf-154">Uso de la placa de estabilización</span><span class="sxs-lookup"><span data-stu-id="c5fdf-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="c5fdf-155">Distancia delimitadores espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="c5fdf-156">Seguimiento</span><span class="sxs-lookup"><span data-stu-id="c5fdf-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-157">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-159"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-160">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-160">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-161">❌</span><span class="sxs-lookup"><span data-stu-id="c5fdf-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-162">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-162">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-163">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-163">Best</span></span>  |  <span data-ttu-id="c5fdf-164">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-164">Meets</span></span> |  <span data-ttu-id="c5fdf-165">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-166">Hologramas aparecen continuamente estables.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="c5fdf-167">Contenido secundario Exhibe movimiento inesperado; o movimiento inesperado impedir la experiencia de aplicación global.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="c5fdf-168">Contenido principal en el marco exhibe un movimiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-169">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-169">How to measure</span></span>

<span data-ttu-id="c5fdf-170">Aunque utilice el dispositivo y la experiencia de visualización:</span><span class="sxs-lookup"><span data-stu-id="c5fdf-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="c5fdf-171">Mover la cabeza de lado a lado, si el hologramas muestran el movimiento inesperado, a continuación, de baja velocidad de fotogramas o alineación incorrecta de la placa de estabilidad en el plano focal es la causa probable.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="c5fdf-172">Moverse por el entorno y hologramas, Buscar comportamientos como nado y jumpiness.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="c5fdf-173">Este tipo de movimiento es probable que deba por el dispositivo no hace seguimiento el entorno o la distancia con relación al anclaje espacial.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="c5fdf-174">Si es grande o varios hologramas están en el marco, observar el comportamiento de holograma en diversos profundidades al mover su posición principal de lado a lado, si aparece de inestabilidad es probable que esto ha provocado por el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="c5fdf-175">Recomendaciones de</span><span class="sxs-lookup"><span data-stu-id="c5fdf-175">Recomendations</span></span>

* <span data-ttu-id="c5fdf-176">Agregar un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="c5fdf-177">Utilice el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="c5fdf-178">Siempre se representan hologramas delimitados dentro de 3 metros de su delimitador.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="c5fdf-179">Asegúrese de que su entorno está configurado para el seguimiento adecuado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="c5fdf-180">Diseñar su experiencia para evitar hologramas en distintos niveles de profundidad focal dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-181">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-182">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-182">Documentation</span></span>

* [<span data-ttu-id="c5fdf-183">Velocidad de fotogramas y la estabilidad de holograma</span><span class="sxs-lookup"><span data-stu-id="c5fdf-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="c5fdf-184">Caso práctico, con el plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="c5fdf-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="c5fdf-185">Análisis de rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c5fdf-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="c5fdf-186">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="c5fdf-187">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="c5fdf-188">Seguimiento de control de errores</span><span class="sxs-lookup"><span data-stu-id="c5fdf-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="c5fdf-189">Marco estático de referencia</span><span class="sxs-lookup"><span data-stu-id="c5fdf-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-190">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-190">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-191">El Sr. complementaria Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="c5fdf-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="c5fdf-192">Posición de hologramas en superficies real</span><span class="sxs-lookup"><span data-stu-id="c5fdf-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="c5fdf-193">Desajustes de hologramas con objetos físicos (si está diseñado para colocarse en relación con ellas) es una indicación clara de la unión no son de hologramas y reales.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="c5fdf-194">Precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; Por ejemplo, colocación de superficie general puede usar la asignación espacial, pero más preciso colocación requerirán algún uso de marcadores y calibración.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-195">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-197"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-198">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-198">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-199">❌</span><span class="sxs-lookup"><span data-stu-id="c5fdf-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-200">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-200">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-201">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-201">Best</span></span>  |  <span data-ttu-id="c5fdf-202">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-202">Meets</span></span> |  <span data-ttu-id="c5fdf-203">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="c5fdf-204">Hologramas alinean a la superficie de normalmente en los centímetros al intervalo pulgadas.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="c5fdf-205">Si se requiere mayor precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="c5fdf-206">N/A</span><span class="sxs-lookup"><span data-stu-id="c5fdf-206">NA</span></span> | <span data-ttu-id="c5fdf-207">El hologramas aparecen sin alinear con el objeto de destino físico interrumpir el plano de la superficie o que aparecen a float lejos de la superficie.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="c5fdf-208">Si se requiere la precisión, hologramas deben cumplir la especificación de la proximidad del escenario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-209">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-209">How to measure</span></span>

* <span data-ttu-id="c5fdf-210">No deben aparecer hologramas que se colocan en el mapa espacial drásticamente flotar encima o debajo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="c5fdf-211">Hologramas que requieren una colocación precisa deben tener algún tipo de marcador y calibración del sistema que es preciso hasta los requisitos del escenario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-212">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-212">Recommendations</span></span>

* <span data-ttu-id="c5fdf-213">Asignación espacial es útil para colocar objetos en superficies cuando la precisión no es necesaria.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="c5fdf-214">La mejor precisión, utilizar marcadores o pósters para establecer el hologramas y un controlador Xbox (o algún mecanismo de alineación manual) para la calibración final.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="c5fdf-215">Considere la posibilidad de dividir hologramas muy grandes en partes lógicas y alinear cada parte a la superficie.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="c5fdf-216">Incorrectamente conjunto interpupilary distancia (IPD) también puede afectar la alineación holograma.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="c5fdf-217">Configure siempre HoloLens en IPD del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-218">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-219">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-219">Documentation</span></span>

* [<span data-ttu-id="c5fdf-220">Selección de ubicación de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="c5fdf-221">Espacio de proceso de detección</span><span class="sxs-lookup"><span data-stu-id="c5fdf-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="c5fdf-222">Prácticas recomendadas de delimitadores espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="c5fdf-223">Seguimiento de control de errores</span><span class="sxs-lookup"><span data-stu-id="c5fdf-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="c5fdf-224">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="c5fdf-225">Introducción al desarrollo de Vuforia</span><span class="sxs-lookup"><span data-stu-id="c5fdf-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-226">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-226">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-227">MR Spatial 230: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="c5fdf-228">El Sr. Kit de herramientas, bibliotecas de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="c5fdf-229">MR complementaria Kit, ejemplo de calibración de póster</span><span class="sxs-lookup"><span data-stu-id="c5fdf-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="c5fdf-230">El Sr. complementaria Kit, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="c5fdf-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="c5fdf-231">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-231">External references</span></span>

* [<span data-ttu-id="c5fdf-232">Caso práctico de Lowes, alineación de precisión</span><span class="sxs-lookup"><span data-stu-id="c5fdf-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="c5fdf-233">Visualización de zona de comodidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-233">Viewing zone of comfort</span></span>

<span data-ttu-id="c5fdf-234">Control de los desarrolladores de aplicaciones donde convergen los ojos de los usuarios mediante la colocación de contenido y hologramas en diversos profundidades.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="c5fdf-235">Los usuarios gastando de HoloLens siempre se alojará a m 2.0 para mantener una imagen clara porque muestra de HoloLens se fija en una distancia óptica aproximadamente 2.0m alejándose del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="c5fdf-236">Profundidad de contenido incorrecto puede provocar fatiga ni incomodidad visual.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-237">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-239"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-240">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-240">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-241">❌</span><span class="sxs-lookup"><span data-stu-id="c5fdf-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-242">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="c5fdf-243">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="c5fdf-244">Colocar contenido en 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-244">Place content at 2m.</span></span></li><li><span data-ttu-id="c5fdf-245">Cuando no se puede colocar hologramas en 2 minutos y no se puede evitar conflictos entre la convergencia y alojamiento, es la zona de colocación holograma óptimo entre 1,25 y 5 millones.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="c5fdf-246">En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios interactúen más de 1 m de distancia (por ejemplo, ajustar el tamaño del contenido y predeterminado de los parámetros de colocación).</span><span class="sxs-lookup"><span data-stu-id="c5fdf-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="c5fdf-247">A menos que específicamente no es necesario según el escenario, un plano de recorte debe implementar con fadeout comenzando en 1 millón.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="c5fdf-248">En casos donde se requiere una observación más cerca de un holograma inmóvil, el contenido no debe ser menor que 50cm.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="c5fdf-249">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-249">Meets</span></span></td><td> <span data-ttu-id="c5fdf-250">Está contenido dentro de la Guía de movimiento y de visualización, pero uso incorrecto o no utiliza el plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c5fdf-251">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-251">Fail</span></span> </td><td> <span data-ttu-id="c5fdf-252">El contenido se presenta demasiado cerca (normalmente &lt;1.25 m, o &lt;50 cm para estacionarios hologramas que requieren más cerca de observación.)</span><span class="sxs-lookup"><span data-stu-id="c5fdf-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-253">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-253">How to measure</span></span>

* <span data-ttu-id="c5fdf-254">Contenido deberían normalmente tener 2m ausente, pero no más cerca que más de 5m o 1,25.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="c5fdf-255">Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en .85CM con fadeout empezando por 1m de contenido.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="c5fdf-256">Enfocar el contenido y tenga en cuenta el efecto del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="c5fdf-257">Contenido estático no debe estar más cerca que 50cm ausente.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-258">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-258">Recommendations</span></span>

* <span data-ttu-id="c5fdf-259">Diseñar el contenido de la distancia óptima de 2 minutos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="c5fdf-260">Establece la distancia de la representación de recorte en 85cm con fadeout empezando por 1m de contenido.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="c5fdf-261">Para hologramas estacionarios que necesitan más cerca de visualización, el plano de recorte debe ser no menos de 30cm y fadeout debe empezar al menos 10cm fuera del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-262">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-262">Resources</span></span>

* [<span data-ttu-id="c5fdf-263">Representar distancia</span><span class="sxs-lookup"><span data-stu-id="c5fdf-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="c5fdf-264">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="c5fdf-265">Experimentar con escala</span><span class="sxs-lookup"><span data-stu-id="c5fdf-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="c5fdf-266">Texto, tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="c5fdf-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="c5fdf-267">Cambio de profundidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-267">Depth switching</span></span>

<span data-ttu-id="c5fdf-268">Independientemente de la zona de visualización de los problemas de comodidad, exige el usuario puede cambiar con frecuencia o rápidamente entre casi y ahora focal objetos (incluidos hologramas y contenido del mundo real) pueden dar lugar a fatiga oculomotor y malestar general.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-269">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-271"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-272">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-272">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-273">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-274">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-274">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-275">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-275">Best</span></span>  |  <span data-ttu-id="c5fdf-276">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-276">Meets</span></span> |  <span data-ttu-id="c5fdf-277">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-278">Profundidad natural o limitada de conmutación no hace que se reenfocar al usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="c5fdf-279">Conmutador de profundidad abrupta es el núcleo y diseñadas en la experiencia de aplicación, o conmutador de profundidad abrupta producida por el contenido real-world inesperado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="c5fdf-280">Conmutador de profundidad coherente, o cambio brusco profundidad que no es necesario o core a la experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-281">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-281">How to measure</span></span>

* <span data-ttu-id="c5fdf-282">Si la aplicación requiere que el usuario para constantemente o repentinamente cambiar el foco de profundidad, no hay profundidad cambiar el problema.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-283">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-283">Recommendations</span></span>

* <span data-ttu-id="c5fdf-284">Mantener el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="c5fdf-285">Alivie oculomotor fatiga y movimiento holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-286">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-286">Resources</span></span>

* [<span data-ttu-id="c5fdf-287">Representar distancia</span><span class="sxs-lookup"><span data-stu-id="c5fdf-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="c5fdf-288">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="c5fdf-289">Uso de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-289">Use of spatial sound</span></span>

<span data-ttu-id="c5fdf-290">En Windows Mixed Reality, el motor de audio proporciona el componente de la experiencia de realidad mixta auditiva simulando 3D sonido con simulaciones del entorno, la distancia y dirección.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="c5fdf-291">Usar sonido espacial en una aplicación permite a los desarrolladores colocar convincingly sonidos en un espacio dimensional 3 (esfera) en todo el usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="c5fdf-292">Los sonidos, a continuación, le resultará como si provinieran objetos físicos real o la hologramas realidad mixta en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="c5fdf-293">Sonido espacial es una herramienta eficaz para inmersión, accesibilidad y diseño de la experiencia de usuario en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-294">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-296"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-297">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-297">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-298">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-299">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-299">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-300">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-300">Best</span></span>  |  <span data-ttu-id="c5fdf-301">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-301">Meets</span></span> |  <span data-ttu-id="c5fdf-302">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-303">Lógicamente es spatialized sonido y la experiencia de usuario adecuadamente usa sonido para ayudar a los comentarios de usuario y la detección de objeto.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="c5fdf-304">Sonido es natural y relevantes para los objetos y normalizado en el escenario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="c5fdf-305">Audio espacial es usado correctamente para believability pero no se encuentra como medio para facilitar la detectabilidad y comentarios del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="c5fdf-306">No se spatialized sonido según lo esperado, o falta de sonido para ayudar a los usuarios de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="c5fdf-307">O bien, no se considera o se usan en el diseño del escenario de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-308">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-308">How to measure</span></span>

* <span data-ttu-id="c5fdf-309">En general, deben emitir sonidos relevantes de hologramas de destino (ej., sonido corteza procedentes de perro holográfica.)</span><span class="sxs-lookup"><span data-stu-id="c5fdf-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="c5fdf-310">Las indicaciones de sonido deben usarse en toda la experiencia de usuario para ayudar al usuario con comentarios ni el conocimiento de las acciones fuera del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-311">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-311">Recommendations</span></span>

* <span data-ttu-id="c5fdf-312">Utilice audio espacial para ayudar con interfaces de usuario y la detección del objeto.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="c5fdf-313">Sonidos real funcionan mejor que síntesis o sonido no natural.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="c5fdf-314">Debe ser spatialized mayoría de los sonidos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="c5fdf-315">Evite los emisores invisibles.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="c5fdf-316">Evite enmascaramiento espacial.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="c5fdf-317">Normalizar todos los sonidos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-318">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-319">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-319">Documentation</span></span>

* [<span data-ttu-id="c5fdf-320">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="c5fdf-321">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="c5fdf-322">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="c5fdf-323">Caso práctico de sonido para HoloTour espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="c5fdf-324">Caso práctico, usar sonido espacial en RoboRaid</span><span class="sxs-lookup"><span data-stu-id="c5fdf-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-325">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-325">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-326">MR Spatial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="c5fdf-327">MRToolkit, Audio espacial</span><span class="sxs-lookup"><span data-stu-id="c5fdf-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="c5fdf-328">Centrarse en los límites del marco holográfica (FOV)</span><span class="sxs-lookup"><span data-stu-id="c5fdf-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="c5fdf-329">Experiencias de usuario bien diseñada pueden crear y mantener un contexto útil del entorno virtual que se extiende en torno a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="c5fdf-330">Mitigar el efecto de los límites FOV implica un diseño concienzudo de escalado de contenido y el contexto, el uso de audio espacial, sistemas de orientación y la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="c5fdf-331">Si se hace correctamente, el usuario se sentirán como menor afectadas por los límites del campo visual al tiempo que tiene una experiencia de aplicación cómodo.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-332">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-334"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-335">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-335">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-336">❌</span><span class="sxs-lookup"><span data-stu-id="c5fdf-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-337">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-337">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-338">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-338">Best</span></span>  |  <span data-ttu-id="c5fdf-339">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-339">Meets</span></span> |  <span data-ttu-id="c5fdf-340">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-341">Usuario nunca pierde el contexto y se siente cómodo ver.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="c5fdf-342">Se proporciona ayuda contextual para los objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="c5fdf-343">Detectabilidad y ver la guía se proporcionan para los objetos fuera del marco.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="c5fdf-344">En general, el diseño de movimiento y la escala de la hologramas son adecuados para una experiencia de visualización cómoda.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="c5fdf-345">Usuario nunca pierde el contexto, pero es posible que deban movimiento cuello adicional en ciertas situaciones.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="c5fdf-346">En ciertas situaciones escalado hace hologramas para interrumpir en el marco vertical u horizontal, causando ciertos movimientos cuello ver hologramas.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="c5fdf-347">Usuario que puede perder contexto o movimiento cuello coherente se requiere para ver hologramas.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="c5fdf-348">Ninguna instrucción de contexto para objetos holográficas grandes, mover objetos fáciles de perder fuera del marco sin instrucciones de detectabilidad ni hologramas altos requiere movimiento cuello regulares para ver.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-349">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-349">How to measure</span></span>

* <span data-ttu-id="c5fdf-350">Contexto para un holograma (grande) se pierde o no entiende debido a que se recorta por los límites.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="c5fdf-351">Ubicación de hologramas son difíciles de encontrar debido a la falta de directores de atención o contenido que entra y sale rápidamente el marco holográfico.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="c5fdf-352">Escenario requiere repetitivas y reducir verticalmente un movimiento principal para ver por completo un holograma resultante en fatiga cuello y regular.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-353">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-353">Recommendations</span></span>

* <span data-ttu-id="c5fdf-354">La experiencia de inicio con objetos pequeños que ajustar el campo visual y, después, realizar la transición con indicaciones visuales a las versiones más grandes.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="c5fdf-355">Use espaciales directores de audio y atención para la búsqueda de contenido de usuario que está fuera del campo visual.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="c5fdf-356">Cuando sea posible, evite hologramas que recortar verticalmente el campo visual.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="c5fdf-357">Proporcionar al usuario con instrucciones de la aplicación para ver la ubicación de mejor.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-358">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-359">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-359">Documentation</span></span>

* [<span data-ttu-id="c5fdf-360">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="c5fdf-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="c5fdf-361">Caso práctico, HoloStudio UI y conocimientos de diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="c5fdf-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="c5fdf-362">Escalado de objetos y entornos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="c5fdf-363">Cursores, indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="c5fdf-364">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-364">External references</span></span>

* [<span data-ttu-id="c5fdf-365">El campo visual con ado</span><span class="sxs-lookup"><span data-stu-id="c5fdf-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="c5fdf-366">Contenido reacciona a la posición del usuario</span><span class="sxs-lookup"><span data-stu-id="c5fdf-366">Content reacts to user position</span></span>

<span data-ttu-id="c5fdf-367">Hologramas deben reaccionar ante el usuario coloque en aproximadamente la misma forma que los objetos de "real".</span><span class="sxs-lookup"><span data-stu-id="c5fdf-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="c5fdf-368">Una consideración de diseño importantes es elementos de interfaz de usuario que no se pueden suponer necesariamente la posición de un usuario esté parados y adaptar y movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="c5fdf-369">Diseñar una aplicación que correctamente se adapta a la posición del usuario creará una experiencia más solo y que sea más fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-370">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-372"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-373">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-373">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-374">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-375">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="c5fdf-376">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-376">Best</span></span> </td><td> <span data-ttu-id="c5fdf-377">Contenido y la interfaz de usuario se adaptan a las posiciones de usuario que permite usuario interactúen de forma natural con contenido dentro del ámbito de movimiento de usuario esperado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c5fdf-378">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-378">Meets</span></span> </td><td> <span data-ttu-id="c5fdf-379">Interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave pedir al usuario que ajustan su posición.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c5fdf-380">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="c5fdf-381">Elementos de interfaz de usuario se pierde o se bloquea durante el usuario que causan de movimiento que se vuelva a controles (o busque).</span><span class="sxs-lookup"><span data-stu-id="c5fdf-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="c5fdf-382">Elementos de interfaz de usuario limitan la vista de contenido principal.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="c5fdf-383">Movimiento de la interfaz de usuario no está optimizado para la visualización de distancia y momentum especialmente con <a href="billboarding-and-tag-along.md">tag-along</a> elementos de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-384">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-384">How to measure</span></span>

* <span data-ttu-id="c5fdf-385">Todas las mediciones deben realizarse dentro de un ámbito razonable del escenario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="c5fdf-386">Aunque puede variar el movimiento de usuario, no intente engañar a la aplicación con el movimiento de usuario extreme.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="c5fdf-387">Para los elementos de interfaz de usuario, los controles relevantes deben estar disponibles, independientemente del movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="c5fdf-388">Por ejemplo, si el usuario está viendo y caminar alrededor de un mapa 3D con zoom, el control de zoom debe ser estén disponible para el usuario independientemente de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-389">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-389">Recommendations</span></span>

* <span data-ttu-id="c5fdf-390">El usuario es la cámara y controlan el movimiento.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="c5fdf-391">Deje que su unidad.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-391">Let them drive.</span></span>
* <span data-ttu-id="c5fdf-392">Considere la posibilidad de vallas publicitarias para texto y sistemas trabajé que de lo contrario serían bloqueado por el mundo u oculta si un usuario tuviera que desplazarse.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="c5fdf-393">Usar tag-along para el contenido que debe seguir al usuario mientras sigue permitiendo que el usuario ver lo que está delante de ellas.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-394">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-395">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-395">Documentation</span></span>

* [<span data-ttu-id="c5fdf-396">Diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="c5fdf-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="c5fdf-397">Color de luz y material</span><span class="sxs-lookup"><span data-stu-id="c5fdf-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="c5fdf-398">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="c5fdf-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c5fdf-399">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c5fdf-400">El movimiento y el desplazamiento del usuario</span><span class="sxs-lookup"><span data-stu-id="c5fdf-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-401">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-401">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-402">MR Input 210: mirada</span><span class="sxs-lookup"><span data-stu-id="c5fdf-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="c5fdf-403">Claridad de interacción de entrada</span><span class="sxs-lookup"><span data-stu-id="c5fdf-403">Input interaction clarity</span></span>

<span data-ttu-id="c5fdf-404">Claridad de interacción de entrada es fundamental para la facilidad de uso de una aplicación e incluye la entrada coherencia, innegables, detectabilidad de los métodos de interacción.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="c5fdf-405">Usuario debería poder usar las interacciones habituales de toda la plataforma sin volver a aprender.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="c5fdf-406">Si la aplicación tiene parámetros de entrada personalizado, se debe claramente comunicar y demostrar.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-407">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-409"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-410">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-410">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-411">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-412">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-412">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-413">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-413">Best</span></span>  |  <span data-ttu-id="c5fdf-414">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-414">Meets</span></span> |  <span data-ttu-id="c5fdf-415">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-416">Métodos de entrada de interacción son coherentes con Windows Mixed Reality proporcionado [orientación](interaction-fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="c5fdf-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="c5fdf-417">Cualquier entrada personalizada no debería ser redundante con la entrada estándar (en su lugar use interacción estándar) y debe claramente comunicar y demostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="c5fdf-418">Es similar a las entradas mejor, pero personalizadas son redundantes con métodos de entrada estándares.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="c5fdf-419">Usuario todavía puede lograr el objetivo y el progreso a través de la experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="c5fdf-420">Difíciles de comprender la asignación de botón o el método de entrada.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="c5fdf-421">Input personalizado en gran medida, no es compatible con la entrada estándar, no hay instrucciones, o puede provocar problemas de fatiga y comodidad.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-422">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-422">How to measure</span></span>

* <span data-ttu-id="c5fdf-423">La aplicación usa coherente [métodos de entrada estándar.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="c5fdf-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="c5fdf-424">Si la aplicación tiene parámetros de entrada personalizados, claramente se comunique a través de:</span><span class="sxs-lookup"><span data-stu-id="c5fdf-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="c5fdf-425">Experiencia de primera ejecución</span><span class="sxs-lookup"><span data-stu-id="c5fdf-425">First-run experience</span></span>
* <span data-ttu-id="c5fdf-426">Pantallas de presentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-426">Introductory screens</span></span>
* <span data-ttu-id="c5fdf-427">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-427">Tooltips</span></span>
* <span data-ttu-id="c5fdf-428">Instructora de mano</span><span class="sxs-lookup"><span data-stu-id="c5fdf-428">Hand coach</span></span>
* <span data-ttu-id="c5fdf-429">Sección de ayuda</span><span class="sxs-lookup"><span data-stu-id="c5fdf-429">Help section</span></span>
* <span data-ttu-id="c5fdf-430">VoiceOver</span><span class="sxs-lookup"><span data-stu-id="c5fdf-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-431">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-431">Recommendations</span></span>

* <span data-ttu-id="c5fdf-432">Utilice los métodos de entrada estándares siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="c5fdf-433">Proporcionar información sobre herramientas, tutoriales y demostraciones para métodos de entrada no estándares.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="c5fdf-434">Usar un modelo de interacción coherente en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-435">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-436">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-436">Documentation</span></span>

* [<span data-ttu-id="c5fdf-437">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="c5fdf-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="c5fdf-438">Objetos interactuable</span><span class="sxs-lookup"><span data-stu-id="c5fdf-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="c5fdf-439">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="c5fdf-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="c5fdf-440">Cursores</span><span class="sxs-lookup"><span data-stu-id="c5fdf-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c5fdf-441">Comodidad y mirada</span><span class="sxs-lookup"><span data-stu-id="c5fdf-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="c5fdf-442">Gestos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="c5fdf-443">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="c5fdf-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="c5fdf-444">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="c5fdf-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="c5fdf-445">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="c5fdf-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="c5fdf-446">Guía de portabilidad de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="c5fdf-447">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="c5fdf-448">Mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="c5fdf-449">Gestos y controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="c5fdf-450">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="c5fdf-451">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="c5fdf-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="c5fdf-452">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="c5fdf-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="c5fdf-453">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="c5fdf-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="c5fdf-454">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="c5fdf-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-455">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-455">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-456">Caso práctico: La búsqueda de informática más personal</span><span class="sxs-lookup"><span data-stu-id="c5fdf-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="c5fdf-457">Estudio de conversión: HoloStudio UI y conocimientos de diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="c5fdf-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="c5fdf-458">Aplicación de ejemplo: Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="c5fdf-459">Aplicación de ejemplo: Módulo lunar</span><span class="sxs-lookup"><span data-stu-id="c5fdf-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="c5fdf-460">MR Input 210: mirada</span><span class="sxs-lookup"><span data-stu-id="c5fdf-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="c5fdf-461">MR Input 211: Gestos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="c5fdf-462">MR Input 212: voz</span><span class="sxs-lookup"><span data-stu-id="c5fdf-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="c5fdf-463">Objetos interactuable</span><span class="sxs-lookup"><span data-stu-id="c5fdf-463">Interactable objects</span></span>

<span data-ttu-id="c5fdf-464">Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="c5fdf-465">En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="c5fdf-466">Nada puede ser un objeto Interactuable que desencadena un evento.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="c5fdf-467">Un objeto interactuable puede representarse como nada una taza de café en la tabla a un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="c5fdf-468">Independientemente del formulario, objetos interactuable deben ser claramente reconocibles por el usuario a través de las pistas de audio y visuales.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-469">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-471"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-472">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-472">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-473">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-474">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-474">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-475">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-475">Best</span></span>  |  <span data-ttu-id="c5fdf-476">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-476">Meets</span></span> |  <span data-ttu-id="c5fdf-477">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-478">Independientemente del formulario, objetos interactuable sean reconocibles a través de las indicaciones visuales y de audio a través de tres estados: inactivo, destinado y seleccionada.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="c5fdf-479">"Vea, diga" claro y coherente sirve a lo largo de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="c5fdf-480">Los objetos se escala y se distribuyen para permitir errores como destino.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="c5fdf-481">Usuario puede reconocer el objeto como interactuable a través de comentarios de audio o el objeto visual y puede tener como destino y activar el objeto.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="c5fdf-482">No dada indicaciones visuales o audio, usuario no puede reconocer un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="c5fdf-483">Las interacciones son propensas a errores debido a la escala del objeto o la distancia entre los objetos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-484">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-484">How to measure</span></span>

* <span data-ttu-id="c5fdf-485">Objetos interactuable son reconocibles como 'interactuable'; incluyendo contenido específico de los botones, menús y la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="c5fdf-486">Como regla general debería haber una pista de audio y visual cuando tenga como destino objetos interactuable.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-487">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-487">Recommendations</span></span>

* <span data-ttu-id="c5fdf-488">Usar comentarios visuales y de audio para las interacciones.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="c5fdf-489">Comentarios visuales es diferente para cada entrada de estado (inactivo, destino, seleccionado)</span><span class="sxs-lookup"><span data-stu-id="c5fdf-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="c5fdf-490">Deben ser escalar y colocan por error libre como destino objetos interactuable.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="c5fdf-491">Los objetos agrupados interactuable (por ejemplo, una barra de menús o lista) deben tener espacio adecuado para dirigirse a.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="c5fdf-492">Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto de la palabra clave de comando ("verlo, diga")</span><span class="sxs-lookup"><span data-stu-id="c5fdf-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-493">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-494">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-494">Documentation</span></span>

* [<span data-ttu-id="c5fdf-495">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="c5fdf-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c5fdf-496">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="c5fdf-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="c5fdf-497">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c5fdf-498">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="c5fdf-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-499">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-499">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-500">Kit de herramientas de realidad mixta - UX</span><span class="sxs-lookup"><span data-stu-id="c5fdf-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="c5fdf-501">Sala de análisis</span><span class="sxs-lookup"><span data-stu-id="c5fdf-501">Room scanning</span></span>

<span data-ttu-id="c5fdf-502">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="c5fdf-503">La integridad y la calidad de los datos depende de varios factores como la cantidad de exploración, el usuario ha hecho, ¿cuánto tiempo ha transcurrido desde la exploración y si objetos como muebles y puertas movido desde que el dispositivo había analizado el área.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="c5fdf-504">Muchas aplicaciones analizará los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad de la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="c5fdf-505">Si el usuario es necesario para analizar el entorno, desactive le proporcionará instrucciones durante la experiencia de exploración.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-506">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-508"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-509">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-509">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-510">❌</span><span class="sxs-lookup"><span data-stu-id="c5fdf-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-511">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-511">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-512">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-512">Best</span></span>  |  <span data-ttu-id="c5fdf-513">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-513">Meets</span></span> |  <span data-ttu-id="c5fdf-514">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-515">Visualización de la malla espacial indique a los usuarios análisis está en curso.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="c5fdf-516">Usuario claramente sabe qué hacer y cuando se inicia y detiene el análisis.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="c5fdf-517">Se proporciona la visualización de la malla espacial, pero el usuario puede saber con claridad qué hacer y se proporciona ninguna información de progreso.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="c5fdf-518">No hay ninguna visualización de malla.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-518">No visualization of mesh.</span></span> <span data-ttu-id="c5fdf-519">No se proporciona al usuario sobre dónde buscar o cuando el examen se inicia o detiene la información de orientación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-520">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-520">How to measure</span></span>

* <span data-ttu-id="c5fdf-521">Durante un examen de espacio necesaria, se proporciona orientación de audio y visual que indica dónde buscar y cuándo se debe iniciar y detener análisis.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-522">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-522">Recommendations</span></span>

* <span data-ttu-id="c5fdf-523">Indicar cuánto volumen total, en la proximidad de los usuarios debe formar parte de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="c5fdf-524">Cuando el examen se inicia y detiene como un indicador de progreso se comunican.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="c5fdf-525">Usar una visualización de la malla durante el análisis.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="c5fdf-526">Proporcionar indicaciones visuales y de audio para fomentar que usuario examinar y desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="c5fdf-527">Informar al usuario dónde debe ir para mejorar los datos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="c5fdf-528">En muchos casos, puede ser mejor indicar que el usuario lo que necesitan (por ejemplo, examine el límite superior, busque detrás de muebles), con el fin de obtener la calidad del análisis necesarios.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-529">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5fdf-530">Documentación</span><span class="sxs-lookup"><span data-stu-id="c5fdf-530">Documentation</span></span>

* [<span data-ttu-id="c5fdf-531">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="c5fdf-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="c5fdf-532">Caso práctico: Expandir las capacidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="c5fdf-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="c5fdf-533">Caso práctico: Diseño espacial de sonido para HoloTour</span><span class="sxs-lookup"><span data-stu-id="c5fdf-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="c5fdf-534">Caso práctico: Creación de una experiencia realmente cautivadora en fragmentos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5fdf-535">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-535">Tools and tutorials</span></span>

* [<span data-ttu-id="c5fdf-536">Kit de herramientas de realidad mixta - UX</span><span class="sxs-lookup"><span data-stu-id="c5fdf-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="c5fdf-537">Indicadores direccionales</span><span class="sxs-lookup"><span data-stu-id="c5fdf-537">Directional indicators</span></span>

<span data-ttu-id="c5fdf-538">En una aplicación de realidad mixta, el contenido puede estar fuera del campo de visión u ocluyeron en objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="c5fdf-539">Una aplicación bien diseñada le resultará más fácil para el usuario buscar el contenido que no sea visible.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="c5fdf-540">Indicadores direccionales alertar a un usuario al contenido importante y asesoramiento sobre el contenido en relación con la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="c5fdf-541">Guía de contenido que no sea visible puede adoptar la forma de los emisores de sonido, flechas direccionales o indicaciones visuales directas.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-542">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-544"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-545">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-545">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-546">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-547">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-547">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-548">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-548">Best</span></span>  |  <span data-ttu-id="c5fdf-549">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-549">Meets</span></span> |  <span data-ttu-id="c5fdf-550">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-551">Indicaciones visuales y de audio directamente guiar al usuario al contenido pertinente fuera el campo de visión.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="c5fdf-552">Una flecha o algún indicador que señala al usuario en la dirección general del contenido.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="c5fdf-553">Contenido relevante está fuera del campo de visión y deficiente o ninguna Guía de ubicación se proporciona al usuario.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-554">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-554">How to measure</span></span>

* <span data-ttu-id="c5fdf-555">Contenido relevante fuera del campo de vista de usuario es reconocible a través de las indicaciones visuales o audio.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-556">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-556">Recommendations</span></span>

* <span data-ttu-id="c5fdf-557">Cuando contenido relevante está fuera del campo de visión del usuario, utilice indicadores direccionales y pistas de sonido para guiar al usuario al contenido.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="c5fdf-558">En muchos casos, se prefiere una guía visual directa a través de las flechas direccionales.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="c5fdf-559">Indicadores direccionales no deben generarse en el cursor.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-560">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-560">Resources</span></span>

* [<span data-ttu-id="c5fdf-561">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="c5fdf-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="c5fdf-562">Carga de datos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-562">Data loading</span></span>

<span data-ttu-id="c5fdf-563">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="c5fdf-564">Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto podría ser el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5fdf-565">Impacto de dispositivo</span><span class="sxs-lookup"><span data-stu-id="c5fdf-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5fdf-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5fdf-567"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5fdf-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5fdf-568">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-568">✔️</span></span></td>
        <td><span data-ttu-id="c5fdf-569">✔️</span><span class="sxs-lookup"><span data-stu-id="c5fdf-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5fdf-570">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="c5fdf-570">Quality criteria</span></span>

|  <span data-ttu-id="c5fdf-571">Mejor</span><span class="sxs-lookup"><span data-stu-id="c5fdf-571">Best</span></span>  |  <span data-ttu-id="c5fdf-572">Cumple</span><span class="sxs-lookup"><span data-stu-id="c5fdf-572">Meets</span></span> |  <span data-ttu-id="c5fdf-573">un error</span><span class="sxs-lookup"><span data-stu-id="c5fdf-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5fdf-574">Anima el indicador visual, en forma de una barra de progreso o anillo, que muestra el progreso durante cualquier dato cargando o procesando.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="c5fdf-575">El indicador visual proporciona orientación sobre cuánto podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="c5fdf-576">Se informa al usuario que la carga de datos está en curso, pero no hay ninguna indicación de cuánto podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="c5fdf-577">No hay carga de datos o indicadores de proceso de tarea tarda más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5fdf-578">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="c5fdf-578">How to measure</span></span>

* <span data-ttu-id="c5fdf-579">Compruebe que no hay ningún estado en blanco durante más de 5 segundos durante la carga de datos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5fdf-580">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="c5fdf-580">Recommendations</span></span>

* <span data-ttu-id="c5fdf-581">Proporcione una animación de la carga de datos muestra el progreso en cualquier situación cuando el usuario puede percibir esta aplicación se ha detenido o se ha bloqueado.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="c5fdf-582">Una regla general razonable es cualquier actividad "Cargando" que podría tardar más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="c5fdf-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="c5fdf-583">Recursos</span><span class="sxs-lookup"><span data-stu-id="c5fdf-583">Resources</span></span>

* [<span data-ttu-id="c5fdf-584">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="c5fdf-584">Displaying progress</span></span>](progress.md)
