---
title: 'Tutoriales de Azure Speech Services: 3. Adición del componente de traducción de voz de Azure Cognitive Services'
description: En este curso, aprenderá a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143227"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="b8611-105">3. agregar el componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="b8611-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="b8611-106">En este tutorial, obtendrá información sobre el componente de traducción de voz de Azure Cognitive Services del proyecto, así como sobre cómo traducir en tres idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="b8611-106">In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="b8611-107">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8611-107">Instructions</span></span>

1. <span data-ttu-id="b8611-108">Seleccione el objeto de Lunarcom_Base de la jerarquía y haga clic en Agregar componente en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="b8611-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="b8611-109">Busque y seleccione reconocedor de traducción de Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="b8611-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="b8611-111">Deshabilite el simulador en modo sin conexión.</span><span class="sxs-lookup"><span data-stu-id="b8611-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="b8611-113">Antes de continuar, asegúrese de que el simulador en modo sin conexión está deshabilitado (como se muestra en la imagen anterior) antes de probar el traductor de Speech-SDK.</span><span class="sxs-lookup"><span data-stu-id="b8611-113">Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator.</span></span> <span data-ttu-id="b8611-114">Para traducir, debe estar conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="b8611-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="b8611-115">Haga clic en la lista desplegable del reconocedor de traducción de Lunarcom y seleccione el idioma al que le gustaría traducir.</span><span class="sxs-lookup"><span data-stu-id="b8611-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="b8611-117">Ejecute la aplicación y pruebe el traductor; para ello, haga clic en el botón satélite y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="b8611-117">Run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="b8611-118">Vuelva a presionar el botón satélite para detener el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="b8611-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="b8611-119">A continuación se muestra un ejemplo de la apariencia de la escena.</span><span class="sxs-lookup"><span data-stu-id="b8611-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="b8611-120">No dude en cambiar el idioma en la lista desplegable "idioma de destino" (consulte la imagen anterior) para explorar la traducción en otros idiomas.</span><span class="sxs-lookup"><span data-stu-id="b8611-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="b8611-121">A continuación se muestra un ejemplo de la apariencia de la escena:</span><span class="sxs-lookup"><span data-stu-id="b8611-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="b8611-123">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="b8611-123">Congratulations</span></span>

<span data-ttu-id="b8611-124">El proyecto ahora puede traducir correctamente las palabras que habla en varios idiomas diferentes.</span><span class="sxs-lookup"><span data-stu-id="b8611-124">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="b8611-125">No dude en experimentar con los lenguajes y probar la precisión de la traducción.</span><span class="sxs-lookup"><span data-stu-id="b8611-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="b8611-126">Siguiente tutorial: 4. configuración del propósito y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="b8611-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
