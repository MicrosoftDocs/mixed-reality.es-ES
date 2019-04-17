---
title: Notas de la versión - octubre de 2018
description: HoloLens y notas de la versión de Windows Mixed Reality para Windows 10 de octubre de 2018 actualización (también conocido como RS5).
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: release notes, versión, windows 10, compilación, rs5, sistema operativo
ms.openlocfilehash: 9838b4dcbdedc4bf2c94a8e31f3f8eb4c9634d36
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605593"
---
# <a name="release-notes---october-2018"></a>Notas de la versión - octubre de 2018

El **[Windows 10 de octubre de 2018 Update](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (también conocido como RS5) incluye nuevas características para HoloLens y Windows Mixed Reality inmersivos conectados a PC. 

Para actualizar a la versión más reciente en HoloLens o PC (para Windows Mixed Reality (VR) inmersivos), abra el **configuración** aplicación, vaya a **actualización y seguridad**, a continuación, seleccione el **comprobar las actualizaciones** botón. En un equipo con Windows 10, puede instalar manualmente Windows 10 de octubre de 2018 actualizar mediante el [herramienta de creación de Windows media](https://www.microsoft.com/software-download/windows10).

**Última versión de escritorio:** Actualización de Windows 10 de octubre de 2018 (**10.0.17763.107**)<br>
**Versión más reciente para HoloLens:** Actualización de Windows 10 de octubre de 2018 (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuevas características para inmersivos Windows Mixed Reality

Windows 10 de octubre de 2018 Update incluye muchas mejoras para usar auriculares de Windows Mixed Reality envolventes (VR) con su PC de escritorio.

### <a name="for-everyone"></a>Para todos los usuarios

* **Mixto realidad linterna** : abrir un portal en el mundo real para encontrar el teclado, ver a alguien cercanos o eche un vistazo a su entorno sin quitar los auriculares! Puede activar linterna de realidad mixta en el menú Inicio, presione Windows + arrastre en el controlador de movimiento o diciendo "Linterna on/off". Seleccione el controlador en el sentido de que desea ver, como el uso de una linterna en la oscuridad.

    ![Realidad mixta linterna](images/mr-flashlight.png)

* **Nuevas aplicaciones y formas de iniciar el contenido de la realidad mixta principal**
    * Si usas [Windows Mixed Reality para SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality), sus títulos SteamVR ahora se muestran en el menú Inicio y los iniciadores de aplicaciones para cada uno pueden colocarse en la realidad mixta principal.
    
        ![Iniciadores de aplicaciones SteamVR](images/steamvr-launchers.png)
        
    * Nuevo *360 vídeos* aplicación para detectar una selección con regularidad protegido de vídeos de 360 grados.
    * Nuevo *WebVR Showcase* experiencias de aplicación para detectar una selección con regularidad protegido de WebVR.
    * Los clientes de Windows Mixed Reality por primera vez introducirá el Cliff House y buscar que rellena previamente con los iniciadores de aplicaciones 3D para algunos de nuestros favoritos aplicaciones envolventes y juegos desde la Microsoft Store.
    * Ventanas de Microsoft Edge ahora incluyen una *Share* botón.
* **Menú Acciones rápidas** -desde dentro de una aplicación de realidad mixta envolventes, puede presionar el botón de Windows para tener acceso a un nuevo menú de acciones rápidas, con un acceso sencillo a *SteamVR menú*, *captura de fotografías y vídeo*, *linterna*, y *principal*.
* **Compatibilidad con equipos mochila** -Windows Mixed Reality inmersivos (VR) se ejecutan en la mochila equipos sin necesidad de un emulador de visualización una vez completada la instalación.
* **Nuevas características de audio** : ahora puede reflejar el audio de una experiencia de realidad mixta de Windows para el conector de audio (o auriculares) en los auriculares *y* un dispositivo de audio conectado a su equipo (por ejemplo, altavoces externos). También hemos agregado un indicador visual para el nivel de volumen en pantalla de los auriculares.
* **Otras mejoras**
    * Actualizaciones del Portal de realidad mixtas ahora se entregan a través de la Microsoft Store, habilitar las actualizaciones más rápidas entre las versiones principales de Windows. Tenga en cuenta que esto solo se aplica a la aplicación de escritorio y la experiencia de auriculares de realidad mixta de Windows todavía se actualiza con el sistema operativo. 
    * Cuando auriculares entrar en suspensión, las aplicaciones de Windows Mixed Reality se suspenden en lugar de terminado (hasta que se cierra el Portal de realidad mixta).
    
### <a name="for-developers"></a>Para desarrolladores

* **[Seguimiento del código QR](qr-code-tracking.md)**  -realizar una copia de código QR habilitar el seguimiento en la aplicación de realidad mixta, lo que permite Windows Mixed Reality (VR) inmersivos buscar los códigos QR y notificarlos a aplicaciones interesadas.
* **Compatibilidad con DRM de hardware para aplicaciones inmersivas** : los desarrolladores pueden texturas de hardware protegido el búfer de reserva de solicitud ahora si es compatible con el hardware de la pantalla, lo que permite a las aplicaciones utilizar contenido protegido de hardware desde orígenes como PlayReady.
* **[Integre la realidad mixta captura la interfaz de usuario en aplicaciones envolventes](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)**  : los desarrolladores pueden integrar la captura de realidad mixta en sus aplicaciones con el Windows integrada [captura la interfaz de usuario de la cámara](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) con unas pocas líneas de código.

## <a name="new-features-for-hololens"></a>Nuevas características para HoloLens

El 10 de octubre de 2018 de Windows Update está disponible públicamente para todos los clientes de HoloLens e incluye una serie de mejoras, como:

### <a name="for-everyone"></a>Para todos los usuarios

* **Menú Acciones rápidas** -desde dentro de una aplicación de realidad mixta envolventes, puede presionar el botón de Windows para tener acceso a un nuevo menú de acciones rápidas, con un acceso sencillo a *Iniciar grabación de vídeo*, *tomar fotografías*, *Mixed Reality principal*, *cambiar el volumen*, y *Connect*.
* **Captura de vídeo de inicios y paradas desde el inicio o el menú Acciones rápidas** -si inicia la captura de vídeo desde el menú Inicio o el menú Acciones rápidas, podrá detener la grabación desde el mismo lugar. (No olvide que siempre hacer esto con los comandos de voz demasiado.)
* **Proyecto para un dispositivo habilitado para Miracast** -el contenido de HoloLens en un dispositivo de superficie cercano o el monitor o TV del proyecto si utiliza un adaptador o habilitado para Miracast para mostrar.
* **Nuevas notificaciones** -ver y responder a las notificaciones en HoloLens, igual que haría en un equipo.  
* **Las superposiciones útiles en aplicaciones de realidad mixta envolventes** -ahora verá superposiciones tales como el teclado, los cuadros de diálogo Selector de archivos, etc. cuando se usa envolventes mixto las aplicaciones de realidad.
* **Indicador visual para el cambio del volumen** : al usar el volumen / botones en su HoloLens verá un indicador visual del nivel de volumen de los auriculares.
* **Nuevos objetos visuales para el arranque del dispositivo** -se agregó un indicador de carga durante el proceso de arranque para proporcionar comentarios visuales que se está cargando el sistema.
* **Uso compartido de mano** -The Windows cercanos compartir experiencia le permite compartir una captura con un dispositivo cercano de Windows.  
* **Recurso compartido de Microsoft Edge** -Microsoft Edge incluye ahora un *Share* botón. 

### <a name="for-developers"></a>Para desarrolladores

* **[Integre la realidad mixta captura la interfaz de usuario en aplicaciones envolventes](mixed-reality-capture-for-developers.md#integrating-mrc-functionality-from-within-your-app)**  : los desarrolladores pueden integrar la captura de realidad mixta en sus aplicaciones con el Windows integrada [captura la interfaz de usuario de la cámara](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) con unas pocas líneas de código.

### <a name="for-commercial-customers"></a>Para los clientes comerciales

* **Habilitar el aprovisionamiento posterior a la instalación** -ahora se puede aplicar un paquete de aprovisionamiento en cualquier momento mediante la configuración en tiempo de ejecución.
* **Asignar acceso con grupos de Azure AD** : ahora puede usar grupos de Azure AD para la configuración de Windows asignada acceso para establecer la configuración de pantalla completa solo o con varias aplicaciones.
* **ANCLAR a inicio de sesión en el conmutador de perfil desde la pantalla de inicio de sesión** -inicio de sesión de PIN ahora está disponible para "Otro usuario" en la pantalla de inicio de sesión. 
* **Inicie sesión con el proveedor de credenciales de Web con contraseña** : ahora puede seleccionar el icono de globo para iniciar el inicio de sesión web con su contraseña. 
* **Leer información de hardware del dispositivo a través de MDM** -los administradores de TI pueden ver y realizar un seguimiento de HoloLens por número de serie del dispositivo en su consola MDM.
* **Establecer nombre de dispositivo HoloLens a través de MDM (rename)** -los administradores de TI pueden ver y cambiar el nombre de los dispositivos HoloLens en su consola MDM.

### <a name="for-international-customers"></a>Para clientes internacionales

Ahora puede usar HoloLens con la interfaz de usuario localizada para chino simplificado o japonés, incluidos los comandos de voz, dictado, texto a voz (TTS) y teclado Pinyin localizado.

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado duro para ofrecer una excelente experiencia de Windows Mixed Reality, pero todavía estamos realizando un seguimiento algunos problemas conocidos. Si encuentra otros, [enviarnos comentarios](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Después de la actualización
Es posible que observe los siguientes problemas cuando usa el Windows 10 de octubre de 2018 actualización en su HoloLens:
* **Las aplicaciones pueden terminar en el inicio de sesión de bucle cuando se inicia desde una notificación** : algunas aplicaciones que requieren inicio de sesión pueden acabar en un bucle sin fin inicio de sesión cuando se inicia desde una notificación. Por ejemplo, esto puede ocurrir después de instalar la aplicación de Portal de empresa de Microsoft desde la Microsoft Store e iniciarlo desde la notificación de instalación completa.
* **Página de inicio de sesión de la aplicación se puede completar con una página en blanco** : en algunos casos, cuando se muestra un mensaje de inicio de sesión a través de la aplicación al finalizar la página de inicio de sesión no se cierra y en su lugar, muestra una página en blanco (negra). Puede cerrar la página en blanco o muévalo para descubrir la aplicación debajo. Por ejemplo, esto puede ocurrir cuando se inicia sesión durante la inscripción de MDM desde la aplicación configuración. 

## <a name="provide-feedback-and-report-issues"></a>Proporcionar comentarios e informe de problemas

Use la [aplicación Centro de opiniones en su equipo con Windows 10 o en HoloLens](give-us-feedback.md) para proporcionar comentarios e informe de problemas. Mediante el centro de comentarios asegura que toda la información de diagnóstico necesarios se incluyen para ayudar a nuestros ingenieros de depurar y resolver el problema rápidamente.

>[!NOTE]
>No olvide acepte el mensaje que pregunta si desea que el centro de opiniones para tener acceso a la carpeta documentos (seleccione **Sí** cuando se le solicite).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión - abril de 2018](release-notes-april-2018.md)
* [Notas de la versión - octubre de 2017](release-notes-october-2017.md)
* [Notas de la versión - agosto de 2016](release-notes-august-2016.md)
* [Notas de la versión - mayo de 2016](release-notes-may-2016.md)
* [Notas de la versión: marzo de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Soporte técnico de auriculares envolventes (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Soporte técnico de HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalar las herramientas](install-the-tools.md)
* [Envíenos sus comentarios](give-us-feedback.md)

