---
title: Usar el simulador de realidad mixta de Windows
description: El simulador de realidad mixta de Windows le permite probar aplicaciones de realidad mixtas en su PC sin un casco de Windows Mixed Reality.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, simulador, pruebas
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580704"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Usar el simulador de realidad mixta de Windows

El simulador de realidad mixta de Windows le permite probar aplicaciones de realidad mixtas en su PC sin un casco de Windows Mixed Reality. Está disponible a partir de Windows 10 Creators Update. El simulador es similar al [emulador de HoloLens](using-the-hololens-emulator.md), aunque el simulador no usa una máquina virtual. Las aplicaciones que se ejecutan en el simulador se ejecutan en la sesión de usuario de escritorio de Windows 10, al igual que lo harían si usara un casco envolvente. En su lugar, las entradas humanas y del entorno que normalmente leerán los sensores en un casco envolvente se simulan con el teclado, el mouse o la controladora Xbox. No es necesario modificar las aplicaciones para que se ejecuten en el simulador y no sabe que no se ejecutan en un casco envolvente.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitar el simulador de realidad mixta de Windows

1. **Habilitar el modo de desarrollador** desde configuración-> Update y > de seguridad para desarrolladores
2. Inicio del **portal de realidad mixta** desde el escritorio
3. Si esta es la primera vez que inicia el portal, deberá pasar por la experiencia de instalación.
   1. Haga **clic** en introducción
   2. Haga **clic** en Acepto para aceptar el contrato
   3. Haga clic en **configurar para simulación (para desarrolladores)** para continuar con la instalación sin un dispositivo físico.
   4. Haga clic en **configurar** para confirmar su elección
4. Haga clic en el botón **para desarrolladores** en el lado izquierdo del portal de realidad mixta.
5. Activar el modificador **de alternancia de** simulación
   * La habilitación de la simulación instala y habilita de forma predeterminada el controlador simulado 6-DOF de la izquierda.  Antes de la actualización de Windows 10 de mayo de 2019, la instalación de un controlador simulado de 6 DOF requiere permisos de administrador.  Debe aceptar el cuadro de diálogo control de cuentas de usuario si aparece alguno.

Ahora debería ejecutarse con simulación.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implementación de aplicaciones en el simulador de realidad mixta

Dado que el simulador se ejecuta en el equipo local sin una máquina virtual, puede simplemente implementar las aplicaciones universales de Windows en el **equipo local** durante la depuración.

## <a name="basic-simulator-input"></a>Entrada básica del simulador

Controlar el simulador es muy similar a muchos juegos de vídeo 3D comunes y el emulador de [HoloLens](using-the-hololens-emulator.md). Hay opciones de entrada mediante el teclado, el mouse o un mando de Xbox.

Puede controlar el simulador dirigiendo las acciones de un usuario simulado con un casco envolvente. Sus acciones mueven el usuario simulado y causan interacciones con las aplicaciones que responden como lo harían en un casco envolvente.
* **Andar hacia delante, hacia atrás, a la izquierda y a la derecha**: usa las teclas W, A, S y D del teclado o el stick izquierdo en un mando de Xbox.
* **Mirar hacia arriba, hacia abajo, a la izquierda y a la derecha**: haz clic y arrastra el mouse, usa las teclas de dirección del teclado o el stick derecho en un mando de Xbox.
* **Botón de acción Presione en el controlador** : haga clic con el botón derecho en el mouse, presione la tecla entrar en el teclado o use el botón a en un controlador de Xbox.
* **Botón Inicio presionar el controlador** : Presione la tecla Windows o la tecla F2 del teclado o presione el botón B en un controlador Xbox.
* **Movimiento del controlador para el desplazamiento** : mantenga presionada la tecla Alt, mantenga presionado el botón secundario del mouse y arrastre el mouse hacia arriba o hacia abajo, o bien, en una controladora Xbox, mantenga presionado el botón derecho y un botón hacia abajo y mueva el stick derecho hacia arriba y hacia abajo.

## <a name="tracked-controllers"></a>Controladores controlados

El simulador de realidad mixta puede simular hasta dos controladores de movimiento de seguimiento a mano. Habilítelo mediante los modificadores de alternancia en el portal de realidad mixta. Cada controlador simulado tiene:
* Posición y orientación en el espacio
* Botón Inicio
* Botón de menú
* Botón de control
* Panel táctil
* Palanca
* Nivel de batería

## <a name="see-also"></a>Vea también
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Entrada del simulador de realidad mixta avanzada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
