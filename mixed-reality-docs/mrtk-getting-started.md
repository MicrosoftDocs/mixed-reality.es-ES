---
title: Introducción a la versión 2 de MRTK
description: Para los nuevos desarrolladores interesados en aprovechar MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, test, kit de herramientas de realidad mixta, MRTK versión 2, MRTK, herramientas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 7eded2c766765a5ccebf741eed2f8b7fe8f65a93
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507930"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="0c4a7-104">Introducción a MRTK V2</span><span class="sxs-lookup"><span data-stu-id="0c4a7-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="0c4a7-105">Guía de Introducción de MRTK</span><span class="sxs-lookup"><span data-stu-id="0c4a7-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="0c4a7-106">Vea la [Guía de introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obtener información sobre cómo empezar a usar MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="0c4a7-107">¿Qué es el kit de herramientas de realidad mixta (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="0c4a7-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="0c4a7-108">MRTK es un increíble kit de herramientas de código abierto que ha estado de la primera vez que se lanzó HoloLens, y no sería el lugar en el que se encontraba hoy sin el trabajo de nuestra comunidad de desarrolladores que ha contribuido.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="0c4a7-109">Durante los últimos 3 años, hemos escuchado los comentarios de nuestra comunidad de desarrolladores y hemos creado MRTK v2 para tener en cuenta las preocupaciones más importantes.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="0c4a7-110">MRTK V2 con Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="0c4a7-111">La versión 2 de MRTK está pensada para acelerar el desarrollo de aplicaciones que tienen como destino Microsoft HoloLens, auriculares con Windows Mixed Reality inmersivo (VR) y plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="0c4a7-112">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="0c4a7-113">Consulte el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="0c4a7-114">Áreas de características</span><span class="sxs-lookup"><span data-stu-id="0c4a7-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> <span data-ttu-id="0c4a7-116">Sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="0c4a7-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Seguimiento de mano (HoloLens 2)" width="105"> <span data-ttu-id="0c4a7-118">Seguimiento de mano (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="0c4a7-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Seguimiento ocular (HoloLens 2)" width="105">
    <span data-ttu-id="0c4a7-120">Seguimiento ocular (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="0c4a7-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comandos de voz" width="105"> <span data-ttu-id="0c4a7-122">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="0c4a7-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Mira y seleccionar (HoloLens (1ª generación))" width="105">
    <span data-ttu-id="0c4a7-124">Mira y seleccionar (HoloLens (1ª generación))</span><span class="sxs-lookup"><span data-stu-id="0c4a7-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teletraslado" width="105"> <span data-ttu-id="0c4a7-126">Teletraslado</span><span class="sxs-lookup"><span data-stu-id="0c4a7-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de la interfaz de usuario" width="105"> <span data-ttu-id="0c4a7-128">Controles de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="0c4a7-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver e interacciones" width="105"> <span data-ttu-id="0c4a7-130">Solver e interacciones</span><span class="sxs-lookup"><span data-stu-id="0c4a7-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualización del controlador" width="105"> <span data-ttu-id="0c4a7-132">Visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="0c4a7-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Descripción espacial" width="105"> <span data-ttu-id="0c4a7-134">Descripción espacial</span><span class="sxs-lookup"><span data-stu-id="0c4a7-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Herramienta de diagnóstico" width="105"> <span data-ttu-id="0c4a7-136">Herramienta de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="0c4a7-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador estándar de MRTK" width="105"> <span data-ttu-id="0c4a7-138">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="0c4a7-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="0c4a7-139">Bloques de creación de interfaces de usuario e interacción</span><span class="sxs-lookup"><span data-stu-id="0c4a7-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botón" width="250"><br>
    <span data-ttu-id="0c4a7-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-141">**Button**</span></span><br>
    <span data-ttu-id="0c4a7-142">Control de botón que admite varios métodos de entrada, incluida la mano articulada de HoloLens 2.<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Cuadro de límite" width="250"><br>
    <span data-ttu-id="0c4a7-144">**Cuadro de límite**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="0c4a7-145">Interfaz de usuario estándar para manipular objetos en el espacio 3D<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Controlador de manipulación" width="250"><br>
    <span data-ttu-id="0c4a7-147">**Controlador de manipulación**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="0c4a7-148">Script para manipular objetos con una o dos manos<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Tabletas" width="250"><br>
    <span data-ttu-id="0c4a7-150">**Tabletas**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-150">**Slate**</span></span> <br>
    <span data-ttu-id="0c4a7-151">plano de estilo 2D que admite el desplazamiento con entrada de mano articulada<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado del sistema" width="250"><br>
    <span data-ttu-id="0c4a7-153">**Teclado del sistema**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="0c4a7-154">Script de ejemplo de uso del teclado del sistema en Unity<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interactuable" width="250"><br>
     <span data-ttu-id="0c4a7-156">**Interactuable**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-156">**Interactable**</span></span> <br>
     <span data-ttu-id="0c4a7-157">Un script para que los objetos interactúen con los Estados visuales y la compatibilidad con temas<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solucionador" width="250"><br>
    <span data-ttu-id="0c4a7-159">**Solucionador**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-159">**Solver**</span></span> <br>
    <span data-ttu-id="0c4a7-160">Varios comportamientos de posicionamiento de objetos, como etiqueta, el bloqueo del cuerpo, el tamaño de la vista constante y el magnetismo de superficie<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Colección de objetos" width="250"><br>
    <span data-ttu-id="0c4a7-162">**Colección de objetos**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-162">**Object Collection**</span></span><br>
    <span data-ttu-id="0c4a7-163">Script para diseñar una matriz de objetos en una forma tridimensional<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Información sobre herramientas" width="250">  <br>
    <span data-ttu-id="0c4a7-165">**Herramienta**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-165">**Tooltip**</span></span><br>
    <span data-ttu-id="0c4a7-166">Interfaz de usuario de anotación con sistema de delimitador/dinamización flexible que se puede usar para etiquetar controladores de movimiento y objetos<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de la aplicación" width="250"><br>
    <span data-ttu-id="0c4a7-168">**Barra de la aplicación**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-168">**App Bar**</span></span><br>
    <span data-ttu-id="0c4a7-169">Interfaz de usuario para la activación manual del cuadro de límite<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Punteros" width="250"><br>
    <span data-ttu-id="0c4a7-171">**Punteros**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-171">**Pointers**</span></span><br>
    <span data-ttu-id="0c4a7-172">Más información sobre los distintos tipos de punteros<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualización del dedo" width="250"><br>
     <span data-ttu-id="0c4a7-174">**Visualización del dedo**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="0c4a7-175">La asequibilidad visual de la mano, lo que mejora la confianza para la interacción directa<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    <span data-ttu-id="0c4a7-177">**Slider**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-177">**Slider**</span></span><br>
    <span data-ttu-id="0c4a7-178">Interfaz de usuario del control deslizante para ajustar los valores que admiten la interacción directa de seguimiento<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador estándar de MRTK" width="250"><br>
    <span data-ttu-id="0c4a7-180">**Sombreador estándar de MRTK**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="0c4a7-181">El sombreador estándar de MRTK admite varios elementos de diseño fluidas con rendimiento<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Persecución de mano" width="250"><br>
     <span data-ttu-id="0c4a7-183">**Persecución de mano**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="0c4a7-184">Muestra cómo usar Solver para adjuntar objetos a las uniones a mano<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Seguimiento ocular: Selección de destino" width="250"><br>
    <span data-ttu-id="0c4a7-186">**Seguimiento ocular: Selección de destino**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="0c4a7-187">Combine los ojos, la voz y la entrada a mano para seleccionar los hologramas de forma rápida y sencilla a través de la escena<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Seguimiento ocular: Navegación" width="250"><br>
    <span data-ttu-id="0c4a7-189">**Seguimiento ocular: Explora**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="0c4a7-190">Obtenga información acerca de Cómo desplazarse por texto automáticamente o acercar el contenido centrado en función de lo que está examinando<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Seguimiento ocular: Mapa térmico" width="250"><br>
    <span data-ttu-id="0c4a7-192">**Seguimiento ocular: Mapa térmico**</span><span class="sxs-lookup"><span data-stu-id="0c4a7-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="0c4a7-193">Ejemplos de registro, carga y visualización de lo que los usuarios han estado examinando en la aplicación<a/></span><span class="sxs-lookup"><span data-stu-id="0c4a7-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="0c4a7-194">Requisito mínimo para MRTK V2</span><span class="sxs-lookup"><span data-stu-id="0c4a7-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="0c4a7-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="0c4a7-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="0c4a7-196">Microsoft Visual Studio 2017 o posterior</span><span class="sxs-lookup"><span data-stu-id="0c4a7-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="0c4a7-197">Windows SDK 18362 +</span><span class="sxs-lookup"><span data-stu-id="0c4a7-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="0c4a7-198">Windows 10 1803 o posterior</span><span class="sxs-lookup"><span data-stu-id="0c4a7-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="0c4a7-199">Novedad con MRTK V2</span><span class="sxs-lookup"><span data-stu-id="0c4a7-199">New with MRTK v2</span></span>
<span data-ttu-id="0c4a7-200">Queremos someter nuestro compromiso a estas herramientas de plataforma.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="0c4a7-201">De hecho, aprovechamos la versión 2 de MRTK para desarrollar nuestras experiencias de bandeja de entrada, como la experiencia de instalación (OOBE) y nuestra aplicación de aprendizaje de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="0c4a7-202">También puede esperar ver las nuevas funcionalidades de HoloLens 2 que se exponen por primera vez a través de MRTK porque creemos que es la mejor manera de desarrollar en nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="0c4a7-203">Módulos</span><span class="sxs-lookup"><span data-stu-id="0c4a7-203">Modular</span></span>
<span data-ttu-id="0c4a7-204">Se ha creado de forma modular, por lo que no es necesario realizar cada bit del kit de herramientas en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="0c4a7-205">En realidad, hay algunas ventajas.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="0c4a7-206">Permite reducir el tamaño del proyecto, así como facilitar la administración.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="0c4a7-207">Además, dado que se crea con objetos que admiten scripts y está orientado a la interfaz, también es posible reemplazar los componentes que se incluyen por su cuenta, para admitir otros servicios, sistemas y plataformas.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="0c4a7-208">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="0c4a7-208">Cross-platform</span></span>
<span data-ttu-id="0c4a7-209">Hablando de otras plataformas, tiene compatibilidad entre plataformas.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="0c4a7-210">Y aunque esto no significa que todas las plataformas se admitan de forma preestablecida, nos hemos asegurado de que ninguno de los códigos del kit de herramientas se interrumpa al cambiar el destino de compilación a otras plataformas.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="0c4a7-211">La robustez y la extensibilidad con el diseño modular le establecen una buena ruta de acceso para poder admitir varias plataformas, como ARCore, ARKit y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="0c4a7-212">Rendimiento</span><span class="sxs-lookup"><span data-stu-id="0c4a7-212">Performant</span></span>
<span data-ttu-id="0c4a7-213">Al trabajar con plataformas móviles, se construyó pensando en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="0c4a7-214">Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan a trabajar con usted.</span><span class="sxs-lookup"><span data-stu-id="0c4a7-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="0c4a7-215">Vea también</span><span class="sxs-lookup"><span data-stu-id="0c4a7-215">See also</span></span>
* [<span data-ttu-id="0c4a7-216">Guía de introducción a MRTK</span><span class="sxs-lookup"><span data-stu-id="0c4a7-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="0c4a7-217">Página principal de la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="0c4a7-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="0c4a7-218">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="0c4a7-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="0c4a7-219">Migración de HTK/MRTK a MRTK versión 2</span><span class="sxs-lookup"><span data-stu-id="0c4a7-219">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
