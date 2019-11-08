---
title: Apuntar y confirmar con las manos
description: Introducción al modelo de entrada de apuntar y confirmar
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, interacción, diseño, HoloLens, manos, lejos, apuntar y confirmar
ms.openlocfilehash: e454b7f26b402d5c168323762865d10f7feb8a17
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437647"
---
# <a name="point-and-commit-with-hands"></a>Apuntar y confirmar con las manos

Apuntar y confirmar con las manos es un modelo de entrada que permite a los usuarios seleccionar como destino, seleccionar y manipular contenidos 2D y objetos 3D que están fuera de su alcance. Esta técnica de interacción "lejana" es única de la realidad mixta y no es la forma en que los seres humanos interactúan de forma natural con el mundo real. Por ejemplo, en la película de superhéroes *X-Men*, el personaje [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) es capaz de llegar a objetos lejanos y manipularlos a distancia con las manos. Esto no es algo que los seres humanos pueden hacer en el mundo real. Tanto en HoloLens (AR) como en Mixed Reality (MR), dotamos a los usuarios con poderes mágicos y eliminamos la limitación física del mundo real, no solo para tener una magnífica experiencia con contenido holográfico, sino también para aumentar la eficacia y eficiencia de las interacciones.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>Modelo de entrada</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Apuntar y confirmar con las manos</td>
     <td>❌ No se admite</td>
     <td>✔️ Recomendado</td>
     <td>✔️ Recomendado</td>
</tr>
</table>


_"Apuntar y confirmar con las manos"_ es una de las nuevas características que utiliza el nuevo sistema articulado de seguimiento de la mano. Este modelo de entrada también es el principal en los cascos envolventes mediante el uso de controladores de movimiento.

<br>

---

## <a name="hand-rays"></a>Rayos de las manos

En HoloLens 2, hemos creado un haz que sale desde el centro de la palma de la mano. Dicho rayo se trata como una extensión de la mano. Un cursor con forma de anillo se acopla al final del rayo para indicar la ubicación en que el rayo se cruza con un objeto de destino. El objeto en que se posa el cursor puede recibir comandos gestuales de la mano.

Este comando gestual básico se desencadena al usar los dedos pulgar e índice para realizar la acción de pulsar en el aire. Si se usa el haz de mano para apuntar y la acción de pulsar en el aire para confirmar, los usuarios pueden activar un botón o un hipervínculo. Con más gestos compuestos, los usuarios son capaces de navegar por el contenido web y manipular objetos 3D a distancia. El diseño visual del rayo de la mano también debe reaccionar a estos estados de apuntar y confirmar, como se describe y se muestra a continuación: 

:::row:::
    :::column:::
        ![haces de mano que apuntan](images/hand-rays-pointing.jpg)<br>
        **Estado de apuntar**<br>
        En el estado *señalar*, el rayo es una línea discontinua y el cursor tiene forma de anillo.
    :::column-end:::
    :::column:::
        ![haces de mano que confirman](images/hand-rays-commit.jpg)<br>
        **Estado de confirmación**<br>
        En el estado *confirmar*, el rayo se convierte en una línea sólida y el cursor se reduce a un punto.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a>Transición entre cerca y lejos

En lugar de usar un gesto concreto, como "apuntar con el dedo índice" para dirigir el haz, hemos diseñado el haz para que parta del centro de la palma de la mano, con el fin de liberar y reservar los cinco dedos para los gestos más manipulativos, como acercar los dedos y agarrar. Con este diseño, creamos solo un modelo mental, se usa el mismo conjunto de gestos de las manos para la interacción cercana y la lejana. Puedes usar el mismo gesto de arrastrar para manipular objetos que se encuentren a distinta distancia. La invocación de los haces es automática y se basa en la proximidad:

:::row:::
    :::column:::
        ![Manipulación cercana](images/transition-near-manipulation.jpg)<br>
        **Manipulación cercana**<br>
        Cuando a un objeto se llega estirando el brazo (aproximadamente 50 cm), los haces se desactivan automáticamente, lo que fomenta la interacción cercana.
    :::column-end:::
    :::column:::
        ![Manipulación lejana](images/transition-far-manipulation.jpg)<br>
        **Manipulación lejana**<br>
        Cuando el objeto está a más de 50 cm, los rayos se activan. La transición suave y sin problemas.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>Interacción con una tableta táctil 2D

Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web. El concepto de diseño para la interacción lejana con una tableta táctil 2D es usar los rayos de las manos para buscar el objetivo y pulsar en el aire para seleccionarlo. Después de buscar el destino con un rayo de la mano, los usuarios pueden pulsar en el aire para desencadenar un hipervínculo o un botón. Pueden usar una mano para "pulsar en el aire y arrastrar" a fin de desplazar el contenido de la tableta táctil hacia arriba y hacia abajo. El movimiento relativo de usar las dos manos para pulsar en el aire y arrastrar puede acercar y alejar el contenido de la tableta táctil.

Si se seleccionan como destino del rayo las esquinas y los bordes aparece la prestación de manipulación más cercana. Al "agarrar y arrastrar" las prestaciones de manipulación, los usuarios pueden realizar un escalado uniforme mediante las prestaciones de la esquina y redistribuir la tableta táctil mediante las prestaciones del borde. El procedimiento de agarrar y arrastrar la barra holográfica de la parte superior de la tableta táctil 2D permite a los usuarios mover toda la tableta táctil.

:::row:::
    :::column:::
       ![Hacer clic en la interacción con una tableta táctil 2D](images/2d-slate-interaction-click.jpg)<br>
       **Hacer clic**<br>
    :::column-end:::
    :::column:::
       ![Desplazar en la interacción con una tableta táctil 2D](images/2d-slate-interaction-scroll.jpg)<br>
        **Desplazar**<br>
    :::column-end:::
    :::column:::
       ![Zoom en la interacción con una tableta táctil 2D](images/2d-slate-interaction-zoom.jpg)<br>
       **Zoom**<br>
    :::column-end:::
:::row-end:::

<br>

**Para manipular la tableta táctil 2D**<br>

* los usuarios apuntan el rayo de la mano a las esquinas y bordes y aparece la prestación de manipulación más cercana. 
* Al aplicar un gesto de manipulación en la prestación, los usuarios pueden realizar un escalado uniforme mediante la prestación de la esquina y redistribuir la tableta táctil mediante la prestación del borde. 
* Al aplicar un gesto de manipulación a la barra holográfica de la parte superior de la tableta táctil 2D, los usuarios pueden mover toda la tableta táctil.<br>


<br>

---

## <a name="3d-object-manipulation"></a>Manipulación de objetos 3D

En la manipulación directa, hay dos formas de que los usuarios manipulen objetos 3D, la manipulación con prestaciones y la manipulación sin prestaciones. En el modelo de señalar y confirmar, los usuarios son capaces de conseguir exactamente las mismas tareas a través de los rayos de las manos. No se necesita ningún aprendizaje adicional.<br>

### <a name="affordance-based-manipulation"></a>Manipulación con prestaciones
Los usuarios usan los rayos de las manos para apuntar y mostrar el rectángulo de selección y las prestaciones de manipulación. Los usuarios pueden aplicar el gesto de manipulación al rectángulo de selección para mover todo el objeto, a las prestaciones del borde para girarlo y a las prestaciones de la esquina para escalarlo de forma uniforme. <br>

:::row:::
    :::column:::
       ![Movimiento lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-move.jpg)<br>
       **Mover**<br>
    :::column-end:::
    :::column:::
       ![Giro lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-rotate.jpg)<br>
        **Girar**<br>
    :::column-end:::
    :::column:::
       ![Escala lejana en la manipulación de objetos 3D](images/3d-object-manipulation-far-scale.jpg)<br>
       **Escalar**<br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a>Manipulación sin prestaciones
Los usuarios señalan con los rayos de las manos para mostrar el rectángulo de selección y, después, le aplican directamente los gestos de manipulación. Con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano. Con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.<br>

<br>

---

## <a name="instinctual-gestures"></a>Gestos instintivos
El concepto de gestos instintivos para señalar y confirmar es similar a la de la [manipulación directa con las manos](direct-manipulation.md). Los gestos que los usuarios realizan en un objeto 3D los guía el diseño de las prestaciones 3D. Por ejemplo, un punto de control pequeño podría motivar a los usuarios a acercar los dedos pulgar e índice, mientras que si un usuario quiere agarrar un objeto mayor, debe usar los cinco dedos.

:::row:::
    :::column:::
       ![gestos instintivos para objetos lejanos pequeños](images/instinctual-gestures-far-smallobject.jpg)<br>
       **Objeto pequeño**<br>
    :::column-end:::
    :::column:::
       ![gestos instintivos para objetos lejanos medianos](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **Objeto mediano**<br>
    :::column-end:::
    :::column:::
       ![gestos instintivos para objetos lejanos grandes](images/instinctual-gestures-far-largeobject.jpg)<br>
       **Objeto grande**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Diseño simétrico entre las manos y 6 controladores DoF 

El concepto de apuntar y confirmar para la interacción lejana se creó y definió inicialmente para el Portal de realidad mixta (MRP), donde un usuario lleva puesto un casco envolvente e interactúa con objetos 3D a través de los controladores de movimiento. Los controladores de movimiento lanzar rayos para señalar y manipular objetos lejanos. Hay botones en los controladores para confirmar más acciones diferentes. Aprovechamos el modelo de interacción de rayos y los acoplamos a ambas manos. Con este diseño simétrico, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para señalar y manipular a distancia cuando usan HoloLens 2, y viceversa.    

:::row:::
    :::column:::
        ![diseño simétrico para haces con controladores](images/symmetric-design-for-rays-controllers.jpg)<br>
        **Haces de controlador**<br>
    :::column-end:::
    :::column:::
        ![diseño simétrico para haces con manos](images/symmetric-design-for-rays-hands.jpg)<br>
        **Haces de mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulte también
* [Manipulación directa con las manos](direct-manipulation.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Interacciones instintivas](interaction-fundamentals.md)