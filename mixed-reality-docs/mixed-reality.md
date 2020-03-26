---
title: ¿Qué es la realidad mixta?
description: En este artículo se define la realidad mixta y se muestra dónde se encuentran los dispositivos sencillos de AR y VR, así como los dispositivos de Windows Mixed Reality, como Microsoft HoloLens y Windows Mixed Reality, en el espectro de la realidad mixta.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, holográfico, ar, vr, mr, xr, realidad aumentada, realidad virtual, explicación
ms.localizationpriority: high
ms.openlocfilehash: f170fe7a3353ac0cce1bd7532802eaff7a357494
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082079"
---
# <a name="what-is-mixed-reality"></a>¿Qué es la realidad mixta?

![Apuntar y confirmar con las manos en HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

La realidad mixta es el resultado de fusionar el mundo físico con el mundo digital. La realidad mixta es el siguiente paso evolutivo en la interacción del ser humano, los equipos y el entornos. Ofrece posibilidades que antes solo eran posibles en nuestra imaginación. Es posible gracias a los avances en Computer Vision, la potencia del procesamiento gráfico, la tecnología de visualización y los sistemas de entrada. El término *realidad mixta* se introdujo originalmente en un documento de 1994 de Paul Milgram y Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". En este documento se introdujo el concepto del *continuum de la virtualización* y se centraba en cómo la categorización de la taxonomía se aplicaba a las pantallas. Desde entonces, la aplicación de realidad mixta va más allá de las pantallas. También incluye la entrada del entorno, el sonido espacial y la ubicación.

![Espectro de la realidad mixta](images/mixedrealityspectrum-worlds.png)<br>
*Imagen: la realidad mixta es el resultado de fusionar el mundo físico con el mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada y percepción del entorno

En las últimas décadas, se ha explorado la relación entre la entrada de las personas y la del equipo. Incluso existe una disciplina muy estudiada conocida como la *interacción persona-equipo*  o HCl. La entrada humana se realiza a través de una gran variedad de medios, como teclados, ratones, toques, tinta, voz e incluso seguimiento del esqueleto de Kinect.

Los avances en los sensores y el procesamiento dan lugar a una nueva área de entrada del equipo desde los entornos. La interacción entre equipos y entornos es el reconocimiento o la *percepción* eficaz del entorno. Por lo tanto, los nombres de API en Windows que revelan la información del entorno se denominan [API de percepción](https://docs.microsoft.com/uwp/api/Windows.Perception). La entrada del entorno captura elementos como la posición de una persona en el mundo (por ejemplo, el [seguimiento de la cabeza](coordinate-systems.md)), las superficies y límites (por ejemplo, la [asignación espacial](spatial-mapping.md) y la [comprensión de la escena](scene-understanding.md)), la iluminación ambiente, el sonido ambiental, el reconocimiento de objetos y la ubicación.

<br>

![Diagrama de Venn que muestra las interacciones entre equipos, seres humanos y entornos](images/mixed-reality-venn-diagram-300px.png)<br> 
*Imagen: interacciones entre equipos, seres humanos y entornos.*

<br>

Ahora, la combinación de los tres, **el procesamiento del equipo, la entrada humana y la entrada del entorno**, ofrece la oportunidad de crear auténticas experiencias de realidad mixta. El movimiento a través del mundo físico puede traducirse al movimiento en el mundo digital. Los límites del mundo físico pueden influir en las experiencias de la aplicación, como jugar a un juego, en el mundo digital. Sin la entrada del entorno, las experiencias no pueden combinar la realidad física y la digital.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Espectro de la realidad mixta

Dado que la realidad mixta combina los mundos físico y digital, estas dos realidades definen los extremos polares de un espectro conocido como el continuum de la virtualización. Para simplificar, hacemos referencia a esto como el *espectro de realidad mixta*. En el lado izquierdo tenemos la realidad física en la que existimos nosotros, las personas, en el lado derecho, tenemos la realidad digital correspondiente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Realidad aumentada frente a virtual

La mayoría de los teléfonos móviles del mercado de hoy en día tienen poca o ninguna funcionalidad de reconocimiento de entorno. Por lo tanto, las experiencias que ofrecen no pueden combinar la realidad física y la digital. Las experiencias que superponen los gráficos en secuencias de vídeo del mundo físico son de *realidad aumentada*. Las experiencias que tapan tu visión para presentar una experiencia digital son de *realidad virtual*. Como puedes ver, las experiencias habilitadas entre estos dos extremos son de *realidad mixta*:
* A partir del mundo físico, colocar un objeto digital, como un holograma, como si estuviera realmente ahí.
* A partir del mundo físico, una representación digital de otra persona, un avatar, muestra la ubicación en la que estaban al dejar notas. Es decir, experiencias que representan la colaboración asincrónica en distintos momentos en el tiempo.
* A partir de un mundo digital, los límites físicos del mundo físico, como las paredes y el mobiliario, aparecen de forma digital dentro de la experiencia para ayudar a los usuarios a evitar los objetos físicos.


<br>

![Espectro de la realidad mixta](images/mixedrealityspectrum.png)<br>
*Imagen: espectro de la realidad mixta*

<br>

Hoy en día, la mayoría de las ofertas de realidad aumentada y de realidad virtual representan una parte muy pequeña de este espectro. Sin embargo, son subconjuntos del espectro mayor de realidad mixta. Windows 10 se ha creado pensando en todo el espectro y permite combinar representaciones digitales de personas, lugares y cosas con el mundo real.




## <a name="devices-and-experiences"></a>Dispositivos y experiencias


Hay dos tipos principales de dispositivos que proporcionan experiencias de Windows Mixed Reality:
1. **Dispositivos holográficos.** Se caracterizan por la capacidad del dispositivo de colocar contenido digital en el mundo real como si estuviera verdaderamente ahí.
2. **Dispositivos envolventes.** Estos se caracterizan por la capacidad del dispositivo de crear una sensación de "presencia": ocultar el mundo físico y reemplazarlo por una experiencia digital.

<table>
<tr>
<th width="30%"> Característica</th><th width="35%"> Dispositivos holográficos</th><th width="35%"> Dispositivos envolventes</th>
</tr><tr>
<td><strong>Dispositivo de ejemplo</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Visualización</strong></td><td> Visualización transparente. Permite al usuario ver el entorno físico cuando lleva el casco.</td><td> Visualización opaca. Bloquea el entorno físico cuando se lleva el casco.</td>
</tr><tr>
<td><strong>Movimiento</strong></td><td> Movimiento de seis grados de libertad completo, rotación y traslación.</td><td> Movimiento de seis grados de libertad completo, rotación y traslación.</td>
</tr>
</table>



Ten en cuenta que, independientemente de si un dispositivo está conectado o vinculado por una línea de puntos a un equipo independiente (a través de un cable USB o Wi-Fi) o es autónomo (sin línea de puntos), no se refleja si un dispositivo es holográfico o envolvente. Ciertamente, las características que mejoran la movilidad conducen a mejores experiencias y los dispositivos holográficos y envolventes podrían estar vinculados por una línea de puntos o no.


El avance tecnológico es lo que ha permitido las experiencias de realidad mixta. Actualmente no hay ningún dispositivo que pueda ejecutar experiencias en todo el espectro. Sin embargo, Windows 10 proporciona una plataforma de realidad mixta común para los desarrolladores y los fabricantes de dispositivos. Los dispositivos de hoy en día pueden admitir un intervalo específico dentro del espectro de realidad mixta. Con el tiempo, los nuevos dispositivos expandirán ese intervalo. En el futuro, los dispositivos holográficos serán más envolventes y los dispositivos envolventes serán más holográficos.

<br>

![Tipos de dispositivos en el espectro de realidad mixta](images/Final_WhatIsMixedReality07.png)<br>
*Imagen: lugar en el que existen los dispositivos en el espectro de realidad mixta*

A menudo, es mejor pensar en qué tipo de experiencia desea el desarrollador crear una aplicación o un juego. Las experiencias normalmente tienen como destino un punto específico o una parte del espectro. Después, los desarrolladores deben tener en cuenta las capacidades de los dispositivos a los que desean dirigirse. Por ejemplo, las experiencias que dependen del mundo físico se ejecutarán mejor en HoloLens.
* **Hacia la izquierda (realidad casi física).** Los usuarios permanecen presentes en su entorno físico y nunca se les hace creer que lo han abandonado.
* **En el centro (realidad totalmente mixta).** Estas experiencias combinan el mundo real y el mundo digital. Los espectadores que vieron la película [Jumanji](https://en.wikipedia.org/wiki/Jumanji) pueden conciliar el modo en que la estructura física de la casa en la que tuvo lugar la trama se combinó con un entorno de selva.
* **Hacia la derecha (realidad casi digital).** Los usuarios experimentan un entorno completamente digital y no saben lo que ocurre en el entorno físico que les rodea.


## <a name="see-also"></a>Consulta también

* [¿Qué es un holograma?](hologram.md)
* [Descripción de los conceptos básicos de la realidad mixta](index.md#understand-the-basics)
* [Empezar a crear y a generar prototipos](design.md)
* [Conocer las herramientas y la arquitectura](development.md)

