---
title: Mediante el simulador de Windows Mixed Reality
description: El simulador de Windows Mixed Reality le permite probar aplicaciones de realidad mixta en su PC sin un auricular envolvente de Windows Mixed Reality.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixto en realidad, el simulador, las pruebas
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605462"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Mediante el simulador de Windows Mixed Reality

El simulador de Windows Mixed Reality le permite probar aplicaciones de realidad mixta en su PC sin un auricular envolvente de Windows Mixed Reality. Está disponible a partir de Windows 10 Creators Update. El simulador es similar a la [emulador de HoloLens](using-the-hololens-emulator.md), aunque el simulador no utiliza una máquina virtual. Aplicaciones que se ejecutan en el simulador se ejecutan en la sesión de usuario de escritorio de Windows 10, tal como haría si estuviera usando un auricular envolvente. La entrada humana y del entorno que normalmente se lean los sensores en un auricular envolvente se simulan en su lugar, mediante el teclado, un mouse o un mando de Xbox. Las aplicaciones no es necesario modificar para ejecutarse en el simulador y no sabe que no se está ejecutando en un auricular envolvente.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitar el simulador de Windows Mixed Reality

1. **Habilitar el modo de programador** en Configuración -> actualizaciones y seguridad -> para desarrolladores
2. Iniciar el **Portal de realidad mixta** desde el escritorio
3. Si se trata de la primera vez que inicie el portal, deberá ir a través de la experiencia de instalación
   1. Haga clic en **empezar a trabajar**
   2. Haga clic en **acepto** que acepte el contrato
   3. Haga clic en **configurado para la simulación (para desarrolladores)** para continuar con la instalación sin un dispositivo físico
   4. Haga clic en **configurar** para confirmar su elección
4. Haga clic en el **para desarrolladores** botón en el lado izquierdo del Portal de realidad mixta
5. Gire el interruptor de alternancia de simulación a **en**
   * Esto requiere permisos de administrador y debe aceptar el cuadro de diálogo Control de cuentas de usuario que aparece

Ahora debe ejecutar con la simulación.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implementación de aplicaciones en el simulador de realidad mixta

Dado que el simulador se ejecuta en su equipo local sin una máquina Virtual, simplemente puede implementar las aplicaciones de Windows Universal para el **máquina Local** al depurar.

## <a name="basic-simulator-input"></a>Entrada de simulador básica

Controlar el simulador es muy similar a muchos juegos de vídeo 3D comunes y [emulador de HoloLens](using-the-hololens-emulator.md). Hay opciones de entrada mediante el teclado, mouse o mando de Xbox.

Controlar el simulador dirigiendo las acciones de un usuario simulado gastando de un auricular envolvente. Las acciones de mover al usuario simulado y hacer que las interacciones con las aplicaciones que responden como lo harían en un auricular envolvente.
* **Recorrer hacia delante, izquierda y derecha** -usar el W, A, S y D teclas del teclado o el stick izquierdo en un controlador de Xbox.
* **Buscar hacia arriba, abajo, izquierda y a la derecha** -hacer clic y arrastrar el mouse, utilice las teclas de flecha del teclado o el stick derecho en un controlador de Xbox.
* **Acción de presionar el botón en el controlador** : haga clic en el mouse, presione la tecla ENTRAR del teclado o usar el botón en un controlador de Xbox.
* **En el controlador de presionar el botón de inicio** : presione la tecla de Windows o la tecla F2 del teclado, o presione el botón B en un controlador de Xbox.
* **Movimiento de controlador para el desplazamiento** : mantenga presionada la tecla Alt, mantenga presionado el botón secundario del mouse y arrastre el mouse arriba / abajo, o en un controlador Xbox presionada el desencadenador correcto y un botón y Subir o bajar el stick derecho.

## <a name="tracked-controllers"></a>Controladores de seguimiento

El simulador de realidad mixta puede simular hasta dos controladores de mano movimiento sometidas a seguimiento. Habilitarlas mediante los conmutadores de alternancia en el Portal de realidad mixta. Cada controlador simulado tiene:
* Posición en el espacio
* Botón Inicio
* Botón de menú
* Botón de control
* Panel táctil

## <a name="see-also"></a>Vea también
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Avanzado de entrada del simulador de realidad mixta](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
