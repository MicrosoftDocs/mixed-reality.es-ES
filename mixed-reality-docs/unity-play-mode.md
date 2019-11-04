---
title: Modo de reproducción de Unity
description: Usar el modo de reproducción en el editor de Unity para obtener una vista previa de los cambios en un dispositivo sin necesidad de implementar una aplicación.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicación remota, comunicación remota holográfica, reproductor remoto Holographic
ms.openlocfilehash: 6164d7ae1bc2d9ac13135f17132aca089e63ecdf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438227"
---
# <a name="unity-play-mode"></a><span data-ttu-id="3bf52-104">Modo de reproducción de Unity</span><span class="sxs-lookup"><span data-stu-id="3bf52-104">Unity Play Mode</span></span>

<span data-ttu-id="3bf52-105">Una forma rápida de trabajar en el proyecto de Unity es usar el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="3bf52-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="3bf52-106">Se ejecuta la aplicación localmente en el editor de Unity en el equipo.</span><span class="sxs-lookup"><span data-stu-id="3bf52-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="3bf52-107">Unity usa la comunicación remota holográfica para proporcionar una manera rápida de obtener una vista previa del contenido en un dispositivo HoloLens real.</span><span class="sxs-lookup"><span data-stu-id="3bf52-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="3bf52-108">El modo de reproducción también puede usarse con un casco de realidad mixta de Windows conectado al equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="3bf52-108">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="3bf52-109">Modo de reproducción de Unity con la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="3bf52-109">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="3bf52-110">Con Holographic Remoting, puedes experimentar tu aplicación en HoloLens mientras se ejecuta en el editor de Unity en tu PC.</span><span class="sxs-lookup"><span data-stu-id="3bf52-110">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="3bf52-111">La entrada de la asignación de miras, gestos, voz y espaciales se envía desde HoloLens al equipo.</span><span class="sxs-lookup"><span data-stu-id="3bf52-111">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="3bf52-112">Los fotogramas representados se envían a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3bf52-112">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="3bf52-113">Esta es una excelente manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo.</span><span class="sxs-lookup"><span data-stu-id="3bf52-113">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="3bf52-114">En HoloLens, vaya al **Microsoft Store** e instale la aplicación **[holográfica Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** .</span><span class="sxs-lookup"><span data-stu-id="3bf52-114">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="3bf52-115">En HoloLens, inicie la aplicación de **reproductor de comunicación remota holográfica** .</span><span class="sxs-lookup"><span data-stu-id="3bf52-115">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="3bf52-116">En Unity, vaya al menú **ventana** y seleccione **emulación holográfica**.</span><span class="sxs-lookup"><span data-stu-id="3bf52-116">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="3bf52-117">Establezca el **modo de emulación** en **remoto en dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="3bf52-117">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="3bf52-118">En **equipo remoto**, escriba la dirección IP de su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3bf52-118">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="3bf52-119">Haz clic en **Connect**.</span><span class="sxs-lookup"><span data-stu-id="3bf52-119">Click **Connect**.</span></span> <span data-ttu-id="3bf52-120">Debería ver el cambio de estado de la **conexión** a **conectado** y ver que la pantalla aparece en blanco en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3bf52-120">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="3bf52-121">Haga clic en el botón **reproducir** para iniciar el modo de reproducción y experimentar la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3bf52-121">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="3bf52-122">Holographic Remoting requiere una conexión Wi-Fi y rápida de PC.</span><span class="sxs-lookup"><span data-stu-id="3bf52-122">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="3bf52-123">Vea [Holographic Remoting Player](holographic-remoting-player.md) para obtener detalles completos.</span><span class="sxs-lookup"><span data-stu-id="3bf52-123">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="3bf52-124">Para obtener los mejores resultados, asegúrese de que la aplicación establece correctamente el [punto de enfoque](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="3bf52-124">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="3bf52-125">Esto ayuda a Holographic Remoting a adaptar mejor su escena a la latencia de la conexión inalámbrica.</span><span class="sxs-lookup"><span data-stu-id="3bf52-125">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bf52-126">Consulta también</span><span class="sxs-lookup"><span data-stu-id="3bf52-126">See Also</span></span>
* [<span data-ttu-id="3bf52-127">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="3bf52-127">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
