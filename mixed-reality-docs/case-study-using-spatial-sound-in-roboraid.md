---
title: 'Caso práctico: uso de sonido espacial en RoboRaid'
description: El sonido espacial es una de las características más emocionantes de Microsoft HoloLens, lo que proporciona a los usuarios una forma de percibir qué está ocurriendo en torno a los objetos fuera de la línea de visión.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, sonido espacial
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524154"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Caso práctico: uso de sonido espacial en RoboRaid

Charles Sinex, responsable de audio en el equipo de experiencia de Microsoft HoloLens, habla sobre los desafíos únicos que encontró al crear audio para [RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j), un shootje de primera persona de realidad mixta.

## <a name="the-tech"></a>La tecnología

El [sonido espacial](spatial-sound.md) es una de las características más emocionantes de Microsoft HoloLens, lo que proporciona a los usuarios una forma de percibir qué está ocurriendo en torno a los objetos fuera de la línea de visión.

En RoboRaid, el uso más obvio y eficaz del sonido espacial consiste en avisar al jugador sobre algo que ocurre fuera de la visión del periférico del usuario. Por ejemplo, el violador puede entrar en cualquiera de las paredes digitalizadas de la habitación, pero si no se encuentra en la ubicación en la que está escribiendo, puede que se lo pierda. Para avisarle de esta invasión, oirá un poco de audio procedente del punto en el que entra el incumplimiento, lo que le permite saber que debe actuar rápidamente para detenerlo.

## <a name="behind-the-scenes"></a>En segundo plano

El proceso de creación de sonido espacial para las aplicaciones de HoloLens es tan nuevo y único, y la falta de los proyectos anteriores que se van a usar como referencia puede conducir a una gran cantidad de arañazos principales cuando surge un problema. Afortunadamente, estos ejemplos de los desafíos de audio que nos enfrentamos al hacer RoboRaid le ayudarán a crear audio para sus propias aplicaciones.

### <a name="be-mindful-of-taxing-the-cpu"></a>Tenga en cuentan el uso de la CPU

El sonido espacial puede ser exigente en la CPU. En el caso de una experiencia de uso como RoboRaid era fundamental mantener las instancias de sonido espacial en menos de ocho en un momento dado. En su mayor parte, era tan sencillo como establecer el límite de instancias de distintos eventos de audio para que se eliminen todas las instancias que se producen después del límite. Por ejemplo, cuando se genera drones, sus Screams se limitan a tres instancias en un momento dado. Considerar solo cuatro drones se puede generar a la vez, hay tres screamss, ya que no hay forma de que su cerebro pueda realizar un seguimiento de los muchos eventos de audio de sonido similar. Esto liberó recursos para otros eventos de sonido espacial, como explosiones de enemigo o enemigos en preparación para disparar.

### <a name="rewarding-a-successful-dodge"></a>Recompensar una sobreexposición correcta

El mecánico de dodging es uno de los aspectos más importantes del juego en RoboRaid y también algo que pensamos que era realmente único para la experiencia de HoloLens. Por lo tanto, queríamos realizar grandes sobreexposicións en el reproductor. Obtuvimos el Doppler "Whizz-by" para que suene bastante atractivo en el desarrollo. Inicialmente, mi plan era usar un bucle y manipularlo en tiempo real mediante el volumen, el paso y el filtro. La implementación de esto iba a ser muy elaborada, por lo que antes de confirmar los recursos para compilar realmente esto, creamos un prototipo barato con un recurso con el efecto Doppler que se preparaba para averiguar cómo lo sentía. Nuestro desarrollo de talentos lo hizo para que este recurso whizzdo se reproduzca exactamente 0,7 segundos antes de que el proyectil pase por los oídos del jugador y los resultados se sentían realmente increíbles. No es necesario decir que se ha reparado la solución más compleja y se ha implementado el prototipo.

\* * (Si desea obtener más información acerca de la creación de un recurso de audio con el efecto Doppler integrado, consulte un artículo con el diseñador de sonido Charles Deenan llamado [100 Whooshes en 2 minutos](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/)). *
<br>
![Dodging correctamente las recompensas de un enemigo en el jugador con un sonido Whizz satisfactorio.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Deszanjar sonidos ineficaces

Originalmente, habíamos querido jugar un sonido de explosión detrás del jugador una vez que ha sobrepasado correctamente el proyectil del enemigo, pero hemos decidido deshacerse por varios motivos. En primer lugar, no se sienta tan efectivo como Whizz-by SFX que usamos para la inexposición. En el momento en que el proyectil llega a una pared detrás, se habría producido algo más en el juego que enmascararía ese sonido. En segundo lugar, no teníamos colisiones en el piso, por lo que no pudimos reproducir la explosión cuando el proyectil alcanzó el piso en lugar de las paredes. Y, por último, el costo de CPU del sonido espacial. El enemigo de Elite Scorpion (uno que puede rastrear dentro de la pared) tiene un ataque especial que alcanza los ocho proyectiles. No solo hizo que un gran desorden en la combinación, sino que también presentaba entrecortados, porque hacía que la CPU estuviera demasiado duro.

### <a name="communicating-a-hit"></a>Comunicar una visita

Un problema interesante que hemos tenido en, que pensamos que era exclusivo de la experiencia de HoloLens, era la dificultad de comunicarse de forma eficaz con los jugadores que se han alcanzado. Lo que hace que una experiencia de realidad mixta sea correcta es la sensación de que se está produciendo la historia. Esto significa que debe creer que está lidiando una invasión del robot extranjero en su propia habitación.

Obviamente, los jugadores no sentirán nada cuando se alcancen, por lo que tuvimos que encontrar una manera de convencer realmente al jugador de que algo malo les happed. En los juegos convencionales podría ver una animación que le permite saber que el personaje ha tenido un golpe o que la pantalla podría parpadear en rojo y el carácter podría resultar un poco. Dado que estos tipos de indicaciones no funcionan en una experiencia de realidad mixta, decidimos combinar la indicación visual con un sonido realmente exagerado que indica que ha sacado el daño. He creado un gran sonido y lo hemos destacado en la combinación de que ha sobrepuesto todo. A continuación, para que se resalte aún más, hemos agregado un breve sonido de advertencia como si se hubiera receptora un subproceso nuclear. 
<br>
![Cuando se alcanza un jugador en RoboRaid, se ve una indicación visual, pero también se obtiene una señal de audio exagerada que indica que han sufrido daños.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtener sonido grande de pequeños altavoces

Los oradores de HoloLens son pequeños y ligeros para adaptarse a las necesidades del dispositivo, por lo que no se puede esperar que escuche demasiado bajo. De forma similar al desarrollo para dispositivos smartphones o dispositivos de juegos de mano, los diseñadores y Composers de sonido deben tener en cuenta el contenido de la frecuencia de su audio. Siempre se diseñan sonidos o se escribe música con un intervalo de frecuencia completo porque la utilización de auriculares es una opción para los usuarios. Sin embargo, para garantizar la compatibilidad con los hablantes de HoloLens, ejecuto una prueba ocasionalmente colocando un EC en el patrón de cualquier DAW en el que estoy trabajando. La configuración de EC consta de un filtro de paso alto de 600 a 700 Hz (no demasiado pronunciada) y un filtro de paso bajo alrededor de 10 000 (muy pronunciada). Esto le dará una idea aproximado de cómo se reproducirán los sonidos en el dispositivo.

Si se basa en graves para dar la sensación de cambiar el valor de cuerda en la música, es posible que la música pierda el sentido de la raíz al aplicar esta configuración de EC. Para solucionarlo, agregué otra capa al graves que es una octava superior (con algunos armónicos ricos) y la combina para obtener el sentido de la raíz. A veces, el uso de la distorsión para aumentar el valor de los armónicos proporcionará suficiente contenido de frecuencia en el intervalo superior para que nuestro cerebro piense que hay algo debajo. Esto es así para SFX como impactos, explosiones o sonidos para momentos especiales, como los ataques de superusuario de un jefe. En realidad, no puede confiar en el low-end para dar al jugador una sensación de impacto o peso. Al igual que con la música, el uso de distorsión para ofrecer un poco de esfuerzo de forma indefinida.

### <a name="making-your-audio-cues-stand-out"></a>Destaque las señales de audio

Naturalmente, todos los miembros del equipo querían bombasticr música, armas de alto volumen y explosiones de loco; pero también querían ser capaces de oír VoiceOver o cualquier otra pista de audio crítica del juego.

En un juego de consola con una gama completa de frecuencia, tiene más opciones para dividir las frecuencias en función de la importancia del sonido. No obstante, en el caso de RoboRaid, se limitaba el número de intervalos de frecuencias que podía curvar de los sonidos. Por ejemplo, si usa un filtro de paso bajo y una curva demasiado en el extremo superior del espectro, no quedará nada en el sonido porque no hay mucho más bajo.

Con el fin de que el sonido RoboRaid sea tan grande como en el dispositivo, tuvimos que reducir el intervalo dinámico de toda la experiencia y realizar un uso extensivo de la carga mediante la creación de una jerarquía clara de importancia para los diferentes tipos de sonidos. Configuro la cadena de-2 a-6 dB en función de la importancia. Personalmente no me gusta la untonía obvia en los juegos, por lo que he dedicado mucho tiempo a optimizar el tiempo de transición y salida y la cantidad de atenuación del volumen. Se configuran buses independientes para sonido espacial, sonido no espacial, VO y bus seco sin reverberación para música y, luego, se crearon buses de alta prioridad, críticos y no críticos. Los recursos se configuraron para ir a los buses correspondientes.

Espero que los profesionales de audio salgan del trabajo en sus propias aplicaciones mientras trabajaba en RoboRaid. No puedo esperar para ver (y oír) el contenido de las personas con talento ajenos a Microsoft para HoloLens.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Un truco que he descubierto para realizar determinados eventos (como explosiones) suena "más grande", al igual que están llenando el salón, era crear un recurso mono para el sonido espacial y combinarlo con un recurso estéreo 2D para reproducirlo en 3D. Lleva cierto ajuste, ya que tener demasiada información en el contenido estéreo disminuirá la direccionalidad de los recursos mono. Sin embargo, el hecho de obtener el equilibrio tiene como resultado grandes sonidos que permitirán a los jugadores activar sus cabezales en la dirección correcta.

Puede probar esto con los recursos de audio siguientes:

**Escenario 1**
1. Descargue [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) y establézcalo en reproducción a través de un sonido espacial y asígnelo a un evento.
2. Descargue [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) y establézcalo en reproducción en estéreo 2D y asígnelo al mismo evento que el anterior. Dado que estos recursos se normalizan en Unity, atenuar el volumen de ambos recursos para que no se recorte.
3. Reproducir ambos sonidos juntos. Mueva el dedo para sentir cómo suena espacial.

**Escenario 2**
1. Descargue [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) y establézcalo en reproducción a través de un sonido espacial y asígnelo a un evento.
2. Reproduzca este recurso y compárelo con el evento del escenario 1.
3. Pruebe un equilibrio diferente de archivos mono y estéreo.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>Ingeniero de audio@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [RoboRaid para Microsoft HoloLens](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
