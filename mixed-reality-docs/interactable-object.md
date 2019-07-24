---
title: Objeto interactuable
description: Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, IU, experiencia de usuario
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415313"
---
# <a name="interactable-object"></a>Objeto interactuable

Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción. Cualquier elemento puede ser un **objeto** interactuable que desencadene un evento. Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire. Todavía hacemos uso de botones tradicionales en ciertas situaciones, como en la interfaz de usuario del cuadro de diálogo. La representación visual del botón depende del contexto.

![Objetos interactivos](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Propiedades importantes del objeto interactuable

### <a name="visual-cue"></a>Indicación visual

Las indicaciones visuales son indicaciones organolépticas recibidas por el ojo en forma de luz y procesadas por el sistema visual durante la percepción visual. Dado que el sistema visual es dominante en muchas especies, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.

En realidad, dado que los objetos holográficas se mezclan con el entorno real, podría ser difícil entender qué objetos son interactivos. En el caso de cualquier objeto interactuable de su experiencia, es importante proporcionar una indicación visual diferenciada para cada estado de entrada. Esto ayuda al usuario a comprender qué parte de su experiencia es interactivable y hace que el usuario esté seguro con un método de interacción coherente.

#### <a name="far-interactions"></a>Interacciones lejanas

En el caso de los objetos que el usuario pueda interactuar con la mirada, el rayo y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres Estados de entrada:
* **Predeterminado (observación)** : Estado de inactividad predeterminado del objeto.
* **Destino (mantener el puntero)** : Cuando el objeto se destine con el cursor de miración, la proximidad del dedo o el puntero del controlador de movimiento.
* **Presionado**: Cuando el objeto se presiona con el gesto de puntear en el aire, presionar el dedo o el botón seleccionar del controlador de movimiento.

Puede usar técnicas como el resaltado o el escalado para proporcionar una indicación visual de los Estados de entrada del usuario. En Windows Mixed Reality, puede encontrar los ejemplos de visualización de distintos Estados de entrada en el menú Inicio y los botones de la barra de la aplicación. 

![Ejemplo de visualización del estado de observación, el estado de destino y el estado presionado](images/640px-interactibleobject-states.png)<br>
*Ejemplo de visualización del estado de observación, el estado de destino y el estado presionado*

![Estado de observación, estado de destino y estado presionado en el botón holográfica](images/MRTK_InteractableState.png)<br>
*Estado de observación, estado de destino y estado presionado en el botón holográfica*

#### <a name="neardirect-interactions"></a>Interacciones cercanas (directas)

HoloLens 2 admite la entrada de seguimiento de mano articulada que permite interactuar con objetos. Sin comentarios hápticos y la percepción de profundidad perfecta a veces puede ser difícil saber hasta dónde se encuentra la mano de un objeto o si se está tocando. Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto y, en particular, las manos en relación con los hologramas.

Use los comentarios visuales para comunicar lo siguiente:
* **Predeterminado (observación)** : Estado de inactividad predeterminado del objeto.
* **Mantener el mouse**: Cuando la mano está cerca de un holograma, cambie los objetos visuales para comunicar que la mano está dirigida al holograma. 
* **Distancia y punto de interacción**: A medida que se aproxima a los hologramas, el diseño de los comentarios para comunicar el punto de interacción proyectado, así como la distancia desde el objeto que es el dedo
* **Inicio de contacto**: Cambiar los objetos visuales (Light, color) para comunicar que se ha producido una entrada táctil
* **Entendido**: Cambie los objetos visuales (Light, color) cuando se agarre el objeto.
* **Fin del contacto**: Cambie los objetos visuales (claro, color) cuando haya finalizado la entrada táctil.

![Ejemplo de visualización de los Estados Near Interaction](images/640px-interactibleobject-states-near.jpg)<br>
*Ejemplo de visualización de los Estados Near Interaction*

El [botón de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) muestra el ejemplo de visualización de distintos Estados de interacción de entrada.

![Ejemplo de botón que se presiona en HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Ejemplo de botón que se presiona en HoloLens 2*

En HoloLens 2, hay una indicación visual adicional que mejora la confianza del usuario en la percepción de profundidad. El anillo en el dedo se muestra y se reduce verticalmente a medida que el dedo se acerca al objeto. El anillo finalmente converge en un punto en el estado Press. Esta prestación visual ayuda al usuario a comprender la distancia desde el objeto.

![Visualización del anillo de la mano](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualización del anillo de la mano en HoloLens 2*

![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)<br>
*Ejemplo de comentarios visuales basados en el cuadro de límite de proximidad*


### <a name="audio-cue"></a>Pila de audio
En el caso de las interacciones directas, los comentarios de audio adecuados pueden mejorar drásticamente la experiencia del usuario. Use los comentarios de audio para comunicar lo siguiente:
* **Inicio de contacto**: Reproducir un sonido cuando se inicie Touch
* **Fin del contacto**: Reproducir sonido en el extremo táctil
* **Inicio**de la toma: Reproducir un sonido cuando se inicie la captura
* **Final**de la toma: Reproducir sonido al final del arrastre

### <a name="voice-command"></a>Comando de voz
Para cualquier objeto interactuable, es importante admitir opciones de interacción alternativas. De forma predeterminada, se recomienda admitir el comando de voz para los objetos que son interactivos. Para mejorar la detectabilidad, puede proporcionar información sobre herramientas en el estado de desplazamiento.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="Información sobre herramientas para el comando de voz" width="350"><br/>*Información sobre herramientas para el comando de voz*

## <a name="sizing"></a>Ajuste de tamaño
Para asegurarse de que los usuarios puedan tocar fácilmente todos los objetos interactivos, se recomienda asegurarse de que el interactuable cumple un tamaño mínimo (el ángulo visual se mide a menudo en grados de arco visual) en función de la distancia que se coloca del usuario. El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia del usuario. Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](http://elvers.us/perception/visualAngle/).

A continuación se muestran las recomendaciones para tamaños mínimos de contenido interactuable.

### <a name="target-size-for-direct-hand-interaction"></a>Tamaño de destino para la interacción directa
| posición | Ángulo de visualización | Tamaño |
|---------|---------|---------|
| 45cm  | no menor que 2 ° | 1,6 x 1,6 cm |

![Tamaño de destino para la interacción directa](images/TargetSizingNear.jpg)<br>
*Tamaño de destino para la interacción directa*

Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay espacio suficiente para contener un icono y posiblemente algún texto * *

| posición | Tamaño mínimo |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![Tamaño de destino de los botones](images/TargetSizingButtons.png)<br>
*Tamaño de destino de los botones*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamaño de destino para la interacción de mano o de rayo
| posición | Ángulo de visualización | Tamaño |
|---------|---------|---------|
| 2m  | no menor que 1 ° | 3,5 x 3,5 cm |

![Tamaño de destino para la interacción de mano o de rayo](images/TargetSizingFar.jpg)<br>
*Tamaño de destino para la interacción de mano o de rayo*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Creación de un objeto interactuable con el kit de herramientas de realidad mixta (MRTK)

En el **[Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede encontrar la serie de scripts de Unity y Prefabs que le ayudarán a crear objetos interactivos. Puede utilizarlos para que los objetos respondan a diversos tipos de Estados de interacción de entrada.

* [Interactuable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Escena de ejemplos de interacción de mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

El sombreador estándar de MixedRealityToolkit proporciona varias opciones, como la **luz de proximidad** , que le ayuda a crear indicaciones visuales y de audio.
* [Sombreador estándar de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Vea también

* [Cuadro de límite](app-bar-and-bounding-box.md)
* [Colección de objetos](object-collection.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)