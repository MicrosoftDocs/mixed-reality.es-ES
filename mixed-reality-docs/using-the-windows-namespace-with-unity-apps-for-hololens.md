---
title: Usar el espacio de nombres de Windows con las aplicaciones de Unity para HoloLens
description: Explica cómo utilizar WinRT APIs en el proyecto de Unity para HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Tutorial de Unity, WinRT, windows mixed reality, API,
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599868"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="f97fe-104">Usar el espacio de nombres de Windows con las aplicaciones de Unity para HoloLens</span><span class="sxs-lookup"><span data-stu-id="f97fe-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="f97fe-105">Esta página describe cómo utilizar WinRT APIs en el proyecto de Unity para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f97fe-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="f97fe-106">Condicionalmente incluyen llamadas a API de WinRT</span><span class="sxs-lookup"><span data-stu-id="f97fe-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="f97fe-107">WinRT APIs solo se usará en las compilaciones de proyecto de Unity que tienen como destino Windows 8, Windows 8.1 o la plataforma Universal de Windows; cualquier código que se escribe en los scripts de Unity que tiene como destino WinRT APIs debe incluirse condicionalmente para solo las compilaciones.</span><span class="sxs-lookup"><span data-stu-id="f97fe-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="f97fe-108">Esto se realiza mediante las definiciones del preprocesador NETFX_CORE o WINDOWS_UWP.</span><span class="sxs-lookup"><span data-stu-id="f97fe-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="f97fe-109">Esta regla se aplica al uso de instrucciones, así como otro código.</span><span class="sxs-lookup"><span data-stu-id="f97fe-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="f97fe-110">El fragmento de código siguiente procede de la página del manual de Unity para [plataforma Universal de Windows: API de WinRT en C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="f97fe-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="f97fe-111">En este ejemplo, un Id. de publicidad se devuelve, pero solo en Windows 8.0 o superior destino compilaciones:</span><span class="sxs-lookup"><span data-stu-id="f97fe-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="f97fe-112">Editar los scripts en un Unity C# proyecto</span><span class="sxs-lookup"><span data-stu-id="f97fe-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="f97fe-113">Cuando hace doble clic en una secuencia de comandos en el editor de Unity, iniciará de forma predeterminada el script en un proyecto del editor.</span><span class="sxs-lookup"><span data-stu-id="f97fe-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="f97fe-114">Las APIs WinRT aparecerán desconocido por dos motivos: NETFX_CORE no está definido en este entorno, y el proyecto no hace referencia el tiempo de ejecución de Windows.</span><span class="sxs-lookup"><span data-stu-id="f97fe-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="f97fe-115">Si usas el [recomienda exportación y compila la configuración](exporting-and-building-a-unity-visual-studio-solution.md)y editar los scripts en el proyecto en su lugar, definirá NETFX_CORE y también incluyen una referencia al tiempo de ejecución de Windows; con esta configuración en su lugar, será WinRT APIs está disponible para IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="f97fe-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="f97fe-116">Tenga en cuenta que el Unity C# proyecto también puede utilizarse para depurar a través de las secuencias de comandos con F5 en Visual Studio de depuración remota.</span><span class="sxs-lookup"><span data-stu-id="f97fe-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="f97fe-117">Si no ve IntelliSense funciona la primera vez que abra el Unity C# del proyecto, cierre el proyecto y vuelva a abrirlo.</span><span class="sxs-lookup"><span data-stu-id="f97fe-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="f97fe-118">IntelliSense debería empezar a trabajar.</span><span class="sxs-lookup"><span data-stu-id="f97fe-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="f97fe-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="f97fe-119">See also</span></span>
* [<span data-ttu-id="f97fe-120">Exportar y creación de una solución de Visual Studio de Unity</span><span class="sxs-lookup"><span data-stu-id="f97fe-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
