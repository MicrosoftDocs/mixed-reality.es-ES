---
title: Streaming en Unreal
description: Guía de streaming de Unreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, realidad mixta, streaming, PC, control remoto de aplicaciones holográficas, Holographic Remoting Player, documentación
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303536"
---
# <a name="streaming-in-unreal"></a>Streaming en Unreal

## <a name="overview"></a>Introducción
El streaming de un equipo a HoloLens ofrece dos ventajas principales: 
* Permite que la aplicación de realidad mixta aproveche la eficacia de cálculo de los equipos. 
* Ayuda a acelerar el tiempo de iteración de desarrollo. 

Para empezar, deberá descargar [Holographic Remoting Player](holographic-remoting-player.md) en su dispositivo HoloLens. Esta descarga permitirá que la aplicación transmita directamente al reproductor de control remoto en HoloLens desde los orígenes siguientes:

* Editor Unreal Engine
* Ejecutable de Windows empaquetado 

Durante el streaming, tiene acceso prácticamente a las mismas funcionalidades de HoloLens que cuando se ejecuta una aplicación en un dispositivo. Esto incluye [seguimiento de articulación de la mano](unreal-hand-tracking.md) (si utiliza HoloLens 2), [asignación espacial](unreal-spatial-mapping.md) y [delimitadores espaciales](unreal-spatial-anchors.md), pero descarta las características de esta [lista de limitaciones](holographic-remoting-troubleshooting.md). 

> [!NOTE]
> * La calidad de streaming depende en gran medida de la intensidad de la señal de su red WiFi.
> * Todas las funciones se habilitan automáticamente para la aplicación Holographic Remoting Player. Si encuentra una funcionalidad que requiere permiso del usuario (p. ej., el seguimiento ocular) para funcionar en streaming, pero no cuando se ejecuta en el dispositivo, asegúrese de haber habilitado las funcionalidades adecuadas en la configuración del proyecto.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Origen</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1.ª generación</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Cascos envolventes</strong></td>
    </tr>
     <tr>
        <td>Editor de Unreal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Paquetes de Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming desde el editor de Unreal

Como desarrollador, descubrirá que el streaming desde el editor de Unreal a su dispositivo HoloLens proporciona grandes ventajas al realizar pruebas; por ejemplo, ya no tiene que esperar a que la aplicación se compile e implemente antes de probar las actualizaciones.

Puede encontrar instrucciones detalladas sobre el [streaming desde el editor de Unreal](unreal-uxt-ch6.md#device-only-streaming) en la última sección de la Introducción a la serie de tutoriales de Unreal.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming desde un ejecutable de Windows empaquetado

A partir de Unreal 4.25.1, puede transmitir la aplicación a un dispositivo HoloLens 2 desde un ejecutable de Windows empaquetado siguiendo estos pasos: 

1. Vaya a **File > Package Project > Windows** (Archivo > Proyecto de paquete > Windows) en el menú del editor. 
    * Elija una ubicación donde guardar el paquete y haga clic en **Select Folder** (Seleccionar carpeta).

2. Una vez que el paquete termine de compilarse, abra **Holographic Remoting Player** en HoloLens 2 y tome nota de la dirección IP. 
3. Deje **Holographic Remoting Player** abierto y en el símbolo del sistema: 
    * Invoque cd en el directorio local donde guardó el paquete.
    * Escriba el comando siguiente: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> El nombre de la aplicación en la configuración del proyecto debe usarse automáticamente para crear el paquete de Windows. Si por alguna razón son diferentes, utilice el nombre del ejecutable de Windows en el símbolo del sistema.

Presione Entrar y observe que la aplicación inicia el streaming.

## <a name="see-also"></a>Consulta también
* [Historial de versiones de Control remoto de holografías](holographic-remoting-version-history.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Establecimiento de una conexión segura con Control remoto de holografías](holographic-remoting-secure-connection.md)
