---
title: 'Tutoriales de Azure Speech Services: 2. Agregar un modo sin conexión para la traducción de voz a texto local'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 962d7d4750cf59fe56de4af9088c90e8ecd0aa16
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913210"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="fc606-105">2. agregar un modo sin conexión para la traducción de voz a texto local</span><span class="sxs-lookup"><span data-stu-id="fc606-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="fc606-106">En este tutorial, vamos a agregar un modo sin conexión que le permite realizar la traducción de voz a texto local cuando no se puede conectar al servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="fc606-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="fc606-107">También se *simulará* un estado desconectado.</span><span class="sxs-lookup"><span data-stu-id="fc606-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="fc606-108">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="fc606-108">Instructions</span></span>

1. <span data-ttu-id="fc606-109">Seleccione el objeto de Lunarcom_Base de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="fc606-109">Select the Lunarcom_Base object in the hierarchy.</span></span>

2. <span data-ttu-id="fc606-110">Haga clic en Agregar componente en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="fc606-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="fc606-111">Busque y seleccione el reconocimiento sin conexión de Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="fc606-111">Search for and select the Lunarcom Offline Recognition.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="fc606-113">Haga clic en la lista desplegable de LunarcomOfflineRecognizer y seleccione habilitado.</span><span class="sxs-lookup"><span data-stu-id="fc606-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="fc606-114">Este programa el proyecto para que actúe como el usuario no tiene conexión.</span><span class="sxs-lookup"><span data-stu-id="fc606-114">This programs the project to act like the user doesn't have a connection.</span></span>

    ![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="fc606-116">Presione reproducir en el editor de Unity y pruébelo.</span><span class="sxs-lookup"><span data-stu-id="fc606-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="fc606-117">Presione el micrófono en la esquina inferior izquierda de la escena y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="fc606-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span>

    >[!NOTE]
    ><span data-ttu-id="fc606-118">Como estamos sin conexión, se ha deshabilitado la funcionalidad de reactivación de Word.</span><span class="sxs-lookup"><span data-stu-id="fc606-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="fc606-119">Deberá hacer clic físicamente en el micrófono cada vez que quiera que la voz se reconozca cuando esté sin conexión.</span><span class="sxs-lookup"><span data-stu-id="fc606-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span>

    <span data-ttu-id="fc606-120">A continuación se muestra un ejemplo de la apariencia que podría tener la escena.</span><span class="sxs-lookup"><span data-stu-id="fc606-120">Below is an example of what your scene could look like.</span></span>

    ![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="fc606-122">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="fc606-122">Congratulations</span></span>

<span data-ttu-id="fc606-123">Se ha habilitado el modo sin conexión.</span><span class="sxs-lookup"><span data-stu-id="fc606-123">The offline mode has been enabled.</span></span> <span data-ttu-id="fc606-124">Ahora, cuando esté sin conexión, puede seguir trabajando en el proyecto con el SDK de Speech.</span><span class="sxs-lookup"><span data-stu-id="fc606-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span>

[<span data-ttu-id="fc606-125">Siguiente tutorial: 3. agregar el componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="fc606-125">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
