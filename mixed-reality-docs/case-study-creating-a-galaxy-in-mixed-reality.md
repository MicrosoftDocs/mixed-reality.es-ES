---
title: 'Caso práctico: creación de una galaxia en una realidad mixta'
description: Antes de que se enviara a Microsoft HoloLens, hemos preguntado a nuestra comunidad de desarrolladores qué tipo de aplicación les gustaría ver una compilación de equipo interna con experiencia para el nuevo dispositivo. Se comparten más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea denominada "explorador de Galaxy".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, compartir ideas, caso práctico
ms.openlocfilehash: 696662eb92371708389f8a128dcee6a61acf1816
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436881"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Caso práctico: creación de una galaxia en una realidad mixta

Antes de que se enviara a Microsoft HoloLens, hemos preguntado a nuestra comunidad de desarrolladores qué tipo de aplicación les gustaría ver una compilación de equipo interna con experiencia para el nuevo dispositivo. Se comparten más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea denominada [Galaxy Explorer](galaxy-explorer.md).

Andy Zibits, el director de arte del proyecto y Karim Luccin, el ingeniero de gráficos del equipo, habla sobre el esfuerzo colaborativo entre arte e ingeniería que llevó a la creación de una representación precisa e interactiva de la forma láctea de Galaxy en el explorador de Galaxy.

## <a name="the-tech"></a>La tecnología

[Nuestro equipo](galaxy-explorer.md#meet-the-team) , compuesto por dos diseñadores, tres desarrolladores, cuatro artistas, un productor y un evaluador, tenía seis semanas para compilar una aplicación totalmente funcional que permitiría a los usuarios obtener información sobre la inmensaidad y la belleza de nuestra forma de ordeño.

Queríamos sacar el máximo partido de la capacidad de HoloLens para representar objetos 3D directamente en tu espacio de vida, por lo que decidimos que queríamos crear una galaxia de aspecto realista en la que los usuarios pudieran hacer zoom para ampliar y ver los estrellas individuales, cada uno con sus propias trayectorias. .

En la primera semana de desarrollo, surgimos con unos pocos objetivos para nuestra representación de la forma láctea de Galaxy: era necesario tener una profundidad, un movimiento y un volumétrico (lleno de estrellas) que le ayuden a crear la forma de la galaxia.

El problema con la creación de una galaxia animada que tenía miles de millones de estrellas era que el número de elementos únicos que es necesario actualizar sería demasiado grande por fotograma para que HoloLens se animase con la CPU. Nuestra solución ha participado en una combinación compleja de arte y ciencia.

## <a name="behind-the-scenes"></a>En segundo plano

Para que los usuarios puedan explorar estrellas individuales, el primer paso era averiguar cuántas partículas se podían representar a la vez.

### <a name="rendering-particles"></a>Representar objetos

Las CPU actuales son ideales para procesar tareas en serie y hasta algunas tareas paralelas a la vez (en función de la cantidad de núcleos que tengan), pero las GPU son mucho más eficaces en el procesamiento de miles de operaciones en paralelo. Sin embargo, dado que normalmente no comparten la misma memoria que la CPU, el intercambio de datos entre < de CPU > GPU puede convertirse rápidamente en un cuello de botella. Nuestra solución era crear una galaxia en la GPU y debía vivir completamente en la GPU.

Iniciamos pruebas de esfuerzo con miles de objetos de punto en distintos patrones. Esto nos permitió obtener la galaxia en HoloLens para ver lo que funcionó y lo que no.

### <a name="creating-the-position-of-the-stars"></a>Crear la posición de las estrellas

Uno de nuestros miembros del equipo ya ha escrito C# el código que generaría estrellas en su posición inicial. Las estrellas se encuentran en una elipse y su posición puede describirse mediante (**curveOffset**, **ellipseSize**, **elevation**), donde **curveOffset** es el ángulo de la estrella a lo largo de la elipse, **ellipseSize** es la dimensión de la elipse. a lo largo de X y Z, y eleva la elevación adecuada de la estrella dentro de la galaxia. Por lo tanto, podemos crear un búfer ([ComputeBuffer de Unity](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que se inicializaría con cada atributo de estrella y lo enviaría en la GPU donde residiría para el resto de la experiencia. Para dibujar este búfer, usamos [DrawProcedural de Unity](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , que permite ejecutar un sombreador (código en una GPU) en un conjunto arbitrario de puntos sin tener una malla real que represente la galaxia:

**CPU**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Comenzamos con patrones circulares sin procesar con miles de partículas. Esto nos dio la prueba de que necesitábamos que podamos administrar muchas partículas y ejecutarla a velocidades de rendimiento, pero no estamos satisfecho con la forma general de Galaxy. Para mejorar la forma, se intentaron varios patrones y sistemas de partículas con rotación. Estarían en primer lugar, ya que el número de partículas y el rendimiento se han mantenido coherentes, pero la forma se ha interrumpido cerca del centro y las estrellas no eran realistas. Necesitábamos una emisión que nos permitiera manipular el tiempo y hacer que las partículas se muevan de forma realista, lo que se repite cada vez más cerca del centro de la galaxia.

![Se han intentado varios patrones y sistemas de partículas que se han girado, como estos.](images/galaxy-patterns-500px.png)

Se han intentado varios patrones y sistemas de partículas que se han girado, como estos.

Nuestro equipo realizó una investigación sobre la manera en que galaxiesó la función y creamos un sistema de partículas personalizado específicamente para la galaxia, de modo que podríamos trasladar las partículas a las elipses en función de "[teoría de ola de densidad](https://en.wikipedia.org/wiki/Density_wave_theory)", que theorizes que los brazos de una galaxia son áreas mayor densidad, pero en flujo constante, como un atasco de tráfico. Parece estable y sólido, pero en realidad las estrellas están pasando y salen de los brazos a medida que se mueven a lo largo de sus puntos suspensivos respectivos. En nuestro sistema, los objetos nunca existen en la CPU, por lo que se generan las tarjetas y se orientan todas en la GPU, por lo que todo el sistema es simplemente el estado inicial + hora. Progresaría de la siguiente manera:

![Progresión del sistema de partículas con representación de GPU](images/spiral-galaxy-arms-500px.jpg)

Progresión del sistema de partículas con representación de GPU


Una vez que se agregan las elipses suficientes y se establecen para rotar, el Galaxies comenzó a formar "armas" donde converge el movimiento de estrellas. El espaciado de las estrellas a lo largo de cada trazado elíptico se proporcionó cierta aleatoriedad y cada estrella tenía un bit de aleatoriedad posicional agregado. Esto creó una distribución mucho más natural del movimiento de estrella y la forma de ARM. Por último, se ha agregado la capacidad de controlar el color en función de la distancia desde el centro.

### <a name="creating-the-motion-of-the-stars"></a>Crear el movimiento de las estrellas

Para animar el movimiento de estrella general, era necesario agregar un ángulo constante para cada fotograma y hacer que las estrellas se muevan a lo largo de sus puntos suspensivos en una velocidad radial constante. Esta es la razón principal para usar **curveOffset**. Esto no es técnicamente correcto, ya que las estrellas se moverán más rápido a lo largo de los extremos largos de las elipses, pero el movimiento general se considera adecuado.

![Las estrellas se mueven más rápido en el arco largo, más lentamente en los bordes.](images/ellipse-movement.jpg)

Las estrellas se mueven más rápido en el arco largo, más lentamente en los bordes.


Con eso, cada estrella se describe por completo (**curveOffset**, **ellipseSize**, **elevación**, **Age**), donde **Age** es una acumulación del tiempo total transcurrido desde que se cargó la escena.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

Esto nos permitió generar decenas de miles de estrellas una vez al principio de la aplicación y, a continuación, animamos un conjunto único de estrellas a lo largo de las curvas establecidas. Dado que todo está en la GPU, el sistema puede animar todas las estrellas en paralelo sin costo alguno en la CPU.

![Este es su aspecto cuando se dibujan cuatros blancos.](images/drawing-white-quads-300px.jpg)

Este es su aspecto cuando se dibujan cuatros blancos.



Para que cada cuatro se enfrente a la cámara, usamos un sombreador de geometría para transformar cada posición en estrella en un rectángulo 2D de la pantalla que contendrá la textura en estrella.

![Diamantes en lugar de cuádruples.](images/drawing-white-quads-300px.jpg)

Diamantes en lugar de cuádruples.


Como queríamos limitar el exceso (el número de veces que se procesará un píxel) en la medida de lo posible, giramos nuestras cuádruples para que tuvieran menos superposición.

### <a name="adding-clouds"></a>Agregar nubes

Hay muchas maneras de obtener una sensación volumétrica con partículas: desde Ray, desde el interior de un volumen hasta el dibujo de tantas partículas como sea posible para simular una nube. El radio en tiempo real de marzo iba a ser demasiado caro y difícil de crear, por lo que primero hemos intentado crear un sistema impostor con un método para representar bosques en juegos, con una gran cantidad de imágenes 2D de árboles orientados a la cámara. Cuando hacemos esto en un juego, podemos hacer que las texturas de los árboles se representen a partir de una cámara que gira, guardar todas esas imágenes y en tiempo de ejecución para cada tarjeta de la cartelera, seleccionar la imagen que coincida con la dirección de la vista. Esto no funciona tan bien cuando las imágenes son hologramas. La diferencia entre el ojo izquierdo y el ojo derecho lo hace para que se necesite una resolución mucho más alta, o bien que se parezca plana, con alias o repetitivo.

En el segundo intento, intentamos tener tantas partículas como sea posible. Los mejores objetos visuales se logran cuando se dibujan partículas y se desenfocaron antes de agregarlas a la escena. Los problemas típicos de ese enfoque estaban relacionados con el número de objetos que se podían dibujar en un momento dado y el área de la pantalla que se encontraban mientras se sigue manteniendo 60fps. Desenfocar la imagen resultante para obtener esta nube suele ser una operación muy costosa.

![Sin textura, este es el aspecto de las nubes con una opacidad del 2%.](images/clouds-without-texture-300px.jpg)

Sin textura, este es el aspecto de las nubes con una opacidad del 2%.



Ser aditivos y tener una gran cantidad de ellos significa que tendremos varias cuádruples en la parte superior entre sí, con un sombreado repetido del mismo píxel. En el centro de la galaxia, el mismo píxel tiene cientos de cuádruples unos de otros, y esto tenía un costo enorme cuando se realizaba una pantalla completa.

Realizar nubes de pantalla completa e intentar desenfocarlos habría sido una mala idea, por lo que, en su lugar, decidimos dejar que el hardware hiciera el trabajo.

### <a name="a-bit-of-context-first"></a>Un bit de contexto primero

Cuando se usan texturas en un juego, el tamaño de la textura rara vez coincidirá con el área en la que se desea utilizar, pero se puede usar un tipo diferente de filtrado de textura para que la tarjeta gráfica se interpole el color que se desea de los píxeles de la textura ([filtrado de textura](https://msdn.microsoft.com/library/dn642451.aspx)). El filtrado que nos interesa es [bilineal Filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) , que calculará el valor de cualquier píxel usando los 4 vecinos más cercanos.

![Original antes del filtrado](images/texture-1.png)

![Resultado después del filtrado](images/texture-2.png)

Con esta propiedad, vemos que cada vez que se intenta dibujar una textura en un área dos veces como grande, se desenfoca el resultado.

En lugar de representarla en una pantalla completa y perder esos precioso milisegundos que podríamos gastar en algo más, representamos en una versión pequeña de la pantalla. Después, copiando esta textura y ajustándola en un factor de 2 varias veces, volveremos a la pantalla completa al desenfocar el contenido del proceso.

![X3 vuelve a escalar a la resolución completa.](images/galaxy-resolutions-300px.png)

X3 vuelve a escalar a la resolución completa.



Esto nos permitió obtener la parte de la nube con solo una fracción del costo original. En lugar de agregar nubes en la resolución completa, solo dibujamos 1/64TH de los píxeles y simplemente ajustamos la textura a la resolución completa.

![Izquierda, con una escala de 1/8 a resolución completa; y a la derecha, con una capacidad de 3 escalado con potencia de 2.](images/stars-upscaled-300px.jpg)

Izquierda, con una escala de 1/8 a resolución completa; y a la derecha, con una capacidad de 3 escalado con potencia de 2.


Tenga en cuenta que el intento de pasar de 1/64TH del tamaño al tamaño completo en un solo aspecto sería completamente diferente, ya que la tarjeta gráfica seguiría usando 4 píxeles en nuestra configuración para sombrear un área más grande y los artefactos comenzarán a aparecer.

A continuación, si agregamos estrellas de resolución completa con tarjetas más pequeñas, obtenemos el completo Galaxy:

![Resultado casi final de la representación de Galaxy con estrellas de resolución completa](images/full-galaxy-500px.png)

Una vez que se encontraba el buen seguimiento con la forma, agregamos una capa de nubes, cambiaban los puntos temporales por los que dibujamos en Photoshop y agregamos un color adicional. El resultado era una forma láctea de Galaxy que nuestros equipos de arte e ingeniería nos sentían bien y cumplían nuestros objetivos de tener profundidad, volumen y movimiento, todo ello sin agotar la CPU.

![La forma láctea final de Galaxy en 3D.](images/final-galaxy-500px.jpg)

La forma láctea final de Galaxy en 3D.


### <a name="more-to-explore"></a>Más información para explorar

Hemos abierto el código para la aplicación Galaxy Explorer y lo hemos puesto a disposición de los desarrolladores en [GitHub](https://github.com/Microsoft/GalaxyExplorer) .

¿Está interesado en encontrar más información sobre el proceso de desarrollo de Galaxy Explorer? Eche un vistazo a las últimas actualizaciones del proyecto en el [canal de YouTube de Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> es un ingeniero de software y entusiasta de los objetos visuales. Fue el ingeniero de gráficos de Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> es un líder de vanguardia y un entusiasta de espacio que administraba el equipo de modelado 3D para Galaxy Explorer y fought para incluso más partículas.</td>
</tr>
</table>


## <a name="see-also"></a>Consulta también
* [Explorador de Galaxy en GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Actualizaciones de proyectos del explorador de Galaxy en YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
