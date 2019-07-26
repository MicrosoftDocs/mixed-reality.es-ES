---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 7fe3c96cf7b888a4a91960147270be81a0973980
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485765"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="5a71f-104">3.    Adición del componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="5a71f-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="5a71f-105">En este tutorial, aprendemos Aabout el componente de traducción de voz de Azure Cognitive Services en nuestro proyecto, además de traducirse en tres lenguajes diferentes.</span><span class="sxs-lookup"><span data-stu-id="5a71f-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="5a71f-106">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="5a71f-106">Instructions</span></span>

1. <span data-ttu-id="5a71f-107">Seleccione el objeto Lunarcom_Base en la jerarquía y haga clic en Agregar componente en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="5a71f-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="5a71f-108">Busque y seleccione LunarcomTranslationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="5a71f-108">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="5a71f-110">Nota: Asegúrese de que el simulador en modo sin conexión está deshabilitado antes de probar el traductor de Speech-SDK.</span><span class="sxs-lookup"><span data-stu-id="5a71f-110">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="5a71f-111">Para traducir, debe estar conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="5a71f-111">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="5a71f-112">Vea la imagen siguiente sobre dónde encontrar esta configuración.</span><span class="sxs-lookup"><span data-stu-id="5a71f-112">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="5a71f-114">Haga clic en la lista desplegable de LunarcomTranslationRecognizer y seleccione el idioma al que le gustaría traducir.</span><span class="sxs-lookup"><span data-stu-id="5a71f-114">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="5a71f-116">Ahora, ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="5a71f-116">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="5a71f-117">Vuelva a presionar el botón satélite para detener el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="5a71f-117">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="5a71f-118">A continuación se muestra un ejemplo de la apariencia de la escena.</span><span class="sxs-lookup"><span data-stu-id="5a71f-118">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="5a71f-119">No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.</span><span class="sxs-lookup"><span data-stu-id="5a71f-119">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="5a71f-120">Nota: Antes de realizar las pruebas, asegúrese de que el simulador sin conexión está deshabilitado, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="5a71f-120">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="5a71f-122">A continuación se muestra un ejemplo de la apariencia de la escena:</span><span class="sxs-lookup"><span data-stu-id="5a71f-122">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="5a71f-124">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="5a71f-124">Congratulations</span></span>

<span data-ttu-id="5a71f-125">Ahora el proyecto puede traducir las palabras que habla en varios idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="5a71f-125">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="5a71f-126">No dude en experimentar con los lenguajes y probar la precisión de la traducción.</span><span class="sxs-lookup"><span data-stu-id="5a71f-126">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="5a71f-127">Siguiente tutorial: 4.  Configuración de reconocimiento de intenciones y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="5a71f-127">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

