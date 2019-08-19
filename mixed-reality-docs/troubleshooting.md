---
title: Solución de problemas de HoloLens
description: Pasos para la solución de problemas de Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: problemas, errores, solución de problemas, corrección, ayuda, soporte técnico, HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550884"
---
# <a name="hololens-troubleshooting"></a>Solución de problemas de HoloLens

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Mi HoloLens no responde o no arranca

Si HoloLens no arranca:
* Si los LEDs del botón de encendido no se encienden, o si solo 1 LED parpadea brevemente, es posible que tenga que cargar HoloLens.
* Si los LED se encienden al presionar el botón de encendido, pero no puede ver nada en las pantallas, mantenga presionado el botón de encendido hasta que el botón de encendido desactive los 5 de los LEDs.

Si HoloLens está inmovilizado o no responde:
* Para desactivar HoloLens, presione el botón de encendido hasta que los 5 LEDs del botón de encendido se desactiven o durante 10 segundos si los LED no responden. Vuelva a presionar el botón de encendido para arrancar.

Si estos pasos no funcionan:
* Puede intentar [recuperar el dispositivo](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Los hologramas no tienen un aspecto correcto o se mueven.

Si los hologramas son inestables, saltan o no parecen correctos, pruebe una de estas correcciones:
* Limpie el visor del dispositivo y asegúrese de que no hay nada que obstruya los sensores.
* Asegúrese de que haya suficiente luz en su habitación.
* Intente caminar y mire el entorno para que HoloLens pueda escanearlos más completamente.
* Intente ejecutar la aplicación de calibración. Calibra su HoloLens para que funcione mejor para sus ojos. Vaya a **configuración** > **utilidades** **del sistema** > . En calibración, seleccione **abrir calibración**.
* Si sigue teniendo problemas después de ejecutar la aplicación de calibración, use la aplicación de optimización de sensor para optimizar los sensores de dispositivos. Vaya a **configuración** > **utilidades** **del sistema** > . En ajuste del sensor, seleccione **abrir la optimización del sensor**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens no responde a mis gestos.

Para asegurarse de que HoloLens puede ver los gestos, mantenga su mano en el marco de gestos, que extiende un par de metros a cada lado de usted. Cuando HoloLens pueda ver su mano, el cursor cambiará de un punto a un anillo. Más información sobre el uso de [gestos](gestures.md).

Si el entorno es demasiado oscuro, es posible que HoloLens no vea su mano, así que asegúrese de que hay suficiente luz.

Si el parasol tiene huellas digitales o manchas, use el tejido de limpieza de microfiber que venía con HoloLens para limpiar el parasol suavemente.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens no responde a los comandos de voz.

Si Cortana no responde a los comandos de voz, asegúrese de que Cortana está activado. En la lista todas las aplicaciones, seleccione el menú de Cortana > > Notebook > configuración para realizar cambios. Para obtener más información sobre lo que puede decir, consulte uso de la voz para controlar HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>No puedo colocar hologramas ni ver los hologramas que había colocado previamente.

Si HoloLens no puede asignar o cargar el espacio, entrará en modo limitado y no podrá colocar hologramas ni ver los hologramas que haya colocado. Estas son algunas cosas que pueden probarse:
* Asegúrese de que haya suficiente luz en su entorno para que HoloLens pueda ver y asignar el espacio.
* Asegúrese de que está conectado a una red Wi-Fi. Si no está conectado a la red Wi-Fi, HoloLens no puede identificar ni cargar un espacio conocido.
* Si necesita crear un nuevo espacio, conéctese a Wi-Fi y, a continuación, reinicie HoloLens.
* Para ver si el espacio correcto está activo o para cargar manualmente un espacio, vaya a **configuración** > **espacios** **del sistema** > .
* Si se carga el espacio correcto y sigue teniendo problemas, puede que el espacio esté dañado. Para corregir esto, seleccione el espacio y, a continuación, seleccione quitar. Una vez que se quita el espacio, HoloLens comenzará a asignar el entorno y creará un espacio nuevo.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Mi HoloLens suele entrar en modo limitado o muestra un mensaje de "seguimiento perdido".

Si el dispositivo suele mostrar un mensaje de "modo limitado" o "se perdió el seguimiento", pruebe las sugerencias de [mis hologramas no se ven bien o se mueven](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>Mi HoloLens no puede saber qué espacio tengo.

Si HoloLens no puede identificar y cargar automáticamente el espacio en el que se encuentra, asegúrese de que está conectado a la red Wi-Fi, hay mucha luz en el salón y no ha habido cambios importantes en el entorno. También puede cargar un espacio manualmente o administrar los espacios; para ello, vaya a **configuración** > **espacios** **del sistema** > .

## <a name="im-getting-a-low-disk-space-error"></a>Obtengo un error de "espacio insuficiente en disco".

Deberá liberar espacio de almacenamiento mediante una o varias de las siguientes acciones:
* Elimine algunos espacios no usados. Vaya a **configuración** > **espacios** **del sistema** > , seleccione un espacio que ya no necesite y, a continuación, seleccione **quitar**.
* Quite algunos de los hologramas que ha colocado.
* Elimine algunas imágenes y vídeos de la aplicación fotos.
* Desinstale algunas aplicaciones de HoloLens. En la lista todas las aplicaciones, pulse y mantenga presionada la aplicación que quiere desinstalar y,a continuación, seleccione Desinstalar.

## <a name="my-hololens-cant-create-a-new-space"></a>Mi HoloLens no puede crear un nuevo espacio.

El problema más probable es que se esté quedando sin espacio de almacenamiento. Pruebe una de las [sugerencias anteriores](#im-getting-a-low-disk-space-error) para liberar espacio en disco.
