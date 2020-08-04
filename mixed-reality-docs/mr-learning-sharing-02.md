---
title: 'Tutoriales sobre las funcionalidades multiusuario: 2. Configuración de Photon Unity Networking'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ed55d1f84db7ee8dc33f0f738de2b6b98a305fd3
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376407"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="cf099-105">2. Configuración de Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="cf099-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="cf099-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="cf099-106">Overview</span></span>

<span data-ttu-id="cf099-107">En este tutorial, se preparará para la creación de una experiencia compartida con Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="cf099-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="cf099-108">Obtendrá información sobre cómo crear una aplicación de PUN, importar recursos de PUN en el proyecto de Unity y conectar el proyecto de Unity a la aplicación de PUN.</span><span class="sxs-lookup"><span data-stu-id="cf099-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="cf099-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cf099-109">Objectives</span></span>

* <span data-ttu-id="cf099-110">Aprender cómo crear una aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="cf099-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="cf099-111">Aprender cómo buscar e importar los recursos de PUN</span><span class="sxs-lookup"><span data-stu-id="cf099-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="cf099-112">Aprender a conectar el proyecto de Unity a la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="cf099-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="cf099-113">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="cf099-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="cf099-114">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="cf099-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="cf099-115">Para ello, antes debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="cf099-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="cf099-116">[Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="cf099-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="cf099-117">Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="cf099-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="cf099-118">Importar los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="cf099-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="cf099-119">Importar Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="cf099-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="cf099-120">Configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="cf099-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="cf099-121">[Crear y configurar la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignar un nombre adecuado a la escena; por ejemplo, *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="cf099-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="cf099-122">A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:</span><span class="sxs-lookup"><span data-stu-id="cf099-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="cf099-123">Cambiar el **perfil de configuración de MRTK** por **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="cf099-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="cf099-124">Cambiar las **opciones de visualización de la malla de reconocimiento espacial** a **Oclusión**.</span><span class="sxs-lookup"><span data-stu-id="cf099-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="cf099-125">Habilitación de funcionalidades adicionales</span><span class="sxs-lookup"><span data-stu-id="cf099-125">Enabling additional capabilities</span></span>

<span data-ttu-id="cf099-126">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="cf099-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="cf099-128">En **Configuración de publicación**, desplácese hasta la sección **Funcionalidades** y compruebe que las funcionalidades **InternetClient**, **Microphone**, **SpatialPerception** y **GazeInput** que habilitó durante el paso anterior titulado [Configuración del proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project), estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="cf099-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="cf099-129">A continuación, habilite las siguientes funcionalidades adicionales:</span><span class="sxs-lookup"><span data-stu-id="cf099-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="cf099-130">Funcionalidad **InternetClientServer**</span><span class="sxs-lookup"><span data-stu-id="cf099-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="cf099-131">Funcionalidad **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="cf099-131">**PrivateNetworkClientServer** capability</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="cf099-133">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="cf099-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="cf099-134">En el menú de Unity, seleccione **Ventana** > **Administrador de paquetes** para abrir la ventana Administrador de paquetes y, a continuación, seleccione **AR Foundation** y haga clic en el botón **Instalar** para instalar el paquete:</span><span class="sxs-lookup"><span data-stu-id="cf099-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cf099-136">Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="cf099-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="cf099-137">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="cf099-137">Importing the tutorial assets</span></span>

<span data-ttu-id="cf099-138">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="cf099-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="cf099-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (versión 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="cf099-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="cf099-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cf099-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="cf099-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cf099-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="cf099-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cf099-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="cf099-143">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="cf099-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="cf099-145">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones de [Importación de Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="cf099-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="cf099-146">Después de importar el paquete de recursos del tutorial de MultiUserCapabilities, verás varios errores con el código [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) en la ventana de la consola en los que se indicará que falta el tipo o el espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="cf099-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="cf099-147">Este comportamiento es el esperado y se resolverá en la sección siguiente cuando importes los recursos de PUN.</span><span class="sxs-lookup"><span data-stu-id="cf099-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="cf099-148">Importación de recursos de PUN</span><span class="sxs-lookup"><span data-stu-id="cf099-148">Importing the PUN assets</span></span>

<span data-ttu-id="cf099-149">En el menú de Unity, seleccione **Ventana** > **Asset Store** (Almacén de recursos) para abrir la ventana del almacén de recursos, busque y seleccione **PUN 2 - FREE** de Exit Games y haga clic en el botón **Descargar** para descargar el paquete de recursos en su cuenta de Unity.</span><span class="sxs-lookup"><span data-stu-id="cf099-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="cf099-150">Una vez completada la descarga, haz clic en el botón **Importar** para abrir la ventana Import Unity Package (Importar paquete de Unity):</span><span class="sxs-lookup"><span data-stu-id="cf099-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="cf099-152">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="cf099-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="cf099-154">Una vez que Unity haya completado el proceso de importación, se mostrará la ventana Pun Wizard (Asistente para PUN) con el menú de configuración de PUN cargado. Por ahora, puedes omitir o cerrar esta ventana:</span><span class="sxs-lookup"><span data-stu-id="cf099-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="cf099-156">Creación de la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="cf099-156">Creating the PUN application</span></span>

<span data-ttu-id="cf099-157">En esta sección, creará una cuenta de Photon, si aún no tiene ninguna, y creará una nueva aplicación de PUN.</span><span class="sxs-lookup"><span data-stu-id="cf099-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="cf099-158">Ve al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">panel</a> de Photon e inicia sesión si ya tienes una cuenta que quieras usar. De lo contrario, haz clic en el vínculo **Crear una** y sigue las instrucciones para registrar una cuenta nueva:</span><span class="sxs-lookup"><span data-stu-id="cf099-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="cf099-160">Una vez que hayas iniciado sesión, haz clic en el botón **Crear una nueva aplicación**:</span><span class="sxs-lookup"><span data-stu-id="cf099-160">Once signed in, click the **Create a New App** button:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="cf099-162">En la página Crear una nueva aplicación, escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="cf099-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="cf099-163">En Photon Type (Tipo de Photon), seleccione PUN.</span><span class="sxs-lookup"><span data-stu-id="cf099-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="cf099-164">En Nombre, escribe un nombre adecuado, por ejemplo, _Tutoriales de MRTK_.</span><span class="sxs-lookup"><span data-stu-id="cf099-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="cf099-165">En Descripción, puedes escribir una descripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="cf099-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="cf099-166">En URL, deja el campo vacío.</span><span class="sxs-lookup"><span data-stu-id="cf099-166">For Url, leave the field empty</span></span>

<span data-ttu-id="cf099-167">A continuación, haga clic en el botón **Crear** para crear la nueva aplicación:</span><span class="sxs-lookup"><span data-stu-id="cf099-167">Then click the **Create** button to create the new app:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="cf099-169">Una vez que Photon haya finalizado el proceso de creación, la nueva aplicación de PUN se mostrará en el panel:</span><span class="sxs-lookup"><span data-stu-id="cf099-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="cf099-171">Conexión del proyecto de Unity con la aplicación de PUN</span><span class="sxs-lookup"><span data-stu-id="cf099-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="cf099-172">En esta sección, conectará el proyecto de Unity a la aplicación de PUN que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="cf099-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="cf099-173">En el panel de Photon, haz clic en el campo **Id. de la aplicación** para mostrar el identificador de la aplicación y, a continuación, cópialo en el portapapeles:</span><span class="sxs-lookup"><span data-stu-id="cf099-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="cf099-175">En el menú de Unity, selecciona **Ventana** > **Photon Unity Networking** > **Pun Wizard** (Asistente para PUN) para abrir la ventana del asistente para PUN, haz clic en el botón **Proyecto de instalación** para abrir el menú de configuración de PUN y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="cf099-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="cf099-176">En el campo **AppId or Email** (Id. de la aplicación o correo electrónico), pega el identificador de la aplicación de PUN que copiaste en el paso anterior</span><span class="sxs-lookup"><span data-stu-id="cf099-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="cf099-177">A continuación, haz clic en el botón **Proyecto de instalación** para aplicar el id. de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="cf099-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="cf099-179">Una vez que Unity termine el proceso de configuración de PUN, se mostrará el mensaje **Listo** en el menú de configuración de PUN.</span><span class="sxs-lookup"><span data-stu-id="cf099-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="cf099-180">Asimismo, se seleccionará automáticamente el recurso **PhotonServerSettings** en la ventana Proyecto para que sus propiedades se muestren en la ventana Inspector:</span><span class="sxs-lookup"><span data-stu-id="cf099-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="cf099-182">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="cf099-182">Congratulations</span></span>

<span data-ttu-id="cf099-183">Creó correctamente una aplicación de PUN y la conectó al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="cf099-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="cf099-184">El siguiente paso consiste en permitir las conexiones con otros usuarios para que varios usuarios puedan verse entre sí.</span><span class="sxs-lookup"><span data-stu-id="cf099-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

[<span data-ttu-id="cf099-185">Tutorial siguiente: 3. Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="cf099-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)
