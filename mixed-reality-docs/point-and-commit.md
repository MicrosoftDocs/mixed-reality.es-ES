---
title: Punto y la confirmación con manos
description: Información general sobre el modelo de entrada de punto y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Ahora, la realidad, interacción, diseño, hololens, manos, mixta elija y confirme
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730811"
---
# <a name="point-and-commit-with-hands"></a>Punto y la confirmación con manos
Punto y la confirmación con manos es un modelo de entrada que permite a los usuarios de destino, seleccionar y manipular objetos 3D y contenidos 2D en la distancia. Esta técnica de interacción de "extremo" es única para realidad mixta y no es un hombre de manera de forma natural intereact con el mundo real. Por ejemplo, en la película héroe *X hombres*, el carácter [reescribible](https://en.wikipedia.org/wiki/Magneto_(comics)) es capaz de llegando y manipular un objeto lejos en la distancia con las manos. No es algo que los seres humanos pueden hacer en realidad. En HoloLens (AR) y realidad mixta (VR), se ofrecen a los usuarios con esta eficacia mágica, interrumpir la restricción física del mundo real no solo para tener una experiencia agradable con contenido holográfica sino también para que la interacción más eficaz y eficiente.

## <a name="device-support"></a>Compatibilidad con dispositivos

Modelo de entrada | [HoloLens (gen 1)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [Inmersivos](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
Punto y la confirmación (interacción mano lejano) | ❌ No compatible | ✔️ Recomendado | ✔️ Recomendado

Punto y confirmación, también conocido como manos ahora, es una de las nuevas características que utiliza el nuevo sistema de seguimiento de la mano articulado. Este modelo de entrada también es el modelo de entrada principal en inmersivos mediante el uso de los controladores de movimiento.

## <a name="hand-rays"></a>Rayos de mano

En HoloLens 2, hemos creado un rayo de mano que le envíe desde el centro de una mano. Este ray se trata como una extensión de la mano. Un cursor en forma de anillo se adjunta al final del rayo para indicar la ubicación donde cruza el rayo con un objeto de destino. El objeto que llega al cursor, a continuación, puede recibir comandos gestural de la mano.

Este comando gestural básico se desencadena al usar el control thumb y dedo índice para realizar la acción de pulsar en el aire. Utilizando el rayo de mano para que apunte y pulse para confirmar en el aire, los usuarios pueden activar un botón o un hipervínculo a un contenido web. Con los gestos compuestos más, los usuarios son capaces de contenido web de explorar y manipular objetos 3D a distancia. El diseño visual del rayo mano también debe reaccionar a estos Estados de punto y confirmación, como se describe y se muestra a continuación: 

* En el *señalando* de estado, el rayo es una línea de guiones y el cursor es una forma de anillo.
* En el *confirmación* de estado, el rayo se convierte en una línea sólida y reduce el cursor en un punto.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>Realizar una transición entre cerca y de extremo

En lugar de usar un gesto específico, como "que apunta con el dedo índice" para indicar el rayo, diseñamos el rayo procedentes de salida desde el centro de la palma, lanzar y reservar los cinco dedos para los gestos de manipulación inherente más, como alejar y tomar. Con este diseño, creamos un único modelo mental, compatibilidad con exactamente el mismo conjunto de gestos de mano para la interacción del próximo y lejano. Puede usar el mismo gesto de arrastre para manipular objetos en las distancias diferentes. La invocación de los rayos es automático y en función de proximidad:

*  Cuando un objeto está dentro de arm alcanzado distancia (aproximadamente 50 cm), los rayos están desactivados fomentar automáticamente para la interacción casi.
*  Cuando el objeto es más lejos de 50 cm, están activados los rayos. Debe ser la transición homogénea y sin problemas.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>Interacción de pizarra 2D

Una pizarra 2D es un contenedor holográfico hospedar contenido de la aplicación 2D, como explorador web. El concepto de diseño para el momento interactuar con una pizarra 2D es usar rayos de mano a tap aire y de destino que seleccione. Después de destino con un rayo de mano, los usuarios pueden pulse en el aire para desencadenar un hipervínculo o un botón. Puede usar por un lado para "pulsar y arrastrar el aire" para desplazarse hacia arriba y abajo un contenido Pizarra. El movimiento relativo del uso de dos manos para pulsar y arrastrar el aire puede aumentar y reducir el contenido de Pizarra.

Como destino el rayo disponible en los bordes y esquinas revela la prestación de manipulación más cercano. "Arrastre y arrastrar" la factibilidad de manipulación, los usuarios puede realizar uniforme de escalado a través de las prestaciones de esquina y puede redistribuir la Pizarra a través de las prestaciones de edge. Hacerlo y arrastre el holobar en la parte superior de la Pizarra 2D pueden mover la Pizarra toda los usuarios.

![](images/2D-Slate-Interaction-Far-720px.jpg)

Para manipular la 2D Pizarra propio:<br>

* Los usuarios señalan el rayo de mano de las esquinas o bordes para revelar la prestación de manipulación más cercano. 
* Aplicando un gesto de manipulación en la prestación, los usuarios pueden realizar un ajuste de escala uniforme a través de la prestación de esquina y pueden redistribuir la Pizarra a través de la prestación de edge. 
* Aplicando un gesto de manipulación en el holobar en la parte superior de la Pizarra 2D, los usuarios pueden mover la Pizarra toda.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipulación del objeto 3D

En la manipulación directa, hay dos maneras para que los usuarios manipular objetos 3D, manipulación de prestación y no prestación en función de manipulación. En el modelo de punto y confirmación, los usuarios son capaces de conseguir exactamente las mismas tareas a través de los rayos de mano. No se necesita ningún aprendizaje adicional.<br>

### <a name="affordance-based-manipulation"></a>Manipulación de prestación
Los usuarios usar rayos de mano para que apunte y mostrar el cuadro de límite y prestaciones de manipulación. Los usuarios pueden aplicar el gesto de manipulación en el cuadro de límite para mover todo el objeto, en la factibilidad de borde se va a girar y en la esquina prestaciones para escalar de manera uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>No prestación en función de manipulación
Los usuarios señalan con rayos de mano para mostrar el cuadro de límite, a continuación, se aplican directamente a gestos de manipulación en él. Con una mano, la traslación y rotación del objeto se asocian a movimiento y la orientación de la mano. Con dos manos, los usuarios pueden trasladar, escalar y girarlo según los movimientos relativos de dos manos.<br>

<br>

## <a name="instinctual-gesturers"></a>Gesturers instinctual
El concepto de gestos instinctual para la confirmación y el punto es similar a la de la manipulación directa. Los gestos se supone que los usuarios deben para realizar en un objeto 3D se le guiará por el diseño de factibilidad de interfaz de usuario. Por ejemplo, un punto de control pequeño podría motivar a los usuarios alejar con su pulgar y el dedo índice, mientras que un usuario podría desear tomar un objeto más grande de todos los dedos de 5.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Diseño simétrica entre manos y 6 controlador GDL 
El concepto de punto y confirmación para la interacción del Lejano inicialmente se ha creado y definido para el Mixed Reality Portal (MRP), donde un usuario desempeña un auricular envolvente e interactúa con objetos 3D a través de los controladores de movimiento. Solucionar los controladores de movimiento horizontal rayos para señalar y manipular objetos lejano. Hay botones en los controladores para confirmar más acciones diferentes. Que aprovechan el modelo de interacción de rayos y ellos conectados a dos manos. Con este diseño simétrica, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para la manipulación y el momento que apunta al usar HoloLen 2 y viceversa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Gestos instinctual

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>Vea también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Manipulación directa con manos](direct-manipulation.md)
* [Interacciones instintivas](interaction-fundamentals.md)

