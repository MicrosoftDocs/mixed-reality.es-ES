---
title: 'Tutoriales sobre las funcionalidades multiusuario: 1. Configuración de Photon Unity Networking'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610738"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="852e5-105">1. Configuración de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="852e5-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="852e5-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="852e5-106">Overview</span></span>

<span data-ttu-id="852e5-107">En este tutorial, aprenderás a prepararte para la creación de una experiencia compartida con Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="852e5-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="852e5-108">Photon es una de las diversas opciones de redes disponibles para que los desarrolladores de Mixed Reality creen experiencias compartidas.</span><span class="sxs-lookup"><span data-stu-id="852e5-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="852e5-109">Obtendrás información sobre cómo crear una aplicación de Photon PUN, importar recursos de Photon PUN en el proyecto de Unity y conectar el proyecto de Unity a la aplicación de Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="852e5-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="852e5-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="852e5-110">Objectives</span></span>

* <span data-ttu-id="852e5-111">Información sobre cómo crear una aplicación de Photon PUN</span><span class="sxs-lookup"><span data-stu-id="852e5-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="852e5-112">Información sobre cómo buscar e importar los recursos de Photon PUN</span><span class="sxs-lookup"><span data-stu-id="852e5-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="852e5-113">Información sobre cómo conectar el proyecto de Unity a la aplicación de Photon PUN</span><span class="sxs-lookup"><span data-stu-id="852e5-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="852e5-114">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="852e5-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="852e5-115">Si aún no has completado los [tutoriales de introducción](mrlearning-base.md) ni los [tutoriales de Azure Spatial Anchors](mrlearning-asa-ch1.md), te recomendamos que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="852e5-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="852e5-116">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="852e5-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="852e5-117">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="852e5-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="852e5-118">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="852e5-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="852e5-119">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="852e5-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="852e5-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="852e5-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="852e5-121">Completa la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="852e5-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="852e5-122">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="852e5-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="852e5-123">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="852e5-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="852e5-124">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="852e5-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="852e5-125">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="852e5-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="852e5-126">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mrlearning-base-ch1.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="852e5-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="852e5-127">[Crear un proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="852e5-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. <span data-ttu-id="852e5-128">[Configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="852e5-128">[Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)</span></span>

3. [<span data-ttu-id="852e5-129">Importar recursos de TextMesh Pro Essential</span><span class="sxs-lookup"><span data-stu-id="852e5-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="852e5-130">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="852e5-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="852e5-131">Configurar el proyecto de Unity para Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="852e5-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="852e5-132">[Agregar Mixed Reality Toolkit a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y asignar un nombre adecuado a la escena; por ejemplo, *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="852e5-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="852e5-133">A continuación, sigue las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (modificación de la opción de visualización del reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="852e5-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="852e5-134">Como se mencionó en las instrucciones vinculadas más arriba, [Configuración del proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), es altamente recomendable no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="852e5-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="852e5-135">Configuración de las funcionalidades</span><span class="sxs-lookup"><span data-stu-id="852e5-135">Configuring the capabilities</span></span>

<span data-ttu-id="852e5-136">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="852e5-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="852e5-138">En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="852e5-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="852e5-139">A continuación, habilita las funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** y **RemovableStorage**:</span><span class="sxs-lookup"><span data-stu-id="852e5-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="852e5-141">Adición de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="852e5-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="852e5-142">En esta sección, instalarás el paquete integrado de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que importarás en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="852e5-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="852e5-143">En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):</span><span class="sxs-lookup"><span data-stu-id="852e5-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="852e5-145">Puede que el paquete de AR Foundation tarde unos segundos en aparecer en la lista.</span><span class="sxs-lookup"><span data-stu-id="852e5-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="852e5-146">En la ventana Package Manager (Administrador de paquetes), selecciona **AR Foundation** e instala el paquete haciendo clic en el botón **Instalar**:</span><span class="sxs-lookup"><span data-stu-id="852e5-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="852e5-148">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="852e5-148">Importing the tutorial assets</span></span>

<span data-ttu-id="852e5-149">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="852e5-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="852e5-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="852e5-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="852e5-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="852e5-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="852e5-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="852e5-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="852e5-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="852e5-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="852e5-154">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="852e5-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="852e5-155">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="852e5-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="852e5-157">Después de importar el paquete de recursos del tutorial de MultiUserCapabilities, verás varios errores con el código [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) en la ventana de la consola en los que se indicará que falta el tipo o el espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="852e5-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="852e5-158">Este comportamiento es el esperado y se resolverá en la sección siguiente cuando importes los recursos de Photon.</span><span class="sxs-lookup"><span data-stu-id="852e5-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="852e5-159">Importación de recursos de Photon</span><span class="sxs-lookup"><span data-stu-id="852e5-159">Importing the Photon assets</span></span>

<span data-ttu-id="852e5-160">En esta sección, importarás los recursos de Photon Unity Network (PUN) del almacén de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="852e5-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="852e5-161">En el menú de Unity, selecciona **Ventana** > **Asset Store** (Almacén de recursos) para abrir la ventana del almacén de recursos, busca y selecciona **PUN 2 - FREE** de Exit Games y, a continuación, haz clic en el botón **Descargar** para descargar el paquete de recursos en tu cuenta de Unity:</span><span class="sxs-lookup"><span data-stu-id="852e5-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="852e5-163">Una vez completada la descarga, haz clic en el botón **Importar** para abrir la ventana Import Unity Package (Importar paquete de Unity):</span><span class="sxs-lookup"><span data-stu-id="852e5-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="852e5-165">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="852e5-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="852e5-167">Una vez que Unity haya completado el proceso de importación, se mostrará la ventana Pun Wizard (Asistente para PUN) con el menú de configuración de PUN cargado. Por ahora, puedes omitir o cerrar esta ventana:</span><span class="sxs-lookup"><span data-stu-id="852e5-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="852e5-169">Configuración de Photon</span><span class="sxs-lookup"><span data-stu-id="852e5-169">Setting up Photon</span></span>

<span data-ttu-id="852e5-170">En esta sección, crearás una cuenta de Photon, si aún no tienes ninguna, y crearás una nueva aplicación de PUN.</span><span class="sxs-lookup"><span data-stu-id="852e5-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="852e5-171">Ve al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">panel</a> de Photon e inicia sesión si ya tienes una cuenta que quieras usar. De lo contrario, haz clic en el vínculo **Crear una** y sigue las instrucciones para registrar una cuenta nueva:</span><span class="sxs-lookup"><span data-stu-id="852e5-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="852e5-173">Una vez que hayas iniciado sesión, haz clic en el botón **Crear una nueva aplicación**:</span><span class="sxs-lookup"><span data-stu-id="852e5-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="852e5-175">En la página Crear una nueva aplicación, escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="852e5-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="852e5-176">En Photon Type (Tipo de Photon), selecciona Photon PUN.</span><span class="sxs-lookup"><span data-stu-id="852e5-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="852e5-177">En Nombre, escribe un nombre adecuado, por ejemplo, _Tutoriales de MRTK_.</span><span class="sxs-lookup"><span data-stu-id="852e5-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="852e5-178">En Descripción, puedes escribir una descripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="852e5-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="852e5-179">En URL, deja el campo vacío.</span><span class="sxs-lookup"><span data-stu-id="852e5-179">For Url, leave the field empty</span></span>

<span data-ttu-id="852e5-180">A continuación, haz clic en el botón **Crear** para crear la nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="852e5-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="852e5-182">Una vez que Photon haya finalizado el proceso de creación, la nueva aplicación de PUN aparecerá en el panel:</span><span class="sxs-lookup"><span data-stu-id="852e5-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="852e5-184">Conexión del proyecto de Unity con la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="852e5-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="852e5-185">En esta sección, conectarás el proyecto de Unity a la aplicación de PUN que creaste en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="852e5-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="852e5-186">En el panel de Photon, haz clic en el campo **Id. de la aplicación** para mostrar el identificador de la aplicación y, a continuación, cópialo en el portapapeles:</span><span class="sxs-lookup"><span data-stu-id="852e5-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="852e5-188">En el menú de Unity, selecciona **Ventana** > **Photon Unity Networking** > **Pun Wizard** (Asistente para PUN) para abrir la ventana del asistente para PUN, haz clic en el botón **Proyecto de instalación** para abrir el menú de configuración de PUN y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="852e5-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="852e5-189">En el campo **AppId or Email** (Id. de la aplicación o correo electrónico), pega el identificador de la aplicación de PUN que copiaste en el paso anterior</span><span class="sxs-lookup"><span data-stu-id="852e5-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="852e5-190">A continuación, haz clic en el botón **Proyecto de instalación** para aplicar el id. de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="852e5-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="852e5-192">Una vez que Unity termine el proceso de configuración de PUN, se mostrará el mensaje **Listo** en el menú de configuración de PUN.</span><span class="sxs-lookup"><span data-stu-id="852e5-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="852e5-193">Así mismo, se seleccionará automáticamente el recurso **PhotonServerSettings** en la ventana Proyecto para que sus propiedades se muestren en la ventana Inspector:</span><span class="sxs-lookup"><span data-stu-id="852e5-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="852e5-195">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="852e5-195">Congratulations</span></span>

<span data-ttu-id="852e5-196">Has creado correctamente una aplicación de Photon PUN y la has conectado al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="852e5-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="852e5-197">El siguiente paso consiste en permitir las conexiones con otros usuarios para que varios usuarios puedan verse entre sí.</span><span class="sxs-lookup"><span data-stu-id="852e5-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="852e5-198">[Tutorial siguiente: 2. Conexión de varios usuarios](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="852e5-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
