---
title: Modo de juego de Unity
description: Uso del modo de reproducir en el editor de Unity para obtener una vista previa de los cambios en un dispositivo sin necesidad de implementar una aplicación.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, comunicación remota, remoting holográfica, Reproductor de remoting holográfica
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597827"
---
# <a name="unity-play-mode"></a><span data-ttu-id="e295b-104">Modo de juego de Unity</span><span class="sxs-lookup"><span data-stu-id="e295b-104">Unity Play Mode</span></span>

<span data-ttu-id="e295b-105">Una forma rápida de trabajar en el proyecto de Unity es usar el "Modo de reproducir".</span><span class="sxs-lookup"><span data-stu-id="e295b-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="e295b-106">Esto ejecuta la aplicación localmente en el editor de Unity en su PC.</span><span class="sxs-lookup"><span data-stu-id="e295b-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="e295b-107">Unity usa holográfica Remoting para proporcionar una forma rápida de obtener una vista previa de su contenido en un dispositivo real de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e295b-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="e295b-108">Modo de juego Unity con comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="e295b-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="e295b-109">Con la comunicación remota de holográfica, pueden experimentar la aplicación en el HoloLens, mientras se ejecuta en el editor de Unity en su PC.</span><span class="sxs-lookup"><span data-stu-id="e295b-109">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="e295b-110">Mirada, gestos, voz y entrada de asignación espacial se envía desde su HoloLens a su equipo.</span><span class="sxs-lookup"><span data-stu-id="e295b-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="e295b-111">Fotogramas representados, a continuación, se envían a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e295b-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="e295b-112">Esto es una excelente manera de depurar la aplicación rápidamente sin compilar e implementar un proyecto completo.</span><span class="sxs-lookup"><span data-stu-id="e295b-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="e295b-113">En su HoloLens, vaya a la **Microsoft Store** e instale el **[holográfica Reproductor Remoting](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span><span class="sxs-lookup"><span data-stu-id="e295b-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="e295b-114">En su HoloLens, inicie el **holográfica Reproductor Remoting** app.</span><span class="sxs-lookup"><span data-stu-id="e295b-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="e295b-115">En Unity, vaya a la **ventana** menú y seleccione **emulación holográfica**.</span><span class="sxs-lookup"><span data-stu-id="e295b-115">In Unity, go to the **Window** menu and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="e295b-116">Establecer **en modo de emulación** a **remota al dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="e295b-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="e295b-117">Para **máquina remota**, escriba la dirección IP de su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e295b-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="e295b-118">Haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="e295b-118">Click **Connect**.</span></span> <span data-ttu-id="e295b-119">Debería ver **estado de la conexión** cambie a **conectado** y marche la pantalla en blanco en el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e295b-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="e295b-120">Haga clic en el **reproducir** botón para iniciar el modo de reproducción y la experiencia de la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e295b-120">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="e295b-121">Remoting holográfica requiere una conexión rápida de PC y Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="e295b-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="e295b-122">Consulte [holográfica Reproductor Remoting](holographic-remoting-player.md) para obtener detalles completos.</span><span class="sxs-lookup"><span data-stu-id="e295b-122">See [Holographic Remoting Player](holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="e295b-123">Para obtener mejores resultados, asegúrese de que la aplicación establece adecuadamente el [centrarse punto](focus-point-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="e295b-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="e295b-124">Esto ayuda a holográfica Remoting para adaptar mejor la escena a la latencia de la conexión inalámbrica.</span><span class="sxs-lookup"><span data-stu-id="e295b-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="e295b-125">Vea también</span><span class="sxs-lookup"><span data-stu-id="e295b-125">See Also</span></span>
* [<span data-ttu-id="e295b-126">Reproductor de Remoting holográfica</span><span class="sxs-lookup"><span data-stu-id="e295b-126">Holographic Remoting Player</span></span>](holographic-remoting-player.md)
