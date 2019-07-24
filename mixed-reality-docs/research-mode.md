---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829934"
---
# <a name="hololens-research-mode"></a>Modo de investigación de HoloLens

> [!NOTE]
> Esta característica se agregó como parte de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md) para HoloLens y no está disponible en versiones anteriores.

El modo de investigación es una nueva funcionalidad de HoloLens que proporciona acceso a las aplicaciones a los sensores de claves en el dispositivo. Entre ellas se incluyen las siguientes:
- Las cuatro cámaras de seguimiento del entorno utilizadas por el sistema para la creación de mapas y el seguimiento de encabezados.
- Dos versiones de los datos de la cámara de profundidad: una para la detección en profundidad de alta frecuencia (30 FPS), que se usa habitualmente en el seguimiento de la mano, y la otra para la detección de la profundidad de baja frecuencia (1 FPS), usada actualmente por la asignación espacial,
- Dos versiones de una secuencia de reflexión de INFRARROJOs, que usa HoloLens para calcular la profundidad, pero valiosa en su propio derecho, ya que estas imágenes se iluminan desde HoloLens y razonablemente no se ven afectadas por la luz ambiente.

![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)<br>
*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Modo de investigación</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>Antes de usar el modo de investigación

El modo de investigación está bien denominado: está pensado para los investigadores académicos e industriales que prueban nuevas ideas en los campos de Computer Vision y robótica.  El modo de investigación no está pensado para las aplicaciones que se implementarán en una empresa o que estarán disponibles en el Microsoft Store. El motivo es que el modo de investigación reduce la seguridad del dispositivo y consume mucha más energía de la batería que el funcionamiento normal. Microsoft no se compromete a admitir este modo en ningún dispositivo futuro. Por lo tanto, se recomienda utilizarlo para desarrollar y probar nuevas ideas; sin embargo, no podrá implementar ampliamente aplicaciones que usen el modo de investigación ni tener ninguna garantía de que seguirá funcionando en hardware futuro.

## <a name="enabling-research-mode"></a>Habilitar el modo de investigación

El modo de investigación es un submodo de modo de programador. En primer lugar, debe habilitar el modo de Desarrollador en la aplicación de configuración (**configuración > actualizar & > de seguridad para desarrolladores**):

1. Establezca "usar características para desarrolladores" **en activado** .
2. Establezca "habilitar portal de dispositivos" **en activado** .

A continuación, use un explorador Web que esté conectado a la misma red Wi-Fi que HoloLens, vaya a la dirección IP de HoloLens (obtenida a través de la **configuración > red & las propiedades de hardware de Internet > Wi-Fi >** ). Este es el [portal de dispositivos](using-the-windows-device-portal.md)y encontrará una página "modo de investigación" en la sección "sistema" del portal:

![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)<br>
*Modo de investigación en el portal de dispositivos de HoloLens*

Después de seleccionar **permitir el acceso a las secuencias del sensor**, deberá reiniciar HoloLens. Puede hacerlo desde el portal de dispositivos, en el elemento de menú "energía" en la parte superior de la página.

Una vez que se ha reiniciado el dispositivo, las aplicaciones que se han cargado a través del portal de dispositivos deben poder acceder a los flujos del modo de investigación.

## <a name="using-sensor-data-in-your-apps"></a>Uso de datos de sensor en las aplicaciones

Las aplicaciones pueden acceder a los datos de la secuencia del sensor abriendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) secuencias exactamente del mismo modo en que acceden a la secuencia de la cámara de fotos o vídeos. 

Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación. En concreto, la aplicación puede saber con exactitud si HoloLens está en el espacio de 6DoF en cada tiempo de captura de fotogramas del sensor.

Las aplicaciones de ejemplo que muestran cómo se obtiene acceso a los distintos flujos del modo de investigación, cómo usar intrínsecos y extrinsics y cómo grabar flujos están disponibles en el [repositorio de github de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Problemas conocidos

Vea el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV.

## <a name="see-also"></a>Vea también

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repositorio de GitHub de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)
