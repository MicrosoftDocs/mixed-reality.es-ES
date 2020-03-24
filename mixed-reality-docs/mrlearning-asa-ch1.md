---
title: 'Tutoriales sobre Azure Spatial Anchors: 1. Introducción a Azure Spatial Anchors'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fa0ebc409fa38f664bdd0966906c6fd77f7a6081
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376152"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="4bb6a-105">1. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4bb6a-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="4bb6a-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="4bb6a-106">Overview</span></span>

<span data-ttu-id="4bb6a-107">Esta es la segunda serie de los tutoriales de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="4bb6a-108">En esta serie de tutoriales de tres partes, aprenderás los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="4bb6a-109">En este primer tutorial, [Introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md), explorarás los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar anclajes de Azure en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="4bb6a-110">En el segundo tutorial, [Guardar, recuperar y compartir Azure Spatial Anchors](mrlearning-asa-ch2.md), aprenderás a guardar Azure Spatial Anchors en varias sesiones de aplicación al guardar la información de anclaje en el almacenamiento de HoloLens 2 y a compartir esta información en otros dispositivos para alinear el anclaje en varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="4bb6a-111">En el tercer tutorial, [Mostrar comentarios de Azure Spatial Anchors](mrlearning-asa-ch3.md), aprenderás a proporcionar a los usuarios comentarios sobre los eventos y estados de anclaje al usar Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="4bb6a-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4bb6a-112">Objectives</span></span>

* <span data-ttu-id="4bb6a-113">Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4bb6a-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="4bb6a-114">Crear, cargar y descargar anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="4bb6a-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4bb6a-115">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="4bb6a-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="4bb6a-116">Si aún no has completado la serie de [tutoriales de introducción](mrlearning-base.md), es recomendable que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="4bb6a-117">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="4bb6a-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="4bb6a-118">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="4bb6a-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="4bb6a-119">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="4bb6a-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="4bb6a-120">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="4bb6a-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="4bb6a-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="4bb6a-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="4bb6a-122">Completa la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación HoloLens en Unity que use Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4bb6a-123">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="4bb6a-124">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="4bb6a-125">Creación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="4bb6a-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="4bb6a-126">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="4bb6a-127">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mrlearning-base-ch1.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="4bb6a-128">[Crear un proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asignarle un nombre adecuado; por ejemplo, *Tutoriales de MRTK*.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="4bb6a-129">Configurar el proyecto de Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4bb6a-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="4bb6a-130">Importar recursos de TextMesh Pro Essential</span><span class="sxs-lookup"><span data-stu-id="4bb6a-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="4bb6a-131">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="4bb6a-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="4bb6a-132">Configurar el proyecto de Unity para Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="4bb6a-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="4bb6a-133">[Agregar Mixed Reality Toolkit a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y asignar un nombre adecuado a la escena; por ejemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="4bb6a-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="4bb6a-134">A continuación, sigue las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (modificación de la opción de visualización reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="4bb6a-135">Como se mencionó en las instrucciones vinculadas más arriba, [Configuración del proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), es altamente recomendable no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="4bb6a-136">Adición de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="4bb6a-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="4bb6a-137">En esta sección, instalarás el paquete integrado de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que importarás en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="4bb6a-138">En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):</span><span class="sxs-lookup"><span data-stu-id="4bb6a-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4bb6a-140">Puede que el paquete de AR Foundation tarde unos segundos en aparecer en la lista.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="4bb6a-141">En la ventana Package Manager (Administrador de paquetes), selecciona **AR Foundation** e instala el paquete haciendo clic en el botón **Instalar**:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="4bb6a-143">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="4bb6a-143">Importing the tutorial assets</span></span>

<span data-ttu-id="4bb6a-144">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="4bb6a-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="4bb6a-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="4bb6a-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4bb6a-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="4bb6a-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4bb6a-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="4bb6a-148">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="4bb6a-149">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="4bb6a-151">Creación y preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="4bb6a-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="4bb6a-152">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="4bb6a-153">Desde la ventana Proyecto, desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs** (Objetos prefabricados).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="4bb6a-154">Mientras mantienes presionado el botón CTRL, haz clic en **ButtonParent**, **DebugWindow**, **Instructions** y **ParentAnchor** para seleccionar los cuatro objetos prefabricados:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="4bb6a-156">Con los cuatro objetos prefabricados aún seleccionados, arrástralos a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="4bb6a-158">Para centrarte en los objetos de la escena, puedes hacer doble clic en el objeto ParentAnchor y, a continuación, volver a alejarte ligeramente:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="4bb6a-160">Si te molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puedes ocultarlos. Para hacerlo, desactiva los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="4bb6a-161">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="4bb6a-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="4bb6a-162">En esta sección, agregarás scripts a la escena para crear una serie de eventos de botón que muestran los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="4bb6a-163">1. Configurar el componente Pressable Button Holo Lens 2 (Script) (Botón presionable de HoloLens 2 [script])</span><span class="sxs-lookup"><span data-stu-id="4bb6a-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="4bb6a-164">En la ventana Hierarchy (Jerarquía), expande el objeto **ButtonParent** y selecciona el primer objeto secundario denominado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="4bb6a-166">En la ventana Inspector, busca el componente **Pressable Button Holo Lens 2 (Script)** (Botón presionable de HoloLens 2 [script]) y agrega un nuevo cliente de escucha de eventos al evento **Button Pressed ()** (Botón presionado []). Para hacerlo, haz clic en el icono **+** :</span><span class="sxs-lookup"><span data-stu-id="4bb6a-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="4bb6a-168">Con el objeto StartAzureSession aún seleccionado en la ventana Hierarchy (Jerarquía), haz clic en el objeto **ParentAnchor** y arrástralo desde la ventana Hierarchy (Jerarquía) al campo **None (Object)** (Ninguno [objeto]) del cliente de escucha de eventos que acabas de agregar para que el objeto ParentAnchor escuche los eventos de botón presionado de este botón:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="4bb6a-170">Haz clic en la lista desplegable **No Function** (Ninguna función) del mismo cliente de escucha de eventos y, a continuación, selecciona **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el evento de botón presionado desde este botón:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="4bb6a-172">2. Configurar el componente Interactable (Script) (Interactuable [script])</span><span class="sxs-lookup"><span data-stu-id="4bb6a-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="4bb6a-173">Con el objeto StartAzureSession todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, busca el componente **Interactable (Script)** (Interactuable [script]) y repite el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="4bb6a-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="4bb6a-175">3. Configurar los botones restantes</span><span class="sxs-lookup"><span data-stu-id="4bb6a-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="4bb6a-176">Para cada uno de los botones restantes, completa el proceso descrito en los pasos 1 y 2 anteriores para asignar funciones a los eventos **Button Pressed ()** (Botón presionado []) y **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="4bb6a-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="4bb6a-177">Para el objeto **StopAzureSession**, asigna la funciónAnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="4bb6a-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="4bb6a-178">Para el objeto **CreateAzureAnchor**, asigna la función AnchorModuleScript > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="4bb6a-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="4bb6a-179">A continuación, vuelve a arrastrar **ParentAnchor** al campo **None (Game Object)** (Ninguno [Objeto del juego]).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="4bb6a-180">Para el objeto **RemoveLocalAnchor**, asigna la función AnchorModuleScript > **RemoveLocalAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="4bb6a-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="4bb6a-181">A continuación, vuelve a arrastrar **ParentAnchor** al campo **None (Game Object)** (Ninguno [Objeto del juego]) vacío.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="4bb6a-182">Para el objeto **FindAzureAnchor**, asigna la función AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="4bb6a-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="4bb6a-183">Para el objeto **DeleteAzureAnchor**, asigna la función AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="4bb6a-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="4bb6a-184">4. Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="4bb6a-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="4bb6a-185">En la ventana Hierarchy (Jerarquía), selecciona el objeto **ParentAnchor** y, en la ventana Inspector, desplázate hacia abajo hasta el componente **Spatial Anchor Manager (Script)** (Administrador del anclaje espacial [script]).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="4bb6a-186">A continuación, en la sección **Credentials** (Credenciales), pega el identificador y la clave de la cuenta de Spatial Anchors, que creaste como parte de los [Requisitos previos](mrlearning-asa-ch1.md#prerequisites) de este tutorial, en los campos **Spatial Anchors Account Id** (Id. de cuenta de Spatial Anchors) y **Spatial Anchors Account Key** (Clave de cuenta de Spatial Anchors):</span><span class="sxs-lookup"><span data-stu-id="4bb6a-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="4bb6a-188">Prueba de los comportamientos básicos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4bb6a-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="4bb6a-189">Ahora que la escena está configurada para mostrar los aspectos básicos de Azure Spatial Anchors, es el momento de implementar la aplicación para que puedas experimentar Azure Spatial Anchors de primera mano.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="4bb6a-190">1. Agregar las funcionalidades adicionales necesarias</span><span class="sxs-lookup"><span data-stu-id="4bb6a-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="4bb6a-191">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador):</span><span class="sxs-lookup"><span data-stu-id="4bb6a-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="4bb6a-193">En la ventana Player Settings (Configuración del jugador), selecciona **Player** (Jugador) y, a continuación, **Publishing Settings** (Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="4bb6a-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="4bb6a-195">En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén activadas.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="4bb6a-196">A continuación, habilita las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** y **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="4bb6a-198">2. Implementar la aplicación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4bb6a-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="4bb6a-199">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad Azure Spatial Anchors, debes implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="4bb6a-200">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puedes consultar las instrucciones de [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="4bb6a-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="4bb6a-201">3. Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="4bb6a-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="4bb6a-202">Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debes asegurarte de que el dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="4bb6a-203">Cuando la aplicación se ejecute en el dispositivo, sigue las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="4bb6a-205">Anclaje de una experiencia</span><span class="sxs-lookup"><span data-stu-id="4bb6a-205">Anchoring an experience</span></span>

<span data-ttu-id="4bb6a-206">En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="4bb6a-207">Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="4bb6a-208">En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="4bb6a-209">1. Incorporación de la experiencia del lanzacohetes</span><span class="sxs-lookup"><span data-stu-id="4bb6a-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="4bb6a-210">En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > Objetos prefabricados > RocketLauncher) y selecciona el objeto prefabricado **RocketLauncher_Complete**:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="4bb6a-212">Con el objeto prefabricado RocketLauncher_Complete todavía seleccionado, arrástralo sobre el objeto **ParentAnchor** en la ventana Hierarchy (Jerarquía) para convertirlo en un elemento secundario del objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="4bb6a-214">2. Cambio de posición de la experiencia del lanzacohetes</span><span class="sxs-lookup"><span data-stu-id="4bb6a-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="4bb6a-215">Coloca, gira y escala el objeto **RocketLauncher_Complete** a una escala y orientación adecuadas, al mismo tiempo que se garantiza que el objeto **ParentAnchor** sigue expuesto; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4bb6a-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="4bb6a-216">Transforma el valor de **Position** (Posición) X = 0, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="4bb6a-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="4bb6a-217">Transforma el valor de **Rotation** (Rotación) X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="4bb6a-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="4bb6a-218">Transforma el valor de **Scale** (Escala) X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="4bb6a-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="4bb6a-220">Ahora, en la aplicación, los usuarios pueden mover el cubo para cambiar la posición de la experiencia del lanzacohetes por completo.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="4bb6a-221">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el cuadro de límite que rodea la experiencia, el uso de gizmos de posición y rotación, etc.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4bb6a-222">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="4bb6a-222">Congratulations</span></span>

<span data-ttu-id="4bb6a-223">En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="4bb6a-224">El tutorial te ha proporcionado varios botones que te permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors y crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="4bb6a-225">En la siguiente lección, aprenderás a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="4bb6a-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="4bb6a-226">Siguiente lección: 2. Guardado, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4bb6a-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
