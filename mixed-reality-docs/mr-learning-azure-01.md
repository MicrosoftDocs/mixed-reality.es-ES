---
title: 'Tutoriales de la nube de Azure: 1. Servicios en la nube de Azure para HoloLens 2'
description: Complete este curso para aprender a implementar distintos servicios de Azure con la aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: azure, realidad mixta, unity, tutorial, hololens, hololens 2, azure blob storage, azure table storage, azure spatial anchors, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: d69ce965718e31bb5a261631f3f40217e8f7c7d6
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376487"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="e8139-105">1. Servicios en la nube de Azure para HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e8139-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="e8139-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="e8139-106">Overview</span></span>

<span data-ttu-id="e8139-107">Le damos la bienvenida a esta serie de tutoriales centrados en incorporar **servicios en la nube de Azure** a una aplicación de **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="e8139-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="e8139-108">En esta serie de tutoriales de cinco partes, aprenderá a integrar varios **servicios en la nube de Azure** en un proyecto de **Unity** para **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="e8139-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="e8139-109">Con cada capítulo consecutivo, agregará nuevos **servicios en la nube de Azure** para ampliar las características de la aplicación y la experiencia del usuario, al tiempo que le enseñará los aspectos básicos de cada **servicio en la nube de Azure**.</span><span class="sxs-lookup"><span data-stu-id="e8139-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="e8139-110">Esta serie de tutoriales se centrará en el **HoloLens 2**, pero, debido a la naturaleza multiplataforma de Unity, la mayoría de los aprendizajes también se aplicarán a las aplicaciones de escritorio y smartphone.</span><span class="sxs-lookup"><span data-stu-id="e8139-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="e8139-111">En este primer tutorial, [Introducción a los servicios en la nube de Azure para HoloLens 2](mr-learning-azure-01.md), se comienza por explicar los objetivos de la aplicación, se presenta brevemente cada servicio en la nube de Azure y se configura el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="e8139-111">In this first tutorial, [Introducing Azure Cloud Services for HoloLens 2](mr-learning-azure-01.md), you begin by explaining the goals of the application, briefly introduce you to each Azure Cloud service and set up the unity project.</span></span>

<span data-ttu-id="e8139-112">En el segundo tutorial, [Integración de Azure Storage](mr-learning-azure-02.md), comienza por integrar Azure Storage como solución de persistencia para la aplicación de demostración, aprende las diferencias entre Blob Storage y Table Storage, prepara los recursos necesarios del proyecto, configura la escena y verifica las operaciones de lectura, actualización y eliminación de datos.</span><span class="sxs-lookup"><span data-stu-id="e8139-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you start off by integrating Azure Storage as the persistence solution for the demo application, learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene and verify the read, update and delete data operations.</span></span>

<span data-ttu-id="e8139-113">Siguiendo con el tercer tutorial, [Integración de Azure Custom Vision](mr-learning-azure-03.md), usará Azure Custom Vision para entrenar y detectar imágenes en la aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e8139-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="e8139-114">El capítulo comienza con la configuración de su propio recurso de Azure Custom Vision, la preparación de los componentes de la escena y la puesta en acción mediante el entrenamiento y la detección de sus propias imágenes desde dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e8139-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="e8139-115">A continuación, avanzará al cuarto tutorial, [Integración de Azure Spatial Anchors](mr-learning-azure-04.md), donde explorará el servicio de Azure Spatial Anchors para guardar y buscar ubicaciones, conocer los conceptos principales, preparar los recursos necesarios, configurar la escena y empezar a usar la nueva característica en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e8139-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="e8139-116">Con el quinto tutorial, [Integración de Azure Bot Service con LUIS](mr-learning-azure-05.md), termina dando a la aplicación un nuevo método de interacción con el usuario: el lenguaje natural.</span><span class="sxs-lookup"><span data-stu-id="e8139-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="e8139-117">Esta característica se logrará mediante Azure Bot Framework junto con Language Understanding (LUIS).</span><span class="sxs-lookup"><span data-stu-id="e8139-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="e8139-118">Este último capítulo le enseña los aspectos básicos de Azure Bot Service y, para acelerar el proceso, utilizará Bot Framework Composer como solución de código cero.</span><span class="sxs-lookup"><span data-stu-id="e8139-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="e8139-119">Una vez que cree el bot, lo integrará en la escena y lo ejecutará con la fase final de la aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e8139-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="e8139-120">Objetivos de la aplicación</span><span class="sxs-lookup"><span data-stu-id="e8139-120">Application goals</span></span>

<span data-ttu-id="e8139-121">En esta serie de tutoriales, compilará una aplicación de **HoloLens 2** que puede detectar objetos a partir de imágenes y encontrar su ubicación espacial.</span><span class="sxs-lookup"><span data-stu-id="e8139-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="e8139-122">Para establecer un idioma de dominio, desde ahora llamaremos a estas entidades **objeto con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="e8139-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="e8139-123">El usuario puede crear un **objeto con seguimiento** para asociar un conjunto de imágenes a través de una visión de equipo o una ubicación espacial, o ambas.</span><span class="sxs-lookup"><span data-stu-id="e8139-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="e8139-124">Todos los datos deben persistir en la nube.</span><span class="sxs-lookup"><span data-stu-id="e8139-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="e8139-125">Además, algunos aspectos de la aplicación se controlarán de manera opcional mediante un lenguaje natural asistido a través de un bot.</span><span class="sxs-lookup"><span data-stu-id="e8139-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="e8139-126">Características</span><span class="sxs-lookup"><span data-stu-id="e8139-126">Features</span></span>

* <span data-ttu-id="e8139-127">Administración básica de datos e imágenes</span><span class="sxs-lookup"><span data-stu-id="e8139-127">Basic managing of data and images</span></span>
* <span data-ttu-id="e8139-128">Entrenamiento y detección de imágenes</span><span class="sxs-lookup"><span data-stu-id="e8139-128">Image training and detection</span></span>
* <span data-ttu-id="e8139-129">Almacenamiento de una ubicación espacial y orientación hacia ella</span><span class="sxs-lookup"><span data-stu-id="e8139-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="e8139-130">Asistente para bot para usar algunas características a través de un lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="e8139-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="e8139-131">Servicios en la nube de Azure</span><span class="sxs-lookup"><span data-stu-id="e8139-131">Azure Cloud services</span></span>

<span data-ttu-id="e8139-132">Para resolver las características necesarias para la aplicación, utilizará estos **servicios en la nube de Azure**:</span><span class="sxs-lookup"><span data-stu-id="e8139-132">To solve the required features for the application, you will use these **Azure Cloud** services:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="e8139-133">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="e8139-133">Azure Storage</span></span>

<span data-ttu-id="e8139-134">Usará [Azure Storage](https://azure.microsoft.com/services/storage/) de la solución de persistencia.</span><span class="sxs-lookup"><span data-stu-id="e8139-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="e8139-135">Le permite almacenar datos en una tabla y cargar archivos binarios de gran tamaño, como imágenes.</span><span class="sxs-lookup"><span data-stu-id="e8139-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="e8139-136">Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="e8139-136">Azure Custom Vision</span></span>

<span data-ttu-id="e8139-137">Con [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (parte de [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) puede asociar a *objetos con seguimiento* un conjunto de imágenes, entrenar un modelo de aprendizaje automático con el conjunto y detectar el *objeto con seguimiento*.</span><span class="sxs-lookup"><span data-stu-id="e8139-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="e8139-138">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e8139-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="e8139-139">Para almacenar la ubicación de un *objeto con seguimiento* y proporcionar una indicación guiada para encontrarla, use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="e8139-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="e8139-140">Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="e8139-140">Azure Bot Service</span></span>

<span data-ttu-id="e8139-141">La aplicación se controla principalmente por una UI tradicional, por lo que se usa [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) para agregar alto de personalidad y actuar como nuevo método de interacción.</span><span class="sxs-lookup"><span data-stu-id="e8139-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8139-142">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="e8139-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="e8139-143">Si aún no has completado la serie de [tutoriales de introducción](mr-learning-base-01.md), es recomendable que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="e8139-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="e8139-144">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e8139-144">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e8139-145">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="e8139-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e8139-146">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="e8139-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="e8139-147">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="e8139-147">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="e8139-148">Una cámara web conectada si desea probar desde el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="e8139-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="e8139-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="e8139-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="e8139-150">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.X.</span><span class="sxs-lookup"><span data-stu-id="e8139-150">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="e8139-151">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e8139-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="e8139-152">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="e8139-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="e8139-153">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="e8139-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="e8139-154">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e8139-154">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="e8139-155">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *Azure Cloud Tutorials*</span><span class="sxs-lookup"><span data-stu-id="e8139-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="e8139-156">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="e8139-156">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="e8139-157">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="e8139-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="e8139-158">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="e8139-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="e8139-159">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="e8139-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="e8139-160">[Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignar un nombre adecuado a la escena; por ejemplo, *AzureCloudServices*</span><span class="sxs-lookup"><span data-stu-id="e8139-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="e8139-161">A continuación, sigue las instrucciones de [Cambio de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="e8139-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="e8139-162">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="e8139-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="e8139-163">En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Install** (Instalar) para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="e8139-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="e8139-165">Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="e8139-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="e8139-166">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="e8139-166">Importing the tutorial assets</span></span>

<span data-ttu-id="e8139-167">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="e8139-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="e8139-168">Azure Storage para Unity</span><span class="sxs-lookup"><span data-stu-id="e8139-168">Azure storage for Unity</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="e8139-169">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="e8139-169">Azure Spatial Anchors</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="e8139-170">MRTK.Tutorials.AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="e8139-170">MRTK.Tutorials.AzureCloudServices</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="e8139-171">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="e8139-171">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="e8139-172">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="e8139-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="e8139-174">Creación y preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="e8139-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="e8139-175">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="e8139-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="e8139-176">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="e8139-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="e8139-177">Mientras mantiene presionado la tecla CTRL, haga clic en **SceneController**, **RootMenu** y **DataManager** para seleccionar los tres objetos prefabricados:</span><span class="sxs-lookup"><span data-stu-id="e8139-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="e8139-179">**SceneController (prefab)** contiene dos scripts, **SceneController (script)** y **UnityDispatcher (script)** .</span><span class="sxs-lookup"><span data-stu-id="e8139-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="e8139-180">El componente de script **SceneController** contiene varias funciones de la experiencia del usuario y facilita la funcionalidad de captura de fotos, mientras que **UnityDispatcher** es una clase auxiliar para permitir las acciones de ejecución en el subproceso principal de Unity.</span><span class="sxs-lookup"><span data-stu-id="e8139-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="e8139-181">**RootMenu (prefab)** es el objeto prefabricado de la UI principal que contiene todas las ventanas de la UI que están conectadas entre sí a través de varios componentes de script pequeños, y controlan el flujo general de la experiencia de usuario en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e8139-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="e8139-182">**DataManager (prefab)** es responsable de comunicarse con Azure Storage y se explicará con más detalle en el siguiente tutorial.</span><span class="sxs-lookup"><span data-stu-id="e8139-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="e8139-183">Ahora, con los tres objetos prefabricados aún seleccionados, arrástralos a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="e8139-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="e8139-185">Para centrarse en los objetos de la escena, puede hacer doble clic en el objeto **RootMenu** y, a continuación, volver a alejarse ligeramente:</span><span class="sxs-lookup"><span data-stu-id="e8139-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="e8139-187">Si te molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puedes ocultarlos. Para hacerlo, desactiva los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>.</span><span class="sxs-lookup"><span data-stu-id="e8139-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="e8139-188">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="e8139-188">Configuring the scene</span></span>

<span data-ttu-id="e8139-189">En esta sección, conectará *SceneManager*, *SceneManager* y *RootMenu* juntos para tener una escena en funcionamiento preparada para el siguiente tutorial, [Integración de Azure Storage](mr-learning-azure-01.md).</span><span class="sxs-lookup"><span data-stu-id="e8139-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="e8139-190">Conexión de los objetos</span><span class="sxs-lookup"><span data-stu-id="e8139-190">Connect the objects</span></span>

<span data-ttu-id="e8139-191">En la ventana Hierarchy (Jerarquía), seleccione el objeto **DataManager**.</span><span class="sxs-lookup"><span data-stu-id="e8139-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="e8139-193">En la ventana Inspector, busque el componente **DataManager (script)** y verá un espacio vacío en el evento **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="e8139-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="e8139-194">Ahora, en la ventana Hierarchy (Jerarquía), arrastre el objeto **SceneController** al evento **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="e8139-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="e8139-196">Observará que el menú desplegable del evento se ha activado, haga clic en el menú desplegable y navegue a **SceneController** y, en el submenú, seleccione la opción **Init ()** :</span><span class="sxs-lookup"><span data-stu-id="e8139-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="e8139-198">En la ventana Hierarchy (Jerarquía), seleccione el objeto **SceneController**, en Inspector encontrará el componente **SceneController** (script).</span><span class="sxs-lookup"><span data-stu-id="e8139-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="e8139-200">Verá que hay varios campos sin rellenar; vamos a cambiar eso.</span><span class="sxs-lookup"><span data-stu-id="e8139-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="e8139-201">Mueva el objeto **DataManager** de Hierarchy (Jerarquía) al campo *Data Manager* (Administrador de datos), y mueva el GameObject **RootMenu** de Hierarchy al campo *Main Menu* (Menú principal).</span><span class="sxs-lookup"><span data-stu-id="e8139-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="e8139-203">Ahora la escena está lista para los próximos tutoriales.</span><span class="sxs-lookup"><span data-stu-id="e8139-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="e8139-204">No olvide guardarla en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="e8139-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="e8139-205">Preparación de la canalización de compilación del proyecto</span><span class="sxs-lookup"><span data-stu-id="e8139-205">Prepare project build pipeline</span></span>

<span data-ttu-id="e8139-206">Aunque el proyecto todavía tiene que rellenarse con contenido, debe realizar algunos preparativos para que el proyecto esté listo para compilar para **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="e8139-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="e8139-207">1. Agregar las funcionalidades adicionales necesarias</span><span class="sxs-lookup"><span data-stu-id="e8139-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="e8139-208">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="e8139-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="e8139-210">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** (Jugador) y, a continuación, **Publishing Settings** (Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="e8139-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="e8139-212">En **Publishing Settings** (Configuración de publicación), desplácese hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitó al crear el proyecto al principio del tutorial estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="e8139-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="e8139-213">A continuación, habilite las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** y **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="e8139-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="e8139-215">2. Implementar la aplicación en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e8139-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="e8139-216">No todas las características que usará en esta serie de tutoriales pueden ejecutarse en el editor de Unity, lo que significa que debe estar familiarizado con la implementación de la aplicación en su dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e8139-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="e8139-217">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Tutoriales de introducción: Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="e8139-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="e8139-218">3. Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación</span><span class="sxs-lookup"><span data-stu-id="e8139-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="e8139-219">Todos los servicios de Azure usan Internet, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="e8139-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="e8139-220">Cuando la aplicación se esté ejecutando en el dispositivo, acepte el acceso a las siguientes funcionalidades solicitadas:</span><span class="sxs-lookup"><span data-stu-id="e8139-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="e8139-221">Micrófono</span><span class="sxs-lookup"><span data-stu-id="e8139-221">Microphone</span></span>
* <span data-ttu-id="e8139-222">Cámara</span><span class="sxs-lookup"><span data-stu-id="e8139-222">Camera</span></span>

<span data-ttu-id="e8139-223">Estas funcionalidades son necesarias para que los servicios como *Chat Bot* y *Custom Vision* funcionen correctamente.</span><span class="sxs-lookup"><span data-stu-id="e8139-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="e8139-224">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="e8139-224">Congratulations</span></span>

<span data-ttu-id="e8139-225">En este tutorial, se le ha presentado la serie de tutoriales, ha aprendido sobre las características que va a implementar y cómo los **servicios en la nube de Azure** se asocian a la aplicación de *HoloLens 2*.</span><span class="sxs-lookup"><span data-stu-id="e8139-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="e8139-226">Agregó los componentes necesarios al proyecto y preparó la escena para esta serie de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="e8139-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="e8139-227">En la lección siguiente, usará Azure Storage como solución de persistencia basada en la nube para almacenar datos e imágenes.</span><span class="sxs-lookup"><span data-stu-id="e8139-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

[<span data-ttu-id="e8139-228">Tutorial siguiente: 2. Integración de Azure Storage</span><span class="sxs-lookup"><span data-stu-id="e8139-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
