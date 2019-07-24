---
title: 'Notas de la versión: octubre 2018'
description: Notas de la versión de HoloLens y Windows Mixed Reality para la actualización 2018 de octubre de Windows 10 (también conocida como RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: Notas de la versión, versión, Windows 10, compilación, RS5, so
ms.openlocfilehash: 794050910be40e7f98d0a1f67c2e1cf6963305dd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524258"
---
# <a name="release-notes---october-2018"></a>Notas de la versión: octubre 2018

La **[actualización 2018 de octubre de Windows 10](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (también conocida como RS5) incluye nuevas características para los auriculares de la realidad de HoloLens y Windows Mixed Reality conectados a equipos. 

Para actualizar a la versión más reciente de HoloLens o PC (para auriculares con Windows Mixed Reality inmersivo (VR)), abra la aplicación de **configuración** , vaya a **Actualizar & seguridad**y, luego, seleccione el botón **Buscar actualizaciones** . En un equipo con Windows 10, también puede instalar manualmente la actualización de Windows 10 de octubre de 2018 con la [herramienta de creación de Windows Media](https://www.microsoft.com/software-download/windows10).

**Versión más reciente del escritorio:** Actualización 2018 de octubre de Windows 10 (**10.0.17763.107**)<br>
**Versión más reciente de HoloLens:** Actualización 2018 de octubre de Windows 10 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuevas características para auriculares con Windows Mixed Reality

La actualización 2018 de octubre de Windows 10 incluye muchas mejoras para usar auriculares con Windows Mixed Reality envolventes (VR) con el equipo de escritorio.

### <a name="for-everyone"></a>Para todos

* **Combinación de realidad mixta** : Abra un portal en el mundo real para encontrar su teclado, ver a alguien cerca o eche un vistazo a su entorno sin necesidad de quitar el casco. Puede activar la linterna de realidad mixta desde el menú Inicio; para ello, presione Windows + Grab en el controlador de movimiento o indique "linterna encendido/desactivado". Señale el controlador en la dirección de lo que desea ver, como el uso de una linterna en el oscuro.

    ![Linterna de realidad mixta](images/mr-flashlight.png)

* **Nuevas aplicaciones y formas de iniciar contenido en la Página principal de la realidad mixta**
    * Si usa [Windows Mixed Reality para SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), los títulos de SteamVR aparecen ahora en el menú Inicio y los iniciadores de aplicaciones para cada uno pueden colocarse en la Página principal de la realidad mixta.
    
        ![Iniciadores de aplicaciones de SteamVR](images/steamvr-launchers.png)
        
    * Nueva aplicación de *vídeos de 360* para detectar una selección de vídeos de 360 grados de seleccionada con regularidad.
    * Nueva aplicación de presentación de *WebVR* para detectar una selección periódica seleccionada de experiencias de WebVR.
    * La primera vez que los clientes de Windows Mixed Reality entrarán en el centro de acantilado y lo encontrarán rellenados previamente con lanzadores de aplicaciones 3D para algunas de nuestras aplicaciones y juegos favoritos de la Microsoft Store.
    * Las ventanas de Microsoft Edge ahora incluyen un botón *compartir* .
* **Menú acciones rápidas** : desde una aplicación de realidad mixta, puede presionar el botón de Windows para obtener acceso a un nuevo menú de acciones rápidas, con fácil acceso al *menú SteamVR*, *captura de fotos o vídeos*, *linterna*y *Inicio*.
* **Compatibilidad con equipos Backpack** : los auriculares con Windows Mixed Reality (VR) se ejecutan en equipos Backpack sin necesidad de un emulador de pantalla una vez que se ha completado la instalación.
* **Nuevas características de audio** : ahora puede reflejar el audio de una experiencia de Windows Mixed Reality en el conector de audio (o auriculares) del casco *y* en un dispositivo de audio conectado a su equipo (por ejemplo, altavoces externos). También hemos agregado un indicador visual para el nivel de volumen en la pantalla del casco.
* **Otras mejoras**
    * Ahora, las actualizaciones del portal de realidad mixta se entregan a través del Microsoft Store, lo que permite actualizaciones más rápidas entre las principales versiones de Windows. Tenga en cuenta que esto solo se aplica a la aplicación de escritorio y la experiencia de auriculares de la realidad mixta de Windows todavía se actualiza con el sistema operativo. 
    * Cuando los auriculares van a la suspensión, las aplicaciones de Windows Mixed Reality se suspenden en lugar de finalizar (hasta que se cierra el portal de realidad mixta).
    
### <a name="for-developers"></a>Para desarrolladores

* **[Seguimiento de código QR](qr-code-tracking.md)** : habilita el seguimiento del código QR en la aplicación de realidad mixta, lo que permite a los auriculares con Windows Mixed Reality (VR) Buscar códigos QR y volver a enviarlos a las aplicaciones interesadas.
* **Compatibilidad de DRM de hardware** con las aplicaciones envolventes: los desarrolladores ahora pueden solicitar texturas de búfer de reserva protegidas por hardware Si se admiten en el hardware de pantalla, lo que permite a las aplicaciones usar contenido protegido por hardware de orígenes como PlayReady.
* **[Integración de la interfaz de usuario de captura de realidad mixta en aplicaciones](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** envolventes: los desarrolladores pueden integrar la captura de realidad mixta en sus aplicaciones con la [interfaz de usuario de captura de cámara](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) integrada de Windows con solo unas pocas líneas de código.

## <a name="new-features-for-hololens"></a>Nuevas características de HoloLens

La actualización 2018 de octubre de Windows 10 está disponible públicamente para todos los clientes de HoloLens e incluye una serie de mejoras, como:

### <a name="for-everyone"></a>Para todos

* **Menú acciones rápidas** : desde una aplicación de realidad mixta, puede presionar el botón Windows para acceder a un nuevo menú de acciones rápidas, con fácil acceso para *empezar a grabar vídeo*, *tomar fotografías*, *Inicio de realidad mixta*, *cambiar Volume*y *Connect*.
* **Iniciar o detener la captura de vídeo desde el menú acciones de inicio o rápido** : Si inicia la captura de vídeo desde el menú Inicio o desde el menú acciones rápidas, podrá detener la grabación desde el mismo lugar. (No olvide que siempre puede hacer esto con comandos de voz).
* **Proyecto a un dispositivo habilitado para Miracast** : permite proyectar el contenido de HoloLens en un dispositivo de Surface Surface o en un monitor o TV, si se usa una pantalla o adaptador habilitado para Miracast.
* **Nuevas notificaciones** : ver y responder a notificaciones en HoloLens, al igual que en un equipo.  
* **Superposiciones útiles en aplicaciones de realidad mixtas** envolventes: ahora verá superposiciones como el teclado, los cuadros de diálogo, el selector de archivos, etc. cuando se usan aplicaciones de realidad mixta.
* **Indicador visual para cambio de volumen** : cuando se usan los botones subir/bajar volumen en la HoloLens, verá un indicador visual del nivel de volumen en los auriculares.
* **Nuevos objetos visuales para el arranque de dispositivos** : se ha agregado un indicador de carga durante el proceso de arranque para proporcionar comentarios visuales que el sistema está cargando.
* **Uso compartido cercano** : la experiencia de uso compartido cercano de Windows permite compartir una captura con un dispositivo Windows cercano.  
* **Compartir desde Microsoft Edge** : ahora, Microsoft Edge incluye un botón *compartir* . 

### <a name="for-developers"></a>Para desarrolladores

* **[Integración de la interfaz de usuario de captura de realidad mixta en aplicaciones](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)** envolventes: los desarrolladores pueden integrar la captura de realidad mixta en sus aplicaciones con la [interfaz de usuario de captura de cámara](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) integrada de Windows con solo unas pocas líneas de código.

### <a name="for-commercial-customers"></a>Para clientes comerciales

* **Habilitar aprovisionamiento posterior** a la instalación: ahora puede aplicar un paquete de aprovisionamiento en tiempo de ejecución en cualquier momento mediante la configuración.
* **Acceso asignado con grupos de Azure ad** : ahora puede usar grupos de Azure ad para la configuración de acceso asignado de Windows para configurar una configuración de pantalla completa de una o varias aplicaciones.
* **Switch inicio de sesión en el perfil cambiar desde** el inicio de sesión del PIN de la pantalla de inicio de sesión ahora está disponible para "otro usuario" en la pantalla de inicio de sesión. 
* **Leer información de hardware de dispositivos a través de MDM** : los administradores de TI pueden ver y realizar un seguimiento de HoloLens por número de serie de dispositivo en la consola de MDM.
* **Establecer el nombre del dispositivo hololens a través de MDM (cambiar nombre)** : los administradores de TI pueden ver y cambiar el nombre de los dispositivos de hololens en la consola de MDM.

### <a name="for-international-customers"></a>Para clientes internacionales

Ahora puede usar HoloLens con la interfaz de usuario localizada para chino simplificado o japonés, incluidos los comandos localizados teclado, dictado, conversión de texto a voz (TTS) y voz de pinyin.

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado mucho para ofrecer una excelente experiencia de realidad mixta de Windows, pero todavía estamos realizando un seguimiento de algunos problemas conocidos. Si encuentra otras personas, envíenos [sus comentarios](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Después de la actualización
Es posible que observe los siguientes problemas al usar la actualización 2018 de octubre de Windows 10 en HoloLens:
* Las **aplicaciones pueden acabar en un bucle de inicio de sesión cuando se inician desde una notificación** : algunas aplicaciones que requieren inicio de sesión pueden acabar en un bucle de inicio de sesión sin fin cuando se inician desde una notificación. Por ejemplo, esto puede ocurrir después de instalar la aplicación de Microsoft Portal de empresa desde la Microsoft Store y de iniciarla desde la notificación de instalación completada.
* La **Página de inicio de sesión de la aplicación puede completarse con una página en blanco** : en algunos casos, cuando se muestra una solicitud de inicio de sesión en la aplicación, al finalizar la página de inicio de sesión no se cierra y muestra una página en blanco (negro). Puede cerrar la página en blanco o moverla para descubrir la aplicación debajo de. Por ejemplo, esto puede ocurrir durante el inicio de sesión durante la inscripción de MDM desde la aplicación de configuración. 

## <a name="provide-feedback-and-report-issues"></a>Proporcionar comentarios e informar de problemas

Use la [aplicación de centro de comentarios en su equipo HoloLens o Windows 10](give-us-feedback.md) para proporcionar comentarios e informar de problemas. El uso del centro de comentarios garantiza que se incluye toda la información de diagnóstico necesaria para ayudar a nuestros ingenieros a depurar y resolver el problema rápidamente.

>[!NOTE]
>Asegúrese de aceptar el mensaje que le pregunta si desea que el centro de comentarios tenga acceso a la carpeta de documentos (seleccione **sí** cuando se le solicite).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión (abril de 2018)](release-notes-april-2018.md)
* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Compatibilidad con auriculares envolvente (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Compatibilidad con HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalación de las herramientas](install-the-tools.md)
* [Comentarios](give-us-feedback.md)

