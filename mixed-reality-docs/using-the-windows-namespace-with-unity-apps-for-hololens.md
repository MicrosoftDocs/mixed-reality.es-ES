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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Usar el espacio de nombres de Windows con las aplicaciones de Unity para HoloLens

Esta página describe cómo utilizar WinRT APIs en el proyecto de Unity para HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Condicionalmente incluyen llamadas a API de WinRT

WinRT APIs solo se usará en las compilaciones de proyecto de Unity que tienen como destino Windows 8, Windows 8.1 o la plataforma Universal de Windows; cualquier código que se escribe en los scripts de Unity que tiene como destino WinRT APIs debe incluirse condicionalmente para solo las compilaciones. Esto se realiza mediante las definiciones del preprocesador NETFX_CORE o WINDOWS_UWP. Esta regla se aplica al uso de instrucciones, así como otro código.

El fragmento de código siguiente procede de la página del manual de Unity para [plataforma Universal de Windows: API de WinRT en C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html). En este ejemplo, un Id. de publicidad se devuelve, pero solo en Windows 8.0 o superior destino compilaciones:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Editar los scripts en un Unity C# proyecto

Cuando hace doble clic en una secuencia de comandos en el editor de Unity, iniciará de forma predeterminada el script en un proyecto del editor. Las APIs WinRT aparecerán desconocido por dos motivos: NETFX_CORE no está definido en este entorno, y el proyecto no hace referencia el tiempo de ejecución de Windows. Si usas el [recomienda exportación y compila la configuración](exporting-and-building-a-unity-visual-studio-solution.md)y editar los scripts en el proyecto en su lugar, definirá NETFX_CORE y también incluyen una referencia al tiempo de ejecución de Windows; con esta configuración en su lugar, será WinRT APIs está disponible para IntelliSense.

Tenga en cuenta que el Unity C# proyecto también puede utilizarse para depurar a través de las secuencias de comandos con F5 en Visual Studio de depuración remota. Si no ve IntelliSense funciona la primera vez que abra el Unity C# del proyecto, cierre el proyecto y vuelva a abrirlo. IntelliSense debería empezar a trabajar.

## <a name="see-also"></a>Vea también
* [Exportar y creación de una solución de Visual Studio de Unity](exporting-and-building-a-unity-visual-studio-solution.md)
