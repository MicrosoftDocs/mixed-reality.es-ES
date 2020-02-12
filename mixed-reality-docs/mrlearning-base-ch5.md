---
title: 'Tutoriales de introducción: 6. Explorar opciones de entrada avanzadas'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129666"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="f6a0f-105">6. explorar opciones de entrada avanzadas</span><span class="sxs-lookup"><span data-stu-id="f6a0f-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="f6a0f-106">En este tutorial, explorará algunas opciones de entrada avanzadas para HoloLens 2, incluido el uso de comandos de voz, gestos de movimiento panorámico y seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="f6a0f-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f6a0f-107">Objectives</span></span>

* <span data-ttu-id="f6a0f-108">Desencadenar eventos mediante comandos de voz y palabras clave</span><span class="sxs-lookup"><span data-stu-id="f6a0f-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="f6a0f-109">Usar manos con seguimiento para panorámicas y objetos 3D con manos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="f6a0f-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="f6a0f-110">Aproveche las capacidades de seguimiento ocular de HoloLens 2 para seleccionar objetos</span><span class="sxs-lookup"><span data-stu-id="f6a0f-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="f6a0f-111">Habilitar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="f6a0f-112">En esta sección, implementará un comando de voz para que el usuario pueda reproducir un sonido en el objeto OCTA.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="f6a0f-113">Para ello, creará un nuevo comando de voz y, a continuación, configurará el evento para que desencadene la acción deseada cuando se pronuncia la palabra clave de comando de voz.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="f6a0f-114">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f6a0f-115">Clonar el perfil del sistema de entrada predeterminado</span><span class="sxs-lookup"><span data-stu-id="f6a0f-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="f6a0f-116">Clonar el perfil predeterminado de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="f6a0f-117">Crear un nuevo comando de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-117">Create a new speech command</span></span>
4. <span data-ttu-id="f6a0f-118">Agregar y configurar el componente de controlador de entrada de voz (Script)</span><span class="sxs-lookup"><span data-stu-id="f6a0f-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="f6a0f-119">Implementar el evento de respuesta para el comando de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="f6a0f-120">1. clonar el perfil del sistema de entrada predeterminado</span><span class="sxs-lookup"><span data-stu-id="f6a0f-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="f6a0f-121">En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana del inspector, seleccione la pestaña **entrada** y Clone el **DefaultHoloLens2InputSystemProfile** para reemplazarlo por su propio perfil de **sistema de entrada**personalizable:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="f6a0f-123">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [configuración de los perfiles de el kit de herramientas de realidad mixta](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="f6a0f-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="f6a0f-124">2. clonar el perfil predeterminado de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="f6a0f-125">Expanda la sección **voz** y Clone el **DefaultMixedRealitySpeechCommandsProfile** para reemplazarlo por su perfil personalizado de **comandos de voz**.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="f6a0f-127">3. crear un nuevo comando de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-127">3. Create a new speech command</span></span>

<span data-ttu-id="f6a0f-128">En la **sección comandos de voz** , haga clic en el botón **+ Agregar un nuevo comando de voz** para agregar un nuevo comando de voz a la parte inferior de la lista de comandos de voz existentes y, a continuación, en el campo **palabra clave** escriba una palabra o frase adecuada, por ejemplo **reproducir música**:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="f6a0f-130">Si el equipo no tiene micrófono y desea probar el comando de voz mediante la simulación en el editor, puede asignar un KeyCode al comando de voz que le permitirá desencadenarlo cuando se presione la tecla correspondiente.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="f6a0f-131">4. agregar y configurar el componente de controlador de entrada de voz (Script)</span><span class="sxs-lookup"><span data-stu-id="f6a0f-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="f6a0f-132">En la ventana jerarquía, seleccione el objeto **OCTA** y agregue el componente **controlador de entrada de voz (Script)** al objeto OCTA.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="f6a0f-133">A continuación, desactive la casilla **se requiere el foco** para que el usuario no tenga que ver el objeto OCTA para desencadenar el comando de voz:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="f6a0f-135">5. implementar el evento de respuesta para el comando de voz</span><span class="sxs-lookup"><span data-stu-id="f6a0f-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="f6a0f-136">En el componente de controlador de entrada de voz (Script), haga clic en el botón Small **+** para agregar una palabra clave y, a continuación, en la lista desplegable **palabra** clave, elija la palabra clave **Play Music** que creó anteriormente:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="f6a0f-138">Las palabras clave de la lista desplegable palabra clave se rellenan en función de las palabras clave definidas en la lista comandos de voz en el perfil comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-138">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="f6a0f-139">Cree un nuevo evento **Response ()** , configure el objeto **OCTA** para recibir el evento, defina **AudioSource. PlayOneShot** como la acción que se va a desencadenar y asigne un clip de audio adecuado al campo **clip de audio** , por ejemplo, el MRTK_Gem clip de audio:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-139">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> <span data-ttu-id="f6a0f-141">Para obtener un recordatorio sobre cómo implementar eventos y asignar un clip de audio, puede hacer referencia a las instrucciones para [implementar el evento on Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .</span><span class="sxs-lookup"><span data-stu-id="f6a0f-141">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="f6a0f-142">Gesto de desplazamiento panorámico</span><span class="sxs-lookup"><span data-stu-id="f6a0f-142">The Pan Gesture</span></span>

<span data-ttu-id="f6a0f-143">El movimiento panorámico es útil para desplazarse por el dedo o la mano para desplazarse por el contenido.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-143">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="f6a0f-144">En este ejemplo, primero aprenderá a desplazarse por una interfaz de usuario 2D y, a continuación, a expandir esa para poder desplazarse por una colección de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-144">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="f6a0f-145">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-145">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f6a0f-146">Crear un objeto cuádruple que se puede usar para la panorámica</span><span class="sxs-lookup"><span data-stu-id="f6a0f-146">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="f6a0f-147">Adición del componente de la interacción táctil (Script) de Near Interaction</span><span class="sxs-lookup"><span data-stu-id="f6a0f-147">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="f6a0f-148">Adición del componente de zoom de pan de interacción manual (Script)</span><span class="sxs-lookup"><span data-stu-id="f6a0f-148">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="f6a0f-149">Agregar contenido 2D que se va a desplazar</span><span class="sxs-lookup"><span data-stu-id="f6a0f-149">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="f6a0f-150">Agregar contenido 3D que se va a desplazar</span><span class="sxs-lookup"><span data-stu-id="f6a0f-150">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="f6a0f-151">Agregar el componente mover con pan (Script)</span><span class="sxs-lookup"><span data-stu-id="f6a0f-151">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="f6a0f-152">El componente de movimiento con pan (Script) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-152">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="f6a0f-153">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-153">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="f6a0f-154">1. crear un objeto cuádruple que se puede usar para la panorámica</span><span class="sxs-lookup"><span data-stu-id="f6a0f-154">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="f6a0f-155">En la ventana jerarquía, haga clic con el botón secundario en un área vacía y seleccione **objeto 3d** > **cuádruple** para agregar un cuádruple a la escena.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-155">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="f6a0f-156">Asígnele un nombre adecuado, por ejemplo, **PanGesture**, y colóquelo en una ubicación adecuada, por ejemplo, X = 0, y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-156">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="f6a0f-158">Para obtener un recordatorio sobre cómo agregar primitivas de Unity, como un 3D cuádruple, a la escena, puede hacer referencia a las instrucciones para [Agregar un cubo a la escena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .</span><span class="sxs-lookup"><span data-stu-id="f6a0f-158">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="f6a0f-159">Como con cualquier otra interacción, el movimiento panorámico también requiere un Colisionador.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-159">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="f6a0f-160">De forma predeterminada, un cuádruple tiene un Colisionador de malla.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-160">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="f6a0f-161">Sin embargo, el Colisionador de malla no es idóneo porque es extremadamente fino.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-161">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="f6a0f-162">Para que sea más fácil para el usuario interactuar con el Colisionador, se reemplazará el Colisionador de malla por un Colisionador de caja.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-162">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="f6a0f-163">Con el objeto PanGesture aún seleccionado, haga clic en el icono de **configuración** del componente de **Colisionador de malla** y seleccione **quitar componente** para quitar el Colisionador de malla:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-163">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="f6a0f-165">En la ventana del inspector, use el botón **Agregar componente** para agregar un **Colisionador de cuadro**y, a continuación, cambie el **tamaño** de colisionador de caja Z a 0,15 para aumentar el grosor del Colisionador de caja:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-165">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="f6a0f-167">2. agregar el componente de secuencia de comandos táctil de interacción cercana</span><span class="sxs-lookup"><span data-stu-id="f6a0f-167">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="f6a0f-168">Con el objeto **PanGesture** aún seleccionado, agregue el componente de **secuencia de comandos táctil (Script) cerca** de la interacción al objeto PanGesture y, a continuación, haga clic en los botones **corregir límites** y **centro de corrección** para actualizar el centro local y las propiedades de los límites del elemento táctil de interacción cercana (Script) para que coincida con BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-168">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="f6a0f-170">3. agregar el componente zoom de pan de interacción (Script)</span><span class="sxs-lookup"><span data-stu-id="f6a0f-170">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="f6a0f-171">Con el objeto **PanGesture** aún seleccionado, agregue el componente **zoom de pan de interacción a mano (Script)** al objeto PanGesture y, a continuación, active la casilla **bloquear horizontalmente** para permitir solo el desplazamiento vertical:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-171">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="f6a0f-173">4. agregar el contenido 2D que se va a desplazar</span><span class="sxs-lookup"><span data-stu-id="f6a0f-173">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="f6a0f-174">En el panel Proyecto, busque el material **PanContent** y, a continuación, haga clic en-y arrástrelo hasta la propiedad 0 del elemento de **material** del representador de malla del objeto **PanGesture** :</span><span class="sxs-lookup"><span data-stu-id="f6a0f-174">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="f6a0f-176">En la ventana del inspector, expanda el componente material de **PanContent** recién agregado y, a continuación, cambie su valor y de **mosaico** a 0,5 para que coincida con el valor X y los mosaicos aparezcan cuadrados:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-176">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="f6a0f-178">Si ahora entra en el modo de juego, puede probar el desplazamiento del contenido 2D mediante el gesto de panorámica en la simulación en el editor:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-178">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="f6a0f-180">5. agregar contenido 3D que se va a desplazar</span><span class="sxs-lookup"><span data-stu-id="f6a0f-180">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="f6a0f-181">En la ventana de jerarquía, **cree cuatro cubos** como objetos secundarios de **PanContent** y establezca su **escala** de transformación en X = 0,15, y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-181">In the Hierarchy window, **create four cubes** as a child objects of the **PanContent** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="f6a0f-183">Para espaciar los cubos de forma uniforme y ahorrar tiempo, agregue el componente de la colección de objetos de cuadrícula (Script) al objeto primario de los cubos, es decir, el objeto PanGesture y configure la colección de objetos Grid (Script) de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-183">To space the cubes out evenly, and save some time, add the Grid Object Collection (Script) component, to the cubes' parent object, i.e. the PanGesture object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="f6a0f-184">Cambie **NUM Rows** a 1 para que todos los cubos estén alineados en una sola fila.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-184">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="f6a0f-185">Cambiar el **ancho de celda** a 0,25 para espaciar los cubos dentro de la fila</span><span class="sxs-lookup"><span data-stu-id="f6a0f-185">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="f6a0f-186">A continuación, haga clic en el botón **Actualizar colección** para aplicar la nueva configuración:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-186">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="f6a0f-188">6. agregar el componente de movimiento con pan (Script)</span><span class="sxs-lookup"><span data-stu-id="f6a0f-188">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="f6a0f-189">En la ventana jerarquía, seleccione todos los **objetos secundarios del cubo**y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente **mover con pan (Script)** a todos los cubos:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-189">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="f6a0f-191">En el caso de un recordatorio sobre cómo seleccionar varios objetos en la ventana jerarquía, las CDU pueden hacer referencia al [componente agregar el controlador de manipulación (Script) a todas las](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instrucciones de objetos.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-191">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="f6a0f-192">Con todos los cubos aún seleccionados, haga clic y arrastre el objeto **PanGesture** al campo **origen de entrada de pan** :</span><span class="sxs-lookup"><span data-stu-id="f6a0f-192">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="f6a0f-194">El componente mover con pan (Script) de cada cubo realiza escuchas para el evento de panorámica actualizado enviado por el componente HandInteractionPanZoom (Script) en el objeto PanGesture, que se asignó como el origen de entrada de pan en el paso anterior, y actualiza la posición de cada cubo. cambia.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-194">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="f6a0f-195">En la ventana jerarquía, seleccione el objeto **PanGesture** y, a continuación, en el inspector, **desactive** la casilla **representador de malla** para deshabilitar el componente de representador de malla:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-195">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="f6a0f-197">Si ahora entra en el modo de juego, puede probar el desplazamiento del contenido 3D con el gesto de panorámica en la simulación en el editor:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-197">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="f6a0f-199">Seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="f6a0f-199">Eye Tracking</span></span>

<span data-ttu-id="f6a0f-200">En esta sección, aprenderá a habilitar el seguimiento ocular en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="f6a0f-201">En este ejemplo, implementará la funcionalidad para hacer que cada objeto del 3DObjectCollection gire lentamente mientras se mira en el ojo del usuario, así como en desencadenar un efecto de señal cuando el objeto que se está buscando está seleccionado por el comando TAP o Speech.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-201">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="f6a0f-202">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-202">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f6a0f-203">Agregar el componente de destino de seguimiento ocular (Script) a todos los objetos de destino</span><span class="sxs-lookup"><span data-stu-id="f6a0f-203">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="f6a0f-204">Agregar el componente de demostración del tutorial de seguimiento de ojo (Script) a todos los objetos de destino</span><span class="sxs-lookup"><span data-stu-id="f6a0f-204">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="f6a0f-205">Implementar mientras se examina el evento de destino</span><span class="sxs-lookup"><span data-stu-id="f6a0f-205">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="f6a0f-206">Implementar el en el evento seleccionado</span><span class="sxs-lookup"><span data-stu-id="f6a0f-206">Implement the On Selected event</span></span>
5. <span data-ttu-id="f6a0f-207">Habilitación del seguimiento ocular simulado para simulaciones en el editor</span><span class="sxs-lookup"><span data-stu-id="f6a0f-207">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="f6a0f-208">Habilitar la entrada de fijamente en las funcionalidades de la aplicación del proyecto de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6a0f-208">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="f6a0f-209">1. agregar el componente de destino de seguimiento ocular (Script) a todos los objetos de destino</span><span class="sxs-lookup"><span data-stu-id="f6a0f-209">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="f6a0f-210">En la ventana de jerarquía, expanda el objeto **3DObjectCollection** y seleccione todos los **objetos secundarios**y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente de **destino de seguimiento ocular (Script)** a todos los objetos secundarios:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-210">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="f6a0f-212">Con todos los **objetos secundarios** todavía seleccionados, configure el componente de **destino de seguimiento ocular (Script)** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-212">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="f6a0f-213">Cambie **Seleccionar acción** a **seleccionar**para definir la acción de punteo de aire para este objeto como SELECT.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-213">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="f6a0f-214">Expanda **Voice seleccione** y establezca el **tamaño** de la lista de comandos de voz en 1 y, a continuación, en la lista de nuevos elementos que aparece, cambie el **elemento 0** a **Select**para definir la acción de comando de voz para este objeto como SELECT.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-214">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="f6a0f-216">2. agregar el componente de demostración del tutorial de seguimiento de ojo (Script) a todos los objetos de destino</span><span class="sxs-lookup"><span data-stu-id="f6a0f-216">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="f6a0f-217">Con todos los **objetos secundarios** todavía seleccionados, use el botón **Agregar componente** para agregar el componente de **demostración del tutorial de seguimiento de ojo (Script)** a todos los objetos secundarios:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-217">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="f6a0f-219">El componente objetivo de seguimiento ocular (Script) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-219">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="f6a0f-220">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-220">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="f6a0f-221">3. implementar mientras se examina el evento de destino</span><span class="sxs-lookup"><span data-stu-id="f6a0f-221">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="f6a0f-222">En la ventana jerarquía, seleccione el objeto de **queso** , cree un nuevo **mientras mira el evento () de destino** , configure el objeto de **queso** para recibir el evento y defina **EyeTrackingTutorialDemo. RotateTarget** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-222">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="f6a0f-224">**Repita el procedimiento** para cada uno de los objetos secundarios de 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-224">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="f6a0f-225">Para obtener un recordatorio sobre cómo implementar eventos, puede consultar las instrucciones de [gestos de seguimiento de mano e](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) interactivos.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-225">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="f6a0f-226">4. implementar el en el evento seleccionado</span><span class="sxs-lookup"><span data-stu-id="f6a0f-226">4. Implement the On Selected event</span></span>

<span data-ttu-id="f6a0f-227">En la ventana jerarquía, seleccione el objeto **queso** y, a continuación, cree un nuevo en el evento **seleccionado ()** , configure el objeto **queso** para recibir el evento y defina **EyeTrackingTutorialDemo. RotateTarget** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-227">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="f6a0f-229">**Repita el procedimiento** para cada uno de los objetos secundarios de 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-229">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="f6a0f-230">5. habilitar el seguimiento ocular simulado para simulaciones en el editor</span><span class="sxs-lookup"><span data-stu-id="f6a0f-230">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="f6a0f-231">En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana del inspector, seleccione la pestaña **entrada** , expanda la sección proveedores de **datos de entrada** y, a continuación, la sección servicio de simulación de **entrada** y Clone el **DefaultMixedRealityInputSimulationProfile** para reemplazarlo por su propio perfil de **simulación de entrada**personalizable:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-231">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="f6a0f-233">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [configuración de los perfiles de el kit de herramientas de realidad mixta](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .</span><span class="sxs-lookup"><span data-stu-id="f6a0f-233">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="f6a0f-234">En la sección **simulación ocular** , active la casilla **simular posición ocular** para habilitar la simulación de seguimiento ocular:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-234">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="f6a0f-236">Si ahora entra en el modo de juego, puede probar los efectos de giro y señalización que ha implementado ajustando la vista para que el cursor toque uno de los objetos y use la interacción a mano o el comando de voz para seleccionar el objeto:</span><span class="sxs-lookup"><span data-stu-id="f6a0f-236">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="f6a0f-238">Si no usó DefaultHoloLens2ConfigurationProfile para clonar el perfil de configuración de MRTK personalizable, como se indica en las instrucciones de configuración [del kit de herramientas de realidad mixta](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , puede que el seguimiento ocular no esté habilitado en el proyecto y deberá habilitarse.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-238">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="f6a0f-239">Para ello, puede consultar las instrucciones [Getting Started with Eye Tracking en MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .</span><span class="sxs-lookup"><span data-stu-id="f6a0f-239">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="f6a0f-240">6. habilitar la entrada fijamente en las funcionalidades de la aplicación del proyecto de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6a0f-240">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="f6a0f-241">Antes de compilar e implementar la aplicación desde Visual Studio en el dispositivo, se debe habilitar la entrada de mirada en las funcionalidades de la aplicación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-241">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="f6a0f-242">Para ello, puede seguir la prueba de la [aplicación de Unity en las instrucciones de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .</span><span class="sxs-lookup"><span data-stu-id="f6a0f-242">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f6a0f-243">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="f6a0f-243">Congratulations</span></span>

<span data-ttu-id="f6a0f-244">Ha agregado correctamente las funciones básicas de seguimiento de los ojos a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-244">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="f6a0f-245">Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-245">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="f6a0f-246">En este tutorial, también aprendió sobre otras características de entrada avanzadas, como comandos de voz y gestos de movimiento panorámico.</span><span class="sxs-lookup"><span data-stu-id="f6a0f-246">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="f6a0f-247">Lección siguiente: 7. crear una aplicación de ejemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="f6a0f-247">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
