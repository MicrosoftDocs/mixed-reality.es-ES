---
title: 'Tutoriales de anclaje espacial de Azure: 1. Introducción a los delimitadores espaciales de Azure'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 21883e95e92f8808bcf270e6d8091f31933ab6fa
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250870"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="bb90e-105">1. Introducción a los anclajes espaciales de Azure</span><span class="sxs-lookup"><span data-stu-id="bb90e-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="bb90e-106">Información general</span><span class="sxs-lookup"><span data-stu-id="bb90e-106">Overview</span></span>

<span data-ttu-id="bb90e-107">Esta es la segunda serie de los tutoriales de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bb90e-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="bb90e-108">En esta serie de tutoriales de tres partes, conocerá los aspectos básicos de los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="bb90e-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="bb90e-109">En este primer tutorial, [Introducción a los anclajes espaciales de Azure](mrlearning-asa-ch1.md), explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure y crear, cargar y descargar los delimitadores de Azure en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bb90e-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="bb90e-110">En el segundo tutorial, [guardado, recuperación y uso compartido de los anclajes espaciales de Azure](mrlearning-asa-ch2.md), aprenderá a guardar los anclajes espaciales de Azure en varias sesiones de la aplicación guardando la información del delimitador en el almacenamiento de HoloLens 2 y compartiendo esta información de delimitador en otros dispositivos para una alineación de delimitador de varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="bb90e-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="bb90e-111">En el tercer tutorial, en el que se [muestran los comentarios del delimitador espacial de Azure](mrlearning-asa-ch3.md), aprenderá a proporcionar a los usuarios comentarios sobre los eventos y Estados de delimitador al usar delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="bb90e-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="bb90e-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="bb90e-112">Objectives</span></span>

* <span data-ttu-id="bb90e-113">Conozca los aspectos básicos del desarrollo con los anclajes espaciales de Azure para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bb90e-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="bb90e-114">Crear, cargar y descargar anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="bb90e-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bb90e-115">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="bb90e-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="bb90e-116">Si aún no ha completado la serie de [tutoriales de introducción](mrlearning-base.md) , se recomienda que complete los tutoriales en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="bb90e-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="bb90e-117">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="bb90e-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="bb90e-118">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="bb90e-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="bb90e-119">Cierta capacidad C# de programación básica</span><span class="sxs-lookup"><span data-stu-id="bb90e-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="bb90e-120">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="bb90e-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="bb90e-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2. X instalado y el módulo de compatibilidad de compilación plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="bb90e-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="bb90e-122">Complete la sección [creación de un recurso de anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) de la guía de [Inicio rápido: creación de una aplicación de HoloLens en Unity que usa anclajes espaciales de Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) .</span><span class="sxs-lookup"><span data-stu-id="bb90e-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb90e-123">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2. X.</span><span class="sxs-lookup"><span data-stu-id="bb90e-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="bb90e-124">Esto sustituye a los requisitos de versión de Unity o a las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="bb90e-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="bb90e-125">Crear el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="bb90e-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="bb90e-126">En esta sección, creará un nuevo proyecto de Unity y lo preparará para el desarrollo de MRTK.</span><span class="sxs-lookup"><span data-stu-id="bb90e-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span> <span data-ttu-id="bb90e-127">Para ello, siga [las instrucciones de](mrlearning-base-ch1.md#build-your-application-to-your-device) [inicialización del proyecto y de la primera aplicación](mrlearning-base-ch1.md), sin incluir los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="bb90e-127">For this, please follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="bb90e-128">[Cree un nuevo proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asígnele un nombre adecuado, por ejemplo, *tutoriales de MRTK*.</span><span class="sxs-lookup"><span data-stu-id="bb90e-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="bb90e-129">Configurar el proyecto de Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="bb90e-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="bb90e-130">Importar recursos esenciales de TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="bb90e-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="bb90e-131">Importar el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="bb90e-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="bb90e-132">Configuración del proyecto de Unity para el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="bb90e-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="bb90e-133">[Agregue el kit de herramientas de realidad mixta a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y proporcione a la escena un nombre adecuado, por ejemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="bb90e-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

> [!CAUTION]
> <span data-ttu-id="bb90e-134">Como se mencionó en el [proyecto de configuración del proyecto de Unity para las instrucciones del kit de herramientas de realidad mixta](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) vinculadas anteriormente, es posible que MSBuild para Unity no admita todos los SDK que va a usar y puede ser difícil de deshabilitar una vez que se ha habilitado.</span><span class="sxs-lookup"><span data-stu-id="bb90e-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="bb90e-135">Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="bb90e-135">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="bb90e-136">Agregar paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="bb90e-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="bb90e-137">En esta sección, instalará el paquete de AR Foundation integrado de Unity porque lo requiere el SDK de anclaje espacial de Azure que se importará en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="bb90e-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="bb90e-138">En el menú de Unity, seleccione **ventana** > **Administrador de paquetes**:</span><span class="sxs-lookup"><span data-stu-id="bb90e-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="bb90e-140">Puede que tarde unos segundos en aparecer en la lista.</span><span class="sxs-lookup"><span data-stu-id="bb90e-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="bb90e-141">En la ventana del administrador de paquetes, seleccione **ar Foundation** e instale el paquete haciendo clic en el botón **instalar** :</span><span class="sxs-lookup"><span data-stu-id="bb90e-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="bb90e-143">Importar los activos del tutorial</span><span class="sxs-lookup"><span data-stu-id="bb90e-143">Importing the tutorial assets</span></span>

<span data-ttu-id="bb90e-144">Descargue e **importe** los siguientes paquetes personalizados **de Unity en el orden en que**aparecen:</span><span class="sxs-lookup"><span data-stu-id="bb90e-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="bb90e-145">[AzureSpatialAnchors. unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="bb90e-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="bb90e-146">MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.2.0.1. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="bb90e-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.1.unitypackage)
* [<span data-ttu-id="bb90e-147">MRTK. HoloLens2. Unity. tutoriales. assets. AzureSpatialAnchors. 2.2.0.0. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="bb90e-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.2.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="bb90e-148">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, puede consultar las instrucciones para [importar el kit de herramientas de realidad mixta](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="bb90e-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="bb90e-149">Después de haber importado los recursos del tutorial, la ventana del proyecto debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="bb90e-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="bb90e-151">Creación y preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="bb90e-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="bb90e-152">En esta sección, va a preparar la escena agregando algunos de los tutoriales de Prefabs.</span><span class="sxs-lookup"><span data-stu-id="bb90e-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="bb90e-153">En la ventana del proyecto, vaya a **activos** > **MRTK. Tutoriales. AzureSpatialAnchors** > carpeta **Prefabs**</span><span class="sxs-lookup"><span data-stu-id="bb90e-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="bb90e-154">Mientras mantiene presionado el botón CTRL, haga clic en **ButtonParent**, **DebugWindow**, **instrucciones**y **ParentAnchor** para seleccionar los cuatro Prefabs:</span><span class="sxs-lookup"><span data-stu-id="bb90e-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="bb90e-156">Con las cuatro Prefabs todavía seleccionadas, arrástrelas a la ventana de jerarquía para agregarlas a la escena:</span><span class="sxs-lookup"><span data-stu-id="bb90e-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="bb90e-158">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto ParentAnchor y, a continuación, hacer zoom ligeramente hacia afuera:</span><span class="sxs-lookup"><span data-stu-id="bb90e-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="bb90e-160">Si encuentra iconos grandes en la escena, por ejemplo, los iconos ' t ' de gran tamaño que distraen, puede ocultarlos cambiando <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">el Gizmos</a> a la posición de apagado.</span><span class="sxs-lookup"><span data-stu-id="bb90e-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="bb90e-161">Configuración de los botones para que funcione la escena</span><span class="sxs-lookup"><span data-stu-id="bb90e-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="bb90e-162">En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestran los aspectos básicos de cómo se comportan los delimitadores locales y los delimitadores espaciales de Azure en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb90e-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="bb90e-163">1. configurar el componente de botón presionado Hololens Lens 2 (Script)</span><span class="sxs-lookup"><span data-stu-id="bb90e-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="bb90e-164">En la ventana jerarquía, expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="bb90e-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="bb90e-166">En la ventana del inspector, busque el componente del botón que se ha **presionado Hololens Lens 2 (Script)** y agregue un nuevo agente de escucha de eventos al evento **pressed ()** . para ello, haga clic en el icono de **+** :</span><span class="sxs-lookup"><span data-stu-id="bb90e-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="bb90e-168">Con el objeto StartAzureSession todavía seleccionado en la ventana de jerarquía, haga clic en el objeto **ParentAnchor** de la ventana de la jerarquía y arrástrelo hasta el campo no vacío **(objeto)** del agente de escucha de eventos que acaba de agregar para hacer que el objeto ParentAnchor escuche los eventos presionados por el botón de este botón:</span><span class="sxs-lookup"><span data-stu-id="bb90e-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="bb90e-170">Haga clic en la lista desplegable **no función** del mismo agente de escucha de eventos y, a continuación, seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer la función StartAzureSession () como la acción que se desencadena cuando se activa el botón eventos presionados desde este botón:</span><span class="sxs-lookup"><span data-stu-id="bb90e-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="bb90e-172">2. configurar el componente interactuable (Script)</span><span class="sxs-lookup"><span data-stu-id="bb90e-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="bb90e-173">Con el objeto StartAzureSession todavía seleccionado en la ventana de la jerarquía, en la ventana del inspector, busque el componente **interactuable (Script)** y repita el mismo proceso que en el paso 1 anterior para el evento **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="bb90e-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="bb90e-175">3. configurar los botones restantes</span><span class="sxs-lookup"><span data-stu-id="bb90e-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="bb90e-176">Para cada uno de los botones restantes, complete el proceso que se describe en los pasos 1 y 2 anteriores para asignar funciones a los eventos **Button pressed ()** y **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="bb90e-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="bb90e-177">Para el objeto **StopAzureSession** , asigne la función AnchorModuleScript > **StopAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="bb90e-178">Para el objeto **CreateAzureAnchor** , asigne la función AnchorModuleScript > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="bb90e-179">a continuación, arrastre **ParentAnchor** de nuevo al campo vacío **ninguno (objeto de juego)** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="bb90e-180">Para el objeto **RemoveLocalAnchor** , asigne la función AnchorModuleScript > **RemoveLocalAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="bb90e-181">a continuación, arrastre **ParentAnchor** de nuevo al campo vacío **ninguno (objeto de juego)** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="bb90e-182">Para el objeto **FindAzureAnchor** , asigne la función AnchorModuleScript > **FindAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="bb90e-183">Para el objeto **DeleteAzureAnchor** , asigne la función AnchorModuleScript > **DeleteAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="bb90e-184">4. conectar la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="bb90e-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="bb90e-185">En la ventana jerarquía, seleccione el objeto **ParentAnchor** y, en la ventana del inspector, desplácese hacia abajo hasta el componente **Administrador de delimitadores espaciales (Script)** .</span><span class="sxs-lookup"><span data-stu-id="bb90e-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="bb90e-186">A continuación, en la sección **credenciales** , pegue el identificador y la clave de la cuenta de anclaje espacial que creó como parte de los [requisitos previos](mrlearning-asa-ch1.md#prerequisites)de este tutorial, en los campos de clave de cuenta de los **delimitadores** espaciales y los **delimitadores espaciales** correspondientes:</span><span class="sxs-lookup"><span data-stu-id="bb90e-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="bb90e-188">Prueba de los comportamientos básicos de los anclajes espaciales de Azure</span><span class="sxs-lookup"><span data-stu-id="bb90e-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="bb90e-189">Ahora que la escena está configurada para mostrar los aspectos básicos de los anclajes espaciales de Azure, es el momento de implementar la aplicación para que pueda experimentar los anclajes espaciales de Azure de primera mano.</span><span class="sxs-lookup"><span data-stu-id="bb90e-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="bb90e-190">1. agregar funcionalidades adicionales necesarias</span><span class="sxs-lookup"><span data-stu-id="bb90e-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="bb90e-191">En el menú de Unity, seleccione **editar** > **configuración del proyecto...** para abrir la ventana Configuración del reproductor:</span><span class="sxs-lookup"><span data-stu-id="bb90e-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="bb90e-193">En la ventana Configuración del reproductor, seleccione **reproductor** y, a continuación, **configuración de publicación**:</span><span class="sxs-lookup"><span data-stu-id="bb90e-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="bb90e-195">En la **configuración de publicación**, desplácese hacia abajo hasta la sección **capacidades** y compruebe que las capacidades **InternetClient**, **Microphone**y **SpatialPerception** , que ha habilitado al crear el proyecto al principio del tutorial, están habilitadas.</span><span class="sxs-lookup"><span data-stu-id="bb90e-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="bb90e-196">A continuación, habilita las funcionalidades de **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**y **Webcam** :</span><span class="sxs-lookup"><span data-stu-id="bb90e-196">Then, enabled the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="bb90e-198">2. implementación de la aplicación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="bb90e-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="bb90e-199">Los anclajes espaciales de Azure no se pueden ejecutar en Unity, por lo que para probar la funcionalidad de los anclajes espaciales de Azure, debe implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bb90e-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="bb90e-200">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones [compilar la aplicación en el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device) .</span><span class="sxs-lookup"><span data-stu-id="bb90e-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="bb90e-201">3. Ejecute la aplicación en HoloLens 2 y siga las instrucciones de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="bb90e-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="bb90e-202">Los delimitadores espaciales de Azure usan Internet para guardar y cargar los datos de delimitador, por lo que debe asegurarse de que el dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="bb90e-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="bb90e-203">Cuando la aplicación se ejecuta en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de delimitador espacial de Azure:</span><span class="sxs-lookup"><span data-stu-id="bb90e-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="bb90e-205">Delimitar una experiencia</span><span class="sxs-lookup"><span data-stu-id="bb90e-205">Anchoring an experience</span></span>

<span data-ttu-id="bb90e-206">En las secciones anteriores, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="bb90e-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="bb90e-207">Usamos un cubo para representar y visualizar el objeto de juego primario con el delimitador adjunto.</span><span class="sxs-lookup"><span data-stu-id="bb90e-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="bb90e-208">En esta sección, aprenderá a anclar una experiencia completa colocándolo como un elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="bb90e-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="bb90e-209">1. agregar la experiencia del selector de Rocket</span><span class="sxs-lookup"><span data-stu-id="bb90e-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="bb90e-210">En la ventana de proyecto, navegue a los **recursos** > **MRTK. Tutoriales. GettingStarted** > **Prefabs** > carpeta **RocketLauncher** y seleccione el **RocketLauncher_Complete** recurso prefabricado:</span><span class="sxs-lookup"><span data-stu-id="bb90e-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="bb90e-212">Con el RocketLauncher_Complete recurso prefabricado todavía seleccionado, arrástrelo sobre el objeto **ParentAnchor** de la ventana jerarquía para convertirlo en un elemento secundario del objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="bb90e-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="bb90e-214">2. cambiar la posición de la experiencia del selector de Rocket</span><span class="sxs-lookup"><span data-stu-id="bb90e-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="bb90e-215">Coloque, gire y escale el objeto de **RocketLauncher_Complete** a una escala y orientación adecuadas, y asegúrese también de que el objeto **ParentAnchor** todavía está expuesto, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bb90e-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="bb90e-216">**Posición** de transformación X = 1, Y = 0, Z = 3,75</span><span class="sxs-lookup"><span data-stu-id="bb90e-216">Transform **Position** X = 1, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="bb90e-217">Transformación de **giro** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bb90e-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="bb90e-218">**Escala** de transformación X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="bb90e-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="bb90e-220">En la aplicación, los usuarios ahora pueden volver a colocar toda la experiencia del selector de Rocket moviendo el cubo.</span><span class="sxs-lookup"><span data-stu-id="bb90e-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="bb90e-221">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (por ejemplo, el cubo que se usa en este tutorial), el uso de un botón para alternar un rectángulo de selección que rodea la experiencia, el uso de la posición y la rotación. Gizmos y mucho más.</span><span class="sxs-lookup"><span data-stu-id="bb90e-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="bb90e-222">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="bb90e-222">Congratulations</span></span>

<span data-ttu-id="bb90e-223">En este tutorial, ha aprendido los aspectos básicos de los delimitadores espaciales de Azure.</span><span class="sxs-lookup"><span data-stu-id="bb90e-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="bb90e-224">El tutorial le proporcionó varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de anclajes espaciales de Azure y crear, cargar y descargar los anclajes espaciales de Azure en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bb90e-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="bb90e-225">En la siguiente lección, aprenderá a guardar los identificadores de delimitador de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, y cómo transferir los identificadores de delimitador entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="bb90e-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="bb90e-226">Lección siguiente: 2. guardar, recuperar y compartir anclajes espaciales de Azure</span><span class="sxs-lookup"><span data-stu-id="bb90e-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
