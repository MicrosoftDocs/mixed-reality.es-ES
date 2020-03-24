---
title: 'Tutoriales de los servicios de voz de Azure: 3. Adición del componente Speech Translation de Azure Cognitive Services'
description: En este curso, aprenderás a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028343"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="9f9c5-105">3. Adición del componente Speech Translation de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="9f9c5-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="9f9c5-106">En este tutorial, agregarás traducción de voz al proyecto, lo que te permitirá traducir y transcribir la voz en tres idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="9f9c5-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="9f9c5-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9f9c5-107">Objectives</span></span>

* <span data-ttu-id="9f9c5-108">Aprender a integrar la traducción de voz de Azure</span><span class="sxs-lookup"><span data-stu-id="9f9c5-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="9f9c5-109">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9f9c5-109">Instructions</span></span>

<span data-ttu-id="9f9c5-110">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Translation Recognizer (Script)** (Reconocimiento de traducción de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="9f9c5-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="9f9c5-111">Cambia **Target Language** (Idioma de destino) al idioma que quieras; por ejemplo, _German_ (Alemán).</span><span class="sxs-lookup"><span data-stu-id="9f9c5-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9f9c5-113">El componente Lunarcom Translation Recognizer (Script) (Reconocimiento de traducción de Lunarcom [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f9c5-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9f9c5-114">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="9f9c5-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="9f9c5-115">Si ahora entras en el modo de juego, puedes probar la traducción de voz presionando primero el botón del satélite:</span><span class="sxs-lookup"><span data-stu-id="9f9c5-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="9f9c5-116">A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se traducirá al idioma seleccionado y se transcribirá en el panel del terminal:</span><span class="sxs-lookup"><span data-stu-id="9f9c5-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="9f9c5-118">La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="9f9c5-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9f9c5-119">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="9f9c5-119">Congratulations</span></span>

<span data-ttu-id="9f9c5-120">Ahora, el proyecto puede traducir correctamente las palabras que digas en varios idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="9f9c5-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="9f9c5-121">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="9f9c5-121">Run the application on your device to ensure the feature is working properly.</span></span>

[<span data-ttu-id="9f9c5-122">Tutorial siguiente: 4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="9f9c5-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
