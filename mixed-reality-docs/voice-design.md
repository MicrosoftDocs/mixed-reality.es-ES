---
title: Diseño de voz
description: Mirada, gestos y voz (GGV) son el medio principal de interacción en HoloLens. Este artículo proporciona información detallada sobre el diseño de voz.
author: rwinj
ms.author: randyw
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, la interacción, voz
ms.openlocfilehash: 2df0e15c66891b08577fcf203d11f7c7008247f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605588"
---
# <a name="voice-design"></a>Diseño de voz

Mirada, gestos y voz (GGV) son el medio principal de interacción en HoloLens. [Observación](gaze.md) usa con un [cursor](cursors.md) es el mecanismo para tener como destino el contenido que están listos para interactuar con un usuario. [Gesto](gestures.md) o [voz](voice-input.md) son los mecanismos de intención. Mirada puede utilizarse con el gesto o de voz para completar una interacción.

En inmersivos, el medio principal de interacción es mirada y confirmación y punto y confirmación (con un [controlador de movimiento](motion-controllers.md)). Si el usuario tiene un auricular con capacidades de voz, voz puede usarse en combinación con la mirada o punto para completar una acción.

Durante el diseño de aplicaciones, debe considerar cómo puede hacer que estas interacciones funcione bien.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (con auriculares adjuntadas)</td>
</tr>
</table>



## <a name="how-to-use-voice"></a>Uso de voz

Considere la posibilidad de agregar los comandos de voz a cualquier experiencia que se compila. Voz es una manera eficaz y conveniente controlar el sistema y aplicaciones. Dado que los usuarios hablan con diversos dialectos y acentos, la opción adecuada de las palabras clave de voz se asegurará de que los comandos de los usuarios se interpretan de forma inequívoca.

### <a name="best-practices"></a>Procedimiento recomendado

A continuación se muestran algunas prácticas que le ayudará en el reconocimiento de voz suave.
* **Use comandos concisos** : cuando sea posible, elija las palabras clave de dos o más sílabas. Palabras uno Sílaba tienden a usar los sonidos vocal diferente cuando habla por personas de distintas acentos. Por ejemplo: "Reproducir vídeo" es mejor que "Reproducir el vídeo seleccionado actualmente"
* **Usar un vocabulario simple** -ejemplo: "Mostrar nota" es mejor que "Mostrar panel"
* **Asegúrese de que los comandos que no sean destructivos** : asegúrese de que cualquier acción que se puede realizar mediante un comando de voz es que no sean destructiva y fácilmente se pueden deshacer en caso de que otra persona que habla accidentalmente casi el usuario desencadena un comando.
* **Evite los comandos similares de sonido** -evitar registrar varios comandos de voz que suenan de forma muy parecidos. Por ejemplo: "Show store" y "Mostrar más" pueden ser muy similar sonido.
* **Anular el registro de la aplicación cuando no usa** : cuando la aplicación no está en un estado en que un comando de voz determinado es válido, considere la posibilidad de anular el registro de modo que otros comandos no se confundan para que uno.
* **Prueba con diferentes acentos** -probar la aplicación con usuarios de diferentes acentos.
* **Mantener la coherencia de comandos de voz** : si "Volver" irá a la página anterior, mantener este comportamiento en sus aplicaciones.
* **Evite el uso de comandos del sistema** -los siguientes comandos de voz están reservados para el sistema. No se recomienda por las aplicaciones.
   * "Hola Cortana"
   * "Select"

### <a name="what-users-can-say"></a>¿Qué pueden decir a los usuarios

Como un usuario tiene como destino cualquier botón a través de mirada o señalando, pueden indicar la palabra **"Select"** para activar ese botón. "Select" es una de las palabras clave de bajo consumo de energía que siempre se realizan escuchas. Si continúa, un usuario también puede usar "gramática del botón" todo el sistema o en las aplicaciones. Por ejemplo, al examinar una aplicación, un usuario puede decir el comando "Remove" (que se encuentra en la barra de la aplicación) para quitar la aplicación del mundo.

### <a name="see-it-say-it"></a>Verlo, por ejemplo

Windows Mixed Reality ha contratado a un modelo de voz "verlo, diga" donde **las etiquetas en los botones son idénticas a los comandos de voz asociado**. Porque no hay ningún dissonance entre la etiqueta y el comando de voz, los usuarios puedan comprender mejor qué decirles a controlar el sistema. Para esto, reforzar al alojamiento en un botón, un **"voz profundizaré sugerencia"** aparece para comunicar los botones son voz habilitada.

![Verlo, lo dirá el ejemplo 1](images/voice-seeitsayit1-640px.jpg)

![Verlo, lo dirá el ejemplo 2](images/voice-seeitsayit2-640px.jpg)<br>
*Ejemplos de "verlo, diga"*

### <a name="voices-strengths"></a>Puntos fuertes de voz

Entrada de voz es una manera natural para nuestras intenciones de comunicarse. Es especialmente buena interfaz voz **recorridos** porque puede ayudar a los usuarios Cortar a través de varios pasos de una interfaz (un usuario podría decir "volver" al buscar en la página Web, en lugar de tener que ir arriba y presione el botón Atrás en la aplicación). Este ahorro de tiempo de pequeño tiene un potente **efecto emocional** usuario la percepción de la experiencia y les da un introduzcan poco. Uso de voz también es un método práctico para entrada cuando se tienen nuestros brazos completas o son **multitarea**. En los dispositivos donde es difícil, escribir en un teclado **dictado de voz** puede ser una alternativa eficaz a la entrada. Por último, en algunos casos, cuando el **intervalo de precisión** mirada y gesto son limitados, voz podría ser un usuario solo de entrada del método de confianza.

**Cómo el uso de voz puede beneficiar el usuario**
* Reduce el tiempo: el objetivo final debe hacer más eficaz.
* Minimiza el esfuerzo - deben realizar las tareas más fluida y sin esfuerzo.
* Reduce la carga cognitive - es intuitiva y fácil de aprender y recordar.
* Es aceptable socialmente, es ideal con normas en términos de comportamiento.
* De la rutina - voz fácilmente puede convertirse en un comportamiento habitual.

### <a name="voices-weaknesses"></a>Puntos débiles de voz

Voz también tiene algunas desventajas. Un control más preciso es uno de ellos. (por ejemplo un usuario podría decir "hechos", pero no se puede decir cuánto. "Un poco" es difícil de cuantificar. Mover o la escala de las cosas con voz también es difícil (voz no ofrece la granularidad del control). También puede ser imperfecta la voz. A veces, un sistema de voz incorrectamente oye un comando o se produce un error al recibir un comando. Recuperarse de estos errores es un desafío en cualquier interfaz. Por último, voz puede no ser aceptable social en lugares públicos. Hay algunas cosas que los usuarios no pueden o no deberían decir. Estos cliffsnotes permiten voz que se usará para lo que lo que es mejor.

### <a name="voice-feedback-states"></a>Estados de comentarios de voz

Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtener comentarios claros** el sistema **oído hablar de ellos correctamente**. Estas dos señales de que el usuario sienta confiar más en voz como una entrada principal. A continuación es un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y comunicación que al usuario.

![Estados de comentarios de voz de cursor](images/voicefeedbackstates.png)<br>
*Estados de comentarios de voz de cursor*

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a>Los usuarios de las cosas superior deben conocer "voz" en Windows Mixed Reality
* Por ejemplo **"Select"** mientras selecciona como destino un botón (que puede utilizarlo desde cualquier lugar que hacer clic en un botón).
* Puede decir el **nombre de etiqueta de un botón de barra de la aplicación** en algunas aplicaciones para realizar una acción. Por ejemplo, al examinar una aplicación, un usuario puede indicar que el comando "Remove" para quitar la aplicación desde el mundo (Esto ahorra tiempo tener que hacer clic en él con la mano).
* Puede iniciar Cortana escucha diciendo: **"Hola Cortana".** Puede formular sus preguntas ("Hola Cortana, el alto es la torre Eiffel"), dígale que abrir una aplicación ("Hola Cortana, abra Netflix") o Dígale que aparezca el menú Inicio ("Hola Cortana, take me home") y mucho más.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Tengan usuarios preguntas e inquietudes comunes acerca de voz
* ¿Qué puedo decir?
* ¿Cómo se puede saber que el sistema me escuchó correctamente?
   * El sistema mantiene obtienen los comandos de voz incorrectas.
   * No reacciona cuando le asigno un comando de voz.
* La forma equivocada reacciona cuando le asigno un comando de voz.
* ¿El destino de mi voz a una aplicación específica o un comando de la aplicación?
* ¿Puedo usar detección de voz y el marco holográfica cosas comando en HoloLens?

## <a name="see-also"></a>Vea también
* [Gestos](gestures.md)
* [Mirada destinadas a](gaze-targeting.md)
