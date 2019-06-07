---
title: Diseño espacial de sonido
description: Sonido espacial es una herramienta eficaz para inmersión, accesibilidad y diseño de la experiencia de usuario en aplicaciones de realidad mixta.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, sonido espacial, el diseño, el estilo
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750304"
---
# <a name="spatial-sound-design"></a>Diseño espacial de sonido

Sonido espacial es una herramienta eficaz para inmersión, accesibilidad y diseño de la experiencia de usuario en aplicaciones de realidad mixta.

Si alguna vez ha jugado [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), o alguien tenía llamarle por teléfono para ayudar a buscarlo, ya está familiarizados con la importancia del sonido espacial. Usamos audibles en nuestra vida diaria para localizar objetos, captar la atención de una persona u obtener una mejor comprensión de nuestro entorno. Cuanto más estrechamente sonido de la aplicación se comporta igual que ocurre en el mundo real, el más convincente y atractivas que será su mundo virtual.

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Diseño espacial de sonido</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Cuatro aspectos clave que hace de sonido espacial para el desarrollo de realidad mixta

De forma predeterminada, sonidos se reproducen en estéreo. Esto significa que el sonido se reproducirá con ninguna posición espacial, por lo que el usuario no sabe de dónde procede el sonido. Sonido espacial hace cuatro aspectos claves para el desarrollo de realidad mixta:

**Toma de tierra**

Sin sonido, objetos virtuales eficazmente dejan de existir cuando se activa el nuestro head fuera de ellas. Al igual que los objetos reales, que desea escuchar estos objetos, incluso cuando no puede verlos y desea poder buscarlos en cualquier lugar que le rodea. Tal como objetos virtuales deben estar conectado a tierra visualmente para combinar con el mundo real, también deberá conexión a tierra audible. Sonido espacial perfectamente combina su entorno de audio del mundo real con el entorno de audio digital.

**Atención del usuario**

En las experiencias de realidad mixta, no puede suponer que el usuario examina y espero ver algo parecido a que colocar visualmente en el mundo. Pero los usuarios siempre pueden oír un sonido reproducir incluso cuando el objeto que se reproduce el sonido está detrás de ellos. Los usuarios están acostumbrados a tener su atención dibujada el sonido - instinctually miramos hacia un objeto que nos llegan a nuestro alrededor. Si desea dirigir la mirada de los usuarios a un lugar determinado, en lugar de utilizar una flecha para que apunten a visualmente, colocar un sonido en que la ubicación es una manera muy rápida y natural para guiar a los usuarios.

**Inmersión**

Cuando los objetos se mueven o entren en conflicto, normalmente recibimos esas interacciones entre los materiales. Así que cuando los objetos no realizan el mismo sonido que lo harían en el mundo real, se pierde - como ver una película de miedo con el volumen hacia abajo un nivel de inmersión. Todos los sonidos en el mundo real proceden de un punto concreto en el espacio - cuando se activa la cabeza, recibimos el cambio en los sonidos de dónde vienen con respecto a nuestros oídos y nos podemos realizar un seguimiento de la ubicación de ningún sonido de este modo. Sonidos spatialized componen la frase"" de un lugar más allá de lo que podemos ver.

**Diseño de interacción**

En las experiencias interactivas más tradicionales, se reproducen los sonidos de interacción como efectos de sonido de la interfaz de usuario en mono estándar o estéreo. Pero dado que todo lo que en realidad mixta existe en el espacio 3D (incluidos con la interfaz de usuario) estos objetos se beneficiarán de sonidos spatialized. Cuando se presiona un botón en el mundo real, el sonido que se oye procede de ese botón. Spatializing sonidos de interacción, vuelva a proporcionamos una experiencia de usuario más naturales y realistas.

## <a name="best-practices-when-using-spatial-sound"></a>Procedimientos recomendados al usar sonido espacial

**Sonidos real funcionan mejor que sonidos sintetizadas o no naturales**

Cuanto más se familiarice es el usuario con un tipo de sonido, sentirá más real y con más facilidad podrán encontrarlo en su entorno. Una voz humana, por ejemplo, es un tipo muy común de sonido, y los usuarios lo encontrarán rápidamente como una persona real en la sala de hablar con ellos.

**Altera el expectativa de simulación**

Si está acostumbrado a un sonido procedentes de una dirección determinada, se guiará su atención en esa dirección, independientemente de las indicaciones espaciales. Por ejemplo, la mayoría de las veces que recibimos pájaros, que estén por encima de nosotros. Reproducir el sonido de una vista de pájaro, probablemente hará que el usuario buscar, incluso si coloca el sonido por debajo de ellas. Esto es generalmente confuso, y se recomienda que trabaje con las expectativas, como estos en lugar de realizar en ellas para obtener una experiencia más natural.

**Deben ser spatialized mayoría sonidos**

Como se mencionó anteriormente, todo lo que en realidad mixta existe en el espacio 3D: los sonidos también deberían. Música incluso a veces puede beneficiarse spatialization, especialmente cuando está vinculada a un menú o alguna otra interfaz de usuario.

**Evite los emisores invisibles**

Dado que nos hemos ha condicionada mirar los sonidos que nos llegan a nuestro alrededor, puede ser una experiencia poco natural e incluso desconcertante para localizar un sonido que se tiene ninguna presencia visual. Sonidos en el mundo real no provienen de un espacio vacío, así que asegúrese de que si se coloca un emisor de audio dentro del entorno del usuario inmediata que también se puede ver.

**Evitar enmascaramiento espacial**

Sonido espacial se basa en pilas acústicos muy sutiles que pueden ser overpowered por otros sonidos. Si es necesario estéreo música o sonido de ambiente, asegúrese de que son lo suficientemente bajas en la combinación para que quede espacio para los detalles de los sonidos de spatialized que permiten a los usuarios encontrarlos fácilmente y mantenerlos suene naturales y realistas.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Conceptos generales que tener en cuenta al usar sonido espacial

**Sonido espacial es una simulación**

El uso más frecuente del sonido espacial realiza un sonido parece como si se procedentes de un objeto real o virtual en el mundo. Por lo tanto, los sonidos spatialized es posible que sean más convenientes procedentes de dichos objetos.

Tenga en cuenta que la precisión percibida de significa espacial de sonido que necesariamente no debe emitir un sonido desde el centro de un objeto, como la diferencia será perceptible según el tamaño del objeto y la distancia desde el usuario. Con objetos pequeños, el punto central del objeto generalmente es suficiente. Para los objetos más grandes, puede que desee un emisor de sonido o varios emisores en la ubicación específica dentro del objeto que se supone que para se puede producir el sonido.

**Normalizar todos los sonidos**

Atenuación de distancia se produce rápidamente en el medidor de la primera parte del usuario, como ocurre en el mundo real. Se deben normalizar todos los archivos de audio para garantizar la atenuación de distancia físicamente precisa y asegúrese de que pueda ser escuchado un sonido cuando varios medidores ausente (si procede). El motor de audio espacial controlará la necesaria para un sonido a "sentir" que se encuentra en una cierta distancia (con una combinación de atenuación y "pilas de distancia") y aplicar cualquier atenuación que podría reducir el efecto de atenuación. Fuera de la simulación de un objeto real, la inicial de distancia decadencia de *sonido espacial* sonidos probablemente será más que suficiente para un correcto mezcla de audio.

**Interfaces del objeto de usuario y la detección**

Al usar pistas de sonido para dirigir la atención del usuario más allá de su vista actual, debe ser el sonido audible y destacado en la combinación, muy por encima de ningún sonido estéreo y otros sonidos spatialized que pueden distraer la pila de audio direccional. Para sonidos y música que están asociados con un elemento de la interfaz de usuario (por ejemplo, un menú), el emisor de sonido debe asociarse a ese objeto. Estéreo y otros que no sea posicional reproducir audio pueden dificultar spatialized elementos a los usuarios localizar (véase más arriba: Evite enmascaramiento espacial).

**Usar un sonido espacial a través de sonido 3D estándar tanto como sea posible**

En realidad mixta, para una mejor experiencia de usuario, audio 3D debe lograrse mediante sonido espacial en lugar de las tecnologías de audio 3D heredadas. En general, el mejorado spatialization vale la pena el pequeño costo de CPU sobre estándar 3D de sonido. Estándar de audio 3D puede usarse para sonidos de prioridad baja, sonidos spatialized pero no necesariamente Unidos a un objeto físico o virtual y los objetos que el usuario nunca necesita localizar para interactuar con la aplicación.

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Asignación espacial](spatial-mapping.md)
