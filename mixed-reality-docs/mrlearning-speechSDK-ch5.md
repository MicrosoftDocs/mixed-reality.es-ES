---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: cf51505cab2db765325c2e7b78a52e4b790845c9
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105957"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="50d9b-104">Módulo de aprendizaje de Speech SDK: control selector de Rocket con comandos de voz</span><span class="sxs-lookup"><span data-stu-id="50d9b-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="50d9b-105">En esta lección, usaremos la característica de intención del servicio de voz de Azure para comprender la intención de la voz.</span><span class="sxs-lookup"><span data-stu-id="50d9b-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="50d9b-106">Usaremos el intento de voz detectado como comandos de voz para controlar el selector de Rocket.</span><span class="sxs-lookup"><span data-stu-id="50d9b-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="50d9b-107">En esta lección, se importará el recurso del selector de Rocket y se interconectarán los comandos de la voz de intención detectados con los botones de control predefinidos para controlar el cohete.</span><span class="sxs-lookup"><span data-stu-id="50d9b-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span>

## <a name="objectives"></a><span data-ttu-id="50d9b-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="50d9b-108">Objectives</span></span>

- <span data-ttu-id="50d9b-109">Obtenga información sobre cómo conectar el intento de voz como comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="50d9b-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="50d9b-110">Obtenga información sobre cómo usar los comandos de voz para el intento de voz como comandos de entrada de control de Rocket.</span><span class="sxs-lookup"><span data-stu-id="50d9b-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="50d9b-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="50d9b-111">Instructions</span></span>

1. <span data-ttu-id="50d9b-112">En este tutorial, vamos a usar un recurso "BaseModule" para integrar Rocket Launcher con los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="50d9b-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="50d9b-113">Para ello, es necesario importar el recurso en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="50d9b-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="50d9b-114">Puede descargar el recurso "Rocket Launcher" mediante este [vínculo](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="50d9b-114">You can download the "Rocket Launcher" asset using this [link](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage).</span></span>

2. <span data-ttu-id="50d9b-115">Para importar el recurso, vaya a activos-> Importar paquete personalizado >-> navegue hasta el archivo descargado y haga clic en importar.</span><span class="sxs-lookup"><span data-stu-id="50d9b-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

    ![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="50d9b-117">Después de importar el recurso "recursos del módulo base", navegue dentro de la carpeta "recursos del módulo base": > Prefabs-> seleccione "Rocket Launcher_Complete" y, a continuación, arrástrelo y colóquelo en la jerarquía de escenas existente.</span><span class="sxs-lookup"><span data-stu-id="50d9b-117">After importing the  "Base Module Assets" asset, navigate inside the "Base Module Assets" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

    ![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="50d9b-119">Ahora tenemos que integrar nuestro "selector de Rocket" con nuestro proyecto LUIS en la [lección](mrlearning-speechSDK-ch4.md)anterior.</span><span class="sxs-lookup"><span data-stu-id="50d9b-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson [lesson](mrlearning-speechSDK-ch4.md).</span></span> <span data-ttu-id="50d9b-120">Para ello, expanda el recurso prefabricado "Rocket Launcher_Complete" en la jerarquía y busque los botones "LaunchRoundButton", "ResetRoundButton" y "sugerencias de colocación".</span><span class="sxs-lookup"><span data-stu-id="50d9b-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

    ![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="50d9b-122">Seleccione "LaunchRoundButton" y, en el panel Inspector, vaya a "interactiveable" y en "OnClick ()", arrastre y coloque "LunarModule" recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="50d9b-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="50d9b-123">A continuación, seleccione la lista desplegable función y seleccione "LunarModule" y, a continuación, vaya a la función "StartThruster ()" y selecciónela.</span><span class="sxs-lookup"><span data-stu-id="50d9b-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

    ![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

    ![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="50d9b-126">Seleccione "ResetRoundButton" y, en el panel Inspector, vaya a "interactiveable" y en "OnClick ()", arrastre y coloque "LunarModule" recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="50d9b-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="50d9b-127">A continuación, seleccione la lista desplegable función y seleccione "LunarModule" y, a continuación, vaya a la función "resetModule ()" y selecciónela.</span><span class="sxs-lookup"><span data-stu-id="50d9b-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

    ![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="50d9b-129">Seleccione "sugerencias de colocación" y, en el panel Inspector, vaya a "interactiveable" y en "OnClick ()", arrastre y coloque el recurso prefabricado "LunarModule".</span><span class="sxs-lookup"><span data-stu-id="50d9b-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="50d9b-130">A continuación, seleccione la lista desplegable función y seleccione "LunarModule" y, a continuación, vaya a la función "TogglePlacementHints" y seleccione ToggleGameOBjects ().</span><span class="sxs-lookup"><span data-stu-id="50d9b-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

    ![module4chapter5step3c](images/module4chapter5step3c.PNG)

8. <span data-ttu-id="50d9b-132">Después, seleccione la Lunarcom_Completed recurso prefabricado en la jerarquía y navegue hasta el script "Lunarcom reconocedor de intenciones" en el inspector y, a continuación, arrastre y coloque los botones "LaunchRoundButton", "ResetRoundButton" y "sugerencias de colocación" a sus lugares respectivos.</span><span class="sxs-lookup"><span data-stu-id="50d9b-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

    ![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="50d9b-134">Presione el botón PLAY (reproducir) en el editor de Unity y haga clic en el botón "Rocket" (jugar) y en las frases como "botón de inicio de la instalación de inserción", "mostrarme una sugerencia de colocación", "Presione el botón de REST" o cualquier otra frase relacionada con la solicitud de inicio, restablecimiento u sugerencia del iniciador de Rocket.</span><span class="sxs-lookup"><span data-stu-id="50d9b-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

    ![module4chapter5step5a](images/module4chapter5step5a.PNG)

    ![module4chapter5step5b](images/module4chapter5step5b.PNG)

    ![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="50d9b-138">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="50d9b-138">Congratulations</span></span>

<span data-ttu-id="50d9b-139">En esta lección, hemos aprendido a conectar los comandos de voz con tecnología de AI a comandos de voz para usarlos como método de entrada.</span><span class="sxs-lookup"><span data-stu-id="50d9b-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="50d9b-140">Ahora nuestro programa puede usar los altavoces intención como comandos de voz para proporcionar entradas para el selector de Rocket.</span><span class="sxs-lookup"><span data-stu-id="50d9b-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>
