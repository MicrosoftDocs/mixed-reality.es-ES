---
title: Captura de realidad mixta
description: Información sobre el uso de la captura de realidad mixta.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, captura de realidad mixta, fotos, vídeo, cámara, captura, uso, Stream, streaming en vivo, Demo
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694489"
---
# <a name="mixed-reality-capture"></a>Captura de realidad mixta

HoloLens ofrece a los usuarios la experiencia de mezclar el mundo real con el mundo digital. La captura de realidad mixta (MRC) le permite capturar esa experiencia como una fotografía o un vídeo. Esto le permite compartir la experiencia con otras personas permitiéndoles ver los hologramas tal y como se ven. Estos vídeos y fotos proceden de un punto de vista de primera persona. Para un punto de vista de terceras personas, use la [vista Spectator](spectator-view.md).

Los casos de uso de la captura de realidad mixta van más allá de compartir vídeos entre un círculo social. Los vídeos se pueden usar para indicar a otros usuarios cómo usar una aplicación. Los desarrolladores pueden usar vídeos o seguir mejorando los pasos de reproducción y depurar las experiencias de la aplicación.

## <a name="live-streaming-from-hololens"></a>Streaming en vivo desde HoloLens

La [actualización 2018 de octubre de Windows 10](release-notes-october-2018.md) agrega compatibilidad con Miracast a HoloLens. Seleccione el botón **conectar** en la parte inferior del menú Inicio para mostrar un selector para los adaptadores y dispositivos habilitados para Miracast. Seleccione el dispositivo al que desea iniciar el streaming. Cuando haya terminado, seleccione el botón **desconectar** situado en la parte inferior del menú Inicio.  La **conexión** y desconexión también están disponibles en el menú acciones rápidas.

El [portal de dispositivos de Windows](using-the-windows-device-portal.md) y la [aplicación complementaria de Microsoft HoloLens](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) exponen opciones de streaming en vivo para dispositivos que están en modo de desarrollador.

[Dynamics 365 Remote Assist](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) admite el streaming en vivo desde HoloLens a los empleados en ubicaciones remotas.

## <a name="taking-mixed-reality-captures"></a>Realizar capturas de realidad mixta

![Haga clic en el icono de cámara situado en la parte inferior del menú Inicio.](images/cameraiconinpins-300px.png)<br>
*Haga clic en el icono de cámara situado en la parte inferior del menú Inicio.*

Hay varias maneras de iniciar una captura de realidad mixta:
* Cortana se puede usar en todo momento, independientemente de la aplicación que se esté ejecutando. Simplemente, supongamos que "oye Cortana, toma una fotografía" o "oye Cortana, comienza a grabar". Para detener un vídeo, di "Hola Cortana, Detener grabación".
* En el menú Inicio, seleccione **cámara** o **vídeo**. Use [Air-TAP](gestures.md#air-tap) para abrir la interfaz de usuario de la cámara MRC integrada.
* En el menú acciones rápidas, seleccione **cámara** o **vídeo** para abrir la interfaz de usuario de la cámara MRC integrada.
* Las aplicaciones pueden exponer su propia interfaz de usuario para la captura de la realidad mixta mediante Custom o, a partir de la [actualización de Windows 10 de octubre de 2018](release-notes-october-2018.md), la [interfaz de usuario de la cámara MRC integrada](mixed-reality-capture-for-developers.md).
* Exclusivo de HoloLens: 
    * [Windows Device portal](using-the-windows-device-portal.md) tiene una página de captura de realidad mixta que se puede usar para tomar fotografías, vídeos, streaming en vivo y vistas de vista.
    * Presione los botones **subir** y **bajar** volumen simultáneamente para tomar una imagen, independientemente de la aplicación que se esté ejecutando.
    * Mantenga los botones **subir volumen** y **bajar el volumen** durante tres segundos para empezar a grabar un vídeo. Para detener un vídeo, puntee en los botones **subir** y **bajar** volumen simultáneamente.
* Solo para auriculares envolventes: 
    * Con un controlador de movimiento, mantenga presionado el botón de **Windows** y, a continuación, puntee en el **desencadenador** para tomar una imagen. 
    * Con un controlador de movimiento, mantenga presionado el botón de **Windows** y, a continuación, puntee en el botón de **menú** para iniciar la grabación de vídeo. Mantenga presionado el botón de **Windows** y, a continuación, puntee en el **desencadenador** para detener la grabación de vídeo.
    
>[!NOTE]
>La [actualización de Windows 10 de octubre de 2018](release-notes-october-2018.md) cambia el funcionamiento del botón de floración y el de Windows. Antes de la actualización, el gesto de la floración o el botón de Windows dejarían de grabar. Después de la actualización, el gesto de floración o el botón de Windows abre el menú Inicio (o el menú acciones rápidas si está en una aplicación). En el menú, seleccione **detener vídeo** para detener la grabación.

### <a name="limitations-of-mixed-reality-capture"></a>Limitaciones de la captura de realidad mixta

En HoloLens, el sistema limitará la velocidad de representación a 30Hz. Esto crea un espacio para la ejecución de MRC, por lo que la aplicación no necesita mantener una reserva de presupuesto constante y también coincide con la velocidad de fotogramas de grabación de vídeo de MRC de (hasta) 30 fps.

Los vídeos tienen una longitud máxima de cinco minutos.

La interfaz de usuario de la cámara MRC integrada solo admite una sola operación de MRC a la vez (tomar una imagen es mutuamente excluyente de la grabación de un vídeo).

### <a name="file-formats"></a>Formatos de archivo

Las capturas de realidad mixta de los comandos de voz de Cortana y las herramientas del menú Inicio crean archivos en los siguientes formatos:

|  Type  |  Formato  |  Extensión  |  Resolución  |  Audio | 
|----------|----------|----------|----------|----------|
|  Foto  |  [FICHEROS](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px (auriculares inmersivo) |  N/D | 
|  Vídeo  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px en 30 fps (HoloLens 2)<br> 1216x684px en 24fps (HoloLens)<br> 1632x918px en 30 fps (auriculares envolventes) |  Estéreo a 48 kHz | 

>[!NOTE]
>La resolución de las fotos y los vídeos puede ser menor si otra aplicación ya está usando la cámara de fotos o vídeo, mientras se transmite por streaming en vivo o cuando los recursos del sistema son bajos.

### <a name="video-stabilization"></a>Estabilización de vídeo

De forma predeterminada:
* La estabilización de vídeo de latencia cero se aplica al streaming en vivo a través de Miracast.
* La estabilización de vídeo de larga latencia se aplica a los vídeos capturados con la interfaz de usuario de la cámara de MRC integrada, los comandos de voz de Cortana y el portal de dispositivos de Windows.

## <a name="viewing-mixed-reality-captures"></a>Ver capturas de realidad mixta

Las fotografías y vídeos de captura de realidad mixta se guardan en la carpeta "rollo de cámara" del dispositivo. Se puede acceder a ellos a través de la [aplicación fotos](see-your-photos.md#photos-app) o el explorador de archivos.

En un equipo conectado a HoloLens, también puede usar el [portal de dispositivos de Windows](using-the-windows-device-portal.md#mixed-reality-capture) o el explorador de archivos de su PC ([a través de MTP](release-notes-april-2018.md#new-features-for-hololens)).

Si instala la [aplicación de OneDrive](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), puede activar la carga de la **cámara** y sus fotos y vídeos de MRC se sincronizarán con onedrive y con los demás dispositivos mediante OneDrive.

>[!NOTE]
>A partir de la actualización del 2018 de abril de Windows 10, la aplicación fotos ya no cargará sus fotos y vídeos en OneDrive.

## <a name="see-also"></a>Vea también
* [Vista del espectador](spectator-view.md)
* [Cámara localizable](locatable-camera.md)
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Visualización de fotos](see-your-photos.md)
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)
