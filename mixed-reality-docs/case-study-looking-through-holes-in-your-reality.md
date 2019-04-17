---
title: 'Caso práctico: examinar los huecos en la realidad'
description: Este caso práctico se explica cómo implementar el efecto de "ventana mágicas" en HoloLens, lo que permite al usuario ver detrás de las paredes, debajo del piso y en aperturas virtuales dentro de su entorno real.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, ventana mágica, paralaje
ms.openlocfilehash: 0c0828a6ebbefdcff7f0a66f48469007c5c532df
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600748"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>Caso práctico: examinar los huecos en la realidad

Cuando las personas piensan en realidad mixta y qué puede hacer con Microsoft HoloLens, suelen quedarse a preguntas como "¿qué objetos puedo agregar a mi salón?" o "¿Qué puedo capa encima de mi espacio?" Gustaría destacar otra área que se puede considerar que, básicamente un truco de magia, con la misma tecnología para buscar en o a través de objetos físicos real que le rodea.

## <a name="the-tech"></a>La tecnología

Si ha luchó alienígenas, ya que la interrupción a través de las paredes en  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, desbloquear una pared segura en  **[fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)**, o hayan afortunado Para ver el hangar la infinito en el  **[Halo 5 experiencia en E3 en 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, a continuación, ha visto lo que estoy hablando. Según su imaginación, se puede utilizar este truco visual para colocar los agujeros temporales en su tabiques u ocultar mundos bajo un floorboard suelto.

![RoboRaid agrega canalizaciones tridimensionales y otra estructura de las paredes, visibles solo a través de agujeros que supere el invaders.](images/roboraid-640px.png)

RoboRaid agrega canalizaciones tridimensionales y otra estructura de las paredes, visibles solo a través de agujeros que supere el invaders.

Una aplicación mediante uno de estos hologramas únicos en HoloLens, puede proporcionar la ilusión de contenido detrás de las paredes o a través de su espacio de la misma manera que la realidad se presenta a través de una ventana real. Mover usted mismo izquierda, y puede ver cualquier cosa que esté en el lado derecho. Acercarse y puede ver una explicación más detallada de todo el contenido. La principal diferencia es que agujeros real permiten a través, mientras que el suelo paralelo no le permitirá trepar a través de ese contenido holográfica mágica. (Agregaré una tarea al trabajo pendiente).

## <a name="behind-the-scenes"></a>En segundo plano

Este truco es una combinación de dos efectos. En primer lugar, holographic contenido está anclado a la del mundo mediante "delimitadores espaciales". Usar delimitadores para poner el contenido "bloqueada world" significa que lo que está viendo no visualmente desvíen fuera de los objetos físicos cerca de él, incluso cuando se mueve o el sistema de asignación espacial subyacente actualiza su modelo en 3D de la sala.

En segundo lugar, ese holográfico contenido tiene limitaciones visuales para un espacio muy específico, para que pueda ver solo a través de la vulnerabilidad en la realidad. Hace falta que oclusión necesario adelantarse a través de un agujero lógico, la ventana o la puerta, que vende el truco. Sin algo bloquea la mayor parte de la vista, una ruptura en el espacio para una dimensión jurásico secreta simplemente podría parecerse a un dinosaurio mal colocado.

![Esto no es una captura de pantalla real, sino una ilustración de cómo se ve el secreto Underword de MR Fundamentos 101 en HoloLens. No se muestre el alojamiento de color negro, pero puede ver el contenido a través de un "agujero" virtual. (Al buscar a través de un dispositivo real, el suelo parece incluso más desaparecen porque con los ojos centran a una distancia más como si no es así incluso.)](images/origamiholecomposited-640px.png)

Esto no es una captura de pantalla real, sino una ilustración de cómo el secreto Underword desde el [MR Fundamentos 101](holograms-101.md) busca en HoloLens. No se muestre el alojamiento de color negro, pero puede ver el contenido a través de un "agujero" virtual. (Al buscar a través de un dispositivo real, el suelo parece incluso más desaparecen porque con los ojos centran a una distancia más como si no es así incluso.)

### <a name="world-locking-holographic-content"></a>Contenido holográfica mundial de bloqueo

En Unity, causando holográfica contenido a permanecer bloqueado por el mundo es tan fácil como agregar un componente WorldAnchor:

```
myObject.AddComponent<WorldAnchor>();
```

El componente WorldAnchor constantemente ajustará la posición y rotación de su GameObject (y, por tanto, nada más en ese objeto en la jerarquía) para mantener estable relativa a los objetos físicos cercanos. Al crear el contenido, cree de manera que el pivote de la raíz del objeto está centrado en este hueco virtual. (Si es dinámica del objeto en la pared, serán mucho más notables sus pequeños ajustes en la posición y rotación y el agujero puede no ser muy estable).

### <a name="occluding-everything-but-the-virtual-hole"></a>Occluding todo excepto el agujero virtual

Hay varias maneras de bloquear la vista a lo que está oculto en las paredes de manera selectiva. Lo más sencillo aprovecha el hecho de que HoloLens utiliza una pantalla aditiva, lo que significa que los objetos completamente negros aparecen invisibles. Puede hacerlo en Unity sin tener que realizar ningún sombreador especial o materiales trucos, cree un material negro y asignarla a un objeto que cuadros en el contenido. Si no quiere realizar el modelado 3D, use un puñado de los objetos predeterminados que cuádruple y superpone un poco. Hay una serie de desventajas de este enfoque, pero es la manera más rápida de obtener algo funcione y obtención de baja fidelidad de prueba de funcionamiento de concepto es genial, incluso si sospecha que puede querer refactorícelo más adelante.

Una desventaja importante para el enfoque de "caja negra" anterior es que no fotografiar bien. Aunque el efecto sería perfecto a través de la presentación de HoloLens, las capturas de pantalla que seguir mostrará un objeto de color negro grande en lugar de lo que queda de la pared o un piso. La razón de esto es que el hologramas compuestos de hardware y las capturas de pantalla físicas y la realidad, forma diferente. Vamos a desviar por un momento en un cálculo matemático falso...

*¡Alerta falsa matemáticas! Estos números y fórmulas están diseñadas para ilustrar un punto, tiene que tener algún tipo de métrica de precisión.*

Lo que se ve a través de HoloLens:

```
( Reality * darkening_amount ) + Holograms
```

Lo que ve en vídeo y capturas de pantalla:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

En inglés: Lo que ve a través de HoloLens es una sencilla combinación de realidad oscura (como a través de gafas de sol) y cualquier hologramas la aplicación que desea mostrar. Pero al realizar una captura de pantalla, la imagen de la cámara se mezcla con hologramas de la aplicación según el valor de transparencia por píxel.

Una manera de solucionar este problema es cambiar el material de "caja negra" para que sólo escribir en el búfer de profundidad y ordenar con todos los materiales opacos. Para obtener un ejemplo de esto, consulte el [WindowOcclusion.shader archivo en el MixedRealityToolkit en GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader). Las líneas correspondientes se copian aquí:

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(Tenga en cuenta el "desplazamiento de 50, 100" línea consiste en tratar con problemas no relacionados, por lo que probablemente tendría sentido dejar que.)

Implementar un material de oclusión invisible así permitirá que la aplicación dibujar un cuadro que parece correcto en la pantalla y capturas de pantalla de realidad mixta. Para los puntos de bonificación, puede intentar mejorar el rendimiento de ese cuadro aún más haciendo cosas inteligentes para dibujar incluso menos píxeles invisibles, pero que realmente puede obtener en el hierbas y normalmente no será necesario.

![Este es el secreto Underword de MR Fundamentos 101 Unity dibuja, excepto las partes del cuadro occluding externas. Tenga en cuenta que el pivote de la Underword está en el centro del cuadro, lo que ayuda a mantener el agujero como estable como sea posible en relación con su espacio real.](images/underworld-occluded-640px.png)

Este es el secreto Underword desde [MR Fundamentos 101](holograms-101.md) como Unity dibuja, excepto las partes del cuadro occluding externas. Tenga en cuenta que el pivote de la Underword está en el centro del cuadro, lo que ayuda a mantener el agujero como estable como sea posible en relación con su espacio real.

## <a name="do-it-yourself"></a>Hágalo usted mismo

Tiene un HoloLens y desea probar el efecto para usted mismo? Lo más fácil hacer (no se requiere código) es instalar la aplicación de visor 3D gratuita y, a continuación, cargar el [archivo the.fbx de descarga que he proporcionado en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) para ver un modelo de olla de flor en la sala. Cargarlo en HoloLens, y puede ver el efecto en el trabajo. Cuando esté delante del modelo, solo puede ver en el pequeño orificio: todo lo demás es invisible. Examine el modelo desde cualquier otro lado y desaparecer por completo. ¡Usar el movimiento, giro y escala de controles del Visor de 3D para colocar el agujero virtual contra cualquier superficie vertical que puede pensar para generar algunas ideas!

![Ver este modelo en el editor de Unity, se mostrará un cuadro negro grande en torno a la flowerpot. En HoloLens, desaparece el cuadro, dar forma a un efecto de ventana mágica.](images/magicwindowflowerpotineditor.png)

Ver este modelo en el editor de Unity, se mostrará un cuadro negro grande en torno a la flowerpot. En HoloLens, desaparece el cuadro, dar forma a un efecto de ventana mágica.

Si desea compilar una aplicación que usa esta técnica, consulte el [MR Fundamentos 101 tutorial](holograms-101.md) en el [Mixed Reality Academy](academy.md). Capítulo 7 termina con un aumento vertiginoso en el suelo que revela un Underword oculto (como se muestra en la imagen anterior). ¿Quién ha dicho tutoriales tenían que ser aburrido?

Aquí le presentamos algunas ideas de donde puede tomar esta idea siguiente:
* Pensar en maneras de hacer que el contenido en el orificio virtual interactiva. Permitir que los usuarios tener algún impacto más allá de sus paredes puede mejorar realmente el sentido de extrañar que puede proporcionar este truco.
* Pensar en maneras de ver a través de los objetos a áreas conocidos. ¿Por ejemplo, cómo puede se coloca un "agujero" holográfico en la mesa de café y ven el piso situado debajo de él?

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>Ingeniero de Software senior @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Conceptos básicos de MR 101: Proyecto completo con el dispositivo](holograms-101.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Asignación espacial](spatial-mapping.md)
