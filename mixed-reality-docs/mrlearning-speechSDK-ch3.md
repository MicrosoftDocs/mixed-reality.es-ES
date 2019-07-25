---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460312"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="df69b-104">3.    Adición del componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="df69b-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="df69b-105">En este tutorial, aprendemos Aabout el componente de traducción de voz de Azure Cognitive Services en nuestro proyecto, además de traducirse en tres lenguajes diferentes.</span><span class="sxs-lookup"><span data-stu-id="df69b-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

1. <span data-ttu-id="df69b-106">Seleccione el objeto Lunarcom_Base en la jerarquía y haga clic en Agregar componente en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="df69b-106">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="df69b-107">Busque y seleccione LunarcomTranslationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="df69b-107">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="df69b-109">Nota: Asegúrese de que el simulador en modo sin conexión está deshabilitado antes de probar el traductor de Speech-SDK.</span><span class="sxs-lookup"><span data-stu-id="df69b-109">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="df69b-110">Para traducir, debe estar conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="df69b-110">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="df69b-111">Vea la imagen siguiente sobre dónde encontrar esta configuración.</span><span class="sxs-lookup"><span data-stu-id="df69b-111">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="df69b-113">Haga clic en la lista desplegable de LunarcomTranslationRecognizer y seleccione el idioma al que le gustaría traducir.</span><span class="sxs-lookup"><span data-stu-id="df69b-113">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="df69b-115">Ahora, ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="df69b-115">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="df69b-116">Vuelva a presionar el botón satélite para detener el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="df69b-116">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="df69b-117">A continuación se muestra un ejemplo de la apariencia de la escena.</span><span class="sxs-lookup"><span data-stu-id="df69b-117">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="df69b-118">No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.</span><span class="sxs-lookup"><span data-stu-id="df69b-118">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="df69b-119">Nota: Antes de realizar las pruebas, asegúrese de que el simulador sin conexión está deshabilitado, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="df69b-119">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="df69b-121">A continuación se muestra un ejemplo de la apariencia de la escena:</span><span class="sxs-lookup"><span data-stu-id="df69b-121">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="df69b-123">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="df69b-123">Congratulations</span></span>

<span data-ttu-id="df69b-124">Ahora el proyecto puede traducir las palabras que habla en varios idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="df69b-124">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="df69b-125">No dude en experimentar con los lenguajes y probar la precisión de la traducción.</span><span class="sxs-lookup"><span data-stu-id="df69b-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="df69b-126">Siguiente tutorial: 4.  Configuración de reconocimiento de intenciones y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="df69b-126">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

