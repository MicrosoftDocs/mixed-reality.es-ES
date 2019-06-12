---
title: Entrada de voz
description: Entrada de voz es una entrada de núcleo para HoloLens y Windows Mixed Reality inmersivos. Voz puede usarse para los comandos, dictado, Cortana y mucho más.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, voz, cortana, voz, de entrada
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829949"
---
# <a name="voice-input"></a>Entrada de voz

Voz es una de las tres formas de clave de entrada en HoloLens. Permite un holograma de comandos directamente sin tener que usar [gestos](gestures.md). Puede simplemente [que mirar](gaze.md) en un holograma y diga su comando. Entrada de voz puede ser una manera natural para comunicar su intención. Voz es especialmente buena atravesar interfaces complejas, ya que permite a los usuarios Cortar a través de los menús anidados con un solo comando.

Entrada de voz está basado el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admita la voz en todas las demás aplicaciones universales de Windows.

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con micrófono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>El comando "select"

Incluso sin específicamente agregar compatibilidad con voz a su aplicación, los usuarios pueden activar hologramas simplemente al decir "select". Este comportamiento es el mismo que un [en el aire](gestures.md#air-tap) en HoloLens, si se presiona el botón de selección en el [HoloLens clicker](hardware-accessories.md#hololens-clicker), o si se presiona el desencadenador en un [controlador de movimiento de Windows Mixed Reality](motion-controllers.md). Oirá un sonido y aparece una información sobre herramientas con "select" como confirmación. "Select" se habilita mediante un algoritmo de detección de la palabra clave de bajo consumo de energía para que siempre esté disponible para decir en cualquier momento con un impacto mínimo batería vida, incluso con las manos a su lado.

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

![Diga "seleccionar" usar el comando de voz para la selección](images/kma-voice-select-00170-800px.png)<br>
*Diga "seleccionar" usar el comando de voz para la selección*

## <a name="hey-cortana"></a>Hola Cortana

También puede decir "Hola Cortana" para que aparezca de Cortana en cualquier momento. No tendrá que esperar para que ella aparezca continuar le pide su pregunta u otorgándole una instrucción - por ejemplo, pruebe diciendo: "Hola Cortana ¿qué es el tiempo?" como una frase única. Para obtener más información acerca de Cortana y qué puede hacer, simplemente le solicito! Diga "Hola Cortana qué decir?" y le traemos una lista de comandos sugeridos y no laborables. ¿Si ya está en la aplicación de Cortana también puede hacer clic en el **?** icono de la barra lateral para extraer el mismo menú.

**Comandos específicos de HoloLens**
* "¿Qué puedo decir?"
* "Go home" o "Ir a Inicio" - en lugar de [bloom](gestures.md#bloom) para llegar a [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Inicie <app>"
* "Mover <app> aquí"
* "Capturar una imagen"
* "Iniciar grabación"
* "Detener la grabación"
* "Aumentar el brillo"
* "Reduce el brillo"
* "Aumentar el volumen"
* "Reducir el volumen"
* "Activar" o "Desactivar"
* "Apagar el dispositivo"
* "Reinicie el dispositivo"
* "Ir al modo de suspensión"
* "¿A qué hora es?"
* "La batería ¿cuánto me queda?"
* "Llamar a <contact>" (requiere Skype para HoloLens)

## <a name="see-it-say-it"></a>"Lo ve, diga"

HoloLens tienen un modelo de "verlo, diga" para la entrada de voz, donde las etiquetas de los botones de indicar a los usuarios también puede decir qué comandos de voz. Por ejemplo, al examinar una aplicación 2D, un usuario puede decir el comando "Ajustar" que se verán en la barra de aplicaciones para ajustar la posición de la aplicación en el mundo.

![Al examinar una aplicación 2D u holograma, un usuario puede decir el comando "Ajustar" que se verán en la barra de aplicaciones para ajustar la posición de la aplicación en el mundo](images/microphone-600px.png)

Cuando las aplicaciones siguen esta regla, pueden comprender fácilmente a los usuarios qué decirles a controlar el sistema. Para reforzar, mientras gazing en un botón, verá una información sobre herramientas "voz permanencia" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para comunicar para "presionar".

![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)<br>
*"Vea, diga" comandos aparecen debajo de los botones*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para la manipulación rápida de holograma

También hay una serie de voz comandos que puede decir al gazing en un holograma para realizar rápidamente tareas de manipulación. Estos comandos de voz funcionan en aplicaciones 2D, así como objetos 3D que se han realizado en el mundo.

**Comandos de manipulación de holograma**
* Se enfrentan a mí
* Mayor | Mejorar
* Más pequeñas

## <a name="dictation"></a>Dictado

En lugar de escribir con [derivaciones del aire](gestures.md#air-tap), dictado de voz puede ser más eficaz para escribir texto en una aplicación. Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.

![Dictado de voz comienza seleccionando el botón de micrófono](images/micbuttonfordictation.png)<br>
*Dictado de voz comienza seleccionando el botón de micrófono en el teclado*

Siempre que el teclado holográfico está activo, puede cambiar al modo de dictado en lugar de escribir. Seleccione el micrófono junto al cuadro de entrada de texto para empezar a trabajar.

## <a name="communication"></a>Comunicación

Para las aplicaciones que desean aprovechar las ventajas de la entrada de audio personalizada proporcionadas por HoloLens de opciones de procesamiento, es importante comprender los distintos [categorías de la secuencia de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) puede consumir la aplicación. Admite Windows 10 realiza varias categorías de flujo diferentes y HoloLens usa de tres de estas para permitir un procesamiento personalizado optimizar la calidad de audio del micrófono adaptada de voz, la comunicación y otros que se puede usar para el sonido de ambiente del entorno escenarios de captura (es decir, "cámaras de vídeo").
* La categoría de la secuencia AudioCategory_Communications se personaliza para escenarios de calidad y la narración de llamada y proporciona al cliente con una secuencia de audio mono 24 de kHz 16 bits de la voz del usuario
* La categoría de la secuencia AudioCategory_Speech personalizada para el motor de voz de HoloLens (Windows) y le proporciona una secuencia de mono 24 de kHz 16 bits de la voz del usuario. Esta categoría se puede usar por 3rd motores de terceros de voz si es necesario.
* La categoría de la secuencia AudioCategory_Other se personaliza para la grabación de audio de ambiente del entorno y proporciona al cliente con una secuencia de audio estéreo de 48 bits 24 kHz.

Todo este procesamiento de audio es lo que significa que mucho menos energía que si se realiza el procesamiento mismo de la CPU de HoloLens de drenaje de las características de aceleración de hardware. Evite ejecutar otra entrada de audio de procesamiento de la CPU para maximizar la duración de la batería del sistema y aprovechar las ventajas de la compilación, descarga el procesamiento de entrada de audio.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene un "Hola Cortana" y los problemas con "select", intente mover a un espacio y más suave, al lado opuesto al origen de ruido o hablando más alto. En este momento, todos los reconocimiento de voz en HoloLens se optimizan y optimizado específicamente para hablantes nativos de inglés de Estados Unidos.

La versión de Windows Mixed Reality Developer Edition 2017, la lógica de administración de extremo de audio funcionará correctamente (de manera indefinida) después de iniciar sesión alejar y atrás en el escritorio del equipo después de la conexión HMD inicial. Antes de ese primer inicio de sesión o en el evento después de pasar por WMR OOBE, el usuario podría experimentar diversos problemas de funcionalidad de audio comprendido entre sin audio sin audio cambiar dependiendo de cómo se ha configurado el sistema antes de conectar el HMD por primera vez.

## <a name="see-also"></a>Vea también
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Entrada de voz en Unity](voice-input-in-unity.md)
* [MR Input 212: voz](holograms-212.md)
