---
title: Criterios de calidad de la aplicación
description: En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: Criterios de calidad de la aplicación, realidad mixta, aplicación de realidad mixta
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437049"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="817bc-104">Criterios de calidad de la aplicación</span><span class="sxs-lookup"><span data-stu-id="817bc-104">App quality criteria</span></span>

<span data-ttu-id="817bc-105">En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="817bc-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="817bc-106">Para cada factor se proporciona la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="817bc-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="817bc-107">Información general: breve descripción del factor de calidad y por qué es importante.</span><span class="sxs-lookup"><span data-stu-id="817bc-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="817bc-108">Impacto en el dispositivo: Qué tipo de dispositivo de realidad mixta de ventana se ve afectado.</span><span class="sxs-lookup"><span data-stu-id="817bc-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="817bc-109">Criterios de calidad: Cómo evaluar el factor de calidad.</span><span class="sxs-lookup"><span data-stu-id="817bc-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="817bc-110">Cómo medir: métodos para medir (o experimentar) el problema.</span><span class="sxs-lookup"><span data-stu-id="817bc-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="817bc-111">Recomendaciones: Resumen de los enfoques para proporcionar una mejor experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="817bc-112">Recursos: recursos de desarrollador y diseño relevantes que son útiles para crear mejores experiencias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="817bc-113">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="817bc-113">Frame rate</span></span>

<span data-ttu-id="817bc-114">La velocidad de fotogramas es el primer pilar de estabilidad del holograma y la comodidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="817bc-115">La velocidad de fotogramas por debajo de los objetivos recomendados puede hacer que los hologramas parezcan vibrantes, lo que afecta negativamente a la increíble potencia de la experiencia y, potencialmente, a la fatiga ocular.</span><span class="sxs-lookup"><span data-stu-id="817bc-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="817bc-116">La velocidad de fotogramas de destino para su experiencia en los auriculares de la realidad mixta de Windows será de 60Hz o 90Hz, según los equipos compatibles con Windows Mixed Reality que desee admitir.</span><span class="sxs-lookup"><span data-stu-id="817bc-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="817bc-117">Para HoloLens, la velocidad de fotogramas de destino es 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="817bc-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-118">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-119"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-120"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-121">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-121">✔️</span></span></td>
        <td><span data-ttu-id="817bc-122">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-123">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-123">Quality criteria</span></span>

|  <span data-ttu-id="817bc-124">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-124">Best</span></span>  |  <span data-ttu-id="817bc-125">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-125">Meets</span></span> |  <span data-ttu-id="817bc-126">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="817bc-127">La aplicación cumple de forma coherente el objetivo de fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en ultra PCs; y 60fps en equipos estándar.</span><span class="sxs-lookup"><span data-stu-id="817bc-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="817bc-128">La aplicación tiene caídas de fotogramas intermitentes que no impiden la experiencia básica; o FPS es constantemente inferior al objetivo deseado, pero no impide la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="817bc-129">La aplicación está experimentando una caída en la velocidad de fotogramas como promedio cada diez segundos o menos.</span><span class="sxs-lookup"><span data-stu-id="817bc-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="817bc-130">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-130">How to measure</span></span>

* <span data-ttu-id="817bc-131">El [portal de dispositivos de Windows](using-the-windows-device-portal.md#system-performance) proporciona un gráfico de velocidad de fotogramas en tiempo real en "rendimiento del sistema".</span><span class="sxs-lookup"><span data-stu-id="817bc-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="817bc-132">Para la depuración de desarrollo, agregue un contador de diagnóstico de velocidad de fotogramas a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="817bc-133">Vea recursos para obtener un contador de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="817bc-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="817bc-134">Las caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras la aplicación se está ejecutando moviendo el encabezado de lado a lado.</span><span class="sxs-lookup"><span data-stu-id="817bc-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="817bc-135">Si el holograma muestra un movimiento de vibración inesperado, es probable que la velocidad de fotogramas baja o el plano de estabilidad sea la causa.</span><span class="sxs-lookup"><span data-stu-id="817bc-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-136">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-136">Recommendations</span></span>

* <span data-ttu-id="817bc-137">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="817bc-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="817bc-138">Los cambios que incurren en una caída en la velocidad de fotogramas se deben evaluar y resolver correctamente como un error de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="817bc-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-139">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-140">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-140">Documentation</span></span>

* [<span data-ttu-id="817bc-141">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="817bc-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="817bc-142">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="817bc-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="817bc-143">Presupuesto de rendimiento de activos</span><span class="sxs-lookup"><span data-stu-id="817bc-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="817bc-144">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-145">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-145">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-146">MRToolkit, pantalla de contador de FPS</span><span class="sxs-lookup"><span data-stu-id="817bc-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="817bc-147">MRToolkit, sombreadores</span><span class="sxs-lookup"><span data-stu-id="817bc-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="817bc-148">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="817bc-148">External references</span></span>

* [<span data-ttu-id="817bc-149">Unity, optimizar aplicaciones móviles</span><span class="sxs-lookup"><span data-stu-id="817bc-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="817bc-150">Estabilidad de holograma</span><span class="sxs-lookup"><span data-stu-id="817bc-150">Hologram stability</span></span>

<span data-ttu-id="817bc-151">Los hologramas estables aumentarán la facilidad de uso y la increíble capacidad de su aplicación, y crearán una experiencia de visualización más cómoda para el usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="817bc-152">La calidad de la estabilidad del holograma es el resultado de un buen desarrollo de la aplicación y la capacidad del dispositivo para comprender (realizar un seguimiento) de su entorno.</span><span class="sxs-lookup"><span data-stu-id="817bc-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="817bc-153">Aunque la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar a la estabilidad, como:</span><span class="sxs-lookup"><span data-stu-id="817bc-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="817bc-154">Uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="817bc-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="817bc-155">Distancia a los delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="817bc-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="817bc-156">Llevar</span><span class="sxs-lookup"><span data-stu-id="817bc-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-157">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-158"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-159"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-159"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-160">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-161">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-161">Quality criteria</span></span>

|  <span data-ttu-id="817bc-162">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-162">Best</span></span>  |  <span data-ttu-id="817bc-163">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-163">Meets</span></span> |  <span data-ttu-id="817bc-164">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-165">Los hologramas aparecen de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="817bc-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="817bc-166">El contenido secundario exhibe un movimiento inesperado. o el movimiento inesperado no impide la experiencia general de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="817bc-167">El contenido principal del marco exhibe un movimiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="817bc-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="817bc-168">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-168">How to measure</span></span>

<span data-ttu-id="817bc-169">Con el dispositivo y la visualización de la experiencia:</span><span class="sxs-lookup"><span data-stu-id="817bc-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="817bc-170">Mover el encabezado de lado a lado, si los hologramas muestran un movimiento inesperado, la velocidad de fotogramas baja o la alineación incorrecta del plano de estabilidad al plano focal es la causa probable.</span><span class="sxs-lookup"><span data-stu-id="817bc-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="817bc-171">Desplazarse por los hologramas y el entorno, busque comportamientos como nadar y salto.</span><span class="sxs-lookup"><span data-stu-id="817bc-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="817bc-172">Este tipo de movimiento probablemente se debe a que el dispositivo no realiza un seguimiento del entorno o a la distancia al delimitador espacial.</span><span class="sxs-lookup"><span data-stu-id="817bc-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="817bc-173">Si hay varios hologramas en el marco, observe el comportamiento de holograma en varias profundidades al mover la posición principal de lado a lado, en caso de que la irregularidad parezca que esto se debe a un plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="817bc-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="817bc-174">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-174">Recomendations</span></span>

* <span data-ttu-id="817bc-175">Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="817bc-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="817bc-176">Use el plano de estabilización.</span><span class="sxs-lookup"><span data-stu-id="817bc-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="817bc-177">Siempre representa los hologramas anclados dentro de los 3 metros de su delimitador.</span><span class="sxs-lookup"><span data-stu-id="817bc-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="817bc-178">Asegúrese de que el entorno está configurado para el seguimiento adecuado.</span><span class="sxs-lookup"><span data-stu-id="817bc-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="817bc-179">Diseñe su experiencia para evitar los hologramas en diversos niveles de profundidad focal dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="817bc-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-180">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-181">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-181">Documentation</span></span>

* [<span data-ttu-id="817bc-182">Estabilidad y velocidad del holograma</span><span class="sxs-lookup"><span data-stu-id="817bc-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="817bc-183">Caso práctico, uso del plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="817bc-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="817bc-184">Descripción del rendimiento de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="817bc-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="817bc-185">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="817bc-186">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="817bc-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="817bc-187">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="817bc-188">Marco estacionario de referencia</span><span class="sxs-lookup"><span data-stu-id="817bc-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-189">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-189">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-190">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="817bc-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="817bc-191">Posición de hologramas en superficies reales</span><span class="sxs-lookup"><span data-stu-id="817bc-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="817bc-192">Las alineaciones de los hologramas con objetos físicos (si se prevé que se colocarán en relación con otras) son una indicación clara de la no Unión de los hologramas y del mundo real.</span><span class="sxs-lookup"><span data-stu-id="817bc-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="817bc-193">La precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; por ejemplo, la selección de ubicación de superficie general puede usar el mapa espacial, pero la selección de ubicación más precisa requerirá el uso de marcadores y calibración.</span><span class="sxs-lookup"><span data-stu-id="817bc-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-194">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-195"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-196"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-196"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-197">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-198">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-198">Quality criteria</span></span>

|  <span data-ttu-id="817bc-199">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-199">Best</span></span>  |  <span data-ttu-id="817bc-200">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-200">Meets</span></span> |  <span data-ttu-id="817bc-201">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="817bc-202">Los hologramas se alinean a la superficie normalmente en el intervalo de centímetros a pulgadas.</span><span class="sxs-lookup"><span data-stu-id="817bc-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="817bc-203">Si se requiere más precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada.</span><span class="sxs-lookup"><span data-stu-id="817bc-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="817bc-204">N/A</span><span class="sxs-lookup"><span data-stu-id="817bc-204">NA</span></span> | <span data-ttu-id="817bc-205">Los hologramas aparecen sin alinear con el objeto de destino físico, ya que separan el plano de la superficie o parecen flotar fuera de la superficie.</span><span class="sxs-lookup"><span data-stu-id="817bc-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="817bc-206">Si se requiere precisión, los hologramas deben cumplir las especificaciones de proximidad del escenario.</span><span class="sxs-lookup"><span data-stu-id="817bc-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-207">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-207">How to measure</span></span>

* <span data-ttu-id="817bc-208">Los hologramas que se colocan en el mapa espacial no deben parecer drásticamente por encima o por debajo de la superficie.</span><span class="sxs-lookup"><span data-stu-id="817bc-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="817bc-209">Los hologramas que requieren una ubicación precisa deben tener algún tipo de sistema de marcadores y calibración que sea preciso para el requisito del escenario.</span><span class="sxs-lookup"><span data-stu-id="817bc-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-210">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-210">Recommendations</span></span>

* <span data-ttu-id="817bc-211">El mapa espacial resulta útil para colocar objetos en superficies cuando no se requiere precisión.</span><span class="sxs-lookup"><span data-stu-id="817bc-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="817bc-212">Para obtener la mejor precisión, use marcadores o pósteres para establecer los hologramas y un controlador de Xbox (o algún mecanismo de alineación manual) para la calibración final.</span><span class="sxs-lookup"><span data-stu-id="817bc-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="817bc-213">Considere la posibilidad de dividir los hologramas extra grandes en partes lógicas y alinear cada parte en la superficie.</span><span class="sxs-lookup"><span data-stu-id="817bc-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="817bc-214">La Interpupilary distancia establecida correctamente (IPD) también puede afectar a la alineación de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="817bc-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="817bc-215">Configure siempre HoloLens en el del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-216">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-217">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-217">Documentation</span></span>

* [<span data-ttu-id="817bc-218">Colocación de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="817bc-219">Proceso de detección de salas</span><span class="sxs-lookup"><span data-stu-id="817bc-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="817bc-220">Procedimientos recomendados para los anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="817bc-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="817bc-221">Control de errores de seguimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="817bc-222">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="817bc-223">Información general sobre el desarrollo de Vuforia</span><span class="sxs-lookup"><span data-stu-id="817bc-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-224">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-224">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-225">MR espacial 230: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="817bc-226">Kit de herramientas de MR, bibliotecas de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="817bc-227">Kit complementario MR, ejemplo de calibración de póster</span><span class="sxs-lookup"><span data-stu-id="817bc-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="817bc-228">Kit complementario MR, Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="817bc-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="817bc-229">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="817bc-229">External references</span></span>

* [<span data-ttu-id="817bc-230">Caso práctico de Lowes, alineación de precisión</span><span class="sxs-lookup"><span data-stu-id="817bc-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="817bc-231">Ver la zona de confort</span><span class="sxs-lookup"><span data-stu-id="817bc-231">Viewing zone of comfort</span></span>

<span data-ttu-id="817bc-232">Los desarrolladores de aplicaciones controlan el lugar en el que los usuarios convergen colocando contenido y hologramas a varias profundidades.</span><span class="sxs-lookup"><span data-stu-id="817bc-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="817bc-233">Los usuarios que contengan HoloLens siempre se acomodarán a 2,0 m para mantener una imagen clara porque las pantallas de HoloLens se fijan a una distancia óptica aproximadamente a 2,0 m del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="817bc-234">Una profundidad de contenido incorrecta puede conducir a la molestia visual o a la fatiga.</span><span class="sxs-lookup"><span data-stu-id="817bc-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-235">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-236"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-237"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-237"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-238">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-239">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="817bc-240">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="817bc-241">Coloque el contenido en 2m.</span><span class="sxs-lookup"><span data-stu-id="817bc-241">Place content at 2m.</span></span></li><li><span data-ttu-id="817bc-242">Cuando los hologramas no se pueden colocar en 2m y no se pueden evitar conflictos entre convergencia y ajuste, la zona óptima para la colocación de hologramas se encuentra entre 1,25 m y 5 m.</span><span class="sxs-lookup"><span data-stu-id="817bc-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="817bc-243">En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar con 1 + m (por ejemplo, ajustar el tamaño del contenido y los parámetros de ubicación predeterminados).</span><span class="sxs-lookup"><span data-stu-id="817bc-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="817bc-244">A menos que el escenario no requiera específicamente, se debe implementar un plano de recorte con fadeout a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="817bc-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="817bc-245">En los casos en los que se requiere una observación más detallada de un holograma de motionless, el contenido no debe estar más cerca que 50CM.</span><span class="sxs-lookup"><span data-stu-id="817bc-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="817bc-246">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-246">Meets</span></span></td><td> <span data-ttu-id="817bc-247">El contenido está dentro de la guía de visualización y movimiento, pero se usa inadecuadamente o no se usa el plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="817bc-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="817bc-248">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-248">Fail</span></span> </td><td> <span data-ttu-id="817bc-249">El contenido se presenta demasiado cerca (normalmente &lt;1,25 m o &lt;50CM para los hologramas estacionales que requieren una observación más detallada).</span><span class="sxs-lookup"><span data-stu-id="817bc-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="817bc-250">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-250">How to measure</span></span>

* <span data-ttu-id="817bc-251">Normalmente, el contenido debe ser de 2 m, pero no más cercano a 1,25 o superior a 5 m.</span><span class="sxs-lookup"><span data-stu-id="817bc-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="817bc-252">Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en. 85CM con fadeout de contenido que empieza en 1m.</span><span class="sxs-lookup"><span data-stu-id="817bc-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="817bc-253">Acerque el contenido y observe el efecto del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="817bc-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="817bc-254">El contenido estacionario no debe estar más cerca de 50CM.</span><span class="sxs-lookup"><span data-stu-id="817bc-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-255">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-255">Recommendations</span></span>

* <span data-ttu-id="817bc-256">Diseñe el contenido para obtener la distancia de visualización óptima de 2 m.</span><span class="sxs-lookup"><span data-stu-id="817bc-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="817bc-257">Establezca la distancia de representación de recorte en 85cm con fadeout de contenido a partir de 1m.</span><span class="sxs-lookup"><span data-stu-id="817bc-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="817bc-258">En el caso de los hologramas estacionales que necesitan una visualización más estrecha, el plano de recorte no debe estar más cerca de 30cm y fadeout debe iniciar al menos 10cm fuera del plano de recorte.</span><span class="sxs-lookup"><span data-stu-id="817bc-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-259">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-259">Resources</span></span>

* [<span data-ttu-id="817bc-260">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="817bc-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="817bc-261">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="817bc-262">Experimentación con escala</span><span class="sxs-lookup"><span data-stu-id="817bc-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="817bc-263">Texto, tamaño de fuente recomendado</span><span class="sxs-lookup"><span data-stu-id="817bc-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="817bc-264">Cambio de profundidad</span><span class="sxs-lookup"><span data-stu-id="817bc-264">Depth switching</span></span>

<span data-ttu-id="817bc-265">Sin tener en cuenta los problemas de la zona de confort, las demandas del usuario a cambiar con frecuencia o rapidez entre los objetos cercanos y lejanos (incluidos los hologramas y el contenido del mundo real) pueden conducir a la fatiga oculomotor y a la molestia general.</span><span class="sxs-lookup"><span data-stu-id="817bc-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-266">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-267"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-268"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-268"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-269">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-269">✔️</span></span></td>
        <td><span data-ttu-id="817bc-270">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-271">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-271">Quality criteria</span></span>

|  <span data-ttu-id="817bc-272">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-272">Best</span></span>  |  <span data-ttu-id="817bc-273">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-273">Meets</span></span> |  <span data-ttu-id="817bc-274">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-275">Cambio de profundidad limitado o natural que no hace que el usuario se recentre sin ningún problema.</span><span class="sxs-lookup"><span data-stu-id="817bc-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="817bc-276">Cambio de profundidad abrupta: este es el núcleo y está diseñado en la experiencia de la aplicación, o en el modificador de profundidad abrupta causado por contenido real inesperado.</span><span class="sxs-lookup"><span data-stu-id="817bc-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="817bc-277">Conmutador de profundidad coherente o cambio de profundidad brusco que no es necesario ni básico para la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-278">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-278">How to measure</span></span>

* <span data-ttu-id="817bc-279">Si la aplicación requiere que el usuario cambie de forma constante y/o repentinamente el foco de profundidad, hay un problema de conmutación de profundidad.</span><span class="sxs-lookup"><span data-stu-id="817bc-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-280">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-280">Recommendations</span></span>

* <span data-ttu-id="817bc-281">Mantenga el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal.</span><span class="sxs-lookup"><span data-stu-id="817bc-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="817bc-282">Esto evitará la fatiga oculomotor y el movimiento de holograma inesperado.</span><span class="sxs-lookup"><span data-stu-id="817bc-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-283">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-283">Resources</span></span>

* [<span data-ttu-id="817bc-284">Distancia de representación</span><span class="sxs-lookup"><span data-stu-id="817bc-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="817bc-285">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="817bc-286">Uso de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-286">Use of spatial sound</span></span>

<span data-ttu-id="817bc-287">En Windows Mixed Reality, el motor de audio proporciona el componente aural de la experiencia de realidad mixta mediante la simulación de un sonido 3D mediante simulaciones de dirección, distancia y entorno.</span><span class="sxs-lookup"><span data-stu-id="817bc-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="817bc-288">El uso de un sonido espacial en una aplicación permite a los desarrolladores colocar los sonidos de forma convincente en un espacio tridimensional (esfera) alrededor del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="817bc-289">Después, esos sonidos parecerán como si provinieran de objetos físicos reales o los hologramas de realidad mixta en el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="817bc-290">El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="817bc-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-291">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-292"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-293"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-293"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-294">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-294">✔️</span></span></td>
        <td><span data-ttu-id="817bc-295">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-296">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-296">Quality criteria</span></span>

|  <span data-ttu-id="817bc-297">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-297">Best</span></span>  |  <span data-ttu-id="817bc-298">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-298">Meets</span></span> |  <span data-ttu-id="817bc-299">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-300">El sonido está espacial lógicamente y la experiencia de usuario usa correctamente el sonido para ayudar con la detección de objetos y los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="817bc-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="817bc-301">El sonido es natural y relevante para los objetos y se normaliza en el escenario.</span><span class="sxs-lookup"><span data-stu-id="817bc-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="817bc-302">El audio espacial se utiliza de forma adecuada para aumentar la capacidad de respuesta, pero falta como medio para ayudar con los comentarios de los usuarios y la detectabilidad.</span><span class="sxs-lookup"><span data-stu-id="817bc-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="817bc-303">El sonido no está espacialmente como se esperaba o falta de sonido para ayudar al usuario dentro de la experiencia de usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="817bc-304">O el audio espacial no se consideró ni usó en el diseño del escenario.</span><span class="sxs-lookup"><span data-stu-id="817bc-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-305">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-305">How to measure</span></span>

* <span data-ttu-id="817bc-306">En general, los sonidos relevantes deben emitirse desde los hologramas de destino (por ejemplo, el sonido de corteza procedente de holográfica Dog).</span><span class="sxs-lookup"><span data-stu-id="817bc-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="817bc-307">Deben usarse señales sonoras en toda la experiencia del usuario para ayudar al usuario a realizar comentarios o a conocer las acciones que se encuentran fuera del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="817bc-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-308">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-308">Recommendations</span></span>

* <span data-ttu-id="817bc-309">Use el audio espacial para ayudar con la detección de objetos y las interfaces de usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="817bc-310">Los sonidos reales funcionan mejor que la síntesis o el sonido no natural.</span><span class="sxs-lookup"><span data-stu-id="817bc-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="817bc-311">La mayoría de los sonidos deben ser espaciales.</span><span class="sxs-lookup"><span data-stu-id="817bc-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="817bc-312">Evite los emisores invisibles.</span><span class="sxs-lookup"><span data-stu-id="817bc-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="817bc-313">Evite el enmascaramiento espacial.</span><span class="sxs-lookup"><span data-stu-id="817bc-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="817bc-314">Normalizar todos los sonidos.</span><span class="sxs-lookup"><span data-stu-id="817bc-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-315">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-316">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-316">Documentation</span></span>

* [<span data-ttu-id="817bc-317">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="817bc-318">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="817bc-319">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="817bc-320">Caso práctico, sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="817bc-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="817bc-321">Caso práctico, uso de sonido espacial en RoboRaid</span><span class="sxs-lookup"><span data-stu-id="817bc-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-322">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-322">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-323">MR espacial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="817bc-324">MRToolkit, audio espacial</span><span class="sxs-lookup"><span data-stu-id="817bc-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="817bc-325">Centrarse en los límites de trama holográfica (hipertema)</span><span class="sxs-lookup"><span data-stu-id="817bc-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="817bc-326">Las experiencias de usuario bien diseñadas pueden crear y mantener un contexto útil del entorno virtual que se extiende alrededor de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="817bc-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="817bc-327">Mitigar el efecto de los límites de los hipertextos implica un diseño minucioso de la escala y el contexto del contenido, el uso de audio espacial, los sistemas de orientación y la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="817bc-328">Si se realiza correctamente, el usuario sentirá menos el límite de los límites de los subprocesos, a la vez que tiene una experiencia de aplicación cómoda.</span><span class="sxs-lookup"><span data-stu-id="817bc-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-329">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-329">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-330"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-331"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-331"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-332">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-332">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-333">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-333">Quality criteria</span></span>

|  <span data-ttu-id="817bc-334">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-334">Best</span></span>  |  <span data-ttu-id="817bc-335">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-335">Meets</span></span> |  <span data-ttu-id="817bc-336">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-337">El usuario nunca pierde el contexto y se siente cómodo.</span><span class="sxs-lookup"><span data-stu-id="817bc-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="817bc-338">Se proporciona asistencia contextual para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="817bc-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="817bc-339">Se proporcionan instrucciones de detección y visualización para los objetos que se encuentran fuera del marco.</span><span class="sxs-lookup"><span data-stu-id="817bc-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="817bc-340">En general, el diseño de movimiento y la escala de los hologramas son adecuados para una experiencia de visualización cómoda.</span><span class="sxs-lookup"><span data-stu-id="817bc-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="817bc-341">El usuario nunca pierde el contexto, pero es posible que se requiera movimiento de cuello adicional en situaciones limitadas.</span><span class="sxs-lookup"><span data-stu-id="817bc-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="817bc-342">En situaciones limitadas, la escala hace que los hologramas interrumpan el fotograma vertical u horizontal, lo que produce un movimiento de cuello para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="817bc-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="817bc-343">Es necesario que el usuario pierda el contexto o el movimiento de cuello coherente para ver los hologramas.</span><span class="sxs-lookup"><span data-stu-id="817bc-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="817bc-344">No hay ninguna guía de contexto para objetos holográficas grandes, el movimiento de objetos es fácil de perder fuera del marco sin ninguna guía de detección, o bien un holograma alto requiere un movimiento de cuello normal para verlo.</span><span class="sxs-lookup"><span data-stu-id="817bc-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-345">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-345">How to measure</span></span>

* <span data-ttu-id="817bc-346">El contexto de un holograma (grande) se pierde o no se entiende debido a que se recortan en los límites.</span><span class="sxs-lookup"><span data-stu-id="817bc-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="817bc-347">La ubicación de los hologramas es difícil de encontrar debido a la falta de directores de atención o al contenido que mueve y sale rápidamente del marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="817bc-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="817bc-348">El escenario requiere un movimiento de cabezal normal y repetitivo hacia arriba y hacia abajo para ver por completo un holograma que dé lugar a una fatiga del cuello.</span><span class="sxs-lookup"><span data-stu-id="817bc-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-349">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-349">Recommendations</span></span>

* <span data-ttu-id="817bc-350">Comience la experiencia con objetos pequeños que se ajusten al objeto de subproceso y, a continuación, transición con indicaciones visuales a versiones más grandes.</span><span class="sxs-lookup"><span data-stu-id="817bc-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="817bc-351">Use los directores de audio y atención espaciales para ayudar al usuario a encontrar contenido que está fuera del hipermismo.</span><span class="sxs-lookup"><span data-stu-id="817bc-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="817bc-352">En la medida de lo posible, evite los hologramas que recortan verticalmente el hipernivel.</span><span class="sxs-lookup"><span data-stu-id="817bc-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="817bc-353">Proporcionar al usuario orientación en la aplicación para obtener la mejor ubicación de visualización.</span><span class="sxs-lookup"><span data-stu-id="817bc-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-354">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-355">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-355">Documentation</span></span>

* [<span data-ttu-id="817bc-356">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="817bc-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="817bc-357">Caso práctico, aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="817bc-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="817bc-358">Escala de objetos y entornos</span><span class="sxs-lookup"><span data-stu-id="817bc-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="817bc-359">Cursores, indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="817bc-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="817bc-360">Referencias externas</span><span class="sxs-lookup"><span data-stu-id="817bc-360">External references</span></span>

* [<span data-ttu-id="817bc-361">Gran cantidad de ADO sobre el visual</span><span class="sxs-lookup"><span data-stu-id="817bc-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="817bc-362">El contenido reacciona a la posición del usuario</span><span class="sxs-lookup"><span data-stu-id="817bc-362">Content reacts to user position</span></span>

<span data-ttu-id="817bc-363">Los hologramas deben reaccionar a la posición del usuario aproximadamente de la misma manera que lo hacen los objetos "reales".</span><span class="sxs-lookup"><span data-stu-id="817bc-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="817bc-364">Una consideración de diseño importante son los elementos de la interfaz de usuario que no pueden suponer necesariamente que la posición de un usuario sea estacional y adaptarse al movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="817bc-365">El diseño de una aplicación que se adapta correctamente a la posición del usuario creará una experiencia más increíble y facilitará su uso.</span><span class="sxs-lookup"><span data-stu-id="817bc-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-366">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-366">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-367"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-368"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-368"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-369">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-369">✔️</span></span></td>
        <td><span data-ttu-id="817bc-370">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-370">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-371">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="817bc-372">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-372">Best</span></span> </td><td> <span data-ttu-id="817bc-373">El contenido y la interfaz de usuario se adaptan a las posiciones de los usuarios, lo que permite al usuario interactuar de forma natural con el contenido dentro del ámbito de movimiento esperado</span><span class="sxs-lookup"><span data-stu-id="817bc-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="817bc-374">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-374">Meets</span></span> </td><td> <span data-ttu-id="817bc-375">La interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave que requiere que el usuario ajuste su posición.</span><span class="sxs-lookup"><span data-stu-id="817bc-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="817bc-376">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="817bc-377">Los elementos de la interfaz de usuario se pierden o se bloquean durante el movimiento, lo que provoca que el usuario vuelva a los controles (o los busque) de una misma.</span><span class="sxs-lookup"><span data-stu-id="817bc-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="817bc-378">Los elementos de la interfaz de usuario limitan la vista del contenido principal.</span><span class="sxs-lookup"><span data-stu-id="817bc-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="817bc-379">El movimiento de la interfaz de usuario no está optimizado para ver la distancia y el momento, especialmente con elementos de interfaz <a href="billboarding-and-tag-along.md">de usuario de etiquetas</a> .</span><span class="sxs-lookup"><span data-stu-id="817bc-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="817bc-380">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-380">How to measure</span></span>

* <span data-ttu-id="817bc-381">Todas las medidas deben realizarse dentro de un ámbito razonable del escenario.</span><span class="sxs-lookup"><span data-stu-id="817bc-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="817bc-382">Aunque el movimiento del usuario variará, no intente engañar a la aplicación con un movimiento de usuario extremo.</span><span class="sxs-lookup"><span data-stu-id="817bc-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="817bc-383">En el caso de los elementos de la interfaz de usuario, los controles pertinentes deben estar disponibles independientemente del movimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="817bc-384">Por ejemplo, si el usuario está viendo y recorriendo un mapa 3D con zoom, el control de zoom debe estar disponible para el usuario independientemente de la ubicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-385">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-385">Recommendations</span></span>

* <span data-ttu-id="817bc-386">El usuario es la cámara y controla el movimiento.</span><span class="sxs-lookup"><span data-stu-id="817bc-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="817bc-387">Dejar que se controlen.</span><span class="sxs-lookup"><span data-stu-id="817bc-387">Let them drive.</span></span>
* <span data-ttu-id="817bc-388">Considere la posibilidad de mostrar los sistemas de texto y de menú que, de otro modo, podrían quedar bloqueados o desconocidos si un usuario tuviera que desplazarse.</span><span class="sxs-lookup"><span data-stu-id="817bc-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="817bc-389">Use la etiqueta junto con el contenido que debe seguir al usuario y, al mismo tiempo, permitir que el usuario vea lo que hay delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="817bc-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-390">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-391">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-391">Documentation</span></span>

* [<span data-ttu-id="817bc-392">Diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="817bc-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="817bc-393">Color, claro y material</span><span class="sxs-lookup"><span data-stu-id="817bc-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="817bc-394">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="817bc-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="817bc-395">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="817bc-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="817bc-396">Automovimiento y Locomotion de usuario</span><span class="sxs-lookup"><span data-stu-id="817bc-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-397">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-397">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-398">Entrada MR 210: mirada</span><span class="sxs-lookup"><span data-stu-id="817bc-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="817bc-399">Claridad de interacción de entrada</span><span class="sxs-lookup"><span data-stu-id="817bc-399">Input interaction clarity</span></span>

<span data-ttu-id="817bc-400">La claridad de la interacción de entrada es fundamental para el uso de una aplicación e incluye la coherencia de entrada, la capacidad de enfoque, la detectabilidad de los métodos de interacción.</span><span class="sxs-lookup"><span data-stu-id="817bc-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="817bc-401">El usuario debe poder usar las interacciones comunes de toda la plataforma sin tener que reaprender.</span><span class="sxs-lookup"><span data-stu-id="817bc-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="817bc-402">Si la aplicación tiene una entrada personalizada, debe comunicarse claramente y mostrarse.</span><span class="sxs-lookup"><span data-stu-id="817bc-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-403">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-403">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-404"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-405"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-405"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-406">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-406">✔️</span></span></td>
        <td><span data-ttu-id="817bc-407">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-407">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-408">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-408">Quality criteria</span></span>

|  <span data-ttu-id="817bc-409">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-409">Best</span></span>  |  <span data-ttu-id="817bc-410">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-410">Meets</span></span> |  <span data-ttu-id="817bc-411">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-412">Los métodos de interacción de entrada son coherentes con las [instrucciones](interaction-fundamentals.md)proporcionadas por Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="817bc-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="817bc-413">Cualquier entrada personalizada no debe ser redundante con entrada estándar (en lugar de usar la interacción estándar) y se debe comunicar y demostrar claramente al usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="817bc-414">Similar a lo mejor, pero las entradas personalizadas son redundantes con los métodos de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="817bc-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="817bc-415">El usuario puede seguir logrando el objetivo y el progreso a través de la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="817bc-416">Es difícil comprender la asignación de botones o métodos de entrada.</span><span class="sxs-lookup"><span data-stu-id="817bc-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="817bc-417">La entrada está muy personalizada, no es compatible con la entrada estándar, no hay instrucciones o probablemente cause problemas de fatiga y confort.</span><span class="sxs-lookup"><span data-stu-id="817bc-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-418">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-418">How to measure</span></span>

* <span data-ttu-id="817bc-419">La aplicación usa [métodos de entrada estándar](interaction-fundamentals.md) coherentes.</span><span class="sxs-lookup"><span data-stu-id="817bc-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="817bc-420">Si la aplicación tiene una entrada personalizada, se comunica claramente mediante:</span><span class="sxs-lookup"><span data-stu-id="817bc-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="817bc-421">Experiencia de primera ejecución</span><span class="sxs-lookup"><span data-stu-id="817bc-421">First-run experience</span></span>
* <span data-ttu-id="817bc-422">Pantallas de introducción</span><span class="sxs-lookup"><span data-stu-id="817bc-422">Introductory screens</span></span>
* <span data-ttu-id="817bc-423">Información de herramientas</span><span class="sxs-lookup"><span data-stu-id="817bc-423">Tooltips</span></span>
* <span data-ttu-id="817bc-424">Autocar manual</span><span class="sxs-lookup"><span data-stu-id="817bc-424">Hand coach</span></span>
* <span data-ttu-id="817bc-425">Sección de ayuda</span><span class="sxs-lookup"><span data-stu-id="817bc-425">Help section</span></span>
* <span data-ttu-id="817bc-426">Voz sobre</span><span class="sxs-lookup"><span data-stu-id="817bc-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-427">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-427">Recommendations</span></span>

* <span data-ttu-id="817bc-428">Utilice los métodos de entrada estándar siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="817bc-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="817bc-429">Proporcione demostraciones, tutoriales e información sobre herramientas para los métodos de entrada no estándar.</span><span class="sxs-lookup"><span data-stu-id="817bc-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="817bc-430">Use un modelo de interacción coherente en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-431">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-432">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-432">Documentation</span></span>

* [<span data-ttu-id="817bc-433">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="817bc-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="817bc-434">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="817bc-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="817bc-435">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="817bc-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="817bc-436">Cursores</span><span class="sxs-lookup"><span data-stu-id="817bc-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="817bc-437">Confort y mira</span><span class="sxs-lookup"><span data-stu-id="817bc-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="817bc-438">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="817bc-438">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="817bc-439">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-439">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="817bc-440">Guía de portabilidad de entrada para Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-440">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="817bc-441">Entrada desde teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-441">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="817bc-442">Mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-442">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="817bc-443">Gestos y controladores de movimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-443">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="817bc-444">Entrada de voz en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-444">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="817bc-445">Entrada desde teclado, ratón y controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="817bc-445">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="817bc-446">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="817bc-446">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="817bc-447">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="817bc-447">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="817bc-448">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="817bc-448">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-449">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-449">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-450">Caso práctico: el logro de más informática personal</span><span class="sxs-lookup"><span data-stu-id="817bc-450">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="817bc-451">Estudio de conversión: aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción</span><span class="sxs-lookup"><span data-stu-id="817bc-451">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="817bc-452">Aplicación de ejemplo: tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="817bc-452">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="817bc-453">Aplicación de ejemplo: módulo lunar</span><span class="sxs-lookup"><span data-stu-id="817bc-453">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="817bc-454">Entrada MR 210: mirada</span><span class="sxs-lookup"><span data-stu-id="817bc-454">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="817bc-455">Entrada MR 211: gestos</span><span class="sxs-lookup"><span data-stu-id="817bc-455">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="817bc-456">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="817bc-456">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="817bc-457">Objetos interactuables</span><span class="sxs-lookup"><span data-stu-id="817bc-457">Interactable objects</span></span>

<span data-ttu-id="817bc-458">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="817bc-458">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="817bc-459">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="817bc-459">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="817bc-460">Cualquier elemento puede ser un objeto interactuable que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="817bc-460">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="817bc-461">Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="817bc-461">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="817bc-462">Independientemente del formulario, los objetos interactivos deben ser claramente reconocibles por el usuario a través de las indicaciones de audio y visual.</span><span class="sxs-lookup"><span data-stu-id="817bc-462">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-463">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-463">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-464"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-465"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-465"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-466">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-466">✔️</span></span></td>
        <td><span data-ttu-id="817bc-467">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-467">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-468">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-468">Quality criteria</span></span>

|  <span data-ttu-id="817bc-469">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-469">Best</span></span>  |  <span data-ttu-id="817bc-470">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-470">Meets</span></span> |  <span data-ttu-id="817bc-471">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-471">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-472">Independientemente del formulario, los objetos interactuables se pueden reconocer a través de las indicaciones de audio y visual en tres Estados: inactivo, dirigido y seleccionado.</span><span class="sxs-lookup"><span data-stu-id="817bc-472">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="817bc-473">"Lo veo, por ejemplo, está claro y se usa de forma coherente en toda la experiencia.</span><span class="sxs-lookup"><span data-stu-id="817bc-473">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="817bc-474">Los objetos se escalan y distribuyen para permitir la finalización de errores de forma gratuita.</span><span class="sxs-lookup"><span data-stu-id="817bc-474">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="817bc-475">El usuario puede reconocer objetos como interactivos a través de comentarios de audio o visuales, y puede tener como destino y activar el objeto.</span><span class="sxs-lookup"><span data-stu-id="817bc-475">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="817bc-476">No se proporcionan indicaciones visuales o de audio, el usuario no puede reconocer un objeto interactuable.</span><span class="sxs-lookup"><span data-stu-id="817bc-476">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="817bc-477">Las interacciones son propensas a errores debido a la escala de objetos o a la distancia entre los objetos.</span><span class="sxs-lookup"><span data-stu-id="817bc-477">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-478">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-478">How to measure</span></span>

* <span data-ttu-id="817bc-479">Los objetos interactuables son reconocibles como ' interactuable '; incluir botones, menús y contenido específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="817bc-479">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="817bc-480">Como regla general, debe haber una indicación visual y de audio cuando el destino es objetos interactivos.</span><span class="sxs-lookup"><span data-stu-id="817bc-480">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-481">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-481">Recommendations</span></span>

* <span data-ttu-id="817bc-482">Use comentarios visuales y de audio para las interacciones.</span><span class="sxs-lookup"><span data-stu-id="817bc-482">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="817bc-483">Los comentarios visuales deben diferenciarse en cada estado de entrada (inactivo, dirigido, seleccionado)</span><span class="sxs-lookup"><span data-stu-id="817bc-483">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="817bc-484">Los objetos que se pueden interactuar deben escalarse y colocarse para los destinos sin errores.</span><span class="sxs-lookup"><span data-stu-id="817bc-484">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="817bc-485">Los objetos interactuables agrupados (por ejemplo, una barra de menús o una lista) deben tener el espaciado adecuado para el destino.</span><span class="sxs-lookup"><span data-stu-id="817bc-485">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="817bc-486">Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto para la palabra clave Command ("vea esto, dígalo")</span><span class="sxs-lookup"><span data-stu-id="817bc-486">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-487">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-487">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-488">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-488">Documentation</span></span>

* [<span data-ttu-id="817bc-489">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="817bc-489">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="817bc-490">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="817bc-490">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="817bc-491">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="817bc-491">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="817bc-492">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="817bc-492">Voice input</span></span>](voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-493">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-493">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-494">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="817bc-494">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="817bc-495">Detección de salas</span><span class="sxs-lookup"><span data-stu-id="817bc-495">Room scanning</span></span>

<span data-ttu-id="817bc-496">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="817bc-496">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="817bc-497">La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.</span><span class="sxs-lookup"><span data-stu-id="817bc-497">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="817bc-498">Muchas aplicaciones analizarán los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad del mapa espacial.</span><span class="sxs-lookup"><span data-stu-id="817bc-498">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="817bc-499">Si es necesario que el usuario analice el entorno, debe proporcionar instrucciones claras durante la experiencia de exploración.</span><span class="sxs-lookup"><span data-stu-id="817bc-499">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-500">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-500">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-501"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-502"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-502"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-503">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-503">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-504">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-504">Quality criteria</span></span>

|  <span data-ttu-id="817bc-505">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-505">Best</span></span>  |  <span data-ttu-id="817bc-506">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-506">Meets</span></span> |  <span data-ttu-id="817bc-507">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-507">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-508">Visualización de la malla espacial indique a los usuarios que el análisis está en curso.</span><span class="sxs-lookup"><span data-stu-id="817bc-508">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="817bc-509">El usuario sabe claramente qué hacer y cuándo se inicia y se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="817bc-509">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="817bc-510">Se proporciona la visualización de la malla espacial, pero es posible que el usuario no sepa claramente qué hacer y que no se proporcione información de progreso.</span><span class="sxs-lookup"><span data-stu-id="817bc-510">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="817bc-511">Ninguna visualización de malla.</span><span class="sxs-lookup"><span data-stu-id="817bc-511">No visualization of mesh.</span></span> <span data-ttu-id="817bc-512">No se proporciona información de orientación al usuario sobre dónde buscar, o Cuándo se inicia o se detiene el examen.</span><span class="sxs-lookup"><span data-stu-id="817bc-512">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="817bc-513">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-513">How to measure</span></span>

* <span data-ttu-id="817bc-514">Durante un examen de habitación necesario, se proporciona orientación visual y de audio que indica dónde buscar y cuándo iniciar y detener el examen.</span><span class="sxs-lookup"><span data-stu-id="817bc-514">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-515">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-515">Recommendations</span></span>

* <span data-ttu-id="817bc-516">Indique la cantidad del volumen total de los usuarios que debe formar parte de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="817bc-516">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="817bc-517">Comunicarse cuando el examen se inicia y se detiene, como un indicador de progreso.</span><span class="sxs-lookup"><span data-stu-id="817bc-517">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="817bc-518">Use una visualización de la malla durante el examen.</span><span class="sxs-lookup"><span data-stu-id="817bc-518">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="817bc-519">Proporcione guías de audio y visual para animar al usuario a buscar y desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="817bc-519">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="817bc-520">Informe al usuario de dónde debe ir para mejorar los datos.</span><span class="sxs-lookup"><span data-stu-id="817bc-520">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="817bc-521">En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="817bc-521">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-522">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-522">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="817bc-523">Documentación</span><span class="sxs-lookup"><span data-stu-id="817bc-523">Documentation</span></span>

* [<span data-ttu-id="817bc-524">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="817bc-524">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="817bc-525">Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="817bc-525">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="817bc-526">Caso práctico: diseño de sonido espacial para HoloTour</span><span class="sxs-lookup"><span data-stu-id="817bc-526">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="817bc-527">Caso práctico: creación de una experiencia envolvente en fragmentos</span><span class="sxs-lookup"><span data-stu-id="817bc-527">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="817bc-528">Herramientas y tutoriales</span><span class="sxs-lookup"><span data-stu-id="817bc-528">Tools and tutorials</span></span>

* [<span data-ttu-id="817bc-529">Kit de herramientas de realidad mixta-UX</span><span class="sxs-lookup"><span data-stu-id="817bc-529">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="817bc-530">Indicadores direccionales</span><span class="sxs-lookup"><span data-stu-id="817bc-530">Directional indicators</span></span>

<span data-ttu-id="817bc-531">En una aplicación de realidad mixta, el contenido puede estar fuera del campo de vista o ocluidos por objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="817bc-531">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="817bc-532">Una aplicación bien diseñada facilitará a los usuarios la búsqueda de contenido no visible.</span><span class="sxs-lookup"><span data-stu-id="817bc-532">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="817bc-533">Los indicadores direccionales avisan a un usuario de contenido importante y proporcionan orientación sobre el contenido en relación con la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-533">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="817bc-534">Las instrucciones para el contenido no visible pueden adoptar la forma de emisores de sonido, flechas direccionales o indicaciones visuales directas.</span><span class="sxs-lookup"><span data-stu-id="817bc-534">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-535">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-535">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-536"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-537"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-537"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-538">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-538">✔️</span></span></td>
        <td><span data-ttu-id="817bc-539">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-539">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-540">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-540">Quality criteria</span></span>

|  <span data-ttu-id="817bc-541">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-541">Best</span></span>  |  <span data-ttu-id="817bc-542">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-542">Meets</span></span> |  <span data-ttu-id="817bc-543">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-543">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-544">Las guías de audio y visual guían directamente al usuario al contenido relevante fuera del campo de vista.</span><span class="sxs-lookup"><span data-stu-id="817bc-544">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="817bc-545">Una flecha o algún indicador que apunta al usuario en la dirección general del contenido.</span><span class="sxs-lookup"><span data-stu-id="817bc-545">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="817bc-546">El contenido relevante está fuera del campo de vista y no se proporciona ninguna guía de ubicación para el usuario.</span><span class="sxs-lookup"><span data-stu-id="817bc-546">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="817bc-547">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-547">How to measure</span></span>

* <span data-ttu-id="817bc-548">El contenido relevante fuera del campo de vista de usuario se detecta mediante señales de audio o visual.</span><span class="sxs-lookup"><span data-stu-id="817bc-548">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-549">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-549">Recommendations</span></span>

* <span data-ttu-id="817bc-550">Cuando el contenido pertinente esté fuera del campo de vista del usuario, use indicadores direccionales e indicaciones de audio para guiar al usuario al contenido.</span><span class="sxs-lookup"><span data-stu-id="817bc-550">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="817bc-551">En muchos casos, se prefiere una guía visual directa a las flechas direccionales.</span><span class="sxs-lookup"><span data-stu-id="817bc-551">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="817bc-552">Los indicadores direccionales no se deben integrar en el cursor.</span><span class="sxs-lookup"><span data-stu-id="817bc-552">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-553">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-553">Resources</span></span>

* [<span data-ttu-id="817bc-554">Marco holográfico</span><span class="sxs-lookup"><span data-stu-id="817bc-554">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="817bc-555">Carga de datos</span><span class="sxs-lookup"><span data-stu-id="817bc-555">Data loading</span></span>

<span data-ttu-id="817bc-556">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="817bc-556">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="817bc-557">Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto tiempo puede ser el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="817bc-557">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="817bc-558">Impacto del dispositivo</span><span class="sxs-lookup"><span data-stu-id="817bc-558">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="817bc-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-559"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="817bc-560"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="817bc-560"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="817bc-561">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-561">✔️</span></span></td>
        <td><span data-ttu-id="817bc-562">✔️</span><span class="sxs-lookup"><span data-stu-id="817bc-562">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="817bc-563">Criterios de calidad</span><span class="sxs-lookup"><span data-stu-id="817bc-563">Quality criteria</span></span>

|  <span data-ttu-id="817bc-564">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="817bc-564">Best</span></span>  |  <span data-ttu-id="817bc-565">Reúne</span><span class="sxs-lookup"><span data-stu-id="817bc-565">Meets</span></span> |  <span data-ttu-id="817bc-566">Puedan</span><span class="sxs-lookup"><span data-stu-id="817bc-566">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="817bc-567">Indicador visual animado, en forma de una barra de progreso o un anillo, que muestra el progreso durante cualquier carga o procesamiento de datos.</span><span class="sxs-lookup"><span data-stu-id="817bc-567">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="817bc-568">El indicador visual proporciona instrucciones sobre cuánto tiempo puede ser la espera.</span><span class="sxs-lookup"><span data-stu-id="817bc-568">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="817bc-569">Se informa al usuario de que la carga de datos está en curso, pero no hay ninguna indicación de cuánto tiempo podría ser la espera.</span><span class="sxs-lookup"><span data-stu-id="817bc-569">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="817bc-570">No hay ningún indicador de carga de datos o de proceso para que la tarea tarde más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="817bc-570">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="817bc-571">Cómo medir</span><span class="sxs-lookup"><span data-stu-id="817bc-571">How to measure</span></span>

* <span data-ttu-id="817bc-572">Durante la carga de datos, compruebe que no hay ningún estado en blanco durante más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="817bc-572">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="817bc-573">Recomendaciones</span><span class="sxs-lookup"><span data-stu-id="817bc-573">Recommendations</span></span>

* <span data-ttu-id="817bc-574">Proporcionar un animador de carga de datos que muestre el progreso en cualquier situación en la que el usuario pueda percibir que esta aplicación se haya detenido o bloqueado.</span><span class="sxs-lookup"><span data-stu-id="817bc-574">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="817bc-575">Una regla general razonable es cualquier actividad de "carga" que podría tardar más de 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="817bc-575">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="817bc-576">Recursos</span><span class="sxs-lookup"><span data-stu-id="817bc-576">Resources</span></span>

* [<span data-ttu-id="817bc-577">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="817bc-577">Displaying progress</span></span>](progress.md)
