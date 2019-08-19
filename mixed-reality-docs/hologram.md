---
title: ¿Qué es un holograma?
description: HoloLens le permite ver e interactuar con hologramas tridimensionales, objetos de luz y sonido que aparecen en el mundo.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologramas, diseño, interacción
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829782"
---
# <a name="what-is-a-hologram"></a>¿Qué es un holograma?

HoloLens le permite crear **hologramas**, objetos de luz y sonido que aparecen en el mundo, al igual que si fueran objetos reales. Los hologramas responden a los comandos de [miradas](gaze.md), [gestos](gestures.md) y [voz](voice-input.md), y pueden interactuar con las [superficies del mundo real](spatial-mapping.md). Con los hologramas, puede crear objetos digitales que formen parte de su mundo.

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Hologramas</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>Un holograma se compone de luz y sonido

Los hologramas que HoloLens [representa](rendering.md) aparecen en el marco holográfica directamente delante de los ojos del usuario. Los hologramas agregan luz a su mundo, lo que significa que puede ver la luz de la pantalla y la luz de su entorno. HoloLens no quita la luz de los ojos, por lo que los hologramas no se pueden representar con el color negro. En su lugar, el contenido negro aparece como transparente.

Los hologramas pueden tener muchos comportamientos y apariencias diferentes. Algunos son reales y sólidos, mientras que otros están animados y Ethereal. Los hologramas pueden resaltar características en el entorno y pueden ser elementos de la interfaz de usuario de la aplicación.

![Holographic Dog en el piso](images/fang3-640px.jpg)

Los hologramas también pueden hacer [sonidos](spatial-sound.md), que parecerá que provienen de un lugar específico del entorno. En HoloLens, el sonido procede de dos altavoces que se encuentran directamente encima de sus oídos, sin cubrirlos. De forma similar a las pantallas, los oradores son aditivos, introduciendo nuevos sonidos sin bloquear los sonidos de su entorno.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Se puede colocar un holograma en el mundo o etiqueta junto con usted

Cuando tenga una ubicación concreta en la que desee un holograma, puede [colocarlo](coordinate-systems.md) precisamente en el mundo. A medida que recorra el holograma, aparecerá estable en relación con el mundo. Si usa un delimitador [espacial](coordinate-systems.md#spatial-anchors) para anclar ese objeto al mundo, el sistema puede incluso recordar dónde lo dejó cuando vuelva más tarde.

![Maquette de creación de Holographic en una tabla](images/image5-640px.png)

Algunos hologramas siguen al usuario en su lugar. Estas etiquetas a lo largo de los hologramas se colocan en relación con el usuario, independientemente de dónde se recorran. Incluso puede optar por un holograma y colocarlo en la pared una vez que llegue a otra habitación.

**Procedimientos recomendados**
* Algunos escenarios pueden exigir que los hologramas se mantengan fácilmente reconocibles o visibles a lo largo de la experiencia. Hay dos enfoques de alto nivel para este tipo de posicionamiento. Vamos a llamarlos **"display-locked"** y **"Body-locked"** .
   * Mostrar el contenido bloqueado está "bloqueado" en la pantalla del dispositivo. Esto es complicado por una serie de motivos, entre los que se incluyen una sensación poco natural de "clingyness" que hace que muchos usuarios se sienten frustrados y desean "sacudirlos". En general, muchos diseñadores lo han descubierto mejor para evitar el contenido de bloqueo de pantalla.
   * El enfoque de cuerpo bloqueado es mucho más forgivable. El bloqueo de cuerpo es cuando un holograma está anclado al cuerpo del usuario o al vector de miración, pero se coloca en el espacio 3D alrededor del usuario. Muchas experiencias han adoptado un comportamiento de bloqueo de cuerpo en el que el holograma "sigue" a los usuarios mirados, lo que permite al usuario girar su cuerpo y desplazarse por el espacio sin perder el holograma. Incorporar un retraso ayuda a que el movimiento de hologramas parezca más natural. Por ejemplo, algunas interfaces de usuario principales del sistema operativo Holographic de Windows usan una variación en el bloqueo del cuerpo que sigue al mirador con un retraso suave y elástico mientras el usuario cambia la cabeza.
* Coloque el holograma con una distancia de visualización cómoda normalmente de aproximadamente 1-2 metros de la cabeza.
* Proporcione una cantidad de desplazamiento para los elementos que deben estar continuamente en el marco holográfica, o considere la posibilidad de animar el contenido a un lado de la pantalla cuando el usuario cambie su punto de vista.

**Coloque los hologramas en la zona óptima: entre 1,25 m y 5 m**

Dos medidores son los más óptimos, y la experiencia se degradará cuanto más se acerque a un medidor. En distancias más cerca de un medidor, es más probable que los hologramas que se mueven con frecuencia en profundidad sean problemáticos que los hologramas estacionarios. Considere la posibilidad de recortar o difuminar correctamente el contenido cuando se acerque demasiado, de modo que no se determine al usuario en una experiencia inesperada.

![Distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un holograma interactúa con usted y su mundo

Los hologramas no solo están relacionados con la luz y el sonido; también son una parte activa de su mundo. Mira un holograma y gesto con la mano y un holograma puede empezar a seguirlo. Asigne un comando de voz a un holograma y puede responder.

![Diseño de la motocicleta holográfica equipado en un cuerpo de la motocicleta real](images/image8-640px.png)

Los hologramas permiten interacciones personales que no son posibles en ningún otro lugar. Dado que HoloLens sabe dónde se encuentra en el mundo, un personaje Holographic puede tener una apariencia directa en los ojos mientras se recorre la habitación.

Un holograma también puede interactuar con su entorno. Por ejemplo, puede colocar una bola de rebote holográfica sobre una tabla. A continuación, con una [derivación aérea](gestures.md#air-tap), vea el rebote de la bola y cree un sonido cuando llegue a la tabla.

Los hologramas también pueden ser ocluidosdos por objetos del mundo real. Por ejemplo, un personaje Holographic podría recorrer una puerta y detrás de una pared, fuera de la vista.

**Sugerencias para la integración de hologramas y el mundo real**
* La alineación de las reglas de Gravitational hace que los hologramas sean más fáciles de relacionar con y más increíble. p.e. Ponga un perro holográfica en el suelo & un jarrón en la tabla en lugar de hacer que floten en el espacio.
* Muchos diseñadores han descubierto que incluso pueden integrar de forma más increíble los hologramas creando una "sombra negativa" en la superficie en la que está sentado el holograma. Para ello, se crea un resplandor blando en torno al holograma y, a continuación, se resta la "sombra" del resplandor. El resplandor suave se integra con la luz del mundo real y la sombra del holograma en el entorno.

## <a name="a-hologram-is-whatever-you-dream-up"></a>Un holograma es todo lo que ha soñado

Como desarrollador de Holographic, tiene la posibilidad de descomponer su creatividad de pantallas 2D y en todo el mundo. ¿Qué *le* compilar?

![Mundo imaginario Holographic en salón](images/designoverview.jpg)

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Color, luz y materiales](color,-light-and-materials.md)
