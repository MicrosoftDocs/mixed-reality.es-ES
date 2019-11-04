---
title: Comandos de voz
description: Mirada, gesto y voz (GGV) son el medio principal de interacción en HoloLens. Este artículo proporciona información detallada sobre el diseño de voz.
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, design, interaction, voice
ms.openlocfilehash: bfcaef787b22f17da9627a53c92c43f5cb1e1d9b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437218"
---
# <a name="voice-commanding"></a>Comandos de voz

Al utilizar los comandos de voz, la mirada se utiliza normalmente como un mecanismo selector de destino, ya sea como un puntero ("seleccionar") o para dirigir un comando a una aplicación ("verlo, decirlo"). Por supuesto, algunos comandos de voz no requieren un destino, como "Ir al comienzo" o "Hola, Cortana".


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Comandos de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con casco adjunto)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>Cómo se usa la voz

Considera la posibilidad de agregar comandos de voz a cualquier experiencia que compiles. La voz es una manera eficaz y cómoda de controlar el sistema y las aplicaciones. Dado que los usuarios hablan con variantes regionales y acentos diversos, la opción adecuada de palabras clave de voz asegurará que los comandos de los usuarios se interpretan de forma inequívoca.

### <a name="best-practices"></a>Procedimiento recomendado

A continuación se muestran algunas prácticas que te ayudarán a realizar sin problemas las tareas de reconocimiento de voz.
* **Usa comandos concisos**: cuando sea posible, elige palabras clave de dos o más sílabas. Las palabras de una sílaba tienden a tener diferentes pronunciaciones de las vocales dependiendo del acento de la persona. Ejemplo: "reproducir vídeo" es mejor que "reproducir el vídeo seleccionado actualmente"
* **Usar vocabulario simple** : por ejemplo, "show Note" es mejor que "show letrero"
* **Asegúrate de que los comandos no sean destructivos**: haz que cualquier acción que se puede realizar mediante un comando de voz no sea destructiva, y se pueda deshacer fácilmente, en caso de que otra persona que esté hablando cerca del usuario pueda desencadenar accidentalmente un comando.
* **Evita los comandos que tengan un sonido similar**: evita registrar varios comandos de voz que suenen de forma parecida. Ejemplo: "Mostrar más" y "Mostrar tienda" puede ser un sonido muy similar.
* **Anula el registro de la aplicación cuando no esté en uso**: cuando la aplicación no está en un estado en el que un comando de voz determinado es válido, considera la posibilidad de anular el registro de modo que otros comandos no se confundan con ese.
* **Prueba con diferentes acentos**: prueba la aplicación con usuarios con diferentes acentos.
* **Mantén la coherencia en los comandos de voz**: si "Volver" va a la página anterior, mantén este comportamiento en tus aplicaciones.
* **Evita el uso de comandos del sistema**: los siguientes comandos de voz están reservados para el sistema. Las aplicaciones no deben utilizar estos comandos.
   * "Hola Cortana"
   * "Seleccionar"

### <a name="select"></a>"Seleccionar"

Decir "seleccionar" en cualquier momento activará aquello a lo que está apuntando el cursor de mirada. 

>Nota: en HoloLens 2, el cursor de miración debe invocarse primero indicando la palabra "Select". Vuelve a decir "seleccionar" para activar. Para ocultar el cursor de mirada, utiliza las manos, pulsa en el aire o toca un objeto. 

### <a name="see-it-say-it"></a>Verlo, decirlo

Windows Mixed Reality emplea un modelo de voz "verlo, decirlo" en el que **las etiquetas en los botones son idénticas a los comandos de voz asociados**. Como no hay ninguna diferencia entre la etiqueta y el comando de voz, los usuarios pueden saber mejor qué decir para controlar el sistema. Para servir de refuerzo, si el usuario se mantiene sobre un botón aparecerá una **"sugerencia de marca para voz"** para comunicar qué botones están habilitados para voz.


![Ejemplo 1 de verlo, decirlo](images/voice-seeitsayit1-640px.jpg)

![Ejemplo 2 de verlo, decirlo](images/voice-seeitsayit2-640px.jpg)<br>
*Ejemplos de "verlo, decirlo"*

### <a name="voices-strengths"></a>Puntos fuertes de los comandos de voz

Las entradas de voz son una manera natural de comunicar nuestras intenciones. La voz es especialmente buena en los **recorridos** por la interfaz, ya que puede ayudar a los usuarios a atajar saltando varios pasos de una interfaz (un usuario podría decir "volver" al buscar en una página web, en lugar de tener que ir y presionar el botón Atrás en la aplicación). Este pequeño ahorro de tiempo tiene un potente **efecto emocional** en la percepción de la experiencia que tiene el usuario, dándoles un pequeño superpoder. El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**. En los dispositivos en los que es difícil escribir en un teclado, el **dictado de voz** puede ser una alternativa eficaz para realizar entradas. Por último, en algunos casos, cuando el **intervalo de precisión** para mirada y gesto es limitado, la voz puede ser el único método de entrada fiable para un usuario.

**Cómo puede beneficiar al usuario la utilización de la voz**
* Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.
* Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.
* Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.
* Es aceptable socialmente: se adapta a las normas sociales en términos de comportamiento.
* Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.

### <a name="voices-weaknesses"></a>Desventajas de los comandos de voz

La voz también tiene algunas desventajas. Uno de ellos es la falta de precisión en el control. (por ejemplo un usuario puede decir "más alto", pero no puede decir cuánto). "Un poco" es algo difícil de cuantificar. El movimiento o el escalado de las cosas con la voz también es también difícil (la voz no ofrece granularidad en el control). Los comandos de voz también pueden ser imperfectos. A veces, un sistema de voz escucha de forma incorrectamente un comando o no lo escucha. Recuperarse de estos errores es un desafío en cualquier interfaz. Por último, el uso de la voz puede no ser socialmente aceptable en lugares públicos. Hay algunas cosas que los usuarios no pueden o no deben decir. Por estos motivos, el habla debe utilizarse para aquello para lo que mejor sirve.

### <a name="voice-feedback-states"></a>Estados de la respuesta a la voz

Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**. Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal. A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.

![Estados de la respuesta a la voz del cursor](images/voicefeedbackstates.png)<br>
*Estados de la respuesta a la voz del cursor*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Cosas principales que los usuarios deben saber sobre los comandos de voz en la realidad mixta
* Di **"Seleccionar"** mientras seleccionas como destino un botón (puedes usar esto en cualquier lugar para hacer clic en un botón).
* Puedes decir el **nombre de etiqueta de un botón de la barra de la aplicación** en algunas aplicaciones para realizar una acción. Por ejemplo, al examinar una aplicación, un usuario puede decir el comando "Quitar" para quitar la aplicación (esto te ahorra el tiempo de hacer clic con la mano).
* Puedes iniciar la escucha de Cortana diciendo **"Hola Cortana".** Puedes preguntarle cosas ("Hola Cortana, cuál es la altura de la torre Eiffel"), decirle que abra una aplicación ("Hola Cortana, abre Netflix") o que abra el menú Inicio ("Hola Cortana, llévame al principio") y mucho más.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Preguntas y dudas comunes que tienen los usuarios acerca del uso de la voz
* ¿Qué puedo decir?
* ¿Cómo sé si el sistema me escuchó correctamente?
   * El sistema se equivoca todo el tiempo con mis comandos de voz.
   * No reacciona cuando digo un comando de voz.
* Reacciona de forma equivocada cuando digo un comando de voz.
* ¿Cómo dirijo mi voz a una aplicación o un comando de la aplicación específicos?
* ¿Puedo usar la voz para comandar cosas en el marco holográfico en HoloLens?

## <a name="see-also"></a>Consulta también
* [Gestos](gaze-and-commit.md#composite-gestures)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
