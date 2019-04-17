---
title: ¿Qué es la realidad mixta?
description: En este artículo se define la realidad mixta y se muestra donde se colocan los dispositivos de AR y VR simple, así como los dispositivos de Windows Mixed Reality, como Microsoft HoloLens e inmersivos Windows Mixed Reality, espectro de realidad mixta.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, holográfica, ar, vr, mr, xr, realidad aumentada de realidad virtual, una explicación
ms.openlocfilehash: 3f6000b3d700d7c13f1efa13a81561464f8fdad1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605726"
---
# <a name="what-is-mixed-reality"></a>¿Qué es la realidad mixta?

Realidad mixta es el resultado de combinar el mundo físico con el mundo digital. Realidad mixta es la siguiente evolución en la interacción humana, el equipo y el entorno y desbloquea las posibilidades que antes estaban restringidas a nuestro imaginación. Es posible por los avances en computer vision, potencia de procesamiento gráficos, tecnología de visualización y sistemas de entrada. El término *la realidad mixta* originalmente se presentó en un documento de 1994 por Paul Milgram y Fumio Kishino, "[una taxonomía mixed Reality Visual muestra](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)." Su papel introdujo el concepto de la *continuum virtuality* y se centra en cómo se muestra la categorización de taxonomía aplicado a. Desde entonces, la aplicación de realidad mixta va más allá de lo muestra, pero también incluye una entrada del entorno, espacial sonido y la ubicación.

## <a name="environmental-input-and-perception"></a>Percepción y entrada del entorno

![Diagrama de Venn que muestra las interacciones entre los equipos, los seres humanos y entornos](images/mixed-reality-venn-diagram-300px.png)<br> 

En las últimas décadas, la relación entre la entrada humana y la entrada de equipo se ha también han explorado. Incluso presenta una disciplina estudiada conocida como *interacción humana equipo* o HCI. Entrada humana se produce a través de diversos medios, incluida la teclados, mouse, táctil, lápiz, voz e incluso seguimiento esqueleto de Kinect.

Los avances en sensores y procesamiento se que dan lugar a una nueva área de entrada del equipo de entornos. La interacción entre los equipos y entornos es una descripción del entorno de forma eficaz, o *percepción*. Por lo tanto, se llama a los nombres de API de Windows que revelan información ambiental el [percepción API](https://docs.microsoft.com/uwp/api/Windows.Perception). Cosas como la posición de una persona del mundo captura la entrada del entorno (por ejemplo, [seguimiento principal](coordinate-systems.md)), superficies y los límites (p. ej. [asignación espacial](spatial-mapping.md) y [descripción espacial](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), iluminación ambiente, sonido del entorno, reconocimiento de objetos y ubicación.

Ahora, la combinación de todos los tres: procesamiento del equipo, entrada humana y la entrada del entorno: establece la oportunidad de crear experiencias de realidad mixta es true. Movimiento a través del mundo físico puede traducirse en movimiento en el mundo digital. Los límites en el mundo físico pueden influir en las experiencias de aplicación, como juegos, en el mundo digital. Sin entrada del entorno, no se pueden fusionar experiencias entre las realidades físicas y digitales.

## <a name="the-mixed-reality-spectrum"></a>El espectro de realidad mixta

Puesto que la realidad mixta es la combinación del mundo físico y el mundo digital, estas dos realidades definen los extremos de un espectro conocido como el espectro de virtuality polares. Por motivos de simplicidad, nos referiremos a ella como la *espectro de realidad mixta*. En el lado izquierdo tenemos realidad física en lo que nosotros, los humanos, existe. A continuación, en la parte derecha tenemos la realidad digital correspondiente.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

Mayoría de los teléfonos móviles en el mercado hoy en día no tienen poca o ninguna capacidades de comprensión del entorno. Por lo tanto no se pueden mezclar las experiencias que ofrecen entre las realidades físicas y digitales. Las experiencias de gráficos en secuencias de vídeo del mundo físico de superposición son *aumentada realidad*, y las experiencias que occlude la vista para presentar una experiencia digital son *de realidad virtual*. Como puede ver, las experiencias habilitadas entre estos dos extremos es *la realidad mixta*:
* A partir del mundo físico, colocar un objeto digital, como un holograma, como si fuese realmente ahí.
* Empezando por el mundo físico, una representación digital de otra persona – un avatar: muestra la ubicación donde estaban permanente al salir de notas. En otras palabras, las experiencias que representan la colaboración asincrónica en distintos puntos en el tiempo.
* A partir de un mundo digital, aparecen digitalmente límites físicos del mundo físico, como las paredes y muebles, dentro de la experiencia para ayudar a los usuarios evitar objetos físicos.

![El espectro de realidad mixta](images/mixed-reality-spectrum-550px.png)

Más de realidad aumentada y las ofertas de realidad virtual disponibles hoy en día representan una pequeña parte de este espectro. Sin embargo, son subconjuntos del mayor espectro de realidad mixta. Windows 10 se ha creado con todo el espectro en mente y permite fusión digitales representaciones de personas, lugares y cosas con el mundo real.

![Tipos de dispositivo en el espectro de realidad mixta](images/mixed-reality-spectrum-device-types-550px.png)

Hay dos tipos principales de dispositivos que ofrezcan experiencias de Windows Mixed Reality:
1. **Dispositivos holográficas.** Estos se caracterizan por la capacidad del dispositivo para colocar contenido digital en el mundo real, como si fuese realmente ahí.
2. **Dispositivos envolventes.** Estos se caracterizan por la capacidad del dispositivo para crear una sensación de "presencia" – ocultar el mundo físico y reemplazarlo con una experiencia digital.

<table>
<tr>
<th width="20%"> Característica</th><th width="40%"> Dispositivos holográficas</th><th width="40%"> Dispositivos envolventes</th>
</tr><tr>
<td> Dispositivo de ejemplo</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Windows Acer mixto realidad Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Pantalla</td><td> <i>Mostrar transparente.</i> Permite al usuario ver el entorno físico cuando se usan los auriculares.</td><td> <i>Mostrar opaco.</i> Bloquea el entorno físico cuando se usan los auriculares.</td>
</tr><tr>
<td> Movimiento</td><td> Completa el movimiento de seis grados de libertad, giro y traslación.</td><td> Completa el movimiento de seis grados de libertad, giro y traslación.</td>
</tr>
</table>

Tenga en cuenta que si un dispositivo está conectado a o bloqueado en un equipo independiente (mediante un cable USB o Wi-Fi) o autocontenida no (sin restricción) no refleja si un dispositivo es holográfica o envolventes. Sin duda, características que mejoran la responsable de movilidad para mejores experiencias y dispositivos holográficas y envolventes podrían estar bloqueadas o sin restricción.

## <a name="devices-and-experiences"></a>Dispositivos y experiencias

Avance tecnológico es lo que ha habilitado las experiencias de realidad mixta. No hay ningún dispositivo hoy en día que se puede ejecutar las experiencias en todo el espectro; Sin embargo, Windows 10 proporciona una plataforma común de realidad mixta para los fabricantes de dispositivos y los desarrolladores. Hoy en día, los dispositivos pueden admitir un intervalo específico del espectro de realidad mixta y con el tiempo nuevos dispositivos deben expanda ese intervalo. En el futuro, dispositivos holográficas estará más envolventes y dispositivos envolventes se convertirá en más holográficas.

![Donde colocar los dispositivos en el espectro de realidad mixta](images/mixed-reality-spectrum-device-placement-550px.png)

A menudo, es mejor pensar en qué tipo de experiencia de una aplicación o juego programador desea crear. Las experiencias normalmente tendrán como destino un momento concreto o parte en el espectro. A continuación, los desarrolladores deben considerar las capacidades de dispositivos que desean tener como destino. Por ejemplo, las experiencias que se basan en el mundo físico se ejecutan mejor HoloLens.
* **Hacia la izquierda (cerca de la realidad física).** Los usuarios continuarán presentes en su entorno físico y nunca se realizan para creer que le quedan ese entorno.
* **En el medio (Gestures totalmente).** Estas experiencias de blend perfectamente el mundo real y el mundo digital. Los usuarios que han visto la película [Jumanji](https://en.wikipedia.org/wiki/Jumanji) puede conciliar la forma en que se mezcla la estructura física de la casa donde la historia tuvo lugar con un entorno Selva.
* **Hacia la derecha (cerca de la realidad digital).** Los usuarios experimentan un entorno completamente digital y ajeno a lo que ocurre en el entorno físico en torno a ellas.


## <a name="see-also"></a>Vea también
* [Referencia de API: Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [Referencia de API: Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [Referencia de API: Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
