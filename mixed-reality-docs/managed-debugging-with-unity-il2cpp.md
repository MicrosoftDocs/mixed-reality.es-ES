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
# <a name="managed-debugging-with-unity-il2cpp"></a>Depuración administrada con Unity IL2CPP

Siga estos pasos para asociar un depurador administrado a la compilación de UWP de Unity IL2CPP. Esta guía se desarrolló originalmente para HoloLens y HoloLens 2.

1. Deberá estar en una red que admita la [multidifusión](https://en.wikipedia.org/wiki/Multicast).
1. Asegúrese de que **InternetClientServer** y **PrivateNetworkClientServer** están protegidos en Unity en las funcionalidades de configuración de publicación de UWP.

    ![Funcionalidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

1. Configurar las opciones de compilación de UWP para Unity:
    - Compilación de desarrollo
    - Depuración de script
    - Esperar al depurador administrado (opcional)

    ![Configuración de compilación de UWP](images/il2cpp-debugging-build.png)

1. Compilar en Unity.
1. Compile e implemente desde la solución de Visual Studio en el dispositivo. Debe compilar con las configuraciones de **depuración** o de **lanzamiento** . La configuración **maestra** deshabilita el generador de perfiles de Unity y puede impedir la depuración óptima. Opcionalmente, compruebe **Internet (cliente & servidor)** y **redes privadas (servidor de & de cliente)** en la lista de capacidades de Package. appxmanifest en la solución.
1. Inicie la aplicación en el dispositivo. Asegúrese de que el dispositivo está conectado a la misma red que el equipo.
1. Asegúrese de que el dispositivo **no está** conectado al equipo a través de USB.
1. Vaya a la solución de Visual Studio que se crea al hacer doble clic en un script en Unity, donde puede ver y editar C# los scripts.
1. Debug: > adjuntar el depurador de Unity.

    ![Adjuntar el depurador de Unity](images/il2cpp-debugging-attach.png)

1. Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntarlo.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
