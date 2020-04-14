---
title: API de WinRT con Unity para HoloLens
description: Explica cómo hacer uso de las API de WinRT (el espacio de nombres de Windows) en el proyecto de Unity para HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, tutorial
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277993"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="b281a-104">API de WinRT con Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="b281a-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="b281a-105">En esta página se describe cómo hacer uso de las API de WinRT en el proyecto de Unity para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b281a-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="b281a-106">API de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b281a-106">Mixed Reality APIs</span></span>

<span data-ttu-id="b281a-107">Un subconjunto centrado en la realidad mixta del Windows SDK se ha puesto a disposición en una proyección compatible con .NET Standard 2,0, que puede usar en el proyecto sin las directivas de preprocesador.</span><span class="sxs-lookup"><span data-stu-id="b281a-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="b281a-108">Esto incluye la mayoría de las API de los espacios de nombres Windows. imception y Windows. UI. Input. Spatial, y puede expandirse para incluir más API en el futuro.</span><span class="sxs-lookup"><span data-stu-id="b281a-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="b281a-109">Las API proyectadas se pueden usar mientras se ejecutan en el editor, lo que permite el uso del [modo de reproducción](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span><span class="sxs-lookup"><span data-stu-id="b281a-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="b281a-110">Para usar esta proyección, realice las siguientes modificaciones en el proyecto:</span><span class="sxs-lookup"><span data-stu-id="b281a-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="b281a-111">Agregue una referencia al paquete de Nuget [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) mediante [Nuget para Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span><span class="sxs-lookup"><span data-stu-id="b281a-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="b281a-112">Referencias de prefijo al espacio de nombres `Windows` con `Microsoft.`:</span><span class="sxs-lookup"><span data-stu-id="b281a-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="b281a-113">Reemplace las conversiones de puntero nativas por `FromNativePtr`:</span><span class="sxs-lookup"><span data-stu-id="b281a-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="b281a-114">Inclusión condicional de llamadas API de WinRT</span><span class="sxs-lookup"><span data-stu-id="b281a-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="b281a-115">Como alternativa, se pueden aprovechar las API de WinRT para los proyectos de Unity creados para el Plataforma universal de Windows y la plataforma Xbox One mediante directivas de preprocesador. cualquier código que escriba en scripts de Unity que tengan como destino las API de WinRT debe incluirse condicionalmente solo para esas compilaciones.</span><span class="sxs-lookup"><span data-stu-id="b281a-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="b281a-116">Esto puede hacerse a través de dos pasos en Unity:</span><span class="sxs-lookup"><span data-stu-id="b281a-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="b281a-117">El nivel de compatibilidad de API debe establecerse en **.net 4,6** o **.net Standard 2,0** en la configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="b281a-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="b281a-118">**Edite** > **configuración del proyecto** > **Player** > **Configuration** > nivel de **compatibilidad de API** a **.net 4,6** o **.net Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="b281a-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="b281a-119">La Directiva de preprocesador **ENABLE_WINMD_SUPPORT** debe ajustarse alrededor de cualquier código aprovechado por WinRT</span><span class="sxs-lookup"><span data-stu-id="b281a-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="b281a-120">El siguiente fragmento de código procede de la página manual de Unity para [plataforma universal de Windows: API C# de WinRT en scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="b281a-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="b281a-121">En este ejemplo, se devuelve un identificador de anuncio, pero solo en las compilaciones de UWP y Xbox One:</span><span class="sxs-lookup"><span data-stu-id="b281a-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="b281a-122">Editar los scripts en un C# proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="b281a-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="b281a-123">Al hacer doble clic en un script en el editor de Unity, se iniciará el script de forma predeterminada en un proyecto de editor.</span><span class="sxs-lookup"><span data-stu-id="b281a-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="b281a-124">Parece que las API de WinRT son desconocidas porque el proyecto de Visual Studio no hace referencia al Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="b281a-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="b281a-125">Además, la Directiva de **ENABLE_WINMD_SUPPORT** será undefined y cualquier código ajustado *#if* se omitirá hasta que compile el proyecto en una solución de Visual Studio para UWP.</span><span class="sxs-lookup"><span data-stu-id="b281a-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="b281a-126">Vea también</span><span class="sxs-lookup"><span data-stu-id="b281a-126">See also</span></span>
* [<span data-ttu-id="b281a-127">Exportación y creación de una solución de Visual Studio para Unity</span><span class="sxs-lookup"><span data-stu-id="b281a-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="b281a-128">Windows Runtime admite Unity</span><span class="sxs-lookup"><span data-stu-id="b281a-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
