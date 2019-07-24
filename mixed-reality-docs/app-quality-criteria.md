---
title: Criterios de calidad de la aplicación
description: En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: Criterios de calidad de la aplicación, realidad mixta, aplicación de realidad mixta
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024493"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="f3f01-104">Criterios de calidad de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f3f01-104">App quality criteria</span></span>

<span data-ttu-id="f3f01-105">En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f3f01-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="f3f01-106">Para cada factor se proporciona la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="f3f01-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="f3f01-107">Información general: breve descripción del factor de calidad y por qué es importante.</span><span class="sxs-lookup"><span data-stu-id="f3f01-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="f3f01-108">Impacto en el dispositivo: Qué tipo de dispositivo de realidad mixta de ventana se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="f3f01-109">Criterios de calidad: Cómo evaluar el factor de calidad.</span><span class="sxs-lookup"><span data-stu-id="f3f01-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="f3f01-110">Cómo medir: métodos para medir (o experimentar) el problema.</span><span class="sxs-lookup"><span data-stu-id="f3f01-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="f3f01-111">Recomendaciones: Resumen de los enfoques para proporcionar una mejor experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="f3f01-112">Recursos: recursos de desarrollador y diseño relevantes que son útiles para crear mejores experiencias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="f3f01-113">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="f3f01-113">Frame rate</span></span>

<span data-ttu-id="f3f01-114">La velocidad de fotogramas es el primer pilar de estabilidad del holograma y la comodidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="f3f01-115">La velocidad de fotogramas por debajo de los objetivos recomendados puede hacer que los hologramas parezcan vibrantes, lo que afecta negativamente a la increíble potencia de la experiencia y, potencialmente, a la fatiga ocular.</span><span class="sxs-lookup"><span data-stu-id="f3f01-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="f3f01-116">La velocidad de fotogramas de destino para su experiencia en los auriculares de la realidad mixta de Windows será de 60Hz o 90Hz, según los equipos compatibles con Windows Mixed Reality que desee admitir.</span><span class="sxs-lookup"><span data-stu-id="f3f01-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="f3f01-117">Para HoloLens, la velocidad de fotogramas de destino es 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="f3f01-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-118">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-120"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-121">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-122">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-123">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-123">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-124">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-124">Best</span></span>  |  <span data-ttu-id="f3f01-125">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-125">Meets</span></span> |  <span data-ttu-id="f3f01-126">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="f3f01-127">La aplicación cumple de forma coherente el objetivo de fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en ultra PCs; y 60fps en equipos estándar.</span><span class="sxs-lookup"><span data-stu-id="f3f01-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="f3f01-128">La aplicación tiene caídas de fotogramas intermitentes que no impiden la experiencia básica; o FPS es constantemente inferior al objetivo deseado, pero no impide la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="f3f01-129">La aplicación está experimentando una caída en la velocidad de fotogramas como promedio cada diez segundos o menos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-130">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-130">How to measure</span></span>

* <span data-ttu-id="f3f01-131">El [portal de dispositivos de Windows](using-the-windows-device-portal.md#system-performance) proporciona un gráfico de velocidad de fotogramas en tiempo real en "rendimiento del sistema".</span><span class="sxs-lookup"><span data-stu-id="f3f01-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="f3f01-132">Para la depuración de desarrollo, agregue un contador de diagnóstico de velocidad de fotogramas a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="f3f01-133">Vea recursos para obtener un contador de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="f3f01-134">Las caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras la aplicación se está ejecutando moviendo el encabezado de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="f3f01-135">Si el holograma muestra un movimiento de vibración inesperado, es probable que la velocidad de fotogramas baja o el plano de estabilidad sea la causa.</span><span class="sxs-lookup"><span data-stu-id="f3f01-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-136">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-136">Recommendations</span></span>

* <span data-ttu-id="f3f01-137">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="f3f01-138">Los cambios que incurren en una caída en la velocidad de fotogramas se deben evaluar y resolver correctamente como un error de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="f3f01-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-140">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-140">Documentation</span></span>

* [<span data-ttu-id="f3f01-141">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f3f01-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f3f01-142">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="f3f01-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="f3f01-143">Presupuesto de rendimiento de activos</span><span class="sxs-lookup"><span data-stu-id="f3f01-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="f3f01-144">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-145">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-145">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-146">MRToolkit, pantalla de contador de FPS</span><span class="sxs-lookup"><span data-stu-id="f3f01-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="f3f01-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="f3f01-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="f3f01-148">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="f3f01-148">External references</span></span>

* [<span data-ttu-id="f3f01-149">Unity, optimizar aplicaciones móviles</span><span class="sxs-lookup"><span data-stu-id="f3f01-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="f3f01-150">Estabilidad de holograma</span><span class="sxs-lookup"><span data-stu-id="f3f01-150">Hologram stability</span></span>

<span data-ttu-id="f3f01-151">Los hologramas estables aumentarán la facilidad de uso y la increíble capacidad de su aplicación, y crearán una experiencia de visualización más cómoda para el usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="f3f01-152">La calidad de la estabilidad del holograma es el resultado de un buen desarrollo de la aplicación y la capacidad del dispositivo para comprender (realizar un seguimiento) de su entorno.</span><span class="sxs-lookup"><span data-stu-id="f3f01-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="f3f01-153">Aunque la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar a la estabilidad, como:</span><span class="sxs-lookup"><span data-stu-id="f3f01-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="f3f01-154">Uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="f3f01-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="f3f01-155">Distancia a los delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="f3f01-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="f3f01-156">Llevar</span><span class="sxs-lookup"><span data-stu-id="f3f01-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-157">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-159"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-160">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-160">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-161">❌</span><span class="sxs-lookup"><span data-stu-id="f3f01-161">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-162">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-162">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-163">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-163">Best</span></span>  |  <span data-ttu-id="f3f01-164">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-164">Meets</span></span> |  <span data-ttu-id="f3f01-165">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-165">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-166">Los hologramas aparecen de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="f3f01-166">Holograms consistently appear stable.</span></span> | <span data-ttu-id="f3f01-167">El contenido secundario exhibe un movimiento inesperado. o el movimiento inesperado no impide la experiencia general de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-167">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="f3f01-168">El contenido principal del marco exhibe un movimiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-168">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-169">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-169">How to measure</span></span>

<span data-ttu-id="f3f01-170">Con el dispositivo y la visualización de la experiencia:</span><span class="sxs-lookup"><span data-stu-id="f3f01-170">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="f3f01-171">Mover el encabezado de lado a lado, si los hologramas muestran un movimiento inesperado, la velocidad de fotogramas baja o la alineación incorrecta del plano de estabilidad al plano focal es la causa probable.</span><span class="sxs-lookup"><span data-stu-id="f3f01-171">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="f3f01-172">Desplazarse por los hologramas y el entorno, busque comportamientos como nadar y salto.</span><span class="sxs-lookup"><span data-stu-id="f3f01-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="f3f01-173">Este tipo de movimiento probablemente se debe a que el dispositivo no realiza un seguimiento del entorno o a la distancia al delimitador espacial.</span><span class="sxs-lookup"><span data-stu-id="f3f01-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="f3f01-174">Si hay varios hologramas en el marco, observe el comportamiento de holograma en varias profundidades al mover la posición principal de lado a lado, en caso de que la irregularidad parezca que esto se debe a un plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="f3f01-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="f3f01-175">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-175">Recomendations</span></span>

* <span data-ttu-id="f3f01-176">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-176">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="f3f01-177">Use el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="f3f01-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="f3f01-178">Siempre representa los hologramas anclados dentro de los 3 metros de su delimitador.</span><span class="sxs-lookup"><span data-stu-id="f3f01-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="f3f01-179">Asegúrese de que el entorno está configurado para el seguimiento adecuado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-179">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="f3f01-180">Diseñe su experiencia para evitar los hologramas en diversos niveles de profundidad focal dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="f3f01-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-181">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-182">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-182">Documentation</span></span>

* [<span data-ttu-id="f3f01-183">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="f3f01-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="f3f01-184">Caso práctico, uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="f3f01-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="f3f01-185">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f3f01-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="f3f01-186">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-186">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="f3f01-187">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="f3f01-187">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="f3f01-188">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-188">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="f3f01-189">Marco estacionario de referencia</span><span class="sxs-lookup"><span data-stu-id="f3f01-189">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-190">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-190">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-191">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="f3f01-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="f3f01-192">Posición de hologramas en superficies reales</span><span class="sxs-lookup"><span data-stu-id="f3f01-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="f3f01-193">Las alineaciones de los hologramas con objetos físicos (si se prevé que se colocarán en relación con otras) son una indicación clara de la no Unión de los hologramas y del mundo real.</span><span class="sxs-lookup"><span data-stu-id="f3f01-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="f3f01-194">La precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; por ejemplo, la selección de ubicación de superficie general puede usar el mapa espacial, pero la selección de ubicación más precisa requerirá el uso de marcadores y calibración.</span><span class="sxs-lookup"><span data-stu-id="f3f01-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-195">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-196"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-197"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-197"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-198">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-198">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-199">❌</span><span class="sxs-lookup"><span data-stu-id="f3f01-199">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-200">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-200">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-201">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-201">Best</span></span>  |  <span data-ttu-id="f3f01-202">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-202">Meets</span></span> |  <span data-ttu-id="f3f01-203">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-203">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="f3f01-204">Los hologramas se alinean a la superficie normalmente en el intervalo de centímetros a pulgadas.</span><span class="sxs-lookup"><span data-stu-id="f3f01-204">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="f3f01-205">Si se requiere más precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada.</span><span class="sxs-lookup"><span data-stu-id="f3f01-205">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="f3f01-206">N/D</span><span class="sxs-lookup"><span data-stu-id="f3f01-206">NA</span></span> | <span data-ttu-id="f3f01-207">Los hologramas aparecen sin alinear con el objeto de destino físico, ya que separan el plano de la superficie o parecen flotar fuera de la superficie.</span><span class="sxs-lookup"><span data-stu-id="f3f01-207">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="f3f01-208">Si se requiere precisión, los hologramas deben cumplir las especificaciones de proximidad del escenario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-208">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-209">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-209">How to measure</span></span>

* <span data-ttu-id="f3f01-210">Los hologramas que se colocan en el mapa espacial no deben parecer drásticamente por encima o por debajo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="f3f01-210">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="f3f01-211">Los hologramas que requieren una ubicación precisa deben tener algún tipo de sistema de marcadores y calibración que sea preciso para el requisito del escenario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-211">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-212">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-212">Recommendations</span></span>

* <span data-ttu-id="f3f01-213">El mapa espacial resulta útil para colocar objetos en superficies cuando no se requiere precisión.</span><span class="sxs-lookup"><span data-stu-id="f3f01-213">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="f3f01-214">Para obtener la mejor precisión, use marcadores o pósteres para establecer los hologramas y un controlador de Xbox (o algún mecanismo de alineación manual) para la calibración final.</span><span class="sxs-lookup"><span data-stu-id="f3f01-214">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="f3f01-215">Considere la posibilidad de dividir los hologramas extra grandes en partes lógicas y alinear cada parte en la superficie.</span><span class="sxs-lookup"><span data-stu-id="f3f01-215">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="f3f01-216">La Interpupilary distancia establecida correctamente (IPD) también puede afectar a la alineación de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="f3f01-216">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="f3f01-217">Configure siempre HoloLens en el del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-217">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-218">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-218">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-219">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-219">Documentation</span></span>

* [<span data-ttu-id="f3f01-220">Colocación de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-220">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="f3f01-221">Proceso de detección de salas</span><span class="sxs-lookup"><span data-stu-id="f3f01-221">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="f3f01-222">Procedimientos recomendados para los anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="f3f01-222">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="f3f01-223">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-223">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="f3f01-224">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-224">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="f3f01-225">Información general sobre el desarrollo de Vuforia</span><span class="sxs-lookup"><span data-stu-id="f3f01-225">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-226">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-226">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-227">MR Spatial 230: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-227">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="f3f01-228">Kit de herramientas de MR, bibliotecas de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-228">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="f3f01-229">Kit complementario MR, ejemplo de calibración de póster</span><span class="sxs-lookup"><span data-stu-id="f3f01-229">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="f3f01-230">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="f3f01-230">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="f3f01-231">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="f3f01-231">External references</span></span>

* [<span data-ttu-id="f3f01-232">Caso práctico de Lowes, alineación de precisión</span><span class="sxs-lookup"><span data-stu-id="f3f01-232">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="f3f01-233">Ver la zona de confort</span><span class="sxs-lookup"><span data-stu-id="f3f01-233">Viewing zone of comfort</span></span>

<span data-ttu-id="f3f01-234">Los desarrolladores de aplicaciones controlan el lugar en el que los usuarios convergen colocando contenido y hologramas a varias profundidades.</span><span class="sxs-lookup"><span data-stu-id="f3f01-234">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="f3f01-235">Los usuarios que contengan HoloLens siempre se acomodarán a 2,0 m para mantener una imagen clara porque las pantallas de HoloLens se fijan a una distancia óptica aproximadamente a 2,0 m del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-235">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="f3f01-236">Una profundidad de contenido incorrecta puede conducir a la molestia visual o a la fatiga.</span><span class="sxs-lookup"><span data-stu-id="f3f01-236">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-237">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-237">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-238"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-239"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-239"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-240">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-240">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-241">❌</span><span class="sxs-lookup"><span data-stu-id="f3f01-241">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-242">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-242">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="f3f01-243">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-243">Best</span></span> </td><td><ul>
<li><span data-ttu-id="f3f01-244">Coloque el contenido en 2m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-244">Place content at 2m.</span></span></li><li><span data-ttu-id="f3f01-245">Cuando los hologramas no se pueden colocar en 2m y no se pueden evitar conflictos entre convergencia y ajuste, la zona óptima para la colocación de hologramas se encuentra entre 1,25 m y 5 m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-245">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="f3f01-246">En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar con 1 + m (por ejemplo, ajustar el tamaño del contenido y los parámetros de ubicación predeterminados).</span><span class="sxs-lookup"><span data-stu-id="f3f01-246">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="f3f01-247">A menos que el escenario no requiera específicamente, se debe implementar un plano de recorte con fadeout a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-247">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="f3f01-248">En los casos en los que se requiere una observación más detallada de un holograma de motionless, el contenido no debe estar más cerca que 50CM.</span><span class="sxs-lookup"><span data-stu-id="f3f01-248">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="f3f01-249">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-249">Meets</span></span></td><td> <span data-ttu-id="f3f01-250">El contenido está dentro de la guía de visualización y movimiento, pero se usa inadecuadamente o no se usa el plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="f3f01-250">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f3f01-251">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-251">Fail</span></span> </td><td> <span data-ttu-id="f3f01-252">El contenido se presenta demasiado cerca ( &lt;normalmente 1,25 m o &lt;50CM para los hologramas estacionales que requieren una observación más detallada).</span><span class="sxs-lookup"><span data-stu-id="f3f01-252">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-253">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-253">How to measure</span></span>

* <span data-ttu-id="f3f01-254">Normalmente, el contenido debe ser de 2 m, pero no más cercano a 1,25 o superior a 5 m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-254">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="f3f01-255">Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en. 85CM con fadeout de contenido que empieza en 1m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-255">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="f3f01-256">Acerque el contenido y observe el efecto del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="f3f01-256">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="f3f01-257">El contenido estacionario no debe estar más cerca de 50CM.</span><span class="sxs-lookup"><span data-stu-id="f3f01-257">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-258">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-258">Recommendations</span></span>

* <span data-ttu-id="f3f01-259">Diseñe el contenido para obtener la distancia de visualización óptima de 2 m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-259">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="f3f01-260">Establezca la distancia de representación de recorte en 85cm con fadeout de contenido a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="f3f01-260">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="f3f01-261">En el caso de los hologramas estacionales que necesitan una visualización más estrecha, el plano de recorte no debe estar más cerca de 30cm y fadeout debe iniciar al menos 10cm fuera del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="f3f01-261">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-262">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-262">Resources</span></span>

* [<span data-ttu-id="f3f01-263">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="f3f01-263">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="f3f01-264">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-264">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="f3f01-265">Experimentación con escala</span><span class="sxs-lookup"><span data-stu-id="f3f01-265">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="f3f01-266">Texto, tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="f3f01-266">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="f3f01-267">Cambio de profundidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-267">Depth switching</span></span>

<span data-ttu-id="f3f01-268">Sin tener en cuenta los problemas de la zona de confort, las demandas del usuario a cambiar con frecuencia o rapidez entre los objetos cercanos y lejanos (incluidos los hologramas y el contenido del mundo real) pueden conducir a la fatiga oculomotor y a la molestia general.</span><span class="sxs-lookup"><span data-stu-id="f3f01-268">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-269">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-269">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-270"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-271"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-271"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-272">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-272">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-273">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-273">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-274">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-274">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-275">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-275">Best</span></span>  |  <span data-ttu-id="f3f01-276">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-276">Meets</span></span> |  <span data-ttu-id="f3f01-277">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-277">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-278">Cambio de profundidad limitado o natural que no hace que el usuario se recentre sin ningún problema.</span><span class="sxs-lookup"><span data-stu-id="f3f01-278">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="f3f01-279">Cambio de profundidad abrupta: este es el núcleo y está diseñado en la experiencia de la aplicación, o en el modificador de profundidad abrupta causado por contenido real inesperado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-279">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="f3f01-280">Conmutador de profundidad coherente o cambio de profundidad brusco que no es necesario ni básico para la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-280">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-281">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-281">How to measure</span></span>

* <span data-ttu-id="f3f01-282">Si la aplicación requiere que el usuario cambie de forma constante y/o repentinamente el foco de profundidad, hay un problema de conmutación de profundidad.</span><span class="sxs-lookup"><span data-stu-id="f3f01-282">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-283">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-283">Recommendations</span></span>

* <span data-ttu-id="f3f01-284">Mantenga el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal.</span><span class="sxs-lookup"><span data-stu-id="f3f01-284">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="f3f01-285">Esto evitará la fatiga oculomotor y el movimiento de holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-285">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-286">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-286">Resources</span></span>

* [<span data-ttu-id="f3f01-287">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="f3f01-287">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="f3f01-288">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-288">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="f3f01-289">Uso de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-289">Use of spatial sound</span></span>

<span data-ttu-id="f3f01-290">En Windows Mixed Reality, el motor de audio proporciona el componente aural de la experiencia de realidad mixta mediante la simulación de un sonido 3D mediante simulaciones de dirección, distancia y entorno.</span><span class="sxs-lookup"><span data-stu-id="f3f01-290">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="f3f01-291">El uso de un sonido espacial en una aplicación permite a los desarrolladores colocar los sonidos de forma convincente en un espacio tridimensional (esfera) alrededor del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-291">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="f3f01-292">Después, esos sonidos parecerán como si provinieran de objetos físicos reales o los hologramas de realidad mixta en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-292">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="f3f01-293">El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f3f01-293">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-294">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-294">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-295"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-296"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-296"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-297">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-297">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-298">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-298">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-299">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-299">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-300">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-300">Best</span></span>  |  <span data-ttu-id="f3f01-301">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-301">Meets</span></span> |  <span data-ttu-id="f3f01-302">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-302">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-303">El sonido está espacial lógicamente y la experiencia de usuario usa correctamente el sonido para ayudar con la detección de objetos y los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="f3f01-303">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="f3f01-304">El sonido es natural y relevante para los objetos y se normaliza en el escenario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-304">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="f3f01-305">El audio espacial se utiliza de forma adecuada para aumentar la capacidad de respuesta, pero falta como medio para ayudar con los comentarios de los usuarios y la detectabilidad.</span><span class="sxs-lookup"><span data-stu-id="f3f01-305">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="f3f01-306">El sonido no está espacialmente como se esperaba o falta de sonido para ayudar al usuario dentro de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-306">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="f3f01-307">O el audio espacial no se consideró ni usó en el diseño del escenario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-307">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-308">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-308">How to measure</span></span>

* <span data-ttu-id="f3f01-309">En general, los sonidos relevantes deben emitirse desde los hologramas de destino (por ejemplo, el sonido de corteza procedente de holográfica Dog).</span><span class="sxs-lookup"><span data-stu-id="f3f01-309">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="f3f01-310">Deben usarse señales sonoras en toda la experiencia del usuario para ayudar al usuario a realizar comentarios o a conocer las acciones que se encuentran fuera del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="f3f01-310">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-311">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-311">Recommendations</span></span>

* <span data-ttu-id="f3f01-312">Use el audio espacial para ayudar con la detección de objetos y las interfaces de usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-312">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="f3f01-313">Los sonidos reales funcionan mejor que la síntesis o el sonido no natural.</span><span class="sxs-lookup"><span data-stu-id="f3f01-313">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="f3f01-314">La mayoría de los sonidos deben ser espaciales.</span><span class="sxs-lookup"><span data-stu-id="f3f01-314">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="f3f01-315">Evite los emisores invisibles.</span><span class="sxs-lookup"><span data-stu-id="f3f01-315">Avoid invisible emitters.</span></span>
* <span data-ttu-id="f3f01-316">Evite el enmascaramiento espacial.</span><span class="sxs-lookup"><span data-stu-id="f3f01-316">Avoid spatial masking.</span></span>
* <span data-ttu-id="f3f01-317">Normalizar todos los sonidos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-317">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-318">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-318">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-319">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-319">Documentation</span></span>

* [<span data-ttu-id="f3f01-320">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-320">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="f3f01-321">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-321">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="f3f01-322">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-322">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="f3f01-323">Caso práctico, sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="f3f01-323">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="f3f01-324">Caso práctico, uso de sonido espacial en RoboRaid</span><span class="sxs-lookup"><span data-stu-id="f3f01-324">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-325">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-325">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-326">MR Spatial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-326">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="f3f01-327">MRToolkit, audio espacial</span><span class="sxs-lookup"><span data-stu-id="f3f01-327">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="f3f01-328">Centrarse en los límites de trama holográfica (hipertema)</span><span class="sxs-lookup"><span data-stu-id="f3f01-328">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="f3f01-329">Las experiencias de usuario bien diseñadas pueden crear y mantener un contexto útil del entorno virtual que se extiende alrededor de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="f3f01-329">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="f3f01-330">Mitigar el efecto de los límites de los hipertextos implica un diseño minucioso de la escala y el contexto del contenido, el uso de audio espacial, los sistemas de orientación y la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-330">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="f3f01-331">Si se realiza correctamente, el usuario sentirá menos el límite de los límites de los subprocesos, a la vez que tiene una experiencia de aplicación cómoda.</span><span class="sxs-lookup"><span data-stu-id="f3f01-331">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-332">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-332">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-333"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-334"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-334"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-335">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-335">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-336">❌</span><span class="sxs-lookup"><span data-stu-id="f3f01-336">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-337">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-337">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-338">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-338">Best</span></span>  |  <span data-ttu-id="f3f01-339">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-339">Meets</span></span> |  <span data-ttu-id="f3f01-340">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-340">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-341">El usuario nunca pierde el contexto y se siente cómodo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-341">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="f3f01-342">Se proporciona asistencia contextual para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="f3f01-342">Context assistance is provided for large objects.</span></span> <span data-ttu-id="f3f01-343">Se proporcionan instrucciones de detección y visualización para los objetos que se encuentran fuera del marco.</span><span class="sxs-lookup"><span data-stu-id="f3f01-343">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="f3f01-344">En general, el diseño de movimiento y la escala de los hologramas son adecuados para una experiencia de visualización cómoda.</span><span class="sxs-lookup"><span data-stu-id="f3f01-344">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="f3f01-345">El usuario nunca pierde el contexto, pero es posible que se requiera movimiento de cuello adicional en situaciones limitadas.</span><span class="sxs-lookup"><span data-stu-id="f3f01-345">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="f3f01-346">En situaciones limitadas, la escala hace que los hologramas interrumpan el fotograma vertical u horizontal, lo que produce un movimiento de cuello para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="f3f01-346">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="f3f01-347">Es necesario que el usuario pierda el contexto o el movimiento de cuello coherente para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="f3f01-347">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="f3f01-348">No hay ninguna guía de contexto para objetos holográficas grandes, el movimiento de objetos es fácil de perder fuera del marco sin ninguna guía de detección, o bien un holograma alto requiere un movimiento de cuello normal para verlo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-348">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-349">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-349">How to measure</span></span>

* <span data-ttu-id="f3f01-350">El contexto de un holograma (grande) se pierde o no se entiende debido a que se recortan en los límites.</span><span class="sxs-lookup"><span data-stu-id="f3f01-350">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="f3f01-351">La ubicación de los hologramas es difícil de encontrar debido a la falta de directores de atención o al contenido que mueve y sale rápidamente del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="f3f01-351">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="f3f01-352">El escenario requiere un movimiento de cabezal normal y repetitivo hacia arriba y hacia abajo para ver por completo un holograma que dé lugar a una fatiga del cuello.</span><span class="sxs-lookup"><span data-stu-id="f3f01-352">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-353">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-353">Recommendations</span></span>

* <span data-ttu-id="f3f01-354">Comience la experiencia con objetos pequeños que se ajusten al objeto de subproceso y, a continuación, transición con indicaciones visuales a versiones más grandes.</span><span class="sxs-lookup"><span data-stu-id="f3f01-354">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="f3f01-355">Use los directores de audio y atención espaciales para ayudar al usuario a encontrar contenido que está fuera del hipermismo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-355">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="f3f01-356">En la medida de lo posible, evite los hologramas que recortan verticalmente el hipernivel.</span><span class="sxs-lookup"><span data-stu-id="f3f01-356">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="f3f01-357">Proporcionar al usuario orientación en la aplicación para obtener la mejor ubicación de visualización.</span><span class="sxs-lookup"><span data-stu-id="f3f01-357">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-358">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-358">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-359">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-359">Documentation</span></span>

* [<span data-ttu-id="f3f01-360">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="f3f01-360">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="f3f01-361">Caso práctico, aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="f3f01-361">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="f3f01-362">Escala de objetos y entornos</span><span class="sxs-lookup"><span data-stu-id="f3f01-362">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="f3f01-363">Cursores, indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="f3f01-363">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="f3f01-364">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="f3f01-364">External references</span></span>

* [<span data-ttu-id="f3f01-365">Gran cantidad de ADO sobre el visual</span><span class="sxs-lookup"><span data-stu-id="f3f01-365">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="f3f01-366">El contenido reacciona a la posición del usuario</span><span class="sxs-lookup"><span data-stu-id="f3f01-366">Content reacts to user position</span></span>

<span data-ttu-id="f3f01-367">Los hologramas deben reaccionar a la posición del usuario aproximadamente de la misma manera que lo hacen los objetos "reales".</span><span class="sxs-lookup"><span data-stu-id="f3f01-367">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="f3f01-368">Una consideración de diseño importante son los elementos de la interfaz de usuario que no pueden suponer necesariamente que la posición de un usuario sea estacional y adaptarse al movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-368">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="f3f01-369">El diseño de una aplicación que se adapta correctamente a la posición del usuario creará una experiencia más increíble y facilitará su uso.</span><span class="sxs-lookup"><span data-stu-id="f3f01-369">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-370">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-370">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-371"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-372"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-372"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-373">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-373">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-374">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-374">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-375">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-375">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="f3f01-376">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-376">Best</span></span> </td><td> <span data-ttu-id="f3f01-377">El contenido y la interfaz de usuario se adaptan a las posiciones de los usuarios, lo que permite al usuario interactuar de forma natural con el contenido dentro del ámbito de movimiento esperado</span><span class="sxs-lookup"><span data-stu-id="f3f01-377">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f3f01-378">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-378">Meets</span></span> </td><td> <span data-ttu-id="f3f01-379">La interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave que requiere que el usuario ajuste su posición.</span><span class="sxs-lookup"><span data-stu-id="f3f01-379">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="f3f01-380">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-380">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="f3f01-381">Los elementos de la interfaz de usuario se pierden o se bloquean durante el movimiento, lo que provoca que el usuario vuelva a los controles (o los busque) de una misma.</span><span class="sxs-lookup"><span data-stu-id="f3f01-381">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="f3f01-382">Los elementos de la interfaz de usuario limitan la vista del contenido principal.</span><span class="sxs-lookup"><span data-stu-id="f3f01-382">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="f3f01-383">El movimiento de la interfaz de usuario no está optimizado para ver la distancia y el momento, especialmente con elementos de interfaz <a href="billboarding-and-tag-along.md">de usuario de etiquetas</a> .</span><span class="sxs-lookup"><span data-stu-id="f3f01-383">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-384">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-384">How to measure</span></span>

* <span data-ttu-id="f3f01-385">Todas las medidas deben realizarse dentro de un ámbito razonable del escenario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-385">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="f3f01-386">Aunque el movimiento del usuario variará, no intente engañar a la aplicación con un movimiento de usuario extremo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-386">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="f3f01-387">En el caso de los elementos de la interfaz de usuario, los controles pertinentes deben estar disponibles independientemente del movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-387">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="f3f01-388">Por ejemplo, si el usuario está viendo y recorriendo un mapa 3D con zoom, el control de zoom debe estar disponible para el usuario independientemente de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-388">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-389">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-389">Recommendations</span></span>

* <span data-ttu-id="f3f01-390">El usuario es la cámara y controla el movimiento.</span><span class="sxs-lookup"><span data-stu-id="f3f01-390">The user is the camera and they control the movement.</span></span> <span data-ttu-id="f3f01-391">Dejar que se controlen.</span><span class="sxs-lookup"><span data-stu-id="f3f01-391">Let them drive.</span></span>
* <span data-ttu-id="f3f01-392">Considere la posibilidad de mostrar los sistemas de texto y de menú que, de otro modo, podrían quedar bloqueados o desconocidos si un usuario tuviera que desplazarse.</span><span class="sxs-lookup"><span data-stu-id="f3f01-392">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="f3f01-393">Use la etiqueta junto con el contenido que debe seguir al usuario y, al mismo tiempo, permitir que el usuario vea lo que hay delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-393">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-394">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-394">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-395">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-395">Documentation</span></span>

* [<span data-ttu-id="f3f01-396">Diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="f3f01-396">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="f3f01-397">Color, claro y material</span><span class="sxs-lookup"><span data-stu-id="f3f01-397">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="f3f01-398">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="f3f01-398">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f3f01-399">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="f3f01-399">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f3f01-400">Automovimiento y Locomotion de usuario</span><span class="sxs-lookup"><span data-stu-id="f3f01-400">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-401">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-401">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-402">MR Input 210: mirada</span><span class="sxs-lookup"><span data-stu-id="f3f01-402">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="f3f01-403">Claridad de interacción de entrada</span><span class="sxs-lookup"><span data-stu-id="f3f01-403">Input interaction clarity</span></span>

<span data-ttu-id="f3f01-404">La claridad de la interacción de entrada es fundamental para el uso de una aplicación e incluye la coherencia de entrada, la capacidad de enfoque, la detectabilidad de los métodos de interacción.</span><span class="sxs-lookup"><span data-stu-id="f3f01-404">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="f3f01-405">El usuario debe poder usar las interacciones comunes de toda la plataforma sin tener que reaprender.</span><span class="sxs-lookup"><span data-stu-id="f3f01-405">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="f3f01-406">Si la aplicación tiene una entrada personalizada, debe comunicarse claramente y mostrarse.</span><span class="sxs-lookup"><span data-stu-id="f3f01-406">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-407">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-407">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-408"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-409"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-409"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-410">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-410">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-411">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-411">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-412">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-412">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-413">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-413">Best</span></span>  |  <span data-ttu-id="f3f01-414">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-414">Meets</span></span> |  <span data-ttu-id="f3f01-415">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-415">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-416">Los métodos de interacción de entrada son coherentes con las [instrucciones](interaction-fundamentals.md)proporcionadas por Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f3f01-416">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="f3f01-417">Cualquier entrada personalizada no debe ser redundante con entrada estándar (en lugar de usar la interacción estándar) y se debe comunicar y demostrar claramente al usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-417">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="f3f01-418">Similar a lo mejor, pero las entradas personalizadas son redundantes con los métodos de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="f3f01-418">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="f3f01-419">El usuario puede seguir logrando el objetivo y el progreso a través de la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-419">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="f3f01-420">Es difícil comprender la asignación de botones o métodos de entrada.</span><span class="sxs-lookup"><span data-stu-id="f3f01-420">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="f3f01-421">La entrada está muy personalizada, no es compatible con la entrada estándar, no hay instrucciones o probablemente cause problemas de fatiga y confort.</span><span class="sxs-lookup"><span data-stu-id="f3f01-421">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-422">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-422">How to measure</span></span>

* <span data-ttu-id="f3f01-423">La aplicación usa [métodos de entrada estándar](interaction-fundamentals.md) coherentes.</span><span class="sxs-lookup"><span data-stu-id="f3f01-423">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="f3f01-424">Si la aplicación tiene una entrada personalizada, se comunica claramente mediante:</span><span class="sxs-lookup"><span data-stu-id="f3f01-424">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="f3f01-425">Experiencia de primera ejecución</span><span class="sxs-lookup"><span data-stu-id="f3f01-425">First-run experience</span></span>
* <span data-ttu-id="f3f01-426">Pantallas de introducción</span><span class="sxs-lookup"><span data-stu-id="f3f01-426">Introductory screens</span></span>
* <span data-ttu-id="f3f01-427">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="f3f01-427">Tooltips</span></span>
* <span data-ttu-id="f3f01-428">Autocar manual</span><span class="sxs-lookup"><span data-stu-id="f3f01-428">Hand coach</span></span>
* <span data-ttu-id="f3f01-429">Sección de ayuda</span><span class="sxs-lookup"><span data-stu-id="f3f01-429">Help section</span></span>
* <span data-ttu-id="f3f01-430">Voz sobre</span><span class="sxs-lookup"><span data-stu-id="f3f01-430">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-431">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-431">Recommendations</span></span>

* <span data-ttu-id="f3f01-432">Utilice los métodos de entrada estándar siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="f3f01-432">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="f3f01-433">Proporcione demostraciones, tutoriales e información sobre herramientas para los métodos de entrada no estándar.</span><span class="sxs-lookup"><span data-stu-id="f3f01-433">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="f3f01-434">Use un modelo de interacción coherente en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-434">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-435">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-435">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-436">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-436">Documentation</span></span>

* [<span data-ttu-id="f3f01-437">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="f3f01-437">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f3f01-438">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="f3f01-438">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="f3f01-439">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="f3f01-439">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="f3f01-440">Cursores</span><span class="sxs-lookup"><span data-stu-id="f3f01-440">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f3f01-441">Confort y mira</span><span class="sxs-lookup"><span data-stu-id="f3f01-441">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="f3f01-442">Gestos</span><span class="sxs-lookup"><span data-stu-id="f3f01-442">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="f3f01-443">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="f3f01-443">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="f3f01-444">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="f3f01-444">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="f3f01-445">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-445">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="f3f01-446">Guía de portabilidad de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-446">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="f3f01-447">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-447">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="f3f01-448">Mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-448">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="f3f01-449">Gestos y controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-449">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="f3f01-450">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-450">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="f3f01-451">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="f3f01-451">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="f3f01-452">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="f3f01-452">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="f3f01-453">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="f3f01-453">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="f3f01-454">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="f3f01-454">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-455">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-455">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-456">Caso práctico: Realización de más informática personal</span><span class="sxs-lookup"><span data-stu-id="f3f01-456">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="f3f01-457">Estudio de conversión: Aprendizaje de la interfaz de usuario y diseño de interacción de HoloStudio</span><span class="sxs-lookup"><span data-stu-id="f3f01-457">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="f3f01-458">Aplicación de ejemplo: Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="f3f01-458">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="f3f01-459">Aplicación de ejemplo: Módulo lunar</span><span class="sxs-lookup"><span data-stu-id="f3f01-459">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="f3f01-460">MR Input 210: mirada</span><span class="sxs-lookup"><span data-stu-id="f3f01-460">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="f3f01-461">MR Input 211: Gestos</span><span class="sxs-lookup"><span data-stu-id="f3f01-461">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="f3f01-462">MR Input 212: voz</span><span class="sxs-lookup"><span data-stu-id="f3f01-462">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="f3f01-463">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="f3f01-463">Interactable objects</span></span>

<span data-ttu-id="f3f01-464">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="f3f01-464">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="f3f01-465">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="f3f01-465">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="f3f01-466">Cualquier elemento puede ser un objeto interactuable que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="f3f01-466">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="f3f01-467">Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="f3f01-467">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="f3f01-468">Independientemente del formulario, los objetos interactivos deben ser claramente reconocibles por el usuario a través de las indicaciones de audio y visual.</span><span class="sxs-lookup"><span data-stu-id="f3f01-468">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-469">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-469">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-470"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-471"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-471"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-472">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-472">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-473">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-473">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-474">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-474">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-475">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-475">Best</span></span>  |  <span data-ttu-id="f3f01-476">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-476">Meets</span></span> |  <span data-ttu-id="f3f01-477">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-477">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-478">Independientemente del formulario, los objetos interactuables se pueden reconocer a través de las indicaciones de audio y visual en tres Estados: inactivo, dirigido y seleccionado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-478">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="f3f01-479">"Lo veo, por ejemplo, está claro y se usa de forma coherente en toda la experiencia.</span><span class="sxs-lookup"><span data-stu-id="f3f01-479">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="f3f01-480">Los objetos se escalan y distribuyen para permitir la finalización de errores de forma gratuita.</span><span class="sxs-lookup"><span data-stu-id="f3f01-480">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="f3f01-481">El usuario puede reconocer objetos como interactivos a través de comentarios de audio o visuales, y puede tener como destino y activar el objeto.</span><span class="sxs-lookup"><span data-stu-id="f3f01-481">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="f3f01-482">No se proporcionan indicaciones visuales o de audio, el usuario no puede reconocer un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="f3f01-482">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="f3f01-483">Las interacciones son propensas a errores debido a la escala de objetos o a la distancia entre los objetos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-483">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-484">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-484">How to measure</span></span>

* <span data-ttu-id="f3f01-485">Los objetos interactuables son reconocibles como ' interactuable '; incluir botones, menús y contenido específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-485">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="f3f01-486">Como regla general, debe haber una indicación visual y de audio cuando el destino es objetos interactivos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-486">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-487">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-487">Recommendations</span></span>

* <span data-ttu-id="f3f01-488">Use comentarios visuales y de audio para las interacciones.</span><span class="sxs-lookup"><span data-stu-id="f3f01-488">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="f3f01-489">Los comentarios visuales deben diferenciarse en cada estado de entrada (inactivo, dirigido, seleccionado)</span><span class="sxs-lookup"><span data-stu-id="f3f01-489">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="f3f01-490">Los objetos que se pueden interactuar deben escalarse y colocarse para los destinos sin errores.</span><span class="sxs-lookup"><span data-stu-id="f3f01-490">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="f3f01-491">Los objetos interactuables agrupados (por ejemplo, una barra de menús o una lista) deben tener el espaciado adecuado para el destino.</span><span class="sxs-lookup"><span data-stu-id="f3f01-491">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="f3f01-492">Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto para la palabra clave Command ("vea esto, dígalo")</span><span class="sxs-lookup"><span data-stu-id="f3f01-492">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-493">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-493">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-494">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-494">Documentation</span></span>

* [<span data-ttu-id="f3f01-495">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="f3f01-495">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f3f01-496">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="f3f01-496">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="f3f01-497">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f3f01-497">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f3f01-498">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="f3f01-498">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-499">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-499">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-500">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="f3f01-500">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="f3f01-501">Detección de salas</span><span class="sxs-lookup"><span data-stu-id="f3f01-501">Room scanning</span></span>

<span data-ttu-id="f3f01-502">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="f3f01-502">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="f3f01-503">La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.</span><span class="sxs-lookup"><span data-stu-id="f3f01-503">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="f3f01-504">Muchas aplicaciones analizarán los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad del mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="f3f01-504">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="f3f01-505">Si es necesario que el usuario analice el entorno, debe proporcionar instrucciones claras durante la experiencia de exploración.</span><span class="sxs-lookup"><span data-stu-id="f3f01-505">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-506">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-506">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-507"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-508"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-508"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-509">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-509">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-510">❌</span><span class="sxs-lookup"><span data-stu-id="f3f01-510">❌</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-511">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-511">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-512">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-512">Best</span></span>  |  <span data-ttu-id="f3f01-513">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-513">Meets</span></span> |  <span data-ttu-id="f3f01-514">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-514">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-515">Visualización de la malla espacial indique a los usuarios que el análisis está en curso.</span><span class="sxs-lookup"><span data-stu-id="f3f01-515">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="f3f01-516">El usuario sabe claramente qué hacer y cuándo se inicia y se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="f3f01-516">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="f3f01-517">Se proporciona la visualización de la malla espacial, pero es posible que el usuario no sepa claramente qué hacer y que no se proporcione información de progreso.</span><span class="sxs-lookup"><span data-stu-id="f3f01-517">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="f3f01-518">Ninguna visualización de malla.</span><span class="sxs-lookup"><span data-stu-id="f3f01-518">No visualization of mesh.</span></span> <span data-ttu-id="f3f01-519">No se proporciona información de orientación al usuario sobre dónde buscar, o Cuándo se inicia o se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="f3f01-519">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-520">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-520">How to measure</span></span>

* <span data-ttu-id="f3f01-521">Durante un examen de habitación necesario, se proporciona orientación visual y de audio que indica dónde buscar y cuándo iniciar y detener el examen.</span><span class="sxs-lookup"><span data-stu-id="f3f01-521">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-522">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-522">Recommendations</span></span>

* <span data-ttu-id="f3f01-523">Indique la cantidad del volumen total de los usuarios que debe formar parte de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="f3f01-523">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="f3f01-524">Comunicarse cuando el examen se inicia y se detiene, como un indicador de progreso.</span><span class="sxs-lookup"><span data-stu-id="f3f01-524">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="f3f01-525">Use una visualización de la malla durante el examen.</span><span class="sxs-lookup"><span data-stu-id="f3f01-525">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="f3f01-526">Proporcione guías de audio y visual para animar al usuario a buscar y desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="f3f01-526">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="f3f01-527">Informe al usuario de dónde debe ir para mejorar los datos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-527">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="f3f01-528">En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="f3f01-528">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-529">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-529">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="f3f01-530">Documentación</span><span class="sxs-lookup"><span data-stu-id="f3f01-530">Documentation</span></span>

* [<span data-ttu-id="f3f01-531">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="f3f01-531">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="f3f01-532">Caso práctico: Ampliación de las capacidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="f3f01-532">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="f3f01-533">Caso práctico: Diseño de sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="f3f01-533">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="f3f01-534">Caso práctico: Creación de una experiencia envolvente en fragmentos</span><span class="sxs-lookup"><span data-stu-id="f3f01-534">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="f3f01-535">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="f3f01-535">Tools and tutorials</span></span>

* [<span data-ttu-id="f3f01-536">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="f3f01-536">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="f3f01-537">Indicadores direccionales</span><span class="sxs-lookup"><span data-stu-id="f3f01-537">Directional indicators</span></span>

<span data-ttu-id="f3f01-538">En una aplicación de realidad mixta, el contenido puede estar fuera del campo de vista o ocluidos por objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="f3f01-538">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="f3f01-539">Una aplicación bien diseñada facilitará a los usuarios la búsqueda de contenido no visible.</span><span class="sxs-lookup"><span data-stu-id="f3f01-539">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="f3f01-540">Los indicadores direccionales avisan a un usuario de contenido importante y proporcionan orientación sobre el contenido en relación con la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-540">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="f3f01-541">Las instrucciones para el contenido no visible pueden adoptar la forma de emisores de sonido, flechas direccionales o indicaciones visuales directas.</span><span class="sxs-lookup"><span data-stu-id="f3f01-541">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-542">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-542">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-543"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-544"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-544"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-545">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-545">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-546">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-546">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-547">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-547">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-548">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-548">Best</span></span>  |  <span data-ttu-id="f3f01-549">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-549">Meets</span></span> |  <span data-ttu-id="f3f01-550">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-550">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-551">Las guías de audio y visual guían directamente al usuario al contenido relevante fuera del campo de vista.</span><span class="sxs-lookup"><span data-stu-id="f3f01-551">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="f3f01-552">Una flecha o algún indicador que apunta al usuario en la dirección general del contenido.</span><span class="sxs-lookup"><span data-stu-id="f3f01-552">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="f3f01-553">El contenido relevante está fuera del campo de vista y no se proporciona ninguna guía de ubicación para el usuario.</span><span class="sxs-lookup"><span data-stu-id="f3f01-553">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-554">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-554">How to measure</span></span>

* <span data-ttu-id="f3f01-555">El contenido relevante fuera del campo de vista de usuario se detecta mediante señales de audio o visual.</span><span class="sxs-lookup"><span data-stu-id="f3f01-555">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-556">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-556">Recommendations</span></span>

* <span data-ttu-id="f3f01-557">Cuando el contenido pertinente esté fuera del campo de vista del usuario, use indicadores direccionales e indicaciones de audio para guiar al usuario al contenido.</span><span class="sxs-lookup"><span data-stu-id="f3f01-557">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="f3f01-558">En muchos casos, se prefiere una guía visual directa a las flechas direccionales.</span><span class="sxs-lookup"><span data-stu-id="f3f01-558">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="f3f01-559">Los indicadores direccionales no se deben integrar en el cursor.</span><span class="sxs-lookup"><span data-stu-id="f3f01-559">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-560">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-560">Resources</span></span>

* [<span data-ttu-id="f3f01-561">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="f3f01-561">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="f3f01-562">Carga de datos</span><span class="sxs-lookup"><span data-stu-id="f3f01-562">Data loading</span></span>

<span data-ttu-id="f3f01-563">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="f3f01-563">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="f3f01-564">Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto tiempo puede ser el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="f3f01-564">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="f3f01-565">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="f3f01-565">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f3f01-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-566"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f3f01-567"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f3f01-567"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f3f01-568">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-568">✔️</span></span></td>
        <td><span data-ttu-id="f3f01-569">✔️</span><span class="sxs-lookup"><span data-stu-id="f3f01-569">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="f3f01-570">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="f3f01-570">Quality criteria</span></span>

|  <span data-ttu-id="f3f01-571">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="f3f01-571">Best</span></span>  |  <span data-ttu-id="f3f01-572">Reúne</span><span class="sxs-lookup"><span data-stu-id="f3f01-572">Meets</span></span> |  <span data-ttu-id="f3f01-573">Puedan</span><span class="sxs-lookup"><span data-stu-id="f3f01-573">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="f3f01-574">Indicador visual animado, en forma de una barra de progreso o un anillo, que muestra el progreso durante cualquier carga o procesamiento de datos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-574">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="f3f01-575">El indicador visual proporciona instrucciones sobre cuánto tiempo puede ser la espera.</span><span class="sxs-lookup"><span data-stu-id="f3f01-575">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="f3f01-576">Se informa al usuario de que la carga de datos está en curso, pero no hay ninguna indicación de cuánto tiempo podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="f3f01-576">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="f3f01-577">No hay ningún indicador de carga de datos o de proceso para que la tarea tarde más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-577">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="f3f01-578">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="f3f01-578">How to measure</span></span>

* <span data-ttu-id="f3f01-579">Durante la carga de datos, compruebe que no hay ningún estado en blanco durante más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-579">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="f3f01-580">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="f3f01-580">Recommendations</span></span>

* <span data-ttu-id="f3f01-581">Proporcionar un animador de carga de datos que muestre el progreso en cualquier situación en la que el usuario pueda percibir que esta aplicación se haya detenido o bloqueado.</span><span class="sxs-lookup"><span data-stu-id="f3f01-581">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="f3f01-582">Una regla general razonable es cualquier actividad de "carga" que podría tardar más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="f3f01-582">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="f3f01-583">Recursos</span><span class="sxs-lookup"><span data-stu-id="f3f01-583">Resources</span></span>

* [<span data-ttu-id="f3f01-584">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="f3f01-584">Displaying progress</span></span>](progress.md)
