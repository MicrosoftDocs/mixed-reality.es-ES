---
title: 'MRTK 101: Cómo usar el kit de herramientas de realidad mixta Unity para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)'
description: Cómo usar el kit de herramientas de realidad mixta Unity para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, kit de herramientas de realidad mixta, Windows Mixed Reality, diseño, aplicación de ejemplo, controles
ms.openlocfilehash: 95c81442cc390da8ac7c9a8de218341cb5e7c948
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439656"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="925be-104">MRTK 101: Cómo usar el kit de herramientas de realidad mixta Unity para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)</span><span class="sxs-lookup"><span data-stu-id="925be-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="925be-106">Obtenga información sobre cómo usar MRTK para lograr algunos de los patrones de interacción comunes más utilizados en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="925be-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="925be-107">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="925be-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="925be-108">Cómo capturar y desplace un objeto</span><span class="sxs-lookup"><span data-stu-id="925be-108">How to grab and move an object?</span></span>
- <span data-ttu-id="925be-109">¿Cómo se cambia el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="925be-109">How to resize an object?</span></span>
- <span data-ttu-id="925be-110">¿Cómo se mueve o gira un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="925be-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="925be-111">Cómo hacer que un objeto responda a los eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="925be-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="925be-112">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="925be-112">How to add visual feedback?</span></span>
- <span data-ttu-id="925be-113">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="925be-113">How to add audio feedback?</span></span>
- <span data-ttu-id="925be-114">¿Cómo se usa el botón de estilo Prefabs de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="925be-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="925be-115">¿Cómo hacer que un objeto siga?</span><span class="sxs-lookup"><span data-stu-id="925be-115">How to make an object follow you?</span></span>
- <span data-ttu-id="925be-116">¿Cómo hacer que un objeto se enfrente?</span><span class="sxs-lookup"><span data-stu-id="925be-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="925be-117">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="925be-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="925be-118">MRTK admite la simulación de entrada en el editor.</span><span class="sxs-lookup"><span data-stu-id="925be-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="925be-119">Simplemente ejecute la escena haciendo clic en el botón de reproducción de Unity.</span><span class="sxs-lookup"><span data-stu-id="925be-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="925be-120">Use estas claves para simular la entrada.</span><span class="sxs-lookup"><span data-stu-id="925be-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="925be-121">Presione las teclas W, a, S y D para desplace la cámara.</span><span class="sxs-lookup"><span data-stu-id="925be-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="925be-122">Mantenga presionado el botón secundario del mouse y mueva el mouse para buscarlo.</span><span class="sxs-lookup"><span data-stu-id="925be-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="925be-123">Para mostrar las manos simuladas, presione la barra espaciadora (derecha) o la tecla Mayús izquierda (mano izquierda) para mantener las manos simuladas en la vista, presione la tecla T o Y para girar las manos simuladas, presione Q o E (horizontal)/R o F (vertical)</span><span class="sxs-lookup"><span data-stu-id="925be-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="925be-124">Más información sobre la simulación de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="925be-125">Cómo capturar y desplace un objeto</span><span class="sxs-lookup"><span data-stu-id="925be-125">How to grab and move an object?</span></span>
<span data-ttu-id="925be-126">Para hacer que un objeto sea propuesto, asigne estos dos scripts: ManipulationHandler.cs y NearInteractionGrabbable. CS (para captación directa con entrada de seguimiento de mano articulada) ManipulationHandler admite interacciones Near y Far.</span><span class="sxs-lookup"><span data-stu-id="925be-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="925be-127">Puede capturar y trasladar un objeto con la entrada de seguimiento articulado de HoloLens 2 (Near), el rayo de mano (lejano), el rayo del controlador de movimiento (lejano), el cursor de miración de HoloLens & cámara de aire.</span><span class="sxs-lookup"><span data-stu-id="925be-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="925be-128">¿Cómo se cambia el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="925be-128">How to resize an object?</span></span>
<span data-ttu-id="925be-129">ManipulationHandler.cs admite el escalado o la rotación bidireccionales.</span><span class="sxs-lookup"><span data-stu-id="925be-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="925be-130">Esto funciona con varios tipos de entrada, como la entrada de mano articulada de HoloLens 2, la entrada de gestos de la flecha de más de HoloLens y la entrada de gestos de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="925be-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="925be-131">Más información sobre el controlador de manipulación en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="925be-132">¿Cómo se mueve o gira un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="925be-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="925be-133">Asigne BoundingBox.cs a un objeto para usar el cuadro de límite, que es la interfaz para el escalado y la rotación de un objeto.</span><span class="sxs-lookup"><span data-stu-id="925be-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="925be-134">De forma predeterminada, se muestran los controladores y los cables de color azul de HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="925be-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="925be-135">Para usar controladores animados basados en proximidad de estilo de HoloLens 2, debe asignar Prefabs y materiales.</span><span class="sxs-lookup"><span data-stu-id="925be-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="925be-136">Consulte la documentación del cuadro de límite y la escena de BoundingBoxExamples. Unity para obtener los detalles de configuración.</span><span class="sxs-lookup"><span data-stu-id="925be-136">Please refer to Bounding Box documentation and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="925be-137">Más información sobre el cuadro de límite en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="925be-138">Cómo hacer que un objeto responda a los eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="925be-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="925be-139">Asigne PointerHandler.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="925be-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="925be-140">En el inspector, podrá usar eventos OnPointerDown (), OnPointerUp (), OnPointerClicked (), OnPointerDragged () para usar estos eventos en un script, implementar IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="925be-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="925be-141">Más información sobre el sistema de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="925be-142">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="925be-142">How to add visual feedback?</span></span>
<span data-ttu-id="925be-143">Asigne Interactable.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="925be-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="925be-144">En el inspector, cree un nuevo tema.</span><span class="sxs-lookup"><span data-stu-id="925be-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="925be-145">Mediante el uso de perfiles de tema de interactúas, puede agregar fácilmente comentarios visuales a todos los Estados de interacción de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="925be-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="925be-146">Interactúable proporciona varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.</span><span class="sxs-lookup"><span data-stu-id="925be-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="925be-147">Más información sobre el interactuable en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="925be-148">Otro bloque de creación importante para los comentarios visuales es el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="925be-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="925be-149">Con el sombreador estándar de MRTK, puede agregar fácilmente efectos de comentarios visuales como luz de desplazamiento y luz de proximidad.</span><span class="sxs-lookup"><span data-stu-id="925be-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="925be-150">Dado que el sombreador estándar de MRTK realiza un cálculo significativamente menor que el sombreador estándar de Unity, puede crear una experiencia de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="925be-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="925be-151">Cree un nuevo material y seleccione el "el kit de herramientas de realidad mixta de el sombreador > estándar".</span><span class="sxs-lookup"><span data-stu-id="925be-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="925be-152">O bien, puede elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="925be-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="925be-153">Más información sobre el sombreador estándar de MRTK en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="925be-154">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="925be-154">How to add audio feedback?</span></span>
<span data-ttu-id="925be-155">Agregue AudioSource a un objeto.</span><span class="sxs-lookup"><span data-stu-id="925be-155">Add AudioSource to an object.</span></span> <span data-ttu-id="925be-156">A continuación, en los scripts que exponen eventos de entrada (por ejemplo, Interactable.cs o PointerHandler.cs), asigne el objeto al evento y seleccione AudioSource. PlayOneShot ().</span><span class="sxs-lookup"><span data-stu-id="925be-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="925be-157">Puede usar los clips de audio o elegir uno de los recursos de audio de MRTK.</span><span class="sxs-lookup"><span data-stu-id="925be-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="925be-158">¿Cómo se usa el botón de estilo Prefabs de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="925be-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="925be-159">MRTK proporciona varios tipos de botones de estilo de Shell (SO) de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="925be-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="925be-160">Proporciona comentarios visuales sofisticados, como la luz de proximidad, el cuadro de compresión y un efecto de rizo en la superficie del botón.</span><span class="sxs-lookup"><span data-stu-id="925be-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="925be-161">Basta con arrastrar y colocar uno de los botones que se presionan en el estilo de HoloLens 2 recurso prefabricado en la escena.</span><span class="sxs-lookup"><span data-stu-id="925be-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="925be-162">Recurso prefabricado usa Interactable.cs, que se presentó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="925be-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="925be-163">Puede usar eventos expuestos como OnClick () en las acciones que pueden interaccionar para desencadenar.</span><span class="sxs-lookup"><span data-stu-id="925be-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="925be-164">Más información sobre el botón Prefabs en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="925be-165">¿Cómo hacer que un objeto siga?</span><span class="sxs-lookup"><span data-stu-id="925be-165">How to make an object follow you?</span></span>
<span data-ttu-id="925be-166">Asigne el script RadialView.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="925be-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="925be-167">Forma parte de la serie de scripts de Solver que permite lograr distintos tipos de ubicación de objetos en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="925be-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="925be-168">SolverHandler.cs se agregará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="925be-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="925be-169">A continuación se muestra un ejemplo de la configuración de RadialView para lograr la etiqueta "Follow Lazy" a lo largo del comportamiento como el menú Inicio en el shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="925be-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="925be-170">Puede especificar la distancia mínima/máxima y los grados de vista mínimo y máximo.</span><span class="sxs-lookup"><span data-stu-id="925be-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="925be-171">En el ejemplo siguiente se muestra cómo colocar el objeto entre 0,4 m y el intervalo de 0,8 m en 15 °.</span><span class="sxs-lookup"><span data-stu-id="925be-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="925be-172">Ajuste los valores de tiempo de lerp para que la actualización posicional sea más rápida o más lenta.</span><span class="sxs-lookup"><span data-stu-id="925be-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="925be-173">Más información sobre las resoluciones en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="925be-174">¿Cómo hacer que un objeto se enfrente?</span><span class="sxs-lookup"><span data-stu-id="925be-174">How to make an object face you?</span></span>
<span data-ttu-id="925be-175">Asigne el script Billboard.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="925be-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="925be-176">Siempre se encontrará con independencia de su posición.</span><span class="sxs-lookup"><span data-stu-id="925be-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="925be-177">Puede especificar la opción del eje dinámico.</span><span class="sxs-lookup"><span data-stu-id="925be-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="925be-178">¿Está listo para crear experiencias sorprendentes para la realidad mixta?</span><span class="sxs-lookup"><span data-stu-id="925be-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="925be-179">Visite las páginas siguientes y obtenga más información sobre MRTK y Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="925be-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="925be-180">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="925be-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="925be-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="925be-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="925be-182">@Microsoft del diseñador de la experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="925be-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="925be-183">Consulta también</span><span class="sxs-lookup"><span data-stu-id="925be-183">See also</span></span>

* [<span data-ttu-id="925be-184">Kit de herramientas de realidad mixta (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="925be-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="925be-185">Portal de documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="925be-186">Introducción con MRTK</span><span class="sxs-lookup"><span data-stu-id="925be-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="925be-187">HoloToolkit a MRTK instrucción de portabilidad</span><span class="sxs-lookup"><span data-stu-id="925be-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
