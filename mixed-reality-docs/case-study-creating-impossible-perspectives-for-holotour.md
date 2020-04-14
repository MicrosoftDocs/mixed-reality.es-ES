---
title: 'Caso práctico: creación de perspectivas imposibles para HoloTour'
description: Queríamos que tu experiencia en HoloTour para Microsoft HoloLens sea unforgettable. Además de las paradas tradicionales de turista, hemos planeado algunas "perspectivas imposibles".
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: f3ca07dfab1e4477039481c268e418aac9034bc5
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278173"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>Caso práctico: creación de perspectivas imposibles para HoloTour

Queríamos que tu experiencia en HoloTour para Microsoft HoloLens sea unforgettable. Además de las paradas tradicionales de turista, hemos planeado algunas "perspectivas imposibles": momentos que serían imposibles de experimentar en cualquier paseo pero que, a través de la tecnología de HoloLens, podríamos traer directamente a su salón. La creación del contenido de estas experiencias requiere algunas técnicas distintas de las del proceso de captura estándar.

## <a name="the-content-challenge"></a>El desafío del contenido

Hay algunas escenas en la experiencia de HoloTour, como el globo de aire activo que se encuentra sobre el período de Roma y la lucha gladiatorial en el Colosseum de la antigua Roma, que proporcionan vistas únicas que no verá en ningún otro lugar. Estos momentos están diseñados para entusiasmarse y sorprenderle, lo que hace que el viaje a través de HoloTour sea algo más que una experiencia educativa. Estos son los momentos en los que queremos que se olvide y se entusiasmará con la información de otras personas. Dado que no pudimos poner en marcha nuestra plataforma de cámara en el cielo y aún no hemos realizado el viaje de tiempo, se ha llamado a cada una de estas "perspectivas no posibles" para un enfoque especial en la creación de contenido.

## <a name="behind-the-scenes"></a>En segundo plano

Crear estos momentos únicos y perspectivas requiere algo más que simplemente filmando y editando. Tardó mucho tiempo, personas con muchos conocimientos diferentes y un poco de Hollywood mágica.

### <a name="viewing-rome-from-a-hot-air-balloon"></a>Ver Roma desde un globo de aire activo

Desde los primeros días de planeación, sabíamos que queríamos realizar vistas aéreas en HoloTour. Ver Roma desde el cielo le proporciona una perspectiva que la mayoría de las personas nunca ven y una idea de cómo se ubican espacialmente los puntos de referencia más populares. Intentar capturarlas con nuestra cámara y la plataforma de micrófono existentes habría sido enormemente difícil, pero afortunadamente no tenemos que hacerlo.

En primer lugar, es importante explicar que todas las ubicaciones que visita en HoloTour tienen movimiento. Nuestro objetivo era "sentir lo que está realmente allí" y, puesto que está rodeado por el movimiento en todo el mundo real, nuestros destinos virtuales son necesarios para transmitir también el movimiento ambiente. Por ejemplo, al visitar el Pantheon de su viaje, verá que los usuarios se desplazan a través de la Plaza y congregating en los pasos. El movimiento de fondo le ayuda a sentir que realmente está en la ubicación, en lugar de hacerlo en un entorno de ensayo y estático.

Para crear las vistas aéreas para la conducción de globo, trabajamos con otros equipos de Microsoft para obtener acceso a imágenes panorámicas aéreas de Roma. La calidad de estas imágenes era excelente y la vista era sorprendente, pero cuando se usaban en segundo plano sin modificarla, parecían de duración en comparación con las otras partes del paseo y la falta de movimiento estaba disstando. 


![la cesta de globo de aire activo, flotando sobre Roma.](images/hotairballoon1-300px.png)<br>
*La cesta de globo de aire activo, flotante sobre Roma*

Para asegurarse de que las ubicaciones aéreas cumplían la misma barra de calidad que otros destinos, decidimos transformar las fotografías estáticas en escenas de vida y mudanzas. El primer paso era editar la imagen y el movimiento compuesto en él. Hemos contratado un artista de efectos visuales para ayudarnos con esto. La edición se realizó para mostrar las nubes con una derivación lenta, las aves voladas por y un plano ocasional o helicóptero que atraviesa el Skyline. En segundo plano, se han realizado varios automóviles para impulsar las calles. Si ha estado en el recorrido de Roma en HoloTour, es poco probable que se haya informado explícitamente de cualquiera de estos movimientos. Eso es realmente fantástico. El movimiento sutil no está diseñado para captar el ojo, pero sin estos pequeños toques, los usuarios se han observado inmediatamente que se trata de una imagen estática en la escena.

Lo segundo que hicimos fue ofrecer un punto de estratégicos desde el que ver la escena. No le parecerá que realmente está en realidad si parece que simplemente flota en midair, por lo que creamos un modelo 3D de un globo y lo colocamos dentro de él. Esto le permite recorrer el globo y mirar el borde para obtener un mejor punto de vista. Encontramos que esto es una forma natural y divertida de experimentar la imagen aérea.

La experiencia de globo de aire activo presentó desafíos únicos para nuestro equipo de audio, ya que la logística nos impidió que los micrófonos se desplazaran a miles de pies en Roma. Afortunadamente, teníamos una gran cantidad de capturas de audio ambiente de toda la ciudad que pudimos usar durante la producción. Colocamos los emisores de audio en sus ubicaciones relativas desde donde se capturaron desde el principio. A continuación, el audio se filtró a sonido distante, como si lo oíra de la perspectiva de alguien que ha atacado en el globo de aire caliente, lo que proporciona un SoundScape auténtico y direccional para la escena.

### <a name="time-traveling-to-ancient-rome"></a>Tiempo de viaje a la antigua Roma

Los restos de monumentos y edificios en Roma son impresionantes incluso 2000 años después de su construcción, pero sabíamos que teníamos una oportunidad única para mostrarle lo que sería como volver atrás en el tiempo y ver estas estructuras tal y como aparecían en la antigua versión Roma.

Naturalmente, no hay ningún material de vídeo o imagen estática de la Colosseum tal como aparecía cuando se compiló, por lo que necesitábamos crear nuestra propia. Tuvimos que hacer una gran cantidad de investigación para aprender sobre la estructura que podríamos. comprender los materiales desde los que se realizó, revisar diagramas arquitectónicos y leer descripciones históricas para obtener información suficiente para poder realizar un recreo virtual. 

![el mínimo de día de la Colosseum con una superposición en la que se muestra el suelo de la arena tal como habría visto en la antigua Roma.](images/rome-colosseum-overlay-500px.png)<br>
*El día actual del Colosseum con una superposición en la que se muestra el suelo de la arena tal como habría visto en la antigua Roma*

Lo primero que queríamos es mejorar las visitas tradicionales con las superposiciones educativas. En HoloTour, cuando visita los soportes de la Colosseum tal y como se encuentra en la actualidad, el suelo se transforma para mostrar cómo se habría visto durante el uso, incluidas las áreas de ensayo subterráneas elaboradas. En un paseo normal, es posible que tenga esta información, que puede intentar imaginarla, pero en HoloTour puede verla realmente.

En el caso de una superposición como esta, nuestros artistas coincidían con el punto de vista de nuestro metraje de captura y creamos la imagen de superposición manualmente. La perspectiva debe coincidir para que, cuando reemplacemos el vídeo con la imagen, ambos se alineen correctamente.

### <a name="staging-the-gladiator-fight"></a>Ensayo de la lucha Gladiator

Mientras que las superposiciones son una manera atractiva de enseñar a las personas sobre el historial, lo que nos entusiasmaba más entusiasmado era transportarle de vuelta. La superposición era simplemente una imagen de un punto de vista determinado, pero el tiempo de viaje requeriría que se modelara todo el Colosseum y, como se explicó anteriormente, era necesario tener movimiento en la escena para que se sienta activo. Lograr esto supuso una cantidad considerable de esfuerzo.

Este compromiso es demasiado grande para que nuestro equipo se haga por sí solo, por lo que nuestro equipo de arte trabajó con Whiskytree, una empresa de efectos externos que normalmente trabaja en efectos visuales para películas de Hollywood. Whiskytree nos ayudó a volver a crear el Colosseum en su Heyday, lo que nos permite enseñarle sobre la estructura mientras se encuentra en el suelo de la arena y crear una vista de una lucha de Gladiator desde el cuadro del emperador. Los amontonamientos de Felicidades y las pancartas de salud agregan el movimiento sutil necesario para que parezca que se trata de lugares reales y no solo de imágenes.

![el Colosseum que se ha creado de forma recreada a partir del suelo de la arena. Cuando se visualizan en HoloTour, los banners se fluttern en el pan, lo que permite un movimiento.](images/recreated-colosseum-holotour-500px.png)<br>
*La Colosseum recreada, tal como se ha detectado en el suelo de la arena. Cuando se visualizan en HoloTour, los banners se fluttern en el pan, lo que permite un movimiento.*

El paseo por Roma culmina con la lucha Gladiator. Whiskytree nos proporcionó las simulaciones de la arena y el terreno 3D representadas como vídeo, pero necesitábamos agregar en el Gladiators en el suelo de la arena. Esta parte de nuestro proceso parecía más similar a una producción de vídeo de Hollywood que un proyecto de un estudio de incubación. Los miembros de nuestro equipo han asignado una secuencia de lucha aproximada y, a continuación, la refinan con un Choreographer. Contratamos a los actores en el ensayo de nuestra lucha simulada y de la armadura comprada para que lo parezcan. Por último, hemos filmado toda la escena en una pantalla verde.

![nuestra Gladiators, obtener instrucciones entre el proceso.](images/green-screen-gladiators-holotour-500px.jpg)<br>
*Nuestro gladiatiors, obteniendo instrucciones entre el proceso*

Esta escena le coloca en el cuadro del emperador, lo que significaba que todo el material de metraje debía ser de esa perspectiva. Si se filmó desde donde el Gladiators lucha en el suelo de la arena, no habríamos componer correctamente la secuencia de lucha en el futuro, por lo que ponemos en marcha nuestro operador de cámara en una gran elevación de tijeras, observando la secuencia de lucha para filmarla.

![obtener la perspectiva adecuada: filmando a partir de una levantar tijera.](images/scissor-lift-holotour-500px.jpg)<br>
*Obtener la perspectiva adecuada: filmando a partir de un elevador de tijeras*

En postproducción, el Gladiators se composite en el suelo de la fase y la perspectiva era correcta, pero quedaba un problema: las sombras del Gladiators en la pantalla verde se quitaban como parte del proceso de composición. Sin sombras, parecía que los Gladiators estaban flotando en el aire. Afortunadamente, Whiskytree es excelente para resolver solo este tipo de problema y usaba un poco de Wizardry técnico para volver a agregar sombras a nuestra escena. El resultado es lo que ve en el paseo hoy mismo.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> es un Desarrollador Senior que ha aprendido más sobre las plataformas de cámara y la reproducción de vídeo de las que pensaba que podía trabajar en HoloTour.</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> es un diseñador de audio que nos ha asegurado de que pudiera experimentar el soundscape de todos los destinos que visita, incluso cuando regresa al tiempo.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> es un artista de vídeo que nos ha asegurado de que su viaje a Roma sea lo más fácil posible.</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>Vea también
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
