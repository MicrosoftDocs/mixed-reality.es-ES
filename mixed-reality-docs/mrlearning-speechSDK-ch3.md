---
title: 'Tutoriales de Azure Speech Services: 3. Adición del componente de traducción de voz de Azure Cognitive Services'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913200"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="0f8b3-105">3. agregar el componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="0f8b3-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="0f8b3-106">En este tutorial, aprendemos sobre el componente de traducción de voz de Azure Cognitive Services en nuestro proyecto, además de traducirse en tres lenguajes diferentes.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="0f8b3-107">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0f8b3-107">Instructions</span></span>

1. <span data-ttu-id="0f8b3-108">Seleccione el objeto de Lunarcom_Base de la jerarquía y haga clic en Agregar componente en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="0f8b3-109">Busque y seleccione reconocedor de traducción de Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="0f8b3-111">Deshabilite el simulador en modo sin conexión.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="0f8b3-113">Antes de continuar, asegúrese de que el simulador en modo sin conexión está deshabilitado, tal como se muestra en la imagen anterior, antes de probar el traductor de Speech-SDK.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="0f8b3-114">Para traducir, debe estar conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="0f8b3-115">Haga clic en la lista desplegable del reconocedor de traducción de Lunarcom y seleccione el idioma al que le gustaría traducir.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="0f8b3-117">Ahora, ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="0f8b3-118">Vuelva a presionar el botón satélite para detener el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="0f8b3-119">A continuación se muestra un ejemplo de la apariencia de la escena.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="0f8b3-120">No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="0f8b3-121">A continuación se muestra un ejemplo de la apariencia de la escena:</span><span class="sxs-lookup"><span data-stu-id="0f8b3-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="0f8b3-123">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="0f8b3-123">Congratulations</span></span>

<span data-ttu-id="0f8b3-124">Ahora el proyecto puede traducir las palabras que habla en varios idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="0f8b3-125">No dude en experimentar con los lenguajes y probar la precisión de la traducción.</span><span class="sxs-lookup"><span data-stu-id="0f8b3-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="0f8b3-126">Siguiente tutorial: 4. configuración del propósito y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="0f8b3-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
