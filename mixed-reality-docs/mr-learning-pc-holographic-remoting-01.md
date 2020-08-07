---
title: 'Tutoriales de comunicación remota holográfica para PC: 1. Introducción a la comunicación remota holográfica para PC'
description: Complete este curso para aprender cómo crear una experiencia de realidad mixta remota del PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4929634d70a082e835eb7bd6b5680719338a5e92
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476977"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="8114c-105">1. Introducción a la comunicación remota holográfica para PC</span><span class="sxs-lookup"><span data-stu-id="8114c-105">1. Getting started with PC Holographic Remoting</span></span>

## <a name="overview"></a><span data-ttu-id="8114c-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="8114c-106">Overview</span></span>

  <span data-ttu-id="8114c-107">Le damos la bienvenida a los tutoriales de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8114c-107">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="8114c-108">En esta serie de tutoriales de dos partes, aprenderá a crear una demostración de experiencia de realidad mixta, así como a crear una aplicación para PC para la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="8114c-108">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

   <span data-ttu-id="8114c-109">En este tutorial sobre cómo [crear una experiencia de realidad mixta](mr-learning-pc-holographic-remoting-01.md), aprenderá a crear una experiencia de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8114c-109">In this tutorial, [Create mixed reality experience](mr-learning-pc-holographic-remoting-01.md), you will learn how to create a mixed reality experience.</span></span> <span data-ttu-id="8114c-110">Se mostrarán los elementos de la interfaz de usuario, la manipulación de modelos 3D, el recorte de modelos y las características de seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="8114c-110">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

  <span data-ttu-id="8114c-111">En el segundo tutorial, [Creación de una aplicación de comunicación remota holográfica](mr-learning-pc-holographic-remoting-02.md), aprenderá a crear una aplicación de PC para comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="8114c-111">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="8114c-112">Y a conectarla a HoloLens 2 en cualquier momento, de modo que podrá visualizar contenido 3D en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8114c-112">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="8114c-113">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8114c-113">Objectives</span></span>

* <span data-ttu-id="8114c-114">Importar recursos y configurar la escena</span><span class="sxs-lookup"><span data-stu-id="8114c-114">Import assets and set up the scene</span></span>
* <span data-ttu-id="8114c-115">Interacción con hologramas mediante botones y elementos de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="8114c-115">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="8114c-116">Configurar objetos 3D para la característica de recorte</span><span class="sxs-lookup"><span data-stu-id="8114c-116">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="8114c-117">Aprender a activar la información sobre herramientas con el seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="8114c-117">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8114c-118">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="8114c-118">Prerequisites</span></span>

* <span data-ttu-id="8114c-119">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8114c-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8114c-120">Conocimientos básicos de programación de C#</span><span class="sxs-lookup"><span data-stu-id="8114c-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="8114c-121">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="8114c-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="8114c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X montado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="8114c-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="8114c-123">Se **recomienda encarecidamente** completar la serie de tutoriales de [introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8114c-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="8114c-124">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="8114c-124">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="8114c-125">Sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8114c-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>
> * <span data-ttu-id="8114c-126">La comunicación remota holográfica con proyectos de MRTK solo funcionará con el XR heredado.</span><span class="sxs-lookup"><span data-stu-id="8114c-126">Holographic Remoting with MRTK projects will only work with legacy XR.</span></span> <span data-ttu-id="8114c-127">De momento no se admite el SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="8114c-127">XR SDK is not supported at this time.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="8114c-128">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="8114c-128">Creating and preparing the Unity project</span></span>

<span data-ttu-id="8114c-129">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="8114c-129">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="8114c-130">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="8114c-130">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="8114c-131">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="8114c-131">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="8114c-132">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="8114c-132">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="8114c-133">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="8114c-133">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="8114c-134">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="8114c-134">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="8114c-135">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="8114c-135">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="8114c-136">[Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignarle un nombre adecuado; por ejemplo, **PC Holographic Remoting**</span><span class="sxs-lookup"><span data-stu-id="8114c-136">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="8114c-137">A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK para la escena por el perfil **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="8114c-137">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="8114c-138">Cambie las opciones de visualización de la malla de reconocimiento espacial a **Oclusión**.</span><span class="sxs-lookup"><span data-stu-id="8114c-138">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="8114c-139">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="8114c-139">Importing the tutorial assets</span></span>

<span data-ttu-id="8114c-140">Descargue e **importe** el paquete [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="8114c-140">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="8114c-141">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="8114c-141">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="8114c-142">Una vez importados los recursos del tutorial, la ventana Proyecto debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="8114c-142">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="8114c-144">Configuración y preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="8114c-144">Configuring and preparing the scene</span></span>

<span data-ttu-id="8114c-145">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="8114c-145">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="8114c-146">Desde la ventana Proyecto, desplácese hasta **Assets** (Recursos) > **MRTK.Tutorials.PCHolograhicRemoting** > carpeta **Prefabs** (Recursos prefabricados).</span><span class="sxs-lookup"><span data-stu-id="8114c-146">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="8114c-147">Mientras mantiene presionado el botón CTRL, haga clic en los seis elementos prefabricados siguientes.</span><span class="sxs-lookup"><span data-stu-id="8114c-147">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="8114c-148">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="8114c-148">ButtonParent</span></span>
* <span data-ttu-id="8114c-149">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="8114c-149">ClippingObjects</span></span>
* <span data-ttu-id="8114c-150">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="8114c-150">HandSpatialMapButton</span></span>
* <span data-ttu-id="8114c-151">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8114c-151">Instructions</span></span>
* <span data-ttu-id="8114c-152">ModelParent</span><span class="sxs-lookup"><span data-stu-id="8114c-152">ModelParent</span></span>
* <span data-ttu-id="8114c-153">Plataforma</span><span class="sxs-lookup"><span data-stu-id="8114c-153">Platform</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="8114c-155">Arrastre y coloque estos modelos de la carpeta Prefabs en la **ventana Jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="8114c-155">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="8114c-157">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **ModelParent** y, a continuación, volver a acercarse ligeramente:</span><span class="sxs-lookup"><span data-stu-id="8114c-157">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="8114c-159">Si le molestan los grandes iconos de la escena, como los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">desactive el menú Gizmos</a>.</span><span class="sxs-lookup"><span data-stu-id="8114c-159">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="8114c-160">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="8114c-160">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="8114c-161">En esta sección, agregará scripts a la escena para crear eventos de botón que muestren los aspectos básicos de la funcionalidad de cambio y recorte de modelos.</span><span class="sxs-lookup"><span data-stu-id="8114c-161">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="8114c-162">1. Configuración del componente Interactable (Script) (Interactivo [script])</span><span class="sxs-lookup"><span data-stu-id="8114c-162">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="8114c-163">En la ventana Jerarquía, expanda el objeto **ButtonParent** y seleccione **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="8114c-163">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="8114c-164">En la ventana Inspector, busque el componente **Interactable (Script)** (Interactivo [script]) y haga clic en el icono **+** debajo del evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="8114c-164">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="8114c-166">Con el objeto **NextButton** aún seleccionado en la ventana Jerarquía, haga clic en el objeto **ButtonParent** y arrástrelo desde la ventana Jerarquía al campo **None (Object)** (Ninguno [objeto]) del evento que acaba de agregar; de este modo, el objeto ButtonParent escuchará los eventos de clic de este botón:</span><span class="sxs-lookup"><span data-stu-id="8114c-166">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="8114c-168">Haga clic en la lista desplegable **Ninguna función** del mismo evento.</span><span class="sxs-lookup"><span data-stu-id="8114c-168">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="8114c-169">A continuación, seleccione **ViewButtonControl** > **NextModel ()** para establecer la función **NextModel ()** como la acción que se desencadenará cuando se activen los eventos de botón presionado de este botón:</span><span class="sxs-lookup"><span data-stu-id="8114c-169">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="8114c-171">2. Configuración de los botones restantes</span><span class="sxs-lookup"><span data-stu-id="8114c-171">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="8114c-172">Para cada uno de los botones restantes, complete el proceso descrito anteriormente para asignar funciones a los eventos **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="8114c-172">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="8114c-173">Para el objeto PreviousButton, asigne la función **ViewButtonControl** > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="8114c-173">For PreviousButton object, assign the **ViewButtonContro**l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="8114c-174">En el caso de ClippingButton, seleccione **ToggleButton** > función **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="8114c-174">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="8114c-175">3. Configuración de los componentes View Button Control (Script) (Ver control de botón [script]) y Toggle Button (Script) (Botón de alternancia [script])</span><span class="sxs-lookup"><span data-stu-id="8114c-175">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="8114c-176">Ahora los botones están configurados para mostrar la funcionalidad de cambio y recorte del modelo.</span><span class="sxs-lookup"><span data-stu-id="8114c-176">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="8114c-177">Es el momento de agregar los modelos 3D y los objetos de recorte al script.</span><span class="sxs-lookup"><span data-stu-id="8114c-177">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="8114c-178">Hemos incluido seis modelos 3D distintos para la demostración; expanda el objeto ***ModelParentobject*** para exponer estos modelos 3D.</span><span class="sxs-lookup"><span data-stu-id="8114c-178">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="8114c-179">Con el objeto ButtonParent aún seleccionado en la ventana Jerarquía, en la ventana Inspector, busque el componente **View Button Control (Script)** (Ver control de botón [script]) y expanda la variable **Models**.</span><span class="sxs-lookup"><span data-stu-id="8114c-179">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="8114c-180">En el campo **Size**, escriba el número de modelos 3D que quiere tener en la escena.</span><span class="sxs-lookup"><span data-stu-id="8114c-180">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="8114c-181">En este caso, sería seis.</span><span class="sxs-lookup"><span data-stu-id="8114c-181">In this case, it would be six.</span></span> <span data-ttu-id="8114c-182">Se crearán los campos para agregar nuevos modelos 3D.</span><span class="sxs-lookup"><span data-stu-id="8114c-182">It will create fields for adding new 3D models.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="8114c-184">Arrastre y coloque cada objeto secundario del objeto ModelParent en dichos campos.</span><span class="sxs-lookup"><span data-stu-id="8114c-184">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="8114c-186">Arrastre y coloque el objeto **ClippingObjects** desde la ventana Jerarquía hasta el campo **Clipping Object** (Objeto de recorte) del componente **Toggle Button (Script)** (Botón de alternancia [script]).</span><span class="sxs-lookup"><span data-stu-id="8114c-186">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="8114c-187">Permanezca solo en el objeto primario de botón.</span><span class="sxs-lookup"><span data-stu-id="8114c-187">Stay in button parent object only.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="8114c-189">En la ventana Jerarquía, seleccione el elemento prefabricado **ClippingObjects** y habilítelo en la ventana Inspector para activar los objetos de recorte.</span><span class="sxs-lookup"><span data-stu-id="8114c-189">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="8114c-190">Configuración de los objetos de recorte para habilitar la característica de recorte</span><span class="sxs-lookup"><span data-stu-id="8114c-190">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="8114c-191">En esta sección, agregará el representador de objetos secundarios del objeto MarsCuriosityRover a un objeto de recorte individual para mostrar el recorte del modelo MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="8114c-191">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="8114c-192">En la ventana Jerarquía, expanda el objeto **ClippingObjects** para exponer los tres objetos de recorte diferentes que usará en este proyecto.</span><span class="sxs-lookup"><span data-stu-id="8114c-192">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="8114c-193">Para configurar el objeto **ClippingSphere**, haga clic en él y, en la ventana Inspector, busque el componente **Clipping Sphere (Script)** (Esfera de recorte [script]).</span><span class="sxs-lookup"><span data-stu-id="8114c-193">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="8114c-194">Escriba el número de representadores en el campo de tamaño que necesita agregar al modelo 3D.</span><span class="sxs-lookup"><span data-stu-id="8114c-194">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="8114c-195">En este caso, agregue 10 objetos secundarios MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="8114c-195">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="8114c-196">De este modo, se crearán campos para agregar los representadores; después, arrastre y coloque los objetos del modelo secundario del objeto MarsCuriosityRover en estos campos.</span><span class="sxs-lookup"><span data-stu-id="8114c-196">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="8114c-198">Siga el mismo proceso y agregue los representadores de objetos secundarios de MarsCuriosityRover a los objetos **ClippingBox** y **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="8114c-198">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="8114c-199">En este tutorial, solo se usará el modelo MarsCuriosityRover como demostración de la característica de recorte.</span><span class="sxs-lookup"><span data-stu-id="8114c-199">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="8114c-200">Se agregarán características de recorte a más modelos, se aumentará el tamaño del representador y se agregarán sus representadores de malla individuales.</span><span class="sxs-lookup"><span data-stu-id="8114c-200">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="8114c-201">Configuración del seguimiento ocular para resaltar información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="8114c-201">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="8114c-202">En esta sección, explorarás cómo habilitar el seguimiento ocular en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="8114c-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="8114c-203">Por ejemplo, implementará la funcionalidad para resaltar la información sobre herramientas relacionada con las piezas de MarsCuriosityRover cuando las mira, y ocultará dicha información al apartar la mirada.</span><span class="sxs-lookup"><span data-stu-id="8114c-203">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="8114c-204">1. Identificación de los objetos de destino y la información sobre herramientas asociada</span><span class="sxs-lookup"><span data-stu-id="8114c-204">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="8114c-205">En la ventana Jerarquía, expanda el objeto ModelParent.</span><span class="sxs-lookup"><span data-stu-id="8114c-205">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="8114c-206">Expanda ***MarsCuriosity-> Rover*** para encontrar cinco piezas principales de MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer** y **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="8114c-206">Expand the ***MarsCuriosity -> Rover*** to find five main parts of the MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="8114c-207">Observe los cinco objetos de información sobre herramientas correspondientes con las piezas de MarsCuriosityRover en la ventana Jerarquía.</span><span class="sxs-lookup"><span data-stu-id="8114c-207">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="8114c-208">Configurará estos objetos para mejorar la experiencia al mirar las piezas de MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="8114c-208">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="8114c-210">2. Implementación de los eventos While Looking At Target () y On Look Away ()</span><span class="sxs-lookup"><span data-stu-id="8114c-210">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="8114c-211">En la ventana Jerarquía, seleccione el objeto ***POI-Camera***.</span><span class="sxs-lookup"><span data-stu-id="8114c-211">In the Hierarchy window, select the ***POI-Camera*** object.</span></span> <span data-ttu-id="8114c-212">En la ventana Inspector, busque el componente **Eye Tracking Target (Script)** (Objetivo de seguimiento ocultar [script]) y configure los eventos **While Looking At Target ()**  & **On Look Away ()** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8114c-212">In the Inspector window, locate the **Eye Tracking Target (Script)** component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="8114c-213">Asigne el objeto **POI-Camera ToolTip** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="8114c-213">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="8114c-214">En la lista desplegable **Ninguna función** del evento **While Looking At Target ()** , seleccione **GameObject** > **SetActive (bool)** .</span><span class="sxs-lookup"><span data-stu-id="8114c-214">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="8114c-215">Active la **Casilla** debajo para que, al mirar el objeto de destino, la acción desencadenada sea resaltar la información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="8114c-215">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="8114c-217">Siga el mismo proceso y haga clic en la lista desplegable **Ninguna función** del escucha de eventos **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="8114c-217">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="8114c-218">A continuación, seleccione **GameObject** > **SetActive (bool)** y deje la **Casilla** vacía para que, al apartar la mirada del objeto de destino, la acción desencadenada sea ocultar la información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="8114c-218">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="8114c-220">Siga el mismo proceso y asigne los objetos de información sobre herramientas a los eventos **While Looking At Target ()**  & **On Look Away ()** de las piezas de **MarsCuriosityRover** correspondientes.</span><span class="sxs-lookup"><span data-stu-id="8114c-220">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="8114c-221">Para habilitar el seguimiento ocular, siga estas [instrucciones](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="8114c-221">To enable eye tracking, please follow these [guidelines](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="8114c-222">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="8114c-222">Congratulations</span></span>

<span data-ttu-id="8114c-223">En este tutorial, aprendió a crear una experiencia de realidad mixta que muestra los elementos de la interfaz de usuario, la manipulación de modelos 3D, el recorte de modelos y las características de seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="8114c-223">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="8114c-224">El tutorial le proporcionó los elementos NextButton y PreviousButton que le permiten explorar la experiencia del visor de modelos 3D.</span><span class="sxs-lookup"><span data-stu-id="8114c-224">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="8114c-225">El elemento ClippingObjectButton activó los objetos de recorte para experimentar la característica de recorte.</span><span class="sxs-lookup"><span data-stu-id="8114c-225">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="8114c-226">El tutorial también le proporcionó un elemento de seguimiento ocular para habilitar el resaltado de la información sobre herramientas en la experiencia.</span><span class="sxs-lookup"><span data-stu-id="8114c-226">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="8114c-227">En la próxima lección, aprenderá a crear una aplicación de comunicación remota holográfica para PC para conectarse a HoloLens 2 en cualquier momento, de modo que podrá visualizar contenido 3D en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8114c-227">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

[<span data-ttu-id="8114c-228">Siguiente lección: 2. Creación de una aplicación de comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="8114c-228">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)
