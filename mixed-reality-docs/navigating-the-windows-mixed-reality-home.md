---
title: Navegar por el inicio de Windows Mixed Reality
description: HoloLens y Windows Mixed Reality auriculares comparten un paradigma para iniciar, colocar y manipular las aplicaciones y modelos 3D en su entorno (ya sea física o digital). Obtenga información sobre cómo navegar por Windows Mixed Reality principal en ambos tipos de dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, sistema operativo, plataforma, casa cliff, casa, inicio, entorno, inicio, menú Inicio, menú Inicio, PIN, aplicación, inicien las aplicaciones, coloque las aplicaciones, teleport, mover, desplazarse
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605743"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navegar por el inicio de Windows Mixed Reality

Al igual que la experiencia de PC de Windows se inicia con el escritorio, Windows Mixed Reality comienza con la página principal. El inicio de Windows Mixed Reality aprovecha nuestra capacidad para comprender y navegar por los lugares 3D innata. Con HoloLens, su casa es el espacio físico. Con inmersivos, su casa es un espacio virtual.

Su casa es también donde usará el menú Inicio para abrir y colocar las aplicaciones y el contenido. Puede rellenar su hogar con contenido de realidad mixta y realizar varias tareas mediante el uso de varias aplicaciones al mismo tiempo. Las cosas que se coloca en su hogar permanecen allí, incluso si reinicia el dispositivo.

## <a name="start-menu"></a>Menú Inicio

![Menú Inicio en Microsoft HoloLens](images/start-500px.png)

El menú Inicio consta de:
* Información del sistema (estado de la red, el porcentaje de batería, la hora actual y volumen)
* Cortana (en inmersivos, un icono de inicio; en HoloLens, en la parte superior de inicio)
* Aplicaciones ancladas
* El botón aplicaciones todo (signo más)
* Botones de fotos y vídeos para [mixto captura realidad](mixed-reality-capture.md)

Cambiar entre las aplicaciones ancladas y todas las aplicaciones vistas seleccionando el signo más o menos botones. Para abrir el menú Inicio en HoloLens, utilice el gesto de bloom. En un auricular envolvente, presione el botón de Windows en el controlador.

## <a name="launching-apps"></a>Ejecución de aplicaciones

Para iniciar una aplicación, selecciónela en el inicio. Desaparecerá el menú Inicio y la aplicación se abrirá en modo de selección de ubicación, como una ventana de 2D o un [modelo 3D](implementing-3d-app-launchers.md).

Para ejecutar la aplicación, necesita lo coloca en su hogar:
1. Use su [que mirar](gaze.md) o un controlador para colocar la aplicación donde desee. Se ajustará automáticamente (en el tamaño y posición) para ajustarse al espacio donde colocarlo.
2. Colocar la aplicación mediante la derivación de aire (HoloLens) o el botón de selección (inmersivos). Para cancelar y vuelva a colocar el menú Inicio, utilice el gesto de bloom o en el botón de Windows.

[Aplicaciones 2D](building-2d-apps.md), creado para el escritorio, portátiles o Xbox puede modificar para ejecutarse como aplicaciones de realidad mixta envolventes mediante el [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Una aplicación envolvente lleva al usuario fuera de la página principal y en una experiencia envolvente. Los usuarios pueden devolver de inicio con el gesto de bloom (HoloLens) o al presionar el botón de Windows en su controlador (inmersivos).

También se pueden iniciar las aplicaciones a través de una aplicación a la aplicación API o a través de Cortana.

![Aplicaciones en el inicio de Windows Mixed Reality](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Movimiento y ajuste de aplicaciones

Seleccione **ajustar** en la aplicación controla la barra para revelar que mueva, escala, y girar mezclado realidad. Cuando haya terminado, seleccione **realiza**.

![La Pizarra de almacén en el modo de ajuste (marco azul). Tenga en cuenta la barra de la aplicación ha cambiado (superior) para incluir 'Listo' y 'Remove' botones.](images/adjust-500px.png)

Las diferentes aplicaciones pueden tener opciones adicionales en la barra de la aplicación. Por ejemplo, Microsoft Edge tiene *desplazamiento*, *arrastre*, y *Zoom* opciones. 

![Barra de la aplicación para aplicaciones 2D que se ejecutan en HoloLens](images/holobar-500px.png)

El **volver** botón navega a pantallas consultadas anteriormente en la aplicación. Se detendrá cuando se alcanza el principio de las experiencias que se ha demostrado en la aplicación y no se le remitirá a otras aplicaciones.

## <a name="getting-around-your-home"></a>Introducción en su hogar

Con **HoloLens**, que se desplaza por espacio físico para desplazarse por su casa.

Con **inmersivos**, de forma similar, puede ponerse en marcha y andar con su playspace para desplazarse por un área similar en el mundo virtual. Para mover a través de distancias más largas, puede usar la tecla de navegación en el controlador para prácticamente "recorrer", o puede usar *teleportation* inmediatamente saltar distancias más largas.

![Teleportation en el inicio de Windows Mixed Reality](images/teleportation-500px.png)

**Para teleport:**
1. Abrir el retículo teleportation.
   * Uso de [motion controladores](motion-controllers.md): presione la tecla de navegación hacia adelante y manténgalo en esa posición.
   * Uso de un controlador Xbox: presione la tecla de navegación izquierda hacia delante y manténgala en esa posición.
   * Usando un mouse: mantenga presionado el botón secundario (y utilice la rueda de desplazamiento para girar la dirección que desee para afrontar cuando le teleport).
2. Coloque el retículo donde desee teleport.
   * Uso de [motion controladores](motion-controllers.md): inclinar el controlador (en el que se mantiene la tecla de navegación hacia adelante) para mover el retículo.
   * Con un controlador Xbox: use su [que mirar](gaze.md) para mover el retículo.
   * Usar un mouse: mueva el mouse para mover el retículo.
3. Suelte el botón para teleport donde se colocó el retículo.

**Para prácticamente "Tutorial:"**
* Mediante [motion controladores](motion-controllers.md): haga clic en la tecla de navegación y la retención, a continuación, mueva la tecla de navegación en la dirección que desee para "recorrer".
* Uso de un controlador Xbox: haga clic en la tecla de navegación izquierda y la retención, a continuación, mover la tecla de navegación en la dirección que desee para "recorrer".

## <a name="immersive-headset-input-support"></a>Compatibilidad con entrada de auriculares envolventes

[Inmersivos Windows Mixed Reality](immersive-headset-hardware-details.md) admite varios tipos de entrada para navegar por el inicio de Windows Mixed Reality. HoloLens no admite accesorios entradas para la navegación, ya que físicamente andar y vea su entorno. Sin embargo, no HoloLens [admiten entradas](hardware-accessories.md) para interactuar con las aplicaciones.

### <a name="motion-controllers"></a>Controladores de movimiento

Será la mejor experiencia de realidad mixta de Windows con Windows Mixed Reality [controladores de movimiento](motion-controllers.md) ese seguimiento 6 grados de libertad de soporte técnico con solo los sensores en los auriculares - ninguna cámaras externas o marcadores necesarios.

Comandos de navegación próximamente.

### <a name="gamepad"></a>Controlador para juegos
* **Tecla de navegación izquierda:**
  * Presione y mantenga presionada la tecla de navegación izquierda hacia delante para que aparezca el [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) retículo.
  * Pulse la tecla de navegación izquierda, derecha, o realizar una copia para mover a la izquierda, derecha o realizar una copia en incrementos pequeños.
  * Haga clic en la tecla de navegación izquierda y mantenga, a continuación, mueva la tecla de navegación en la dirección que desee [prácticamente "recorrer".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Pulse el **tecla de navegación derecha** izquierda o derecha para girar la dirección se enfrenta con 45 grados.
* Al presionar el **A** botón realiza una instrucción select y actúa como el [en el aire](gestures.md#air-tap) gesto.
* Al presionar el **guía** botón abre el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu) y actúa como el [bloom](gestures.md#bloom) gesto.
* Al presionar el **desencadenadores izquierdos y derecho** permite hace zoom dentro y fuera de una aplicación de escritorio 2D está interactuando con en el hogar.

### <a name="keyboard-and-mouse"></a>Teclado y mouse

**Nota:** Use **tecla Windows + Y** para pasar el mouse entre el control del escritorio de su PC y Windows Mixed Reality principal.

Dentro de la Windows Mixed Reality principal:
* Al presionar el **primario** botón del mouse realiza una instrucción select y actúa como el [en el aire](gestures.md#air-tap) gesto.
* Que contiene el **haga** botón del mouse se abrirá el [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) retículo.
* Al presionar el **Windows** tecla del teclado, se abrirá el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu) y actúa como el [bloom](gestures.md#bloom) gesto.
* Cuando [gazing](gaze.md) en una aplicación de escritorio 2D, es posible **haga clic en** para seleccionar, **haga** para mostrar menús contextuales y usar el **rueda de desplazamiento** desplazamiento (al igual que en el escritorio de su PC).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) es asistente personal en Windows Mixed Reality, exactamente igual que en PC y teléfonos. HoloLens tiene un micrófono integrado, pero inmersivos pueden requerir hardware adicional. Usar Cortana para abrir las aplicaciones, reinicie el dispositivo, buscar cosas en línea y mucho más. Los programadores también pueden elegir [integrar Cortana](https://dev.windows.com/cortana) en sus experiencias.

También puede usar los comandos de voz para obtener en su hogar. Por ejemplo, seleccione un botón (con [que mirar](gaze.md) o un controlador, en función del dispositivo) y diga "Select". Otros comandos de voz incluyen "Go home", "Más grande", "más pequeño," "Cerrar" y "Se enfrentan me."

## <a name="store-settings-and-system-apps"></a>Aplicaciones de Store, la configuración y del sistema

Windows Mixed Reality tiene un número de aplicaciones integradas, como:
* **Microsoft Store** para obtener aplicaciones y juegos
* **Centro de opiniones** para enviar comentarios sobre el sistema y las aplicaciones del sistema
* **Configuración de** para configurar la configuración del sistema ([incluidas las redes](connecting-to-wi-fi-on-hololens.md) y las actualizaciones del sistema)
* **Microsoft Edge** para examinar los sitios Web
* **Fotos** para ver y compartir fotos y vídeos
* **Calibración** (solo para HoloLens) para ajustar la experiencia de HoloLens al usuario actual
* **Obtenga información sobre los gestos** (HoloLens) o **aprender Mixed Reality** (inmersivos) para obtener información sobre el uso de un dispositivo
* **Visor de 3D** para decorar su mundo con contenido de realidad mixta
* **Mixto realidad Portal** (escritorio) para configurar y administrar los auriculares envolventes y streaming de una vista previa dinámica de la vista mediante los auriculares ver otros usuarios.
* **TV y películas** para ver 360 vídeos y las últimas películas y tv muestra
* **Cortana** para todos los asistentes virtuales debe
* **Escritorio** (inmersivos) para ver el monitor de escritorio mientras se encuentra en un auricular envolventes
* **Explorador de archivos** acceso a archivos y carpetas que se encuentran en el dispositivo

## <a name="see-also"></a>Vea también
* [Vistas de aplicación](app-views.md)
* [Controladores de movimiento](motion-controllers.md)
* [Accesorios de hardware](hardware-accessories.md)
* [Consideraciones sobre el entorno de HoloLens](environment-considerations-for-hololens.md)
* [Implementación de los iniciadores de aplicaciones 3D](implementing-3d-app-launchers.md)
* [Creación de modelos 3D para su uso en el hogar de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
