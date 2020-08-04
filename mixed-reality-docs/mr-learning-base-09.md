---
title: 'Tutoriales de introducción: 9. Uso de los comandos de voz'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b0b9771d9569d100a354af96a34cd20ef2a3d7c4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376597"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="b6033-105">9. Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="b6033-105">9. Using speech commands</span></span>

## <a name="overview"></a><span data-ttu-id="b6033-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="b6033-106">Overview</span></span>

<span data-ttu-id="b6033-107">En este tutorial, aprenderá a crear comandos de voz y a controlarlos de forma global.</span><span class="sxs-lookup"><span data-stu-id="b6033-107">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="b6033-108">También aprenderá a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b6033-108">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="b6033-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b6033-109">Objectives</span></span>

* <span data-ttu-id="b6033-110">Aprender a crear comandos de voz</span><span class="sxs-lookup"><span data-stu-id="b6033-110">Learn how to create speech commands</span></span>
* <span data-ttu-id="b6033-111">Aprender a controlar los comandos de voz global y localmente</span><span class="sxs-lookup"><span data-stu-id="b6033-111">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="b6033-112">Asegurarse de que la funcionalidad del micrófono está habilitada</span><span class="sxs-lookup"><span data-stu-id="b6033-112">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="b6033-113">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:</span><span class="sxs-lookup"><span data-stu-id="b6033-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b6033-115">La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) al configurar el proyecto de Unity al principio de esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="b6033-115">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="b6033-116">Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.</span><span class="sxs-lookup"><span data-stu-id="b6033-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="b6033-117">Creación de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="b6033-117">Creating speech commands</span></span>

<span data-ttu-id="b6033-118">En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit**, a continuación, en la ventana Inspector, seleccione MixedRealityToolkit > pestaña **Input** (Entrada) y siga los pasos a continuación:</span><span class="sxs-lookup"><span data-stu-id="b6033-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="b6033-119">Expanda la sección **Speech** (Voz).</span><span class="sxs-lookup"><span data-stu-id="b6033-119">Expand the **Speech** section</span></span>
* <span data-ttu-id="b6033-120">Clone **DefaultMixedRealitySpeechCommandsProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_.</span><span class="sxs-lookup"><span data-stu-id="b6033-120">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="b6033-121">Verifique que **Start Behaviour** (Iniciar comportamiento) está establecido en **Auto Start** (Inicio automático).</span><span class="sxs-lookup"><span data-stu-id="b6033-121">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="b6033-123">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="b6033-123">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="b6033-124">En Speech (Voz) > sección **Speech Commands** (Comandos de voz), haz clic en el botón **+ Add a New Speech Command** (Agregar nuevo comando de voz) cuatro veces para agregar cuatro nuevos comandos de voz a la lista de comandos de voz existentes y, a continuación, en el campo **Keyword** (Palabra clave), escriba las frases siguientes:</span><span class="sxs-lookup"><span data-stu-id="b6033-124">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="b6033-125">Enable Indicator (Habilitar indicador)</span><span class="sxs-lookup"><span data-stu-id="b6033-125">Enable Indicator</span></span>
* <span data-ttu-id="b6033-126">Enable Tap to Place (Habilitar pulsar para colocar)</span><span class="sxs-lookup"><span data-stu-id="b6033-126">Enable Tap to Place</span></span>
* <span data-ttu-id="b6033-127">Enable Bounding Box (Habilitar cuadro de límite)</span><span class="sxs-lookup"><span data-stu-id="b6033-127">Enable Bounding Box</span></span>
* <span data-ttu-id="b6033-128">Disable Bounding Box (Deshabilitar cuadro de límite)</span><span class="sxs-lookup"><span data-stu-id="b6033-128">Disable Bounding Box</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="b6033-130">Si el equipo no tiene micrófono, puede asignar un KeyCode a los comandos de voz, lo que le permitirá desencadenarlos cuando se presione la tecla correspondiente.</span><span class="sxs-lookup"><span data-stu-id="b6033-130">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="b6033-131">Control de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="b6033-131">Controlling speech commands</span></span>

<span data-ttu-id="b6033-132">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** para buscar los objetos prefabricados de información sobre herramientas:</span><span class="sxs-lookup"><span data-stu-id="b6033-132">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="b6033-134">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena.</span><span class="sxs-lookup"><span data-stu-id="b6033-134">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="b6033-135">Asigna al objeto el nombre **SpeechInputHandler_Global** y, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="b6033-135">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="b6033-136">**Desactive** la casilla **Is Focus Required** (Se requiere foco) para que no sea necesario que el usuario observe el objeto con el componente SpeechInputHandler para desencadenar el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b6033-136">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="b6033-137">En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b6033-137">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="b6033-139">En el componente SpeechInputHandler, haga clic en el icono pequeño **+** tres veces para agregar tres elementos de palabra clave:</span><span class="sxs-lookup"><span data-stu-id="b6033-139">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="b6033-141">Expanda **Element 0** (Elemento 0) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="b6033-141">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="b6033-142">En el campo **Keyword** (Palabra clave), escriba **Enable Indicator** (Habilitar indicador) para hacer referencia al comando de voz Enable Indicator que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="b6033-142">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="b6033-143">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b6033-144">En la ventana Hierarchy (Jerarquía), asigne el objeto **Indicator** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="b6033-144">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b6033-145">En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-145">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="b6033-146">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="b6033-146">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="b6033-148">Expanda **Element 1** (Elemento 1) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="b6033-148">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="b6033-149">En el campo **Keyword** (Palabra clave), escriba **Enable Bounding Box** (Habilitar cuadro de límite) para hacer referencia al comando de voz Enable Bounding Box que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="b6033-149">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="b6033-150">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-150">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b6033-151">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="b6033-151">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b6033-152">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundingBox** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-152">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b6033-153">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="b6033-153">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="b6033-154">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-154">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="b6033-155">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="b6033-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b6033-156">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-156">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b6033-157">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="b6033-157">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="b6033-159">Expanda **Element 2** (Elemento 2) y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="b6033-159">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="b6033-160">En el campo **Keyword** (Palabra clave), escriba **Disable Bounding Box** (Deshabilitar cuadro de límite) para hacer referencia al comando de voz Disable Bounding Box que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="b6033-160">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="b6033-161">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-161">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b6033-162">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="b6033-162">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b6033-163">En la lista desplegable **No Function** (Ninguna función), seleccione **BoundingBox** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-163">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b6033-164">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="b6033-164">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="b6033-165">Haga clic en el icono **+** pequeño para agregar otro evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-165">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="b6033-166">En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).</span><span class="sxs-lookup"><span data-stu-id="b6033-166">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="b6033-167">En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-167">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b6033-168">Verifique que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="b6033-168">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="b6033-170">En la ventana Hierarchy (Jerarquía), seleccione RoverExplorer > objeto **RoverAssembly** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b6033-170">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="b6033-171">Verifique que la casilla **Is Focus Required** (Se requiere foco) esté **activada** para exigir que el usuario observe el objeto con el componente SpeechInputHandler, es decir, RoverAssembly, para desencadenar el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b6033-171">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="b6033-172">En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b6033-172">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="b6033-174">En el componente SpeechInputHandler, haga clic en el icono **+** pequeño para agregar un elemento de palabra clave, expanda el elemento recién creado y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="b6033-174">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="b6033-175">En el campo **Keyword** (Palabra clave), escriba **Enable Tap to Place** (Habilitar pulsar para colocar) para hacer referencia al comando de voz Enable Tap to Place que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="b6033-175">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="b6033-176">Haga clic en el icono **+** pequeño para agregar un evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-176">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="b6033-177">En la ventana Hierarchy (Jerarquía), asigne el propio objeto, es decir, el mismo objeto **RoverAssembly**, al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="b6033-177">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="b6033-178">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="b6033-178">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="b6033-179">Marque la casilla del argumento para que esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="b6033-179">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="b6033-181">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="b6033-181">Congratulations</span></span>

<span data-ttu-id="b6033-182">En este tutorial, ha aprendido a crear comandos de voz y a controlarlos de forma global.</span><span class="sxs-lookup"><span data-stu-id="b6033-182">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="b6033-183">También ha aprendido a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.</span><span class="sxs-lookup"><span data-stu-id="b6033-183">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="b6033-184">Esto también concluye la serie de [tutoriales de introducción](mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="b6033-184">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="b6033-185">A través de estos tutoriales, ha creado correctamente una experiencia de realidad mixta completa desde cero con MRTK.</span><span class="sxs-lookup"><span data-stu-id="b6033-185">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="b6033-186">En las siguientes dos series de tutoriales, [Tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) y [Tutoriales de funcionalidades para varios usuarios](mr-learning-sharing-01.md), primero aprenderá a integrar Azure Spatial Anchors en el proyecto para anclar la experiencia del explorador de róver que creó en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="b6033-186">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="b6033-187">A continuación, aprenderá a agregar funcionalidades de varios usuarios al proyecto para compartir movimientos de usuarios y objetos en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="b6033-187">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>
