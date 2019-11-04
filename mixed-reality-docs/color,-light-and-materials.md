---
title: Color, Light y material
description: El diseño de contenido para la realidad mixta requiere considerar con cautela el color, la iluminación y los materiales de cada uno de los recursos visuales que se usan en tu experiencia.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, color, Light, material
ms.openlocfilehash: c49d88c2bb53c07adcb77e8dbb0e3cd77e1e78ae
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436405"
---
# <a name="color-light-and-materials"></a>Color, Light y material

El diseño de contenido para la realidad mixta requiere considerar con cautela el color, la iluminación y los materiales de cada uno de los recursos visuales que se usan en tu experiencia. Estas decisiones pueden ser para fines estéticos, como usar la luz y el material para establecer el tono de un entorno envolvente y propósitos funcionales, como el uso de colores impactantes para alertar a los usuarios de una acción inminente. Cada una de estas decisiones se debe sopesar con respecto a las oportunidades y las restricciones del dispositivo de destino de su experiencia.

A continuación se muestran las instrucciones específicas para la representación de recursos en auriculares envolvente y holográfica. Muchos de ellos están estrechamente vinculados a otras áreas técnicas y se puede encontrar una lista de temas relacionados en la sección [Consulte también](color,-light-and-materials.md#see-also) al final de este artículo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Representación en dispositivos envolventes frente a holográficas

El contenido representado en auriculares envolventes tendrá una apariencia visual diferente en comparación con el contenido representado en auriculares holográficas. Aunque los auriculares más envolventes suelen representar el contenido de la forma que cabría esperar en una pantalla 2D, los auriculares holográficas como HoloLens usan el color de secuencia de colores, consulte la muestra sobre RGB para representar hologramas.

Siempre Tómese tiempo para probar sus experiencias holográficas en un casco holográfica. La apariencia del contenido, incluso si se crea específicamente para dispositivos holográficas, variará según se muestra en monitores secundarios, instantáneas y en la vista Spectator. Recuerde recorrer las experiencias con un dispositivo, probar la iluminación de los hologramas y observar a partir de todos los lados (así como de arriba y abajo) cómo se representa el contenido. Asegúrese de probar una variedad de opciones de brillo en el dispositivo, ya que es improbable que todos los usuarios compartan un valor predeterminado asumido, así como un conjunto diverso de condiciones de iluminación.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Aspectos básicos de la representación en dispositivos holográficas
* Los **dispositivos holográficas tienen pantallas aditivas** : los hologramas se crean agregando luz a la luz del mundo real: el blanco aparecerá brillante, mientras que el negro aparecerá transparente.
* **El impacto de los colores varía en el entorno del usuario** : hay muchas condiciones de iluminación diferentes en el salón de un usuario. Cree contenido con los niveles de contraste adecuados para ayudar a mejorar la claridad.
* **Evitar la iluminación dinámica** : los hologramas que están iluminados uniformemente en las experiencias holográficas son los más eficaces. Con la iluminación avanzada, el alumbrado dinámico probablemente superará las capacidades de los dispositivos móviles. Cuando se requiere la iluminación dinámica, se recomienda usar el [sombreador estándar del kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md). 

## <a name="designing-with-color"></a>Diseñar con color

Debido a la naturaleza de las pantallas aditivas, algunos colores pueden aparecer diferentes en pantallas holográficas. Algunos colores aparecerán en entornos de iluminación, mientras que otros aparecerán como menos impactantes. Los colores fríos tienden a recede en segundo plano mientras que los colores cálidos saltan al primer plano. Tenga en cuenta estos factores a medida que explora el color de sus experiencias:
* **Gama** -HoloLens se beneficia de una "amplia gama" de color, conceptualmente similar a Adobe RGB. Como resultado, algunos colores pueden presentar cualidades y representaciones diferentes en el dispositivo.
* **Gamma** : el brillo y el contraste de la imagen representada variarán entre dispositivos envolventes y holográficas. Estas diferencias de dispositivo suelen parecer que las áreas oscuras de color y de sombras son más o menos brillantes.
* **Separación de colores** : también denominada "división de color" o "halo de color", la separación de colores suele producirse con los hologramas móviles (incluido el cursor) cuando un usuario realiza un seguimiento de los objetos con sus ojos.
* **Uniformidad de color** : normalmente los hologramas se representan lo suficientemente brillantes como para mantener la uniformidad del color, independientemente del fondo. Es posible que las áreas de gran tamaño estén desfavorecidas. Evite grandes regiones de color sólido y brillante.
* **Colores claros de representación** : el blanco aparece muy brillante y debe usarse con moderación. En la mayoría de los casos, considere un valor blanco alrededor de R 235 G 235 B 235. Las áreas brillantes de gran tamaño pueden ocasionar la molestia del usuario.

**Representación de colores oscuros**

Debido a la naturaleza de las pantallas aditivas, los colores oscuros aparecen transparentes. Un objeto de negro sólido no será diferente del mundo real. Consulte canal alfa a continuación. Para dar la apariencia de "Black", pruebe un valor RGB gris muy oscuro como 16, 16, 16.

![gama de colores normal frente a ancho](images/640px-widegamut.png)<br>
*Gama de colores normal frente a ancho*

## <a name="technical-considerations"></a>Consideraciones técnicas
* **Alias** : tenga de alias, escalonados o "pasos de escalera", donde el borde de la geometría de un holograma cumple el mundo real. El uso de texturas con un alto nivel de detalle puede agravar este efecto. Las texturas deben estar asignadas y filtrados habilitados. Considere la posibilidad de difuminar los bordes de los hologramas o de agregar una textura que cree un borde de borde negro alrededor de los objetos. Evite la geometría fina siempre que sea posible.
* **Canal alfa** : debe borrar el canal alfa completamente transparente para cualquier parte en la que no se represente un holograma. Dejar el alfa sin definir conduce a artefactos visuales al tomar imágenes o vídeos del dispositivo o con la vista Spectator.
* **Suavizado de textura** : puesto que la luz es aditiva en pantallas holográficas, es mejor evitar grandes regiones de color sólido y brillante, ya que a menudo no producen el efecto visual deseado.

## <a name="storytelling-with-light-and-color"></a>Contar historias con luz y color

La luz y el color pueden ayudar a que los hologramas aparezcan de forma más natural en el entorno de un usuario, así como ofrecer orientación y ayuda para el usuario. En el caso de las experiencias holográficas, tenga en cuenta estos factores a medida que explora la iluminación y el color:

:::row:::
    :::column:::
* **Viñetas** : un efecto de ' viñetas ' para oscurecer materiales puede ayudar a centrar la atención del usuario en el centro del campo de la vista. Este efecto oscurece el material del holograma en algún radio desde el vector de mirada del usuario. Tenga en cuenta que esto también es efectivo cuando el usuario ve los hologramas de un ángulo oblicuo o glancing.<br>
* Recalque la atención de los objetos o puntos de interacción mediante el **contraste de los** colores, el brillo y la iluminación. Para obtener una visión más detallada de los métodos de iluminación de contar historias, consulte el cine de los [píxeles: un enfoque de iluminación para gráficos informáticos](https://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).<br>
        <br>
        *Imagen: uso de color para mostrar el énfasis de los elementos contar historias, que se muestran aquí en una escena de [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*
    :::column-end:::
        :::column:::
        ![Uso de color para mostrar el énfasis de los elementos contar historias, que se muestran aquí en una escena de fragmentos.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Consulta también
* [Separación de colores](hologram-stability.md#color-separation)
* [Hologramas](hologram.md)
* [Lenguaje de diseño de Microsoft: color](https://www.microsoft.com/design/color)
* [Color de Plataforma universal de Windows](https://docs.microsoft.com/windows/uwp/style/color)
