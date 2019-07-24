---
title: Escala
description: Una clave para mostrar el contenido que parece realista en forma holográfica es imitar las estadísticas visuales del mundo real lo más cerca posible.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, estilo, diseño
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524116"
---
# <a name="scale"></a>Escala

Una clave para mostrar el contenido que parece realista en forma holográfica es imitar las estadísticas visuales del mundo real lo más cerca posible. Esto significa que se incorporan tantas indicaciones visuales como podamos que nos ayuden (en el mundo real) a entender dónde se encuentran los objetos, lo grande que son y de qué se crean. La escala de un objeto es uno de los más importantes de esas indicaciones visuales, lo que da a un visor un sentido del tamaño de un objeto, así como las entradas de su ubicación (especialmente para los objetos que tienen un tamaño conocido). Además, la visualización de objetos en escala real se ha visto como uno de los diferenciadores de experiencia clave para la realidad mixta en general, algo que no ha sido posible en la visualización basada en pantalla previamente.

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Cómo sugerir la escala de objetos y entornos

Hay muchas maneras de sugerir la escala de un objeto, algunas de las cuales tienen efectos posibles en otros factores de percepción. La clave es simplemente mostrar los objetos en un tamaño ' real ' y mantener ese tamaño realista a medida que los usuarios se mueven. Esto significa que los hologramas ocuparán una cantidad diferente del ángulo visual de un usuario a medida que se acerquen o alejen, del mismo modo que los objetos reales.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Uso de la distancia de los objetos a medida que se presentan al usuario

Un método común es el uso de la distancia de los objetos a medida que se presentan al usuario. Por ejemplo, considere la posibilidad de visualizar un automóvil de gran familia delante del usuario. Si el coche estuviera directamente delante de ellos, dentro de la longitud de ARM, sería demasiado grande para caber en el campo de vista del usuario. Esto requeriría que el usuario desplace el encabezado y el cuerpo para comprender el completo del objeto. Si el coche se colocó fuera (en todo el salón), el usuario puede establecer un sentido de escala; para ello, Ve el completo del objeto en su campo de vista y, a continuación, se mueve a él para inspeccionar áreas en detalle.

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec) usó esta técnica para crear una experiencia de sala de exposición para un coche nuevo, con la escala del coche holográfica de una forma realista e intuitiva para el usuario. La experiencia comienza con un holograma del coche en una tabla física, lo que permite al usuario comprender el tamaño y la forma totales del modelo. Más adelante en la experiencia, el coche se expande a una escala mayor (más allá del tamaño del campo de vista del dispositivo), pero, puesto que el usuario ya adquirió un fotograma de referencia del modelo más pequeño, puede navegar adecuadamente por las características del coche.

![Experiencia de Volvo Cars para HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*Experiencia de Volvo Cars para HoloLens*

### <a name="use-holograms-to-modify-the-users-real-space"></a>Usar hologramas para modificar el espacio real del usuario

Otro método consiste en usar hologramas para modificar el espacio real del usuario, reemplazando los planos laterales o techos existentes con entornos o anexando "huecos" o "ventanas", lo que permite que los objetos con un tamaño excesivo parezcan "desplazarse" por el espacio físico. Por ejemplo, un árbol grande podría no caber en la mayoría de los salones de los usuarios, pero al colocar un cielo virtual en el límite superior, el espacio físico se expande en el virtual. Esto permite al usuario desplazarse por la base del árbol virtual y recopilar una idea de la escala de cómo aparecería en la vida real y después buscar para ver que se extiende mucho más allá del espacio físico del salón.

[Minecraft](https://minecraft.net/) desarrolló una experiencia de concepto mediante una técnica similar. Al agregar una ventana virtual a una superficie física de una habitación, los objetos existentes en el salón se colocan en el contexto de un entorno de gran tamaño, más allá de las limitaciones de escala física de la habitación.

![Experiencia de concepto de Minecraft para HoloLens](images/800px-minecraftwindow-640px.jpg)<br>
*Experiencia de concepto de Minecraft para HoloLens*

## <a name="experimenting-with-scale"></a>Experimentación con escala

En algunos casos, los diseñadores han experimentado la modificación de la escala (cambiando el tamaño "real" mostrado del objeto) mientras se mantiene una única posición del objeto, para aproximar un objeto que se acerque más o más a un visor sin ningún movimiento real. Esto se probó en algunos casos como una forma de simular la visualización vertical de los elementos, a la vez que sigue respetando las posibles limitaciones de comodidad de ver el contenido virtual más cerca de la "zona de confort" que sugeriría.

Sin embargo, esto puede crear algunos artefactos posibles en la experiencia:
* En el caso de los objetos virtuales que representan algún objeto con un tamaño "conocido" en el visor, el cambio de la escala sin cambiar la posición conduce a indicaciones visuales en conflicto: los ojos todavía pueden "ver" el objeto a cierta profundidad debido a las vergence de las pilas (vea la [comodidad](comfort.md) artículo para obtener más información sobre esto), pero el tamaño actúa como una señal de cierre de sesión que el objeto podría estar más cerca. Estas claves conflictivas conducen a las percepciones de confusión: los visores ven a menudo el objeto como permanece en su lugar (debido a la indicación de profundidad constante), pero aumentan rápidamente.
* En algunos casos, el cambio de escala se considera como una indicación de "tela" en su lugar, donde el objeto puede o no verse para cambiar la escala de un visor, pero parece moverse directamente hacia los ojos del espectador (lo que puede ser un repentino incómodo).
* Con las superficies de comparación en el mundo real, los cambios de escalado a veces se ven como una posición cambiante a lo largo de varios ejes: es posible que los objetos parezcan inferiores en lugar de moverse más cerca (similar en una proyección 2D del movimiento 3D en algunos casos).
* Por último, en el caso de los objetos sin un tamaño conocido del "mundo real" (por ejemplo, formas arbitrarias con tamaños arbitrarios, elementos de la interfaz de usuario, etc.), cambiar la escala puede actuar funcionalmente como una manera de imitar los cambios de distancia: los visores no tienen tantas guías arriba preexistentes como para comprenda el tamaño o la ubicación verdaderos del objeto, por lo que la escala se puede procesar como una pista más importante.

## <a name="see-also"></a>Vea también
* [Color, luz y materiales](color,-light-and-materials.md)
* [Tipografía](typography.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
