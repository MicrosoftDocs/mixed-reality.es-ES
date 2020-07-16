---
title: Implementación en el dispositivo en Unreal
description: Guía para la implementación en el dispositivo de un equipo inreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, equipo, documentación
appliesto:
- HoloLens 2
ms.openlocfilehash: 2d0cd67db79c1970695334d826fbbaf0f2f92ec0
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408183"
---
# <a name="deploy-to-device-in-unreal"></a>Implementación en el dispositivo en Unreal

## <a name="overview"></a>Introducción
Hay dos maneras de implementar una aplicación no real en HoloLens 2: 
* Directamente desde el editor desareal
* Como un paquete cargado a través del portal de dispositivos

Ambas opciones requieren la configuración de HoloLens para usar el portal de [dispositivos](using-the-windows-device-portal.md) para el desarrollo. 

## <a name="deploying-to-device-from-the-unreal-editor"></a>Implementación en el dispositivo desde el editor desareal

1. Haga clic en la flecha desplegable situada junto al botón **iniciar** . Inicialmente, la opción de dispositivo HoloLens estará atenuada.

![Iniciar opciones de lista desplegable](images/unreal/launch-dropdown.png)

2. Abra el **Device Manager**. Tenga en cuenta que HoloLens no aparecerá automáticamente en la lista de dispositivos.

3. Expanda la sección **Agregar un dispositivo** que no está en la lista.

4. Seleccione **HoloLens** como **plataforma**.

5. Escriba la dirección IP y la información de puerto de los dispositivos separadas por un signo de dos puntos como identificador de dispositivo. Por ejemplo, "127.0.0.1:10080" (cuando se conecta a través de USB). Use las credenciales de nombre de usuario y contraseña del portal de dispositivos.

6. Presione **Agregar** y cierre el administrador de dispositivos. 
    * En el caso de un error (por ejemplo, una dirección incorrecta, un nombre de usuario o una contraseña), se imprimirá un mensaje en el registro de salida.

![Agregar un dispositivo que no está en la lista](images/unreal/add-unlisted-device.png)

7. Haga clic en la flecha desplegable situada junto al botón **Launch (iniciar** ) de nuevo; esta vez debería ver el dispositivo HoloLens que acaba de agregar. Seleccione el dispositivo HoloLens para compilar e implementar en HoloLens. 

>[!NOTE]
>La compilación para el dispositivo puede implicar la recompilación de los sombreadores (especialmente en la primera ejecución). esto puede tardar unos minutos. No deje que el dispositivo pase a suspensión hasta que la aplicación se esté ejecutando (es posible que tenga que hacerlo). De lo contrario, se producirá un error de compilación del sombreador.

## <a name="deploying-to-device-via-device-portal"></a>Implementación en el dispositivo a través del portal de dispositivos

Puede encontrar instrucciones detalladas sobre cómo [empaquetar e implementar una aplicación](unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) en la última sección del introducción con una serie de tutoriales inreal.
