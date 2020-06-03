---
title: 'Tutoriales sobre Azure Spatial Anchors: 1. Introducción a Azure Spatial Anchors'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2a171d601d094375a56734e8d7890c9d3e17c887
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866915"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="719b4-105">1. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="719b4-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="719b4-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="719b4-106">Overview</span></span>

<span data-ttu-id="719b4-107">Esta es la segunda serie de los tutoriales de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="719b4-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="719b4-108">En esta serie de tutoriales de cuatro partes, aprenderás los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="719b4-108">In this four-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="719b4-109">En este primer tutorial, [Introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md), explorarás los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar anclajes de Azure en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="719b4-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="719b4-110">En el segundo tutorial, [Guardar, recuperar y compartir Azure Spatial Anchors](mrlearning-asa-ch2.md), aprenderás a guardar Azure Spatial Anchors en varias sesiones de aplicación al guardar la información de anclaje en el almacenamiento de HoloLens 2 y a compartir esta información en otros dispositivos para alinear el anclaje en varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="719b4-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="719b4-111">En el tercer tutorial, [Mostrar comentarios de Azure Spatial Anchors](mrlearning-asa-ch3.md), aprenderás a proporcionar a los usuarios comentarios sobre los eventos y estados de anclaje al usar Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="719b4-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="719b4-112">En el cuarto tutorial, [Azure Spatial Anchors para iOS y Android](mrlearning-asa-ch4.md), aprenderás a compilar e implementar tu proyecto en dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="719b4-112">In the fourth tutorial, [Azure Spatial Anchors for Android and iOS](mrlearning-asa-ch4.md), you will learn how to build and deploy your project to Android and iOS devices.</span></span>

## <a name="objectives"></a><span data-ttu-id="719b4-113">Objetivos</span><span class="sxs-lookup"><span data-stu-id="719b4-113">Objectives</span></span>

* <span data-ttu-id="719b4-114">Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="719b4-114">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="719b4-115">Crear, cargar y descargar anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="719b4-115">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="719b4-116">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="719b4-116">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="719b4-117">Si aún no has completado la serie de [tutoriales de introducción](mrlearning-base.md), es recomendable que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="719b4-117">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="719b4-118">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="719b4-118">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="719b4-119">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="719b4-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="719b4-120">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="719b4-120">Some basic C# programming ability</span></span>
* <span data-ttu-id="719b4-121">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="719b4-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="719b4-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="719b4-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="719b4-123">Completa la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación HoloLens en Unity que use Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="719b4-123">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="719b4-124">Si piensas implementar en Android</span><span class="sxs-lookup"><span data-stu-id="719b4-124">If you intend to deploy to Android</span></span>
    * <span data-ttu-id="719b4-125">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="719b4-125">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
    * <span data-ttu-id="719b4-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de Android agregado</span><span class="sxs-lookup"><span data-stu-id="719b4-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Android Build Support module added</span></span>
* <span data-ttu-id="719b4-127">Si piensas implementar en iOS</span><span class="sxs-lookup"><span data-stu-id="719b4-127">If you intend to deploy to iOS</span></span>
    * <span data-ttu-id="719b4-128">Un equipo macOS que tenga instalada la versión más reciente de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="719b4-128">A macOS computer with the the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
    * <span data-ttu-id="719b4-129">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS</span><span class="sxs-lookup"><span data-stu-id="719b4-129">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
    * <span data-ttu-id="719b4-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de iOS agregado</span><span class="sxs-lookup"><span data-stu-id="719b4-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the iOS Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="719b4-131">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="719b4-131">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="719b4-132">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="719b4-132">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="719b4-133">Creación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="719b4-133">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="719b4-134">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="719b4-134">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="719b4-135">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mrlearning-base-ch1.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="719b4-135">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="719b4-136">[Crear un proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="719b4-136">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. <span data-ttu-id="719b4-137">[Configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="719b4-137">[Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)</span></span>

3. [<span data-ttu-id="719b4-138">Importar recursos de TextMesh Pro Essential</span><span class="sxs-lookup"><span data-stu-id="719b4-138">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="719b4-139">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="719b4-139">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="719b4-140">Configurar el proyecto de Unity para Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="719b4-140">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="719b4-141">[Agregar Mixed Reality Toolkit a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y asignar un nombre adecuado a la escena; por ejemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="719b4-141">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="719b4-142">A continuación, sigue las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (modificación de la opción de visualización reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="719b4-142">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="719b4-143">Como se mencionó en las instrucciones vinculadas más arriba, [Configuración del proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), es altamente recomendable no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="719b4-143">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="719b4-144">Adición de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="719b4-144">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="719b4-145">En esta sección, instalarás el paquete integrado de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que importarás en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="719b4-145">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="719b4-146">En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):</span><span class="sxs-lookup"><span data-stu-id="719b4-146">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="719b4-148">Puede que el paquete de AR Foundation tarde unos segundos en aparecer en la lista.</span><span class="sxs-lookup"><span data-stu-id="719b4-148">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="719b4-149">En la ventana Package Manager (Administrador de paquetes), selecciona **AR Foundation** e instala el paquete haciendo clic en el botón **Instalar**:</span><span class="sxs-lookup"><span data-stu-id="719b4-149">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="719b4-151">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="719b4-151">Importing the tutorial assets</span></span>

<span data-ttu-id="719b4-152">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="719b4-152">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="719b4-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="719b4-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="719b4-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="719b4-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="719b4-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="719b4-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="719b4-156">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="719b4-156">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="719b4-157">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="719b4-157">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="719b4-159">Creación y preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="719b4-159">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="719b4-160">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="719b4-160">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="719b4-161">Desde la ventana Proyecto, desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs** (Objetos prefabricados).</span><span class="sxs-lookup"><span data-stu-id="719b4-161">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="719b4-162">Mientras mantienes presionado el botón CTRL, haz clic en **ButtonParent**, **DebugWindow**, **Instructions** y **ParentAnchor** para seleccionar los cuatro objetos prefabricados:</span><span class="sxs-lookup"><span data-stu-id="719b4-162">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="719b4-164">Con los cuatro objetos prefabricados aún seleccionados, arrástralos a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="719b4-164">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="719b4-166">Para centrarte en los objetos de la escena, puedes hacer doble clic en el objeto ParentAnchor y, a continuación, volver a alejarte ligeramente:</span><span class="sxs-lookup"><span data-stu-id="719b4-166">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="719b4-168">Si te molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puedes ocultarlos. Para hacerlo, desactiva los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>.</span><span class="sxs-lookup"><span data-stu-id="719b4-168">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="719b4-169">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="719b4-169">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="719b4-170">En esta sección, agregarás scripts a la escena para crear una serie de eventos de botón que muestran los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="719b4-170">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="719b4-171">1. Configurar el componente Pressable Button Holo Lens 2 (Script) (Botón presionable de HoloLens 2 [script])</span><span class="sxs-lookup"><span data-stu-id="719b4-171">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="719b4-172">En la ventana Hierarchy (Jerarquía), expande el objeto **ButtonParent** y selecciona el primer objeto secundario denominado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="719b4-172">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="719b4-174">En la ventana Inspector, busca el componente **Pressable Button Holo Lens 2 (Script)** (Botón presionable de HoloLens 2 [script]) y agrega un nuevo cliente de escucha de eventos al evento **Button Pressed ()** (Botón presionado []). Para hacerlo, haz clic en el icono **+** :</span><span class="sxs-lookup"><span data-stu-id="719b4-174">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="719b4-176">Con el objeto StartAzureSession aún seleccionado en la ventana Hierarchy (Jerarquía), haz clic en el objeto **ParentAnchor** y arrástralo desde la ventana Hierarchy (Jerarquía) al campo **None (Object)** (Ninguno [objeto]) del cliente de escucha de eventos que acabas de agregar para que el objeto ParentAnchor escuche los eventos de botón presionado de este botón:</span><span class="sxs-lookup"><span data-stu-id="719b4-176">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="719b4-178">Haz clic en la lista desplegable **No Function** (Ninguna función) del mismo cliente de escucha de eventos y, a continuación, selecciona **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el evento de botón presionado desde este botón:</span><span class="sxs-lookup"><span data-stu-id="719b4-178">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="719b4-180">2. Configurar el componente Interactable (Script) (Interactuable [script])</span><span class="sxs-lookup"><span data-stu-id="719b4-180">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="719b4-181">Con el objeto StartAzureSession todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, busca el componente **Interactable (Script)** (Interactuable [script]) y repite el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="719b4-181">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="719b4-183">3. Configurar los botones restantes</span><span class="sxs-lookup"><span data-stu-id="719b4-183">3. Configure the remaining buttons</span></span>

<span data-ttu-id="719b4-184">Para cada uno de los botones restantes, completa el proceso descrito en los pasos 1 y 2 anteriores para asignar funciones a los eventos **Button Pressed ()** (Botón presionado []) y **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="719b4-184">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="719b4-185">Para el objeto **StopAzureSession**, asigna la funciónAnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="719b4-185">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="719b4-186">Para el objeto **CreateAzureAnchor**, asigna la función AnchorModuleScript > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="719b4-186">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="719b4-187">A continuación, vuelve a arrastrar **ParentAnchor** al campo **None (Game Object)** (Ninguno [Objeto del juego]).</span><span class="sxs-lookup"><span data-stu-id="719b4-187">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="719b4-188">Para el objeto **RemoveLocalAnchor**, asigna la función AnchorModuleScript > **RemoveLocalAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="719b4-188">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="719b4-189">A continuación, vuelve a arrastrar **ParentAnchor** al campo **None (Game Object)** (Ninguno [Objeto del juego]) vacío.</span><span class="sxs-lookup"><span data-stu-id="719b4-189">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="719b4-190">Para el objeto **FindAzureAnchor**, asigna la función AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="719b4-190">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="719b4-191">Para el objeto **DeleteAzureAnchor**, asigna la función AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="719b4-191">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="719b4-192">4. Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="719b4-192">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="719b4-193">En la ventana Hierarchy (Jerarquía), selecciona el objeto **ParentAnchor** y, en la ventana Inspector, desplázate hacia abajo hasta el componente **Spatial Anchor Manager (Script)** (Administrador del anclaje espacial [script]).</span><span class="sxs-lookup"><span data-stu-id="719b4-193">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="719b4-194">A continuación, en la sección **Credentials** (Credenciales), pega el identificador y la clave de la cuenta de Spatial Anchors, que creaste como parte de los [Requisitos previos](mrlearning-asa-ch1.md#prerequisites) de este tutorial, en los campos **Spatial Anchors Account Id** (Id. de cuenta de Spatial Anchors) y **Spatial Anchors Account Key** (Clave de cuenta de Spatial Anchors):</span><span class="sxs-lookup"><span data-stu-id="719b4-194">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="719b4-196">Prueba de los comportamientos básicos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="719b4-196">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="719b4-197">Ahora que la escena está configurada para mostrar los aspectos básicos de Azure Spatial Anchors, es el momento de implementar la aplicación para que puedas experimentar Azure Spatial Anchors de primera mano.</span><span class="sxs-lookup"><span data-stu-id="719b4-197">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="719b4-198">1. Agregar las funcionalidades adicionales necesarias</span><span class="sxs-lookup"><span data-stu-id="719b4-198">1. Add additional required capabilities</span></span>

<span data-ttu-id="719b4-199">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador):</span><span class="sxs-lookup"><span data-stu-id="719b4-199">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="719b4-201">En la ventana Player Settings (Configuración del jugador), selecciona **Player** (Jugador) y, a continuación, **Publishing Settings** (Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="719b4-201">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="719b4-203">En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén activadas.</span><span class="sxs-lookup"><span data-stu-id="719b4-203">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="719b4-204">A continuación, habilita las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** y **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="719b4-204">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="719b4-206">2. Implementar la aplicación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="719b4-206">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="719b4-207">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad Azure Spatial Anchors, debes implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="719b4-207">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="719b4-208">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puedes consultar las instrucciones de [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="719b4-208">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="719b4-209">3. Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="719b4-209">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="719b4-210">Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debes asegurarte de que el dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="719b4-210">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="719b4-211">Cuando la aplicación se ejecute en el dispositivo, sigue las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="719b4-211">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="719b4-213">Anclaje de una experiencia</span><span class="sxs-lookup"><span data-stu-id="719b4-213">Anchoring an experience</span></span>

<span data-ttu-id="719b4-214">En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="719b4-214">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="719b4-215">Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto.</span><span class="sxs-lookup"><span data-stu-id="719b4-215">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="719b4-216">En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="719b4-216">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="719b4-217">1. Incorporación de la experiencia del lanzacohetes</span><span class="sxs-lookup"><span data-stu-id="719b4-217">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="719b4-218">En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > Objetos prefabricados > RocketLauncher) y selecciona el objeto prefabricado **RocketLauncher_Complete**:</span><span class="sxs-lookup"><span data-stu-id="719b4-218">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="719b4-220">Con el objeto prefabricado RocketLauncher_Complete todavía seleccionado, arrástralo sobre el objeto **ParentAnchor** en la ventana Hierarchy (Jerarquía) para convertirlo en un elemento secundario del objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="719b4-220">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="719b4-222">2. Cambio de posición de la experiencia del lanzacohetes</span><span class="sxs-lookup"><span data-stu-id="719b4-222">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="719b4-223">Coloca, gira y escala el objeto **RocketLauncher_Complete** a una escala y orientación adecuadas, al mismo tiempo que se garantiza que el objeto **ParentAnchor** sigue expuesto; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="719b4-223">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="719b4-224">Transforma el valor de **Position** (Posición) X = 0, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="719b4-224">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="719b4-225">Transforma el valor de **Rotation** (Rotación) X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="719b4-225">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="719b4-226">Transforma el valor de **Scale** (Escala) X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="719b4-226">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="719b4-228">Ahora, en la aplicación, los usuarios pueden mover el cubo para cambiar la posición de la experiencia del lanzacohetes por completo.</span><span class="sxs-lookup"><span data-stu-id="719b4-228">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="719b4-229">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el cuadro de límite que rodea la experiencia, el uso de gizmos de posición y rotación, etc.</span><span class="sxs-lookup"><span data-stu-id="719b4-229">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="719b4-230">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="719b4-230">Congratulations</span></span>

<span data-ttu-id="719b4-231">En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="719b4-231">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="719b4-232">El tutorial te ha proporcionado varios botones que te permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors y crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="719b4-232">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="719b4-233">En la siguiente lección, aprenderás a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="719b4-233">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="719b4-234">Siguiente lección: 2. Guardado, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="719b4-234">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
