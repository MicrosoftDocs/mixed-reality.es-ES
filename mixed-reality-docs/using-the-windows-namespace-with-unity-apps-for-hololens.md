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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Uso del espacio de nombres de Windows con aplicaciones de Unity para HoloLens

En esta página se describe cómo hacer uso de las API de WinRT en el proyecto de Unity para HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Inclusión condicional de llamadas API de WinRT

Las API de WinRT se pueden aprovechar para los proyectos de Unity creados para el Plataforma universal de Windows y la plataforma Xbox One; cualquier código que escriba en scripts de Unity que tengan como destino las API de WinRT debe incluirse condicionalmente solo para esas compilaciones. 

Esto puede hacerse a través de dos pasos en Unity:
1) El nivel de compatibilidad de API debe establecerse en **.net 4,6** o **.net Standard 2,0** en la configuración del reproductor.
    - **Editar** >  >    configuración de proyecto nivel de compatibilidad de API de configuración del reproductor en .net 4,6 o .net Standard 2,0 >  > 
2) La Directiva de preprocesador **ENABLE_WINMD_SUPPORT** debe estar encapsulada en torno a cualquier código aprovechado por WinRT

El siguiente fragmento de código procede de la página manual de [Unity para plataforma universal de Windows: API de WinRT C# en](http://docs.unity3d.com/Manual/windowsstore-scripts.html)scripts. En este ejemplo, se devuelve un identificador de anuncio, pero solo en las compilaciones de UWP y Xbox One:

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

Al hacer doble clic en un script en el editor de Unity, se iniciará el script de forma predeterminada en un proyecto de editor. Parece que las API de WinRT son desconocidas porque el proyecto de Visual Studio no hace referencia al Windows Runtime. Además, la directiva **ENALBE_WINMD_SUPPORT** estará sin definir y cualquier código ajustado *#if* se omitirá hasta que compile el proyecto en una solución de Visual Studio para UWP.

## <a name="see-also"></a>Vea también
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Runtime admite Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)