---
title: 'Tutoriales de los servicios de voz de Azure: 1. Integración y uso de reconocimiento de voz y la transcripción'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a72eb808adbc14df65c55e694ea985d97f9ec24c
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79032592"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="8bc3e-105">1. Integración y uso del reconocimiento de voz y la transcripción</span><span class="sxs-lookup"><span data-stu-id="8bc3e-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="8bc3e-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="8bc3e-106">Overview</span></span>


<span data-ttu-id="8bc3e-107">En esta serie de tutoriales, crearás una aplicación de Mixed Reality que explore el uso de los servicios de voz de Azure con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="8bc3e-108">Cuando completes esta serie de tutoriales, podrás usar el micrófono del dispositivo para transcribir la voz a texto en tiempo real, traducir la voz a otros idiomas y aprovechar la característica Reconocimiento de la intención para comprender los comandos de voz mediante inteligencia artificial.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="8bc3e-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8bc3e-109">Objectives</span></span>

* <span data-ttu-id="8bc3e-110">Aprender a integrar los servicios de voz de Azure con una aplicación de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8bc3e-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="8bc3e-111">Aprender a usar el reconocimiento de voz para transcribir texto</span><span class="sxs-lookup"><span data-stu-id="8bc3e-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bc3e-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="8bc3e-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="8bc3e-113">Si aún no has completado la serie de [tutoriales de introducción](mrlearning-base.md), es recomendable que lo hagas en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-113">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="8bc3e-114">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8bc3e-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="8bc3e-115">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="8bc3e-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="8bc3e-116">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="8bc3e-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="8bc3e-117">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="8bc3e-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="8bc3e-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="8bc3e-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bc3e-119">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="8bc3e-120">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="8bc3e-121">Creación y preparación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="8bc3e-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="8bc3e-122">En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="8bc3e-123">Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mrlearning-base-ch1.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device), que incluyen los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-123">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="8bc3e-124">[Crear un proyecto de Unity](mrlearning-base-ch1.md#create-new-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="8bc3e-124">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. <span data-ttu-id="8bc3e-125">[Configurar el proyecto de Unity para Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-125">[Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)</span></span>

3. <span data-ttu-id="8bc3e-126">[Importar recursos de TextMesh Pro Essential](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-126">[Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)</span></span>

4. <span data-ttu-id="8bc3e-127">[Importar Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-127">[Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)</span></span>

5. <span data-ttu-id="8bc3e-128">[Configurar el proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-128">[Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)</span></span>

6. <span data-ttu-id="8bc3e-129">[Agregar Mixed Reality Toolkit a la escena de Unity](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) y asignar un nombre adecuado a la escena; por ejemplo, *AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="8bc3e-129">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="8bc3e-130">A continuación, sigue las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (modificación de la opción de visualización del reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) para cambiar el perfil de configuración de MRTK de la escena a **DefaultHoloLens2ConfigurationProfile** y las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-130">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="8bc3e-131">Como se mencionó en las instrucciones vinculadas más arriba, [Configuración del proyecto de Unity para Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit), es altamente recomendable no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-131">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="8bc3e-132">Configurar el comportamiento inicial de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="8bc3e-132">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="8bc3e-133">Dado que usarás el SDK de voz para el reconocimiento de voz y la transcripción, debes configurar los comandos de voz de MRTK para que no interfieran con la funcionalidad del SDK de voz.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-133">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="8bc3e-134">Para ello, puedes cambiar el comportamiento inicial de los comandos de voz de Auto Start (Inicio automático) a Manual Start (Inicio manual).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-134">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="8bc3e-135">Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, selecciona la pestaña **Input** (Entrada), clona **DefaultHoloLens2InputSystemProfile** y **DefaultMixedRealitySpeechCommandsProfile** y, a continuación, cambia el valor de **Start Behavior** (Comportamiento inicial) de los comandos de voz a **Manual Start** (Inicio manual):</span><span class="sxs-lookup"><span data-stu-id="8bc3e-135">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="8bc3e-137">Para obtener un recordatorio sobre cómo clonar y configurar perfiles de MRTK, puedes consultar las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit (opción para cambiar la visualización del reconocimiento espacial)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-137">For a reminder on how to clone and configure MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="8bc3e-138">Configuración de las funcionalidades</span><span class="sxs-lookup"><span data-stu-id="8bc3e-138">Configuring the capabilities</span></span>

<span data-ttu-id="8bc3e-139">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):</span><span class="sxs-lookup"><span data-stu-id="8bc3e-139">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="8bc3e-141">En **Publishing Settings** (Configuración de publicación), desplázate hasta la sección **Capabilities** (Funcionalidades) y comprueba que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception** que habilitaste al crear el proyecto al principio del tutorial estén habilitadas.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-141">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="8bc3e-142">A continuación, habilita las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer**:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-142">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="8bc3e-144">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="8bc3e-144">Importing the tutorial assets</span></span>

<span data-ttu-id="8bc3e-145">Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-145">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="8bc3e-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versión más reciente)</span><span class="sxs-lookup"><span data-stu-id="8bc3e-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="8bc3e-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8bc3e-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="8bc3e-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="8bc3e-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="8bc3e-149">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-149">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="8bc3e-150">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-150">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="8bc3e-152">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="8bc3e-152">Preparing the scene</span></span>

<span data-ttu-id="8bc3e-153">En esta sección, prepararás la escena agregando el objeto prefabricado del tutorial y configurarás el componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) para controlar la escena.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-153">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="8bc3e-154">En la ventana Project (Proyecto), desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpeechServices** > carpeta **Prefabs** y arrastra y coloca el objeto prefabricado **Lunarcom**en la ventana Hierarchy (Jerarquía) para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-154">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="8bc3e-156">Con el objeto **Lunarcom** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) al objeto Lunarcom:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-156">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="8bc3e-158">El componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-158">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="8bc3e-159">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-159">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="8bc3e-160">Con el objeto **Lunarcom** todavía seleccionado, expándelo para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **Terminal** al campo **Terminal** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]):</span><span class="sxs-lookup"><span data-stu-id="8bc3e-160">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="8bc3e-162">Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Terminal para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **ConnectionLight** al campo **Connection Light** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) y el objeto **OutputText** al campo **Output Text** (Texto de salida):</span><span class="sxs-lookup"><span data-stu-id="8bc3e-162">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="8bc3e-164">Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Buttons para mostrar sus objetos secundarios y, a continuación, en la ventana Inspector, expande la lista **Buttons** (Botones), establece su valor de **Size** (Tamaño) en 3 y arrastra los objetos **MicButton**, **SatelliteButton** y **RocketButton** a los campos de **Element** (Elemento) 0, 1 y 2, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-164">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="8bc3e-166">Conexión del proyecto de Unity con el recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="8bc3e-166">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="8bc3e-167">Para usar los servicios de voz de Azure, debes crear un recurso de Azure y obtener una clave de API para el servicio de voz.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-167">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="8bc3e-168">Sigue las instrucciones de [Prueba gratuita del servicio Voz](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) y toma nota de la región de servicio (también conocida como ubicación) y la clave de API (también conocida como Key1 o Key2).</span><span class="sxs-lookup"><span data-stu-id="8bc3e-168">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="8bc3e-169">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca la sección **Speech SDK Credentials** (Credenciales del SDK de voz) de **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) y configúrala como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-169">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="8bc3e-170">En el campo **Speech Service API Key** (Clave de API del servicio Voz), escribe la clave de API (Key1 o Key2)</span><span class="sxs-lookup"><span data-stu-id="8bc3e-170">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="8bc3e-171">En el campo **Speech Service Region** (Región del servicio Voz), escribe tu región de servicio (ubicación) con letras minúsculas y sin espacios.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-171">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="8bc3e-173">Uso del reconocimiento de voz para transcribir la voz</span><span class="sxs-lookup"><span data-stu-id="8bc3e-173">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="8bc3e-174">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Speech Recognizer (Script)** (Reconocimiento de voz de Lunarcom [script]):</span><span class="sxs-lookup"><span data-stu-id="8bc3e-174">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="8bc3e-176">El componente Lunarcom Speech Recognizer (Script) (Reconocimiento de voz de Lunarcom [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-176">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="8bc3e-177">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-177">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="8bc3e-178">Si ahora entras en el modo de juego, puedes probar el reconocimiento de voz presionando primero el botón del micrófono:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-178">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="8bc3e-180">A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se transcribirá en el panel del terminal:</span><span class="sxs-lookup"><span data-stu-id="8bc3e-180">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="8bc3e-182">La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-182">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8bc3e-183">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="8bc3e-183">Congratulations</span></span>

<span data-ttu-id="8bc3e-184">Has implementado el reconocimiento de voz con tecnología de Azure.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-184">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="8bc3e-185">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-185">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="8bc3e-186">En el próximo tutorial, obtendrás información sobre cómo ejecutar comandos con el reconocimiento de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="8bc3e-186">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="8bc3e-187">Tutorial siguiente: 2. Usar el reconocimiento de voz para ejecutar comandos</span><span class="sxs-lookup"><span data-stu-id="8bc3e-187">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
