---
title: Diseño de sonido espacial
description: El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, sonido espacial, diseño, estilo
ms.openlocfilehash: acc568eeb08d2a27574dcfbc9f132519e1e31843
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438289"
---
# <a name="spatial-sound-design"></a>Diseño de sonido espacial

El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.

Si alguna vez ha jugado el número de [marco](https://en.wikipedia.org/wiki/Marco_Polo_(game))o si alguien llama a su teléfono para ayudarle a encontrarlo, ya está familiarizado con la importancia del sonido espacial. Usamos señales sonoras en nuestras vidas diarias para buscar objetos, obtener la atención de un usuario u obtener una mejor comprensión de nuestro entorno. Cuanto más se comporta el sonido de la aplicación como lo hace en el mundo real, más convincente será el universo virtual.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Diseño de sonido espacial</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Cuatro aspectos clave del sonido espacial para el desarrollo de la realidad mixta

De forma predeterminada, los sonidos se reproducen en estéreo. Esto significa que el sonido se reproducirá sin posición espacial, por lo que el usuario no sabe de dónde procede el sonido. El sonido espacial hace cuatro cosas clave para el desarrollo de la realidad mixta:

**Tierra**

Sin sonido, los objetos virtuales dejan de existir de forma eficaz cuando se desactiva nuestra cabeza. Al igual que los objetos reales, se desea poder oír estos objetos incluso cuando no se pueden ver y se desea poder encontrarlos en cualquier lugar. Del mismo modo que los objetos virtuales deben basarse visualmente para combinarse con su mundo real, también deben estar en el nivel de forma audible. El sonido espacial combina sin problemas el entorno de audio del mundo real con el entorno de audio digital.

**Atención del usuario**

En el caso de las experiencias de realidad mixta, no puede asumir el lugar en el que está buscando el usuario y espera ver algo que usted coloca en el mundo visualmente. Sin embargo, los usuarios siempre pueden oír una reproducción de sonido incluso cuando el objeto que reproduce el sonido está detrás de ellos. Los usuarios se utilizan para que su atención se dibujen por sonido: instinctually buscar un objeto que nos encanta. Si desea dirigir la mirada de un usuario a un lugar determinado, en lugar de usar una flecha para apuntar visualmente, la colocación de un sonido en esa ubicación es una forma muy natural y rápida de guiarlos.

**Profundidad**

Cuando los objetos se mueven o entran en conflicto, normalmente escuchan esas interacciones entre materiales. Por lo tanto, cuando los objetos no hacen el mismo sonido en el mundo real, se pierde un nivel de inmersión, como ver una película de miedo con el volumen todo el recorrido. Todos los sonidos del mundo real provienen de un punto determinado en el espacio: cuando se activan nuestros cabezales, se oye el cambio en el lugar en el que provienen esos sonidos con respecto a nuestros oídos, y podemos realizar un seguimiento de la ubicación de cualquier sonido de esta manera. Los sonidos espaciales componen la "sensación" de un lugar más allá de lo que podemos ver.

**Diseño de interacción**

En las experiencias interactivas más tradicionales, los sonidos de interacción como la interfaz de usuario se reproducen en mono o estéreo estándar. No obstante, dado que todo lo que hay en realidad está en el espacio 3D, incluida la interfaz de usuario, estos objetos se benefician de los sonidos espaciales. Cuando se presiona un botón en el mundo real, el sonido que se oye viene de ese botón. Mediante la espacialización de los sonidos de interacción, se proporciona una experiencia de usuario más natural y realista.

## <a name="best-practices-when-using-spatial-sound"></a>Prácticas recomendadas al usar el sonido espacial

**Los sonidos reales funcionan mejor que los sonidos sintetizados o no naturales**

Cuanto más familiar es el usuario con un tipo de sonido, más real se sentirá y cuanto más sencillo podrá encontrarlo en su entorno. Una voz humana, por ejemplo, es un tipo muy común de sonido y los usuarios la ubicarán tan pronto como una persona real en el salón hablando.

**La expectativa supera la simulación**

Si utiliza un sonido procedente de una dirección determinada, su atención se guiará en esa dirección independientemente de las indicaciones espaciales. Por ejemplo, la mayor parte del tiempo en el que escuchamos pájaros, están por encima de nosotros. La reproducción del sonido de un pájaro probablemente hará que el usuario realice una búsqueda, incluso si coloca el sonido por debajo de ellos. Esto suele ser confuso y se recomienda que trabaje con expectativas como estas en lugar de hacerlo para una experiencia más natural.

**La mayoría de los sonidos deben estar espaciales**

Como se mencionó anteriormente, todo lo que se encuentra en Mixed Reality existe en el espacio 3D. Incluso la música a veces puede beneficiarse de la espacialización, especialmente cuando está asociada a un menú o a alguna otra interfaz de usuario.

**Evitar emisores invisibles**

Como nos hemos acondicionado para examinar los sonidos que nos oyen, puede ser una experiencia poco natural e incluso unnerving para localizar un sonido que no tenga ninguna presencia visual. Los sonidos del mundo real no provienen de un espacio vacío, por lo que debe asegurarse de que si se coloca un emisor de audio en el entorno inmediato del usuario, también puede verse.

**Evitar el enmascaramiento espacial**

El sonido espacial se basa en señales acústicas muy sutiles que pueden ser sobrealimentadas por otros sonidos. Si tiene música estéreo o sonidos ambientales, asegúrese de que son lo suficientemente bajas en la combinación para dar cabida a los detalles de los sonidos espaciales que permitirán a los usuarios encontrarlos fácilmente y mantenerlos más sólidos y naturales.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Conceptos generales que se deben tener en cuenta al usar el sonido espacial

**El sonido espacial es una simulación**

El uso más frecuente del sonido espacial es que parece que es emanante de un objeto real o virtual del mundo. Por lo tanto, los sonidos espaciales pueden llegar a ser el más apropiado de estos objetos.

Tenga en cuenta que la precisión percibida del sonido espacial significa que un sonido no debe emitir necesariamente desde el centro de un objeto, ya que la diferencia será apreciable en función del tamaño del objeto y de la distancia del usuario. Con los objetos pequeños, el punto central del objeto suele ser suficiente. En el caso de objetos grandes, puede que desee un emisor de sonido o varios emisores en la ubicación específica del objeto que se supone que está produciendo el sonido.

**Normalizar todos los sonidos**

La atenuación de distancia se produce rápidamente en el primer medidor del usuario, como en el mundo real. Todos los archivos de audio se deben normalizar para garantizar la atenuación física de la distancia y asegurarse de que se pueda oír un sonido cuando se encuentren varios medidores (cuando proceda). El motor de audio espacial controlará la atenuación necesaria para que un sonido "se sienta" como está a cierta distancia (con una combinación de atenuación e "indicaciones de distancia") y aplicar cualquier atenuación encima de eso podría reducir el efecto. Fuera de la simulación de un objeto real, es probable que la caída de la distancia inicial de los sonidos de *sonido espacial* sea lo suficientemente grande como para una combinación adecuada del audio.

**Detección de objetos e interfaces de usuario**

Al utilizar las señales de audio para dirigir la atención del usuario más allá de la vista actual, el sonido debe ser audible y destacado en la mezcla, por encima de los sonidos estéreo y de cualquier otro sonido espacial que pudiera distraerse de la señal de audio direccional. En el caso de los sonidos y la música que están asociados a un elemento de la interfaz de usuario (por ejemplo, un menú), el emisor de sonido se debe adjuntar a ese objeto. El sonido estéreo y otra reproducción de audio no posicional pueden dificultar la búsqueda de elementos espaciales (vea más arriba: evitar el enmascaramiento espacial).

**Usar el sonido espacial sobre el sonido 3D estándar lo máximo posible**

En la realidad mixta, para obtener la mejor experiencia de usuario, el audio 3D se debe lograr utilizando un sonido espacial en lugar de tecnologías de audio 3D heredadas. En general, la espacialización mejorada merece la pena el pequeño costo de la CPU en comparación con el sonido 3D estándar. El audio 3D estándar se puede usar para sonidos de baja prioridad, sonidos que están espaciales pero no necesariamente asociados a un objeto físico o virtual, y objetos que el usuario nunca necesita buscar para interactuar con la aplicación.

## <a name="see-also"></a>Consulta también
* [Sonido espacial](spatial-sound.md)
* [Asignación espacial](spatial-mapping.md)
