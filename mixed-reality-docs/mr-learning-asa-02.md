---
title: 'Tutoriales sobre Azure Spatial Anchors: 2. Introducción a Azure Spatial Anchors'
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d117839e51e586f4b905a20510fffc670d34cd4e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376497"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="38a18-105">2. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="38a18-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="38a18-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="38a18-106">Overview</span></span>

<span data-ttu-id="38a18-107">En este tutorial, explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors, y para crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38a18-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="38a18-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="38a18-108">Objectives</span></span>

* <span data-ttu-id="38a18-109">Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="38a18-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="38a18-110">Aprender a crear anclajes espaciales y a capturarlos desde Azure</span><span class="sxs-lookup"><span data-stu-id="38a18-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="38a18-111">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="38a18-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="38a18-112">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="38a18-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="38a18-113">Para ello, antes debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="38a18-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="38a18-114">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="38a18-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="38a18-115">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="38a18-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="38a18-116">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="38a18-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="38a18-117">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="38a18-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="38a18-118">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="38a18-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="38a18-119">[Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignarle un nombre adecuado; por ejemplo, *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="38a18-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="38a18-120">A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:</span><span class="sxs-lookup"><span data-stu-id="38a18-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="38a18-121">Cambiar el **perfil de configuración de MRTK** por **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="38a18-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="38a18-122">Cambiar las **opciones de visualización de la malla de reconocimiento espacial** a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="38a18-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="38a18-123">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="38a18-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="38a18-124">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Install** (Instalar) para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="38a18-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="38a18-126">Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="38a18-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="38a18-127">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="38a18-127">Importing the tutorial assets</span></span>

<span data-ttu-id="38a18-128">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="38a18-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="38a18-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versión 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="38a18-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="38a18-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="38a18-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="38a18-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="38a18-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="38a18-132">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="38a18-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="38a18-134">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo [Importación de Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="38a18-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="38a18-135">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="38a18-135">Preparing the scene</span></span>

<span data-ttu-id="38a18-136">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="38a18-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="38a18-137">En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** y, a continuación, haga clic y arrastre los siguientes objetos prefabricados a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="38a18-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="38a18-138">Objeto prefabricado **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="38a18-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="38a18-139">Objeto prefabricado **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="38a18-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="38a18-140">Objeto prefabricado **Instructions**</span><span class="sxs-lookup"><span data-stu-id="38a18-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="38a18-141">Objeto prefabricado **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="38a18-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="38a18-143">Si le molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, desactive los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>, como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="38a18-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="38a18-144">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="38a18-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="38a18-145">En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestren los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="38a18-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="38a18-146">En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="38a18-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="38a18-147">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="38a18-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="38a18-148">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="38a18-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="38a18-150">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **StopAzureSession**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="38a18-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="38a18-151">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="38a18-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="38a18-152">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StopAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="38a18-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="38a18-154">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **CreateAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="38a18-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="38a18-155">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="38a18-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="38a18-156">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **CreateAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="38a18-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="38a18-157">Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="38a18-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="38a18-159">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **RemoveLocalAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="38a18-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="38a18-160">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="38a18-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="38a18-161">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **RemoveLocalAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="38a18-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="38a18-162">Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="38a18-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="38a18-164">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **FindAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="38a18-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="38a18-165">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="38a18-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="38a18-166">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **FindAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="38a18-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="38a18-168">En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **DeleteAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="38a18-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="38a18-169">Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="38a18-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="38a18-170">En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **DeleteAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="38a18-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="38a18-172">Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="38a18-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="38a18-173">En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="38a18-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="38a18-174">Configure la sección **Credentials** (Credenciales) con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mr-learning-asa-01.md#prerequisites) de esta serie de tutoriales:</span><span class="sxs-lookup"><span data-stu-id="38a18-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="38a18-175">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="38a18-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="38a18-176">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="38a18-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="38a18-178">Prueba de los comportamientos básicos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="38a18-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="38a18-179">Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad de Azure Spatial Anchors, debe compilar el proyecto e implementar la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38a18-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="38a18-180">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="38a18-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="38a18-181">Cuando la aplicación se ejecute en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="38a18-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="38a18-182">Mueva el cubo a una ubicación diferente.</span><span class="sxs-lookup"><span data-stu-id="38a18-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="38a18-183">Inicie una sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="38a18-183">Start Azure Session</span></span>
1. <span data-ttu-id="38a18-184">Cree un anclaje de Azure (se crea un anclaje en la ubicación del cubo).</span><span class="sxs-lookup"><span data-stu-id="38a18-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="38a18-185">Detenga la sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="38a18-185">Stop Azure Session</span></span>
1. <span data-ttu-id="38a18-186">Quite el anclaje local (permite que el usuario mueva el cubo).</span><span class="sxs-lookup"><span data-stu-id="38a18-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="38a18-187">Mueva el cubo a otro lugar.</span><span class="sxs-lookup"><span data-stu-id="38a18-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="38a18-188">Inicie una sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="38a18-188">Start Azure Session</span></span>
1. <span data-ttu-id="38a18-189">Busque el anclaje de Azure (posiciona el cubo en la ubicación del paso 3).</span><span class="sxs-lookup"><span data-stu-id="38a18-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="38a18-190">Elimine el anclaje de Azure.</span><span class="sxs-lookup"><span data-stu-id="38a18-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="38a18-191">Detenga la sesión de Azure.</span><span class="sxs-lookup"><span data-stu-id="38a18-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="38a18-193">Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="38a18-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="38a18-194">Anclaje de una experiencia</span><span class="sxs-lookup"><span data-stu-id="38a18-194">Anchoring an experience</span></span>

<span data-ttu-id="38a18-195">En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="38a18-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="38a18-196">Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto.</span><span class="sxs-lookup"><span data-stu-id="38a18-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="38a18-197">En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="38a18-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="38a18-198">En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, configure los componentes **Transform** de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="38a18-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="38a18-199">Cambie **Scale X** (Escala X) a 1.1.</span><span class="sxs-lookup"><span data-stu-id="38a18-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="38a18-200">Cambie **Scale Z** (Escala Z) a 1.1.</span><span class="sxs-lookup"><span data-stu-id="38a18-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="38a18-202">En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** > **Rover** y haga clic y arrastre el objeto prefabricado **RoverExplorer_Complete** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="38a18-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="38a18-204">Con el objeto RoverModule_Complete recién agregado todavía seleccionado en la ventana Hierarchy (Jerarquía), arrástralo sobre el objeto **ParentAnchor** para convertirlo en un elemento secundario del objeto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="38a18-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="38a18-206">Si vuelve a compilar el proyecto e implementar la aplicación en el dispositivo, ahora podrá cambiar la posición de toda la experiencia del explorador de róver moviendo el cubo cuyo tamaño se ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="38a18-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="38a18-207">Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el cuadro de límite que rodea la experiencia, el uso de gizmos de posición y rotación, etc.</span><span class="sxs-lookup"><span data-stu-id="38a18-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="38a18-208">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="38a18-208">Congratulations</span></span>

<span data-ttu-id="38a18-209">En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="38a18-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="38a18-210">El tutorial le ha proporcionado varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="38a18-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="38a18-211">Además de crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38a18-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="38a18-212">En el siguiente tutorial, aprenderá a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="38a18-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="38a18-213">Tutorial siguiente: 3. Guardado, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="38a18-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
