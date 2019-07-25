---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460303"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="a4a58-104">2.    Agregar un modo sin conexión para la traducción de voz a texto local</span><span class="sxs-lookup"><span data-stu-id="a4a58-104">2.    Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="a4a58-105">En este tutorial, vamos a agregar un modo sin conexión que le permite realizar la traducción de voz a texto local cuando no se puede conectar al servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="a4a58-105">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="a4a58-106">También se *simulará* un estado desconectado.</span><span class="sxs-lookup"><span data-stu-id="a4a58-106">We will also *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="a4a58-107">Seleccione el objeto Lunarcom_Base en la jerarquía y haga clic en Agregar componente en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="a4a58-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="a4a58-108">Busque y seleccione el reconocimiento sin conexión de Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="a4a58-108">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="a4a58-110">Haga clic en la lista desplegable de LunarcomOfflineRecognizer y seleccione habilitado.</span><span class="sxs-lookup"><span data-stu-id="a4a58-110">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="a4a58-111">Este programa el proyecto para que actúe como el usuario no tiene conexión.</span><span class="sxs-lookup"><span data-stu-id="a4a58-111">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="a4a58-113">Ahora, presione reproducir en el editor de Unity y pruébelo.</span><span class="sxs-lookup"><span data-stu-id="a4a58-113">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="a4a58-114">Presione el micrófono situado en la esquina inferior izquierda de la escena y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="a4a58-114">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="a4a58-115">Como estamos sin conexión, se ha deshabilitado la funcionalidad de reactivación de Word.</span><span class="sxs-lookup"><span data-stu-id="a4a58-115">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="a4a58-116">Tendrá que hacer clic físicamente en el micrófono cada vez que quiera que la voz se reconozca cuando esté sin conexión.</span><span class="sxs-lookup"><span data-stu-id="a4a58-116">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="a4a58-117">A continuación se muestra un ejemplo de la apariencia que podría tener la escena.</span><span class="sxs-lookup"><span data-stu-id="a4a58-117">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="a4a58-119">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="a4a58-119">Congratulations</span></span>

<span data-ttu-id="a4a58-120">Se ha habilitado el modo sin conexión.</span><span class="sxs-lookup"><span data-stu-id="a4a58-120">The offline mode has been enabled.</span></span> <span data-ttu-id="a4a58-121">Ahora, cuando esté sin conexión, puede seguir trabajando en el proyecto con el SDK de Speech.</span><span class="sxs-lookup"><span data-stu-id="a4a58-121">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="a4a58-122">Siguiente tutorial: 3.  Adición del componente de traducción de voz de Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="a4a58-122">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

