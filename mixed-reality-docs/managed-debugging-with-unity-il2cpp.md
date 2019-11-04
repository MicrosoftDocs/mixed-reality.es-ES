---
title: Depuración administrada con Unity IL2CPP
description: En este artículo se explica cómo ejecutar un depurador administrado en el proyecto de IL2CPP para UWP de Unity.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, depuración, il2cpp
ms.openlocfilehash: fd09c3ca1bd410c56e46eb8e8815742f87482d08
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439636"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="be66d-104">Depuración administrada con Unity IL2CPP</span><span class="sxs-lookup"><span data-stu-id="be66d-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="be66d-105">Siga estos pasos para asociar un depurador administrado a la compilación de UWP de Unity IL2CPP.</span><span class="sxs-lookup"><span data-stu-id="be66d-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="be66d-106">Esta guía se desarrolló originalmente para HoloLens y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="be66d-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="be66d-107">Deberá estar en una red que admita la [multidifusión](https://en.wikipedia.org/wiki/Multicast).</span><span class="sxs-lookup"><span data-stu-id="be66d-107">You will need to be on a network that supports [multicast](https://en.wikipedia.org/wiki/Multicast).</span></span>
1. <span data-ttu-id="be66d-108">Asegúrese de que **InternetClientServer** y **PrivateNetworkClientServer** están protegidos en Unity en las funcionalidades de configuración de publicación de UWP.</span><span class="sxs-lookup"><span data-stu-id="be66d-108">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Funcionalidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="be66d-110">Configurar las opciones de compilación de UWP para Unity:</span><span class="sxs-lookup"><span data-stu-id="be66d-110">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="be66d-111">Compilación de desarrollo</span><span class="sxs-lookup"><span data-stu-id="be66d-111">Development Build</span></span>
    - <span data-ttu-id="be66d-112">Depuración de script</span><span class="sxs-lookup"><span data-stu-id="be66d-112">Script Debugging</span></span>
    - <span data-ttu-id="be66d-113">Esperar al depurador administrado (opcional)</span><span class="sxs-lookup"><span data-stu-id="be66d-113">Wait for Managed Debugger (optional)</span></span>

    ![Configuración de compilación de UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="be66d-115">Compilar en Unity.</span><span class="sxs-lookup"><span data-stu-id="be66d-115">Build in Unity.</span></span>
1. <span data-ttu-id="be66d-116">Compile e implemente desde la solución de Visual Studio en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="be66d-116">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="be66d-117">Debe compilar con las configuraciones de **depuración** o de **lanzamiento** .</span><span class="sxs-lookup"><span data-stu-id="be66d-117">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="be66d-118">La configuración **maestra** deshabilita el generador de perfiles de Unity y puede impedir la depuración óptima.</span><span class="sxs-lookup"><span data-stu-id="be66d-118">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="be66d-119">Opcionalmente, compruebe **Internet (cliente & servidor)** y **redes privadas (servidor de & de cliente)** en la lista de capacidades de Package. appxmanifest en la solución.</span><span class="sxs-lookup"><span data-stu-id="be66d-119">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="be66d-120">Inicie la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="be66d-120">Start the app on your device.</span></span> <span data-ttu-id="be66d-121">Asegúrese de que el dispositivo está conectado a la misma red que el equipo.</span><span class="sxs-lookup"><span data-stu-id="be66d-121">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="be66d-122">Asegúrese de que el dispositivo **no está** conectado al equipo a través de USB.</span><span class="sxs-lookup"><span data-stu-id="be66d-122">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="be66d-123">Vaya a la solución de Visual Studio que se crea al hacer doble clic en un script en Unity, donde puede ver y editar C# los scripts.</span><span class="sxs-lookup"><span data-stu-id="be66d-123">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="be66d-124">Debug: > adjuntar el depurador de Unity.</span><span class="sxs-lookup"><span data-stu-id="be66d-124">Debug -> Attach Unity Debugger.</span></span>

    ![Adjuntar el depurador de Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="be66d-126">Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntarlo.</span><span class="sxs-lookup"><span data-stu-id="be66d-126">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
