---
title: 'Caso práctico: búsqueda de agujeros en su realidad'
description: En este caso práctico se explica cómo implementar el efecto "Magic Window" en HoloLens, lo que permite al usuario ver detrás de las paredes, debajo del suelo, y en aperturas virtuales dentro de su entorno real.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, ventana mágica, Parallax
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873937"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Caso práctico: búsqueda de agujeros en su realidad

Cuando los usuarios piensan en la realidad mixta y lo que pueden hacer con Microsoft HoloLens, normalmente se adhieren a preguntas como "¿Qué objetos puedo agregar a mi habitación?". o "¿Qué puedo hacer en la capa de mi espacio?" Me gustaría resaltar otra área que puede considerar, esencialmente un truco mágico, con la misma tecnología para buscar en los objetos físicos reales o a través de ellos.

## <a name="the-tech"></a>La tecnología

Si ha fought a los extranjeros a medida que se desplazan por los muros de **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** , desbloquea un muro en **[fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)** o estaba lo suficientemente afortunado como para ver el UNSC de infinidad de hangar en la **[experiencia de Halo 5 en E3 en 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)** , entonces ha visto lo que me está hablando. En función de su imaginación, este truco visual se puede usar para colocar agujeros temporales en el prefabricado o para ocultar mundos en un Floorboard suelto.

![RoboRaid agrega canalizaciones tridimensionales y otras estructuras detrás de las paredes, solo visibles a través de los agujeros creados como los invadidores.](images/roboraid-640px.png)

RoboRaid agrega canalizaciones tridimensionales y otras estructuras detrás de las paredes, solo visibles a través de los agujeros creados como los invadidores.

Con uno de estos hologramas únicos en HoloLens, una aplicación puede proporcionar la ilusión de contenido detrás de las paredes o a través de su piso, de la misma forma que la realidad se presenta a través de una ventana real. Desplácese a la izquierda y puede ver lo que hay en el lado derecho. Póngase más cerca y podrá ver un poco más de todo. La principal diferencia es que los agujeros reales le permiten, mientras que el paralelo de piso no le permitirá alcanzar el contenido de este mágico. (Agregaré una tarea al trabajo pendiente).

## <a name="behind-the-scenes"></a>En segundo plano

Este truco es una combinación de dos efectos. En primer lugar, el contenido holográfica está anclado al mundo mediante "anclajes espaciales". El uso de delimitadores para hacer que el contenido esté "bloqueado en todo el mundo" significa que lo que busca no se aparta visualmente de los objetos físicos cerca de él, ni siquiera cuando se mueve o el sistema de asignación espacial subyacente actualiza su modelo 3D de su habitación.

En segundo lugar, el contenido holográfica está limitado visualmente a un espacio muy específico, por lo que solo puede ver a través del hueco en su realidad. Esa oclusión es necesaria para requerir el examen de un orificio lógico, una ventana o una puerta, lo que vende la baza. Si no hay algo que bloquee la mayor parte de la vista, una grieta en el espacio de una dimensión Jurassic secreta podría parecerse a un dinosaurio mal colocado.

![No se trata de una captura de pantalla real, sino una ilustración de cómo el secreto mundial de MR Basics 101 busca en HoloLens. El alojamiento negro no se muestra, pero puede ver el contenido a través de un agujero virtual. (Al mirar a través de un dispositivo real, el piso parece desaparecer aún más porque sus ojos se centran en una distancia adicional como si no fuera así).](images/origamiholecomposited-640px.png)

No se trata de una captura de pantalla real, pero una ilustración de cómo el secreto mundial de los [conceptos básicos del MR 101](holograms-101.md) busca en HoloLens. El alojamiento negro no se muestra, pero puede ver el contenido a través de un agujero virtual. (Al mirar a través de un dispositivo real, el piso parece desaparecer aún más porque sus ojos se centran en una distancia adicional como si no fuera así).

### <a name="world-locking-holographic-content"></a>Contenido holográfica de bloqueo mundial

En Unity, hacer que el contenido Holographic se bloquee con un mundo tan sencillo como agregar un componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

El componente WorldAnchor ajustará constantemente la posición y la rotación de su GameObject (y, por tanto, todo lo demás que se encuentre bajo ese objeto en la jerarquía) para mantenerla estable en relación con los objetos físicos cercanos. Al crear el contenido, créelo de tal forma que el pivote de la raíz del objeto se Centre en este agujero virtual. (Si el pivote del objeto es profundo en la pared, sus ligeros ajustes en la posición y la rotación serán mucho más perceptibles, y es posible que el orificio no sea muy estable).

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding todo excepto el agujero virtual

Hay varias maneras de bloquear selectivamente la vista a lo que está oculto en las paredes. La más sencilla aprovecha el hecho de que HoloLens usa una presentación aditiva, lo que significa que los objetos completamente negros aparecen invisibles. Puede hacer esto en Unity sin realizar ningún sombreador especial ni trucos de material, solo tiene que crear un material negro y asignarlo a un objeto que aparezca en el contenido. Si no le gusta realizar el modelado 3D, solo tiene que usar una serie de objetos cuatro predeterminados y superponerlos ligeramente. Hay una serie de inconvenientes en este enfoque, pero es la forma más rápida de hacer algo operativo y obtener una prueba de concepto de baja fidelidad en el trabajo es excelente, incluso si sospecha que podría querer refactorizarla más adelante.

Uno de los principales inconvenientes del enfoque "Black Box" anterior es que no es un buen gráfico. Aunque el efecto puede ser perfecto a través de la presentación de HoloLens, las capturas de pantalla que realice mostrarán un objeto negro de gran tamaño en lugar de lo que queda de la pared o el piso. La razón es que el hardware físico y las capturas de pantallas componen hologramas y la realidad de manera diferente. Vamos a recorrer un momento en algunas matemáticas falsas...

*Alerta matemática falsa Estos números y fórmulas están diseñados para ilustrar un punto, no para un tipo de métricas precisas.*

Lo que se ve a través de HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Lo que se ve en las capturas de pantalla y en el vídeo:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

En Inglés: Lo que se ve a través de HoloLens es una combinación sencilla de realidad oscura (por ejemplo, a través de vidrios de la luna) y los hologramas que quiere mostrar la aplicación. Pero cuando se realiza una captura de pantalla, la imagen de la cámara se combina con los hologramas de la aplicación de acuerdo con el valor de transparencia por píxel.

Una manera de solucionar esto es cambiar el material de "Black Box" para escribir solo en el búfer de profundidad y ordenar con el resto de materiales opacos. Para obtener un ejemplo de esto, consulte el [archivo WindowOcclusion. Shader en MixedRealityToolkit en github](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Aquí se copian las líneas correspondientes:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Tenga en cuenta que la línea "desplazamiento 50, 100" es tratar con problemas no relacionados, por lo que probablemente tenga sentido dejarlo).

La implementación de un material de oclusión invisible como esto permitirá que la aplicación dibuje un cuadro que tenga un aspecto correcto en la pantalla y en capturas de pantalla de realidad mixta. En el caso de los puntos de bonificación, puede intentar mejorar el rendimiento de ese cuadro aún más si realiza acciones inteligentes para dibujar incluso menos píxeles invisibles, pero eso puede llegar realmente a las malas hierbas y, por lo general, no será necesario.

![Este es el secreto mundial de MR Basics 101 como Unity lo dibuja, excepto las partes externas del cuadro occluding. Tenga en cuenta que el pivote del mundo se encuentra en el centro del cuadro, lo que ayuda a mantener el agujero lo más estable posible con respecto a su piso real.](images/underworld-occluded-640px.png)

Este es el secreto mundial de [Mr basics 101](holograms-101.md) como Unity lo dibuja, excepto las partes externas del cuadro occluding. Tenga en cuenta que el pivote del mundo se encuentra en el centro del cuadro, lo que ayuda a mantener el agujero lo más estable posible con respecto a su piso real.

## <a name="do-it-yourself"></a>Hágalo usted mismo

¿Tiene HoloLens y desea probar el efecto? Lo más sencillo que puede hacer (sin necesidad de codificación) es instalar la aplicación gratuita de visor 3D y, a continuación, cargar el [archivo. FBX que he proporcionado en github](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) para ver un modelo de olla de flores en su habitación. Cárguelo en HoloLens y podrá ver la ilusión en el trabajo. Cuando esté delante del modelo, solo puede ver en el agujero pequeño; todo lo demás es invisible. Examine el modelo desde cualquier otro lado y desaparecerá por completo. Use los controles de movimiento, rotación y escala del visor 3D para colocar el agujero virtual en cualquier superficie vertical que pueda considerar para generar algunas ideas.

![Al ver este modelo en el editor de Unity, se mostrará un cuadro negro grande alrededor de FLOWERPOT. En HoloLens, el cuadro desaparece, lo que permite un efecto de ventana mágica.](images/magicwindowflowerpotineditor.png)

Al ver este modelo en el editor de Unity, se mostrará un cuadro negro grande alrededor de FLOWERPOT. En HoloLens, el cuadro desaparece, lo que permite un efecto de ventana mágica.

Si quiere compilar una aplicación que use esta técnica, consulte el tutorial de los [conceptos básicos de MR 101](holograms-101.md) en los tutoriales de [realidad mixta](tutorials.md). El capítulo 7 finaliza con una explosión en el piso que revela un submundo oculto (como se muestra arriba). ¿Quién ha comentado que los tutoriales debían ser aburridos?

A continuación se muestran algunas ideas de dónde puede adoptar esta idea:
* Piense en formas de hacer que el contenido dentro del agujero virtual sea interactivo. El hecho de que los usuarios tengan algún impacto más allá de sus muros puede mejorar realmente el sentido de la pregunta que este truco puede proporcionar.
* Piense en maneras de volver a ver los objetos en áreas conocidas. Por ejemplo, ¿cómo puede colocar un agujero holográfica en la mesa de café y ver su piso debajo?

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Ingeniero de software Senior@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [MR Basics 101: proyecto completo con dispositivo](holograms-101.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Asignación espacial](spatial-mapping.md)
