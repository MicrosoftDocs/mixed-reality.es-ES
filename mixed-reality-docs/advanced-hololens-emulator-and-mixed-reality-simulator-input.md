---
title: Introducción de datos avanzada en el emulador de HoloLens y el simulador de realidad mixta
description: Instrucciones detalladas para usar el teclado, el mouse y el controlador Xbox para simular la entrada para el emulador de HoloLens y el simulador de realidad de Windows Mixed.
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, emulador, simulación, Windows Mixed Reality
ms.openlocfilehash: e9051ae9e7853924f583b6c38f6177f2f967d9f0
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "83227960"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Introducción de datos avanzada en el emulador de HoloLens y el simulador de realidad mixta

La mayoría de los usuarios del emulador solo tendrán que usar los controles de entrada básicos para el [emulador de HoloLens](using-the-hololens-emulator.md#basic-emulator-input) o el [simulador de realidad de Windows Mixed](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Los detalles siguientes son para usuarios avanzados que han encontrado una necesidad de simular tipos de entrada más complejos.


## <a name="concepts"></a>Conceptos

Para empezar a controlar la entrada virtual en el emulador de HoloLens y el simulador de realidad de Windows Mixed, primero debe comprender algunos conceptos.

El movimiento se refiere a controlar y cambiar la posición y la orientación de un elemento de la escena. En el caso de un objeto controlable en el destino, el movimiento se controla con la rotación y la traslación (movimiento) a lo largo de tres ejes.
* **Guiñada**: gire a la izquierda o a la derecha.
* **Paso**: activar o desactivar.
* **Roll**: rollo de un lado a otro.
* **X**: moverse a la izquierda o a la derecha.
* **Y**: subir o bajar.
* **Z**: moverse hacia delante o hacia atrás.

Los gestos y la entrada del controlador de movimiento se asignan estrechamente a la manera en que los dispositivos físicos:
* **Acción**: esto simula la acción de presionar índice al control de posición o de extraer el botón de acción de un controlador. Por ejemplo, la entrada de acción se puede usar para simular el gesto de punteo de aire, desplazarse por el contenido y mantener presionado.
* **Gesto o inicio del/System de [floración](system-gesture.md#bloom)**: el gesto de la floración/del sistema de HoloLens o el botón Inicio de un controlador se usa para volver al shell y realizar acciones del sistema.

Las manos tienen una representación enriquecida en HoloLens 2.  Además de ser sometidos a seguimiento y sin seguimiento, y que se pueden usar para llevar a cabo gestos, ahora tienen un modelo de esqueleto articulado y se exponen al desarrollador.  Esto introduce 26 puntos de seguimiento en cada mano.  
* **Conjunto**: una de las veinte posiciones de las que se ha realizado un seguimiento para una mano controlada determinada. Esto tendrá un punto con el espacio 3D asociado.
* **Pose**: colección completa de todas las uniones en una mano A la que se ha realizado un seguimiento. En este momento, se trata de una colección de 26 uniones. 

En este momento, no se expone el control directo de cada posición de la Unión a través de la interfaz de usuario del emulador, aunque se pueden establecer a través de la API de simulación. En su lugar, tenemos un conjunto de representativos útiles que el emulador le permite alternar entre.

También puede controlar el estado de la entrada de sensor simulado:
* **Restablecer**: se devolverán todos los sensores simulados a sus valores predeterminados.  A partir del emulador de HoloLens 2, se puede establecer un restablecimiento para el ámbito de una o las dos manos mediante la participación de las manos deseadas mediante las teclas modificadoras apropiadas o los botones (de la izquierda o derecha, o del reboteador izquierdo y/o derecho en el controlador de juegos).
* **Tracking**: recorre los modos de seguimiento posicional. Esto incluye:
  * **Valor predeterminado**: el sistema operativo elige el mejor modo de seguimiento en función de las solicitudes realizadas del sistema.
   * **Orientation**: fuerza el seguimiento de solo orientación, independientemente de las solicitudes realizadas del sistema.
   * **Posicional**: fuerza el seguimiento posicional, independientemente de las solicitudes realizadas del sistema.

## <a name="types-of-input"></a>Tipos de entrada

En la tabla siguiente se muestra cómo se asignan los tipos de entrada al teclado, el mouse y el controlador Xbox. Cada tipo tiene una asignación diferente en función del modo de control de entrada; más adelante en este documento se proporciona más información sobre los modos de control de entrada.

|  |  Teclado |  Mouse |  Controladora Xbox | 
|----------|----------|----------|----------|
|  Eje |  Flechas izquierda/derecha |  Arrastrar a la izquierda o a la derecha |  Palanca derecha izquierda/derecha | 
|  Tono |  Flechas arriba/abajo |  Arrastrar hacia arriba o hacia abajo |  Palanca derecha arriba/abajo | 
|  Volver |  P/E |  |  DPad izquierda/derecha | 
|  X |  A/D |  |  Stick izquierdo izquierdo/derecho | 
|  esté |  RE PÁG/AV pág |  |  DPad arriba/abajo | 
|  Z |  W/S |  |  Stick izquierdo hacia arriba/abajo | 
|  Acción |  Escriba o espacio |  Botón derecho |  Un botón o cualquier desencadenador | 
|  Floración/sistema |  F2 o tecla Windows |  |  Botón B | 
|  Botón de control del controlador |  G  |  |  | 
|  Botón de menú controlador |  M  |  |  | 
|  Touch Touchpad del controlador |  U  |  |  | 
|  Pulsador de controlador Touchpad |  P  |  |  | 
|  Pulsador del Stick del controlador |  K  |  |  | 
|  Estado de seguimiento del controlador izquierdo |  F9 |  |  | 
|  Estado correcto de seguimiento del controlador |  F10 |  |  | 
|  Pose de mano ' Close ' | 7 |  |  |
|  Pose de mano ' abrir ' (predeterminado) | 8 |  |  |
|  Pose de mano | 9 |  |  |
|  Postura de mano ' Pinch ' | 0 |  |  |
|  Reset |  Tecla escape |  |  Botón Iniciar | 
|  Seguimiento |  T o F3 |  |  Botón X | 


Nota: los botones del controlador pueden tener como destino una mano o un controlador, o el otro, mediante los modificadores de destino de la mano.

## <a name="targeting"></a>Establecer destinos 

Algunos de los conceptos de entrada anteriores se destacan por sí mismos.  Acción, floración/sistema, restablecimiento y seguimiento son conceptos completos, no necesitan y no se ven afectados por ningún modificador adicional para el destino.  Sin embargo, los conceptos restantes se pueden aplicar a uno de varios destinos. Hemos introducido maneras de especificar el destino al que debe aplicarse el comando.  En todos los casos, es posible especificar a través de la interfaz de usuario o a través de las pulsaciones de teclado, a qué objeto se va a dirigir.  En algunos casos, también es posible especificar con el controlador Xbox directamente. 

En la tabla siguiente se describen las opciones de destino y la manera de activar cada una de ellas.

| Object | Modificador de teclado | Modificador de controlador | Modificador de interfaz de usuario del emulador |
|----------|----------|----------|----------|
| Body | (predeterminado). | (predeterminado). | (predeterminado). |
| Head | Mantener H | (No disponible) | (No disponible) |
| Mano izquierda/controlador | Mantener presionado el botón Alt izq | Mantenga presionado el botón izquierdo del hombro | Marcador izquierdo | 
| Mano derecha/controlador | Mantenga presionado el botón Alt derecho | Botón mantener el hombro derecho | Tachuela derecha |
| Perspectiva | Mantener Y | (No disponible) | Marcador de ojos |
  
En la tabla siguiente se muestra cómo cada modificador de destino asigna cada uno de los conceptos de entrada de movimiento principales.

|  | Predeterminado (cuerpo) |  Mano/controlador (mantenga presionada la tecla Alt, mantenga presionado el botón de juego del controlador de juegos o alterne el marcador de IU) |  Head (mantener H)  |  Ojos (mantener el marcador de IU Y o alternar) |
|----------|----------|----------|----------|
|  Eje |  Convertir cuerpo a la izquierda o a la derecha |  Subir a la derecha o a la izquierda |  Desactivar la izquierda o la derecha | Ojo mira a la izquierda o a la derecha |
|  Tono |  Activar o desactivar el cabezal |  Subir o bajar |  Activar o desactivar el cabezal | El ojo mira hacia arriba o hacia abajo | 
|  Volver |  Deshacer el cabezal izquierdo y derecho |  |  Deshacer el cabezal izquierdo y derecho | (Ninguna acción) |
|  X |  Cuerpo de la diapositiva a la izquierda o a la derecha |  Movimiento de mano o controlador izquierda/derecha |  Desactivar la izquierda o la derecha | (Ninguna acción) |
|  esté |  Subir o bajar el cuerpo |  Subir o bajar el controlador |  Activar o desactivar el cabezal | (Ninguna acción) |
|  Z |  Desplazar el cuerpo hacia delante o hacia atrás |  Avanzar o retroceder el controlador |  Activar o desactivar el cabezal | (Ninguna acción) |
 
 
## <a name="controlling-an-app"></a>Controlar una aplicación

Se sugiere el siguiente conjunto de controles para el uso cotidiano:

|  Operación |  Teclado y mouse |  Controlador | 
|----------|----------|----------|
|  Cuerpo X |  A/D |  Stick izquierdo izquierdo/derecho | 
|  Cuerpo Y |  RE PÁG/AV pág |  DPad arriba/abajo | 
|  Cuerpo Z |  W/S |  Stick izquierdo hacia arriba/abajo | 
|  Guiñada del cuerpo |  Arrastrar el mouse hacia la izquierda o la derecha |  Palanca derecha izquierda/derecha | 
|  Guiñada de encabezado |  H + arrastrar el mouse hacia la izquierda o la derecha |  H (en el teclado) + stick analógico izquierdo/derecho | 
|  Extremo principal |  Arrastrar el mouse hacia arriba o abajo |  Palanca derecha arriba/abajo | 
|  Rollo de cabeza |  P/E |  DPad izquierda/derecha | 
|  Mano/controlador X |  Alt + A/D |  Hombro + Stick izquierdo izquierdo/derecho | 
|  Mano/controlador Y |  Alt + Re Pág/Av Pág |  Hombro + DPad arriba/abajo | 
|  Mano/controlador Z |  Alt + W/S |  Hombro + Stick izquierdo hacia arriba/abajo | 
|  Guiñada de mano/controlador |  Alt + arrastrar mouse a la izquierda/derecha |  Hombro + stick analógico izquierdo/derecho | 
|  Tono de mano/controlador |  Alt + arrastrar el mouse hacia arriba o abajo |  Hombro + stick analógico derecho arriba/abajo | 
|  Rollo de mano/controlador |  Alt + Q/E |  Hombro + DPad izquierda/derecha | 
|  Acción |  Botón secundario del mouse |  Desencadenador | 
|  Floración/sistema/Inicio |  F2 o tecla Windows |  Botón B | 
|  Reset |  Escape |  Botón Iniciar | 
|  Seguimiento |  T |  Botón X | 
|  Desplazamiento |  Alt + botón derecho del mouse + arrastrar el mouse hacia arriba o abajo |  Hombro + desencadenador + stick derecho arriba/abajo | 
|  Movimiento y giro más rápido | Tecla Mayús izquierda o derecha | Mantenga presionado el stick derecho |
|  Movimiento y giro lentos | Tecla Ctrl izquierda o derecha | Mantenga presionado el stick izquierdo |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Uso de un casco y controladores de movimiento de Windows Mixed Reality con el emulador de HoloLens 2

Cuando se usa un auricular envolvente de Windows Mixed Reality con el emulador de HoloLens 2, el movimiento y la rotación se asignan automáticamente al movimiento y la rotación de los auriculares.  La posición y la orientación del controlador de movimiento se asignan automáticamente a la posición y orientación de la mano en el emulador.  En la tabla siguiente se enumeran las acciones adicionales disponibles cuando se usa un controlador de movimiento.

Tenga en cuenta que cuando se usa un auricular, el teclado estándar, el mouse y los controles de controlador para juegos se omiten automáticamente.

|  Operación |  Acción |  Notas | 
|----------|----------|----------|
|  Cuerpo X |  Palanca izquierda/derecha |   | 
|  Cuerpo Z |  Avanzar/retroceder del stick analógico |   | 
|  Cuerpo Y |  Página del teclado arriba/Down | Asegúrese de que Windows Mixed Reality tiene el foco.  Presione Win + Y si el foco está en el escritorio de Windows para devolver el foco a Windows Mixed Reality. |
|  Los ojos se ven a la izquierda o a la derecha |  DPad izquierda/derecha | |
|  Apariencia de los ojos | DPad arriba/abajo | |
|  Pulsar | Desencadenador | |
|  Contacto y agarre | Botón de control | |
|  Gestos del sistema | Botón de menú | |
|  Restablecer posición | Clic en el Stick | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Métodos abreviados de teclado del panel de control de simulación de percepción

Los siguientes métodos abreviados de teclado están disponibles para tener acceso al panel de control de simulación de percepción y habilitar o deshabilitar dispositivos de entrada de equipo para su uso con la simulación.

| Operación | Método abreviado | Descripción/Notas |
|-----------|----------|-------------|
| Alternancia de ' usar teclado para simulación ' | F4 | Cuando está desactivada, la entrada de teclado se dirige a la aplicación HoloLens o Windows Mixed Reality. |
| Alternancia de ' usar Mouse para simulación ' | F5 | Cuando está desactivada, la entrada del mouse se dirige al entorno de realidad mixta (solo Windows Mixed Reality) |
| Alternar ' usar controlador de juegos para simulación ' | F6 | Cuando esta opción está desactivada, la simulación omite la entrada del controlador de juegos |
| Mostrar u ocultar el panel de control | F7 | |
| Establecer el foco del teclado en el panel de control | F8 | Si el panel no está visible actualmente, se mostrará primero. |
| Acoplar o desacoplar el panel en el emulador o en la ventana del portal de realidad mixta | F9 | Si la ventana se cierra cuando está desacoplada, está acoplada y oculta. |

## <a name="see-also"></a>Vea también
* [Instalación de las herramientas](install-the-tools.md)
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Uso del simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
