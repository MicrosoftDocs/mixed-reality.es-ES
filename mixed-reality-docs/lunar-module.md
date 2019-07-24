---
title: Módulo lunar
description: LunarModule es una aplicación de ejemplo de código abierto de laboratorios de diseño de la realidad mixta de Microsoft. Con este proyecto, puede obtener información sobre cómo ampliar los gestos base de Hololens con seguimiento de dos manos y entrada de la controladora Xbox, crear objetos reactivos para la asignación de superficie y la búsqueda de planos e implementar sistemas de menús sencillos.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicaciones de ejemplo, diseño, HoloLens
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516036"
---
# <a name="lunar-module"></a>Módulo lunar

>[!NOTE]
>En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta. Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.

El [módulo lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft. Con este proyecto, puede obtener información sobre cómo ampliar los gestos base de Hololens con seguimiento de dos manos y entrada de la controladora Xbox, crear objetos reactivos para la asignación de superficie y la búsqueda de planos e implementar sistemas de menús sencillos. Todos los componentes del proyecto están disponibles para su uso en sus propias experiencias de aplicación de realidad mixta.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Recreo experiencias clásicas para Windows Mixed Reality

En un nivel superior en la atmósfera, una pequeña recuerda a de envío del módulo Apollo realiza encuestas de forma escalonada a continuación. Nuestro piloto de Fearless tiene un área de aterrizaje adecuada. El descenso es arduo, pero afortunadamente, este viaje se ha realizado muchas veces antes...

![Interfaz original del Lander lunar 1979 de Atari](images/640px-atari-lunar-lander.png)<br>
*Interfaz original del Lander lunar 1979 de Atari*

[Luna Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) es un clásico arcade en el que los jugadores intentan realizar un piloto de una Luna Lander en una zona plana del terreno lunar. Cualquier persona nacida en la década tiene más probabilidades de gastar horas en un arcade con sus ojos pegados a este vector de envío plummeting del cielo. A medida que un jugador navega hacia un área de aterrizaje deseada, el terreno se escala para mostrar progresivamente más detalles. Success significa aterrizaje en el umbral seguro de velocidad horizontal y vertical. Se conceden puntos para el aterrizaje invertido y el combustible restante, con un multiplicador basado en el tamaño del área de aterrizaje.

Aparte del juego, la era de arcade de los juegos llevó una innovación constante de los esquemas de control. De las configuraciones de los botones y del joystick de 4 vías más sencillos (que se muestran en el icono de iconos de [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) a los esquemas muy específicos e complicados que se han detectado en las últimas 90s y 00s (por ejemplo, en simuladores de golf y disparos de carril). El esquema de entrada que se usa en el equipo Lander lunar es especialmente interesante por dos motivos: frenar la apelación e inmersión.

![Consola de Arcade del Lander lunar de Atari](images/atariconsole.png)<br>
*Consola de Lander Arcade lunar de Atari*

¿Por qué Atari y muchas otras empresas de juegos deciden reconsiderar la entrada?

El equipo flashiest más reciente le informará de un niño a través de un arcade. Pero lunar Lander incluye un mecánico de entrada de una novela que se ha extraído de la multitud.

Lander lunar usa dos botones para rotar el envío a la izquierda y a la derecha, y una **palanca de empuje** para controlar la cantidad de empuje que produce el envío. Esta palanca proporciona a los usuarios un nivel determinado de fines de fin que un joystick normal no puede proporcionar. También es un componente común a las cabinas de aviación modernas. Atari querían lunar Lander para sumergir al usuario en la sensación de que en realidad produjeron un módulo lunar. Este concepto se conoce como **inmersión táctil**.

La inmersión en el tacto es la experiencia de los comentarios organolépticos de realizar las acciones de redundante resulta. En este caso, la acción repetitiva de ajustar la palanca y la rotación del acelerador que ven nuestros ojos y nuestros oídos oyen le ayuda a conectar el jugador al acto de aterrizaje en la superficie de la luna. Este concepto puede estar vinculado al concepto psicológico de "Flow". En los casos en los que un usuario se absorbe por completo en una tarea que tiene la combinación adecuada de desafío y recompensa, o se coloca más simplemente, es "en la zona".

Posiblemente, el tipo más destacado de inmersión en la realidad mixta es la inmersión espacial. El punto entero de la realidad mixta es engañar a estos objetos digitales en el mundo real. Estamos sintetizando los hologramas en nuestro entorno y se ha sumergido espacialmente en los entornos y experiencias completos. Esto no significa que no podamos seguir empleando otros tipos de inmersión en nuestras experiencias tal y como Atari hacía con la inmersión táctil en Lander lunar.

## <a name="designing-with-immersion"></a>Diseño con inmersión

¿Cómo se puede aplicar la inmersión táctil a un seguido volumétrico actualizado al clásico de Atari? Antes de abordar el esquema de entrada, es necesario solucionar la construcción del juego para el espacio de tres dimensiones.

![Visualización de la asignación de superficie en HoloLens](images/surfacemapping.png)<br>
*Visualización de la asignación espacial en HoloLens*

Aprovechando el entorno de un usuario, de hecho tenemos opciones infinitas de terreno para desembarcar el módulo lunar. Para que el juego sea más parecido al título original, un usuario podría manipular y colocar los paneles de aterrizaje de distintas dificultades en su entorno.

![Volar en el módulo lunar](images/640px-lm-hero.jpg)<br>
*Volar en el módulo lunar*

Solicitar al usuario que obtenga información sobre el esquema de entrada, controle el envío y haga que un pequeño objetivo de la tierra sea una gran cantidad de preguntas. Una experiencia de juego correcta presenta la combinación correcta de desafío y recompensa. El usuario debe ser capaz de elegir un nivel de dificultad, con el modo más sencillo, simplemente requiriendo que el usuario se desembarque correctamente en un área definida por el usuario en una superficie examinada por HoloLens. Una vez que un usuario recibe el bloqueo del juego, puede arrancar la dificultad tal como se ve.

### <a name="adding-input-for-hand-gestures"></a>Agregar entradas para gestos de mano

La entrada base de HoloLens solo tiene dos gestos: [TAP y floración del aire](gestures.md). Los usuarios no necesitan recordar matices contextuales o una lista de los gestos específicos, lo que hace que la interfaz de la plataforma sea versátil y fácil de aprender. Aunque el sistema solo puede exponer estos dos gestos, HoloLens como dispositivo es capaz de hacer un seguimiento de dos manos a la vez. Nuestra node a lunar Lander es una [aplicación](app-model.md) envolvente, lo que significa que tenemos la capacidad de ampliar el conjunto básico de gestos para aprovechar dos manos y agregar nuestros propios medios táctiles y agradables para la navegación del módulo lunar.

Volviendo al esquema de control original, **necesitábamos resolver para la empuje y la rotación**. La advertencia es que la rotación en el nuevo contexto agrega un eje adicional (técnicamente dos, pero el eje Y es menos importante para el aterrizaje). Los dos movimientos de envío distintos se prestan de forma natural a ser asignados a cada mano:

![Toque y arrastre el gesto para girar Lander en los tres ejes](images/module-handdrag.gif)<br>
*Toque y arrastre el gesto para girar Lander en los tres ejes*

**Con**

La palanca en el equipo arcade original asignada a una escala de valores. cuanto mayor sea la palanca, más se aplicará el aumento al envío. Un aspecto importante que cabe señalar aquí es que el usuario puede desechar su mano del control y mantener un valor deseado. Podemos usar el comportamiento de puntear y arrastrar de manera eficaz para lograr el mismo resultado. El valor de empuje comienza en cero. El usuario puntea y arrastra para aumentar el valor. En ese momento, podrían dejar de mantenerse. Cualquier cambio de valor de gesto de pulsar y arrastrar sería el delta del valor original.

**Rotación**

Esto es un poco más complicado. La presencia de los botones de "girar" de Holographic es una experiencia muy terrible. No hay un control físico para aprovechar, por lo que el comportamiento debe proponerse de la manipulación de un objeto que represente el Lander o con el propio Lander. Nos hemos incorporado un método con la función de pulsar y arrastrar que permite a un usuario "Insertar y extraer" de manera eficaz en la dirección en la que desea que se enfrente. Cada vez que un usuario pulsa y mantiene, el punto en el espacio en el que se inició el gesto se convierte en el origen de la rotación. Al arrastrar desde el origen se convierte la diferencia de la traslación de la mano (X, Y, Z) y se aplica a la diferencia de los valores de rotación del Lander. O más simplemente, al *arrastrar hacia la izquierda <-> derecha, hacia arriba < > hacia abajo, hacia delante <-> en espacios se gira el buque en consecuencia*.

Dado que HoloLens puede realizar un seguimiento de dos manos, el giro se puede asignar a la mano derecha mientras el empuje está controlado por la izquierda. Fines de proceso es el factor que motiva el éxito en este juego. La *sensación* de estas interacciones es la prioridad máxima absoluta. Especialmente en el contexto de inmersión táctil. Un envío que reacciona demasiado rápido sería difícil de dirigir, mientras que uno demasiado lento requeriría que el usuario "insertara y extraer" en el buque durante un período de tiempo bastante largo.

### <a name="adding-input-for-game-controllers"></a>Agregar entradas para dispositivos de juego

Aunque los gestos de mano de HoloLens proporcionan un método de control minucioso, todavía hay cierta falta de comentarios táctiles "verdaderos" que se obtienen de los controles analógicos. La conexión de un dispositivo de juego de Xbox permite devolver este sentido de la física al tiempo que se aprovechan los controles para mantener un control minucioso.

Hay varias maneras de aplicar el esquema de control relativamente sencillo al controlador Xbox. Dado que estamos intentando permanecer lo más cerca posible de la configuración de Arcade **original, el** ajuste de los mapas es idóneo para el botón desencadenador. Estos botones son controles analógicos, lo que significa que tienen más de un estado *activado y* desactivado, y realmente responden al grado de presión que se les ha puesto en ellos. Esto nos da una construcción similar a la **palanca de empuje**. A diferencia del juego original y el gesto de mano, este control cortará el empuje del buque una vez que el usuario deje de poner presión en el desencadenador. Además, proporciona al usuario el mismo grado de fines de tiempo que tenía el juego de arcade original.

![El stick izquierdo se asigna a la guiñada y a la vuelta, el stick derecho se asigna al paso y al lanzamiento](images/thumbsticksidebyside.gif)<br>
*El stick izquierdo se asigna a guiñada y a rollo. el stick analógico derecho está asignado al paso y al lanzamiento*

La thumbsticks dual se presta en el control de la rotación del buque de forma natural. Desafortunadamente, hay 3 ejes en los que el envío puede girar y dos thumbsticks que ambos admiten dos ejes. Esta falta de coincidencia significa que un stick analógico controla un eje; o hay una superposición de los ejes para el thumbsticks. La solución anterior terminó de sentirse "rota", ya que thumbsticks combina de forma inherente sus valores X e y locales. La última solución requirió algunas pruebas para encontrar qué ejes redundantes sienten lo más natural. En el ejemplo final  se usan guiñada y *Roll* (ejes y y x) para el stick analógico izquierdo y el *paso* y el *rollo* (ejes Z y x) para el stick analógico derecho. En este aspecto, lo más natural es que el *rollo* parezca emparejarse de forma independiente con *guiñada* y el *paso*. Como nota al margen, el uso de thumbsticks para *Roll* también produce el doble del valor de rotación; es bastante divertido tener los bucles do Lander.

En esta aplicación de ejemplo se muestra cómo el reconocimiento espacial y el inmersión táctil pueden cambiar significativamente una experiencia gracias a las modalidades de entrada extensibles de Windows Mixed Reality. Aunque los Lander lunares pueden estar próximos a 40 años de edad, los conceptos que se exponen con ese poco octágono con tramos se activan en todo momento. Al imaginarse el futuro, ¿por qué no mirar el pasado?

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar scripts y Prefabs para la aplicación de ejemplo del módulo lunar en el laboratorio de diseño de la [realidad mixta de github](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Diseñador de la experiencia del usuario@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Controladores de movimiento](motion-controllers.md)
* [Gestos](gestures.md)
* [Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)
