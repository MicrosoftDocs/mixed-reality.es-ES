---
title: Uso del espacio de nombres de Windows con aplicaciones de Unity para HoloLens
description: Explica cómo hacer uso de las API de WinRT en el proyecto de Unity para HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, tutorial
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548737"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="ea656-104">Uso del espacio de nombres de Windows con aplicaciones de Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="ea656-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="ea656-105">En esta página se describe cómo hacer uso de las API de WinRT en el proyecto de Unity para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ea656-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="ea656-106">Inclusión condicional de llamadas API de WinRT</span><span class="sxs-lookup"><span data-stu-id="ea656-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="ea656-107">Las API de WinRT se pueden aprovechar para los proyectos de Unity creados para el Plataforma universal de Windows y la plataforma Xbox One; cualquier código que escriba en scripts de Unity que tengan como destino las API de WinRT debe incluirse condicionalmente solo para esas compilaciones.</span><span class="sxs-lookup"><span data-stu-id="ea656-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="ea656-108">Esto puede hacerse a través de dos pasos en Unity:</span><span class="sxs-lookup"><span data-stu-id="ea656-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="ea656-109">El nivel de compatibilidad de API debe establecerse en **.net 4,6** o **.net Standard 2,0** en la configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="ea656-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="ea656-110">**Editar** >  >    configuración de proyecto nivel de compatibilidad de API de configuración del reproductor en .net 4,6 o .net Standard 2,0 >  > </span><span class="sxs-lookup"><span data-stu-id="ea656-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="ea656-111">La Directiva de preprocesador **ENABLE_WINMD_SUPPORT** debe estar encapsulada en torno a cualquier código aprovechado por WinRT</span><span class="sxs-lookup"><span data-stu-id="ea656-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="ea656-112">El siguiente fragmento de código procede de la página manual de [Unity para plataforma universal de Windows: API de WinRT C# en](http://docs.unity3d.com/Manual/windowsstore-scripts.html)scripts.</span><span class="sxs-lookup"><span data-stu-id="ea656-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="ea656-113">En este ejemplo, se devuelve un identificador de anuncio, pero solo en las compilaciones de UWP y Xbox One:</span><span class="sxs-lookup"><span data-stu-id="ea656-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="ea656-114">Editar los scripts en un C# proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ea656-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="ea656-115">Al hacer doble clic en un script en el editor de Unity, se iniciará el script de forma predeterminada en un proyecto de editor.</span><span class="sxs-lookup"><span data-stu-id="ea656-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="ea656-116">Parece que las API de WinRT son desconocidas porque el proyecto de Visual Studio no hace referencia al Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="ea656-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="ea656-117">Además, la directiva **ENALBE_WINMD_SUPPORT** estará sin definir y cualquier código ajustado *#if* se omitirá hasta que compile el proyecto en una solución de Visual Studio para UWP.</span><span class="sxs-lookup"><span data-stu-id="ea656-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea656-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="ea656-118">See also</span></span>
* [<span data-ttu-id="ea656-119">Exportación y creación de una solución de Visual Studio para Unity</span><span class="sxs-lookup"><span data-stu-id="ea656-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="ea656-120">Windows Runtime admite Unity</span><span class="sxs-lookup"><span data-stu-id="ea656-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)