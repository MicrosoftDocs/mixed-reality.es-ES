---
title: 'Tutoriales de los servicios de voz de Azure: 2. Adición de un modo sin conexión para la traducción de voz a texto local'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031625"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="d22de-105">2. Usar el reconocimiento de voz para ejecutar comandos</span><span class="sxs-lookup"><span data-stu-id="d22de-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="d22de-106">En este tutorial, agregarás la posibilidad de ejecutar comandos con el reconocimiento de voz de Azure, lo que te permitirá hacer que pase algo en función de la palabra o frase que definas.</span><span class="sxs-lookup"><span data-stu-id="d22de-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="d22de-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d22de-107">Objectives</span></span>

* <span data-ttu-id="d22de-108">Aprender a usar el reconocimiento de voz de Azure para ejecutar comandos</span><span class="sxs-lookup"><span data-stu-id="d22de-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="d22de-109">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d22de-109">Instructions</span></span>

<span data-ttu-id="d22de-110">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Wake Word Recognizer (Script)** (Reconocimiento de la palabra de activación de Lunarcom [script]) al objeto Lunarcom y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d22de-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="d22de-111">En el campo **Wake Word** (Palabra de activación), escribe una frase adecuada; por ejemplo, _Activate terminal_ (Activar terminal).</span><span class="sxs-lookup"><span data-stu-id="d22de-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="d22de-112">En el campo **Dismiss Word** (Palabra de descarte), escribe una frase adecuada; por ejemplo, _Dismiss terminal_ (Descartar terminal).</span><span class="sxs-lookup"><span data-stu-id="d22de-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d22de-114">El componente Wake Word Recognizer (Script) (Reconocimiento de palabra de activación [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d22de-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="d22de-115">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="d22de-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="d22de-116">Si ahora entras en el modo de juego, como en el tutorial anterior, el panel del terminal está habilitado de forma predeterminada, pero puedes deshabilitarlo diciendo la palabra de descarte: **Dismiss terminal** (Descartar terminal):</span><span class="sxs-lookup"><span data-stu-id="d22de-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="d22de-118">Para volver a habilitarlo, indica la palabra de activación **Activate terminal** (Activar terminal):</span><span class="sxs-lookup"><span data-stu-id="d22de-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="d22de-120">La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="d22de-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="d22de-121">Si prevés que no podrás conectarte a Azure con frecuencia, también puedes implementar comandos de voz mediante MRTK, para lo que debes seguir las instrucciones de [Habilitar comandos de voz](mrlearning-base-ch5.md#enabling-voice-commands).</span><span class="sxs-lookup"><span data-stu-id="d22de-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d22de-122">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="d22de-122">Congratulations</span></span>

<span data-ttu-id="d22de-123">Has implementado comandos de voz con tecnología de Azure.</span><span class="sxs-lookup"><span data-stu-id="d22de-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="d22de-124">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="d22de-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="d22de-125">En el próximo tutorial, aprenderás a traducir la voz mediante la traducción de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="d22de-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="d22de-126">Tutorial siguiente: 3. Adición del componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="d22de-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
