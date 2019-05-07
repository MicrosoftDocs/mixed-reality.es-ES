---
title: Punto y confirmación
description: Información general sobre el modelo de entrada de punto y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: Diseño de interacción, la realidad mixta
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581315"
---
# <a name="point-and-commit"></a>Punto y confirmación
Punto y confirmación es un modelo de entrada permite a los usuarios de destino, seleccionar y manipular contenido 2D y 3D objetos en una distancia. Esta técnica de interacción de "Extremo" es una experiencia interactiva del ombligo que realmente no tenía el ser humano durante sus interacciones diarias con el mundo real. Por ejemplo, en una película héroe, reescribible es capaz de llegando y manipular un objeto a través de las manos en una distancia mucho, pero humanos no pueden hacerlo en realidad. En Microsoft HoloLens (AR) y realidad mixta de Microsoft (VR), se ofrecen a los usuarios este poder mágica, interrumpir la restricción física del mundo real no solo para tener una experiencia agradable con contenido holográfica pero hacer más eficaz la interacción y eficaz.

## <a name="device-support"></a>Compatibilidad con dispositivos
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Punto y la confirmación (interacción mano lejano)</td>
        <td>❌ No compatible</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>
<br>
Punto y la confirmación ha sido uno de los modelos de entrada principales en HoloLens 2, el uso de la mano articulada nuevo sistema de seguimiento. Este modelo de entrada también es el modelo de entrada principal en inmersivos mediante el uso de los controladores de movimiento. Punto y confirmación es el modelo de entrada que se recomienda para reemplazar el encabezado que mirar y validará en HoloLens (gen 1). 

## <a name="hand-rays"></a>Rayos de mano
En el 2 de HoloLens, creamos un rayo de mano filmar desde el centro de una mano. El rayo se trata como una extensión de la mano. Un cursor de la forma de anillo se adjunta al final del rayo que implique la ubicación donde cruza el rayo con un objeto hitted. El objeto que llega cursor recibirán gestural comandos de la mano. 

El comando gestural muy básico se desencadena al usar el pulgar y el dedo índice para realizar el gesto de pulsar de aire. Mediante el uso de ray mano para que apunte y pulse para confirmar en el aire, los usuarios pueden activar un botón o un hipervínculo a un contenido web. Con los gestos compuestos más, los usuarios son capaces de explorar el contenido web y manipular objetos 3D en una distancia. También debe reaccionar el diseño visual del rayo de mano para que apunte y Estados de confirmación: <br>
* En el estado señalador, el rayo es dash con líneas y el cursor se encuentra una forma de anillo.
* en el estado de confirmación, el rayo se convierte en una línea sólida y reduce el cursor en un punto.<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>Realizar una transición entre cerca y de extremo
En lugar de usar gestos específicos, como la que apunta con el dedo índice para dirigir el rayo, diseñamos el rayo salir desde el centro de la palma, lanzar y reservar los dedos para manipulaciones gestural más cinco. Por lo tanto, HoloLens 2 admite exactamente el mismo conjunto de gestos de mano para la interacción del próximo y lejano. Aprendizaje adicional no es necesaria cuando los usuarios en tránsito desde cerca de lejos interacciones y viceversa. Los usuarios pueden usar el mismo gesto de arrastre para manipular objetos en las distancias diferentes. La invocación de los rayos es automático y en función de proximidad: <br>
* Cuando un objeto está dentro de arm alcanzado distancia (aproximadamente 50 cm), los rayos están desactivados fomentar automáticamente para la interacción casi. 
* Cuando el objeto es más lejos de 50 cm, están activados los rayos.

Este mecanismo realiza la transición homogénea y sin problemas.<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>Interacción de pizarra 2D
Una pizarra 2D es un contenedor holográfico hospedar contenido de la aplicación 2D, como explorador web. El concepto de diseño para el momento interactuar con una pizarra 2D es usar los rayos de mano para que apunte y pulse para confirmar en el aire.<br>

Para interactuar con la Pizarra permite:<br>

* Los usuarios pueden apuntar a un hipervínculo o un botón, a continuación, en el aire para activarlo. 
* Los usuarios pueden usar por un lado para realizar un gesto de navegación para desplazarse arriba y abajo un contenido Pizarra. 
* Los usuarios pueden usar dos manos a realizar gestos de navegación para aumentar y reducir el contenido de Pizarra.<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

Para manipular la 2D Pizarra propio:<br>

* Los usuarios señalan el rayo de mano de las esquinas o bordes para revelar la prestación de manipulación más cercano. 
* Aplicando un gesto de manipulación en la prestación, los usuarios pueden realizar un ajuste de escala uniforme a través de la prestación de esquina y pueden redistribuir la Pizarra a través de la prestación de edge. 
* Aplicando un gesto de manipulación en el holobar en la parte superior de la Pizarra 2D, los usuarios pueden mover la Pizarra toda.<br>

<br>

## <a name="3d-object-manipulation"></a>Manipulación del objeto 3D
En la manipulación directa, hay dos maneras para que los usuarios manipular objetos 3D, manipulación en función de prestación y Non-affordnace basado manipulación. En el modelo de punto y confirmación, los usuarios son capaces de conseguir exactamente las mismas tareas a través de los rayos de mano. No se necesita ningún aprendizaje adicional.<br>

### <a name="affordance-based-manipulation"></a>Manipulación de prestación basado
Los usuarios usar rayos de mano para que apunte y mostrar el cuadro de límite y prestaciones de manipulación. Los usuarios pueden aplicar el gesto de manipulación en el cuadro de límite para mover todo el objeto, en la factibilidad de borde se va a girar y en la esquina prestaciones para escalar de manera uniforme. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>No prestación en función de manipulación
Los usuarios señalan con rayos de mano para mostrar el cuadro de límite, a continuación, se aplican directamente a gestos de manipulación en él. Con una mano, la traslación y rotación del objeto se asocian a movimiento y la orientación de la mano. Con dos manos, los usuarios pueden trasladar, escalar y girarlo según los movimientos relativos de dos manos.<br>

<br>

## <a name="instinctual-gesturers"></a>Gesturers instinctual
El concepto de gestos instinctual para la confirmación y el punto está sincronizado con la para la manipulación directa. ¿Qué gestos supone que los usuarios a realizar en un objeto 3D se guían por el diseño de factibilidad de interfaz de usuario. Un punto de control pequeño podría motivar a los usuarios para alejar con el pulgar y el dedo índice, mientras que los usuarios a tomar con dedo 5 hace que un objeto grande.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>Diseño simétrica entre manos y 6 controlador GDL 
El concepto del modelo de punto y confirmación para la interacción del extremo en primer lugar se crea y definido para el mixto realidad Portal (MRP), donde los usuarios llevar un auricular envolvente e interactúan con el objeto 3d a través de los controladores de movimiento. Solucionar los controladores de movimiento horizontal rayos para señalar y manipular objetos lejano. Hay botones en los controladores para confirmar más funcionalidades diferentes. Se aprovechan el modelo de interacción de rayos y adjúntelos en dos manos. Con este diseño simétrica, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para ahora señalando y manipulación durante la primera vez que usa HoloLen 2 y viceversa.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>Vea también
* [Mirada y confirmación](gaze-and-commit.md)
* [Manipulación directa](direct-manipulation.md)
* [Conceptos básicos de la interacción](interaction-fundamentals.md)
