---
title: Accesorios de hardware
description: Describe los tipos de accesorios disponibles para usar con HoloLens y Windows Mixed Reality, y cómo configurarlos.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: procedimientos, accesorios, Bluetooth, BT, controlador, controlador para juegos, haga clic en Xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526609"
---
# <a name="hardware-accessories"></a>Accesorios de hardware

Los dispositivos de Windows Mixed Reality admiten accesorios. Puede emparejar los accesorios admitidos a HoloLens con Bluetooth, mientras que puede usar Bluetooth o USB para emparejar los accesorios admitidos con un casco envolvente a través del equipo al que está conectado.

Dos escenarios comunes para usar accesorios con HoloLens son los sustitutos del gesto de pulsación de aire y el teclado virtual. Para ello, los dos accesorios más comunes son el **clic de HoloLens** y los **teclados Bluetooth**. Microsoft HoloLens incluye una radio Bluetooth 4,1 y admite los perfiles [HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) Bluetooth y [Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) .

Los auriculares que se encuentran en la realidad mixta de Windows requieren accesorios para la entrada más allá de la [mirada](gaze.md) y la [voz](voice-input.md). Los accesorios admitidos son el **teclado y el mouse**, el **controlador de juegos**y **[los controladores de movimiento](motion-controllers.md)** .

## <a name="pairing-bluetooth-accessories"></a>Emparejamiento de accesorios Bluetooth

Emparejar un periférico Bluetooth con Microsoft HoloLens es similar a emparejar un periférico Bluetooth con un dispositivo móvil o de escritorio de Windows 10:
1. En el menú Inicio, abra la aplicación de **configuración** .
2. Ir a **dispositivos**
3. Activar el radio Bluetooth Si está desactivado con el conmutador deslizante
4. Coloque el dispositivo Bluetooth en modo de emparejamiento. Esto varía de un dispositivo a un dispositivo. En la mayoría de los dispositivos Bluetooth, esto se hace presionando y manteniendo uno o más botones.
5. Espere a que el nombre del dispositivo se muestre en la lista de dispositivos Bluetooth. Cuando lo haga, seleccione el dispositivo y, a  continuación, seleccione el botón emparejar. Si tiene muchos dispositivos Bluetooth cerca, puede que tenga que desplazarse hasta la parte inferior de la lista de dispositivos Bluetooth para ver el dispositivo que está intentando emparejar.
6. Cuando se emparejan periféricos Bluetooth con la función de entrada (por ejemplo: Teclados Bluetooth), se puede mostrar un PIN de 6 dígitos o 8 dígitos. Asegúrese de escribir ese pin en el periférico y, a continuación, presione Entrar para completar el emparejamiento con Microsoft HoloLens.

## <a name="motion-controllers"></a>Controladores de movimiento

Los auriculares envolventes admiten [controladores de movimiento](motion-controllers.md) de Windows Mixed Reality, pero no HoloLens. Estos controladores ofrecen un seguimiento preciso y con capacidad de respuesta del movimiento en el campo de vista mediante los sensores en el casco envolvente, lo que significa que no es necesario instalar hardware en las paredes del espacio. Cada controlador incluye varios métodos de entrada.

![Controladores de movimiento de Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>Clic en HoloLens

El clic de HoloLens es el primer dispositivo periférico creado específicamente para HoloLens y se incluye con la edición HoloLens Development. El clic de HoloLens permite al usuario hacer clic y desplazarse con un movimiento de mano mínimo como sustituto del gesto de pulsación de aire. No se sustituye por todos los [gestos](gestures.md). Por ejemplo, los gestos de [floración](gestures.md#bloom) y [cambio de tamaño o](gestures.md#composite-gestures) movimiento usan movimientos de mano. El clic de HoloLens es un dispositivo de sensor de orientación con un sencillo botón. Se conecta a HoloLens con Bluetooth de baja energía (BTLE).

![El clic de HoloLens](images/hololens-clicker-500px.jpg)

Para seleccionar un [holograma](hologram.md), mira en él y, después, haz clic en. La orientación del clic en no es importante para esta operación. Para desplazarse o desplazarse, haga clic y mantenga presionado el botón, y después gire el clic hacia arriba o hacia abajo o hacia la izquierda o la derecha. Al desplazarse, alcanzará la velocidad más rápida con un mínimo de +/-15 ° de rotación de la muñeca. Mover más no se desplazará más rápido.

Hay dos LED dentro del clic:
* El LED blanco indica si el dispositivo está emparejando (parpadeando) o cargándose (sólido)
* El LED ámbar indica que el dispositivo tiene batería baja (parpadeo) o ha sufrido un error (sólido)

Puede esperar 2 semanas o más de uso normal con una carga completa (es decir, 2-3 horas en un cargador de pared). Cuando la batería es baja, el LED ámbar parpadea 10 veces en un período de 5 segundos si presiona el botón o lo activa de suspensión. El LED ámbar parpadeará más rápido en un período de 5 segundos si el clic está en el modo de batería de nivel crítico.

## <a name="bluetooth-keyboards"></a>Teclados Bluetooth

Se pueden emparejar y usar los teclados de Bluetooth de inglés QWERTY en cualquier lugar en el que pueda usar el teclado Holographic. Obtener un teclado de calidad hace una diferencia, por lo que se recomienda el [teclado Microsoft universal doblado](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) o el [escritorio Bluetooth de Microsoft Designer](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Controladores para juegos Bluetooth

Puede usar un controlador con aplicaciones y juegos que habilitan específicamente la compatibilidad con el controlador de juegos. Los controladores de juegos no se pueden usar para controlar la interfaz de usuario de HoloLens.

Controladores inalámbricos de Xbox que se incluyen con la Xbox One S o como accesorios de la característica Xbox One S para la conectividad Bluetooth que les permite usarlos con HoloLens y cascos con auriculares envolvente. La controladora inalámbrica Xbox [debe actualizarse](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de poder usarla con HoloLens.

Otras marcas de los controladores de mandos de Bluetooth pueden funcionar con dispositivos de Windows Mixed Reality, pero la compatibilidad variará según la aplicación.

## <a name="other-bluetooth-accessories"></a>Otros accesorios Bluetooth

Siempre que el periférico admita los perfiles HID o GATT de Bluetooth, podrá emparejarse con HoloLens. Otros dispositivos HID y GATT de Bluetooth Además del teclado, el mouse y el clic de HoloLens pueden requerir que una aplicación complementaria en Microsoft HoloLens sea totalmente funcional.

Entre los periféricos no admitidos se incluyen:
* No se admiten periféricos en los perfiles de audio Bluetooth.
* Los dispositivos de audio Bluetooth, como los altavoces y los auriculares, pueden aparecer como disponibles en la aplicación de configuración, pero no se pueden usar con Microsoft HoloLens como punto de conexión de audio.
* Los teléfonos y equipos habilitados para Bluetooth no se admiten para la transferencia de archivos.

## <a name="unpairing-a-bluetooth-peripheral"></a>Desemparejar un periférico Bluetooth
1. En el menú Inicio, abra la aplicación de **configuración** .
2. Ir a **dispositivos**
3. Activar la radio Bluetooth Si está desactivada
4. Busque el dispositivo en la lista de dispositivos Bluetooth disponibles
5. Seleccione el dispositivo en la lista y, a continuación, seleccione el botón **quitar** .

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Deshabilitación de Bluetooth en Microsoft HoloLens

Se desactivarán los componentes de RF del radio Bluetooth y se deshabilitará toda la funcionalidad de Bluetooth en Microsoft HoloLens.
1. En el menú Inicio, abra la aplicación de **configuración** .
2. Ir a **dispositivos**
3. Mover el interruptor del control deslizante para Bluetooth a la posición de apagado
