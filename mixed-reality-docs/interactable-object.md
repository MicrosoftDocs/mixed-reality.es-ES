---
title: Objeto interactuable
description: Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D. En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, interfaz de usuario, experiencia de usuario
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601178"
---
# <a name="interactable-object"></a>Objeto interactuable

Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D. En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya. Nada puede ser un **Interactuable objeto** que desencadena un evento. Un objeto interactuable puede representarse como nada una taza de café en la tabla a un globo flotante en el aire. Todavía hacemos uso de los botones tradicionales en determinados situación tal como se muestra en la interfaz de usuario del cuadro de diálogo. La representación visual del botón depende del contexto.

![Imagen de hero objeto interactible](images/640px-interactibleobject-hero-640px.jpg)


En el  **[Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, hemos creado una serie de scripts de Unity y prefabricados que le ayudarán a crean objetos Interactuable. Puede usarlas para crear cualquier tipo de objeto que el usuario puede interactuar con, uso de estos Estados interacción estándar: observación, destino y presionado. Puede personalizar fácilmente el diseño visual con sus propios recursos. Animaciones detalladas pueden personalizarse mediante la creación y asignación correspondientes clips de animación para los Estados de interacción en el controlador de animación de Unity o utilizar offset y escala. 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>Comentarios visuales para los Estados de interacción de entrada diferente

En realidad mixta, puesto que los objetos holográficas se mezclan con el entorno real, podría ser difícil de entender qué objetos son interactuable. Para los objetos interactuable en su experiencia, es importante proporcionar comentarios visuales diferenciadas para cada estado de entrada. Esto ayuda al usuario a entender qué parte de su experiencia es interactuable y hace que el usuario seguro con el método de interacción coherente.

Para todos los objetos que el usuario puede interactuar con, se recomienda tener comentarios visuales diferentes para estos tres estados de entrada:
* **Observación**: Estado de inactividad predeterminado del objeto.
* **Destino**: Cuando el objeto se destina a cursor mirada, un toque el puntero de movimiento o proximidad del controlador.
* **Presiona**: Cuando se presiona el objeto con el gesto de pulsar en el aire, presione dedo o botón de selección del controlador de movimiento.

![Botón holográfica](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*Observación de estado, estado de destino y estado presionado*

En Windows Mixed Reality, puede encontrar los ejemplos de visualización de los distintos Estados de entrada en el menú Inicio y los botones de barra de la aplicación. Puede usar técnicas como el resaltado o la escala para proporcionar comentarios visuales a los Estados de entrada del usuario.

En el 2 de HoloLens, ya que admite mano totalmente articulados y seguimiento de entrada, podemos proporcionar prestaciones adicionales según la proximidad a las manos. El [botón en 2 HoloLens](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) se muestra en este ejemplo.

![Botón pressable](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>Ejemplos de objetos interactuable

### <a name="mesh-button"></a>Botón de malla

![Botón de malla](images/640px-interactibleobject-meshbutton.jpg)

Estos son ejemplos de uso de tipos primitivos y mallas 3D importadas como objetos Interactuable. Puede asignar fácilmente diferentes valores de escala, desplazamiento y color para responder a cada estado de interacción de entrada.

### <a name="toolbar"></a>Barra de herramientas

![Barra de herramientas](images/640px-interactibleobject-toolbar.jpg)

Una barra de herramientas es un patrón ampliamente utilizado en las experiencias de realidad mixta. Es una colección simple de botones con comportamientos adicionales como [Billboarding y tag-along](billboarding-and-tag-along.md). Este ejemplo utiliza una secuencia de comandos Billboarding y tag-along desde el MixedRealityToolkit. Puede controlar comportamientos detallados como distancia, mover los valores de velocidad y el umbral.

### <a name="traditional-button"></a>Botón tradicional

![Botón tradicional](images/640px-interactibleobject-traditionalbutton.jpg)

En este ejemplo se muestra un botón de estilo tradicional de 2D. El estado de cada entrada tiene una profundidad ligeramente diferente y la propiedad de animación.

### <a name="other-examples"></a>Otros ejemplos

![Botón de comando](images/640px-interactibleobject-pushbutton.jpg)<br>
*Botón de comando*
<br>
![Objeto vida real](images/640px-interactibleobject-reallifeobject.jpg)<br>
*Objeto de la vida real*

Con HoloLens, puede aprovechar el espacio físico. Imagine un botón de comando holográfico en una pared físico. O ¿qué le parece una taza de café en una tabla real? Con modelos 3D importados de modelado de software, podemos crear un objeto Interactuable similar al objeto de la vida real. Puesto que es un objeto digital, podemos agregar interacciones mágicos a él.

## <a name="interactable-object-in-mixed-reality-toolkit"></a>Objeto interactuable en el Kit de herramientas de realidad mixta
Puede encontrar el [ejemplos de Interactable de objeto en el Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>Vea también
* [Botón pressable en realidad mixta Kit de herramientas de Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Colección de objetos](object-collection.md)
* [Vallas publicitarias y tag-along](billboarding-and-tag-along.md)
