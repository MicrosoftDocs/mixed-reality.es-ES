---
title: Apuntar y confirmar con las manos
description: Introducción al modelo de entrada de apuntar y confirmar
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, interaction, design, hololens, hands, far, point and commit
ms.openlocfilehash: 30f85d2bb455abab3a533e0a829b4fba8cea0a7a
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66402381"
---
# <a name="point-and-commit-with-hands"></a>Apuntar y confirmar con las manos
Apuntar y confirmar con las manos es un modelo de entrada que permite a los usuarios seleccionar como destino, seleccionar y manipular contenidos 2D y objetos 3D a distancia. Esta técnica de interacción de "lejana" es única de la realidad mixta, no es una forma que los humanos usan para interactuar de forma natural con el mundo real. Por ejemplo, en la película se superhéroes *X-Men*, el personaje [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) es capaz de llegar a objetos lejanos y manipularlos a distancia con las manos. Esto no es algo que los seres humanos pueden hacer en el mundo real. Tanto en HoloLens (AR) como en la realidad mixta (VR), dotamos a los usuarios con poderes mágicos, eliminando la limitación física del mundo real no para tener una magnífica experiencia con contenido holográfico, sino también para aumentar la eficacia de la interacción.

## <a name="device-support"></a>Compatibilidad con dispositivos

Modelo de entrada | [HoloLens (1ª generación)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Cascos envolventes](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Apuntar y confirmar con las manos | ❌ No se admite | ✔️ Recomendado | ✔️ Recomendado

Apuntar y confirmar, también conocido como manos lejanas, es una de las nuevas características que utiliza el nuevo sistema de seguimiento de la mano articulado. Este modelo de entrada también es el principal en los cascos envolventes mediante el uso de controladores de movimiento.

## <a name="hand-rays"></a>Rayos de las manos

En HoloLens 2, hemos creado un rayo que sale desde el centro de la palma de la mano. Dicho rayo se trata como una extensión de la mano. Un cursor con forma de anillo se acopla al final del rayo para indicar la ubicación en que el rayo se cruza con un objeto de destino. El objeto en que se posa el cursor puede recibir comandos gestuales de la mano.

Este comando gestual básico se desencadena al usar los dedos pulgar e índice para realizar la acción de pulsar en el aire. Si se usa el rayo de la mano para apunte y la acción de pulsar en el aire para confirmar, los usuarios pueden activar un botón o un hipervínculo en un contenido web. Con más gestos compuestos, los usuarios son capaces de navegar por el contenido web y manipular objetos 3D a distancia. El diseño visual del rayo de la mano también debe reaccionar a estos estados de apuntar y confirmar, como se describe y se muestra a continuación: 

* En el estado *señalar*, el rayo es una línea discontinua y el cursor tiene forma de anillo.
* En el estado *confirmar*, el rayo se convierte en una línea sólida y el cursor se reduce a un punto.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Transición entre cerca y lejos

En lugar de usar un gesto concreto, como "apuntar con el dedo índice" para dirigir el rayo, hemos diseñado que el rayo parta del centro de la palma de la mano, con el fin de liberar y reservar los cinco dedos para los gestos más manipulativos, como acercar los dedos y agarrar. Con este diseño, creamos solo un modelo mental, que admite exactamente el mismo conjunto de gestos de las manos para la interacción cercana y la lejana. Puedes usar el mismo gesto de arrastrar para manipular objetos que se encuentren a distinta distancia. La invocación de los rayos es automática y se basa en la proximidad:

*  Cuando a un objeto se llega estirando el brazo (aproximadamente 50 cm), los rayos se desactivan automáticamente, lo que fomenta la interacción cercana.
*  Cuando el objeto está a más de 50 cm, los rayos se activan. La transición suave y sin problemas.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>Interacción con una tableta táctil 2D

Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web. El concepto de diseño para la interacción lejana con una tableta táctil 2D es usar los rayos de las manos para buscar el objetivo y pulsar en el aire para seleccionarlo. Después de buscar el destino con un rayo de la mano, los usuarios pueden pulsar en el aire para desencadenar un hipervínculo o un botón. Pueden usar una mano para "pulsar en el aire y arrastrar" para desplazar el contenido de una tableta táctil hacia arriba y hacia abajo. El movimiento relativo de usar las dos manos para pulsar en el aire y arrastrar puede acercar y alejar el contenido de la tableta táctil.

Si se seleccionan como destino del rayo las esquinas y los bordes aparece la prestación de manipulación más cercana. Mediante "agarrar y arrastrar" las prestaciones de manipulación los usuarios pueden realizar un escalado uniforme mediante las prestaciones de la esquina y pueden redistribuir la tableta táctil mediante las prestaciones del borde. El procedimiento de agarrar y arrastrar la barra holográfica de la parte superior de la tableta táctil 2D puede permitir a los usuarios mover toda la tableta táctil.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Para manipular la propia tableta táctil 2D:<br>

* los usuarios apuntan el rayo de la mano a las esquinas y bordes y aparece la prestación de manipulación más cercana. 
* Al aplicar un gesto de manipulación en la prestación, los usuarios pueden realizar un escalado uniforme mediante la prestación de la esquina y pueden redistribuir la tableta táctil mediante la prestación del borde. 
* Si aplican un gesto de manipulación a la barra holográfica de la parte superior de la tableta táctil 2D, los usuarios pueden mover toda la tableta táctil.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipulación de objetos 3D

En la manipulación directa, hay dos formas de que los usuarios manipulen objetos 3D, la manipulación con prestaciones y la manipulación sin prestaciones. En el modelo de señalar y confirmar, los usuarios son capaces de conseguir exactamente las mismas tareas a través de los rayos de las manos. No se necesita ningún aprendizaje adicional.<br>

### <a name="affordance-based-manipulation"></a>Manipulación con prestaciones
Los usuarios usan los rayos de las manos para apuntar y mostrar el rectángulo de selección y las prestaciones de manipulación. Los usuarios pueden aplicar el gesto de manipulación al rectángulo de selección para mover todo el objeto, a las prestaciones del borde para girarlo y a las prestaciones de la esquina para escalarlo de forma uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>Manipulación sin prestaciones
Los usuarios señalan con los rayos de las manos para mostrar el rectángulo de selección y, después, le aplican directamente los gestos de manipulación. Con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano. Con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.<br>

<br>

## <a name="instinctual-gesturers"></a>Gestos instintivos
El concepto de gestos instintivos para señalar y confirmar es similar a la de la manipulación directa. Los gestos que se supone que los usuarios van a realizar en un objeto 3D los guía el diseño de las prestaciones 3D. Por ejemplo, un punto de control pequeño podría motivar a los usuarios a acercar los dedos pulgar e índice, mientras que si un usuario desea agarrar un objeto mayor, debe usar los cinco dedos.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Diseño simétrico entre las manos y 6 controladores DoF 
El concepto de apuntar y confirmar para la interacción lejana se creó y definió inicialmente para el Portal de realidad mixta (MRP), donde un usuario lleva puesto un casco envolvente e interactúa con objetos 3D a través de los controladores de movimiento. Los controladores de movimiento lanzar rayos para señalar y manipular objetos lejanos. Hay botones en los controladores para confirmar más acciones diferentes. Aprovechamos el modelo de interacción de rayos y los acoplamos a ambas manos. Con este diseño simétrico, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para señalar y manipular a distancia cuando usan HoloLens 2, y viceversa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Gestos instintivos

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Consulte también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Manipulación directa con las manos](direct-manipulation.md)
* [Interacciones instintivas](interaction-fundamentals.md)

