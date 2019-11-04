---
title: API de WinRT con Unity para HoloLens
description: Explica cómo hacer uso de las API de WinRT (el espacio de nombres de Windows) en el proyecto de Unity para HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, tutorial
ms.openlocfilehash: 73764d191813f6dcae750e74ce3181af987c9e0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437232"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>API de WinRT con Unity para HoloLens

En esta página se describe cómo hacer uso de las API de WinRT en el proyecto de Unity para HoloLens.

## <a name="mixed-reality-apis"></a>API de realidad mixta

Un subconjunto centrado en la realidad mixta del Windows SDK se ha puesto a disposición en una proyección compatible con .NET Standard 2,0, que puede usar en el proyecto sin las directivas de preprocesador. Esto incluye la mayoría de las API de los espacios de nombres Windows. imception y Windows. UI. Input. Spatial, y puede expandirse para incluir más API en el futuro. Las API proyectadas se pueden usar mientras se ejecutan en el editor, lo que permite el uso del [modo de reproducción](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode). Para usar esta proyección, realice las siguientes modificaciones en el proyecto:

1) Agregue una referencia al paquete de Nuget [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) mediante [Nuget para Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Referencias de prefijo al espacio de nombres `Windows` con `Microsoft.`:
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Reemplace las conversiones de puntero nativas por `FromNativePtr`:
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Inclusión condicional de llamadas API de WinRT

Como alternativa, se pueden aprovechar las API de WinRT para los proyectos de Unity creados para el Plataforma universal de Windows y la plataforma Xbox One mediante directivas de preprocesador. cualquier código que escriba en scripts de Unity que tengan como destino las API de WinRT debe incluirse condicionalmente solo para esas compilaciones. 

Esto puede hacerse a través de dos pasos en Unity:
1) El nivel de compatibilidad de API debe establecerse en **.net 4,6** o **.net Standard 2,0** en la configuración del reproductor.
    - **Edite** > **configuración del proyecto** > **Player** > **Configuration** > nivel de **compatibilidad de API** a **.net 4,6** o **.net Standard 2,0**
2) La Directiva de preprocesador **ENABLE_WINMD_SUPPORT** debe estar encapsulada en torno a cualquier código aprovechado por WinRT

El siguiente fragmento de código procede de la página manual de Unity para [plataforma universal de Windows: API C# de WinRT en scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html). En este ejemplo, se devuelve un identificador de anuncio, pero solo en las compilaciones de UWP y Xbox One:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Editar los scripts en un C# proyecto de Unity

Al hacer doble clic en un script en el editor de Unity, se iniciará el script de forma predeterminada en un proyecto de editor. Parece que las API de WinRT son desconocidas porque el proyecto de Visual Studio no hace referencia al Windows Runtime. Además, la directiva **ENABLE_WINMD_SUPPORT** estará sin definir y cualquier código ajustado *#if* se omitirá hasta que compile el proyecto en una solución de Visual Studio para UWP.

## <a name="see-also"></a>Consulta también
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Runtime admite Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
