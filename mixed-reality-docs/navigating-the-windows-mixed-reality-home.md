---
title: Navegar por la Página principal de Windows Mixed Reality
description: Los auriculares HoloLens y Windows Mixed Reality comparten un paradigma para iniciar, colocar y manipular aplicaciones y modelos 3D en su entorno (ya sea físico o digital). Obtenga información sobre cómo navegar por la Página principal de Windows Mixed Reality en ambos tipos de dispositivo.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, so, plataforma, acantilado House, casa, Inicio, entorno, Inicio, menú Inicio, menú Inicio, PIN, aplicación, iniciar aplicaciones, colocar aplicaciones, teletransportar, trasladar, navegar
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525217"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navegar por la Página principal de Windows Mixed Reality

Al igual que la experiencia de PC de Windows se inicia con el escritorio, Windows Mixed Reality comienza con el hogar. La Página principal de Windows Mixed Reality aprovecha nuestra capacidad de INNATE para comprender y navegar por los lugares 3D. Con HoloLens, su hogar es el espacio físico. Con auriculares más inmersivo, su hogar es un lugar virtual.

En su hogar también podrá usar el menú Inicio para abrir y colocar aplicaciones y contenido. Puede rellenar su página principal con contenido de realidad mixta y a través de varias aplicaciones al mismo tiempo. Las cosas que coloque en su hogar permanecerán allí, incluso aunque reinicie el dispositivo.

## <a name="start-menu"></a>Menú Inicio

![Menú Inicio en Microsoft HoloLens](images/start-500px.png)

El menú Inicio consta de:
* Información del sistema (estado de la red, porcentaje de la batería, hora actual y volumen)
* Cortana (en auriculares envolventes, un icono de inicio, en HoloLens, en la parte superior de inicio)
* Aplicaciones ancladas
* Botón todas las aplicaciones (signo más)
* Botones de foto y vídeo para la [captura de realidad mixta](mixed-reality-capture.md)

Cambie entre las vistas aplicaciones ancladas y todas las aplicaciones. para ello, seleccione los botones más o menos. Para abrir el menú Inicio en HoloLens, use el gesto de floración. En un casco inmersivo, presione el botón de Windows del controlador.

## <a name="launching-apps"></a>Inicio de aplicaciones

Para iniciar una aplicación, selecciónela en Inicio. El menú Inicio desaparecerá y la aplicación se abrirá en modo de selección de ubicación, como una ventana 2D o un [modelo 3D](implementing-3d-app-launchers.md).

Para ejecutar la aplicación, deberá colocarla en su hogar:
1. Use la [mirada](gaze.md) o el controlador para colocar la aplicación donde quiera. Se ajustará automáticamente (en tamaño y posición) para ajustarse al espacio en el que se coloca.
2. Coloque la aplicación con el toque de aire (HoloLens) o el botón Seleccionar (auriculares envolventes). Para cancelar y volver a colocar el menú Inicio, use el gesto de floración o el botón de Windows.

las [aplicaciones 2D](building-2d-apps.md), creadas para escritorio, móviles o Xbox, se pueden modificar para que se ejecuten como aplicaciones envolventes de realidad mixta mediante la [API de HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx). Una aplicación envolvente saca al usuario de la casa y en una experiencia envolvente. Los usuarios pueden devolver casa con el gesto de floración (HoloLens) o presionando el botón de Windows en el controlador (auriculares envolventes).

Las aplicaciones también se pueden iniciar a través de una API de aplicación a aplicación o a través de Cortana.

![Aplicaciones en la Página principal de Windows Mixed Reality](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Mover y ajustar aplicaciones

Seleccione **ajustar** en la barra de la aplicación para mostrar los controles que mueven, escalan y giran el contenido de la realidad mixta. Cuando haya terminado, seleccione **listo**.

![La pizarra de la tienda en modo de ajuste (fotograma azul). Tenga en cuenta que la barra de la aplicación (superior) ha cambiado para incluir los botones ' listo ' y ' quitar '.](images/adjust-500px.png)

Distintas aplicaciones pueden tener opciones adicionales en la barra de la aplicación. Por ejemplo, Microsoft Edge tiene opciones de *desplazamiento*, *arrastre*y *zoom* . 

![Barra de la aplicación para aplicaciones 2D que se ejecutan en HoloLens](images/holobar-500px.png)

El botón **atrás** navega de nuevo a las pantallas que se vieron anteriormente en la aplicación. Se detendrá cuando llegue al principio de las experiencias que se han mostrado en la aplicación y no se desplazará a otras aplicaciones.

## <a name="getting-around-your-home"></a>Desplazarse por su hogar

Con **HoloLens**, puede desplazarse por el espacio físico para moverse por su hogar.

Con **auriculares**más ajustados, puede empezar de forma similar en su Playspace para moverse dentro de una zona similar del mundo virtual. Para desplazarse a través de distancias largas, puede usar el stick analógico en el controlador para "caminar", o bien puede usar la teleportabilidad para saltar inmediatamente distancias más largas.

![Teleportabilidad en la Página principal de Windows Mixed Reality](images/teleportation-500px.png)

**Para teletranspórtate:**
1. Abra el retículo de teleportabilidad.
   * Usar [controladores de movimiento](motion-controllers.md): Presione el stick analógico hacia delante y manténgalo en esa posición.
   * Usar un controlador Xbox: Presione el stick analógico izquierdo hacia delante y manténgalo en esa posición.
   * Usar un mouse: mantenga presionado el botón secundario del mouse (y use la rueda de desplazamiento para girar la dirección a la que desea que se enfrente al transportar).
2. Coloque el retículo en el que desea transportar.
   * Uso de [los controladores de movimiento](motion-controllers.md): Incline el controlador (en el que está manteniendo el stick analógico hacia delante) para desplazar el retículo.
   * Usar una controladora Xbox: Use la [mirada](gaze.md) para trasladar el retículo.
   * Usar un mouse: mueva el mouse para desplace el retículo.
3. Suelte el botón para teletranspórtate donde se colocó el retículo.

**Para "recorrer":**
* Uso de [controladores de movimiento](motion-controllers.md): haga clic en el stick y mantenga presionado el stick y, a continuación, mueva el stick analógico en la dirección en la que desea "caminar".
* Usar un controlador de Xbox: haga clic en el stick analógico izquierdo y, después, mueva el stick analógico en la dirección en la que desea "caminar".

## <a name="immersive-headset-input-support"></a>Compatibilidad con entrada con auriculares envolvente

Los auriculares envolventes de [realidad mixta de Windows](immersive-headset-hardware-details.md) admiten varios tipos de entrada para navegar por la Página principal de Windows Mixed Reality. HoloLens no es compatible con entradas de accesorios para la navegación, ya que se recorre físicamente el entorno y se ve. Sin embargo, HoloLens [admite entradas](hardware-accessories.md) para interactuar con las aplicaciones.

### <a name="motion-controllers"></a>Controladores de movimiento

La mejor experiencia de Windows Mixed Reality será con [los controladores de movimiento](motion-controllers.md) de Windows Mixed Reality que admiten el seguimiento de 6 grados de libertad mediante el uso de los sensores en el casco: no se requiere ninguna cámara ni marcador externos.

Los comandos de navegación estarán disponibles próximamente.

### <a name="gamepad"></a>Controlador para juegos
* **Stick analógico izquierdo:**
  * Mantenga presionado el stick izquierdo hacia delante para abrir el retículo de [teleportabilidad](navigating-the-windows-mixed-reality-home.md#getting-around-your-home).
  * Pulse el stick analógico hacia la izquierda, derecha o hacia atrás para moverse a la izquierda, a la derecha o hacia atrás en incrementos pequeños.
  * Haga clic en bajar en el stick analógico izquierdo y, a continuación, mueva el stick analógico en la dirección en la que desea ["caminar".](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Puntee en el **stick analógico** situado a la izquierda o a la derecha para girar la dirección a la que está orientada en 45 grados.
* Al presionar el botón **a** , se realiza una selección y actúa como el gesto de pulsación de [aire](gestures.md#air-tap) .
* Al presionar el botón **Guía** , se abre el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu) y se actúa como el gesto de [floración](gestures.md#bloom) .
* Presionar los **desencadenadores izquierdo y derecho** le permite acercar y alejar una aplicación de escritorio 2D con la que interactúa en el hogar.

### <a name="keyboard-and-mouse"></a>Teclado y mouse

**Nota:** Use la **tecla Windows + Y** para cambiar el mouse entre el control del escritorio de su PC y la Página principal de Windows Mixed Reality.

En la Página principal de Windows Mixed Reality:
* Al presionar el botón primario del mouse **,** se realiza una selección y se comporta como el gesto de pulsación de [aire](gestures.md#air-tap) .
* Si mantiene presionado el **botón secundario** del mouse, aparecerá el retículo de [teleportabilidad](navigating-the-windows-mixed-reality-home.md#getting-around-your-home).
* Al presionar la tecla **Windows** en el teclado, se abre el [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu) y se actúa como el gesto de [floración](gestures.md#bloom) .
* Cuando [Gazing](gaze.md) en una aplicación de escritorio 2D, puede **hacer clic** con el botón derecho para seleccionar, **hacer clic con el botón secundario** para abrir los menús contextuales y usar la **rueda de desplazamiento** para desplazarse (al igual que en el escritorio de su PC).

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) es su asistente personal en Windows Mixed Reality, al igual que en PC y teléfono. HoloLens tiene un micrófono integrado, pero los auriculares envolventes pueden requerir hardware adicional. Use Cortana para abrir aplicaciones, reiniciar el dispositivo, buscar elementos en línea, etc. Los desarrolladores también pueden optar por [integrar Cortana](https://dev.windows.com/cortana) en sus experiencias.

También puede usar comandos de voz para hacer todo su hogar. Por ejemplo, señale un botón (mediante la tecla de [mira](gaze.md) o un controlador, en función del dispositivo) y "seleccione". Otros comandos de voz incluyen "ir a casa", "más grande", "más pequeño", "cerrar" y "me encuentro".

## <a name="store-settings-and-system-apps"></a>Almacenamiento, configuración y aplicaciones del sistema

Windows Mixed Reality tiene varias aplicaciones integradas, como:
* **Microsoft Store** para obtener aplicaciones y juegos
* **Centro de comentarios** para enviar comentarios sobre las aplicaciones del sistema y del sistema
* **Configuración** para configurar las opciones del sistema ([incluidas las redes](connecting-to-wi-fi-on-hololens.md) y las actualizaciones del sistema)
* **Microsoft Edge** para examinar sitios web
* **Fotos** para ver y compartir fotos y vídeos
* **Calibración** de (Solo HoloLens) para ajustar la experiencia de HoloLens al usuario actual
* **Aprendizaje** de los gestos (HoloLens) o **aprender la realidad mixta** (auriculares envolventes) para obtener información sobre cómo usar el dispositivo
* **Visor 3D** para decorar su mundo con contenido de realidad mixta
* **Portal de realidad mixta** (escritorio) para configurar y administrar el casco envolvente y el streaming de una vista previa dinámica de la vista en los auriculares para que otros puedan verlo.
* **Películas y TV** para ver vídeos de 360 y las películas y programas de TV más recientes
* **Cortana** para todas las necesidades del asistente virtual
* **Escritorio** de (auriculares envolventes) para ver el monitor de escritorio en un casco envolvente
* **Explorador de archivos** Acceder a archivos y carpetas ubicados en el dispositivo

## <a name="see-also"></a>Vea también
* [Vistas de aplicación](app-views.md)
* [Controladores de movimiento](motion-controllers.md)
* [Accesorios de hardware](hardware-accessories.md)
* [Consideraciones acerca del entorno en HoloLens](environment-considerations-for-hololens.md)
* [Implementación de iniciadores de aplicaciones 3D](implementing-3d-app-launchers.md)
* [Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
