---
title: 'Notas de la versión: mayo 2016'
description: Notas de la versión de HoloLens para la actualización 2016 de Windows Holographic.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de la versión, sistema operativo, características, compilación, plataforma
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524570"
---
# <a name="release-notes---may-2016"></a>Notas de la versión: mayo 2016

El equipo de HoloLens se compromete a proporcionarle una actualización sobre el desarrollo de características más reciente y las principales correcciones a través del programa Windows Insider. Gracias a todas sus sugerencias, tomamos sus comentarios en esencia. Envíenos [sus comentarios](give-us-feedback.md) a través del centro de comentarios, los [foros para desarrolladores](https://forums.hololens.com) y [Twitter @HoloLensa través ](https://twitter.com/hololens)de.

**Versión de lanzamiento:** Actualización de Windows Holographic 2016 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Para actualizar a la versión actual, abra la aplicación de *configuración* , vaya a *Actualizar & seguridad*y, a continuación, seleccione el botón *Buscar actualizaciones* .

## <a name="new-features"></a>Nuevas características

* Ahora puede **ejecutar hasta tres aplicaciones en la vista 2D simultáneamente**. Esto permite casos de uso infinitos para la multitarea en HoloLens. Tenga el nuevo centro de comentarios con la lista de las comprobaciones abiertas mientras explora las nuevas características de este vuelo.

  ![HoloLens puede ejecutar tres aplicaciones al mismo tiempo](images/img-3625-400px.jpg)<br>
  Ejecutar hasta tres aplicaciones en la vista 2D simultáneamente

* Hemos agregado nuevos **comandos de voz**:
   * Intente mirar un holograma y girarlo diciendo "me me digo"
   * Cambiar su tamaño diciendo "mayor o menor"
   * Mueva una aplicación diciendo "Hola Cortana, mueva *el nombre* de la aplicación aquí".
* Hemos facilitado el **desarrollo en HoloLens**. Ahora puede examinar, cargar y descargar archivos a través del [portal de dispositivos de Windows](using-the-windows-device-portal.md). Puede tener acceso a la carpeta documentos, a la carpeta imágenes y al almacenamiento local de cualquier aplicación que se haya cargado o implementado a través de Visual Studio.
* El **emulador ahora admite el inicio de sesión con una cuenta de Microsoft** tal como lo haría en una HoloLens real. Puede habilitarlo en el menú herramientas adicionales "> >".
* **las aplicaciones 2D ahora ocultan la barra de la aplicación y el cursor al ver la pantalla completa de vídeo** para evitar la distracción. Con esto, su experiencia de visualización de vídeo será aún más agradable en HoloLens.
* También puede **anclar fotos sin la barra de la aplicación** en su mundo.

  ![La barra de la aplicación se puede ocultar para aplicaciones en 2D como fotos](images/img-3626-400px.jpg)<br>
  La barra de la aplicación se puede ocultar para aplicaciones con una vista 2D, como fotos
  
* El **selector de archivos** funciona como se espera en HoloLens.
* **Explorador Edge** actualizado para asignar experiencia de usuario unificada con escritorio y teléfono. Hemos habilitado varias instancias del explorador, la página de pestañas nueva de HoloLens personalizada, el método de inspección de pestañas y la apertura en nuevas ventanas, junto con las mejoras de rendimiento de Power &.
* La aplicación **Groove Music** está ahora en HoloLens. Visite la tienda para descargarla y pruebe a reproducirla en segundo plano.
* Puede personalizar fácilmente el modo en que las aplicaciones están organizadas en su mundo. Intente **girar los hologramas** en el modo ajustar simplemente haga clic y arrastre el círculo en los tramas de alambres verticales del centro. Es posible que observe que los hologramas tienen **cuadros de límite ajustados** para garantizar una interacción maximizada. También puede cambiar el tamaño de todas las aplicaciones sin formato verticalmente (excepto las aplicaciones fotos y hologramas).

  ![Los hologramas se pueden girar después de colocarlos en el mundo](images/img-3627-400px.jpg)<br>
  Gire los hologramas después de colocarlos en su mundo

* Hemos realizado una gran cantidad de **mejoras de entrada** en este vuelo. Puede conectar un mouse Bluetooth normal a HoloLens. El clic se ha optimizado para habilitar el cambio de tamaño & mover hologramas con un clic. El teclado también se ejecuta mejor que nunca.
* Ahora puede tomar **fotografías de realidad mixta** simplemente presionando el volumen subir + volumen simultáneamente. También puede compartir las fotos de la realidad mixta capturadas & vídeos en Facebook, Twitter y YouTube.
* La longitud máxima de grabación de **vídeos de realidad mixta** se ha aumentado a cinco minutos.
* La **aplicación photos** ahora transmite vídeos desde OneDrive en lugar de tener que descargar todo el vídeo antes de la reproducción.
* Hemos mejorado el modo en que los hologramas estarán **justo donde los dejó**. También se le presentará la opción de volver a conectarse a la red Wi-Fi y volver a intentarlo si HoloLens no puede detectar dónde están.
* El teclado tiene un **diseño mejorado para escribir la dirección de correo electrónico** con claves que le permiten especificar los dominios de correo electrónico más populares con un solo clic.
* **Registro de aplicaciones** más rápido y **detección automática de la zona horaria** durante Oobe, lo que le brinda la mejor experiencia de usuario.
* El **sensor de almacenamiento** le permite ver el espacio en disco restante y usado por el sistema y las aplicaciones en la aplicación de configuración.
* Tenemos una aplicación de comentarios convergente y dentro del centro en un solo **centro de comentarios** de la aplicación que será la herramienta de navegación para enviarnos **sus comentarios**, las características que le encantan, las características que puede realizar sin él o cuando algo pudiera ser mejor. Al unirse al programa Insider, puede mantenerse al día sobre las **últimas noticias**de Insider, **tarifas** compilaciones y comentarios sobre las **respuestas** de la central de comentarios.
* También hemos publicado una compilación del emulador de [HoloLens actualizada](install-the-tools.md) .
* Los vídeos de realidad mixta ahora tienen un aspecto mejor debido a la estabilización automática de **vídeo**.

## <a name="major-fixes"></a>Correcciones principales

Se han corregido problemas con espacios de hologramas en los que los espacios serían lentos o incorrectamente detectados. Se corrigió un problema de apagado que podía continuar intentando iniciar el shell durante el cierre.

Se ha corregido un problema
* Esto bloquea la capacidad de reanudar una aplicación XAML.
* en los casos en los que un bloqueo dejaría una pantalla negra y algunas líneas escalonadas.
* en ocasiones, el desplazamiento se centraría en la dirección equivocada al usar algunas aplicaciones.
* los LED de alimentación podrían indicar un estado desactivado cuando el dispositivo todavía estaba encendido.
* Wi-Fi podría desactivarse después de reanudar el estado de espera.
* el proveedor de identidades de Xbox ofrece la configuración de gamertag y se bloquea en un bucle.
* en ocasiones, el Shell se bloquea al seleccionar un archivo descargado en el selector de archivos de OneDrive.
* al presionar y mantener un vínculo a veces, se abre una pestaña nueva y rota y se abre un menú contextual.
* donde Windows Device Portal no permitiera los ajustes de IPD de 50 a 80

Se han corregido problemas con fotos en las que
* en ocasiones, una imagen se muestra girada debido a que se omite la propiedad de orientación EXIF.
* podría bloquearse durante el inicio de las fotos ancladas.
* los vídeos se reiniciaron después de pausar en lugar de continuar desde donde se pausó por última vez.
* la reproducción de un vídeo compartido podría evitarse si se compartía mientras se reproduce.
* Las grabaciones de captura de realidad mixta comenzarían con 0,5-1 segundo de la fuente de solo audio.
* el botón sincronizar desaparece durante la sincronización inicial de OneDrive.

Se han corregido problemas con la configuración donde
* se necesitaba una actualización cuando el entorno cambia.
* ' Entrar ' en el teclado no se comportará como hacer clic en siguiente en algunos cuadros de diálogo.
* era difícil saber cuándo se produjo un error en el emparejamiento del clic.
* podría dejar de responder con la conexión WiFi y conectarse.

Se han corregido problemas con Cortana, donde
* podría quedarse atascado mostrando la interfaz de usuario de escucha.
* preguntar "Hola a Cortana, lo que se puede decir" de una aplicación en modo exclusivo se bloqueará si ha respondido a la solicitud para salir de la aplicación.
* la interfaz de usuario de escucha de Cortana no se reanuda correctamente si pide a Cortana que vaya a suspensión y luego se reanude.
* las consultas "¿a qué red estoy conectado?" y "estoy conectado?" podría producirse un error cuando el primer perfil de red vuelve sin conectividad.
* la interfaz de usuario inmovilizó en "escuchando", pero al salir de una aplicación iniciaría de nuevo el reconocimiento de voz.
* donde el cierre de sesión de la aplicación Cortana no le permitirá volver a iniciar sesión en ella hasta que se reinicie.
* no se iniciaría cuando estaba activa la interfaz de usuario de captura de realidad mixta.

Se han corregido problemas con Visual Studio, donde
* no funciona la depuración de tareas en segundo plano.
* el análisis de fotogramas en el depurador de gráficos no funcionó.
* el emulador de HoloLens no aparecía en la lista desplegable de Visual Studio a menos que el TargetPlatformVersion del proyecto estuviera establecido en 10240.

## <a name="changes-from-previous-release"></a>Cambios con respecto a la versión anterior
* El comando Cortana **Hola Cortana, reiniciar el dispositivo,** no funciona. El usuario puede decir **Hola Cortana, reiniciar** o **Hola Cortana, reiniciar el dispositivo**.
* El modo de quiosco se ha quitado del producto.

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Problemas conocidos de HoloLens](hololens-known-issues.md)
* [Instalación de las herramientas](install-the-tools.md)
* [Interfaz](navigating-the-windows-mixed-reality-home.md)
* [Actualización de aplicaciones para UWP bidimensionales para la realidad mixta](building-2d-apps.md)
* [Accesorios de hardware](hardware-accessories.md)
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Entrada de voz](voice-input.md)
* [Envío de una aplicación a la tienda Windows](submitting-an-app-to-the-microsoft-store.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
