---
title: Entrada de emulador de HoloLens y el simulador de realidad mixta avanzados
description: Instrucciones detalladas para usar el teclado, mouse y controlador de X-Box para simular la entrada para el emulador de HoloLens y el simulador de Windows Mixed Reality.
author: ChimeraScorn
ms.author: cwhite
ms.date: 02/24/2018
ms.topic: article
keywords: HoloLens, emulador, simulación, Windows Mixed Reality
ms.openlocfilehash: 59bea340a2ecdd2d65481c9ace4ab3f0bf15bc6f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597848"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada de emulador de HoloLens y el simulador de realidad mixta avanzados

Solo tendrá que usar los controles de entrada básicos para la mayoría de los usuarios de emulador el [emulador de HoloLens](using-the-hololens-emulator.md#basic-emulator-input) o [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Los detalles siguientes son para usuarios avanzados que han encontrado una necesidad para simular tipos más complejos de entrada.

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="concepts"></a>Conceptos

Para empezar a controlar la entrada virtual para el emulador de HoloLens y el simulador de Windows Mixed Reality, primero debe conocer algunos conceptos.

Movimiento se refiere a controlar y cambiar la posición y la orientación de algo en la escena. Para un objeto de destino puede controlar el movimiento se controla con rotación y traslación (movimiento) a lo largo de tres ejes.
* **Yaw**: Activa la izquierda o derecha.
* **Pitch**: Gire hacia arriba o hacia abajo.
* **Roll**: La puesta en paralelo.
* **X**: Mover a la izquierda o derecha.
* **Y**: Subir o Bajar.
* **Z**: Desplazarse hacia delante o hacia atrás.

[Gesto](gestures.md) y entrada del controlador de movimiento se asignan estrechamente a la forma que los dispositivos físicos:
* **Acción**: Esto simula la acción de presionar el pulgar a la miniatura o extraer el botón de acción en un controlador. Por ejemplo, la entrada de la acción se puede usar para simular el gesto de pulsar en el aire, desplazarse a través de contenido y presione y mantenga.
* **[Bloom](gestures.md#bloom) o Home**: Botón de inicio de un controlador se utiliza para devolver al shell y para realizar acciones del sistema o el HoloLens florezcan gesto.

Manos tienen un amplio reprresentation en HoloLens V2.  Además de ser sometidas a seguimiento o no realiza un seguimiento y, a continuación, puede utilizables para movimientos de conducción, manos ahora tienen un modelo de esqueleto articulado ajustar a ellas y se expone al desarrollador.  Esto introduce 20 puntos sometidas a seguimiento por cada lado.  
* **Joint**: Uno de veinte posiciones sometidas a seguimiento para una determinado mano sometidas a seguimiento. Esto tendrá un punto es un espacio 3d asociado con él.
* **Suponer**: Una colección completa de todos los puntos de unión en una mano sometidas a seguimiento. En este momento, se trata de una colección de 20 juntas. 

En este momento, no se exponen control directo de cada posición conjunta individualmente mediante la interfaz de usuario del emulador. Aunque se puede establecer a través de la API de simulación. En su lugar, tenemos un conjunto de plantea representativo útil que permite alternar entre el emulador.

También puede controlar el estado de la entrada de sensor simulados:
* **Reset**: Esto devolverá todos los sensores simulados a sus valores predeterminados.
* **Seguimiento**: Recorre los modos de seguimiento posicional. Esto incluye:
  * **Predeterminado**: El sistema operativo elegirá el mejor modo de seguimiento en función de las solicitudes realizadas del sistema.
   * **Orientación**: Fuerzas sólo orientación seguimiento, independientemente de las solicitudes realizadas del sistema.
   * **Posicionales**: Seguimiento de posición de fuerza, independientemente de las solicitudes realizadas del sistema.

## <a name="types-of-input"></a>Tipos de entrada

En la tabla siguiente se muestra cómo cada tipo de entrada se asigna al teclado, mouse y controlador de Xbox. Cada tipo tiene una asignación diferente según el modo de control de entrada; Para obtener más información acerca de los modos de control de entrada se proporciona más adelante en este documento.

|  |  Teclado |  Mouse |  Mando de Xbox | 
|----------|----------|----------|----------|
|  Guiñada |  Flechas izquierdas / derecha |  Arrastre izquierda / derecha |  Tecla de navegación derecha izquierda / derecha | 
|  Rotación alrededor del eje x (pitch) |  Arriba / flecha abajo |  Arrastrar arriba / abajo |  Tecla de navegación derecha arriba / abajo | 
|  Balanceo |  Q / E |  |  DPad izquierda / derecha | 
|  X |  A / D |  |  Tecla de navegación izquierda izquierda / derecha | 
|  esté |  AV PÁG / AV PÁG |  |  DPad arriba / abajo | 
|  Z |  W / S |  |  Tecla de navegación izquierda arriba / abajo | 
|  Acción |  ENTRAR o espacio |  Botón secundario |  Un botón o cualquier desencadenador | 
|  Bloom |  F2 o Windows key (clave de Windows sólo funciona con el emulador de HoloLens) |  |  Botón B | 
|  Botón de control de controlador |  G (Windows Mixed Reality solo simulator) |  |  | 
|  Botón de menú del dispositivo |  M (Windows Mixed Reality solo simulator) |  |  | 
|  Interacción de teclado táctil de controlador |  U (Windows Mixed Reality solo simulator) |  |  | 
|  Presione panel táctil de controlador |  P (Windows Mixed Reality solo simulator) |  |  | 
|  Establezca la postura de mano | 7, 8, 9 o 0 |  |  |
|  Restablecer |  Tecla escape |  |  Botón Inicio | 
|  Seguimiento |  T o F3 |  |  Botón X | 


Nota: En el simulador de Windows Mixed Reality únicamente, los botones del controlador pueden ser destino a una mano o el otro con la mano de los modificadores de compatibilidad.

## <a name="targeting"></a>Selección de destino 

Algunos de los conceptos de entrada anteriores apóyate en sus propios.  Acción, Bloom, restablecer y seguimiento son conceptos completados, no es necesario y no se ven afectados por los modificadores adicionales para seleccionar como destino.  Sin embargo, los conceptos restantes pueden aplicarse a uno de varios destinos. Hemos introducido formas para especificar cuál previsto de destino a que se debe aplicar el comando.  En todos los casos, es posible especificar a través de la interfaz de usuario o a través de pulsaciones de teclado, que targtet de objeto.  En algunos casos, también es posible especificar directamente con el controlador de xbox. 

En la tabla siguiente se describen las opciones de destino y la forma activar cada uno de ellos.

| Objeto | Modificador de teclado | Modificador de controlador | Modificador de la interfaz de usuario del emulador |
|----------|----------|----------|----------|
| Cuerpo | <default> | <default> | <default> |
| Head | Suspensión H | <None available> | Head chincheta en la interfaz de usuario |
| Controlador o la izquierda | Botón Alt izquierda | Botón izquierdo del hombro | PIN de la mano izquierda | 
| Controlador o la derecha | Botón Alt derecha | Botón hombro derecho | PIN de la mano derecha |
| Ojos | Suspensión Y | <No contoller modifier available> | PIN de ojos |
  
En la tabla siguiente se muestra cómo cada modificador destino asigna cada uno de los conceptos de entrada de movimiento

|  Predeterminado (cuerpo) |  Controlador/mano (presionada la tecla alt y respaldar) |  HEAD (mantenga H)  |  Ojos (mantenga Y) |
|----------|----------|----------|----------|
|  Guiñada |  Activar el cuerpo de la izquierda / derecha |  Mover la mano izquierda / derecha |  Activar encabezado izquierda / derecha | Mirada ojo busca izquierda/derecha |
|  Rotación alrededor del eje x (pitch) |  Activar encabezado arriba / abajo |  Mover la mano arriba / abajo |  Activar encabezado arriba / abajo | Mirada ojo busca arriba/abajo | 
|  Balanceo |  Rollo de head izquierda / derecha |  |  Rollo de head izquierda / derecha | (Sin acción) |
|  X |  Deslice el cuerpo de la izquierda / derecha |  Mover/controlador de la mano izquierda / derecha |  Activar encabezado izquierda / derecha | (Sin acción) |
|  esté |  Mover el cuerpo de arriba / abajo |  Mover la mano/controlador arriba / abajo |  Activar encabezado arriba / abajo | (Sin acción) |
|  Z |  Mover hacia delante o hacia atrás de cuerpo |  Mover la mano por controlador hacia delante o hacia atrás |  Activar encabezado arriba / abajo | (Sin acción) |
 
Nota: En el simulador de Windows Mixed Reality únicamente, los botones del controlador pueden ser destino a una mano o el otro con la mano de los modificadores de compatibilidad. Del mismo modo, en el emulador de HoloLens solo, la postura de mano articulados puede ser destino a una mano o el otro con los modificadores de mano. 
 
## <a name="controlling-an-app"></a>Controlar una aplicación

En este artículo se describe el conjunto completo de tipos de entrada y los modos de entrada que están disponibles en el emulador de HoloLens y el simulador de Windows Mixed Reality. El siguiente conjunto de controles se recomienda para el uso diario:

|  Operación |  Teclado y mouse |  Controlador | 
|----------|----------|----------|
|  Cuerpo X |  A / D |  Tecla de navegación izquierda izquierda / derecha | 
|  Cuerpo Y |  AV PÁG / AV PÁG |  DPad arriba / abajo | 
|  Cuerpo de la Z |  W / S |  Tecla de navegación izquierda arriba / abajo | 
|  Guiñada cuerpo |  Arrastre el mouse izquierdo / derecha |  Tecla de navegación derecha izquierda / derecha | 
|  Guiñada HEAD |  H + arrastrar el mouse izquierda / derecha |  H (en el teclado) + tecla de navegación derecha izquierda / derecha | 
|  Encabezado de tono |  Arrastre el mouse arriba / abajo |  Tecla de navegación derecha arriba / abajo | 
|  Rollo de head |  Q / E |  DPad izquierda / derecha | 
|  Mano X |  Alt + arrastrar el mouse izquierda / derecha |  Hombro + tecla de navegación derecha izquierda / derecha | 
|  Mano Y |  Alt + arrastrar el mouse arriba / abajo |  Hombro + tecla de navegación derecha arriba / abajo | 
|  Mano Z |  ALT + W / S |  Hombro + tecla de navegación izquierda arriba / abajo | 
|  Acción |  Botón secundario del mouse |  desencadenador | 
|  Florezcan / Home |  F2 o Windows key (clave de Windows es solo para el emulador de HoloLens) |  Botón B | 
|  Restablecer |  Escape |  Botón Inicio | 
|  Seguimiento |  T |  Botón X | 
|  Desplazamiento |  ALT + derecha botón del mouse y arrastre del mouse arriba / abajo |  Hombro desencadenador + tecla de navegación derecha arriba / abajo | 

## <a name="see-also"></a>Vea también
* [Instalar las herramientas](install-the-tools.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Mediante el simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
