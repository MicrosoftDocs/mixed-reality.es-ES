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
# <a name="managed-debugging-with-unity-il2cpp"></a>Depuración con Unity IL2CPP administrada

Siga estos pasos para asociar a un depurador administrado a la compilación de Unity IL2CPP UWP. Esta guía se desarrolló originalmente para HoloLens y HoloLens 2.

1. Asegúrese de que **InternetClientServer** y **PrivateNetworkClientServer** se comprueban en Unity en las funcionalidades de configuración de publicación de UWP.

    ![Capacidades de configuración de publicación de UWP](images/il2cpp-debugging-capabilities.png)

1. Configure las opciones de compilación de Unity UWP:
    - Compilación de desarrollo
    - Depuración de script
    - Espere de depurador administrado (opcional)

    ![Configuración de compilación para UWP](images/il2cpp-debugging-build.png)

1. Compilación de Unity.
1. Compilar e implementar de la solución de Visual Studio en el dispositivo. Debe compilar con la **depurar** o **versión** configuraciones. El **Master** configuración deshabilita el generador de perfiles de Unity y puede impedir la depuración óptima. Si lo desea, compruebe **Internet (cliente y servidor)** y **redes privadas (cliente y servidor)** en la lista de capacidades en Package.appxmanifest en la solución.
1. Inicie la aplicación en el dispositivo. Asegúrese de que el dispositivo está conectado a la misma red que su PC.
1. Asegúrese de que el dispositivo **no** conectado a su equipo a través de USB.
1. Vaya a la solución de Visual Studio que se crea al hacer doble clic en una secuencia de comandos en Unity, donde puede ver y editar su C# secuencias de comandos.
1. Depurar -> adjuntar depurador de Unity.

    ![Adjuntar a depurador de Unity](images/il2cpp-debugging-attach.png)

1. Seleccione el dispositivo en la lista y haga clic en "Aceptar" para adjuntar.

    ![Lista de dispositivos](images/il2cpp-debugging-machines.png)
