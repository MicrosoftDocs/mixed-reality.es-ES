---
title: Módulo lunar
description: LunarModule es una aplicación de ejemplo de código abierto de laboratorios de diseño de realidad mixta de Microsoft. Con este proyecto, puede aprender cómo ampliar los gestos en base con el seguimiento de manos de Hololens y mando de Xbox de entrada, crear objetos que se reactiva a asignación de superficie y buscar plano e implementar los sistemas de menú simple.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Ejemplo HoloLens de aplicaciones, diseño, la realidad mixta de Windows
ms.openlocfilehash: 38f70d78b5572930b874e221fa4a85572c07b342
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602487"
---
# <a name="lunar-module"></a>Módulo lunar

>[!NOTE]
>Este artículo describe un ejemplo de exploración que hemos creado en el [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde se comparten la información que recabemos sobre y sugerencias para mezclan el desarrollo de aplicaciones de realidad. Nuestros artículos relacionados con el diseño y código evolucionará a medida que introducimos nuevos descubrimientos.

[Módulo lunar](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) es una aplicación de ejemplo de código abierto de laboratorios de diseño de realidad mixta de Microsoft. Con este proyecto, puede aprender cómo ampliar los gestos en base con el seguimiento de manos de Hololens y mando de Xbox de entrada, crear objetos que se reactiva a asignación de superficie y buscar plano e implementar los sistemas de menú simple. Todos los componentes del proyecto están disponibles para su uso en sus propias experiencias de aplicaciones de realidad mixta.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Replanteamiento de experiencia clásica de Windows Mixed Reality

Alta seguridad en la atmósfera, un buque pequeño que recuerda a del módulo Apollo metódicamente encuestas escalonada terreno a continuación. Nuestro estudio piloto audaz topos un área de aterrizaje adecuado. El descenso es difícil, pero afortunadamente, este recorrido se ha realizado muchas veces...

![Interfaz original desde 1979 Lunar Lander del Atari](images/640px-atari-lunar-lander.png)<br>
*Interfaz original desde 1979 Lunar Lander del Atari*

[Lander lunar](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) es una clásica arcade donde los jugadores intentan piloto un lander luna en una zona sin formato del terreno lunar. Más probable es que cualquier persona nació en la década de 1970 ha pasado de horas en un arcade con sus ojos pegados buque vector impresionante desde el cielo. Como un reproductor navega hacia un área de aterrizaje que desee de su envío se escala el terreno para revelar progresivamente más detalles. Éxito significa aterrizaje dentro del umbral de velocidad horizontal y vertical seguro. Para el tiempo empleado de aterrizaje y restante de combustible, con un multiplicador en función del tamaño del área de aterrizaje se obtienen puntos.

Aparte de los juegos, la era de arcade de juegos pone constante innovación de esquemas de control. De las configuraciones de joystick y un botón de 4 vías más sencillas (visto en el icónico [Pac-Man](https://en.wikipedia.org/wiki/Pac-Man)) para los esquemas muy complicados y específicos se ven en los años 90 en tiempo de ejecución y 00s (como aquellos en los simuladores de golf y tiro al blanco carril). El esquema de entrada usado en la máquina Lander Lunar resulta especialmente interesante por dos motivos: criar atractivo de inmersión.

![Consola de Lander Lunar de Atari arcade](images/atariconsole.png)<br>
*Consola de Atari Lander Lunar arcade*

¿Por qué Atari y muchas otras compañías juego decide que replantear la entrada?

La máquina más reciente, flashiest naturalmente se intrigado a un niño recorriendo un arcade. Pero Lander Lunar características un mecánico entrado novedosas que destacaba entre la multitud.

Lander lunar usa dos botones para girar la nave izquierda y derecha y un **empuje palanca** para controlar la cantidad de empuje produce el envío. Esta palanca ofrece a los usuarios un cierto nivel de astucia que no puede proporcionar un joystick normal. También resulta ser un componente común para cabinas de aviación modernas. Atari quería Lunar Lander para que se sumerja el usuario la sensación de que estaba piloto en realidad un módulo lunar. Este concepto se conoce como **inmersión al tacto**.

Inmersión al tacto es la experiencia de comentarios sensorial realicen acciones repetitivas. En este caso, la acción repetitiva de ajuste de la palanca de limitación y la rotación que sus ojos los ven y escuche a nuestros oídos, ayuda a conectar el Reproductor a la acción de un barco de aterrizaje en la superficie de la luna. Este concepto se puede vincular al psicológico concepto de "flujo". Cuando un usuario totalmente absorbe en una tarea que tiene la combinación correcta de desafío y recompensa, o en términos más simples, que se encuentren "en"la zona.

Sin duda, el tipo más destacado de inmersión en realidad mixta es inmersión espacial. El objetivo de realidad mixta es engañar a nosotros para creer que estos objetos digitales existen en el mundo real. Hologramas nos estamos sintetiza en nuestro entorno, espacialmente usuario está inmerso en las experiencias y entornos completos. Esto no significa que no podemos seguiremos usando otros tipos de inmersión en nuestra experiencia al igual que hizo Atari al tacto inmersión en Lander Lunar.

## <a name="designing-with-immersion"></a>Diseño de inmersión

¿Cómo podríamos aplicar inmersión al tacto para una continuación actualizada y volumétrico el Atari clásico? Antes de comenzar con el esquema de entrada, la construcción de juegos para el espacio de 3 dimensiones debe solucionarse.

![Visualización de asignación de superficie en HoloLens](images/surfacemapping.png)<br>
*Visualización de asignación espacial en HoloLens*

Mediante el aprovechamiento de su entorno de un usuario, tenemos eficazmente opciones de terreno infinito de aterrizaje de nuestro módulo lunar. Para que el juego sea más parecido a la original título, un usuario potencialmente podría manipular y coloque los paneles de aterrizaje de dificultades diferentes en su entorno.

![Volar el módulo Lunar](images/640px-lm-hero.jpg)<br>
*Volar el módulo Lunar*

Solicitar al usuario que obtenga información sobre el esquema de entrada, controlar el envío y tiene un destino pequeños lleguen a es mucho pedir. Una experiencia de juego correcta de características la mezcla correcta de desafío y recompensa. El usuario debería poder elegir un nivel de dificultad, con el modo más fácil simplemente pedir al usuario que lleguen correctamente en un área definida por el usuario en una superficie analizados por el HoloLens. Una vez que un usuario obtiene la falta de respuesta del juego, puede, a continuación, suba la dificultad según lo consideren oportuno.

### <a name="adding-input-for-hand-gestures"></a>Adición de entrada para los gestos de mano

Entrada de base de HoloLens tiene solo dos movimientos - [Bloom y puntee en el aire](gestures.md). Los usuarios no necesitan recordar matices contextuales o confeccionar una lista de los gestos específicos que hace que la interfaz de la plataforma versátil y fácil de aprender. Mientras el sistema solo puede exponer estos gestos de dos, HoloLens, como un dispositivo es capaz de seguimiento dos manos a la vez. Es nuestro ode a Lunar Lander una [aplicaciones envolventes](app-model.md) lo que significa que tenemos la capacidad de ampliar el conjunto de gestos para aprovechar dos manos y agregar nuestra propia significa perfectamente al tacto para la navegación de módulo lunar base.

Si volvemos a la combinación de control original, **teníamos que resolver de empuje y giro**. La advertencia es la rotación en el nuevo contexto agrega un eje adicional (técnicamente dos, pero es menos importante para el inicio del eje Y). Los dos movimientos de envío distintos naturalmente se prestan a asignarse a cada lado:

![Pulse y arrastre el gesto para girar lander en los tres ejes](images/module-handdrag.gif)<br>
*Pulse y arrastre el gesto para girar lander en los tres ejes*

**Incursión**

La palanca de la máquina de arcade original asignada a una escala de valores, mayor será la palanca se ha movido se aplicó el empuje más para el envío. Cabe destacar aquí es el usuario puede tomar su mano fuera del control y mantener un valor deseado. Podemos usar eficazmente el comportamiento de tap y arrastre para lograr el mismo resultado. El valor de empuje comienza en cero. El usuario pulsa y arrastra para aumentar el valor. En ese momento podría suéltela para mantenerlo. Cualquier cambio del valor de gesto de tap y arrastre sería el delta del valor original.

**Rotación**

Esto es un poco más complicado. Tener holográficas botones "girar" pulsar facilita una experiencia terrible. No hay un control físico aprovechar, por lo que el comportamiento debe proceder de manipulación de un objeto que representa el lander, o con el lander propio. Habíamos llegado a un método de tap y arrastrar que permite que un usuario eficazmente "inserción y extracción" en la dirección desean que se enfrentan. Siempre que un usuario toca y mantiene presionado, el punto en el espacio donde se inició el gesto se convierte en el origen de la rotación. Arrastrar desde el origen convierte el delta de traducción de la mano (X, Y, Z) y aplica a las diferencias entre los valores de rotación del lander. O, sencillamente, *arrastrar izquierda <> – derecha, arriba <> – hacia abajo, hacia delante <> – en espacios gira en consecuencia la nave*.

Puesto que la HoloLens pueden realizar un seguimiento de los dos manos, rotación puede asignarse a la derecha mientras empuje está controlado por la izquierda. Astucia es un factor determinante para lograr el éxito en este juego. El *sentir* de estas interacciones es la máxima prioridad absoluta. Especialmente en el contexto de inmersión al tacto. Un barco que reaccione demasiado rápido sería innecesariamente difícil dirigir, mientras que uno demasiado lento requieren que el usuario "inserción y extracción" en el envío para un período de tiempo con desmaña largo.

### <a name="adding-input-for-game-controllers"></a>Agregar entrada de juego

Aunque los gestos de mano en la HoloLens proporcionan un método novedoso de un control pormenorizado, sigue siendo falta 'true' comentarios al tacto que obtendrá de controles analógicos. Conectar un dispositivo de juego Xbox permite para devolver esta idea de physicality aprovechando el control se adhiere para mantener el control minucioso.

Hay varias formas de aplicar el esquema de control relativamente sencilla para el controlador de Xbox. Puesto que estamos tratando de mantenerse lo más cerca de la original arcade configurado como sea posible, **empuje** mejor se asigna al botón de desencadenador. Estos botones son controles analógicos, lo que significa que tienen más que un simple *activar y desactivar* indica, realmente responden al grado de presión sobre ellos. Esto nos da una construcción similar como la **empuje palanca**. A diferencia del juego original y el gesto de mano, este control cortará empuje del envío una vez que un usuario deja de hacer presión sobre el desencadenador. También ofrece al usuario el mismo grado de astucia como hacía el juego arcade original.

![Tecla de navegación izquierda está asignado para la guiñada y revertir, tecla de navegación derecha se asigna para revertir y tono](images/thumbsticksidebyside.gif)<br>
*Tecla de navegación izquierda está asignado para la guiñada y revierta; tecla de navegación derecha está asignado para revertir y tono*

El sticks analógicos duales naturalmente se prestan a control de envío de rotación. Desafortunadamente, hay 3 ejes en que se puede girar el envío y dos sticks analógicos que admiten dos ejes. Esta falta de coincidencia, significa que ya sea una tecla de navegación controles un eje; o bien hay superposición de los ejes para el sticks analógicos. La primera solución terminé se siente "roto" puesto que sticks analógicos inherentemente blend su local valores X e Y. La última solución requiere algunas pruebas para encontrar qué ejes redundantes sienten más natural. El último ejemplo se usa *guiñada* y *poner* (los ejes X e Y) para la tecla de navegación izquierda, y *pitch* y *poner* (ejes Z y X) de la derecha tecla de navegación. Esto sentí natural como *poner* parece de forma independiente se combinan bien con *guiñada* y *pitch*. Como una nota al margen, usando tanto sticks analógicos para *poner* también ocurre al doble del valor de rotación; es bastante divertido para tener la lander "do loops".

Esta aplicación de ejemplo muestra cómo espacial reconocimiento y al tacto inmersión puede cambiar considerablemente una experiencia gracias a modalidades de entrada extensibles de realidad mixta de Windows. A pesar de que Lander Lunar puede ser casi 40 años de edad, los conceptos exponen con que se encontrarán poco octágono con piernas indefinidamente. Cuando uno se imagina el futuro, ¿por qué no consultar en el pasado?

## <a name="technical-details"></a>Detalles técnicos

Puede encontrar prefabricados y secuencias de comandos para la aplicación de ejemplo de módulo Lunar en el [GitHub de laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Diseñador UX @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Controladores de movimiento](motion-controllers.md)
* [Gestos](gestures.md)
* [Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)
