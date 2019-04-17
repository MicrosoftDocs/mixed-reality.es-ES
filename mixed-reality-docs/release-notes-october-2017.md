---
title: Notas de la versión - octubre de 2017
description: Notas de la versión de Windows Mixed Reality para el Windows 10 Fall Creators Update (octubre de 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: release notes, versión, windows 10, compilación, rs3, sistema operativo
ms.openlocfilehash: 7274dcf1db449fa35981eb72192fea9873fcc90a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597828"
---
# <a name="release-notes---october-2017"></a>Notas de la versión - octubre de 2017

Bienvenido a la realidad mixta de Windows! La versión de la **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** introduce compatibilidad con los nuevos [inmersivos Windows Mixed Reality](immersive-headset-hardware-details.md) y [controladores de movimiento ](motion-controllers.md), lo que le permite explorar nuevos mundos, jugar a juegos VR y experiencia de entretenimiento envolvente cuando se conecta a un [equipos aptos para Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

El lanzamiento de auriculares de realidad mixta de Windows y los controladores de movimiento es la culminación de un trabajo en equipo masivos y un gran avance para la [plataforma Windows Mixed Reality](mixed-reality.md), que incluye [Microsoft HoloLens](hololens-hardware-details.md). Mientras HoloLens no están recibiendo una actualización con el lanzamiento de Windows 10 Fall Creators Update, sabe que no se ha detenido el trabajo en HoloLens; tendremos bastantes conocimientos e información para aplicar de nuestro reciente trabajo a través de Windows Mixed Reality como un todo. De hecho, inmersivos Windows Mixed Reality y movimiento controladores representan una excelente entrada apuntan al desarrollo para HoloLens demasiado, como las mismas API, herramientas, y los conceptos se aplican a ambos.

Para actualizar a la versión más reciente para cada dispositivo, abra el **configuración** aplicación, vaya a **actualización y seguridad**, a continuación, seleccione el **buscar actualizaciones** botón. En un equipo con Windows 10, puede instalar manualmente el uso de Windows 10 Fall Creators Update la [herramienta de creación de Windows media](https://www.microsoft.com/software-download/windows10).

 **Última versión de escritorio:** Escritorio de Windows 10 de octubre de 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Versión más reciente para HoloLens:** [Windows 10 Holographic de agosto de 2016](release-notes-august-2016.md) (**10.0.14393.0**, actualización de aniversario de Windows 10)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introducción a Windows Mixed Reality

El Windows 10 Fall Creators Update oficialmente introduce compatibilidad con auriculares de realidad mixta de Windows y los controladores de movimiento, así como realizar primer sistema operativo espacial de todo el mundo de Windows 10. Estos son los aspectos destacados:
* **[Gran variedad de auriculares](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)**  -Windows Mixed Reality es permitir que los asociados ofrecen una variedad de auriculares que hayan empezado en 399 USD incluido con los controladores de movimiento.
* **[Controladores de movimiento](motion-controllers.md)**  -controladores de Windows Mixed Reality movimiento inalámbrica emparejar con su PC a través de Bluetooth y seis grados de libertad de seguimiento, una gran cantidad de métodos de entrada y IMUs de características.
* **[Instalación fácil y portabilidad](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)**  : Configure configurar y empezar a trabajar en menos de 10 minutos. Inmersivos utilizar el seguimiento de por completo para realizar un seguimiento de su movimiento y los controladores de movimiento, con seis grados de libertad. ¡Ningún cámaras externas o marcadores de lighthouse necesarios!
* **[Compatibilidad con un intervalo más amplio de equipos](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)**  -Windows Mixed Reality permitirá que más personas a la experiencia de escritorio VR que nunca, con compatibilidad con select integrada tarjetas gráficas y equipos a partir de 499 USD.
* **[Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md)**  -primer sistema de operativo espaciales del mundo proporciona un entorno de inicio familiar para multitarea con aplicaciones 2D, al iniciar juegos de realidad virtual y las aplicaciones y poner hologramas decorativos.
* **[Increíbles juegos de realidad virtual y aplicaciones en la Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)**  : en entretenimiento envolvente como Hulu VR y 360 vídeo juegos epic como VR SUPERHOT y Arizona sol, la Microsoft Store tiene un intervalo de contenido para experimentar en mixto de Windows Realidad.
* **[Acceso anticipado SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)**  : The Windows 10 Fall Creators Update habilita la compatibilidad con los títulos de SteamVR para que se reproduzca con auriculares de realidad mixta de Windows y controladores, hacer que el catálogo más grande de VR titles disponible para Windows mixto Usuarios de la realidad.

## <a name="known-issues"></a>Problemas conocidos

Hemos trabajado duro para ofrecer una excelente experiencia de Windows Mixed Reality, pero todavía estamos realizando un seguimiento algunos problemas conocidos. Si encuentra otros, [enviarnos comentarios](give-us-feedback.md).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Aplicación de escritorio en el inicio de Windows Mixed Reality
* Herramienta recortes no funciona en una aplicación de escritorio.
* Aplicación de escritorio no conserva la configuración al volver a iniciar.
* Si usas un vista previa del Portal de realidad mixta en el escritorio, al abrir la aplicación de escritorio en el inicio de Windows Mixed Reality, puede observar el efecto de espejo infinito. 
* Ejecuta la aplicación de escritorio puede provocar problemas de rendimiento en no - Ultra Mixed Reality equipos con Windows; no se recomienda.  
* Aplicación de escritorio puede iniciar automáticamente porque una ventana invisible en escritorio tiene el foco. 
* Control de cuentas de usuario de escritorio símbolo del sistema hará auriculares mostrar negro hasta que se complete el símbolo del sistema.

### <a name="windows-mixed-reality-setup"></a>Programa de instalación de Windows Mixed Reality
* Al configurar Windows con un auricular conectado, el monitor del equipo puede entrar en blanco. Desconecte los auriculares para habilitar la salida en el monitor de equipo para completar la instalación de Windows.
* Al crear un límite, se puede producir un error en el seguimiento. Si es así, vuelva a intentarlo, como el sistema aprenderemos más cosas sobre el espacio con el tiempo.
* Si activa la Cortana activado o desactivado durante la instalación de Windows Mixed Reality, este cambio se aplicará a la configuración del escritorio Cortana.
* Si no tiene los auriculares conectados, se pueden perder sugerencias adicionales cuando visite por primera vez el inicio de Windows Mixed Reality.
* Auriculares Bluetooth pueden causar interferencias con controladores de movimiento. Se recomienda desemparejamiento o apagar los controladores de Bluetooth durante las sesiones de Windows Mixed Reality.

### <a name="games-and-apps-from-windows-store"></a>Juegos y aplicaciones de Windows Store
* Algunos juegos con muchos gráficos, como Forza Motorsports 6, pueden causar problemas de rendimiento en equipos con menor capacidad cuando reproduce dentro de Windows Mixed Reality.

### <a name="audio"></a>Audio
* Como se mencionó anteriormente, periféricos de Bluetooth Audio no funcionan bien con voz de Windows Mixed Reality y experiencias espaciales de sonido. Negativamente también pueden afectar a su experiencia de controlador de movimiento. No se recomienda usar auriculares de Bluetooth Audio con Windows Mixed Reality.
* No se puede usar el dispositivo conectado al audio (o parte de) los auriculares para reproducción de audio cuando el dispositivo no está agotado. Si solo tiene un auriculares de audio, desea conectar los auriculares de audio al equipo host en lugar de los auriculares. Si por lo tanto, a continuación, debe desactivar la opción "cambiar a audio auriculares" **configuración** > **Mixed Reality** > **Audio y voz**.
* Algunas aplicaciones, incluidos muchos de los iniciados mediante SteamVR, pueden perder el audio o responder cuando el dispositivo de audio cambia como iniciar o detener el Portal de realidad mixta. Después de haber abierto la aplicación de Portal de realidad mixta para corregir este problema, reinicie la aplicación.
* Si tiene Cortana habilitado en el equipo host antes de usar los auriculares de Windows Mixed Reality, puede perder la simulación de sonido espacial aplicada a las aplicaciones que coloque en torno a Windows Mixed Reality principal. La solución alternativa es permitirle "Windows Sonic para auriculares" en todos los dispositivos de audio conectados a su equipo, incluso los auriculares audio dispositivo conectado:
   1. Haga clic en el icono Altavoz de la barra de tareas de escritorio y seleccione en la lista de dispositivos de audio.
   2. Haga clic en el icono Altavoz de la barra de tareas de escritorio y seleccione "Windows Sonic para auriculares" en el menú "Configuración de altavoces".
   3. Repita estos pasos para todos los dispositivos de audio (extremos).
>[!NOTE]
> - Dado que los auriculares o altavoces conectados a los auriculares no aparecerá a menos que se están gastando, tendrá que hacerlo desde la ventana de aplicación de escritorio en el Windows Mixed Reality doméstica para aplicar esta configuración para el dispositivo de audio conectado a los auriculares (o integrado en los auriculares).
> - Otra opción consiste en desactivar "Cortana permiten responder a Hola Cortana" en **configuración** > **Cortana** en el escritorio antes de iniciar Windows Mixed Reality.

* Cuando otro dispositivo USB multimedia (por ejemplo, una cámara web) comparte el mismo concentrador USB (externo o dentro de su equipo) con los auriculares de realidad mixta de Windows, en raras ocasiones audio jack/auriculares de los auriculares puede tener un sonido zunbido o sin audio en absoluto. Puede corregir esto por los auriculares en un puerto USB que no comparten el mismo concentrador que el otro dispositivo o desconectar o deshabilitar su otro dispositivo multimedia USB.
* En muy raras ocasiones, concentrador USB del equipo de host no puede proporcionar suficiente capacidad para los auriculares de realidad mixta de Windows y es posible que observe una ráfaga de ruido de los auriculares conectados a los auriculares.

### <a name="speech"></a>Voz
* Cortana puede producir un error al reproducir sus indicaciones de sonido para escuchar/pensamiento y audio respuestas a los comandos.
* Cortana en los mercados de China y Japón no mostrar correctamente texto debajo el círculo de Cortana durante el uso.
* Cortana puede ser lento en la primera vez que se invoca en una sesión del Portal de realidad mixta. Puede solucionar esto mediante la realización de seguro "permitir que Cortana" responder a Hola Cortana en **configuración** > **Cortana** > **hablar a Cortana** es habilitada.
* Cortana puede ser lento en equipos que no sean Windows Mixed Reality Ultra PC.
* Cuando el teclado del sistema se establece en un idioma distinto del idioma de interfaz de usuario de Windows Mixed Reality, uso el dictado del teclado en Windows Mixed Reality dará como resultado un cuadro de diálogo de error sobre el dictado no funciona debido a no tener conexión Wi-Fi. Para corregir el problema simplemente asegúrese de que el idioma de teclado del sistema coincida con el idioma de interfaz de usuario de Windows Mixed Reality.
* España no es que se reconozca correctamente como un mercado donde está habilitada voz para Windows Mixed Reality.

### <a name="holograms"></a>Hologramas
* Si ha colocado un gran número de hologramas en el inicio de Windows Mixed Reality, algunos pueden desaparecer y volverán a aparecer como echa un vistazo alrededor. Para evitar este problema, quite algunas de las hologramas en esa área de Windows Mixed Reality principal.

### <a name="motion-controllers"></a>Controladores de movimiento
* En ocasiones, si hace clic en una página Web en Edge, irá el contenido en lugar de hacer clic.
* En ocasiones, al hacer clic en un vínculo en Edge, la selección no funcionará.

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión - agosto de 2016](release-notes-august-2016.md)
* [Notas de la versión - mayo de 2016](release-notes-may-2016.md)
* [Notas de la versión: marzo de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Soporte técnico de auriculares envolventes (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Problemas conocidos de HoloLens](hololens-known-issues.md)
* [Instalar las herramientas](install-the-tools.md)
* [Envíenos sus comentarios](give-us-feedback.md)
