---
title: Objeto interactuable
description: Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D. En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, interfaz de usuario, experiencia de usuario
ms.openlocfilehash: b0397e00763f70e4caf55a84b6541085e56fafd4
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148731"
---
# <a name="interactable-object"></a>Objeto interactuable

Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D. En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya. Nada puede ser un **interactuable objeto** que desencadena un evento. Un objeto interactuable puede representarse como nada una taza de café en la tabla a un globo flotante en el aire. Todavía hacemos uso de los botones tradicionales en determinados situación tal como se muestra en la interfaz de usuario del cuadro de diálogo. La representación visual del botón depende del contexto.

![Objetos interactible](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Propiedades importantes del objeto interactuable

### <a name="visual-cue"></a>Indicación Visual

Indicaciones visuales son indicaciones sensoriales recibidos por el ojo en forma de luz y procesados por el sistema visual durante la percepción visual. Puesto que el sistema visual es dominante en muchas especies, especialmente los seres humanos, indicaciones visuales son una gran fuente de información de cómo se percibe el mundo.

En realidad mixta, puesto que los objetos holográficas se mezclan con el entorno real, podría ser difícil de entender qué objetos son interactuable. Para los objetos interactuable en su experiencia, es importante proporcionar indicación visual diferenciada para cada estado de entrada. Esto ayuda al usuario a entender qué parte de su experiencia es interactuable y hace que el usuario seguro con el método de interacción coherente.

#### <a name="far-interactions"></a>Interacciones de extremo

Para todos los objetos que el usuario puede interactuar con mirada, ray mano y ray del controlador de movimiento, se recomienda tener indicación visual diferente para estos tres estados de entrada:
* **Predeterminado (observaciones)** : Estado de inactividad predeterminado del objeto.
* **Destino (desplazamiento)** : Cuando el objeto se destina a cursor mirada, un toque el puntero de movimiento o proximidad del controlador.
* **Presiona**: Cuando se presiona el objeto con el gesto de pulsar en el aire, presione dedo o botón de selección del controlador de movimiento.

Puede usar técnicas como el resaltado o la escala para proporcionar una indicación visual a Estados de entrada del usuario. En Windows Mixed Reality, puede encontrar los ejemplos de visualización de los distintos Estados de entrada en el menú Inicio y los botones de barra de la aplicación. 

![Ejemplo de visualizar el estado de observación, estado de destino y estado presionado](images/640px-interactibleobject-states.png)<br>
*Ejemplo de visualizar el estado de observación, estado de destino y estado presionado*

![Estado de observación, estado de destino y estado de presionado en el botón holográfica](images/MRTK_InteractableState.png)<br>
*Estado de observación, estado de destino y estado de presionado en el botón holográfica*

#### <a name="neardirect-interactions"></a>Interacciones NEAR(Direct)

HoloLens 2 es compatible con la mano articulado entrada que le permite interactuar con objetos de seguimiento. Sin comentarios hápticos y la percepción de profundidad perfecta a veces puede ser difícil saber cómo de lejos la mano de un objeto o si al tocar. Es importante proporcionar suficiente indicaciones visuales para comunicar el estado del objeto y, en particular de sus manos en relación con hologramas.

Use comentarios visuales para comunicar lo siguiente:
* **Predeterminado (observaciones)** : Estado de inactividad predeterminado del objeto.
* **Mantenga el mouse**: Cuando está disponible cerca un holograma, objetos visuales de cambio para comunicarse en esa mano está destinada a holograma. 
* **Distancia y punto de interacción**: Como aproxima a mano holograma, diseñar comentarios para comunicarse el punto proyectado de interacción, así como cómo lejos de ser el objeto es el dedo
* **Póngase en contacto con Begin**: Se ha producido el cambio los objetos visuales (luz, color) para comunicarse ese toque
* **Captado**: Cambiar los objetos visuales (luz, color) cuando se entendido todo el objeto.
* **Póngase en contacto con el fin**: Cambiar los objetos visuales (luz, color) que finalizó táctil.

![Ejemplo de visualizar cerca de los Estados de interacción](images/640px-interactibleobject-states-near.jpg)<br>
*Ejemplo de visualizar cerca de los Estados de interacción*

El [botón en 2 HoloLens](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) muestra el ejemplo de interacción de entrada diferentes Estados de visualización.

![Ejemplo de botón pressable en HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*Ejemplo de botón pressable en HoloLens 2*

En el 2 de HoloLens, hay una indicación visual adicional que mejora la confianza del usuario en la percepción de profundidad. El anillo de la yema del dedo muestre y escala hacia abajo, según la yema del dedo que se aproxime al objeto. Finalmente adoptan el anillo en un punto en el estado de la prensa. Esta prestación visual ayuda al usuario a comprender la distancia desde el objeto.

![Visualización de anillo de yema del dedo](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*Visualización de anillo de yema del dedo en HoloLens 2*

![Comentarios visuales en la proximidad de mano](images/HoloLens2_Proximity.gif)<br>
*Ejemplo de comentarios visuales basados en la proximidad - cuadro de límite*


### <a name="audio-cue"></a>Indicación de audio
Para las interacciones directas de mano, comentarios de audio adecuados pueden mejorar considerablemente la experiencia del usuario. Utilice comentarios de audio para comunicar lo siguiente:
* **Póngase en contacto con begin**: Reproducir un sonido cuando comienza el toque
* **Póngase en contacto con final**: Reproducir un sonido en el toque final
* **Agarre comenzar**: Reproducir un sonido cuando se inicia el arrastre
* **Agarre final**: Reproducir un sonido en el extremo de captura

### <a name="voice-command"></a>Comando de voz
Para los objetos interactuable, es importante admitir opciones alternativas de interacción. De forma predeterminada, se recomienda para admitir los comandos de voz para los objetos que se interactuable. Para mejorar la detectabilidad, puede proporcionar información sobre herramientas en estado de desplazamiento.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="Información sobre herramientas para el comando de voz" width="350"><br/>*Información sobre herramientas para el comando de voz*

## <a name="sizing"></a>Ajuste de tamaño
Para asegurarse de que todos los objetos interactuable pueden fácilmente han tocado mediante los usuarios le sugerimos lo que garantiza el interactuable cumple un tamaño mínimo (suele medido en ángulo de grados visual) según la distancia que se encuentra el usuario. Ángulo de grados visual se basa en la distancia entre el usuario y el objeto y permanece constante, mientras que puede cambiar el tamaño físico de destino como la distancia de los cambios de usuario. Para determinar el tamaño físico necesario de un objeto basado en la distancia desde un seguro y el grado ángulo visual pruebe a usar una calculadora como: http://elvers.us/perception/visualAngle/

A continuación se muestran las recomendaciones de tamaño mínimo de contenido interactuable

### <a name="target-size-for-direct-hand-interaction"></a>Tamaño de destino para la interacción directa de mano
| distancia | Ángulo de visión | Tamaño |
|---------|---------|---------|
| 45cm  | No menor que 2° | 1.6 1,6 cm |

![Tamaño de destino para la interacción directa de mano](images/TargetSizingNear.jpg)<br>
*Tamaño de destino para la interacción directa de mano*

Al crear botones para la interacción directa, se recomienda es de un tamaño mínimo de cm de 3,2 x 3.2 para asegurarse de que existe espacio suficiente para contener un icono y potencialmente algún texto **

| distancia | Tamaño mínimo |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![Tamaño de destino para los botones](images/TargetSizingButtons.png)<br>
*Tamaño de destino para los botones*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamaño de ray mano del destino o interacción que mirar
| distancia | Ángulo de visión | Tamaño |
|---------|---------|---------|
| 2m  | No menor que 1° | 3.5 3,5 cm |

![Tamaño de ray mano del destino o interacción que mirar](images/TargetSizingFar.jpg)<br>
*Tamaño de ray mano del destino o interacción que mirar*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>Crear objeto interactuable con el Kit de herramientas de realidad mixta (MRTK)

En el  **[Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede encontrar la serie de scripts de Unity y prefabricados que le ayudarán a crean objetos interactuable. Puede usarlas para crear objetos responder a distintos tipos de Estados de interacción de entrada.

* [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Escena de ejemplos de interacción de mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

Sombreador estándar del MixedRealityToolkit proporciona varias opciones, como **luz proximidad** que le ayudará a crear señales de audio y visuales.
* [Sombreador MRTK estándar](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>Vea también

* [cuadro de límite](app-bar-and-bounding-box.md)
* [Colección de objetos](object-collection.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)