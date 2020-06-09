---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens, HoloLens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533107"
---
# <a name="hololens-research-mode"></a>Modo de investigación de HoloLens

## <a name="overview"></a>Información general

El modo de investigación se presentó en la primera generación de HoloLens para dar acceso a los sensores de claves en el dispositivo, específicamente para las aplicaciones de investigación que no están pensadas para la implementación. Ahora puede recopilar datos de las siguientes entradas:

* **Cámaras de seguimiento de entornos claros visibles** : utilizadas por el sistema para el seguimiento de los cabezales y el edificio de mapas.
* **Cámara de profundidad** : funciona en dos modos:  
    + Detección de breves y de alta frecuencia (30 FPS) de profundidad usada para el [seguimiento manual](interaction-fundamentals.md)
    + Detección de profundidad larga de baja frecuencia (1-5 FPS) usada por la [asignación espacial](spatial-mapping.md)
* **Dos versiones de la secuencia ir-reflectividad** : usadas por HoloLens para calcular la profundidad. Estas imágenes se iluminan por infrarrojos y no se ven afectadas por la luz visible de ambiente.

Si usa una HoloLens 2, también podrá acceder a las siguientes entradas:

* **Acelerómetro** : lo usa el sistema para determinar la aceleración lineal a lo largo de los ejes X, y y Z y la gravedad.
* **Gyro** : el sistema lo usa para determinar los giros.
* **Magnetómetro** : lo usa el sistema para calcular la orientación absoluta.

![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)<br>
*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*

> [!NOTE]
> La característica de modo de investigación se ha agregado como parte de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md) para HoloLens y no está disponible en versiones anteriores.

## <a name="usage"></a>Uso

El modo de investigación está diseñado para investigadores académicos e industriales que exploran ideas nuevas en los campos de Computer Vision y robótica.  No está diseñado para aplicaciones implementadas en entornos empresariales o disponibles a través del Microsoft Store u otros canales de distribución.

Además, Microsoft no proporciona garantías de que el modo de investigación o la funcionalidad equivalente se admitirán en futuras actualizaciones de hardware o del sistema operativo. Sin embargo, esto no debería impedir su uso para desarrollar y probar nuevas ideas.

## <a name="security-and-performance"></a>Seguridad y rendimiento

Tenga en cuenta que la habilitación del modo de investigación usa más energía de la batería que el uso de HoloLens 2 en condiciones normales. Esto es así incluso si la aplicación que usa las características de modo de investigación no se está ejecutando.  Habilitar este modo también puede reducir la seguridad general del dispositivo, ya que las aplicaciones pueden hacer uso indebido de los datos del sensor.  Puede encontrar más información sobre la seguridad de los dispositivos en las [preguntas más frecuentes sobre seguridad de HoloLens](https://docs.microsoft.com/hololens/hololens-faq-security).  


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>La primera generación de HoloLens</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>Cámaras de seguimiento de cabezales</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Profundidad & cámara de INFRARROJOs</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Acelerómetro</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Giroscopio</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>Magnetómetro</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> Se espera que la compatibilidad con el modo de investigación de HoloLens 2 esté disponible en versión preliminar pública en julio de 2020 y incluirá todas las características indicadas anteriormente. Vuelva a consultar para obtener más información. 

## <a name="enabling-research-mode"></a>Habilitar el modo de investigación

El modo de investigación es una extensión del modo de programador. Antes de comenzar, las características del desarrollador del dispositivo deben estar habilitadas para tener acceso a la configuración del modo de investigación: 

* Abra el **menú inicio > configuración** y seleccione **actualizaciones**.
* Seleccione **para desarrolladores** y habilite el **modo de desarrollador**.
* Desplácese hacia abajo y habilite el **portal de dispositivos**.

Una vez habilitadas las características de desarrollador, [Conéctese al portal de dispositivos](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar las características del modo de investigación.

En la *primera generación de HoloLens*:

* Vaya al **modo System > Research** en el **portal de dispositivos**.
* Seleccione **permitir el acceso a la secuencia del sensor**.
* Reinicie el dispositivo desde el elemento de menú de **energía** en la parte superior de la página.

Una vez que haya reiniciado el dispositivo, las aplicaciones que se cargan a través del **portal de dispositivos** pueden acceder a los flujos del modo de investigación.

![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)<br>
*Ventana del modo de investigación en el portal de dispositivos de HoloLens*

## <a name="using-sensor-data-in-your-apps"></a>Uso de datos de sensor en las aplicaciones

*La primera generación de HoloLens*

Las aplicaciones pueden tener acceso a los datos de la secuencia del sensor de la misma manera que se obtiene acceso a los flujos de cámara de fotos y vídeo a través de [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197). 

Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación. En concreto, la aplicación sabe exactamente dónde se encuentra HoloLens en el espacio 6DoF en cada tiempo de captura de fotogramas del sensor.

Puede encontrar aplicaciones de ejemplo sobre cómo obtener acceso a las diversas secuencias del modo de investigación, cómo usar las [funciones intrínsecas y extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), y cómo grabar secuencias en el repositorio de [repositorios de github de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV) .

 > [!NOTE]
 > En este momento, el ejemplo HoloLensForCV no funciona en HoloLens 2.

## <a name="known-issues"></a>Problemas conocidos

Puede usar el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV para seguir los problemas conocidos.

## <a name="see-also"></a>Consulte también:

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [Repositorio de GitHub de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)
