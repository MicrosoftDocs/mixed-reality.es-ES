---
title: Accesorios de hardware
description: Describe los tipos de accesorios disponibles para usar con Windows Mixed Reality y cómo configurarlos.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: procedimientos, accesorios, Bluetooth, BT, controlador, controlador para juegos, haga clic en Xbox
ms.openlocfilehash: 556fc77ffb588c02ea17e8c97293f527469216f8
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866875"
---
# <a name="hardware-accessories"></a>Accesorios de hardware

Los dispositivos de Windows Mixed Reality admiten accesorios. Puede usar Bluetooth o USB para emparejar los accesorios admitidos con un casco envolvente mediante el equipo al que está conectado.

Para obtener información sobre el uso de accesorios Bluetooth con HoloLens, consulte [conexión a dispositivos Bluetooth y USB-C](https://docs.microsoft.com/hololens/hololens-connect-devices).

Los auriculares que se encuentran en la realidad mixta de Windows requieren accesorios para la entrada más allá de la [mirada](gaze-and-commit.md) y la [voz](voice-input.md). Los accesorios admitidos son el **teclado y el mouse**, el **controlador de juegos**y **[los controladores de movimiento](motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Emparejamiento de accesorios Bluetooth

Emparejar un periférico Bluetooth con un casco inmersivo es similar a emparejar un periférico Bluetooth con un dispositivo móvil o de escritorio de Windows 10:

1. En el menú Inicio, abra la aplicación de **configuración** .
2. Ir a **dispositivos**
3. Activar el radio Bluetooth Si está desactivado con el conmutador deslizante
4. Coloque el dispositivo Bluetooth en modo de emparejamiento. Esto varía de un dispositivo a un dispositivo. En la mayoría de los dispositivos Bluetooth, esto se hace presionando y manteniendo uno o más botones.
5. Espere a que el nombre del dispositivo se muestre en la lista de dispositivos Bluetooth. Cuando lo haga, seleccione el dispositivo y, a continuación, seleccione el botón **emparejar** . Si tiene muchos dispositivos Bluetooth cerca, puede que tenga que desplazarse hasta la parte inferior de la lista de dispositivos Bluetooth para ver el dispositivo que está intentando emparejar.
6. Cuando se emparejan periféricos Bluetooth con capacidad de entrada (por ejemplo, teclados Bluetooth), es posible que se muestre un PIN de 6 dígitos o 8 dígitos. Asegúrese de escribir ese pin en el periférico y, a continuación, presione Entrar para completar el emparejamiento con el casco.

## <a name="motion-controllers"></a>Controladores de movimiento

Los auriculares envolventes admiten [controladores de movimiento](motion-controllers.md) de Windows Mixed Reality, pero no HoloLens. Estos controladores ofrecen un seguimiento preciso y con capacidad de respuesta del movimiento en el campo de vista mediante los sensores en el casco envolvente, lo que significa que no es necesario instalar hardware en las paredes del espacio. Cada controlador incluye varios métodos de entrada.

![Controladores de movimiento de Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)

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
