---
title: 'Notas de la versión: octubre 2017'
description: Notas de la versión de Windows Mixed Reality para Windows 10 Fall Creators Update (2017 de octubre).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Notas de la versión, versión, Windows 10, compilación, RS3, so
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524092"
---
# <a name="release-notes---october-2017"></a>Notas de la versión: octubre 2017

¡ Bienvenido a Windows Mixed Reality! El lanzamiento de la **[actualización de Windows 10 Fall Creators](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** incluye compatibilidad con nuevos auriculares y [controladores de movimiento](motion-controllers.md)para la [realidad mixta de Windows](immersive-headset-hardware-details.md) , lo que le permite explorar nuevos mundos, jugar a juegos de VR y experimentar entretenimiento cuando se conecta a un [equipo compatible con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

La versión de los auriculares y controladores de movimiento de realidad mixta de Windows es la culminante de un esfuerzo de equipo masivo y un importante paso adelante para la [plataforma Windows Mixed Reality](mixed-reality.md), que incluye [Microsoft HoloLens](hololens-hardware-details.md). Aunque HoloLens no recibe una actualización con la versión de Windows 10 Fall Creators Update, sabe que el trabajo en HoloLens no se ha detenido. tendremos una gran cantidad de aprendizajes e información para aplicarnos desde nuestro trabajo reciente en Windows Mixed Reality en conjunto. De hecho, Windows Mixed Reality y los controladores de movimiento presentan un excelente punto de entrada al desarrollo de HoloLens, ya que las mismas API, herramientas y conceptos se aplican a ambos.

Para actualizar a la versión más reciente de cada dispositivo, abra la aplicación de **configuración** , vaya a **Actualizar & seguridad**y, a continuación, seleccione el botón **Buscar actualizaciones** . En un equipo con Windows 10, también puede instalar manualmente Windows 10 Fall Creators Update con la [herramienta de creación de Windows Media](https://www.microsoft.com/software-download/windows10).

 **Versión más reciente del escritorio:** Windows 10 Desktop 2017 de octubre (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Versión más reciente de HoloLens:** [Windows 10 Holographic 2016 de agosto](release-notes-august-2016.md) (**10.0.14393.0**, actualización de aniversario de Windows 10)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introducción a Windows Mixed Reality

Windows 10 Fall Creators Update incorpora oficialmente compatibilidad con auriculares y controladores de movimiento de realidad mixta de Windows, así como para que Windows 10 sea el primer sistema operativo espacial del mundo. Estos son los aspectos destacados:
* **[Variedad de auriculares](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** : Windows Mixed Reality permite que los asociados ofrezcan una variedad de auriculares que se inician a $399 USD con controladores de movimiento.
* **[Controladores de movimiento](motion-controllers.md)** : los controladores de movimiento de Windows Mixed Reality se emparejan de forma inalámbrica con su equipo a través de Bluetooth y incluyen un seguimiento de seis grados de libertad, una gran cantidad de métodos de entrada y Imus.
* **[Instalación y portabilidad fáciles](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** : Configure y empiece en menos de 10 minutos. Los auriculares envolventes usan el seguimiento interior para realizar el seguimiento del movimiento y los controladores de movimiento, con seis grados de libertad. No se requiere ninguna cámara externa ni marcadores de Lighthouse.
* **[Compatibilidad con una gama más amplia de equipos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** : Windows Mixed Reality permite que más personas experimenten Desktop VR que nunca, con compatibilidad con tarjetas gráficas y equipos integrados de selección, a partir de $499 USD.
* **[Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md)** : el primer sistema operativo espacial del mundo proporciona un entorno doméstico familiar para la multitarea con aplicaciones 2D, el inicio de juegos y aplicaciones de VR y la colocación de hologramas decorativos.
* **[Sorprendentes aplicaciones y juegos de la plataforma en el Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** : desde entretenimiento inmersivo como Hulu vr y 360 video a juegos de epopeya como SUPERHOT VR y Arizona sol, el Microsoft Store tiene una variedad de contenido para experimentar en Windows Mixed Reality.
* **[SteamVR Early Access](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** : Windows 10 Fall Creators Update permite reproducir los títulos de SteamVR con auriculares y controladores de realidad mixta de Windows, lo que hace que el catálogo más grande de los títulos de VR esté disponible para los usuarios de Windows Mixed Reality.

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado mucho para ofrecer una excelente experiencia de realidad mixta de Windows, pero todavía estamos realizando un seguimiento de algunos problemas conocidos. Si encuentra otras personas, envíenos [sus comentarios](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicación de escritorio en la Página principal de Windows Mixed Reality
* Recortes no funciona en la aplicación de escritorio.
* La configuración de la aplicación de escritorio no se mantiene al volver a iniciarla.
* Si usa la versión preliminar del portal de realidad mixta en el escritorio, al abrir la aplicación de escritorio en la Página principal de Windows Mixed Reality, es posible que observe el efecto de reflejo infinito. 
* La ejecución de la aplicación de escritorio puede producir problemas de rendimiento en equipos que no son de alta calidad de Windows. no se recomienda.  
* La aplicación de escritorio puede iniciarse automáticamente porque una ventana invisible en el escritorio tiene el foco. 
* El aviso de control de cuentas de usuario de escritorio hará que el casco se muestre en negro hasta que se complete el aviso.

### <a name="windows-mixed-reality-setup"></a>Configuración de Windows Mixed Reality
* Al configurar Windows con un auricular conectado, el monitor de PC puede dejar de estar en blanco. Desenchufe los auriculares para habilitar la salida en el monitor de PC para completar la instalación de Windows.
* Al crear un límite, puede producirse un error de seguimiento. Si es así, inténtelo de nuevo, ya que el sistema obtendrá más información sobre el espacio a lo largo del tiempo.
* Si activa o desactiva Cortana durante la configuración de Windows Mixed Reality, este cambio se aplicará a la configuración de Cortana de escritorio.
* Si no tiene auriculares conectados, es posible que se pierdan sugerencias adicionales cuando visite por primera vez la Página principal de Windows Mixed Reality.
* Los auriculares Bluetooth pueden producir interferencias con los controladores de movimiento. Se recomienda desemparejar o apagar controladores Bluetooth durante las sesiones de Windows Mixed Reality.

### <a name="games-and-apps-from-windows-store"></a>Juegos y aplicaciones de la tienda Windows
* Algunos juegos con un uso intensivo de gráficos, como Forza Motorsports 6, pueden provocar problemas de rendimiento en equipos menos compatibles cuando se reproducen dentro de Windows Mixed Reality.

### <a name="audio"></a>Audio
* Como se indicó anteriormente, los periféricos de audio Bluetooth no funcionan bien con las experiencias de voz y sonido espacial de Windows Mixed Reality. También pueden afectar negativamente a la experiencia del controlador de movimiento. No se recomienda usar auriculares de audio Bluetooth con Windows Mixed Reality.
* No se puede usar el dispositivo de audio conectado a (o parte de) los auriculares para la reproducción de audio cuando no se está gastando el dispositivo. Si solo tiene un casco de audio, es posible que desee conectar los auriculares de audio al equipo host en lugar de los auriculares. En ese caso, debe desactivar la opción "cambiar a audio con auriculares" en **configuración** > **audio y voz**de**realidad** > mixta.
* Algunas aplicaciones, incluidas muchas de las que se inician a través de SteamVR, pueden perder audio o bloquearse cuando el dispositivo de audio cambia cuando se inicia o se detiene el portal de realidad mixta. Reinicie la aplicación después de abrir la aplicación del portal de realidad mixta para corregir este comportamiento.
* Si tiene Cortana habilitada en el equipo host antes de usar el casco de la realidad mixta de Windows, puede perder la simulación de sonido espacial aplicada a las aplicaciones que coloca en la Página principal de Windows Mixed Reality. La solución consiste en habilitar "Sonic de Windows para auriculares" en todos los dispositivos de audio conectados al equipo, incluso en el dispositivo de audio conectado con auriculares:
   1. Haga clic con el botón izquierdo en el icono de altavoz de la barra de tareas del escritorio y seleccione de la lista de dispositivos de audio.
   2. Haga clic con el botón secundario en el icono de altavoz de la barra de tareas del escritorio y seleccione "Windows Sonic para auriculares" en el menú "configuración del altavoz".
   3. Repita estos pasos para todos los dispositivos de audio (puntos de conexión).
>[!NOTE]
> - Dado que los auriculares o altavoces conectados al casco no aparecerán a menos que lo consigas, tienes que hacerlo desde la ventana de la aplicación de escritorio en la Página principal de Windows Mixed Reality para aplicar esta configuración al dispositivo de audio conectado a tu casco (o integrado en el casco).
> - Otra opción consiste en desactivar "permitir que Cortana responda a Hola Cortana" en **configuración** > **Cortana** en el escritorio antes de iniciar Windows Mixed Reality.

* Cuando otro dispositivo USB multimedia (como una cámara web) comparte el mismo concentrador USB (ya sea externo o dentro de su PC) con el casco de realidad mixta de Windows, en raras ocasiones, es posible que el Jack o los auriculares de audio del casco tengan un sonido sonoro o que no haya audio. Puede corregirlo mediante los auriculares en un puerto USB que no comparta el mismo concentrador que el otro dispositivo o desconectar o deshabilitar el otro dispositivo multimedia USB.
* En raras ocasiones, el concentrador USB del equipo host no puede proporcionar suficiente energía para los auriculares de la realidad mixta de Windows y es posible que observe una ráfaga de ruido de los auriculares conectados al casco.

### <a name="speech"></a>Voz
* Cortana puede no reproducir sus señales de audio para escuchar, pensar y responder a los comandos.
* Cortana en los mercados de China y Japón no muestra correctamente el texto debajo del círculo de Cortana durante el uso.
* Cortana puede ser lento la primera vez que se invoca en una sesión de portal de realidad mixta. Para solucionar este tema, asegúrese de que "permitir que Cortana responda a Hola Cortana" en **configuración** > **Cortana** > **hablar con Cortana** está habilitada.
* Cortana puede ejecutarse más lentamente en equipos que no son equipos con Windows Mixed Reality.
* Cuando el teclado del sistema se establece en un idioma distinto del idioma de la interfaz de usuario de Windows Mixed Reality, el uso del dictado del teclado en Windows Mixed Reality dará como resultado un cuadro de diálogo de error que indica que el dictado no funciona debido a que no tiene conexión Wi-Fi. Para corregir el problema, asegúrese simplemente de que el idioma del teclado del sistema coincide con el idioma de la interfaz de usuario de Windows Mixed Reality.
* España no se reconoce correctamente como un mercado en el que la voz está habilitada para Windows Mixed Reality.

### <a name="holograms"></a>Hologramas
* Si ha colocado un gran número de hologramas en su página principal de Windows Mixed Reality, algunos pueden desaparecer y volver a aparecer mientras busca. Para evitar esto, quite algunos de los hologramas en esa área de la Página principal de Windows Mixed Reality.

### <a name="motion-controllers"></a>Controladores de movimiento
* En ocasiones, si hace clic en una página web en Edge, el contenido se acercará en lugar de hacer clic en él.
* A veces, cuando se hace clic en un vínculo en Edge, la selección no funcionará.

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Compatibilidad con auriculares envolvente (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Problemas conocidos de HoloLens](hololens-known-issues.md)
* [Instalación de las herramientas](install-the-tools.md)
* [Comentarios](give-us-feedback.md)
