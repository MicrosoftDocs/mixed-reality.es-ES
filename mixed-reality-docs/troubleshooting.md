---
title: Solución de problemas de HoloLens
description: Pasos para solucionar problemas para Microsoft HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: problemas de errores, solucionar problemas, corregir, ayuda, soporte técnico, HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597577"
---
# <a name="hololens-troubleshooting"></a>Solución de problemas de HoloLens

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>Mi HoloLens no responde o no se inicia

Si no se inicia su HoloLens:
* Si no encenderán el LED mediante el botón de encendido, activada o solo 1 LED parpadea brevemente, es posible que deba cargar su HoloLens.
* Si el LED se iluminan cuando hay presiona el botón de encendido pero no puede ver nada en las pantallas, mantenga el botón de encendido hasta las 5 los LED mediante el botón de encendido se desactiva.

Si se convierte en su HoloLens inmovilizado o no responde:
* Desactivar la HoloLens presionando el botón de encendido hasta que todos los 5 de los LED mediante el botón de encendido desactivar a sí mismos, o durante 10 segundos si el LED son no responde. Presione el botón de encendido para que vuelva a arrancar.

Si estos pasos no funcionan:
* Puede intentar [recuperar el dispositivo](reset-or-recover-your-hololens.md).

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Hologramas no aparezcan correctamente o se a mover.

Si sus hologramas están inestable, con saltos o no se ven bien, intente una de estas correcciones:
* Limpiar el visor de dispositivo y asegúrese de que nada esté obstruyendo los sensores.
* Asegúrese de que hay suficiente luz en la habitación.
* Try deambulan y examinando respecto a su entorno de HoloLens por lo que pueden explorarlas más completamente.
* Intente ejecutar la aplicación de calibración. Lo calibra el HoloLens funcionar mejor para sus ojos. Vaya a **configuración** > **sistema** > **utilidades**. En la calibración, seleccione **calibración abierto**.
* Si sigue teniendo problemas después de ejecutar la aplicación de calibración, usar la aplicación de optimización Sensor para optimizar los sensores del dispositivo. Vaya a **configuración** > **sistema** > **utilidades**. En la optimización Sensor, seleccione **abierto de optimización Sensor**.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens no responden a mi gestos.

Para asegurarse de que HoloLens pueden ver los movimientos, mantener la mano en el marco de gesto, que amplía un par de pies a cada lado de ustedes. HoloLens pueden ver la mano, el cursor cambiará desde un punto a un anillo. Más información sobre el uso de [gestos](gestures.md).

Si su entorno es demasiado oscuro, HoloLens no es posible que vea su mano, así que asegúrese de que hay suficiente luz.

Si el hipervisor tiene las huellas digitales o el dedo, use el microfiber paño suministrada con el HoloLens para limpiar el hipervisor suavemente de limpieza.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens no responden a los comandos de voz.

Si Cortana no responde a los comandos de voz, asegúrese de que Cortana está activado. En la lista de todas las aplicaciones, seleccione Cortana > menú > cuaderno > configuración para realizar cambios. Para obtener más información sobre lo que puede decir, consulte usar su voz para controlar HoloLens.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>No puedo colocar hologramas o vea hologramas que coloqué anteriormente.

Si HoloLens no se pueden asignar o el espacio de carga, se pasará al modo limitado y no podrá colocar hologramas o vea hologramas que haya colocado. Estas son algunas cosas que pueden probarse:
* Asegúrese de que hay suficiente luz en su entorno para que pueden ver y asignar el espacio de HoloLens.
* Asegúrese de que está conectado a una red Wi-Fi. Si no está conectado a Wi-Fi, HoloLens no pueden identificar y cargar un espacio conocido.
* Si necesita crear un espacio, conectarse a Wi-Fi y reinicie la HoloLens.
* Para ver si el espacio correcto está activo, o para cargar manualmente un espacio, vaya a **configuración** > **sistema** > **espacios**.
* Si se carga el espacio correcto y sigue teniendo problemas, el espacio puede estar dañado. Para solucionar este problema, seleccione el espacio y luego seleccione Quitar. Una vez que se quita el espacio, HoloLens iniciará asignación respecto a su entorno y crear un nuevo espacio.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>Con frecuencia mi HoloLens entra en modo limitado o muestran un mensaje de "Seguimiento perdidos".

Si el dispositivo a menudo muestra un mensaje de "seguimiento perdido" o "modo limited", pruebe las sugerencias de [hologramas mi no aparezcan correctamente o se mueve en torno a](#holograms-dont-look-good-or-are-moving-around).

## <a name="my-hololens-cant-tell-what-space-im-in"></a>Mi HoloLens no pueden saber qué espacio me encuentro en.

Si su HoloLens automáticamente no se pueden identificar y cargar el espacio que se encuentra en, asegúrese de que está conectado a Wi-Fi, hay una gran cantidad de luz en la sala de reuniones y no ha habido cambios importantes a su entorno. También puede cargar manualmente un espacio o administrar los espacios, vaya a **configuración** > **sistema** > **espacios**.

## <a name="im-getting-a-low-disk-space-error"></a>Obtengo un error de "espacio en disco insuficiente".

Necesita liberar espacio de almacenamiento mediante uno o varios de los siguientes:
* Eliminar algunos espacios no utilizados. Vaya a **configuración** > **sistema** > **espacios**, seleccione un espacio ya no necesita y, a continuación, seleccione **quitar**.
* Quite algunos de los hologramas que haya colocado.
* Elimine algunas imágenes y vídeos en la aplicación fotos.
* Desinstalar algunas aplicaciones de su HoloLens. En la lista de todas las aplicaciones, pulse y mantenga la aplicación que desea desinstalar y, a continuación, seleccione **desinstalar**.

## <a name="my-hololens-cant-create-a-new-space"></a>Mi HoloLens no pueden crear un nuevo espacio.

El problema más probable es que está quedando sin espacio de almacenamiento. Pruebe uno de los [sugerencias anteriores](#im-getting-a-low-disk-space-error) para liberar espacio en disco.
