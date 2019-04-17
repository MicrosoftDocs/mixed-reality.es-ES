---
title: Notas de la versión - mayo de 2016
description: Notas de la versión para Windows Holographic HoloLens pueden actualizarse a 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de la versión del sistema operativo, características, compilación, plataforma
ms.openlocfilehash: bc4e09c36a3ab6643be1144873a624fc5ed66e37
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605501"
---
# <a name="release-notes---may-2016"></a>Notas de la versión - mayo de 2016

El equipo de HoloLens se compromete a proporcionarle una actualización en nuestra última hora de desarrollar características y correcciones importantes a través del programa de Windows Insider. Gracias a todas sus sugerencias, tomamos los comentarios en serio. Continúe para [enviarnos comentarios](give-us-feedback.md) a través del centro de comentarios, la [foros para desarrolladores de](https://forums.hololens.com) y [a través de Twitter @HoloLens ](https://twitter.com/hololens).

**Versión de lanzamiento:** Actualización de Windows Holographic de mayo de 2016 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Para actualizar a la versión actual, abra el *configuración* aplicación, vaya a *actualización y seguridad*, a continuación, seleccione el *buscar actualizaciones* botón.

## <a name="new-features"></a>Nuevas características

* Ahora puede **ejecutar hasta tres aplicaciones en la vista 2D simultáneamente**. Esto permite que los casos de uso sin fin para multitarea en HoloLens. Tener el nuevo centro de comentarios con la lista de programas abiertos durante la exploración de las nuevas características en este vuelo.

  ![HoloLens pueden ejecutar tres aplicaciones al mismo tiempo](images/img-3625-400px.jpg)<br>
  Ejecutar hasta tres aplicaciones en la vista 2D simultáneamente

* Hemos agregado nuevas **comandos de voz**:
   * Pruebe a buscar en un holograma y girarlo diciendo "se enfrentan a mí"
   * Cambiar su tamaño diciendo "mayores" o "menores"
   * Mover una aplicación diciendo: "Hola Cortana, mover *nombre de la aplicación* aquí."
* Hemos realizado **desarrollando en HoloLens más fácil**. Ahora puede examinar, cargar y descargar archivos a través de la [Windows Device Portal](using-the-windows-device-portal.md). Puede tener acceso a la carpeta documentos, carpeta imágenes y el almacenamiento local para cualquier aplicación de carga lateral o implementado a través de Visual Studio.
* El **emulador ahora admite el inicio de sesión con una Account Microsoft** tal como lo haría en un HoloLens real. Puede habilitar esta opción en el menú Herramientas adicionales ">>".
* **Aplicaciones 2D ahora ocultan la barra de la aplicación y el cursor cuando se ve el vídeo en pantalla completa** para evitar la distracción. Con esto, su experiencia viendo vídeo será aún más divertida en HoloLens.
* También puede **anclar fotografías sin la barra de la aplicación** en el mundo.

  ![Se puede ocultar la barra de aplicaciones para aplicaciones de 2D como fotos](images/img-3626-400px.jpg)<br>
  Se puede ocultar la barra de aplicaciones para las aplicaciones con una vista 2D, como fotos
  
* **Selector de archivos** funciona tal como se espera que en HoloLens.
* Actualizar **explorador Edge** para asignar la experiencia de usuario unificadas con el escritorio y teléfono. Hemos habilitado varias instancias de su explorador, HoloLens nueva página de ficha personalizada, peek pestaña y abierto en nuevas ventanas, junto con las mejoras de potencia y rendimiento.
* **Groove música** aplicación ya está en HoloLens. Visite la tienda para descargarlo e intente reproducir en segundo plano.
* Puede personalizar fácilmente cómo las aplicaciones se organizan en el mundo. Pruebe **girar sus hologramas** en ajustar el modo, simplemente haga clic y arrastre en un círculo en las tramas de alambres vertical central. Es posible que observe hologramas tienen **estricta ajustada rectángulos** para garantizar la interacción maximizada. También puede cambiar el tamaño todas las aplicaciones sin formato verticalmente (excepto las fotos y holograma aplicaciones).

  ![Se pueden girar hologramas después de colocarlos en el mundo](images/img-3627-400px.jpg)<br>
  Girar hologramas después de colocarlos en el mundo

* Hemos realizado una gran cantidad de **entrada mejora** en este curso es elevado. Puede conectar un mouse Bluetooth regular a HoloLens. El clicker ha sido bien ajustados para habilitar el cambio de tamaño de & Mover hologramas con un clicker. Teclado también se ejecuta mejor que nunca.
* Ahora puede controlar **mixto imágenes realidad** , basta con presionar presionadas las Subir volumen + Bajar volumen simultáneamente. También puede compartir sus fotografías de realidad mixta capturada y los vídeos para Facebook, Twitter y YouTube.
* La longitud máxima de grabación de **mixto vídeos realidad** ha aumentado a cinco minutos.
* **Aplicación fotos** ahora transmite vídeos desde OneDrive, en lugar de tener que descargar todo el vídeo antes de la reproducción.
* Hemos mejorado cómo su **hologramas estará contento se dejaron**. También verá la opción de volver a conectarse a Wi-Fi e inténtelo de nuevo si no pueden detectar HoloLens donde estén.
* El teclado tiene un **diseño mejorado para escribir la dirección de correo electrónico** con claves que podrá escribir el correo electrónico más popular haga clic en dominios con un único.
* Con mayor rapidez **registro de la aplicación** y **auto detección de zona horaria** durante OOBE, lo que le ofrece el primer usuario mejor experiencia.
* **Sensor de almacenamiento** le permite ver el espacio en disco restante y utilizado por el sistema y las aplicaciones en la aplicación configuración.
* Nos hemos convergente aplicación de comentarios y dentro de Hub en una sola aplicación **centro comentarios** que será la herramienta preferida para **y Proporciónenos comentarios**, las características que le encanta, las características que podría hacer sin o cuando algo podría ser mejor. Cuando se une al programa Insider, puede mantenerse al día **obtener las últimas noticias de Insider**, **calificar las compilaciones** e ir **programas de comentarios** desde el centro de opiniones.
* Hemos también [publicado un emulador de HoloLens actualizada](install-the-tools.md) de compilación.
* Los vídeos de realidad mixta aspecto mejor debido a automático **estabilización de vídeo**.

## <a name="major-fixes"></a>Correcciones importantes

Se ha corregido problemas con espacios holograma donde los espacios sería lenta o detectado incorrectamente. Se ha corregido un problema de cierre que podría seguir intente iniciar el shell durante el cierre.

Se ha corregido un problema
* que bloquea la capacidad de reanudar una aplicación XAML.
* donde un bloqueo dejaría a una pantalla en negro y algunos las líneas irregulares.
* desplazamiento a veces podría quedarse en la dirección equivocada al usar algunas aplicaciones.
* la potencia LED podrían indicar un estado desactivado cuando el dispositivo ha estado aún activado.
* Wi-Fi podría obtener desactivado después de reanudar en modo de espera.
* el proveedor de identidades de Xbox ofrece el programa de instalación de nombre de jugador y, a continuación, se atasca en un bucle.
* el Shell se bloquea en ocasiones, al seleccionar un archivo descargado en el selector de archivos de OneDrive.
* presionando y manteniendo presionado en un vínculo a veces, abre una pestaña nueva, rota tanto abre un menú contextual.
* donde el portal de dispositivos de windows no permitía que los ajustes de IPD de 50 a 80

Se ha corregido problemas con fotografías donde
* en ocasiones, puede mostrar una imagen girado debido a que se omitirá la propiedad orientation EXIF.
* podría bloquearse durante el inicio en fotos ancladas.
* vídeos reiniciaría después de una pausa en lugar de continuar desde donde detenido por última vez.
* reproducción de un vídeo compartido podría evitarse si se compartieran mientras se está reproduciendo.
* Grabaciones de capturar la realidad mixtas comenzaría con 0,5 1 segundo de audio solo avance.
* el botón Sincronizar desaparece durante la sincronización inicial de OneDrive.

Se ha corregido problemas con la configuración donde
* se necesita una actualización cuando cambia el entorno.
* "Escriba" teclado no se comportará como hacer clic en siguiente, en algunos cuadros de diálogo.
* era difícil saber cuándo la clicker no pudo emparejar.
* podría dejar de responder con Wi-Fi desconectar y conectar.

Se ha corregido problemas con Cortana donde
* puede atascarse mostrar la interfaz de usuario a la escucha.
* pedir "Hola Cortana, ¿qué puedo decir" de un modo exclusivo de aplicación quedará bloqueada si quizás en su lugar, sí/no respondió a la solicitud para salir de la aplicación.
* la interfaz de usuario a la escucha de Cortana no se reanuda correctamente si se pide a Cortana para ir al modo de suspensión y, a continuación, reanudar.
* las consultas "qué red me conecté a?" ¿y el "Am I connected"? podría producirse un error cuando vuelve el primer perfil de red sin conectividad.
* la interfaz de usuario se queda bloqueado en "Escucha" pero cuando se sale de una aplicación podría inmediatamente comenzaron a reconocimiento de voz de nuevo.
* donde la sesión de la aplicación de Cortana no permite inicio de sesión en él hasta que se reinicie.
* no iniciarían cuando estaba activa la UI de captura de realidad mixta.

Se ha corregido problemas con Visual Studio donde
* depuración de tareas en segundo plano no ha funcionado.
* análisis de fotogramas en el depurador de gráficos no funcionó.
* el emulador de HoloLens no estaba en la lista desplegable para Visual Studio a menos que TargetPlatformVersion su proyecto se estableció en 10240.

## <a name="changes-from-previous-release"></a>Cambios de la versión anterior
* El comando Cortana **Hola Cortana, reiniciar el dispositivo** no funciona. Puede decir usuario **Hola Cortana, reinicie** o **Hola Cortana, reinicie el dispositivo**.
* Se quitó el modo de pantalla completa del producto.

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión: marzo de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vea también
* [Problemas conocidos de HoloLens](hololens-known-issues.md)
* [Instalar las herramientas](install-the-tools.md)
* [Shell](navigating-the-windows-mixed-reality-home.md)
* [Actualización de aplicaciones UWP 2D de realidad mixta](building-2d-apps.md)
* [Accesorios de hardware](hardware-accessories.md)
* [Captura de realidad mixta](mixed-reality-capture.md)
* [Entrada de voz](voice-input.md)
* [Envío de una aplicación para el Store de Windows](submitting-an-app-to-the-microsoft-store.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
