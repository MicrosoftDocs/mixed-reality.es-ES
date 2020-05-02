---
title: 'MRTK 101: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)'
description: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, design, sample app, controls
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028309"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="78246-104">MRTK 101: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)</span><span class="sxs-lookup"><span data-stu-id="78246-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="78246-106">Aprende a usar MRTK para lograr algunos de los patrones de interacción comunes más usados en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="78246-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="78246-107">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="78246-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="78246-108">¿Cómo agarrar y desplazar un objeto?</span><span class="sxs-lookup"><span data-stu-id="78246-108">How to grab and move an object?</span></span>
- <span data-ttu-id="78246-109">¿Cómo cambiar el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="78246-109">How to resize an object?</span></span>
- <span data-ttu-id="78246-110">¿Cómo mover o girar un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="78246-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="78246-111">¿Cómo conseguir que un objeto responda a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="78246-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="78246-112">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="78246-112">How to add visual feedback?</span></span>
- <span data-ttu-id="78246-113">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="78246-113">How to add audio feedback?</span></span>
- <span data-ttu-id="78246-114">¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="78246-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="78246-115">¿Cómo hacer que un objeto te siga?</span><span class="sxs-lookup"><span data-stu-id="78246-115">How to make an object follow you?</span></span>
- <span data-ttu-id="78246-116">¿Cómo hacer que un objeto se ponga delante de ti?</span><span class="sxs-lookup"><span data-stu-id="78246-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="78246-117">¿Cómo simular interacciones de entrada en el editor de Unity?</span><span class="sxs-lookup"><span data-stu-id="78246-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="78246-118">MRTK admite la simulación de entrada en el editor.</span><span class="sxs-lookup"><span data-stu-id="78246-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="78246-119">Simplemente, ejecuta la escena haciendo clic en el botón de juego de Unity.</span><span class="sxs-lookup"><span data-stu-id="78246-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="78246-120">Usa estas claves para simular la entrada.</span><span class="sxs-lookup"><span data-stu-id="78246-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="78246-121">Presiona las teclas W, A, S y D para mover la cámara.</span><span class="sxs-lookup"><span data-stu-id="78246-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="78246-122">Mantén presionado el botón derecho del ratón y muévelo para mirar alrededor.</span><span class="sxs-lookup"><span data-stu-id="78246-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="78246-123">Para mostrar las manos simuladas, presiona la barra espaciadora (mano derecha) o la tecla Mayús izquierda (mano izquierda). Para mantener las manos simuladas en la vista, presiona la tecla T o Y. Para girar las manos simuladas, presiona Q o E (horizontal)/R o F (vertical).</span><span class="sxs-lookup"><span data-stu-id="78246-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="78246-124">Más información sobre la simulación de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="78246-125">¿Cómo agarrar y mover un objeto?</span><span class="sxs-lookup"><span data-stu-id="78246-125">How to grab and move an object?</span></span>
<span data-ttu-id="78246-126">Para que un objeto se pueda agarrar, asigna estos dos scripts: ManipulationHandler.cs y NearInteractionGrabbable.cs (para captación directa con entrada de seguimiento de manos articulada). ManipulationHandler admite interacciones cercanas y lejanas.</span><span class="sxs-lookup"><span data-stu-id="78246-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="78246-127">Puedes agarrar y mover un objeto con la entrada de seguimiento de manos articulada de HoloLens 2 (cercana), el haz de mano (lejana), el cursor del controlador de movimiento (lejano), el cursor de mirada de HoloLens y el toque en el aire (lejana).</span><span class="sxs-lookup"><span data-stu-id="78246-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="78246-128">¿Cómo cambiar el tamaño de un objeto?</span><span class="sxs-lookup"><span data-stu-id="78246-128">How to resize an object?</span></span>
<span data-ttu-id="78246-129">ManipulationHandler.cs admite el escalado o la rotación con dos manos.</span><span class="sxs-lookup"><span data-stu-id="78246-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="78246-130">Esto funciona con varios tipos de entrada, como la entrada de manos articulada de HoloLens 2, la entrada de mirada y gestos de HoloLens 1 y la entrada del controlador de movimiento del casco envolvente de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="78246-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="78246-131">Más información sobre el controlador de manipulación en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="78246-132">¿Cómo mover o girar un objeto con precisión?</span><span class="sxs-lookup"><span data-stu-id="78246-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="78246-133">Asigna BoundingBox.cs a un objeto para usar el cuadro de límite, que es la interfaz para escalar y girar un objeto.</span><span class="sxs-lookup"><span data-stu-id="78246-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="78246-134">De forma predeterminada, se muestran los controladores y los cables de color azul del estilo de HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="78246-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="78246-135">Para usar controladores animados basados en proximidad del estilo de HoloLens 2, debes asignar objetos prefabricados y materiales.</span><span class="sxs-lookup"><span data-stu-id="78246-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="78246-136">Consulta la [documentación del cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) y la escena de BoundingBoxExamples.unity para obtener los detalles de configuración.</span><span class="sxs-lookup"><span data-stu-id="78246-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="78246-137">Más información sobre los cuadros de límite en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="78246-138">¿Cómo conseguir que un objeto responda a eventos de entrada?</span><span class="sxs-lookup"><span data-stu-id="78246-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="78246-139">Asigna PointerHandler.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="78246-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="78246-140">En el inspector, podrás usar los eventos OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Para usarlos en un script, implementa IMixedRealityPointerHandler.</span><span class="sxs-lookup"><span data-stu-id="78246-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="78246-141">Más información sobre el sistema de entrada en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="78246-142">¿Cómo agregar comentarios visuales?</span><span class="sxs-lookup"><span data-stu-id="78246-142">How to add visual feedback?</span></span>
<span data-ttu-id="78246-143">Asigna Interactable.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="78246-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="78246-144">En el inspector, crea un tema.</span><span class="sxs-lookup"><span data-stu-id="78246-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="78246-145">Mediante el uso de perfiles de tema interactuables, puedes agregar comentarios visuales a todos los estados de interacción de entrada disponibles.</span><span class="sxs-lookup"><span data-stu-id="78246-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="78246-146">Los elementos interactuables proporcionan varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.</span><span class="sxs-lookup"><span data-stu-id="78246-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="78246-147">Más información sobre los elementos interactuables en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="78246-148">Otro bloque de creación importante para los comentarios visuales es el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="78246-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="78246-149">Con el sombreador estándar de MRTK, puedes agregar fácilmente efectos de comentarios visuales, como luz de desplazamiento y de proximidad.</span><span class="sxs-lookup"><span data-stu-id="78246-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="78246-150">Dado que el sombreador estándar de MRTK realiza un cálculo significativamente menor que el sombreador estándar de Unity, puedes crear una experiencia de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="78246-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="78246-151">Crea un nuevo material y selecciona el sombreador "Mixed Reality Toolkit > Standard (Estándar)".</span><span class="sxs-lookup"><span data-stu-id="78246-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="78246-152">También puedes elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="78246-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="78246-153">Más información sobre el sombreador estándar de MRTK en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="78246-154">¿Cómo agregar comentarios de audio?</span><span class="sxs-lookup"><span data-stu-id="78246-154">How to add audio feedback?</span></span>
<span data-ttu-id="78246-155">Agrega AudioSource a un objeto.</span><span class="sxs-lookup"><span data-stu-id="78246-155">Add AudioSource to an object.</span></span> <span data-ttu-id="78246-156">A continuación, en los scripts que exponen eventos de entrada (p. ej., Interactable.cs o PointerHandler.cs), asigna el objeto al evento y selecciona AudioSource.PlayOneShot().</span><span class="sxs-lookup"><span data-stu-id="78246-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="78246-157">Puedes usar los clips de audio o elegir uno de los recursos de audio de MRTK.</span><span class="sxs-lookup"><span data-stu-id="78246-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="78246-158">¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="78246-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="78246-159">MRTK proporciona varios tipos de botones de estilo de Shell (SO) de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="78246-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="78246-160">Proporciona comentarios visuales sofisticados, como la luz de proximidad, el cuadro de compresión y un efecto de rizado en la superficie del botón.</span><span class="sxs-lookup"><span data-stu-id="78246-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="78246-161">Basta con arrastrar y colocar uno de los objetos prefabricados de botón presionable del estilo de HoloLens 2 a la escena.</span><span class="sxs-lookup"><span data-stu-id="78246-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="78246-162">El objeto prefabricado usa Interactable.cs, que se presentó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="78246-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="78246-163">Puedes usar eventos expuestos como OnClick() en el objeto interactuable para desencadenar acciones.</span><span class="sxs-lookup"><span data-stu-id="78246-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="78246-164">Más información sobre los objetos prefabricados de botón en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="78246-165">¿Cómo hacer que un objeto te siga?</span><span class="sxs-lookup"><span data-stu-id="78246-165">How to make an object follow you?</span></span>
<span data-ttu-id="78246-166">Asigna el script RadialView.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="78246-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="78246-167">Forma parte de la serie de scripts del solucionador que permite lograr distintos tipos de selección de ubicación de objetos en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="78246-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="78246-168">SolverHandler.cs se agregará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="78246-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="78246-169">A continuación se incluye un ejemplo de configuración de RadialView para lograr el comportamiento y la etiqueta "lazy follow" (seguimiento diferido), como el menú Inicio del shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="78246-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="78246-170">Puedes especificar la distancia mínima/máxima y los grados de vista mínimos y máximos.</span><span class="sxs-lookup"><span data-stu-id="78246-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="78246-171">En el ejemplo siguiente se muestra cómo colocar el objeto en un intervalo entre 0,4 m y 0,8 m en 15°.</span><span class="sxs-lookup"><span data-stu-id="78246-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="78246-172">Ajusta los valores de tiempo de Lerp para que la actualización posicional sea más rápida o más lenta.</span><span class="sxs-lookup"><span data-stu-id="78246-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="78246-173">Más información sobre los solucionadores en la documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="78246-174">¿Cómo hacer que un objeto se ponga delante de ti?</span><span class="sxs-lookup"><span data-stu-id="78246-174">How to make an object face you?</span></span>
<span data-ttu-id="78246-175">Asigna el script Billboard.cs a un objeto.</span><span class="sxs-lookup"><span data-stu-id="78246-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="78246-176">Siempre se situará delante de ti, independientemente de tu posición.</span><span class="sxs-lookup"><span data-stu-id="78246-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="78246-177">Puedes especificar la opción del eje dinámico.</span><span class="sxs-lookup"><span data-stu-id="78246-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="78246-178">¿Estás listo para crear experiencias sorprendentes para la realidad mixta?</span><span class="sxs-lookup"><span data-stu-id="78246-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="78246-179">Visita las páginas siguientes y obtén más información sobre MRTK y Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="78246-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="78246-180">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="78246-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="78246-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="78246-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="78246-182">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="78246-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="78246-183">Consulta también</span><span class="sxs-lookup"><span data-stu-id="78246-183">See also</span></span>

* [<span data-ttu-id="78246-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="78246-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="78246-185">Portal de documentación de MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="78246-186">Introducción a MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="78246-187">Guía de portabilidad de HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="78246-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
