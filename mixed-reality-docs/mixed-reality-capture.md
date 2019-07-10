---
title: Captura de realidad mixta
description: Información sobre el uso de la captura de realidad mixta.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: MRC, mixto captura realidad, fotos, vídeo, cámara, captura, uso, secuencia, streaming en vivo, demostración
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694489"
---
# <a name="mixed-reality-capture"></a>Captura de realidad mixta

HoloLens ofrece a los usuarios la experiencia de mezclar el mundo real con el mundo digital. Captura de realidad mixta (MRC) le permite capturar esa experiencia como una fotografía o un vídeo. Esto le permite compartir la experiencia con otros usuarios, por lo que les permite ver el hologramas según se ve. Estas fotos y vídeos proceden de un punto de vista de la primera persona. Para un punto de vista de tercera persona use [vista del espectador](spectator-view.md).

Casos de uso para la captura de realidad mixta ir más allá de compartir vídeos entre un círculo social. Vídeos pueden utilizarse para indicar a otros usuarios sobre cómo usar una aplicación. Los desarrolladores pueden usar vídeos o imágenes fijas para mejorar los pasos de reproducción y depurar las experiencias de aplicación.

## <a name="live-streaming-from-hololens"></a>Live streaming de HoloLens

El [Windows 10 de octubre de 2018 Update](release-notes-october-2018.md) agrega compatibilidad con Miracast a HoloLens. Seleccione el **Connect** situado en la parte inferior del menú Inicio para que aparezca un selector para los adaptadores y dispositivos habilitados para Miracast. Seleccione el dispositivo a la que desea iniciar el streaming. Cuando haya terminado, seleccione el **desconexión** situado en la parte inferior del menú Inicio.  **Conectar** y **desconexión** también están disponibles en el menú Acciones rápidas.

El [Windows Device Portal](using-the-windows-device-portal.md) y [aplicación complementaria de Microsoft HoloLens](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) exponen las opciones para dispositivos que están en modo de programador de streaming en vivo.

[Dynamics 365 remoto Assist](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) admite el streaming en vivo de HoloLens a los empleados en ubicaciones remotas.

## <a name="taking-mixed-reality-captures"></a>Captura de tomar la realidad mixta

![Haga clic en el icono de cámara en la parte inferior del menú Inicio](images/cameraiconinpins-300px.png)<br>
*Haga clic en el icono de cámara en la parte inferior del menú Inicio*

Hay varias maneras de iniciar una captura de realidad mixta:
* Cortana puede usarse en todo momento, independientemente de la aplicación en ejecución actualmente. Decir: "Hola Cortana, tomar una foto" o "Hola Cortana, iniciar la grabación." Para detener un vídeo, diga "Hola Cortana, detenga la grabación."
* En el menú Inicio, seleccione **cámara** o **vídeo**. Use [pulsar en el aire](gestures.md#air-tap) para abrir la cámara integrada MRC la interfaz de usuario.
* En el menú Acciones rápidas, seleccione **cámara** o **vídeo** para abrir la cámara integrada MRC la interfaz de usuario.
* Las aplicaciones son capaces de exponer su propia interfaz de usuario para la captura de realidad mixta mediante personalizados o, como de la [Windows 10 de octubre de 2018 Update](release-notes-october-2018.md), [cámara integrada de MRC UI](mixed-reality-capture-for-developers.md).
* Exclusivo de HoloLens: 
    * [Windows Device Portal](using-the-windows-device-portal.md) tiene una página de captura de realidad mixta que puede usarse para tomar fotografías, vídeos, streaming en vivo y ver capturas.
    * Presione tanto el **Subir volumen** y **Bajar volumen** botones simultáneamente para tomar una foto, independientemente de la aplicación en ejecución actualmente.
    * Mantenga el **Subir volumen** y **Bajar volumen** botones durante tres segundos comenzar a grabar un vídeo. Para detener un vídeo, puntee en ambos **Subir volumen** y **Bajar volumen** botones al mismo tiempo.
* Auriculares envolventes exclusivas: 
    * Con un controlador de movimiento, mantenga pulsada la **Windows** botón y, a continuación, puntee en el **desencadenador** para tomar una foto. 
    * Con un controlador de movimiento, mantenga pulsada la **Windows** botón y, a continuación, puntee en el **menú** botón para iniciar la grabación de vídeo. Mantenga el **Windows** botón y, a continuación, puntee en el **desencadenador** para detener la grabación de vídeo.
    
>[!NOTE]
>El [Windows 10 de octubre de 2018 Update](release-notes-october-2018.md) cambia cómo se comportan bloom y botón de Windows. Antes de la actualización, el botón de Windows o el gesto de bloom podría detener la grabación. Tras la actualización, el gesto de bloom o en el botón de Windows se abre el menú Inicio (o en el menú Acciones rápidas si se encuentra en una aplicación). En el menú, seleccione **Stop vídeo** para detener la grabación.

### <a name="limitations-of-mixed-reality-capture"></a>Limitaciones de la captura de realidad mixta

En HoloLens, el sistema limita la tasa de procesamiento a 30Hz. Esto crea algún espacio disponible para MRC para ejecutarse por lo que la aplicación no necesita mantener una reserva de presupuesto constante y también coincide con la velocidad de fotogramas de vídeo registro MRC de (hasta) 30fps.

Vídeos de tener una longitud máxima de cinco minutos.

La cámara integrada MRC UI sólo admite una única operación MRC a la vez (tomar una foto es mutuamente excluyente de grabar un vídeo).

### <a name="file-formats"></a>Formatos de archivo

Captura de realidad mixta de comandos de voz de Cortana y herramientas del menú Inicio crean archivos en los siguientes formatos:

|  Tipo  |  Formato  |  Extensión  |  Resolución  |  Audio | 
|----------|----------|----------|----------|----------|
|  Foto  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920 x 1080 px (inmersivos) |  N/D | 
|  Vídeo  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920 x 1080 px a 30fps (HoloLens 2)<br> 1216x684px a 24fps (HoloLens)<br> 1632x918px a 30fps (inmersivos) |  48kHz estéreo | 

>[!NOTE]
>La resolución de las fotos y vídeos puede ser menor si la cámara de vídeo y fotos ya está en uso por otra aplicación, al streaming en vivo, o cuando hay pocos recursos del sistema.

### <a name="video-stabilization"></a>Estabilización de vídeo

De forma predeterminada:
* Estabilización de vídeo con latencia cero se aplica cuando está activada la transmisión por secuencias a través de Miracast.
* Estabilización de vídeo de latencia se aplica a vídeos capturados mediante la cámara integrada de MRC la interfaz de usuario, los comandos de voz de Cortana y Windows Device Portal.

## <a name="viewing-mixed-reality-captures"></a>Captura de la visualización de realidad mixta

Realidad mixta captura fotos y vídeos se guardan en la carpeta de "Álbum de cámara" del dispositivo. Éstos son accesibles a través de la [aplicación fotos](see-your-photos.md#photos-app) o explorador de archivos.

En un equipo conectado a HoloLens, también puede usar [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture) o explorador de archivos de su PC ([mediante MTP](release-notes-april-2018.md#new-features-for-hololens)).

Si instala el [aplicación OneDrive](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3), puede activar **carga de la cámara,** y se sincronizarán MRC fotografías y vídeos en OneDrive y otros dispositivos con OneDrive.

>[!NOTE]
>A partir de Windows 10 de abril de 2018 actualización, la aplicación fotos ya no cargará tus fotos y vídeos en OneDrive.

## <a name="see-also"></a>Vea también
* [Vista del espectador](spectator-view.md)
* [Cámara localizable](locatable-camera.md)
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Visualización de fotos](see-your-photos.md)
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)
