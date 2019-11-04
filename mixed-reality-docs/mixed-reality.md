---
title: ¿Qué es la realidad mixta?
description: En este artículo se define la realidad mixta y se muestran los dispositivos sencillos de AR y VR, así como los dispositivos de Windows Mixed Reality, como Microsoft HoloLens y Windows Mixed Reality, que se encuentran a lo largo del espectro de realidad mixta.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality, Holographic, ar, VR, Mr, XR, realidad aumentada, realidad virtual, explicación
ms.openlocfilehash: 83beca8b6abad56fc37800ddfc9faad0d21859bf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437876"
---
# <a name="what-is-mixed-reality"></a>¿Qué es la realidad mixta?

La realidad mixta es el resultado de fusionar el mundo físico con el mundo digital. La realidad mixta es el siguiente paso evolutivo en la interacción del ser humano, los equipos y el entornos. Ofrece posibilidades que antes solo eran posibles en nuestra imaginación. Es posible gracias a los avances en Computer Vision, la potencia de procesamiento gráfico, la tecnología de pantalla y los sistemas de entrada. El término *Mixed Reality* se presentó originalmente en un papel de 1994 de Paul Milgram y Fumio Kishino, "se[muestra una taxonomía de la realidad visual de la realidad mixta](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)". En este documento se ha introducido el concepto de *continuum de virtualización*y se ha centrado en cómo se muestra la categorización de la taxonomía aplicada. Desde entonces, la aplicación de realidad mixta va más allá de las pantallas. También incluye la entrada del entorno, el sonido espacial y la ubicación.

![el espectro de realidad mixta](images/MixedRealitySpectrum-worlds.jpg)<br>
*La realidad mixta es el resultado de mezclar el mundo físico con el mundo digital.*

<br>

---

## <a name="environmental-input-and-perception"></a>Entrada y percepción del entorno

En las últimas décadas, la relación entre la entrada del equipo y el usuario se ha explorado bien. Incluso tiene una disciplina muy estudiada conocida como *interacción del equipo humano* o HCl. La entrada humana se realiza a través de una gran variedad de medios, como teclados, ratones, toque, tinta, voz e incluso seguimiento del esqueleto de Kinect.

Los avances en los sensores y el procesamiento dan lugar a una nueva área de entrada del equipo desde los entornos. La interacción entre equipos y entornos es realmente una comprensión o *percepción*del entorno. Por lo tanto, los nombres de API de Windows que revelan información del entorno se denominan [API de percepción](https://docs.microsoft.com/uwp/api/Windows.Perception). La entrada del entorno captura elementos como la posición de una persona en el mundo (por ejemplo, el seguimiento de los [cabezales](coordinate-systems.md)), las superficies y los límites (por ejemplo, la [asignación espacial](spatial-mapping.md) y el conocimiento de la [escena](scene-understanding.md)), la iluminación ambiente, el sonido ambiental, el reconocimiento de objetos, y ubicación.

<br>



:::row:::
    :::column:::
        Ahora, la combinación de los**datos de procesamiento, entrada humana e información del entorno**de tres equipos establece la oportunidad de crear verdaderas experiencias de realidad mixta. El movimiento a través del mundo físico puede traducirse al movimiento en el mundo digital. Los límites del mundo físico pueden influir en las experiencias de la aplicación, como la reproducción de juegos, en el mundo digital. Sin la intervención del entorno, las experiencias no pueden mezclar entre realidad real y digital.<br>
        <br>
        *Imagen: las interacciones entre equipos, seres humanos y entornos.*
    :::column-end:::
        :::column:::
       ![Diagrama de Venn que muestra las interacciones entre equipos, seres humanos y entornos](images/mixed-reality-venn-diagram-300px.png)<br> 
    :::column-end:::
:::row-end:::

<br>

---


## <a name="the-mixed-reality-spectrum"></a>El espectro de realidad mixta

Dado que la realidad mixta mezcla los mundos físicos y digitales, estos dos hechos definen los extremos polares de un espectro conocido como el continuum de la virtualización. Para simplificar, hacemos referencia a esto como el *espectro de realidad mixta*. En el lado izquierdo tenemos la realidad física en la que nosotros somos humano, en el lado derecho, tenemos la realidad digital correspondiente.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Aumento frente a realidad virtual

La mayoría de los teléfonos móviles del mercado hoy en día tienen poca o ninguna funcionalidad de comprensión medioambiental. Por lo tanto, las experiencias que ofrecen no pueden combinarse entre realidad física y digital. Las experiencias que superponen los gráficos en las secuencias de vídeo del mundo físico son la *realidad aumentada*. Las experiencias que tapaba la vista para presentar una experiencia digital son la *realidad virtual*. Como puede ver, las experiencias habilitadas entre estos dos extremos son de *realidad mixta*:
* A partir del mundo físico, colocar un objeto digital, como un holograma, como si estuviera realmente ahí.
* A partir del mundo físico, una representación digital de otra persona, un avatar, muestra la ubicación en la que estaban de pie al pasar notas. En otras palabras, experiencias que representan la colaboración asincrónica en distintos momentos en el tiempo.
* A partir de un mundo digital, los límites físicos del mundo físico, como las paredes y el mobiliario, aparecen de forma digital dentro de la experiencia para ayudar a los usuarios a evitar objetos físicos.


<br>

![el espectro de realidad mixta](images/MixedRealitySpectrum.jpg)<br>
*Specturm de realidad mixta*

<br>

Hoy en día, la realidad más aumentada y las ofertas de realidad virtual representan una parte muy pequeña de este espectro. Sin embargo, son subconjuntos del espectro de realidad mixta más grande. Windows 10 se ha creado pensando en todo el espectro y permite mezclar representaciones digitales de personas, lugares y cosas con el mundo real.




## <a name="devices-and-experiences"></a>Dispositivos y experiencias


Hay dos tipos principales de dispositivos que proporcionan experiencias de Windows Mixed Reality:
1. **Dispositivos holográficas.** Se caracterizan por la capacidad del dispositivo de colocar contenido digital en el mundo real como si estuviera en realidad.
2. **Dispositivos envolventes.** Estos se caracterizan por la capacidad del dispositivo para crear una sensación de "presencia": ocultar el mundo físico y reemplazarlo por una experiencia digital.

<table>
<tr>
<th width="20%"> Característica</th><th width="40%"> Dispositivos holográficas</th><th width="40%"> Dispositivos envolventes</th>
</tr><tr>
<td> Dispositivo de ejemplo</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer edición de desarrollo de Windows Mixed Reality<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Pantalla</td><td> <i>Ver: visualización.</i> Permite al usuario ver el entorno físico mientras tiene los auriculares.</td><td> <i>Presentación opaca.</i> Bloquea el entorno físico mientras se contiene el casco.</td>
</tr><tr>
<td> Marcha</td><td> Movimiento de seis grados de libertad completo, rotación y traslación.</td><td> Movimiento de seis grados de libertad completo, rotación y traslación.</td>
</tr>
</table>

Tenga en cuenta que si un dispositivo está conectado o acoplado a un equipo independiente (a través de un cable USB o Wi-Fi) o autónomo (untethered), no refleja si un dispositivo es Holographic o envolvente. Ciertamente, las características que mejoran la movilidad conducen a mejores experiencias y los dispositivos holográficas y envolventes podrían estar anclados o untethered.


El avance tecnológico es lo que ha habilitado experiencias de realidad mixta. Actualmente no hay ningún dispositivo que pueda ejecutar experiencias en todo el espectro. Sin embargo, Windows 10 proporciona una plataforma de realidad mixta común para los desarrolladores y los fabricantes de dispositivos. Los dispositivos de hoy en día pueden admitir un intervalo específico dentro del espectro de realidad mixta. Con el tiempo, los nuevos dispositivos expandirán ese intervalo. En el futuro, los dispositivos holográficas serán más envolventes y los dispositivos envolventes serán más holográficas.

<br>

![tipos de dispositivo en el espectro de realidad mixta](images/MixedRealitySpectrum-devices.jpg)<br>
*Dónde existen los dispositivos en el espectro de realidad mixta*

A menudo, es mejor pensar en qué tipo de experiencia desea crear una aplicación o un desarrollador de juegos. Las experiencias normalmente se destinan a un punto o parte específicos del espectro. Después, los desarrolladores deben tener en cuenta las capacidades de los dispositivos a los que desean dirigirse. Por ejemplo, las experiencias que dependen del mundo físico se ejecutarán mejor en HoloLens.
* **Hacia la izquierda (la realidad casi física).** Los usuarios permanecen presentes en su entorno físico y nunca se crean para creer que han dejado ese entorno.
* **En el centro (realidad totalmente mixta).** Estas experiencias combinan el mundo real y el mundo digital. Los visores que han visto la película [Jumanji](https://en.wikipedia.org/wiki/Jumanji) pueden conciliar el modo en que la estructura física de la casa en la que tuvo lugar la historia se ha fusionado con un entorno selva.
* **Hacia la derecha (casi digital reality).** Los usuarios experimentan un entorno completamente digital y no saben lo que ocurre en el entorno físico.


## <a name="see-also"></a>Consulta también

* [¿Qué es un holograma?](hologram.md)
* [Descripción de los conceptos básicos de la realidad mixta](index.md#understand-the-basics)
* [Empezar a crear y crear prototipos](design.md)
* [Conozca las herramientas y la arquitectura](development.md)

