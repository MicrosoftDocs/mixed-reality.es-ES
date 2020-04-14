---
title: Entrada de voz
description: La entrada de voz es una entrada básica para los auriculares de la realidad de HoloLens y Windows Mixed Reality. Voice se puede usar para comandos, dictado, Cortana y mucho más.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, voz, Cortana, voz, entrada
ms.openlocfilehash: 6cf94e6bc828c6f07ee81cb121cb64601df41c4e
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277983"
---
# <a name="voice-input"></a>Entrada de voz

![Entrada de voz](images/UX/UX_Hero_VoiceCommand.jpg)

La voz es una de las formas clave de entrada en HoloLens. Permite comandos directamente de un holograma sin tener que usar [gestos de mano](gaze-and-commit.md#composite-gestures). La entrada de voz es una manera natural de comunicar tus intenciones. La voz es especialmente adecuada en el recorrido de interfaces complejas, ya que permite a los usuarios cortar menús anidados con un comando.

La entrada de voz se basa en el [mismo motor](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) que admite la voz en todas las demás _aplicaciones universales de Windows_. En HoloLens, el reconocimiento de voz siempre funcionará en el idioma de visualización de Windows configurado en configuración. 

<br>

## <a name="voice-and-gaze"></a>Voz y miras

Cuando se usan comandos de voz, se usa normalmente (encabezado o ojo) para hacer clic en el mecanismo de destino, ya sea con un cursor ("Select") o para canalizar implícitamente el comando a una aplicación que se está viendo. En este caso, es posible que no sea necesario que muestre ningún cursor de miras _("verlo, decirlo")_ . Por supuesto, algunos comandos de voz no requieren un destino, como "ir a Inicio" o "Hola Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


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
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con micrófono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Comando "seleccionar"

**HoloLens (1ª generación)**

Incluso sin agregar específicamente compatibilidad con voz a su aplicación, los usuarios pueden activar los hologramas simplemente diciendo el comando de voz del sistema "Select". Esto se comporta igual que una [pulsación aérea](gaze-and-commit.md#composite-gestures) en HoloLens, presionando el botón seleccionar en el [clic de hololens](hardware-accessories.md#hololens-clicker)o presionando el desencadenador en un controlador de [movimiento de Windows Mixed Reality](motion-controllers.md). Oirá un sonido y verá que aparece una información sobre herramientas con "seleccionar" como confirmación. "Select" está habilitado por un algoritmo de detección de palabras clave de baja energía, por lo que siempre está disponible para que lo indique en cualquier momento con un impacto mínimo en la duración de la batería, incluso con sus manos en el lateral.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Para usar el comando "seleccionar" de voz en HoloLens 2, primero debe abrir el cursor de miración para usarlo como puntero. El comando para ponerlo al día es fácil de recordar (simplemente, por ejemplo, "Select").<br><br>
        Para salir del modo, simplemente vuelva a usar las manos, ya sea mediante el toque de aire, cerca de un botón con los dedos o usando el gesto del sistema.<br>
        <br>
        *Imagen: "seleccionar" para usar el comando de voz para la selección*
    :::column-end:::
        :::column:::
       ![Un usuario puede decir "seleccionar" para usar el comando de voz para una selección.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>Hola Cortana

También puede decir "Hola Cortana" para abrir Cortana en cualquier momento. No tiene que esperar a que parezca que siga preguntando a su pregunta o le dé una instrucción; por ejemplo, intente decir "Hola Cortana, ¿cuál es el tiempo?". como una sola oración. Para obtener más información sobre Cortana y lo que puede hacer, simplemente pregúntele. Por ejemplo, "Hola Cortana, ¿qué puedo decir?" y desplegarán una lista de comandos de trabajo y sugeridos. Si ya está **en la aplicación** de Cortana, también puede hacer clic en el en la barra lateral para desplegar el mismo menú.

**Comandos específicos de HoloLens**
* "¿Qué puedo decir?"
* "Ir a Inicio"-en lugar de a la [floración](system-gesture.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Iniciar <app>"
* "Mueva <app> aquí"
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



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"Verlo, decirlo"<br>
        HoloLens tiene un modelo "ver ti" para la entrada de voz, donde las etiquetas de los botones indican a los usuarios los comandos de voz que también pueden decir. Por ejemplo, al examinar una ventana de la aplicación en HoloLens (1ª generación), un usuario puede decir el comando "ajustar" que se ve en la barra de la aplicación para ajustar la posición de la aplicación en el mundo.<br>
        <br>
        *Imagen: un usuario puede decir el comando "ajustar" que ve en la barra de la aplicación para ajustar la posición de la aplicación*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
        ![al mirar una ventana de la aplicación o un holograma, un usuario puede decir el comando "ajustar" que aparecen en la barra de la aplicación para ajustar la posición de la aplicación en el mundo](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        Cuando las aplicaciones siguen esta regla, los usuarios pueden comprender fácilmente qué decir para controlar el sistema. Para reforzar esto, mientras Gazing en un botón de HoloLens (1ª generación), verá una información sobre herramientas de "permanencia de voz" que aparece después de un segundo si el botón está habilitado para voz y muestra el comando para hablar de ella. Para mostrar la información sobre herramientas de voz en HoloLens 2, muestre el cursor de voz indicando "seleccionar" o "Qué puedo decir" (vea la imagen). <br>
        <br>
        *Imagen: "ver, por ejemplo," los comandos aparecen debajo de los botones*
    :::column-end:::
        :::column:::
       ![Verlo, por ejemplo, los comandos aparecen debajo de los botones](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para la manipulación rápida de hologramas

Hay una serie de comandos de voz que puede decir mientras Gazing en un holograma para realizar rápidamente tareas de manipulación. Estos comandos de voz funcionan en las ventanas de la aplicación, así como en los objetos 3D que ha colocado en el mundo.

**Comandos de manipulación de hologramas**
* Me encuentro
* Mayor | Enhance
* Disminuye

En HoloLens 2, también puede crear interacciones más naturales en combinación con la mirada, lo que proporciona implícitamente información contextual sobre lo que se está haciendo referencia. Por ejemplo, podría simplemente mirar un holograma y decir "colocarlo" y, a continuación, buscar _el_lugar en el que desea colocarlo y decir " _aquí_".
O bien, podría ver una pieza holográfica en una máquina compleja y decir: "proporcione más información acerca de _esto_".



## <a name="discovering-voice-commands"></a>Detección de comandos de voz

Algunos comandos, como los comandos para la manipulación rápida anterior, se pueden ocultar. Para obtener información sobre los comandos que puede usar, mira fijamente a un objeto y, por ejemplo, "¿Qué puedo decir?". Aparece una lista de posibles comandos. También puede usar el cursor de mirar hacia abajo para buscar y mostrar la información sobre herramientas de voz de cada botón delante. 

Si desea una lista completa, simplemente indique "Mostrar todos los comandos" en cualquier momento. 


## <a name="dictation"></a>Dictado

En lugar de escribir con [grifos de aire](gaze-and-commit.md#composite-gestures), el dictado de voz puede ser más eficaz para escribir texto en una aplicación. Esto puede acelerar en gran medida la entrada con menos esfuerzo para el usuario.

![dictado de voz comienza seleccionando el botón micrófono](images/micbuttonfordictation.png)<br>
*El dictado de voz comienza seleccionando el botón micrófono del teclado.*

Siempre que el teclado Holographic esté activo, puede cambiar al modo de dictado en lugar de escribir. Seleccione el micrófono en el lateral del cuadro de entrada de texto para comenzar.


## <a name="adding-voice-commands-to-your-app"></a>Agregar comandos de voz a la aplicación

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
   * "Ir a Inicio"

### <a name="advantages-of-voice-input"></a>Ventajas de la entrada de voz

Las entradas de voz son una manera natural de comunicar nuestras intenciones. La voz es especialmente útil en los recorridos de la interfaz, ya que puede ayudar a los usuarios a **resaltar** varios pasos de una interfaz (un usuario podría decir "volver atrás" mientras mira una página web, en lugar de tener que subir y presionar el botón atrás en la aplicación). Esta pequeña hora de guardar tiene un **efecto emocional** eficaz sobre la percepción del usuario de la experiencia y les da una pequeña cantidad de mejorar enormemente. El uso de la voz es también un método práctico de entrada cuando tenemos las manos ocupadas o estamos **realizando varias tareas a la vez**. En los dispositivos en los que es difícil escribir en un teclado, el **dictado de voz** puede ser una forma alternativa eficaz de escribir texto. Por último, en algunos casos en los que el **intervalo de precisión** de la mirada y el gesto es limitado, la voz puede ayudar a eliminar la ambigüedad de la intención del usuario. 

**Cómo puede beneficiar al usuario la utilización de la voz**
* Reduce el tiempo: debe hacer que el objetivo final sea más eficaz.
* Minimiza el esfuerzo: debe hacer que las tareas se realicen de forma más fluida y sin esfuerzo.
* Reduce la carga cognitiva: es una forma intuitiva y fácil de aprender y recordar.
* Es aceptable socialmente: se adapta a las normas sociales en términos de comportamiento.
* Es fácil de convertir en rutina: puede convertirse fácilmente en un comportamiento habitual.

### <a name="challenges-for-voice-input"></a>Desafíos de la entrada de voz

Aunque la entrada de voz es excelente para muchas aplicaciones diferentes, también enfrenta varios desafíos. La comprensión de las ventajas y los desafíos de la entrada de voz permite a los desarrolladores de aplicaciones tomar decisiones más inteligentes sobre cómo y Cuándo usar la entrada de voz y crear una excelente experiencia para los usuarios.

**Entrada de voz para el control de entrada continuo** El control específico es uno de ellos. Por ejemplo, un usuario podría querer cambiar su volumen en su aplicación de música. Puede simplemente decir "más alto", pero no está claro cuánto se supone que el sistema hace el volumen. El usuario podría decir: "hacer que sea un poco más alto", pero "un poco" es difícil de cuantificar. El movimiento o el escalado de los hologramas con la voz es igualmente difícil. 

**Confiabilidad de la detección de entrada de voz** Aunque los sistemas de entrada de voz son mejores y mejores, a veces pueden oír e interpretar de forma incorrecta un comando de voz.
La clave es abordar este desafío en la aplicación proporcionando comentarios al usuario cuando el sistema está escuchando y lo que el sistema entendió para crear claridad sobre los posibles problemas al comprender correctamente el usuario.  

**Entrada de voz en espacios compartidos** Es posible que la voz no sea socialmente aceptable en espacios que comparta con otros usuarios.
Estos son algunos ejemplos:
* Es posible que el usuario no quiera molestar a otros (por ejemplo, en una biblioteca tranquila o en una oficina compartida).
* Es posible que los usuarios no se vean tan complicados como hablar en el público.
* Un usuario puede sentirse incómodo dictar un mensaje personal o confidencial (incluidas las contraseñas) mientras que otros están escuchando

**Entrada de voz de palabras únicas o desconocidas** Las dificultades para la entrada de voz también se muestran cuando los usuarios están dictando palabras que pueden ser desconocidas para el sistema, como sobrenombres, determinadas palabras o abreviaturas de jergas. 

**Comandos de voz de aprendizaje** Aunque el objetivo final es conversar naturalmente con el sistema, a menudo las aplicaciones siguen confiando en comandos de voz específicos predefinidos.
Un desafío asociado a un gran conjunto de comandos de voz es cómo enseñarlas sin sobrecargar al usuario y cómo ayudar al usuario a conservarlas. 

<br>

---

### <a name="voice-feedback-states"></a>Estados de la respuesta a la voz

Cuando la voz se aplica correctamente, el usuario entiende **lo que puede decir y obtiene una respuesta clara** de que el sistema **le ha oído correctamente**. Estas dos señales hacen que el usuario se sienta seguro utilizando la voz como entrada principal. A continuación se muestra un diagrama que muestra lo que sucede con el cursor cuando se reconoce la entrada de voz y cómo se lo comunica al usuario.


:::row:::
    :::column:::
       ![1. Estado normal del cursor](images/voicefeedbackstates-regular.jpg)<br>
       **1. estado normal del cursor**<br>
    :::column-end:::
    :::column:::
       ![2. Comunica los comentarios de voz y, a continuación, desaparece](images/voicefeedbackstates-voice.jpg)<br>
        **2. comunica comentarios de voz y luego desaparece**<br>
    :::column-end:::
    :::column:::
       ![* 3. Estado normal del cursor](images/voicefeedbackstates-regular.jpg)<br>
       **3. vuelve al estado normal del cursor**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

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

## <a name="communication"></a>Comunicación

En el caso de las aplicaciones que desean aprovechar las opciones de procesamiento de entrada de audio personalizadas proporcionadas por HoloLens, es importante comprender las distintas [categorías de flujo de audio](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) que puede consumir la aplicación. Windows 10 admite varias categorías de secuencias diferentes y HoloLens usa tres de ellas para habilitar el procesamiento personalizado con el fin de optimizar la calidad de audio del micrófono adaptada a la voz, la comunicación y otras que se pueden usar para escenarios de captura de audio de entorno ambiente (es decir, "videocámara").
* La categoría AudioCategory_Communications Stream está personalizada para escenarios de calidad y narración de llamadas y proporciona al cliente una secuencia de audio mono 16kHz 24bit de la voz del usuario
* La categoría AudioCategory_Speech Stream está personalizada para el motor de voz de HoloLens (Windows) y le proporciona una secuencia de 16kHz 24bit mono de la voz del usuario. Los motores de voz de terceros pueden usar esta categoría si es necesario.
* La categoría AudioCategory_Other Stream está personalizada para la grabación de audio del entorno ambiente y proporciona al cliente una secuencia de audio estéreo de 24 bits de 48 bits.

Todo este procesamiento de audio se acelera en hardware, lo que significa que las características agotan una gran cantidad de energía que si se realizara el mismo procesamiento en la CPU de HoloLens. Evite ejecutar otro procesamiento de entrada de audio en la CPU para maximizar la duración de la batería del sistema y aprovechar el procesamiento de entrada de audio descargado integrado.

## <a name="languages"></a>Lenguajes

HoloLens 2 también admite idiomas adicionales. Tenga en cuenta que los comandos de voz siempre se ejecutarán en el idioma para mostrar del sistema aunque se instalen varios teclados o cuando las aplicaciones intenten crear un reconocedor de voz en otro idioma.

## <a name="troubleshooting"></a>Solucionar problemas

Si tiene algún problema con "Select" y "Hola Cortana", intente cambiar a un espacio más silencioso, desplazarse fuera del origen del ruido o hablar de más alto. En este momento, todo el reconocimiento de voz en HoloLens se ajusta y optimiza específicamente a los hablantes nativos de Estados Unidos inglés.

En el caso de la versión 2017 de Windows Mixed Reality Developer Edition, la lógica de administración de puntos de conexión de audio funcionará bien (siempre) después de cerrar la sesión y volver a iniciarla en el escritorio del equipo después de la conexión inicial de HMD. Antes de ese primer evento de cierre de sesión/en el momento de pasar a través de WMR OOBE, el usuario podría experimentar varios problemas de funcionalidad de audio que van desde sin audio hasta sin conmutación de audio, en función de cómo se haya configurado el sistema antes de conectarse a HMD por primera vez.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Entrada de voz en MRTK (kit de herramientas de realidad mixta) para Unity
Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede asignar fácilmente comandos de voz en cualquier objeto. Use el **Perfil de entrada de voz** de MRTK para definir sus palabras clave. Mediante la asignación del script **SpeechInputHandler** , puede hacer que cualquier objeto responda a las palabras clave definidas en el perfil de entrada de voz. SpeechInputHandler también proporciona una etiqueta de confirmación de voz para mejorar la confianza del usuario.

* [Comando MRTK-Voice](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>Vea también
* [Mirada y confirmación](gaze-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada MR 212: voz](holograms-212.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Entrada de voz en Unity](voice-input-in-unity.md)
