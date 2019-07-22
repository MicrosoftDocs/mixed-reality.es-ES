---
title: ¿Qué es un holograma?
description: HoloLens le permite ve e interactuar con hologramas tridimensionales, objetos de luz y sonido aparecen en el mundo que le rodea.
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

HoloLens le permite crear **hologramas**, realizan los objetos de luz y sonido que aparecen en el mundo, simplemente como si fueran objetos reales. Hologramas responden a su [que mirar](gaze.md), [gestos](gestures.md) y [comandos de voz](voice-input.md)y puede interactuar con [reales superficies](spatial-mapping.md) que le rodea. Con hologramas, puede crear objetos digitales que forman parte de su mundo.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Hologramas</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>Se realiza un holograma de luz y sonido

El hologramas ese HoloLens [representa](rendering.md) aparecen en el fotograma holográfico directamente delante de la vista del usuario. Hologramas aportan iluminación a su mundo, lo que significa que aparece la luz de la visualización y la luz de su entorno. HoloLens no quite luz de los ojos, por lo que no se pueden representar hologramas con el color negros. En su lugar, negro contenido aparece como transparente.

Hologramas pueden tener muchos aspectos diferentes y comportamientos. Algunas son realistas y sólido y otras son cartoonish y ethereal. Hologramas pueden resaltar las características de los alrededores, y pueden ser elementos de interfaz de usuario de la aplicación.

![Perro holográfica recorrido en el suelo](images/fang3-640px.jpg)

También pueden hacer hologramas [sonidos](spatial-sound.md), que parecerá que proviene de una ubicación específica en su entorno. En HoloLens, sonido procede de dos altavoces que se encuentran directamente encima de las orejas, sin protegerlas. Al igual que las pantallas, los altavoces son aditivas, introducir nuevos sonidos sin bloquear los sonidos de su entorno.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Un holograma puede colocarse en el mundo o etiqueta con usted

Cuando haya una ubicación concreta en la que desea un holograma, puede [colocar](coordinate-systems.md) que existe exactamente en el mundo. Durante el recorrido en torno a esa holograma, aparecerán estable en relación con el mundo que le rodea. Si usa un [delimitador espacial](coordinate-systems.md#spatial-anchors) para anclar ese objeto firmemente a todo el mundo, el sistema puede recordar incluso donde lo dejó cuando regrese en otro momento.

![Maquette creación holográfica sentado en una tabla](images/image5-640px.png)

Algunos hologramas seguir al usuario en su lugar. Estos hologramas tag-along se posicionan en relación con el usuario, independientemente de donde guían. Incluso puede poner un holograma con usted durante un tiempo y, a continuación, colóquelo en la pared cuando esté en otra habitación.

**Procedimientos recomendados**
* Algunos escenarios pueden solicitar que hologramas permanecen fácilmente reconocible o visible a lo largo de la experiencia. Hay dos enfoques de alto nivel para este tipo de colocación. Vamos a llamar a **"bloqueada para mostrar"** y **"bloqueada cuerpo"** .
   * Bloqueado para mostrar el contenido es por posición "bloqueado" a la pantalla del dispositivo. Esto es complicado para una serie de motivos, incluidos una sensación natural de "clingyness" que hace que muchos usuarios frustrados y desean "shake off". En general, muchos diseñadores han encontrado lo mejor evitar el contenido de pantalla de bloqueo.
   * El enfoque bloqueado por el cuerpo es mucho más condonable. Cuerpo de bloqueo es cuando un holograma está anclado al cuerpo del usuario o vector mirada, pero se coloca en el espacio 3d alrededor del usuario. Muchas experiencias han adoptado un comportamiento de bloqueo de cuerpo, donde el holograma "sigue" la mirada a los usuarios, lo que permite al usuario girar su cuerpo y desplazarse por el espacio sin perder el holograma. Incorpora un retraso ayuda a que el movimiento holograma resultar más natural. Por ejemplo, alguna interfaz de usuario de que el sistema operativo de Windows Holographic core usa una variación en el cuerpo de bloqueo que sigue a la mirada del usuario con un retraso suave, tipo elástico mientras el usuario activa su cabeza.
* Coloque el holograma a una distancia de visualización cómoda normalmente aproximadamente un 1-2 metros del encabezado.
* Proporcionar una cantidad de desfase para los elementos que deben estar continuamente en el marco holográfico o considere la posibilidad de animar el contenido a un lado de la pantalla cuando el usuario cambia su punto de vista.

**Colocar hologramas en la zona óptima - entre 1,25 m y 5m**

Dos medidores es el óptimo y la experiencia empeorará más cerca que obtiene de un medidor. En las distancias más cerca de lo que un medidor, son más probables que sea problemático que hologramas estacionarios hologramas que mueven periódicamente en profundidad. Considere la posibilidad de recorte de forma correcta o difuminación su contenido cuando obtiene demasiado estrecha para evitar que el usuario del producto en una experiencia inesperada.

![Distancia óptima para colocar hologramas del usuario.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un holograma interactúa con usted y su mundo

Hologramas no solo acerca de la luz y sonido; también son una parte activa del su mundo. Mirada a una holograma gestos con la mano, y puede iniciar un holograma seguirle. Proporcione un comando de voz a un holograma, y puede responder.

![Ajusta el diseño de las moto holográfica en un cuerpo de la vida real motocicleta](images/image8-640px.png)

Hologramas habilitar interacciones personales que no son posibles en otro lugar. Porque el HoloLens sepa dónde está en el mundo, un carácter holográfico puede buscar, directamente a los ojos durante el recorrido en torno a la sala de reuniones.

También puede interactuar un holograma con respecto a su entorno. Por ejemplo, puede colocar una bola que rebota holográfica encima de la tabla. A continuación, con un [en el aire](gestures.md#air-tap), vea la bola rebote y que suene cuando llega a la tabla.

También se pueden ocluyeron hologramas en objetos del mundo real. Por ejemplo, un carácter holográfico podría guiará a través de una puerta y detrás de una pared, pierda de vista.

**Sugerencias para la integración de hologramas y el mundo real**
* Alinear las reglas de gravitatoria facilita hologramas relacionar con y solo más. eg: Colocar un perro holográfico en el suelo & un jarrón en la tabla en lugar de tenerlos flotando en el espacio.
* Muchos diseñadores han descubierto que se pueden integrar hologramas believably aún más mediante la creación de una "sombra negativa" en la superficie que se encuentra el holograma en. Para ello, cree un suave efecto de iluminado en cero en torno a la holograma y restando la "sombra" desde el efecto de iluminado. El efecto de iluminado temporal se integra con la luz procedentes del mundo real y holograma de lo motivos que la sombra en el entorno.

## <a name="a-hologram-is-whatever-you-dream-up"></a>Un holograma es todo lo que imaginar

Como desarrollador holográfico, tiene la posibilidad de interrumpir su creatividad, las pantallas 2D y en el mundo que le rodea. ¿Qué *le* compilar?

![Holográfica mundial imaginaria salón](images/designoverview.jpg)

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Color, luz y materiales](color,-light-and-materials.md)
