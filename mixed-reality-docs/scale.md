---
title: Escala
description: Una clave para mostrar el contenido que busca realista en formulario holográfica es imitar lo máximo posible de las estadísticas visuales del mundo real.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Diseño de Windows Mixed Reality, estilo,
ms.openlocfilehash: f13414bff7d84692e8e87aa2abdcded15627346f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598917"
---
# <a name="scale"></a>Escala

Una clave para mostrar el contenido que busca realista en formulario holográfica es imitar lo máximo posible de las estadísticas visuales del mundo real. Esto significa que se incorpora como muchas de las indicaciones visuales como sea posible que nos (en el mundo real) ayudan a comprender dónde están los objetos, qué tamaño son y que se realizan de. La escala de un objeto es una de las más importantes de esas indicaciones visuales, lo que proporciona un visor de una idea del tamaño de un objeto, así como indicaciones a su ubicación (especialmente para los objetos que tienen un tamaño conocido). Además, la visualización de objetos a escala real se ha visto como uno de los diferenciadores clave de experiencia de realidad mixta en general, algo que no era posible en basado en pantalla ver anteriormente.

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Cómo sugerir la escala de los objetos y entornos

Hay muchas maneras para sugerir la escala de un objeto, algunos de los cuales tienen posibles efectos de otros factores perceptuales. La clave es simplemente mostrar objetos con un tamaño de "real", y mantener ese tamaño realista como mover los usuarios. Esto significa que pueden tardar hasta una cantidad diferente de un ángulo visual de un usuario de un usuario hologramas cuando se lo más cerca o lejos aún más la misma manera que lo hacen los objetos reales.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Usar la distancia de los objetos que se presentan al usuario

Un método común consiste en utilizar la distancia de los objetos que se presentan al usuario. Por ejemplo, considere la posibilidad de visualizar un automóvil familiar gran delante del usuario. Si fuera el automóvil directamente frente a ellas, dentro de la longitud de arm, sería demasiado grande para caber en el campo de visión del usuario. Esto requeriría al usuario mover su cabeza y el cuerpo para comprender la totalidad del objeto. Si el vehículo se colocaron aún más lejos (a través de la sala), el usuario puede establecer una sensación de escala viendo la totalidad del objeto en su campo de visión, a continuación, mover a sí mismos más cercanos a ella para inspeccionar las áreas de detalle.

[Volvo](https://www.youtube.com/watch?v=DilzwF90vec) usa esta técnica para crear una experiencia de sala de exposición de un automóvil nuevo, utilizando la escala del automóvil holográfica de manera que pensaban realista e intuitivo para el usuario. La experiencia comienza con un holograma del automóvil en una tabla física, que permite al usuario a comprender el tamaño total y la forma del modelo. Más adelante en la experiencia, se expande el coche a una escala mayor (más allá del tamaño del campo de visión del dispositivo), pero, puesto que el usuario ha adquirido un marco de referencia desde el modelo más pequeño, puede navegar adecuadamente en torno a las características del automóvil.

![Experiencia de los automóviles Volvo para HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
*Experiencia de los automóviles Volvo para HoloLens*

### <a name="use-holograms-to-modify-the-users-real-space"></a>Use hologramas para modificar el espacio real del usuario

Otro método es usar hologramas para modificar el espacio real del usuario, reemplazando las paredes o techos existente con entornos o anexar 'agujeros' o 'windows', lo que permite objetos sobredimensionados a aparentemente 'vanguardista' el espacio físico. Por ejemplo, un árbol de gran tamaño podría no caber en salas de estar de la mayoría de los usuarios, pero colocando un cielo virtual de su límite superior, se expande el espacio físico en el virtual. Esto permite al usuario a caminar alrededor de la base del árbol virtual y obtener una idea de cómo podría aparecer en la vida real, a continuación, buscar para ver cómo se extienden más allá del espacio físico de la sala.

[Minecraft](https://minecraft.net/) desarrolló una experiencia de concepto mediante una técnica similar. Mediante la adición de una ventana virtual a una superficie física en una sala, los objetos existentes en la sala se colocan en el contexto de un entorno mucho mayor, más allá de las limitaciones físicas de escalado de la sala.

![Experiencia del concepto de Minecraft para HoloLens](images/800px-minecraftwindow-640px.jpg)<br>
*Experiencia del concepto de Minecraft para HoloLens*

## <a name="experimenting-with-scale"></a>Experimentar con escala

En algunos casos, los diseñadores han experimentado con la modificación del escalado (cambiando el tamaño de "real" mostrado del objeto) manteniendo una posición única del objeto, para aproximarse a un objeto que se obtienen más cerca o más allá de un visor sin ningún movimiento real. Se ha probado en algunos casos como una forma de simular descubrir visualización de elementos al tiempo que respeta posibles limitaciones de confort de visualización virtual contenido más cerca que sugeriría la "zona de comodidad".

Sin embargo esto puede crear algunos artefactos posibles en la experiencia:
* Para los objetos virtuales que representan un objeto con un tamaño 'conocido' en el Visor, cambiar la escala sin cambiar la posición conduce a indicaciones visuales en conflicto: es posible que igualmente los ojos "ver" el objeto en cierta profundidad debido a las indicaciones de vergence (consulte la [comodidad ](comfort.md) artículo para obtener más información sobre esto), pero el tamaño actúa como una indicación monocular que podría obtener el objeto más de cerca. Provocar percepciones confundirse estas pilas en conflicto: visores a menudo ve el objeto permanece en su lugar (debido a la pila constante profundidad) pero crece rápidamente.
* En algunos casos, el cambio de escala se ve como una indicación 'looming' en su lugar, donde el objeto puede o un visor no puede aparecer para cambiar la escala, pero parece ser móvil directamente hacia los ojos del (que pueden ser una sensación incómoda).
* Con superficies de comparación en el mundo real, dichos cambios de escala se puede observar a veces que el cambio de posición a lo largo de varios ejes: objetos pueden aparecer quitar inferior en lugar de mover más cercano (similar en una proyección 2D de movimiento 3D en algunos casos).
* Por último, para los objetos sin un tamaño conocido "real world" (p. ej. arbitrarios formas con tamaños arbitrarios, elementos de interfaz de usuario, etc.), puede cambiar la escala actúan funcionalmente como una manera para imitar los cambios en la distancia: visores no tiene tantas indicaciones preexistentes de arriba a abajo por la que se va a comprender el tamaño real del objeto o la ubicación, por lo que la escala se puede procesar como una indicación más importante.

## <a name="see-also"></a>Vea también
* [Color, claro y materiales](color,-light-and-materials.md)
* [Tipografía](typography.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
