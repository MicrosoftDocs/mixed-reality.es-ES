---
title: 'Caso práctico: capturar y crear contenido para HoloTour'
description: HoloTour para Microsoft HoloLens proporciona paseos personales 3D envolventes icónica ubicaciones en todo el mundo.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloTour, HoloLens, la realidad mixta
ms.openlocfilehash: 6c9e5f44c439310883c8b0271187a7b2263b0854
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597637"
---
# <a name="case-study---capturing-and-creating-content-for-holotour"></a>Caso práctico: capturar y crear contenido para HoloTour

HoloTour para Microsoft HoloLens proporciona paseos personales 3D envolventes icónica ubicaciones en todo el mundo. Como los diseñadores, artistas, productores, diseñadores de audio y los desarrolladores que trabajan en este proyecto ha descubierto, creación de una representación en 3D convincingly real de una ubicación conocida toma una combinación única de la magia creativa y tecnológica.

## <a name="the-tech"></a>La tecnología

Con HoloTour, queríamos hacer posible que las personas que visite algunos de los destinos más asombrosos del mundo, como el [ruinas de Machu Pichu](https://en.wikipedia.org/wiki/Machu_Picchu) en Perú o el día modernas [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) en Italia, directamente desde sus propias salas de estar. Nuestro equipo hizo el objetivo de HoloTour "hacerla sentir como que está realmente ahí." La experiencia necesaria para ser algo más que imágenes o vídeos. Mediante el aprovechamiento de la presentación únicos, el seguimiento y la tecnología de audio de HoloLens se consideró que nos podríamos prácticamente de transporte, en otro lugar. Necesitamos capturar el punto de mira, sonidos y geometría tridimensional de todas las ubicaciones se visitado y, a continuación, volver a crear que dentro de nuestra aplicación.

Para ello, necesitamos una cámara de 360 ° plataforma con la captura de audio direccional. Necesitaba capturar en muy alta resolución, por lo que tendría un aspecto nítida cuando reproduce en un HoloLens el material de archivo y las cámaras deberá colocarse juntos con el fin de minimizar los artefactos de combinación. Queríamos esférica completa cobertura, no solo en el horizonte, pero por encima y debajo de usted también. La plataforma de pruebas también es necesario para ser portátil, de modo que nos podríamos aprovechar todo el mundo. Se evalúan las opciones disponibles de listos para usar y producidas simplemente no lo suficientemente buenas para hacer realidad nuestra visión: ya sea debido a la resolución, el costo o el tamaño. No pudimos encontrar una plataforma de cámara que satisface las necesidades de nuestros, tendríamos creado uno nosotros mismos.

### <a name="building-the-rig"></a>Creación de la plataforma de pruebas

La primera versión, realizadas desde cartulina, Velcro, conducto 14 cámaras GoPro y cinta, fue algo MacGyver habría sido me siento orgulloso de. Después de revisar todo, desde soluciones low-end para las plataformas fabricadas personalizadas, cámaras GoPro eran en última instancia, la mejor opción para nosotros porque fueron pequeños, asequible y tenía almacenamiento fácil de usar memoria. El factor de forma pequeño era especialmente importante ya que nos ha permitido colocar las cámaras bastante juntos: cuanto menor sea la distancia entre las cámaras, menor será la combinación artefactos estarán. Nuestra organización de cámara único nos ha permitido lograr cobertura completa esfera *plus* superposición suficiente para alinear las cámaras y suavizar algunos artefactos durante el proceso de creación de forma inteligente.

Aprovechar la [sonido espacial](spatial-sound.md) capacidades en HoloLens es fundamental para crear una experiencia envolvente convincingly real. Utilizamos una matriz de cuatro micrófono situada debajo de las cámaras en el trípode, lo que podría capturar sonidos desde la ubicación de la cámara en cuatro direcciones, que nos da información suficiente para crear sonidos espaciales en nuestro segundo plano.

![Nuestra plataforma de cámara de 360° se configure para grabación fuera el Pantheon.](images/camera-pantheon-200px.png)

Nuestra plataforma de cámara de 360° se configure para grabación fuera el Pantheon. 


Hemos probado out nuestra plataforma casero tomando hasta Rattlesnake Ridge cerca de Seattle, capturar el escenario en la parte superior de la montar. El resultado, aunque mucho menos perfeccionado de las ubicaciones que se ve en HoloTour hoy en día, nos dio confianza que era lo suficientemente buena para hacerla sentir como que está realmente ahí nuestro diseño de la plataforma de pruebas.

Hemos actualizado nuestra plataforma de pruebas desde Velcro y cartulina para una carcasa de cámara 3D impresa y compró paquetes externos de la batería para las cámaras GoPro simplificar la administración de la batería. A continuación, hicimos una prueba más amplia, viaja hasta San Francisco para crear un paseo en miniatura de la costa de la ciudad y el puente de Golden Gate icónico. Esta plataforma de pruebas de la cámara es lo que se usa para la mayoría de nuestras capturas de las ubicaciones que visita en HoloTour.

![La plataforma de cámara de 360° grabando in Machu Pichu.](images/camera-machu-pichu-500px.png)

La plataforma de cámara de 360° grabando in Machu Pichu. 


## <a name="behind-the-scenes"></a>En segundo plano

Antes de la grabación, se necesitan para out las ubicaciones que deseamos incluir en nuestra visita virtual. Roma fue la primera ubicación que nos propusimos para el envío y queríamos que todo quede correcto, por lo que decidimos realizar una exploración de ida y vuelta de antemano. Le hemos enviado un equipo de seis personas, incluidos los artistas, diseñadores y los productores, para una visita en persona a los sitios que estábamos pensando en. El recorrido se tardó aproximadamente 9 días – 2.5 de viaje, el resto de la grabación. (Para Machu Pichu hemos optado por no para hacer un viaje de scout, investigación de antemano y unos días de búfer para la grabación de reserva.)

Mientras esté en Roma, el equipo tuvo las fotos de cada área y anotado datos interesantes, así como consideraciones prácticas, como lo difícil que resulta de viaje a cada zona y la dificultad que sería película debido a restricciones o muchedumbres. Esto puede parecer unas vacaciones, pero resulta mucho trabajo. Días se inicia al principio de la mañana e iría continuo hasta la noche. Todas las noches, material de archivo se ha cargado para el equipo en Seattle para revisar. 

![Nuestro equipo de captura en Roma.](images/holotour-filming-crew-rome-500px.jpg) 

Nuestro equipo de captura en Roma. 


Una vez completado la ida y vuelta scout, un plan final se realizó para grabación real. Esto requiere una lista detallada de donde que íbamos a una película, qué día y en qué momento. Cada día extranjero es costosa, por lo que necesita estos viajes sean eficaces. Hemos reservado las guías y los controladores en Roma para ayudarnos a y había usado por completo todos los días antes de Amanecer para después de la vigencia de. Debemos obtener el mejor material de archivo posibles con el fin de hacerla sentir como que está realmente ahí.

### <a name="capturing-the-video"></a>Captura de vídeo

Realizar unas cuantas cosas durante la captura puede hacer mucho más fácil el procesamiento posterior. Por ejemplo, cada vez que unir imágenes desde múltiples cámaras, terminará con artefactos visuales porque cada cámara tiene una vista ligeramente diferente. Los objetos de más de cerca son a la cámara, mayor será la diferencia entre las vistas, y mayor será la combinación de artefactos. Aquí es una forma sencilla para visualizar el problema: retener el pulgar delante de nuestras narices y mirar con solo un efecto de ojos. Ahora, cambie los ojos. Verá que aparece el control de posición para mover en relación con el fondo. Si mantiene el pulgar aún más lejos de la cara y repetir el experimento, aparecerá el pulgar a mueve menos. Es evidente movimiento es similar a la combinación problema nos enfrentamos: Los ojos, al igual que nuestra cámaras, no ven exactamente la misma imagen porque están separados por una pequeña distancia.

Dado que es mucho más fácil de evitar que el peor de los artefactos durante la grabación de corregirlos en el procesamiento posterior, intentamos mantener las personas y las cosas muy lejos de la cámara con la esperanza que podríamos eliminar la necesidad de que se deben combinar objetos de primer planos. Mantener una compensación grande en torno a nuestro cámara probablemente fue uno de los mayores desafíos que teníamos durante la grabación y se tenía que ser creativos para que funcione. Trabajar con guías locales era una gran ayuda en la administración de muchedumbres, pero también descubrimos que usar firme y a veces pequeños conos o bolsas bean: marcar nuestro espacio rodaje era razonablemente eficaz, sobre todo porque solo necesitamos obtener una breve cantidad de material de archivo en cada ubicación. A menudo era solo para llegar muy pronto en la mañana, antes de la mayoría de las personas que aparecían la mejor manera de obtener una buena captura.

Algunas otras técnicas útiles captura proceden directamente de prácticas de películas tradicionales. Por ejemplo, una tarjeta de corrección de color se utiliza en todas nuestras cámaras y las fotos de referencia capturada de texturas y los objetos que necesitemos más adelante. 

![Un montaje inicial de Machu Pichu que muestra la tarjeta de corrección de color.](images/rough-cut-machu-picchu-500px.png)

Cortar aproximada del material de archivo de Pantheon antes de la unión.

### <a name="processing-the-video"></a>Procesamiento del vídeo

Capturar el contenido de 360° es sólo el primer paso, se necesita una gran cantidad de procesamiento para convertir las grabaciones de cámaras sin procesar se capturan en los activos finales se ve en HoloTour. Una vez que estábamos volver principal debíamos tomar el vídeo de 14 cámara diferentes fuentes de distribución y convertirlo en un único vídeo continuo con artefactos mínima. Nuestro equipo de material gráfico usa una serie de herramientas para combinar y perfeccionar el material de archivo capturado y desarrollamos una canalización para optimizar el procesamiento tanto como sea posible. El material de archivo tenía que ser pegada color junto, corregido y, a continuación, compuesto para quitar distraer elementos y los artefactos o agregar bolsillos complementarios de vida y el movimiento, todo ello con el objetivo de mejorar esa sensación de estar realmente allí.

![Cortar aproximada del material de archivo de Pantheon antes de la unión.](images/rough-cut-pantheon-500px.png)

Cortar aproximada del material de archivo de Pantheon antes de la unión. 


Para unir los vídeos, hemos usado una herramienta denominada [PTGui](http://www.ptgui.com/) y se integra en nuestra canalización de procesamiento. Como parte del procesamiento posterior a la se extraen todavía marcos nuestros vídeos y encuentra un modelo de combinación que tenía bueno para uno de esos marcos. Se aplica, a continuación, ese patrón para un complemento personalizado que escribimos que permiten a nuestro vídeo artistas ajustar con precisión y ajustar el modelo de combinación durante la composición en After Effects. 

![Captura de pantalla de PTGui que muestra el material de archivo de Pantheon unida.](images/stitching-tool-pantheon-500px.png)

Captura de pantalla de PTGui que muestra el material de archivo de Pantheon unida. 


### <a name="video-playback"></a>Reproducción de vídeo

Después de que se complete el procesamiento del material de archivo, tenemos un vídeo sin problemas, pero es extraordinariamente grandes, resolución de aproximadamente 8 K. Descodificación de vídeo es costosa y hay muy pocos equipos que pueden controlar un vídeo de 8 KB, por lo que el siguiente desafío fue encontrar una manera de reproducir este vídeo en HoloLens. Hemos desarrollado varias estrategias para evitar el costo de descodificación al mismo tiempo que la sensación de usuario como la estaban viendo todo el vídeo.

La optimización más sencilla consiste en evitar las partes del vídeo que no cambian mucho la descodificación. Se escribió una herramienta para identificar áreas en cada escena que tienen poco o ningún movimiento. Para dichas regiones se muestra una imagen estática en lugar de un vídeo de descodificación cada fotograma. Para que esto sea posible, se divide el vídeo gran en fragmentos mucho menores.

También se ha asegurado de que cada píxel que se puede descodificar se usaba la forma más eficaz. Experimentamos con técnicas de compresión para reducir el tamaño del vídeo; dividimos el vídeo regiones con arreglo a los polígonos de la geometría ¿se proyectan en; hemos ajustado UVs y EE.UU los vídeos en función de cuánto polígonos diferentes de detalle incluidas. El resultado de este trabajo es lo que comenzó como una sola 8k vídeo activa en muchos fragmentos que tienen un aspecto prácticamente ininteligibles hasta que estén correctamente, vuelva a proyectados en la escena. Para un desarrollador de juegos que entiende la asignación de textura y empaquetado de UV, probablemente se le resultarán familiar. 

![Una vista completa de la Pantheon antes de las optimizaciones.](images/pantheon-before-optimization-500px.png) 

Una vista completa de la Pantheon antes de las optimizaciones. 


![La mitad derecha de la Pantheon, procesado para la reproducción de vídeo.](images/pantheon-process-video-playback-500px.png) 

La mitad derecha de la Pantheon, procesado para la reproducción de vídeo. 


![Ejemplo de una sola región vídeo después de la optimización y mejora del empaquetado.](images/single-video-region-after-optimization-500px.png) 

Ejemplo de una sola región vídeo después de la optimización y mejora del empaquetado. 


Otro truco que usamos fue evitar la descodificación de vídeo que no está viendo activamente. Mientras se encuentra en HoloTour, solo puede ver parte de la escena completa en un momento dado. Sólo nos descodificar vídeos dentro o fuera de su campo de visión (FOV) que en breve. Al girar la cabeza, se iniciará la reproducción de las regiones del vídeo que se encuentran ahora en su campo visual y detener la reproducción de los que ya no están dentro de él. Mayoría de los usuarios incluso no tenga en cuenta que esto sucede, pero si activa en torno a rápidamente, podrá ver el vídeo tarda un segundo para iniciar, mientras tanto verá una imagen estática que fundidos, a continuación, hacer una copia vídeo una vez que esté listo.

Para que esta estrategia funcione desarrollamos un sistema de reproducción de vídeo extenso. Hemos optimizado el código de reproducción de nivel bajo para asegurarse de vídeo cambiar extremadamente eficaz. Además, hemos tenido que codificar nuestros vídeos de una manera especial y le permite cambiar rápidamente a cualquier vídeo en cualquier momento. Esta canalización de reproducción tardó una cantidad considerable de tiempo de desarrollo, por lo que implementamos en fases. Comenzamos con un sistema más sencillo que era menos eficiente, pero los diseñadores permitidos y los artistas para trabajar en la experiencia y lentamente mejorada a un sistema más sólido de reproducción que nos ha permitido para el envío en la barra de calidad final. Este sistema final tenía herramientas personalizadas que hemos creado dentro de Unity para configurar el vídeo dentro de la escena y supervise el motor de reproducción.

### <a name="recreating-near-space-objects-in-3d"></a>Volver a crear objetos de cerca de espacio en 3D

Vídeos constituyen la mayor parte de lo que ve en HoloTour, pero hay una serie de objetos 3D que aparecen cerca de usted, como la pintura en Piazza Navona, la fuente fuera el Pantheon o el globo de aire caliente que se representan segundo plano aéreo. Estos objetos 3D son importantes porque es muy buena de cerca la percepción humana de profundidad, pero no muy buena lejos. Que podríamos conseguirlo con vídeo en la distancia, pero para permitir que los usuarios a caminar alrededor de su espacio y parezca que realmente existen, los objetos próximos necesitan profundidad. Esta técnica es similar a la clase de cosas que puede aparecer en un Museo de historia natural, un diorama paisajismo físico, plantas y especímenes animales en primer plano, pero se aleja en un dibujo mate inteligentemente enmascarada en segundo plano de la imagen.

Algunos objetos son recursos 3D simplemente hemos creado y agregado a la escena para mejorar la experiencia. La pintura y el globo de aire caliente entran en esta categoría porque no estaban presentes cuando se graban. Al igual que los activos de juego, se crearon de un intérprete en 3D de nuestro equipo y con textura adecuadamente. Colocamos en nuestro segundo plano cerca de dónde está parado y el motor de juego puede reproducirlas en la muestra de HoloLens dos para que aparezcan como un objeto 3D.

Otros recursos, como la fuente fuera el Pantheon, son objetos reales que existen en las ubicaciones donde nos estamos grabar vídeo, pero para poner estos objetos fuera del vídeo y en 3D, tenemos que hacer varias cosas.

En primer lugar, necesitamos información adicional acerca de cada objeto. Mientras se encuentra en la ubicación de la grabación, nuestro equipo captura una gran cantidad de material de referencia de estos objetos para que tendríamos suficiente detallada de las imágenes con precisión volver a crear las texturas. El equipo también ha realizado una [photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) scan, que construye un modelo 3D entre docenas de imágenes en 2D, lo que nos proporciona un modelo aproximado del objeto a escala perfecto.

Estamos procesando nuestro material de archivo, se quitan los objetos que más adelante se reemplazará con una representación 3D del vídeo. Los activos 3D están basado en el modelo photogrammetry pero limpia y simplificado por nuestro artistas. Algunos objetos, podemos usar las partes del vídeo, por ejemplo, la textura de agua en la fuente, pero la mayoría de la fuente es ahora un objeto 3D, que permite a los usuarios percibir la profundidad y andar en un espacio limitado en la experiencia. Tener objetos cerca de espacio similar al siguiente en gran medida se agrega a la sensación de realismo y ayuda a hacer que los usuarios en la ubicación virtual. 

![Quita el material de archivo de pantheon con la fuente. Se reemplazará con un recurso de 3D.](images/object-removal-pantheon-500px.png)

Quita el material de archivo de pantheon con la fuente. Se reemplazará con un recurso de 3D.


## <a name="final-thoughts"></a>Observaciones finales

Obviamente, hubo más a la creación de contenido que lo que hemos descrito aquí. Hay unos escenas, nos gusta llamarlos "imposibles perspectivas", incluyendo luchar contra el manejo de globo de aire caliente y el gladiator en el Colosseum, lo que llevó un enfoque más creativo. Trataremos estas opciones en un caso práctico futuras.

Esperamos que compartir las soluciones a algunos de los desafíos más grandes que teníamos durante la producción es útil para otros desarrolladores y que está lleno de inspiración para utilizar algunas de estas técnicas para crear sus propias experiencias envolventes para HoloLens. (Y si, asegúrese de que comparta con nosotros en el [foro de HoloLens App Development](https://forums.hololens.com/)!)

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> es un desarrollador sénior que aprendió más acerca de las plataformas de cámara y reproducción de vídeo de pensó que sea posible de trabajando HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny torcidas</b> es un artista de vídeo que asegurado de que su viaje a través de Roma fue como sin errores como sea posible.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> es un diseñador de Audio y asegurado de que puede experimentar el soundscape de cada destino visita, incluso cuando retroceder en el tiempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> es un Director de diseño que investigado y scouted ubicaciones, crea planes de viajes y dirige la grabación en el sitio.</td>
</tr>
</table>



## <a name="see-also"></a>Vea también
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
