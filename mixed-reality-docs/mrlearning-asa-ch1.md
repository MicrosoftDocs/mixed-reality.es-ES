---
title: 'Tutoriales de anclaje espacial de Azure: 1. Introducción a los delimitadores espaciales de Azure'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74941143"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="956c3-105">1. Introducción a los anclajes espaciales de Azure</span><span class="sxs-lookup"><span data-stu-id="956c3-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="956c3-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="956c3-106">Overview</span></span>

<span data-ttu-id="956c3-107">Esta es la segunda serie de los tutoriales de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="956c3-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="956c3-108">En esta serie de tutoriales de tres partes, conocerá los aspectos básicos de los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="956c3-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="956c3-109">En este primer tutorial, [Introducción a los anclajes espaciales de Azure](mrlearning-asa-ch1.md), explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar los delimitadores de Azure en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="956c3-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="956c3-110">En el segundo tutorial, [guardado, recuperación y uso compartido de los anclajes espaciales de Azure](mrlearning-asa-ch2.md), aprenderá a guardar los anclajes espaciales de Azure en varias sesiones de la aplicación guardando la información del delimitador en el almacenamiento de HoloLens 2 y compartiendo esta información de delimitador en otros dispositivos para una alineación de delimitador de varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="956c3-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="956c3-111">En el tercer tutorial, en el que se [muestran los comentarios del delimitador espacial de Azure](mrlearning-asa-ch3.md), aprenderá a proporcionar a los usuarios comentarios sobre los eventos y Estados de delimitador al usar delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="956c3-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="956c3-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="956c3-112">Objectives</span></span>

* <span data-ttu-id="956c3-113">Conozca los aspectos básicos del desarrollo con los anclajes espaciales de Azure para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="956c3-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="956c3-114">Crear, cargar y descargar anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="956c3-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="956c3-115">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="956c3-115">Prerequisites</span></span>

* <span data-ttu-id="956c3-116">Cumpla los requisitos enumerados en la sección de [requisitos previos](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) del tutorial de [Inicio rápido: creación de una aplicación de HoloLens de Unity que usa delimitadores espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="956c3-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="956c3-117">Complete la sección [creación de un recurso de anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) de la guía de [Inicio rápido: creación de una aplicación de HoloLens en Unity que usa anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="956c3-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="956c3-118">Si aún no ha completado la serie de [tutoriales de introducción](mrlearning-base.md) , se recomienda que complete los tutoriales en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="956c3-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="956c3-119">Crear el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="956c3-119">Creating the Unity project</span></span>

<span data-ttu-id="956c3-120">En esta sección, creará un nuevo proyecto de Unity y lo configurará para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="956c3-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="956c3-121">Cree un proyecto de Unity y asígnele un nombre adecuado, por ejemplo, el _tutorial de anclajes espaciales de Azure_.</span><span class="sxs-lookup"><span data-stu-id="956c3-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="956c3-122">Configure el proyecto de Unity para Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="956c3-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="956c3-123">Para obtener un recordatorio sobre cómo crear un proyecto de Unity y configurarlo para Windows Mixed Reality, puede consultar las secciones creación de un [nuevo proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y [configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) del tutorial [inicialización del proyecto y de la primera aplicación](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , que forma parte de la serie de [tutoriales de introducción](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="956c3-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="956c3-124">Agregar paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="956c3-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="956c3-125">En esta sección, agregará recursos y paquetes de Unity integrados que necesitarán los kits de herramientas y los SDK que utilizará en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="956c3-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="956c3-126">Importe los recursos de TMP Essential.</span><span class="sxs-lookup"><span data-stu-id="956c3-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="956c3-127">Estamos agregando este paquete porque lo requiere el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="956c3-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="956c3-128">En el menú de Unity, seleccione **Window** > **TEXTMESHPRO** > **Import tmp Essential Resources**.</span><span class="sxs-lookup"><span data-stu-id="956c3-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="956c3-130">En la ventana emergente importar paquete Unity, primero asegúrese de que se seleccionan todos los recursos haciendo clic en el botón **todos** y, a continuación, importe los recursos haciendo clic en el botón **importar** .</span><span class="sxs-lookup"><span data-stu-id="956c3-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="956c3-132">Instale AR Foundation.</span><span class="sxs-lookup"><span data-stu-id="956c3-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="956c3-133">Estamos agregando este paquete porque lo requiere el SDK de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="956c3-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="956c3-134">En el menú de Unity, seleccione **ventana** > **Administrador de paquetes**.</span><span class="sxs-lookup"><span data-stu-id="956c3-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="956c3-136">En la ventana del administrador de paquetes, seleccione **ar Foundation** e instale el paquete haciendo clic en el botón **instalar** .</span><span class="sxs-lookup"><span data-stu-id="956c3-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="956c3-137">Puede que tarde unos segundos en aparecer en la lista.</span><span class="sxs-lookup"><span data-stu-id="956c3-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="956c3-139">Importar los activos del tutorial</span><span class="sxs-lookup"><span data-stu-id="956c3-139">Importing the tutorial assets</span></span>

<span data-ttu-id="956c3-140">En esta sección, descargará e importará todos los recursos del tutorial.</span><span class="sxs-lookup"><span data-stu-id="956c3-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="956c3-141">Descargue los recursos.</span><span class="sxs-lookup"><span data-stu-id="956c3-141">Download the assets.</span></span>

    * <span data-ttu-id="956c3-142">[AzureSpatialAnchors. unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (versión 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="956c3-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="956c3-143">Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="956c3-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="956c3-144">MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.1.0.1. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="956c3-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="956c3-145">MRTK. HoloLens2. Unity. tutoriales. assets. AzureSpatialAnchors. 2.1.0.1. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="956c3-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="956c3-146">Importe los recursos.</span><span class="sxs-lookup"><span data-stu-id="956c3-146">Import the assets.</span></span>

    <span data-ttu-id="956c3-147">En el menú de Unity, seleccione **recursos** > **importar paquete** > **paquete personalizado.** ...</span><span class="sxs-lookup"><span data-stu-id="956c3-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="956c3-149">En el paquete de importación... en la ventana emergente, seleccione **AzureSpatialAnchors. unitypackage Tools** y haga clic en el botón **abrir** .</span><span class="sxs-lookup"><span data-stu-id="956c3-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="956c3-151">En la ventana emergente importar paquete Unity, primero asegúrese de que se seleccionan todos los recursos haciendo clic en el botón **todos** y, a continuación, importe los recursos haciendo clic en el botón **importar** .</span><span class="sxs-lookup"><span data-stu-id="956c3-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="956c3-153">Repita estos pasos para importar los paquetes de recursos restantes.</span><span class="sxs-lookup"><span data-stu-id="956c3-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="956c3-154">Una vez que haya finalizado, la carpeta **assets** del proyecto de Unity debe contener estas subcarpetas.</span><span class="sxs-lookup"><span data-stu-id="956c3-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="956c3-156">Creación y preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="956c3-156">Creating and preparing the scene</span></span>

<span data-ttu-id="956c3-157">En esta sección, creará y preparará la escena agregando el kit de herramientas de realidad mixta y algunos de los tutoriales Prefabs.</span><span class="sxs-lookup"><span data-stu-id="956c3-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="956c3-158">Cree una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="956c3-158">Create a new scene.</span></span>

    <span data-ttu-id="956c3-159">En el menú de Unity, seleccione **archivo** > **nueva escena**.</span><span class="sxs-lookup"><span data-stu-id="956c3-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="956c3-161">En el menú de Unity, seleccione **archivo** > **Guardar como..** ..</span><span class="sxs-lookup"><span data-stu-id="956c3-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="956c3-163">En la ventana emergente guardar escena, vaya a la carpeta **escenas** del proyecto, asigne un nombre adecuado a la escena, por ejemplo, _ASATutorialScene_, y guarde la escena haciendo clic en el botón **Guardar** .</span><span class="sxs-lookup"><span data-stu-id="956c3-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="956c3-165">Puede guardar la escena en cualquier lugar que desee, siempre y cuando se encuentre dentro de la carpeta activos del proyecto.</span><span class="sxs-lookup"><span data-stu-id="956c3-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="956c3-166">Sin embargo, para mantener el proyecto organizado, normalmente se recomienda guardarlo en la carpeta Scenes del proyecto.</span><span class="sxs-lookup"><span data-stu-id="956c3-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="956c3-167">Agregue el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="956c3-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="956c3-168">En el menú de Unity, seleccione el **Kit de herramientas de realidad mixta** > **Agregar a la escena y configurar..** ..</span><span class="sxs-lookup"><span data-stu-id="956c3-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="956c3-170">En la ventana emergente seleccionar MixedRealityToolkitConfigurationProfile, haga clic en **DefaultHoloLens2ConfigurationProfile** para establecerlo como el perfil de configuración MRTK de la escena.</span><span class="sxs-lookup"><span data-stu-id="956c3-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="956c3-172">En el menú de Unity, seleccione **archivo** > **Guardar** para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="956c3-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="956c3-174">Puede usar el método abreviado de teclado CTRL + S (comando + S en macOS) para guardar rápidamente la escena mientras está trabajando en este tutorial.</span><span class="sxs-lookup"><span data-stu-id="956c3-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="956c3-175">Agregue el tutorial Prefabs.</span><span class="sxs-lookup"><span data-stu-id="956c3-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="956c3-176">En el panel Proyecto, vaya a **activos** > **MRTK. Tutoriales. AzureSpatialAnchors** > carpeta **Prefabs**</span><span class="sxs-lookup"><span data-stu-id="956c3-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="956c3-177">Mientras mantiene presionado el botón CTRL (comando en macOS), haga clic en **ButtonParent**, **DebugWindow**y **ParentAnchor** para seleccionar los tres Prefabs.</span><span class="sxs-lookup"><span data-stu-id="956c3-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="956c3-179">Con los tres Prefabs todavía seleccionados, arrástrelos al panel jerarquía para agregarlos a la escena.</span><span class="sxs-lookup"><span data-stu-id="956c3-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="956c3-181">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto ParentAnchor y, a continuación, hacer zoom ligeramente hacia afuera.</span><span class="sxs-lookup"><span data-stu-id="956c3-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="956c3-183">Si encuentra iconos grandes en la escena, por ejemplo, los iconos ' t ' de gran tamaño que distraen, puede ocultarlos cambiando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">el Gizmos</a> a la posición de apagado.</span><span class="sxs-lookup"><span data-stu-id="956c3-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="956c3-184">Configuración de los botones para que funcione la escena</span><span class="sxs-lookup"><span data-stu-id="956c3-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="956c3-185">En esta sección, agregará Prefabs y scripts a la escena para crear una serie de botones que muestran los aspectos básicos de cómo se comportan los delimitadores locales y los delimitadores espaciales de Azure en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="956c3-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="956c3-186">Configure el componente de botón presionado Hololens Lens 2 (Script).</span><span class="sxs-lookup"><span data-stu-id="956c3-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="956c3-187">En el panel jerarquía, expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**.</span><span class="sxs-lookup"><span data-stu-id="956c3-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="956c3-189">En el panel Inspector, desplácese hacia abajo hasta el componente **Button Hololens Lens 2 (Script)** y agregue un nuevo agente de escucha de eventos al evento **pressed ()** . para ello, haga clic en el icono de **+** .</span><span class="sxs-lookup"><span data-stu-id="956c3-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="956c3-191">Con el objeto StartAzureSession todavía seleccionado en el panel jerarquía, haga clic y arrastre el objeto **ParentAnchor** desde el panel jerarquía al campo **ninguno (objeto)** vacío del agente de escucha de eventos que acaba de agregar para hacer que el objeto ParentAnchor escuche los eventos presionados por el botón de este botón.</span><span class="sxs-lookup"><span data-stu-id="956c3-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="956c3-193">Haga clic en la lista desplegable **no función** del mismo agente de escucha de eventos y, a continuación, seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el botón eventos presionados desde este botón.</span><span class="sxs-lookup"><span data-stu-id="956c3-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="956c3-195">Configure el componente interactuable (Script).</span><span class="sxs-lookup"><span data-stu-id="956c3-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="956c3-196">Con el objeto StartAzureSession todavía seleccionado en el panel de jerarquías, en el panel Inspector, desplácese hacia abajo hasta el componente **interactuable (Script)** y repita el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="956c3-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="956c3-198">Configurar los botones restantes</span><span class="sxs-lookup"><span data-stu-id="956c3-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="956c3-199">Para cada uno de los botones restantes, complete el proceso que se describe en los pasos 1 y 2 anteriores para asignar funciones a los eventos Button pressed () y OnClick () que se indican a continuación:</span><span class="sxs-lookup"><span data-stu-id="956c3-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="956c3-200">Para el objeto **StopAzureSession** , asigne la función **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="956c3-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="956c3-201">Para el objeto **CreateAnchor** , asigne la función **CreateAzureAnchor ()** y, a continuación, arrastre el **ParentAnchor** de nuevo al campo **ninguno (objeto de juego)** vacío.</span><span class="sxs-lookup"><span data-stu-id="956c3-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="956c3-202">Para **empezar a buscar el objeto delimitador** , asigne la función **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="956c3-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="956c3-203">Para eliminar el objeto de **delimitador de Azure** , asigne la función **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="956c3-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="956c3-204">Para el objeto **eliminar el delimitador local** , asigne la función **RemoveLocalAnchor ()** y, a continuación, arrastre el **ParentAnchor** de nuevo al campo **ninguno (objeto de juego)** vacío.</span><span class="sxs-lookup"><span data-stu-id="956c3-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="956c3-205">Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="956c3-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="956c3-206">En el panel jerarquía, seleccione el objeto **ParentAnchor** y, en el panel Inspector, desplácese hacia abajo hasta el componente **Administrador de delimitadores espaciales (Script)** .</span><span class="sxs-lookup"><span data-stu-id="956c3-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="956c3-207">Después, en la sección **credenciales** , pegue el identificador y la clave de la cuenta de anclaje espacial en los campos ID. de cuenta de anclaje **espacial** y **anclaje espacial** correspondientes.</span><span class="sxs-lookup"><span data-stu-id="956c3-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="956c3-208">Ha creado el identificador de cuenta y la clave de los delimitadores espaciales como parte de los [requisitos previos](mrlearning-asa-ch1.md#prerequisites)de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="956c3-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="956c3-210">Asegúrese de guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="956c3-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="956c3-211">Prueba de los comportamientos básicos de los anclajes espaciales de Azure</span><span class="sxs-lookup"><span data-stu-id="956c3-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="956c3-212">Ahora que la escena está configurada para mostrar los aspectos básicos de los anclajes espaciales de Azure, es el momento de implementar la aplicación para que pueda experimentar los anclajes espaciales de Azure de primera mano.</span><span class="sxs-lookup"><span data-stu-id="956c3-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="956c3-213">Agregue capacidades adicionales necesarias.</span><span class="sxs-lookup"><span data-stu-id="956c3-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="956c3-214">En el menú de Unity, seleccione **editar** > **configuración del proyecto...** para abrir el panel de configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="956c3-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="956c3-216">En el panel de configuración del reproductor, seleccione **reproductor** y, a continuación, **configuración de publicación**.</span><span class="sxs-lookup"><span data-stu-id="956c3-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="956c3-218">En la **configuración de publicación**, desplácese hacia abajo hasta la sección **capacidades** y compruebe que **SpatialPerception**, que habilitó al crear el proyecto al principio del tutorial, está habilitado.</span><span class="sxs-lookup"><span data-stu-id="956c3-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="956c3-219">A continuación, habilitó las capacidades **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **cámara web**y **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="956c3-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="956c3-221">Implemente la aplicación en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="956c3-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="956c3-222">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las secciones [compilar la aplicación en el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) del tutorial [inicialización del proyecto y la primera aplicación](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , que forma parte de la serie de [tutoriales de introducción](mrlearning-base.md) .</span><span class="sxs-lookup"><span data-stu-id="956c3-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="956c3-223">Ejecute la aplicación y siga las instrucciones de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="956c3-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="956c3-224">Los delimitadores espaciales de Azure usan Internet para guardar y cargar los datos de delimitador, por lo que debe asegurarse de que el dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="956c3-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="956c3-225">Cuando la aplicación se ejecuta en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de **instrucciones del módulo de delimitador espacial de Azure** .</span><span class="sxs-lookup"><span data-stu-id="956c3-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="956c3-227">Delimitar una experiencia</span><span class="sxs-lookup"><span data-stu-id="956c3-227">Anchoring an experience</span></span>

<span data-ttu-id="956c3-228">En las secciones anteriores, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="956c3-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="956c3-229">Usamos un cubo para representar y visualizar el objeto de juego primario con el delimitador adjunto.</span><span class="sxs-lookup"><span data-stu-id="956c3-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="956c3-230">En esta sección, aprenderá a anclar una experiencia completa colocándolo como un elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="956c3-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="956c3-231">Agregue la experiencia del selector de Rocket.</span><span class="sxs-lookup"><span data-stu-id="956c3-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="956c3-232">En el panel Proyecto, vaya a **activos** > **MRTK. Tutoriales. GettingStarted** > carpeta **Prefabs** y seleccione **Rocket Launcher_Complete** recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="956c3-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="956c3-234">Con el Rocket Launcher_Complete recurso prefabricado todavía seleccionado, arrástrelo sobre el objeto **ParentAnchor** en el panel jerarquía para convertirlo en un elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="956c3-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="956c3-236">Cambie la posición de la experiencia del selector de Rocket.</span><span class="sxs-lookup"><span data-stu-id="956c3-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="956c3-237">Mueva el módulo **Rocket Launcher_Complete** objeto para que el **ParentAnchor** (el cubo) siga expuesto.</span><span class="sxs-lookup"><span data-stu-id="956c3-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning-asa](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="956c3-239">En la aplicación, los usuarios ahora pueden volver a colocar toda la experiencia del selector de Rocket moviendo el cubo.</span><span class="sxs-lookup"><span data-stu-id="956c3-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="956c3-240">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (por ejemplo, el cubo que se usa en este tutorial), el uso de un botón para alternar un rectángulo de selección que rodea la experiencia, el uso de la posición y la rotación. Gizmos y mucho más.</span><span class="sxs-lookup"><span data-stu-id="956c3-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="956c3-241">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="956c3-241">Congratulations</span></span>

<span data-ttu-id="956c3-242">En este tutorial, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="956c3-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="956c3-243">En esta lección se proporcionan varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar delimitadores de Azure en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="956c3-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="956c3-244">En la siguiente lección, aprenderá a guardar los identificadores de delimitador de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, y cómo transferir los identificadores de delimitador entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="956c3-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="956c3-245">Lección siguiente: 2. guardar, recuperar y compartir anclajes espaciales de Azure</span><span class="sxs-lookup"><span data-stu-id="956c3-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
