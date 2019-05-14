---
title: 'Caso práctico: creación de una galaxia en realidad mixta'
description: Antes de enviar Microsoft HoloLens, pedimos a nuestra comunidad de desarrolladores a qué tipo de aplicación les gustaría ver un equipo interno con experiencia de compilación para el nuevo dispositivo. Se compartieron más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea denominada "Explorador de Galaxy".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Explorador de Galaxy, HoloLens, Windows Mixed Reality, comparta sus ideas, caso práctico
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605730"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Caso práctico: creación de una galaxia en realidad mixta

Antes de enviar Microsoft HoloLens, pedimos a nuestra comunidad de desarrolladores a qué tipo de aplicación les gustaría ver un equipo interno con experiencia de compilación para el nuevo dispositivo. Se compartieron más de 5000 ideas y, después de un sondeo de Twitter de 24 horas, el ganador era una idea llamada [Explorer Galaxy](galaxy-explorer.md).

Andy Zibits, el responsable de material gráfico en el proyecto y Karim Luccin, ingeniero de gráficos del equipo, hablar sobre el esfuerzo de colaboración entre imágenes y de ingeniería que dieron lugar a la creación de una representación precisa interactiva de galaxy vía láctea en el Explorador de Galaxy.

## <a name="the-tech"></a>The Tech

[Nuestro equipo](galaxy-explorer.md#meet-the-team) : realizar copia de dos diseñadores, tres desarrolladores, cuatro artistas, un productor y un evaluador, tenía seis semanas para compilar una aplicación totalmente funcional que le permite que la gente conozca y explore la gran amplitud y la belleza de nuestro Galaxy vía láctea.

Queríamos aprovechar al máximo la capacidad de representar objetos 3D directamente en su espacio vital, por lo que decidimos que queríamos crear un realista galaxy atractivo donde las personas sería capaz de acercar close y ver estrellas individuales, cada uno en sus propia trayectorias de HoloLens .

En la primera semana del desarrollo, dimos con unos pocos objetivos para la representación de Galaxy vía láctea: Necesita para tener profundidad, el movimiento y el funcionamiento volumétrico: completo de estrellas que ayudaría a crear la forma de galaxy.

El problema con la creación de un galaxy animado que tuviera miles de millones de estrellas fue que la mera cantidad de elementos únicos que requieren actualización sería demasiado grande por fotograma para HoloLens se va a animar el uso de la CPU. Nuestra solución implicaba una mezcla compleja de arte y conocimientos teóricos.

## <a name="behind-the-scenes"></a>En segundo plano

Para permitir a los usuarios explorar estrellas individuales, nuestro primer paso fue averiguar cuántos objetos representamos podríamos a la vez.

### <a name="rendering-particles"></a>Objetos de representación

CPU actuales son excelentes para procesar tareas en serie y un máximo de algunas tareas en paralelo a la vez (dependiendo de cuántos núcleos tengan), pero las GPU son mucho más eficaces para procesar miles de operaciones en paralelo. Sin embargo, porque normalmente no comparten la misma memoria que la CPU, el intercambio de datos entre CPU <> GPU puede volverse rápidamente un cuello de botella. Nuestra solución fue hacer que un galaxy en la GPU y tenía que residen completamente en la GPU.

Comenzamos a las pruebas de esfuerzo con miles de partículas de punto en varios modelos. Esto nos permitió obtener galaxy en HoloLens para ver lo que funcionó y lo que no.

### <a name="creating-the-position-of-the-stars"></a>Creación de la posición de las estrellas

Uno de nuestros miembros del equipo ya había desarrollado el C# código que generaría estrellas en su posición inicial. Las estrellas se encuentran en una elipse y se puede describir su posición (**curveOffset**, **ellipseSize**, **elevación**) donde **curveOffset**es el ángulo de la estrella a lo largo de la elipse, **ellipseSize** es la dimensión de la elipse a lo largo de X y Z y la elevación la elevación de la estrella dentro de galaxy adecuada. Por lo tanto, podemos crear un búfer ([ComputeBuffer de Unity](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) que se inicializaría a cada atributo de estrella y enviarlo en la GPU donde sería definitivamente durante el resto de la experiencia. Para dibujar este búfer, usamos [DrawProcedural de Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) que permite ejecutar un sombreador (código de una GPU) en un conjunto arbitrario de puntos sin necesidad de una malla real que representa el galaxy:

**CPU:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**GPU:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Comenzamos con patrones circulares sin procesar con miles de partículas. Esto nos dio la prueba que necesitábamos que podríamos administrar muchos objetos y ejecutarla a velocidades de alto rendimiento, pero no se ha satisfechos con la forma general de galaxy. Para mejorar la forma, hemos intentado distintos patrones y sistemas de partículas con una rotación. Se trataba inicialmente prometedor porque permanecido coherente, el número de objetos y el rendimiento, pero la forma infringió cerca del centro y estaban emitiendo las estrellas aparentemente sea lo que no era realista. Necesitábamos una emisión que nos permitiría manipular tiempo y que las partículas mover de manera realista, bucle cada vez más estrecha al centro de galaxy.

![Hemos intentado distintos patrones y sistemas de partículas que girar, como estos.](images/galaxy-patterns-500px.png)

Hemos intentado distintos patrones y sistemas de partículas que girar, como estos.

Nuestro equipo hizo investigar un poco acerca de la función de manera galaxias y hemos realizado un sistema de partículas personalizado específicamente para galaxy, por lo que podríamos pasar las partículas en función de un botón de puntos suspensivos "[teoría de onda de densidad](https://en.wikipedia.org/wiki/Density_wave_theory)," que theorizes que las ramas de un Galaxy son áreas de una mayor densidad pero inestable constante, como un atasco de tráfico. Parece sólido y estable, pero las estrellas se mueven realmente dentro y fuera de las ramas como mueva a lo largo de sus respectivos elipses. En nuestro sistema, las partículas nunca existen en la CPU, generamos las tarjetas y orientar a ellos en la GPU, por lo que todo el sistema es el estado inicial simplemente + tiempo. Lo progresado similar al siguiente:

![Progresión de sistema de partículas con la representación de GPU](images/spiral-galaxy-arms-500px.jpg)

Progresión de sistema de partículas con la representación de GPU


Una vez suficientes puntos suspensivos se agregan y se establecen para girar, las galaxias comenzaron a formulario donde el movimiento de estrellas converger "segmentos". El espaciado de las estrellas a lo largo de cada trazado elíptico recibió algo de aleatoriedad, y cada estrella tiene algo de aleatoriedad posicional agregado. Esto crea una distribución de aspecto mucho más natural de la forma de estrella, movimiento y arm. Por último, agregamos la capacidad al color de la unidad en función de la distancia desde el centro.

### <a name="creating-the-motion-of-the-stars"></a>Crear el movimiento de las estrellas

Para animar el movimiento de estrella general, se necesita para agregar un ángulo constante para cada fotograma y obtener estrellas moverse a lo largo de los puntos suspensivos a una velocidad constante radial. Esta es la razón principal para usar **curveOffset**. Esto no es técnicamente correcta tal y como estrellas se moverá con mayor rapidez a los lados largo de los puntos suspensivos, pero el movimiento general consideramos buena.

![Estrellas más rápido pasar del arco largo, más lento en los bordes.](images/ellipse-movement.jpg)

Estrellas más rápido pasar del arco largo, más lento en los bordes.


Con esto, se describe detalladamente cada estrella por (**curveOffset**, **ellipseSize**, **elevación**, **Age**) donde **edad** es una acumulación del tiempo total que ha transcurrido desde que se cargó la escena.




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

Esto nos ha permitido generar decenas de miles de estrellas una vez al principio de la aplicación y, a continuación, se anima un conjunto de estrellas a lo largo de las curvas establecidas un. Puesto que todo está en la GPU, el sistema puede animar todas las estrellas en paralelo sin costo a la CPU.

![Este es su aspecto cuando cuadrantes blancos de dibujo.](images/drawing-white-quads-300px.jpg)

Este es su aspecto cuando cuadrantes blancos de dibujo.



Para hacer que la cámara cada cara cuádruple, hemos usado a un sombreador de geometría para transformar cada posición estrella a un rectángulo en la pantalla que contendrá la estrella textura 2D.

![Diamantes en lugar de cuadrantes.](images/drawing-white-quads-300px.jpg)

Diamantes en lugar de cuadrantes.


Dado que quisiéramos limitar el sobredibujo (número de veces que se procesará un píxel) tanto como sea posible, se giran nuestro cuadrantes para que se tengan menos superposiciones.

### <a name="adding-clouds"></a>Adición de nubes

Hay muchas maneras para hacerse una idea volumétrica con partículas — de ray marching dentro de un volumen para dibujar las partículas tantos como sea posible para simular una nube. Ray en tiempo real marching iba a ser demasiado costoso y difícil de autor, así que intentamos primero la creación de un sistema impostor mediante un método de bosques de representación en juegos, con una gran cantidad de imágenes en 2D de árboles orientado a la cámara. Al hacer esto en un juego, podemos tener las texturas de árboles que se procesan a partir de una cámara que gira en torno a y guarde todas esas imágenes en tiempo de ejecución para cada tarjeta cartelera, seleccione la imagen que coincide con la dirección de la vista. Esto no funciona tan bien cuando las imágenes son hologramas. La diferencia entre el ojo izquierdo y derecho ojo permiten que se necesita una resolución mucho mayor, o bien se ve plana, alias, o repetitivas.

En nuestro segundo intento, intentamos tener tantos objetos como sea posible. Se obtuvieron los objetos visuales mejor cuando nos aditivamente dibujó partículas y borrosa ellos antes de agregarlos a la escena. Los problemas típicos con ese enfoque eran objetos relacionados a cuántos nos podemos dibujar en una sola vez y cuánto pantalla área que cubierta manteniendo los 60fps. Desenfoque de la imagen resultante para obtener esta nube se siente normalmente era una operación muy costosa.

![Sin la textura, esto es lo que sería las nubes con 2% de opacidad.](images/clouds-without-texture-300px.jpg)

Sin la textura, esto es lo que sería las nubes con 2% de opacidad.



Que se va a aditivas y tener una gran cantidad de ellos significa que se tendría varios cuadrantes encima de otro, sombreado repetidamente el mismo píxel. En el centro de galaxy, el mismo píxel tiene cientos de cuadrantes uno sobre otro y esto tuvo un costo enorme cuando se realiza a pantalla completa.

Realizando las nubes de pantalla completa y tratando de les desenfoque habría sido una mala idea, por lo tanto, que hemos decidido permitir que el hardware de hacer el trabajo por nosotros.

### <a name="a-bit-of-context-first"></a>Un bit del contexto en primer lugar

Al usar las texturas en un juego el tamaño de la textura rara vez coincidirá con el área que deseamos utilizar en, pero podemos usar otro tipo de filtrado para obtener la tarjeta gráfica para interpolar el color que desee de los píxeles de la textura de textura ([Texture Filtering<C3/>).](https://msdn.microsoft.com/library/dn642451.aspx) El filtrado que nos interesa es [filtrado bilineal](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) que va a calcular el valor de cualquier píxel con el 4 de vecinos más cercanos.

![Original antes de filtrado](images/texture-1.png)

![Como resultado tras el filtrado](images/texture-2.png)

Con esta propiedad, vemos que cada vez que se intente dibujar una textura a un área dos veces más grandes, se desenfoca el resultado.

En lugar de representación a pantalla completa y perder los milisegundos preciosos que nos podríamos emplear en algo más, representamos a una versión pequeña de la pantalla. A continuación, copiando esta textura y ajuste en un factor de 2 varias veces, obtenemos a pantalla completa mientras el contenido en el proceso de desenfoque.

![x3 exclusiva a resolución completa.](images/galaxy-resolutions-300px.png)

x3 exclusiva a resolución completa.



Esto nos permitió obtener la parte de la nube con sólo una fracción del costo original. En lugar de agregar nubes en la resolución por completa, solo se paint 1/64 de los píxeles y tan solo ajustar la textura a resolución completa.

![Izquierda, con un lujoso de 1/8 a resolución completa; y, con 3 exclusiva con la potencia de 2.](images/stars-upscaled-300px.jpg)

Izquierda, con un lujoso de 1/8 a resolución completa; y, con 3 exclusiva con la potencia de 2.


Tenga en cuenta que intenta ir de 1/64 del tamaño al máximo tamaño en una sola operación tendría el aspecto completamente diferente, como la tarjeta gráfica seguiría usando 4 píxeles en nuestro programa de instalación para sombrear un área más grande y artefactos empiecen a aparecer.

A continuación, si se agregan las estrellas de resolución completa con tarjetas más pequeñas, obtenemos el galaxy completa:

![Cerca del resultado final de la representación de galaxy con estrellas de resolución completa](images/full-galaxy-500px.png)

Una vez que se estaban en el camino correcto con la forma, se agrega una capa de nubes, intercambiadas los puntos temporales con los se pinta en Photoshop y agregan algunos colores adicionales. El resultado fue una galaxia vía láctea nuestro material gráfico y tanto los equipos de ingeniería sentían estupendo y cumple nuestros objetivos de disponer de profundidad, el volumen y movimiento, todo sin recargar la CPU.

![Nuestro Galaxy vía láctea final en 3D.](images/final-galaxy-500px.jpg)

Nuestro Galaxy vía láctea final en 3D.


### <a name="more-to-explore"></a>Más para explorar

Hemos conseguido que esté disponible en y abierto el código de la aplicación de explorador Galaxy [GitHub](https://github.com/Microsoft/GalaxyExplorer) a los desarrolladores compilar.

¿Está interesado en obtener más información sobre el proceso de desarrollo para Galaxy Explorer? Consulte todas nuestras actualizaciones de proyecto anteriores en el [canal de YouTube de Microsoft HoloLens](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Luccin</b> es un ingeniero de Software y un entusiasta de los objetos visuales decorativo. Fue el ingeniero de gráficos para Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> es un entusiasta de arte Lead y el espacio que administra el equipo de modelado 3D para Galaxy Explorer y luchó de partículas aún más.</td>
</tr>
</table>


## <a name="see-also"></a>Vea también
* [Explorador de Galaxy en GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Actualizaciones del explorador de Galaxy de project en YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
