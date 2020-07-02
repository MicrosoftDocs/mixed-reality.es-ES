---
title: 'Tutoriales de introducción: 6. Exploración de opciones avanzadas de entrada'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 9a19ad59e520a2743aafd954910f43c6f51d6c8a
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441862"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="c8395-105">6. Exploración de opciones avanzadas de entrada</span><span class="sxs-lookup"><span data-stu-id="c8395-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="c8395-106">En este tutorial, explorarás varias opciones de entrada avanzadas para HoloLens 2, como el uso de comandos de voz, gestos panorámicos y seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="c8395-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="c8395-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c8395-107">Objectives</span></span>

* <span data-ttu-id="c8395-108">Desencadenar eventos mediante comandos de voz y palabras clave</span><span class="sxs-lookup"><span data-stu-id="c8395-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="c8395-109">Usar el seguimiento de manos para desplazar lateralmente las texturas y objetos 3D</span><span class="sxs-lookup"><span data-stu-id="c8395-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="c8395-110">Aprovechar las funcionalidades de seguimiento ocular de HoloLens 2 para seleccionar objetos</span><span class="sxs-lookup"><span data-stu-id="c8395-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="c8395-111">Habilitar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="c8395-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="c8395-112">En esta sección, implementarás un comando de voz para que el usuario pueda reproducir un sonido en el objeto Octa.</span><span class="sxs-lookup"><span data-stu-id="c8395-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="c8395-113">Para ello, deberás crear un nuevo comando de voz y, a continuación, configurar el evento para que desencadene la acción deseada cuando se diga la palabra clave del comando de voz.</span><span class="sxs-lookup"><span data-stu-id="c8395-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="c8395-114">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="c8395-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="c8395-115">Clonar el perfil del sistema de entrada predeterminado</span><span class="sxs-lookup"><span data-stu-id="c8395-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="c8395-116">Clonar el perfil de los comandos de voz predeterminados</span><span class="sxs-lookup"><span data-stu-id="c8395-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="c8395-117">Crear un nuevo comando de voz</span><span class="sxs-lookup"><span data-stu-id="c8395-117">Create a new speech command</span></span>
4. <span data-ttu-id="c8395-118">Agregar y configurar el componente Speech Input Handler (Script) (Controlador de entrada de voz [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="c8395-119">Implementar el evento de respuesta para el comando de voz</span><span class="sxs-lookup"><span data-stu-id="c8395-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="c8395-120">1. Clonar el perfil del sistema de entrada predeterminado</span><span class="sxs-lookup"><span data-stu-id="c8395-120">1. Clone the default Input System Profile</span></span>
<span data-ttu-id="c8395-121">En la ventana Hierarchy (Jerarquía), selecciona el objeto **MixedRealityToolkit**. A continuación, en la ventana Inspector, selecciona la pestaña **Input** (Entrada) y clona **DefaultHoloLens2InputSystemProfile** para sustituirlo por tu propio valor de **Input System Profile** (Perfil de sistema de entrada):</span><span class="sxs-lookup"><span data-stu-id="c8395-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="c8395-123">Si utiliza MRTK 2.4.0 o posterior:</span><span class="sxs-lookup"><span data-stu-id="c8395-123">If you're using MRTK 2.4.0 or later:</span></span>
> * <span data-ttu-id="c8395-124">Seleccione el objeto **MixedRealityToolkit** en la pestaña Hierarchy (Jerarquía) y, después, haga clic en la pestaña **Input** (Entrada) en la ventana Inspector y expanda la sección **Pointers** (Punteros).</span><span class="sxs-lookup"><span data-stu-id="c8395-124">Select the **MixedRealityToolkit** object from the Hierarchy tab, then click the **Input** tab in the Inspector window and expand the **Pointers** section.</span></span> 
> * <span data-ttu-id="c8395-125">Clone el objeto **DefaultMixedRealityInputPointerProfile** y reemplácelo por su propio valor de **Input Pointer Profile** (Perfil de puntero de entrada) personalizable.</span><span class="sxs-lookup"><span data-stu-id="c8395-125">Clone the **DefaultMixedRealityInputPointerProfile** and replace it with your own customizable **Input Pointer Profile**.</span></span>
> * <span data-ttu-id="c8395-126">Compruebe que **Is Eye Tracked Enabled** (Seguimiento visual habilitado) sea true en la sección **Gaze Settings** (Configuración de mirada).</span><span class="sxs-lookup"><span data-stu-id="c8395-126">Check that **Is Eye Tracked Enabled** is true in the **Gaze Settings** section.</span></span> 

> [!TIP]
> <span data-ttu-id="c8395-127">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puedes consultar las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="c8395-127">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="c8395-128">2. Clonar el perfil de los comandos de voz predeterminados</span><span class="sxs-lookup"><span data-stu-id="c8395-128">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="c8395-129">Expande la sección **Speech** (Voz) y clona **DefaultMixedRealitySpeechCommandsProfile** para sustituirlo por tu propio valor personalizable de **Speech Commands Profile** (Perfil de comandos de voz):</span><span class="sxs-lookup"><span data-stu-id="c8395-129">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="c8395-131">3. Crear un nuevo comando de voz</span><span class="sxs-lookup"><span data-stu-id="c8395-131">3. Create a new speech command</span></span>

<span data-ttu-id="c8395-132">En la sección **Speech Commands** (Comandos de voz), haz clic en el botón **+ Add a New Speech Command** (Agregar nuevo comando de voz) en la parte inferior de la lista de comandos de voz existentes y, a continuación, en el campo **Keyword** (Palabra clave), escribe una palabra o frase adecuada; por ejemplo, **Play Music** (Reproducir música):</span><span class="sxs-lookup"><span data-stu-id="c8395-132">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="c8395-134">Si el equipo no tiene micrófono y quieres probar el comando de voz con la simulación en el editor, puedes asignar un valor de KeyCode al comando de voz que te permitirá desencadenarlo cuando se presione la tecla correspondiente.</span><span class="sxs-lookup"><span data-stu-id="c8395-134">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="c8395-135">4. Agregar y configurar el componente Speech Input Handler (Script) (Controlador de entrada de voz [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-135">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="c8395-136">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Octa** y agrega el componente **Speech Input Handler (Script)** (Controlador de entrada de voz [script]) al objeto Octa.</span><span class="sxs-lookup"><span data-stu-id="c8395-136">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="c8395-137">A continuación, desactiva la casilla **Is Focus Required** (Se requiere foco) para que no sea necesario que el usuario observe objeto Octa para desencadenar el comando de voz:</span><span class="sxs-lookup"><span data-stu-id="c8395-137">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="c8395-139">5. Implementar el evento de respuesta para el comando de voz</span><span class="sxs-lookup"><span data-stu-id="c8395-139">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="c8395-140">En el componente Speech Input Handler (Script) (Controlador de entrada de voz [script]), haz clic en el pequeño botón **+** para agregar un elemento de palabra clave a la lista de palabras clave:</span><span class="sxs-lookup"><span data-stu-id="c8395-140">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="c8395-142">Haz clic en el **elemento 0** recién creado para expandirlo y, a continuación, en la lista desplegable **Keyword** (Palabra clave), elige la palabra clave **Play Music** (Reproducir música) que creaste anteriormente:</span><span class="sxs-lookup"><span data-stu-id="c8395-142">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="c8395-144">Las palabras clave de la lista desplegable Keyword (Palabra clave) se rellenan en función de las palabras clave definidas en la lista Speech Commands (Comandos de voz) en el perfil de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="c8395-144">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="c8395-145">Crea un nuevo evento **Response ()** (Respuesta []), configura el objeto **Octa** para recibir el evento, define **AudioSource.PlayOneShot** como la acción que se desencadenará y asigna un clip de audio adecuado al campo **Audio Clip** (Clip de audio); por ejemplo, el clip de audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="c8395-145">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="c8395-147">Para obtener un recordatorio sobre cómo implementar eventos y asignar un clip de audio, puedes consultar las instrucciones de [Implementar el evento On Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) (Iniciado con el tacto []).</span><span class="sxs-lookup"><span data-stu-id="c8395-147">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="c8395-148">Gesto de desplazamiento panorámico</span><span class="sxs-lookup"><span data-stu-id="c8395-148">The Pan Gesture</span></span>

<span data-ttu-id="c8395-149">El gesto de desplazamiento lateral es útil para desplazarse empleando un dedo o la mano para desplazarse por el contenido.</span><span class="sxs-lookup"><span data-stu-id="c8395-149">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="c8395-150">En este ejemplo, primero aprenderás a desplazarte por una interfaz de usuario 2D y, a continuación, a desplazarte por una colección de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="c8395-150">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="c8395-151">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="c8395-151">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="c8395-152">Crear un objeto cuádruple que se pueda usar para el desplazamiento lateral</span><span class="sxs-lookup"><span data-stu-id="c8395-152">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="c8395-153">Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-153">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="c8395-154">Agregar el componente Hand Interaction Pan Zoom (Script) (Interacción de mano de zoom de desplazamiento lateral [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-154">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="c8395-155">Agregar contenido 2D que se desplazará</span><span class="sxs-lookup"><span data-stu-id="c8395-155">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="c8395-156">Agregar contenido 3D que se desplazará</span><span class="sxs-lookup"><span data-stu-id="c8395-156">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="c8395-157">Agregar el componente Move With Pan (Script) (Mover con desplazamiento lateral [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-157">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="c8395-158">El componente Move With Pan (Script) (Mover con desplazamiento lateral [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="c8395-158">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="c8395-159">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="c8395-159">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="c8395-160">1. Crear un objeto cuádruple que se pueda usar para el desplazamiento lateral</span><span class="sxs-lookup"><span data-stu-id="c8395-160">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="c8395-161">En la ventana Hierarchy (Jerarquía), haz clic con el botón derecho en una área vacía y selecciona **3D Object** > **Quad** (Objeto 3D > Cuadrante) para agregar un cuadrante a la escena.</span><span class="sxs-lookup"><span data-stu-id="c8395-161">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="c8395-162">Asígnale un nombre adecuado; por ejemplo, **PanGesture** y colócalo en una ubicación adecuada; por ejemplo, X = 0, Y = -0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="c8395-162">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="c8395-164">Para obtener un recordatorio sobre cómo agregar objetos primitivos de Unity, como un cuadrante 3D, a la escena, consulta las instrucciones de [Agregar un cubo a la escena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).</span><span class="sxs-lookup"><span data-stu-id="c8395-164">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="c8395-165">Como sucede con cualquier otra interacción, el gesto de desplazamiento lateral también requiere un colisionador.</span><span class="sxs-lookup"><span data-stu-id="c8395-165">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="c8395-166">De forma predeterminada, un cuadrante tiene un colisionador de malla.</span><span class="sxs-lookup"><span data-stu-id="c8395-166">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="c8395-167">Sin embargo, este no es el ideal, ya que es extremadamente fino.</span><span class="sxs-lookup"><span data-stu-id="c8395-167">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="c8395-168">Para que al usuario le resulte más fácil interactuar con el colisionador, lo reemplazaremos con un colisionador de cuadro.</span><span class="sxs-lookup"><span data-stu-id="c8395-168">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="c8395-169">Con el objeto PanGesture aún seleccionado, haz clic en el icono de **configuración** del componente **Mesh Collider** (Colisionador de malla) y selecciona **Remove Component** (Quitar componente) para quitar este colisionador:</span><span class="sxs-lookup"><span data-stu-id="c8395-169">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="c8395-171">En la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar un elemento **Box Collider** (Colisionador de cuadro). A continuación, cambia su valor **Size** (Tamaño) Z a 0,15 para aumentar su espesor:</span><span class="sxs-lookup"><span data-stu-id="c8395-171">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="c8395-173">2. Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-173">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="c8395-174">Con el objeto **PanGesture** todavía seleccionado, agrega el componente **Near Interaction Touchable (Script)** (Interacción próxima táctil [script]) al objeto PanGesture y, a continuación, haz clic en los botones **Fix Bounds** (Corregir límites) y **Fix Center** (Corregir centro) para actualizar el centro local y las propiedades de los límites de Near Interaction Touchable (Script) (Interacción próxima táctil [script]) para que coincidan con BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="c8395-174">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="c8395-176">3. Agregar el componente Hand Interaction Pan Zoom (Script) (Interacción de mano de zoom de desplazamiento lateral [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-176">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="c8395-177">Con el objeto **PanGesture** todavía seleccionado, agrega el componente **Hand Interaction Pan Zoom (Script)** (Interacción de mano de zoom de deslizamiento horizontal [script]) al objeto PanGesture y, a continuación, activa la casilla **Lock Horizontal** (Bloquear horizontalmente) para permitir solo el desplazamiento vertical:</span><span class="sxs-lookup"><span data-stu-id="c8395-177">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="c8395-179">4. Agregar contenido 2D que se desplazará</span><span class="sxs-lookup"><span data-stu-id="c8395-179">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="c8395-180">En el panel Project (Proyecto), busca el material de **PanContent** y, a continuación, haz clic y arrástralo hasta la propiedad 0 del elemento **Material** del representador de malla del objeto **PanGesture**:</span><span class="sxs-lookup"><span data-stu-id="c8395-180">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="c8395-182">En la ventana Inspector, expande el componente de material **PanContent** recién agregado y, a continuación, cambia su valor Y de **Tiling** (Disposición en mosaico) Y a 0,5 para que coincida con el valor de X y los iconos sean cuadrados:</span><span class="sxs-lookup"><span data-stu-id="c8395-182">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="c8395-184">Si entras en el modo de juego, puedes probar el desplazamiento del contenido 2D mediante el gesto de desplazamiento lateral en la simulación en el editor:</span><span class="sxs-lookup"><span data-stu-id="c8395-184">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="c8395-186">5. Agregar contenido 3D que se desplazará</span><span class="sxs-lookup"><span data-stu-id="c8395-186">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="c8395-187">En la ventana Hierarchy (Jerarquía), **crea cuatro cubos** como objetos secundarios del objeto **PanGesture** y define su **escala** de transformación como X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="c8395-187">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="c8395-189">Para espaciar los cubos de forma uniforme y ahorrar tiempo, agrega el componente **Grid Object Collection (Script)** (Colección de objetos de cuadrícula [script]) al objeto principal de los cubos (p. ej., el objeto **PanGesture**) y configura Grid Object Collection (Script) (Colección de objetos de cuadrícula [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="c8395-189">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="c8395-190">Cambia **Num Rows** (Número de filas) a 1 para que todos los cubos estén alineados en una sola fila.</span><span class="sxs-lookup"><span data-stu-id="c8395-190">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="c8395-191">Cambia **Cell Width** (Ancho de celda) a 0,25 para espaciar los cubos dentro de la fila.</span><span class="sxs-lookup"><span data-stu-id="c8395-191">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="c8395-192">A continuación, haz clic en el botón **Actualizar colección** para aplicar la nueva configuración:</span><span class="sxs-lookup"><span data-stu-id="c8395-192">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="c8395-194">6. Agregar el componente Move With Pan (Script) (Mover con desplazamiento lateral [script])</span><span class="sxs-lookup"><span data-stu-id="c8395-194">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="c8395-195">En la ventana Hierarchy (Jerarquía), selecciona todos los **objetos secundarios del cubo** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Move With Pan (Script)** (Mover con desplazamiento lateral [script]) a todos los cubos:</span><span class="sxs-lookup"><span data-stu-id="c8395-195">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="c8395-197">Para obtener un recordatorio sobre cómo seleccionar varios objetos en la ventana Hierarchy (Jerarquía), consulta las instrucciones de [Agregar el componente Manipulation Handler (Script) (Controlador de manipulación [script]) a todos los objetos](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects).</span><span class="sxs-lookup"><span data-stu-id="c8395-197">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="c8395-198">Con todos los cubos aún seleccionados, haz clic en el objeto **PanGesture** y arrástralo al campo **Pan Input Source** (Origen de entrada de desplazamiento lateral):</span><span class="sxs-lookup"><span data-stu-id="c8395-198">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="c8395-200">El componente Move With Pan (Script) (Mover con desplazamiento lateral [script]) de cada cubo realiza escuchas del evento Pan Updated (Actualizado con desplazamiento lateral) que envía el componente Hand Interaction Pan Zoom (Script) (Interacción de mano de zoom de desplazamiento lateral [script]) en el objeto PanGesture, que se asignó como Origen de entrada de desplazamiento lateral en el paso anterior, y actualiza la posición de cada cubo según corresponde.</span><span class="sxs-lookup"><span data-stu-id="c8395-200">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="c8395-201">En la ventana Hierarchy (Jerarquía), selecciona el objeto **PanGesture** y, a continuación, en el inspector, **desactiva** la casilla **Mesh Renderer** (Representador de malla) para deshabilitar el componente del representador de malla:</span><span class="sxs-lookup"><span data-stu-id="c8395-201">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="c8395-203">Si entras en el modo de juego, puedes probar el desplazamiento del contenido 3D mediante el gesto de desplazamiento lateral en la simulación en el editor:</span><span class="sxs-lookup"><span data-stu-id="c8395-203">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="c8395-205">Seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="c8395-205">Eye Tracking</span></span>

<span data-ttu-id="c8395-206">En esta sección, explorarás cómo habilitar el seguimiento ocular en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c8395-206">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="c8395-207">En este ejemplo, implementarás la funcionalidad para hacer que cada objeto de 3DObjectCollection gire lentamente mientras la mirada del usuario lo observa. Además, cuando el objeto observado se seleccione pulsando en el aire o mediante un comando de voz, se desencadenará un efecto de parpadeo.</span><span class="sxs-lookup"><span data-stu-id="c8395-207">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="c8395-208">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="c8395-208">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="c8395-209">Agrega el componente Eye Tracking Target (Script) (Destino del seguimiento ocular [script]) a todos los objetos de destino.</span><span class="sxs-lookup"><span data-stu-id="c8395-209">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="c8395-210">Agrega el componente Eye Tracking Tutorial Demo (Script) (Demostración de tutorial de seguimiento ocular [script]) a todos los objetos de destino.</span><span class="sxs-lookup"><span data-stu-id="c8395-210">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="c8395-211">Implementa el evento While Looking At Target (Al mirar el objetivo).</span><span class="sxs-lookup"><span data-stu-id="c8395-211">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="c8395-212">Implementa el evento On Selected (En selección).</span><span class="sxs-lookup"><span data-stu-id="c8395-212">Implement the On Selected event</span></span>
5. <span data-ttu-id="c8395-213">Habilita el seguimiento ocular simulado para las simulaciones en el editor.</span><span class="sxs-lookup"><span data-stu-id="c8395-213">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="c8395-214">Habilita la entrada de mirada en las funcionalidades de la aplicación del proyecto de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8395-214">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="c8395-215">1. Agrega el componente Eye Tracking Target (Script) (Destino del seguimiento ocular [script]) a todos los objetos de destino.</span><span class="sxs-lookup"><span data-stu-id="c8395-215">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="c8395-216">En la ventana Hierarchy (Jerarquía), expande el objeto **3DObjectCollection** y selecciona todos los **objetos secundarios**. A continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Eye Tracking Target (Script)** (Destino del seguimiento ocular [script]) a todos los objetos secundarios:</span><span class="sxs-lookup"><span data-stu-id="c8395-216">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="c8395-218">Con todos los **objetos secundarios** todavía seleccionados, configura el componente **Eye Tracking Target (Script)** (Destino del seguimiento ocular [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="c8395-218">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="c8395-219">Cambia **Select Action** (Seleccionar acción) a **Select** (Seleccionar) para definir la acción de punteo en el aire para este objeto como selección.</span><span class="sxs-lookup"><span data-stu-id="c8395-219">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="c8395-220">Expande **Voice Select** (Selección de voz) y establece el valor de **Size** (Tamaño) de la lista de comandos de voz en 1. A continuación, en la lista de nuevos elementos que aparece, cambia **Element 0** (Elemento 0) a **Select** (Seleccionar) para definir la acción de comando de voz para este objeto como selección.</span><span class="sxs-lookup"><span data-stu-id="c8395-220">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="c8395-222">2. Agrega el componente Eye Tracking Tutorial Demo (Script) (Demostración de tutorial de seguimiento ocular [script]) a todos los objetos de destino.</span><span class="sxs-lookup"><span data-stu-id="c8395-222">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="c8395-223">Con todos los **objetos secundarios** todavía seleccionados, usa el botón **Add Component** (Agregar componente) para agregar el componente **Eye Tracking Tutorial Demo (Script)** (Demostración de tutorial de seguimiento ocular [script]) a todos los objetos secundarios:</span><span class="sxs-lookup"><span data-stu-id="c8395-223">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="c8395-225">El componente Eye Tracking Target (Script) (Destino del seguimiento ocular [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="c8395-225">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="c8395-226">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="c8395-226">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="c8395-227">3. Implementa el evento While Looking At Target (Al mirar el objetivo).</span><span class="sxs-lookup"><span data-stu-id="c8395-227">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="c8395-228">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cheese** y, a continuación, crea un nuevo evento **While Looking At Target ()** (Al observar el destino []), configura el objeto **Cheese** para recibir el evento y define **EyeTrackingTutorialDemo.RotateTarget** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="c8395-228">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="c8395-230">**Repite** esta acción para cada uno de los objetos secundarios de 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="c8395-230">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="c8395-231">Para obtener un recordatorio sobre cómo implementar eventos, consulta las instrucciones de [Gestos de seguimiento de manos y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="c8395-231">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="c8395-232">4. Implementa el evento On Selected (En selección).</span><span class="sxs-lookup"><span data-stu-id="c8395-232">4. Implement the On Selected event</span></span>

<span data-ttu-id="c8395-233">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cheese** y, a continuación, crea un nuevo evento **On Selected ()** (En la selección []), configura el objeto **Cheese** para recibir el evento y define **EyeTrackingTutorialDemo.BlipTarget** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="c8395-233">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="c8395-235">**Repite** esta acción para cada uno de los objetos secundarios de 3DObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="c8395-235">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="c8395-236">5. Habilita el seguimiento ocular simulado para las simulaciones en el editor.</span><span class="sxs-lookup"><span data-stu-id="c8395-236">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="c8395-237">En la ventana Hierarchy (Jerarquía), selecciona el objeto **MixedRealityToolkit**. A continuación, en la ventana Inspector, selecciona la pestaña **Input** (Entrada), expande la sección **Input Data Providers** (Proveedores de datos de entrada) y, a continuación, la sección **Input Simulation Service** (Servicio de simulación de entrada) y clona **DefaultMixedRealityInputSimulationProfile** para reemplazarlo con tu propio **Input Simulation Profile** (Perfil de simulación de entrada):</span><span class="sxs-lookup"><span data-stu-id="c8395-237">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="c8395-239">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puedes consultar las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="c8395-239">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="c8395-240">En la sección **Eye Simulation** (Simulación ocular), activa la casilla **Simulate Eye Position** (Simular posición ocular) para habilitar la simulación del seguimiento ocular:</span><span class="sxs-lookup"><span data-stu-id="c8395-240">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="c8395-242">Si ahora entras en el modo de juego, puedes probar los efectos de giro y parpadeo que has implementado ajustando la vista para que el cursor toque uno de los objetos y usando la interacción con la mano o el comando de voz para seleccionar el objeto:</span><span class="sxs-lookup"><span data-stu-id="c8395-242">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="c8395-244">Si no usaste DefaultHoloLens2ConfigurationProfile para clonar el perfil de configuración de MRTK personalizable, como se indica en las instrucciones de [Configuración de Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), puede que el seguimiento ocular no esté habilitado en el proyecto y que se deba habilitar.</span><span class="sxs-lookup"><span data-stu-id="c8395-244">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="c8395-245">Para ello, puedes consultar las instrucciones de [Introducción al seguimiento ocular en MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).</span><span class="sxs-lookup"><span data-stu-id="c8395-245">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="c8395-246">6. Habilita la entrada de mirada en las funcionalidades de la aplicación del proyecto de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8395-246">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="c8395-247">Antes de compilar e implementar la aplicación desde Visual Studio en el dispositivo, se debe habilitar la entrada de mirada en las funcionalidades de la aplicación del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c8395-247">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="c8395-248">Para hacerlo, puedes seguir las instrucciones de [Probar la aplicación de Unity en HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="c8395-248">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="c8395-249">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="c8395-249">Congratulations</span></span>

<span data-ttu-id="c8395-250">Has conseguido agregar las funcionalidades básicas de seguimiento ocular a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c8395-250">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="c8395-251">Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="c8395-251">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="c8395-252">En este tutorial, también has obtenido información sobre otras características de entrada avanzadas, como los comandos de voz y los gestos de desplazamiento lateral.</span><span class="sxs-lookup"><span data-stu-id="c8395-252">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="c8395-253">Siguiente lección: 7. Creación de una aplicación de ejemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="c8395-253">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
