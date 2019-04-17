---
title: Modo de investigación de HoloLens
description: Utiliza el modo de investigación en HoloLens, una aplicación puede tener acceso a secuencias de sensor de clave de dispositivo (profundidad, el entorno de seguimiento y reflexión de infrarrojos).
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: modo de investigación, cv, rs4, visión de equipo, la investigación, HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597508"
---
# <a name="hololens-research-mode"></a>Modo de investigación de HoloLens

> [!NOTE]
> Esta característica se agregó como parte de la [Windows 10 de abril de 2018 Update](release-notes-april-2018.md) para HoloLens y no está disponible en versiones anteriores.

Modo de investigación es una nueva funcionalidad de HoloLens que proporciona acceso a las aplicaciones a los sensores de clave en el dispositivo. Entre ellos se incluyen los siguientes:
- Los cuatro cámaras utilizadas por el sistema para la compilación de mapa y seguimiento principal de seguimiento del entorno.
- Dos versiones de los datos de cámara de profundidad, uno para la alta frecuencia (30 FPS) cerca de la profundidad de detección usados en la mano de seguimiento y otro para frecuencia inferior (1 FPS) lejano profundidad detección, se usan actualmente mediante la asignación espacial,
- Dos versiones de un flujo de reflexión de infrarrojos, usada por el HoloLens para calcular la profundidad, pero valioso en sí misma como estas imágenes son iluminada desde el HoloLens y razonablemente se ven afectados por esta luz ambiente.

![Captura de pantalla de aplicación de modo de investigación](images/sensor-stream-viewer.jpg)<br>
*Una captura de realidad mixta de una aplicación de prueba que muestra las secuencias de ocho sensores disponibles en el modo de investigación*

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Modo de investigación</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a>Antes de usar el modo de investigación

También se denomina modo de investigación: está destinado a los investigadores industriales y académicos probando nuevas ideas en los campos de Computer Vision y robótica.  Modo de investigación no está diseñado para aplicaciones que se implementará en una empresa o están disponibles en la Microsoft Store. La razón de esto es que el modo de investigación reduce la seguridad del dispositivo y consume mucho más energía de batería que el funcionamiento normal. Microsoft no está confirmando que admiten este modo en todos los futuros dispositivos. Por lo tanto, se recomienda que usarla para desarrollar y probar nuevas ideas; Sin embargo, no podrá implementar ampliamente las aplicaciones que utiliza el modo de investigación o tienen cualquier garantía de que seguirán funcionando en hardware en el futuro.

## <a name="enabling-research-mode"></a>Habilitar el modo de investigación

Modo de investigación es un secundario del modo de programador. Primero debe habilitar el modo de desarrollador en la aplicación de configuración (**configuración > actualización y seguridad > para los desarrolladores**):

1. Establezca "Usar características del desarrollador" en **en**
2. Establece la opción "Habilitar el Portal del dispositivo" en **en**

A continuación, mediante un explorador web que está conectado a la misma red Wi-Fi como su HoloLens, vaya a la dirección IP de su HoloLens (obtenido a través de **configuración > red e Internet > Wi-Fi > Propiedades de Hardware**). Se trata de la [Device Portal](using-the-windows-device-portal.md), y encontrará una página de "Modo de investigación" en la sección "Sistema" del portal:

![Ficha de modo de investigación del Portal de dispositivo HoloLens](images/ResearchModeDevPortal.png)<br>
*Modo de investigación en el Portal de dispositivo HoloLens*

Después de seleccionar **permitir el acceso a secuencias de sensor**, tendrá que reiniciar HoloLens. Puede hacerlo desde el Portal de dispositivo, en el elemento de menú "Power" en la parte superior de la página.

Una vez que se ha reiniciado el dispositivo, las aplicaciones que se han cargado a través del Portal de dispositivos deben ser capaz de obtener acceso a secuencias de modo de investigación.

## <a name="using-sensor-data-in-your-apps"></a>Uso de datos del sensor en las aplicaciones

Las aplicaciones pueden tener acceso a datos del sensor de la secuencia abriendo [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) secuencias de exactamente la misma manera que acceden a la secuencia de la cámara de fotografías y vídeo. 

Todas las API que funcionan para el desarrollo de HoloLens también están disponibles en el modo de investigación. En concreto, la aplicación puede saber exactamente donde HoloLens de 6GDL espacio en cada momento de captura de fotogramas del sensor.

Aplicaciones de ejemplo que muestra cómo tener acceso a los distintos flujos de modo Research, cómo usar las funciones intrínsecas y extrinsics y cómo grabar secuencias están disponibles en el [repositorio de HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Problemas conocidos

Consulte la [issue tracker de](https://github.com/Microsoft/HololensForCV/issues) en el repositorio HoloLensForCV.

## <a name="see-also"></a>Vea también

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repositorio de HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)
* [Uso de la Windows Device Portal](using-the-windows-device-portal.md)
