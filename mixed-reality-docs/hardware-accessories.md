---
title: Accesorios de hardware
description: Describe los tipos de accesorios disponibles para su uso con HoloLens y Windows Mixed Reality y cómo configurarlas.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: tema de procedimientos, Accesorios, bluetooth, bt, controlador, controlador para juegos, clicker, xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605711"
---
# <a name="hardware-accessories"></a>Accesorios de hardware

Los dispositivos de Windows Mixed Reality admiten accesorios. Par de accesorios admitidos de HoloLens con Bluetooth, mientras que puede usar Bluetooth o USB al par admite accesorios de un auricular envolvente mediante el equipo al que está conectado.

Dos escenarios comunes para el uso de accesorios con HoloLens son como sustitutos para el aire pulse gestos y el teclado virtual. Para ello, los dos accesorios más comunes son el **HoloLens Clicker** y **teclados Bluetooth**. Microsoft HoloLens incluye una radio Bluetooth 4.1 y admite [HID de Bluetooth](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) y [Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) perfiles.

Inmersivos Windows Mixed Reality requieren accesorios para la entrada más allá de [que mirar](gaze.md) y [voz](voice-input.md). Accesorios admitidos incluyen **teclado y mouse**, **gamepad**, y  **[controladores de movimiento](motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Emparejamiento accesorios Bluetooth

Emparejamiento un Bluetooth periférico con Microsoft HoloLens es similar al emparejamiento un Bluetooth periférico con Windows 10 escritorio o dispositivo móvil:
1. En el menú Inicio, abra el **configuración** app
2. Vaya a **dispositivos**
3. Activar la radio Bluetooth si está desactivada utilizando el control deslizante
4. Coloque el dispositivo Bluetooth en modo de emparejamiento. Esto varía de un dispositivo a otro. En la mayoría de los dispositivos Bluetooth, esto se hace presionando y manteniendo presionado a uno o varios botones.
5. Espere a que el nombre del dispositivo en aparecer en la lista de dispositivos Bluetooth. Cuando lo, seleccione el dispositivo, a continuación, seleccione el **par** botón. Si tiene muchos dispositivos Bluetooth cercanos deba desplazarse a la parte inferior de la lista de dispositivos Bluetooth para ver el dispositivo que intenta emparejar.
6. Cuando emparejamiento periféricos Bluetooth con capacidad de entrada (p. ej.: Teclados Bluetooth), puede aparecer un dígito de 6 o un pin de 8 dígitos. Asegúrese de escribir el pin en los periféricos y, a continuación, presione ENTRAR para completar el emparejamiento con Microsoft HoloLens.

## <a name="motion-controllers"></a>Controladores de movimiento

Windows Mixed Reality [controladores de movimiento](motion-controllers.md) son compatibles con inmersivos, pero no HoloLens. Estos controladores ofrecen seguimiento precisa y con capacidad de respuesta de movimiento en el campo de visión con los sensores en los auriculares envolventes, lo que significa que no es necesario instalar hardware de los planos laterales en su espacio. Cada controlador incluye varios métodos de entrada.

![Controladores de movimiento Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

El HoloLens Clicker es el primer dispositivo periférico creado específicamente para HoloLens y se incluye con la edición de desarrollo de HoloLens. El HoloLens Clicker permite a un usuario haga clic en y se desplazan con el movimiento de mano mínimo como un reemplazo para el gesto de pulsar en el aire. No es un reemplazo para todos los [gestos](gestures.md). Por ejemplo, [bloom](gestures.md#bloom) y [cambiar el tamaño o](gestures.md#composite-gestures) gestos usar movimientos de mano. El clicker HoloLens es un dispositivo de sensor de orientación con un botón simple. Se conecta a la HoloLens con Bluetooth baja energía (BTLE).

![El HoloLens Clicker](images/hololens-clicker-500px.jpg)

Para seleccionar un [holograma](hologram.md), mire en él y, a continuación, haga clic en. Orientación de la clicker no es relevante para esta operación. Para desplazar o panorámica, haga clic y mantenga, gire a la Clicker arriba/abajo o izquierda/derecha. Durante el desplazamiento, pondremos en contacto con la velocidad más rápida con tan solo +/-15 º de giro de muñeca. Transfiriendo más no se desplazan cualquiera con mayor rapidez.

Hay dos LED dentro de la Clicker:
* El LED blanco indica si el dispositivo es de emparejamiento (parpadeante) o cargando (sólido)
* El ámbar LED indica que el dispositivo tiene poca batería (parpadeante) o ha producido un error (sólido)

Puede esperar dos semanas o más de uso habitual en una carga completa (es decir, 2 y 3 horas en un cargador de pared). Cuando la batería es baja, el ámbar que LED parpadea 10 veces durante un período de 5 segundos si presiona el botón o se activará desde suspensión. El ámbar que LED parpadea más rápidamente a través de un período de 5 segundos si su Clicker está en modo de batería críticamente baja.

## <a name="bluetooth-keyboards"></a>Teclados de Bluetooth

Teclados de Bluetooth Qwerty inglés pueden combinarse y usan en cualquier lugar que puede usar el teclado holográfico. Obtención de un teclado de calidad hace una diferencia, por lo que se recomienda la [Microsoft Keyboard que pueden doblarse Universal](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) o el [Bluetooth de diseñador de Microsoft Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Controladores de Bluetooth

Puede usar un controlador con aplicaciones y juegos que habiliten específicamente la compatibilidad de controlador para juegos. Configuración de los controles no se puede usar para controlar la interfaz de usuario de HoloLens.

Controladores de Wireless Xbox que vienen con la S de una Xbox o vende como Accesorios para la característica de S una Xbox conectividad Bluetooth que puedan usarse con HoloLens e inmersivos. El controlador de Xbox Wireless [debe actualizarse](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) antes de que se puede usar con HoloLens.

Otras marcas de la configuración de Bluetooth los controles pueden trabajar con dispositivos de Windows Mixed Reality, pero el soporte técnico variará por aplicación.

## <a name="other-bluetooth-accessories"></a>Otros accesorios Bluetooth

Siempre que los periféricos es compatible con perfiles de HID de Bluetooth o GATT, podrá emparejar con HoloLens. Otros dispositivos HID de Bluetooth y GATT además de teclado, mouse y el HoloLens Clicker pueden requerir una aplicación complementaria de Microsoft HoloLens en estar completamente funcional.

Periféricos no admitidos se incluyen:
* No se admiten los periféricos en los perfiles de audio de Bluetooth.
* Dispositivos de audio de Bluetooth como altavoces y auriculares pueden aparecer como disponibles en la aplicación de configuración, pero no se admiten para su uso con Microsoft HoloLens como un punto de conexión de audio.
* No se admiten equipos y teléfonos habilitados para Bluetooth emparejados y usar para transferir archivos.

## <a name="unpairing-a-bluetooth-peripheral"></a>Desemparejamiento un periférico Bluetooth
1. En el menú Inicio, abra el **configuración** app
2. Vaya a **dispositivos**
3. Activar la radio Bluetooth si está desactivada
4. Busque el dispositivo en la lista de dispositivos Bluetooth disponibles
5. Seleccione el dispositivo de la lista y, a continuación, seleccione el **quitar** botón

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Deshabilitar Bluetooth en Microsoft HoloLens

Esto se desactivará los componentes de RF de la radio Bluetooth y deshabilitar toda la funcionalidad de Bluetooth en Microsoft HoloLens.
1. En el menú Inicio, abra el **configuración** app
2. Vaya a **dispositivos**
3. Mueva el control deslizante de Bluetooth a la posición de apagado
