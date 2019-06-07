---
title: Introducción a MRTK versión 2
description: Para los nuevos desarrolladores interesados en aprovechar MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, probar, Kit de herramientas de realidad mixta, MRTK versión 2, MRTK, herramientas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750377"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="bcb19-104">Introducción a MRTK v2</span><span class="sxs-lookup"><span data-stu-id="bcb19-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="bcb19-105">MRTK Guía de introducción</span><span class="sxs-lookup"><span data-stu-id="bcb19-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="bcb19-106">Consulte la [MRTK Guía de introducción](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obtener información sobre cómo comenzar con MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="bcb19-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="bcb19-107">¿Qué es el Kit de herramientas de realidad mixta (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="bcb19-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="bcb19-108">El MRTK es un Kit de herramientas increíbles de código abierto que ha estado presente desde el HoloLens publicó por primera vez y no sería donde se encuentra hoy sin el trabajo duro de nuestra comunidad de desarrolladores que han contribuido a él.</span><span class="sxs-lookup"><span data-stu-id="bcb19-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="bcb19-109">Durante los últimos 3 años, hemos tenido en cuenta los comentarios de nuestra comunidad de desarrolladores y generado MRTK v2 para las principales preocupaciones de tener en cuenta.</span><span class="sxs-lookup"><span data-stu-id="bcb19-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="bcb19-110">La versión 2 MRTK con Unity es un kit de desarrollo multiplataforma de código abierto para las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="bcb19-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="bcb19-111">MRTK versión 2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, inmersivos (VR) Windows Mixed Reality y OpenVR plataforma.</span><span class="sxs-lookup"><span data-stu-id="bcb19-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="bcb19-112">El proyecto está destinado a reducir las barreras de entrada para crear aplicaciones de realidad mixta y contribuir a la Comunidad que todos a medida que crecen.</span><span class="sxs-lookup"><span data-stu-id="bcb19-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="bcb19-113">Consulte la [portal de documentación MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="bcb19-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="bcb19-114">Áreas de características</span><span class="sxs-lookup"><span data-stu-id="bcb19-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> <span data-ttu-id="bcb19-116">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="bcb19-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Mano de seguimiento (HoloLens 2)" width="105"> <span data-ttu-id="bcb19-118">Mano de seguimiento (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="bcb19-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Seguimiento (HoloLens 2) de los ojos" width="105">
    <span data-ttu-id="bcb19-120">Seguimiento (HoloLens 2) de los ojos</span><span class="sxs-lookup"><span data-stu-id="bcb19-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comandos de voz" width="105"> <span data-ttu-id="bcb19-122">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="bcb19-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Observación + seleccionar (HoloLens (gen 1))" width="105">
    <span data-ttu-id="bcb19-124">Observación + seleccionar (HoloLens (gen 1))</span><span class="sxs-lookup"><span data-stu-id="bcb19-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> <span data-ttu-id="bcb19-126">Teleportation</span><span class="sxs-lookup"><span data-stu-id="bcb19-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de la interfaz de usuario" width="105"> <span data-ttu-id="bcb19-128">Controles de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="bcb19-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver e interacciones" width="105"> <span data-ttu-id="bcb19-130">Solver e interacciones</span><span class="sxs-lookup"><span data-stu-id="bcb19-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualización de controlador" width="105"> <span data-ttu-id="bcb19-132">Visualización de controlador</span><span class="sxs-lookup"><span data-stu-id="bcb19-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Understanding espacial" width="105"> <span data-ttu-id="bcb19-134">Understanding espacial</span><span class="sxs-lookup"><span data-stu-id="bcb19-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Herramienta de diagnóstico" width="105"> <span data-ttu-id="bcb19-136">Herramienta de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="bcb19-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador MRTK estándar" width="105"> <span data-ttu-id="bcb19-138">Sombreador MRTK estándar</span><span class="sxs-lookup"><span data-stu-id="bcb19-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="bcb19-139">Bloques de interfaz de usuario y la creación de interacción</span><span class="sxs-lookup"><span data-stu-id="bcb19-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botón" width="250"><br>
    <span data-ttu-id="bcb19-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="bcb19-141">**Button**</span></span><br>
    <span data-ttu-id="bcb19-142">Un control de botón que admite varios métodos de entrada, incluyendo mano articulado del 2 de HoloLens <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Cuadro de límite" width="250"><br>
    <span data-ttu-id="bcb19-144">**Cuadro de límite**</span><span class="sxs-lookup"><span data-stu-id="bcb19-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="bcb19-145">Interfaz de usuario estándar para manipular objetos en el espacio 3D <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Controlador de manipulación" width="250"><br>
    <span data-ttu-id="bcb19-147">**Controlador de manipulación**</span><span class="sxs-lookup"><span data-stu-id="bcb19-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="bcb19-148">Secuencia de comandos para manipular objetos con uno o dos manos <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Pizarra" width="250"><br>
    <span data-ttu-id="bcb19-150">**Slate**</span><span class="sxs-lookup"><span data-stu-id="bcb19-150">**Slate**</span></span> <br>
    <span data-ttu-id="bcb19-151">Plano 2D de estilo que admite el desplazamiento con la entrada de la mano articulados <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado del sistema" width="250"><br>
    <span data-ttu-id="bcb19-153">**Teclado del sistema**</span><span class="sxs-lookup"><span data-stu-id="bcb19-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="bcb19-154">Script de ejemplo de usar el teclado del sistema en Unity <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interactuable" width="250"><br>
     <span data-ttu-id="bcb19-156">**Interactable**</span><span class="sxs-lookup"><span data-stu-id="bcb19-156">**Interactable**</span></span> <br>
     <span data-ttu-id="bcb19-157">Una secuencia de comandos para hacer que los objetos interactuable con estados visuales y compatibilidad de tema <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    <span data-ttu-id="bcb19-159">**Solver**</span><span class="sxs-lookup"><span data-stu-id="bcb19-159">**Solver**</span></span> <br>
    <span data-ttu-id="bcb19-160">Distintos comportamientos de posicionamiento como tag-along, bloqueo de cuerpo, tamaño de la vista constante y superficie magnética de objeto <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Colección de objetos" width="250"><br>
    <span data-ttu-id="bcb19-162">**Colección de objetos**</span><span class="sxs-lookup"><span data-stu-id="bcb19-162">**Object Collection**</span></span><br>
    <span data-ttu-id="bcb19-163">Secuencia de comandos para disponer de una matriz de objetos de una forma tridimensional <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Información sobre herramientas" width="250">  <br>
    <span data-ttu-id="bcb19-165">**Información sobre herramientas**</span><span class="sxs-lookup"><span data-stu-id="bcb19-165">**Tooltip**</span></span><br>
    <span data-ttu-id="bcb19-166">Anotación de la interfaz de usuario con el sistema delimitador/pivot flexible que puede utilizarse para etiquetar el objeto y los controladores de movimiento <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de la aplicación" width="250"><br>
    <span data-ttu-id="bcb19-168">**Barra de la aplicación**</span><span class="sxs-lookup"><span data-stu-id="bcb19-168">**App Bar**</span></span><br>
    <span data-ttu-id="bcb19-169">Interfaz de usuario para la activación manual del cuadro de límite <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Punteros" width="250"><br>
    <span data-ttu-id="bcb19-171">**Punteros**</span><span class="sxs-lookup"><span data-stu-id="bcb19-171">**Pointers**</span></span><br>
    <span data-ttu-id="bcb19-172">Obtenga información sobre los distintos tipos de punteros <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualización de la yema del dedo" width="250"><br>
     <span data-ttu-id="bcb19-174">**Visualización de la yema del dedo**</span><span class="sxs-lookup"><span data-stu-id="bcb19-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="bcb19-175">Prestación Visual de la yema del dedo que mejora la confianza para la interacción directa <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="bcb19-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="bcb19-177">**Slider**</span></span><br>
    <span data-ttu-id="bcb19-178">Control deslizante de la interfaz de usuario para ajustar los valores auxiliar mano directo interacción de seguimiento <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador MRTK estándar" width="250"><br>
    <span data-ttu-id="bcb19-180">**Sombreador MRTK estándar**</span><span class="sxs-lookup"><span data-stu-id="bcb19-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="bcb19-181">Sombreador de estándar de MRTK es compatible con diversos elementos de diseño Fluent con rendimiento <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Chaser conjunta de mano" width="250"><br>
     <span data-ttu-id="bcb19-183">**Chaser conjunta de mano**</span><span class="sxs-lookup"><span data-stu-id="bcb19-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="bcb19-184">Muestra cómo usar Solver para asociar objetos a los puntos de unión de mano <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Seguimiento de los ojos: Selección de destino" width="250"><br>
    <span data-ttu-id="bcb19-186">**Seguimiento de los ojos: Selección de destino**</span><span class="sxs-lookup"><span data-stu-id="bcb19-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="bcb19-187">Combinar los ojos, voz y mano rápidamente y sin esfuerzo seleccionar hologramas a través de la escena de entrada <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Seguimiento de los ojos: Navegación" width="250"><br>
    <span data-ttu-id="bcb19-189">**Seguimiento de los ojos: Navegación**</span><span class="sxs-lookup"><span data-stu-id="bcb19-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="bcb19-190">Obtenga información sobre cómo desplazarse por el texto de auto o zoom con fluidez en contenido centrado en función de lo que se trata de <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Seguimiento de los ojos: Mapa térmico" width="250"><br>
    <span data-ttu-id="bcb19-192">**Seguimiento de los ojos: Mapa térmico**</span><span class="sxs-lookup"><span data-stu-id="bcb19-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="bcb19-193">Ejemplos para el registro, cargar y visualizar qué usuarios han empezado a en la aplicación <a/></span><span class="sxs-lookup"><span data-stu-id="bcb19-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="bcb19-194">Requisito mínimo para MRTK v2</span><span class="sxs-lookup"><span data-stu-id="bcb19-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="bcb19-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="bcb19-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="bcb19-196">Microsoft Visual Studio 2017 o posterior</span><span class="sxs-lookup"><span data-stu-id="bcb19-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="bcb19-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="bcb19-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="bcb19-198">Windows 10 1803 o posterior</span><span class="sxs-lookup"><span data-stu-id="bcb19-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="bcb19-199">Nuevo con MRTK v2</span><span class="sxs-lookup"><span data-stu-id="bcb19-199">New with MRTK v2</span></span>
<span data-ttu-id="bcb19-200">Queremos hacer hincapié en nuestro compromiso con estas herramientas de plataforma.</span><span class="sxs-lookup"><span data-stu-id="bcb19-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="bcb19-201">De hecho, hemos aprovechado MRTK versión 2 para desarrollar nuestras experiencias de bandeja de entrada, como la experiencia de instalación (OOBE) y nuestra aplicación de aprendizaje de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="bcb19-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="bcb19-202">También puede esperar ver nuevas capacidades de HoloLens 2 que primero se expone a través de MRTK porque creemos que es la mejor manera de desarrollar en nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="bcb19-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="bcb19-203">Modular</span><span class="sxs-lookup"><span data-stu-id="bcb19-203">Modular</span></span>
<span data-ttu-id="bcb19-204">Hemos creado, de manera modular, por lo que no es necesario tener cada bit del Kit de herramientas en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="bcb19-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="bcb19-205">Existen realmente algunas ventajas a este.</span><span class="sxs-lookup"><span data-stu-id="bcb19-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="bcb19-206">Mantiene el tamaño del proyecto más pequeños, así como hace que sea más fácil de administrar.</span><span class="sxs-lookup"><span data-stu-id="bcb19-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="bcb19-207">En él, porque se ha creado teniendo objetos programables y está controlada de interfaz, también es posible para reemplazar los componentes que se incluyen con su propio para admitir otros servicios, sistemas y plataformas.</span><span class="sxs-lookup"><span data-stu-id="bcb19-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="bcb19-208">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="bcb19-208">Cross-platform</span></span>
<span data-ttu-id="bcb19-209">Hablando de otras plataformas, tiene la compatibilidad multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="bcb19-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="bcb19-210">Y aunque esto no significa que todas las plataformas solo es compatible de fábrica, nos hemos asegurado de que ninguno de los códigos de Kit de herramientas se interrumpirá cuando cambie su destino de compilación para otras plataformas.</span><span class="sxs-lookup"><span data-stu-id="bcb19-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="bcb19-211">La solidez y la extensibilidad con el diseño modular configura en una ruta de acceso válida para poder admitir varias plataformas, como ARCore, ARKit y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="bcb19-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="bcb19-212">Alto rendimiento</span><span class="sxs-lookup"><span data-stu-id="bcb19-212">Performant</span></span>
<span data-ttu-id="bcb19-213">Trabajar con las plataformas móviles, se construyó con miras al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="bcb19-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="bcb19-214">Esto es muy importante, y deseamos asegurarnos de que las herramientas no se van a funcionar en su contra.</span><span class="sxs-lookup"><span data-stu-id="bcb19-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="bcb19-215">Vea también</span><span class="sxs-lookup"><span data-stu-id="bcb19-215">See also</span></span>
* [<span data-ttu-id="bcb19-216">Guía de introducción de MRTK</span><span class="sxs-lookup"><span data-stu-id="bcb19-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="bcb19-217">Documentación de MRTK principal</span><span class="sxs-lookup"><span data-stu-id="bcb19-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="bcb19-218">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="bcb19-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="bcb19-219">Portabilidad de HTK/MRTK a MRTK versión 2</span><span class="sxs-lookup"><span data-stu-id="bcb19-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
