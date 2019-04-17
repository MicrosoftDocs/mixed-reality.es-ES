---
title: 'Caso práctico: uso sonido espacial en RoboRaid'
description: Sonido espacial es una de las características más interesantes de Microsoft HoloLens, que proporciona una manera para que los usuarios perciben qué está pasando en torno a ellas cuando los objetos están fuera de la línea de visión.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, sonido espacial
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600778"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Caso práctico: uso sonido espacial en RoboRaid

Charles Sinex, responsable de audio en el equipo de experiencia de Microsoft HoloLens, habla sobre los desafíos únicos que afrontó al crear audio para [RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j), un solucionador de la primera persona de realidad mixta.

## <a name="the-tech"></a>La tecnología

[Sonido espacial](spatial-sound.md) es una de las características más interesantes de Microsoft HoloLens, que proporciona una manera para que los usuarios perciben qué está pasando en torno a ellas cuando los objetos están fuera de la línea de visión.

En RoboRaid, el uso más obvio y eficaz de sonido espacial es alerta al Reproductor que algo que sucede fuera de la visión periféricos del usuario. Por ejemplo, puede escribir el Breacher desde cualquiera de las paredes digitalizadas en la sala, pero si no está accesible desde la ubicación donde está entrando, podría perder. Para generar una alerta para este invasión, oirá un poco distinto de audio procedentes de donde está entrando en el Breacher, que le permite saber que necesita para actuar rápidamente para detenerlo.

## <a name="behind-the-scenes"></a>En segundo plano

El proceso de creación de sonido espacial para las aplicaciones de HoloLens es tan nuevo y único y puede provocar la falta de proyectos anteriores para usarla como referencia a un lote de cabeza arañazos cuando surge un problema. Con suerte, estos ejemplos de los desafíos de audio nos enfrentamos mientras lo RoboRaid le ayudará a medida que cree audio para sus propias aplicaciones.

### <a name="be-mindful-of-taxing-the-cpu"></a>Esté atento a recargar la CPU

Puede ser exigentes sonido espacial en la CPU. Para obtener una experiencia ocupada como RoboRaid resultó crucial mantener las instancias de sonido espacial en ocho en un momento dado. En su mayor parte, era tan sencillo como establecer el límite de instancias de diferentes eventos de audio para que se eliminan todas las instancias que se producen cuando se alcanza el límite. Por ejemplo, al generan drones, sus screams se limitan a tres instancias en un momento dado. Considerar la actividad sólo aproximadamente cuatro drones pueden generar a la vez, tres screams son muchas ya que no hay ninguna manera su cerebro puede realizar un seguimiento de que muchos eventos de audio de sonido parecido. Esto libera los recursos para otros eventos espaciales de sonido, como enemigas explosiones o enemigos preparando para alcanzar.

### <a name="rewarding-a-successful-dodge"></a>Un regalo para una correcta dodge

El mecánico dodging es uno de los aspectos más importantes del juego en RoboRaid y algo que pensamos que era realmente único a la experiencia de HoloLens. Por lo tanto, hemos querido sobreexpone correcta muy gratificante para el Reproductor. Tenemos al Doppler "pasen zumbando-por" para que se emita atractivas bastante pronto en el desarrollo. Inicialmente, mi plan fue usar un bucle y manipularlos en tiempo real con el volumen, el cabeceo y filtro. La implementación para que esto iba a ser muy elaborada, por lo que antes de confirmar los recursos necesarios para realmente crear esto, hemos creado un prototipo económico con un recurso con el efecto de Doppler preparados para averiguar cómo simplemente se sentía *. Nuestro desarrollo talento resultaba para que este activo por pasen zumbando podría reproducir exactamente 0,7 segundos antes de que habrá pasado el proyectil auricular del jugador y los resultados creía realmente increíbles! Obviamente, se ha descartado la solución más compleja e implementa el prototipo.

** (Si desea obtener más información acerca de cómo crear un recurso de audio con el efecto de Doppler integrado, consulte un artículo por diseñador sonido llamado Charles Deenan [100 Whooshes en 2 minutos](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/).) *
<br>
![Correctamente. evitar proyectil un enemigo recompensa al Reproductor con un sonido pasen zumbando forma satisfactoria.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Ditching sonidos ineficaces

Originalmente, habíamos queríamos reproducir un sonido en el Reproductor un aumento vertiginoso una vez que hayan sobreexpuesta correctamente el proyectil enemigo, pero hemos decidido eliminar esto por varias razones. En primer lugar, no se siente tan eficaz como se ha usado para la dodge whizz mediante SFX. En el momento en que el proyectil llega a una pared detrás, cosa hubiese sucedido en el juego que sería bastante mucho máscara que suenan. En segundo lugar, no tenemos colisiones en el suelo, por lo que no se pueden obtener la expansión a reproducir cuando el proyectil alcanza el límite inferior en lugar de las paredes. Y por último, se ha producido el costo de CPU del sonido espacial. El enemigo Elite Scorpion (uno que pueda rastrear dentro de la pared) tiene un ataque especial que dispara proyectiles aproximadamente ocho. No sólo hizo un caos enorme en la combinación, también introdujo desagradables entrecortado porque experimentaba la CPU muy difícil.

### <a name="communicating-a-hit"></a>Comunica un acierto

Un problema interesante hemos tenido que pensamos que eran exclusivos de la experiencia de HoloLens, es la dificultad de se comunican eficazmente a los jugadores que ha alcanzado. Lo que hace una realidad mixta experiencia correcta es la sensación de que se está realizando la historia para usted. Esto significa que tiene que creer que lucha una invasión robot externo en su propia sala de estar.

Los jugadores obviamente no sienten nada cuando alcanzarán, por lo que tuvimos que encontrar una manera realmente convencer al Reproductor que algo malo tenía happed a ellos. En juegos convencionales, puede que vea una animación que permite conocer su carácter ha tomado un acierto o la pantalla puede parpadear rojo y su carácter podría grunt un poco. Puesto que estos tipos de señales no funcionan en una experiencia de realidad mixta, hemos decidido combinar la indicación visual con un sonido realmente exagerado que indica que ha tomado el daño. Creé un sonido grande y resultaba tan destacado en la combinación de todo ducked hacia abajo. A continuación, para que destaque incluso más, se ha agregado un breve sonido de advertencia como si se desactivaba sub nuclear. 
<br>
![Cuando se alcanza un reproductor en RoboRaid, vea una indicación visual, pero también obtendrá una indicación de audio exagerada que les informa de que han tomado el daño.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Obtención de sonido grande de altavoces pequeños

HoloLens altavoces son pequeños y ligeros satisfacer las necesidades del dispositivo, por lo que no se puede esperar recibir demasiado bajo. De forma similar al desarrollo para smartphones o dispositivos de juegos portátiles, los diseñadores de sonido y compositores tienen que ser consciente del contenido de audio de su frecuencia. Siempre diseñar sonidos o escribir música con el intervalo de frecuencia completa porque el exceso de auriculares es una opción para los usuarios. Sin embargo, para garantizar la compatibilidad con altavoces HoloLens, ejecutar una prueba ocasionalmente colocando un EQ en el servidor maestro de cualquier DAW llego a estar trabajando en. La configuración de EQ consta de un filtro paso alto aproximadamente 600 a 700 Hz (no demasiado pronunciada) y paso bajo de filtro en aproximadamente 10 K (muy pronunciada). Que debe proporcionarle una idea aproximada de cómo los sonidos de realizarán la reproducción en el dispositivo.

Si confía en graves para dar el sentido de cuerda cambiar de la música, es posible que su música pierde completamente el sentido de raíz al aplicar esta configuración EQ. Para solucionar este problema, agrega otra capa a los sonidos graves que es una octava superior (con algunas armónicos enriquecido) y se puede combinar para obtener el sentido de la parte posterior de la raíz. A veces con distorsión de amp copia la armonía proporcionará suficiente contenido de la frecuencia del intervalo superior para hacer que nuestro cerebro creer que hay algo debajo de ella. Esto es cierto para SFX como impactos, explosiones o sonidos para momentos especiales, como los ataques super un jefe. Realmente no puede depender de bajo costo para hacerse una idea del impacto o el peso del Reproductor. Al igual que con la música, distorsión para dar un poco de estudio sin duda ha ayudado a.

### <a name="making-your-audio-cues-stand-out"></a>Hacer que su pistas de sonido destaque

Naturalmente, todo el equipo deseaba bombastic música, cañones mucho ruidos y explosiones locos; pero también deseaba escuchar voiceover o cualquier otras pistas de sonido críticos para el juego.

En un juego de consola con una gama completa de frecuencia tiene más opciones para dividir las frecuencias según la importancia del sonido. Para RoboRaid, sin embargo, estaba limitado el número de intervalos de frecuencias que podría curva de sonidos. Por ejemplo, si usa el filtro de paso bajo y curva demasiado desde el extremo superior del espectro, no tendrá todo lo que queda en el sonido porque no hay mucho low-end.

Con el fin de que RoboRaid suene tan grande como sea posible en el dispositivo, se debían reducir el intervalo dinámico de la experiencia completa y realiza un uso extensivo de sobra mediante la creación de una jerarquía clara de importancia para los distintos tipos de sonidos. Establezca evite desde -2-6 DB según la importancia. Personalmente no me gusta evite evidente en los juegos, por lo que me pasaba mucho tiempo, ajuste el fundido de entrada/salida agote el tiempo y la cantidad de atenuación de volumen. Se configure buses separadas para sonido espacial, sonido no espaciales, VO y bus seco sin reverberación para copiar música, a continuación, crean los buses de prioridad muy alta, críticas y que no son críticas. Los activos, a continuación, se han configurado para ir a su autobús adecuados.

Espero que los profesionales de audio tendrá tanta diversión y emoción trabajar en sus propias aplicaciones igual de trabajar en RoboRaid. Estoy ansioso por ver (y escuchar) lo que las personas con talento fuera de Microsoft aparecerá con para HoloLens.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Un truco que descubrí efectúe determinados eventos (por ejemplo, explosiones) de sonido "mayores", como está llenando la sala: consistía en crear un recurso de mono para el sonido espacial y combina con un recurso de estéreo 2D, que se reproducirá en 3D. Realizar algunos ajustes, ya que tener demasiada información en el contenido estéreo disminuirá la direccionalidad de los activos de mono. Sin embargo, conseguir el equilibrio adecuado dará como resultado enormes sonidos que obtendrán los jugadores a Predestinado en la dirección correcta.

Puede probar usted mismo con los recursos de audio a continuación:

**Escenario 1**
1. Descargar [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) y establezca para la reproducción de sonido espacial y asígnelo a un evento.
2. Descargar [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) y establecido en reproducción en 2D estéreo y asignarse al mismo evento anterior. Dado que estos recursos se normalizan en Unity, atenuar volumen de los activos para que no recorta.
3. Reproducir sonidos de ambos juntos. Mover la cabeza aproximadamente a sentirse espacial cómo suena.

**Escenario 2**
1. Descargar [roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav) y establecido en la reproducción de sonido espacial y asignar a un evento.
2. Reproducir este activo por sí solo, a continuación, compárelo con el evento del escenario 1.
3. Pruebe el equilibrio entre distintos archivos estéreo y mono.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>Ingeniero de audio @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [RoboRaid para Microsoft HoloLens](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
