---
title: Color, claro y materiales
description: Diseñar el contenido de la realidad mixta requiere una consideración cuidadosa de color, iluminación y materiales para cada uno de los activos visuales utilizados en su experiencia.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, color, luz, materiales
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601378"
---
# <a name="color-light-and-materials"></a>Color, claro y materiales

Diseñar el contenido de la realidad mixta requiere una consideración cuidadosa de color, iluminación y materiales para cada uno de los activos visuales utilizados en su experiencia. Estas decisiones pueden para fines estéticos, como el uso de luz y material para establecer el tono de un entorno envolvente y funcionales propósitos, como el uso de colores sorprendente avisos a los usuarios de una acción inminente. Cada una de estas decisiones debe sopesar en comparación con las oportunidades y restricciones de dispositivo de destino de su experiencia.

A continuación se muestran directrices específicas a los recursos de representación en auriculares envolventes y holográficas. Muchas de ellas se vinculan estrechamente a otras áreas técnicas y encontrará una lista de temas relacionados en el [Vea también](color,-light-and-materials.md#see-also) sección al final de este artículo.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>Representación en envolventes frente a dispositivos holográficas

Contenido representado en inmersivos aparecerá visualmente diferente en comparación con el contenido representado de auriculares holográficas. Mientras inmersivos suele representan el contenido tanto como cabría esperar en una pantalla 2D, auriculares holográficas como el uso de HoloLens muestra transparente, secuencial de color RGB a hologramas representa.

Dedicar tiempo para probar sus experiencias holográficas auriculares holográfica. La apariencia del contenido, incluso si se ha creado específicamente para dispositivos holográficas, variarán tal como se muestra en los monitores secundarios, las instantáneas y en la vista del espectador. No olvide caminar alrededor de las experiencias con un dispositivo, las pruebas de la iluminación de hologramas y observando desde todos los lados (así como desde arriba y a continuación) cómo se representa el contenido. No olvide probar en una variedad de opciones de brillo en el dispositivo, ya que es poco probable que todos los usuarios compartirán supone el valor predeterminado, así como un conjunto diverso de iluminación.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Aspectos básicos de la representación en dispositivos holográficas
* **Dispositivos holográficas tienen pantallas aditivos** – hologramas se crean mediante la adición de luz a la luz desde el mundo real: blanco brillante, aparecerá al negro aparecerá transparente.
* **Impacto de colores varía según el entorno del usuario** : hay muchas condiciones de iluminación diversos en la sala de un usuario. Crear contenido con los niveles adecuados de contraste para conseguir una mayor claridad.
* **Evitar la iluminación dinámica** – hologramas que se iluminación uniformemente en experiencias holográficas son las más eficaces. Utilizando la iluminación dinámica avanzada, superará probablemente las capacidades de sombreadores móviles.

## <a name="designing-with-color"></a>Diseñar con color

Dada la naturaleza de las pantallas de suma, algunos colores pueden aparecer diferentes en pantallas holográficas. Algunos colores se mostrará el mensaje en entornos de iluminación mientras que otras personas aparecerán como menos alto impacto. Colores fríos tienden a desvanecen en segundo plano mientras colores cálidos saltar al primer plano. Tenga en cuenta estos factores cuando explore color en sus experiencias:
* **Valor comprendido entre** -HoloLens se beneficia de un "amplia gama" de color, conceptualmente similar a Adobe RGB. Como resultado, pueden presentar algunos colores diferentes calidades y representación en el dispositivo.
* **Gamma** -el brillo y contraste de la imagen representada variará entre dispositivos envolventes y holográficas. A menudo aparecen estas diferencias de dispositivo realizar las áreas oscuras de color y las sombras, más o menos brillante.
* **Separación de colores** -también se denomina "desglose color" o "halos color", la separación de colores con más frecuencia se produce con el traslado hologramas (incluido el cursor) cuando un usuario realiza un seguimiento de los objetos con sus ojos.
* **Color uniformidad** -normalmente se representan hologramas brillante suficiente para que mantengan uniformidad de color, independientemente del fondo. Las áreas grandes pueden quedar borrosa. Evitar áreas grandes de colores brillantes y sólidos.
* **Representación colores claros** -parece muy brillante de blanco y debe usarse con moderación. Para la mayoría de los casos, considere la posibilidad de un valor en blanco en torno a R 235 G 235 B 235. Grandes áreas brillantes pueden causar molestias del usuario.

**Representación de colores oscuros**

Dada la naturaleza de las pantallas de suma, colores oscuros aparecen transparentes. Un objeto de color negro sólido aparecerá no difiere del mundo real. Canal alfa de vea a continuación. Para dar la apariencia de "black" Pruebe con un valor RGB gris oscuro muy como 16,16,16.

![Normal frente a la amplia gama de colores](images/640px-widegamut.png)<br>
*Normal frente a la amplia gama de colores*

## <a name="technical-considerations"></a>Consideraciones técnicas
* **Alias** -se puede considerar el uso de alias, escalonadas o "peldaños" donde el borde de la geometría de un holograma toca el mundo real. Uso de las texturas con gran detalle puede agravar este efecto. Se deben asignar las texturas y habilita el filtrado. Considere la posibilidad de difuminación los bordes de hologramas o agregar una textura que crea un borde negro borde alrededor de los objetos. Siempre que sea posible, evite geometría fino.
* **Canal alfa** -debe borrar el canal alfa a totalmente transparente para cualquier parte donde no está representando un holograma. Salir de los clientes potenciales indefinidos alfabéticos para artefactos visuales al tomar imágenes o vídeos desde el dispositivo o con la vista del espectador.
* **Textura suavizando** : puesto que es la luz aditivos muestra holográfica, es mejor evitar las regiones grandes de color sólido, brillante como a menudo no producen el efecto visual deseado.

## <a name="storytelling-with-light-and-color"></a>Contar historias con luz y color

Luz y color pueden ayudar a sus hologramas aparecen de manera más natural en de un usuario entorno, así como proporcionan orientación y ayuda para el usuario. Para la experiencia holográfica, tenga en cuenta estos factores mientras explora la iluminación y color:
* **Las viñetas** -un efecto de 'viñeta' oscurecer materiales puede ayudar a centrar la atención del usuario en el centro del campo de visión. Este efecto oscurece material del holograma en algunos radius del objeto vector mirada del usuario. Tenga en cuenta que esto también es eficaz cuando el usuario ve hologramas desde un ángulo oblicuo o echar un vistazo.
* **Énfasis** -llamar la atención sobre los objetos o los puntos de interacción por colores, brillo, de contraste e iluminación. Para conocer más métodos de iluminación en contar historias, consulte [píxel cinematografía - un enfoque de iluminación de gráficos para PC](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).

![Uso de color para mostrar de énfasis para los elementos de contar historias, que aquí se muestra en una escena de fragmentos.](images/640px-fragments.jpg)<br>
*Uso de colores para mostrar de énfasis para los elementos de contar historias, se muestra a continuación en una escena de [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*

## <a name="see-also"></a>Vea también
* [Separación de colores](hologram-stability.md#color-separation)
* [Hologramas](hologram.md)
* [Idioma de Microsoft Design - color](https://www.microsoft.com/design/color)
* [Plataforma universal de Windows - color](https://docs.microsoft.com/windows/uwp/style/color)
