---
title: Entrada de emulador de HoloLens y el simulador de realidad mixta avanzados
description: Instrucciones detalladas para usar el teclado, mouse y controlador de Xbox para simular la entrada para el simulador de emulador de HoloLens y Windows Mixed Reality.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, emulador, simulación, Windows Mixed Reality
ms.openlocfilehash: 6ea493d8c1269ff0bea1d4102b9e224e30d06aef
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580593"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Entrada de emulador de HoloLens y el simulador de realidad mixta avanzados

Solo tendrá que usar los controles de entrada básicos para la mayoría de los usuarios de emulador el [emulador de HoloLens](using-the-hololens-emulator.md#basic-emulator-input) o [simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Los detalles siguientes son para usuarios avanzados que han encontrado una necesidad para simular tipos más complejos de entrada.


## <a name="concepts"></a>Conceptos

Para empezar a controlar la entrada virtual en el simulador de emulador de HoloLens y Windows Mixed Reality, primero debe conocer algunos conceptos.

Movimiento se refiere a controlar y cambiar la posición y la orientación de algo en la escena. Para un objeto de destino puede controlar el movimiento se controla con rotación y traslación (movimiento) a lo largo de tres ejes.
* **Yaw**: Activa la izquierda o derecha.
* **Pitch**: Gire hacia arriba o hacia abajo.
* **Roll**: La puesta en paralelo.
* **X**: Mover a la izquierda o derecha.
* **Y**: Subir o Bajar.
* **Z**: Desplazarse hacia delante o hacia atrás.

[Gesto](gestures.md) y entrada del controlador de movimiento se asignan estrechamente a la forma que los dispositivos físicos:
* **Acción**: Esto simula la acción de presionar el pulgar a la miniatura o extraer el botón de acción en un controlador. Por ejemplo, la entrada de la acción se puede usar para simular el gesto de pulsar en el aire, desplazarse a través de contenido y presione y mantenga.
* **[Bloom](gestures.md#bloom)casa o gesto/System**: El gesto de bloom/sistema HoloLens o botón de inicio de un controlador se usa para devolver al shell y para realizar acciones del sistema.

Manos tienen un amplio reprresentation en HoloLens 2.  Además de ser sometidas a seguimiento o no realiza un seguimiento y, a continuación, puede utilizables para movimientos de conducción, manos ahora tienen un modelo de esqueleto articulado ajustar a ellas y se expone al desarrollador.  Esto introduce 26 puntos sometidas a seguimiento por cada lado.  
* **Joint**: Uno de veinte posiciones sometidas a seguimiento para una determinado mano sometidas a seguimiento. Esto tendrá un punto es un espacio 3d asociado con él.
* **Suponer**: Una colección completa de todos los puntos de unión en una mano sometidas a seguimiento. En este momento, se trata de una colección de 26 juntas. 

En este momento, no se exponen control directo de cada posición conjunta individualmente mediante la interfaz de usuario del emulador, aunque se puede establecer a través de la API de simulación. En su lugar, tenemos un conjunto de plantea representativo útil que permite alternar entre el emulador.

También puede controlar el estado de la entrada de sensor simulados:
* **Reset**: Esto devolverá todos los sensores simulados a sus valores predeterminados.  Comenzando con el emulador de HoloLens 2, un restablecimiento se puede alcanzar a uno o dos manos Subcontratando la hand(s) deseado mediante el modificador apropiado claves o según corresponda (izquierda o derecha Alt o al paragolpes izquierdo o derecho en el controlador para juegos).
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
|  Bloom/sistema |  Tecla F2 o Windows |  |  Botón B | 
|  Botón de control de controlador |  G  |  |  | 
|  Botón de menú del dispositivo |  M  |  |  | 
|  Interacción de teclado táctil de controlador |  U  |  |  | 
|  Presione panel táctil de controlador |  P  |  |  | 
|  Presione tecla de navegación de controlador |  K  |  |  | 
|  Controlador izquierdo de seguimiento de estado |  F9 |  |  | 
|  Controlador derecho de seguimiento de estado |  F10 |  |  | 
|  "Cerrar" postura de mano | 7 |  |  |
|  Entregar la postura de "Open" (valor predeterminado) | 8 |  |  |
|  Postura de mano "Apunta" | 9 |  |  |
|  Postura de mano 'Acercar' | 0 |  |  |
|  Restablecer |  Tecla escape |  |  Botón Inicio | 
|  Seguimiento |  T o F3 |  |  Botón X | 


Nota: Los botones del controlador pueden ser el destino a una mano/controlador u otra con la mano de los modificadores de compatibilidad.

## <a name="targeting"></a>Selección de destino 

Algunos de los conceptos de entrada anteriores apóyate en sus propios.  Acción, Bloom/System, restablecimiento y el seguimiento son conceptos completados, no es necesario y no se ven afectados por los modificadores adicionales para seleccionar como destino.  Sin embargo, los conceptos restantes pueden aplicarse a uno de varios destinos. Hemos introducido formas para especificar cuál previsto de destino a que se debe aplicar el comando.  En todos los casos, es posible especificar a través de la interfaz de usuario o a través de pulsaciones de teclado, que targtet de objeto.  En algunos casos, también es posible especificar directamente con el controlador de xbox. 

En la tabla siguiente se describen las opciones de destino y la forma activar cada uno de ellos.

| Object | Modificador de teclado | Modificador de controlador | Modificador de la interfaz de usuario del emulador |
|----------|----------|----------|----------|
| Cuerpo | (valor predeterminado) | (valor predeterminado) | (valor predeterminado) |
| Head | Suspensión H | (No disponible) | (No disponible) |
| Controlador o la izquierda | Mantenga presionado el botón de Alt izquierda | Mantenga presionado el botón de hombros izquierdo | PIN de la mano izquierda | 
| Controlador o la derecha | Mantenga presionado un botón Alt derecha | Mantenga presionado el botón de hombro derecho | PIN de la mano derecha |
| Ojos | Suspensión Y | (No disponible) | Los ojos chincheta |
  
En la tabla siguiente se muestra cómo cada modificador destino asigna cada uno de los conceptos de entrada de movimiento

|  | Predeterminado (cuerpo) |  Controlador/mano (mantenga Alt, botón de suspensión gamepad hombro o Alternar marcador de interfaz de usuario) |  HEAD (mantenga H)  |  Ojos (Y mantenga o Alternar marcador de interfaz de usuario) |
|----------|----------|----------|----------|
|  Guiñada |  Activar el cuerpo de la izquierda / derecha |  Mover la mano izquierda / derecha |  Activar encabezado izquierda / derecha | Mirada ojo busca izquierda/derecha |
|  Rotación alrededor del eje x (pitch) |  Activar encabezado arriba / abajo |  Mover la mano arriba / abajo |  Activar encabezado arriba / abajo | Mirada ojo busca arriba/abajo | 
|  Balanceo |  Rollo de head izquierda / derecha |  |  Rollo de head izquierda / derecha | (Sin acción) |
|  X |  Deslice el cuerpo de la izquierda / derecha |  Mover/controlador de la mano izquierda / derecha |  Activar encabezado izquierda / derecha | (Sin acción) |
|  esté |  Mover el cuerpo de arriba / abajo |  Mover la mano/controlador arriba / abajo |  Activar encabezado arriba / abajo | (Sin acción) |
|  Z |  Mover hacia delante o hacia atrás de cuerpo |  Mover la mano por controlador hacia delante o hacia atrás |  Activar encabezado arriba / abajo | (Sin acción) |
 
 
## <a name="controlling-an-app"></a>Controlar una aplicación

El siguiente conjunto de controles se recomienda para el uso diario:

|  Operación |  Teclado y mouse |  Controlador | 
|----------|----------|----------|
|  Cuerpo X |  A / D |  Tecla de navegación izquierda izquierda / derecha | 
|  Cuerpo Y |  AV PÁG / AV PÁG |  DPad arriba / abajo | 
|  Cuerpo de la Z |  W / S |  Tecla de navegación izquierda arriba / abajo | 
|  Guiñada cuerpo |  Arrastre el mouse izquierdo / derecha |  Tecla de navegación derecha izquierda / derecha | 
|  Guiñada HEAD |  H + arrastrar el mouse izquierda / derecha |  H (en el teclado) + tecla de navegación derecha izquierda / derecha | 
|  Encabezado de tono |  Arrastre el mouse arriba / abajo |  Tecla de navegación derecha arriba / abajo | 
|  Rollo de head |  Q / E |  DPad izquierda / derecha | 
|  Controlador/mano X |  Alt + A / D |  Hombro + tecla de navegación izquierda izquierda / derecha | 
|  Controlador/mano Y |  ALT + RE PÁG / AV PÁG |  Hombro + DPad arriba / abajo | 
|  Controlador de mano/Z |  ALT + W / S |  Hombro + tecla de navegación izquierda arriba / abajo | 
|  Guiñada mano por controlador |  Alt + arrastrar el mouse izquierda / derecha |  Hombro + tecla de navegación derecha izquierda / derecha | 
|  Paso de mano o controlador |  Alt + arrastrar el mouse arriba / abajo |  Hombro + tecla de navegación derecha arriba / abajo | 
|  Rollo de mano o controlador |  Alt + Q / E |  Hombro + DPad izquierda / derecha | 
|  Acción |  Botón secundario del mouse |  desencadenador | 
|  Bloom / sistema / Home |  Tecla F2 o Windows |  Botón B | 
|  Restablecer |  Escape |  Botón Inicio | 
|  Seguimiento |  T |  Botón X | 
|  Desplazamiento |  ALT + derecha botón del mouse y arrastre del mouse arriba / abajo |  Hombro desencadenador + tecla de navegación derecha arriba / abajo | 
|  Más rápido movimiento/girar | Tecla MAYÚS izquierda o derecha | Presione y mantenga presionada la tecla de navegación derecha |
|  Mover o girar lenta | Tecla Ctrl izquierda o derecha | Presione y mantenga presionada la tecla de navegación izquierda |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Métodos abreviados de teclado del Panel de Control de simulación de percepción

Los siguientes métodos abreviados de teclado están disponibles para el acceso al panel de Control de la simulación de percepción y habilitar o deshabilitar dispositivos de entrada de PC para usar con la simulación.

| Operación | Método abreviado | Descripción/notas |
|-----------|----------|-------------|
| Alternar "Usar el teclado para la simulación" | F4 | Si está desactivada, entrada de teclado se dirige a la aplicación de HoloLens o Windows Mixed Reality. |
| Alternar "Usar el mouse para la simulación" | F5 | Si está desactivada, la entrada del mouse entra en el entorno de realidad mixta (solo en la realidad mixta de Windows) |
| Alternar 'Usar gamepad para simulación' | F6 | Si está desactivada, se omite la entrada de gamepad mediante la simulación |
| Mostrar u ocultar el panel de control | F7 | |
| Establecer el foco de teclado en el panel de control | F8 | Si no está actualmente visible en el panel se mostrará primero. |
| Acoplar o desacoplar del panel hacia y desde el emulador o ventana del Portal de realidad mixta | F9 | Si la ventana se cierra cuando desacoplado, está acoplado y oculta. |

## <a name="see-also"></a>Vea también
* [Instalación de las herramientas](install-the-tools.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Uso del simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
