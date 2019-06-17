---
title: Depuración con Unity IL2CPP administrada
description: Este artículo describe cómo ejecutar a un depurador administrado en su proyecto Unity IL2CPP UWP.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: Unity, visual studio, depuración, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148860"
---
# <a name="managed-debugging-with-unity-il2cpp"></a><span data-ttu-id="12a92-104">Depuración con Unity IL2CPP administrada</span><span class="sxs-lookup"><span data-stu-id="12a92-104">Managed debugging with Unity IL2CPP</span></span>

<span data-ttu-id="12a92-105">Siga estos pasos para asociar a un depurador administrado a la compilación de Unity IL2CPP UWP.</span><span class="sxs-lookup"><span data-stu-id="12a92-105">Follow these steps to attach a managed debugger to your Unity IL2CPP UWP build.</span></span> <span data-ttu-id="12a92-106">Esta guía se desarrolló originalmente para HoloLens y HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="12a92-106">This guide was originally developed for HoloLens and HoloLens 2.</span></span>

1. <span data-ttu-id="12a92-107">Asegúrese de que **InternetClientServer** y **PrivateNetworkClientServer** se comprueban en Unity en las funcionalidades de configuración de publicación de UWP.</span><span class="sxs-lookup"><span data-stu-id="12a92-107">Ensure that **InternetClientServer** and **PrivateNetworkClientServer** are checked in Unity under the UWP Publishing Settings Capabilities.</span></span>

    ![Capacidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

1. <span data-ttu-id="12a92-109">Configure las opciones de compilación de Unity UWP:</span><span class="sxs-lookup"><span data-stu-id="12a92-109">Configure the Unity UWP build settings:</span></span>
    - <span data-ttu-id="12a92-110">Compilación de desarrollo</span><span class="sxs-lookup"><span data-stu-id="12a92-110">Development Build</span></span>
    - <span data-ttu-id="12a92-111">Depuración de script</span><span class="sxs-lookup"><span data-stu-id="12a92-111">Script Debugging</span></span>
    - <span data-ttu-id="12a92-112">Espere de depurador administrado (opcional)</span><span class="sxs-lookup"><span data-stu-id="12a92-112">Wait for Managed Debugger (optional)</span></span>

    ![Configuración de compilación para UWP](images/il2cpp-debugging-build.png)

1. <span data-ttu-id="12a92-114">Compilación de Unity.</span><span class="sxs-lookup"><span data-stu-id="12a92-114">Build in Unity.</span></span>
1. <span data-ttu-id="12a92-115">Compilar e implementar de la solución de Visual Studio en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="12a92-115">Build and deploy from the Visual Studio solution to your device.</span></span> <span data-ttu-id="12a92-116">Debe compilar con la **depurar** o **versión** configuraciones.</span><span class="sxs-lookup"><span data-stu-id="12a92-116">You should build with the **Debug** or **Release** configurations.</span></span> <span data-ttu-id="12a92-117">El **Master** configuración deshabilita el generador de perfiles de Unity y puede impedir la depuración óptima.</span><span class="sxs-lookup"><span data-stu-id="12a92-117">The **Master** configuration disables the Unity profiler and can prevent optimal debugging.</span></span> <span data-ttu-id="12a92-118">Si lo desea, compruebe **Internet (cliente y servidor)** y **redes privadas (cliente y servidor)** en la lista de capacidades en Package.appxmanifest en la solución.</span><span class="sxs-lookup"><span data-stu-id="12a92-118">Optionally, verify **Internet (Client & Server)** and **Private Networks (Client & Server)** in the capabilities list in Package.appxmanifest in the solution.</span></span>
1. <span data-ttu-id="12a92-119">Inicie la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="12a92-119">Start the app on your device.</span></span> <span data-ttu-id="12a92-120">Asegúrese de que el dispositivo está conectado a la misma red que su PC.</span><span class="sxs-lookup"><span data-stu-id="12a92-120">Make sure your device is connected to the same network as your PC.</span></span>
1. <span data-ttu-id="12a92-121">Asegúrese de que el dispositivo **no** conectado a su equipo a través de USB.</span><span class="sxs-lookup"><span data-stu-id="12a92-121">Make sure the device **is not** connected to your PC via USB.</span></span>
1. <span data-ttu-id="12a92-122">Vaya a la solución de Visual Studio que se crea al hacer doble clic en una secuencia de comandos en Unity, donde puede ver y editar su C# secuencias de comandos.</span><span class="sxs-lookup"><span data-stu-id="12a92-122">Go to the Visual Studio solution that's created when you double click a script in Unity, where you can view and edit your C# scripts.</span></span>
1. <span data-ttu-id="12a92-123">Depurar -> adjuntar depurador de Unity.</span><span class="sxs-lookup"><span data-stu-id="12a92-123">Debug -> Attach Unity Debugger.</span></span>

    ![Adjuntar a depurador de Unity](images/il2cpp-debugging-attach.png)

1. <span data-ttu-id="12a92-125">Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntar.</span><span class="sxs-lookup"><span data-stu-id="12a92-125">Select your device in the list and click "OK" to attach.</span></span>

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
