---
title: Entrada de voz
description: La entrada de voz es una entrada básica para los auriculares de la realidad de HoloLens y Windows Mixed Reality. Voice se puede usar para comandos, dictado, Cortana y mucho más.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: GGV, voz, Cortana, voz, entrada
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829949"
---
# <a name="voice-input"></a>Entrada de voz

Voice es una de las tres formas clave de entrada en HoloLens. Permite comandos directamente de un holograma sin tener que usar [gestos](gestures.md). Simplemente [mira](gaze.md) un holograma y habla el comando. La entrada de voz puede ser una forma natural de comunicar su intención. La voz es especialmente adecuada en el recorrido de interfaces complejas, ya que permite a los usuarios cortar menús anidados con un comando.

La entrada de voz se basa en el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admite la voz en todas las demás aplicaciones universales de Windows.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con micrófono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Comando "seleccionar"

Incluso sin agregar específicamente compatibilidad con voz a su aplicación, los usuarios pueden activar los hologramas simplemente diciendo "Select". Esto se comporta igual que una pulsación [aérea](gestures.md#air-tap) en HoloLens, presionando el botón seleccionar en el [clic de hololens](hardware-accessories.md#hololens-clicker)o presionando el desencadenador en un controlador de [movimiento de Windows Mixed Reality](motion-controllers.md). Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación. "Select" está habilitado por un algoritmo de detección de palabras clave de baja energía, por lo que siempre está disponible para que lo indique en cualquier momento con un impacto mínimo en la duración de la batería, incluso con sus manos en el lateral.

> [!NOTE]
> [Próximamente](index.md#news-and-notes) se ofrecerá orientación específica para HoloLens 2.

![Decir "seleccionar" para usar el comando de voz para la selección](images/kma-voice-select-00170-800px.png)<br>
*Decir "seleccionar" para usar el comando de voz para la selección*

## <a name="hey-cortana"></a>Hola Cortana

También puede decir "Hola Cortana" para abrir Cortana en cualquier momento. No tiene que esperar a que parezca que siga preguntando su pregunta o le dé una instrucción; por ejemplo, intente decir "Hola a Cortana ¿cuál es el tiempo?". como una sola oración. Para obtener más información sobre Cortana y lo que puede hacer, simplemente pregúntele. "Hola a Cortana ¿Qué puedo decir?" y desplegarán una lista de comandos de trabajo y sugeridos. Si ya está en la aplicación de Cortana, también puede hacer clic **en el** en la barra lateral para desplegar el mismo menú.

**Comandos específicos de HoloLens**
* "¿Qué puedo decir?"
* "Ir a Inicio" o "ir a Inicio"-en lugar de la [floración](gestures.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Launch <app>"
* "Moverse <app> aquí"
* "Tomar una imagen"
* "Iniciar grabación"
* "Detener grabación"
* "Aumentar el brillo"
* "Reducir el brillo"
* "Aumentar el volumen"
* "Reducir el volumen"
* "Silenciar" o "dessilenciar"
* "Apagar el dispositivo"
* "Reiniciar el dispositivo"
* "Ir a suspensión"
* "¿Qué hora es?"
* "¿Cuánta batería he dejado?"
* "Llamada <contact>" (requiere Skype para HoloLens)

## <a name="see-it-say-it"></a>"Verlo, decirlo"

HoloLens tiene un modelo "ver ti" para la entrada de voz, donde las etiquetas de los botones indican a los usuarios los comandos de voz que también pueden decir. Por ejemplo, al mirar una aplicación en 2D, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.

![Al mirar una aplicación 2D o un holograma, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.](images/microphone-600px.png)

Cuando las aplicaciones siguen esta regla, los usuarios pueden comprender fácilmente qué decir para controlar el sistema. Para reforzar esto, mientras se Gazing en un botón, verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar de "presionar".

![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)<br>
*"Ver, por ejemplo," los comandos aparecen debajo de los botones*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para la manipulación rápida de hologramas

También hay una serie de comandos de voz que puede decir mientras Gazing en un holograma para realizar rápidamente tareas de manipulación. Estos comandos de voz funcionan en aplicaciones 2D y en objetos 3D que se han colocado en el mundo.

**Comandos de manipulación de hologramas**
* Me encuentro
* Mayor | Enhance
* Disminuye

## <a name="dictation"></a>Dictado

En lugar de escribir con grifos de [aire](gestures.md#air-tap), el dictado de voz puede ser más eficaz para escribir texto en una aplicación. Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.

![El dictado de voz comienza seleccionando el botón micrófono](images/micbuttonfordictation.png)<br>
*El dictado de voz comienza seleccionando el botón micrófono del teclado.*

Siempre que el teclado Holographic esté activo, puede cambiar al modo de dictado en lugar de escribir. Seleccione el micrófono en el lateral del cuadro de entrada de texto para comenzar.

## <a name="communication"></a>Comunicación

En el caso de las aplicaciones que desean aprovechar las opciones de procesamiento de entrada de audio personalizadas proporcionadas por HoloLens, es importante comprender las distintas [categorías de flujo de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que puede consumir la aplicación. Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de ellas para habilitar el procesamiento personalizado con el fin de optimizar la calidad de audio del micrófono adaptada a la voz, la comunicación y otras que se pueden usar para el audio del entorno ambiente. escenarios de captura (es decir, "videocámara").
* La categoría AudioCategory_Communications Stream está personalizada para escenarios de calidad y narración de llamadas y proporciona al cliente una secuencia de audio mono 16kHz 24bit de la voz del usuario
* La categoría AudioCategory_Speech Stream está personalizada para el motor de voz HoloLens (Windows) y le proporciona un flujo mono 16kHz 24bit de la voz del usuario. Los motores de voz de terceros pueden usar esta categoría si es necesario.
* La categoría AudioCategory_Other Stream está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits de 48 bits.

Todo este procesamiento de audio se acelera en hardware, lo que significa que las características agotan una gran cantidad de energía que si se realizara el mismo procesamiento en la CPU de HoloLens. Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene algún problema con "Select" y "Hola Cortana", intente cambiar a un espacio más silencioso, desplazarse fuera del origen del ruido o hablar de más alto. En este momento, todo el reconocimiento de voz en HoloLens se ajusta y optimiza específicamente a los hablantes nativos de Estados Unidos inglés.

En el caso de la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (siempre) después de cerrar la sesión y volver a iniciarla en el escritorio del equipo después de la conexión inicial de HMD. Antes de ese primer evento de cierre de sesión/en el momento de pasar a través de WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio hasta sin conmutación de audio, en función de cómo se haya configurado el sistema antes de conectarse a HMD por primera vez.

## <a name="see-also"></a>Vea también
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Entrada de voz en Unity](voice-input-in-unity.md)
* [MR Input 212: voz](holograms-212.md)
