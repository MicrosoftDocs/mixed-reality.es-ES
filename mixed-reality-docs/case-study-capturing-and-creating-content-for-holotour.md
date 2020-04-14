---
title: 'Caso práctico: HoloTour'
description: HoloTour para Microsoft HoloLens proporciona paseos en 3D sobre las ubicaciones de iconos en todo el mundo. Este caso práctico le guiará a través del proceso de captura y creación del contenido que se usa para HoloTour.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: 59c3dffd48009aa792643ea27b59f8f6f85b64d7
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278193"
---
# <a name="case-study---holotour"></a>Caso práctico: HoloTour

HoloTour para Microsoft HoloLens proporciona paseos en 3D sobre las ubicaciones de iconos en todo el mundo. A medida que los diseñadores, artistas, productores, diseñadores de audio y desarrolladores que trabajan en este proyecto han descubierto, la creación de una representación 3D convincentemente real de una ubicación conocida toma una mezcla exclusiva de Wizardry de creatividad y tecnología. Este caso práctico le guiará a través del proceso de captura y creación del contenido que se usa para HoloTour.

## <a name="the-tech"></a>La tecnología

Con HoloTour, queríamos permitir que las personas visiten algunos de los destinos más increíbles del mundo, como la [de Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) en Perú o el día moderno [Piazza Navona](https://en.wikipedia.org/wiki/Piazza_Navona) en Italia, directamente desde sus propios salones. Nuestro equipo ha hecho el objetivo de HoloTour a "hacer que le parezca que está realmente ahí". La experiencia necesitaba ser más que solo imágenes o vídeos. Al aprovechar la exclusiva tecnología de visualización, seguimiento y audio de HoloLens, pensamos que podríamos realizar un transporte prácticamente en otro lugar. Tendremos que capturar los lugares, los sonidos y la geometría tridimensional de cada ubicación que visitamos y, a continuación, volver a crear eso en nuestra aplicación.

Para ello, necesitábamos una plataforma de una cámara 360 ° con captura de audio direccional. Era necesario capturar en una resolución extremadamente alta, de modo que el metraje tendría un aspecto nítido cuando se reproduzca en HoloLens y las cámaras deban estar colocadas cerca para minimizar los artefactos de Unión. Queríamos una cobertura esférica completa, no solo a lo largo del horizonte, sino también por encima y por debajo. La plataforma de pruebas también necesitaba ser portable, por lo que podríamos tomarla todo en todo el mundo. Hemos evaluado opciones fuera de las estantes disponibles y hemos hecho que simplemente no eran lo suficientemente buenos como para obtener nuestra visión, ya sea debido a la resolución, el costo o el tamaño. Si no pudimos encontrar una plataforma de cámaras que cumpliera nuestras necesidades, tendríamos que crear una.

### <a name="building-the-rig"></a>Compilar la plataforma de pruebas

La primera versión, procedente de cartón, velcro, cinta de conductos y 14 cámaras de GoPro, era algo que MacGyver habría orgulloso. Después de revisar todo desde soluciones de low-end a las plataformas de pruebas personalizadas, las cámaras de GoPro eran la mejor opción para nosotros porque eran pequeñas, económicas y tenían almacenamiento en memoria fácil de usar. El factor de forma pequeño era especialmente importante porque nos permitía colocar las cámaras bastante cerca: cuanto menor sea la distancia entre las cámaras, más pequeños serán los artefactos de Unión. Nuestra única disposición de cámara nos permitió obtener una cobertura de esfera completa *más* suficiente superposición para alinear las cámaras de forma inteligente y suavizar algunos artefactos durante el proceso de Unión.

Aprovechar las ventajas de las funcionalidades de [sonido espacial](spatial-sound.md) en HoloLens es fundamental para crear una experiencia de envolvente convincentemente real. Usamos una matriz de cuatro micrófonos situada bajo las cámaras del trípode, lo que captaría sonido de la ubicación de nuestra cámara en cuatro direcciones, lo que nos proporcionaría información suficiente para crear sonidos espaciales en nuestras escenas.

![Nuestra plataforma de cámaras 360 ° configurada para el rodaje fuera del Pantheon.](images/camera-pantheon-200px.png)

Nuestra plataforma de cámaras 360 ° configurada para el rodaje fuera del Pantheon. 


Probamos nuestra plataforma de homemade llevando a Rattlesnake saliente cerca de Seattle y Capturamos el escenario en la parte superior de la excursión. El resultado, aunque es mucho menos pulido que las ubicaciones que se ven en HoloTour hoy en día, nos proporciona la confianza de que el diseño de la plataforma era lo suficientemente bueno como para que se sienta lo que está realmente ahí.

Hemos actualizado nuestra plataforma de velcro y cartón a un alojamiento de cámara impreso en 3D y he comprado paquetes de baterías externos para las cámaras GoPro para simplificar la administración de la batería. Después, realizamos una prueba más exhaustiva, desplazamos a San Francisco para crear un paseo en miniatura de la costa de la ciudad y el puente de la puerta de Golden. Esta plataforma de cámara es lo que se usa para la mayoría de las capturas de las ubicaciones que se visitan en HoloTour.

![La plataforma de cámaras 360 ° filmada en Machu Picchu.](images/camera-machu-pichu-500px.png)

La plataforma de cámaras 360 ° filmada en Machu Picchu. 

## <a name="behind-the-scenes"></a>En segundo plano

Antes de filmarnos, es necesario averiguar qué ubicaciones deseamos incluir en nuestro paseo virtual. Roma era la primera ubicación en la que se pretendía enviar y queríamos obtenerla, por lo que decidimos realizar un viaje de Scout con antelación. Hemos enviado un equipo de seis personas, incluidos artistas, diseñadores y productores, para una visita en persona a los sitios que estamos considerando. El viaje tardó unos 9 días: 2,5 para viajar, el resto para filmarlos. (En el caso de Machu Picchu, hemos optado por no hacer un viaje de Scout, investigar de antemano y reservar unos días de búfer para filmarlos).

En Roma, el equipo tomó fotografías de cada área y anotó hechos interesantes, así como consideraciones prácticas, por ejemplo, en qué medida es desplazarse a cada lugar y lo difícil que sería filmar en película debido a los amontonamientos o las restricciones. Esto puede parecer una vacaciones, pero es mucho trabajo. Los días comenzaron pronto en la mañana y no se detendrían hasta la noche. Cada noche, se cargó el material de trabajo para el equipo en Seattle para revisarlo. 

![Nuestra tripulación de captura en Roma.](images/holotour-filming-crew-rome-500px.jpg) 

Nuestra tripulación de captura en Roma. 


Una vez finalizado el viaje del Scout, se realizó un plan final para el filmado real. Esto requiere una lista detallada de la ubicación en la que se iba a filmar, en qué día y en qué momento. Cada día es caro, por lo que estos viajes deben ser eficientes. Se han reservado guías y controladores en Roma para ayudarnos y usarse por completo todos los días desde antes del amanecer hasta después de la atardecer. Necesitamos obtener el mejor metraje posible para que se sienta que está realmente ahí.

### <a name="capturing-the-video"></a>Captura del vídeo

Realizar algunos sencillos pasos durante la captura puede hacer que el procesamiento posterior sea mucho más fácil. Por ejemplo, cada vez que une imágenes de varias cámaras, acaba con artefactos visuales porque cada cámara tiene una vista ligeramente diferente. Cuanto más se acerquen los objetos a la cámara, mayor será la diferencia entre las vistas y mayores serán los artefactos de Unión. Esta es una manera fácil de visualizar el problema: Sujete el dedo delante de su cara y examínelo con un solo ojo. Ahora cambie los ojos. Verá que el control Thumb parece moverse en relación con el fondo. Si mantiene el control lejos de su esfera y repite el experimento, parecerá que el control de posición se mueve menos. Ese movimiento aparente es similar al de la Unión que nos enfrentamos: los ojos, al igual que las cámaras, no ven exactamente la misma imagen porque están separadas por un poco de distancia.

Dado que es mucho más fácil evitar los peores artefactos mientras se filman que para corregirlos en el procesamiento posterior, se intentó mantener a las personas y cosas lejos de la cámara en la espera de que se pudiera eliminar la necesidad de unir objetos. Mantener un gran desplazamiento alrededor de nuestra cámara era probablemente uno de los mayores desafíos que teníamos durante el rodaje y tuvimos que crear creatividad para que funcione. Trabajar con guías locales era una gran ayuda en la administración de amontonamientos, pero también encontramos que el uso de signos (y a veces pequeños conos o bolsas de Bean) para marcar el espacio de filmación era razonablemente eficaz, especialmente porque solo necesitábamos obtener una breve cantidad de material de trabajo en cada ubicación. A menudo, la mejor manera de obtener una buena captura era llegar a la primera vez por la mañana, antes de que la mayoría de las personas se hubieran mostrado.

Algunas otras técnicas de captura útiles provienen directamente de las prácticas de películas tradicionales. Por ejemplo, se ha usado una tarjeta de corrección de color en todas nuestras cámaras y se han capturado fotografías de referencia de texturas y objetos que podríamos necesitar más adelante. 

![Un corte aproximado de Machu Picchu que muestra la tarjeta de corrección de color.](images/rough-cut-machu-picchu-500px.png)

Un corte aproximado del material de Pantheon antes de la Unión.

### <a name="processing-the-video"></a>Procesamiento del vídeo

La captura del contenido de 360 ° es solo el primer paso; se necesita una gran cantidad de procesamiento para convertir el metraje de cámara sin procesar capturado en los recursos finales que se ven en HoloTour. Una vez que volvamos a casa, necesitábamos tomar el vídeo de 14 fuentes de cámara diferentes y convertirlo en un vídeo continuo con los artefactos mínimos. Nuestro equipo de arte usó una serie de herramientas para combinar y perfeccionar el metraje capturado y hemos desarrollado una canalización para optimizar el procesamiento tanto como sea posible. Se debía unir el metraje, corregir el color y, a continuación, componerlo para quitar elementos y artefactos que distraigan o para agregar bolsillos complementarios de la vida y el movimiento, todo ello con el objetivo de mejorar la sensación de que realmente está ahí.

![Un corte aproximado del material de Pantheon antes de la Unión.](images/rough-cut-pantheon-500px.png)

Un corte aproximado del material de Pantheon antes de la Unión. 


Para unir los vídeos, usamos una herramienta denominada [PTGui](https://www.ptgui.com/) y la integró en nuestra canalización de procesamiento. Como parte del procesamiento posterior se extrajeron los fotogramas de nuestros vídeos y se encontró un patrón de Unión que parecía adecuado para uno de esos fotogramas. A continuación, aplicamos ese patrón a un complemento personalizado que hemos escrito que permitió a nuestros artistas de vídeo ajustar y ajustar el patrón de unión directamente durante la composición en After Effects. 

![Captura de pantalla de PTGui que muestra el material de Pantheon de Unión.](images/stitching-tool-pantheon-500px.png)

Captura de pantalla de PTGui que muestra el material de Pantheon de Unión. 


### <a name="video-playback"></a>Reproducción de vídeo

Una vez completado el procesamiento del metraje, tenemos un vídeo sin problemas, pero es extraordinariamente grande, en torno a la resolución de 8K. La descodificación de vídeo es costosa y hay muy pocos equipos que pueden controlar un vídeo de 8 KB, por lo que el siguiente desafío era encontrar una manera de volver a reproducir este vídeo en HoloLens. Hemos desarrollado una serie de estrategias para evitar el costo de la descodificación y, al mismo tiempo, parece que el usuario estaba viendo todo el vídeo.

La optimización más sencilla es evitar descodificar partes del vídeo que no cambian mucho. Hemos escrito una herramienta para identificar áreas de cada escena que tienen poco o ningún movimiento. En esas regiones, se muestra una imagen estática en lugar de descodificar un vídeo en cada fotograma. Para que esto sea posible, se divide el vídeo masivo en fragmentos mucho más pequeños.

También nos hemos asegurado de que todos los píxeles que hemos descodificado se hayan usado de forma más eficaz. Hemos experimentado técnicas de compresión para reducir el tamaño del vídeo. Dividimos las regiones de vídeo según los polígonos de la geometría en la que se proyectaría; Hemos ajustado UVs y reempaquetado los vídeos en función de la cantidad de detalles que se incluyen en los distintos polígonos. El resultado de este trabajo es que lo que comenzó como un vídeo de 8k único se convirtió en muchos fragmentos que parecen casi ininteligibles hasta que se reproyectan correctamente en la escena. Para un desarrollador de juegos que comprenda la asignación de texturas y el empaquetado de UV, probablemente le resulte familiar. 

![Una vista completa de Pantheon antes de las optimizaciones.](images/pantheon-before-optimization-500px.png) 

Una vista completa de Pantheon antes de las optimizaciones. 


![La mitad derecha de Pantheon, procesada para la reproducción de vídeo.](images/pantheon-process-video-playback-500px.png) 

La mitad derecha de Pantheon, procesada para la reproducción de vídeo. 


![Ejemplo de una sola región de vídeo después de la optimización y el empaquetado.](images/single-video-region-after-optimization-500px.png) 

Ejemplo de una sola región de vídeo después de la optimización y el empaquetado. 


Otro truco que usamos era evitar descodificar el vídeo que no está viendo de forma activa. En HoloTour, solo puede ver parte de la escena completa en un momento dado. Solo descodificamos vídeos dentro o fuera del campo de vista (campo de vista). A medida que gira el cabezal, empezamos a reproducir las regiones del vídeo que se encuentran ahora en el campo de campo y dejan de reproducirse que ya no se encuentran en ella. La mayoría de las personas ni siquiera observarán que esto sucede, pero si lo hace rápidamente, verá que el vídeo tarda un segundo en iniciarse. mientras tanto, verá una imagen estática que luego se atenúa hasta el vídeo una vez que está lista.

Para que esta estrategia funcione, desarrollamos un gran sistema de reproducción de vídeo. Hemos optimizado el código de reproducción de bajo nivel para que la conmutación de vídeo sea extremadamente eficaz. Además, teníamos que codificar nuestros vídeos de una forma especial para que pueda cambiar rápidamente a cualquier vídeo en cualquier momento. Esta canalización de reproducción tardó una cantidad significativa de tiempo de desarrollo, por lo que la implementamos en fases. Comenzamos con un sistema más sencillo que era menos eficaz, pero permitían que los diseñadores y artistas trabajaran en la experiencia y lo mejoraran lentamente a un sistema de reproducción más robusto que nos permitió enviar en la barra de calidad final. Este sistema final tenía herramientas personalizadas que creamos en Unity para configurar el vídeo dentro de la escena y supervisar el motor de reproducción.

### <a name="recreating-near-space-objects-in-3d"></a>Volver a crear objetos cercanos a espacios en 3D

Los vídeos componen la mayor parte de lo que se ve en HoloTour, pero hay una serie de objetos 3D cercanos, como el pintado en Piazza Navona, la fuente fuera del Pantheon o el globo de aire caliente que se encuentra en las escenas aéreas. Estos objetos 3D son importantes porque la percepción de profundidad humana está muy bien cerca, pero no está muy bien. Podemos echar un vídeo a la distancia, pero para que los usuarios puedan desplazarse por su espacio y parezca que realmente están allí, los objetos cercanos necesitan profundidad. Esta técnica es similar a la del tipo de cosa que puede ver en un Museo de historial natural, que es una imagen de un diorama que tiene landscaping físicos, plantas y especímenes de animales en primer plano, pero recedes en un dibujo de mate con máscara inteligente en segundo plano.

Algunos objetos son simplemente activos 3D que se han creado y agregado a la escena para mejorar la experiencia. La pintura y el globo de aire activo entran en esta categoría porque no estaban presentes cuando se filmó. De forma similar a los recursos de juego, fueron creados por un artista 3D en nuestro equipo y con la textura adecuada. Se colocan en nuestras escenas cerca de donde se encuentra y el motor de juegos puede representarlas en las dos pantallas de HoloLens para que aparezcan como un objeto 3D.

Otros recursos, como la fuente fuera de Pantheon, son objetos reales que existen en las ubicaciones en las que estamos filmando el vídeo, pero para sacar estos objetos del vídeo y en 3D, tenemos que hacer una serie de cosas.

En primer lugar, necesitamos información adicional sobre cada objeto. Mientras está en la ubicación de filmación, nuestro equipo capturó una gran cantidad de material de referencia de estos objetos para que tengamos suficientes imágenes detalladas para volver a crear las texturas con precisión. El equipo también realizó un examen [Photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) , que construye un modelo 3D a partir de docenas de imágenes 2D, lo que nos proporciona un modelo aproximado del objeto en la escala perfecta.

A medida que procesamos el metraje, los objetos que se reemplazarán más adelante con una representación 3D se quitarán del vídeo. El recurso 3D se basa en el modelo Photogrammetry, pero los artistas lo limpian y simplifican. En algunos objetos, podemos usar partes del vídeo, como la textura de agua en la fuente, pero la mayor parte de la fuente es ahora un objeto 3D, lo que permite a los usuarios percibir la profundidad y desplazarse por ella en un espacio limitado en la experiencia. El hecho de que los objetos cercanos, como esto, se agregan en gran medida a la sensación de realismo y ayuda a los usuarios en la ubicación virtual. 

![Pantheon metraje con la fuente quitada. Se reemplazará por un activo 3D.](images/object-removal-pantheon-500px.png)

Pantheon metraje con la fuente quitada. Se reemplazará por un activo 3D.


## <a name="final-thoughts"></a>Opiniones finales

Obviamente, había más que crear este contenido de lo que se ha explicado aquí. Hay algunas escenas que nos gustaría denominarlas "perspectivas imposibles", como la conducción del globo de aire activo y la lucha Gladiator en el Colosseum, lo que supuso un enfoque más creativo. Los abordaremos en un caso práctico futuro.

Esperamos que el uso compartido de soluciones a algunos de los desafíos más importantes que teníamos durante la producción sea útil para otros desarrolladores y que esté inspirado en el uso de algunas de estas técnicas para crear sus propias experiencias envolventes para HoloLens. (Si lo hace, asegúrese de compartirlo con nosotros en el foro de [desarrollo de aplicaciones de HoloLens](https://forums.hololens.com/)).

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> es un Desarrollador Senior que ha aprendido más sobre las plataformas de cámara y la reproducción de vídeo de las que pensaba que podía trabajar en HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> es un artista de vídeo que nos ha asegurado de que su viaje a Roma sea lo más fácil posible.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> es un diseñador de audio que nos ha asegurado de que pudiera experimentar el soundscape de todos los destinos que visita, incluso cuando regresa al tiempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> es un director de diseño que investiga y dirige las ubicaciones, crea planes de viajes y filma en el sitio.</td>
</tr>
</table>



## <a name="see-also"></a>Vea también
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
