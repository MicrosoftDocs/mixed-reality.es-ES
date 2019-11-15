---
title: Objeto interactuable
description: Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, IU, experiencia de usuario
ms.openlocfilehash: 5305af97e9811134212fc6c730727962bb9e8353
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105799"
---
# <a name="interactable-object"></a>Objeto interactuable

![Objetos interactivos](images/UX/UX_Hero_Interactable.jpg)

Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción. Cualquier elemento puede ser un **objeto interactuable** que desencadene un evento. Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire. Todavía hacemos uso de botones tradicionales en ciertas situaciones, como en la interfaz de usuario del cuadro de diálogo. La representación visual del botón depende del contexto.

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>Propiedades importantes del objeto interactuable

### <a name="visual-cues"></a>Indicaciones visuales

Las indicaciones visuales son indicaciones organolépticas recibidas por el ojo en forma de luz y procesadas por el sistema visual durante la percepción visual. Dado que el sistema visual es dominante en muchas especies, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.

Dado que los objetos holográficas se mezclan con el entorno real en realidad mixta, podría ser difícil comprender con qué objetos puede interactuar. En el caso de cualquier objeto interactuable de su experiencia, es importante proporcionar indicaciones visuales diferenciadas para cada estado de entrada. Esto ayuda al usuario a comprender qué parte de su experiencia es interactivable y hace que el usuario esté seguro mediante el uso de un método de interacción coherente.

<br>

---

### <a name="far-interactions"></a>Interacciones lejanas

En el caso de los objetos que el usuario pueda interactuar con la mirada, el rayo y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres Estados de entrada:

:::row:::
    :::column:::
       ![interactibleobject-States-](images/interactibleobject-states-default.jpg) predeterminada<br>
       **Estado predeterminado (observación)**<br>
        Estado de inactividad predeterminado del objeto.
    El cursor no está en el objeto. No se detecta la mano.
    :::column-end:::
    :::column:::
       ![interactibleobject-States-](images/interactibleobject-states-targeted.jpg) de destino<br>
        **Estado de destino (mantener el mouse)**<br>
        Cuando el objeto se destine con el cursor de miración, la proximidad del dedo o el puntero del controlador de movimiento.
    El cursor está en el objeto. La mano se detecta y está lista.
    :::column-end:::
    :::column:::
       ![interactibleobject-States-pressed](images/interactibleobject-states-pressed.jpg)<br>
       **Estado presionado**<br>
        Cuando el objeto se presiona con un gesto de pulsación de aire, presionar el dedo o el botón seleccionar del controlador de movimiento.
    El cursor está en el objeto. Se detecta una mano, se puntea en el aire.
    :::column-end:::
:::row-end:::

<br>

---

Puede usar técnicas como resaltado o escalado para proporcionar indicaciones visuales para el estado de entrada del usuario. En la realidad mixta, puede encontrar los ejemplos de visualización de distintos Estados de entrada en el menú Inicio y con los botones de la barra de la aplicación. 

Este es el aspecto de estos Estados en un **botón holográfica**:

:::row:::
    :::column:::
       ![interactibleobject-States-](images/MRTK_InteractableState-default.jpg) predeterminada<br>
       **Estado predeterminado (observación)**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-States-](images/MRTK_InteractableState-targeted.jpg) de destino<br>
        **Estado de destino (mantener el mouse)**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-States-pressed](images/MRTK_InteractableState-pressed.jpg)<br>
       **Estado presionado**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Interacciones cercanas (directas) 

HoloLens 2 admite la entrada de seguimiento de mano articulada que permite interactuar con objetos. Sin comentarios hápticos e percepción de profundidad perfecta, a veces puede ser difícil saber hasta dónde se encuentra su mano de un objeto o si lo toca. Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto y, en particular, el estado de las manos con respecto a ese objeto.

Use los comentarios visuales para comunicar lo siguiente:
* **Predeterminado (observación)** : estado de inactividad predeterminado del objeto.
* **Mantener el mouse**: cuando una mano está cerca de un holograma, cambie los objetos visuales para comunicar que esa mano está dirigida al holograma. 
* **Distancia y punto de interacción**: a medida que la mano se aproxima a un holograma, el diseño de comentarios para comunicar el punto de interacción proyectado, así como la distancia desde el objeto que es el dedo
* **Inicio de contacto**: cambie los objetos visuales (Light, color) para comunicar que se ha producido una entrada táctil
* **Agarre**: cambiar objetos visuales (claros, de color) cuando se agarre el objeto
* **Extremos de contacto**: cambios visuales (claros, de color) cuando la entrada táctil ha finalizado

<br>

---

:::row:::
    :::column:::
        ![al mantener el mouse (lejano)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Mantener el mouse (lejano)**<br>
        Resaltado en función de la proximidad de la mano.
    :::column-end:::
    :::column:::
        ![mantener el mouse (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Mantener el mouse (Near)**<br>
        Resaltar cambios de tamaño en función de la distancia a la mano.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![tocar y presionar](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Tocar y presionar**<br>
        Comentarios de Visual Plus audio.
    :::column-end:::
    :::column:::
        ![agarre](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Visión**<br>
        Comentarios de Visual Plus audio.
    :::column-end:::
:::row-end:::

<br>

<br>

---

Un [botón de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) es un ejemplo de cómo se visualizan los distintos Estados de interacción de entrada:

:::row:::
    :::column:::
        ![](images/640px-interactibleobject-pressablebutton-default.jpg) predeterminada<br>
        **Predeterminada**<br>
    :::column-end:::
    :::column:::
        ![mantener el puntero](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Activada**<br>
        Revela un efecto de iluminación basado en proximidad.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Función táctil](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Función táctil**<br>
        Mostrar efecto de rizo.
    :::column-end:::
    :::column:::
        ![Presione](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Pulse**<br>
        Mueva la placa frontal.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>La indicación visual "Ring" en HoloLens 2<br>
        En HoloLens 2, hay una indicación visual adicional que puede ayudar a la percepción del usuario de la profundidad. Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto. El anillo finalmente converge en un punto cuando se alcanza el estado presionado. Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.<br>
        <br>
        *Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![comentarios visuales sobre la proximidad](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Señales de audio

En el caso de las interacciones directas, los comentarios de audio adecuados pueden mejorar drásticamente la experiencia del usuario. Use los comentarios de audio para comunicar lo siguiente:
* **Inicio de contacto**: reproducir un sonido cuando se inicie Touch
* **Contactos**finales: reproducir sonido en el extremo táctil
* **Inicio**de la toma: reproducir sonido cuando se inicie la captura
* Acabado de **agarre**: reproducir un sonido al finalizar la toma

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Comandos de voz<br>
        Para cualquier objeto interactuable, es importante admitir opciones de interacción alternativas. De forma predeterminada, se recomienda que se admitan los [comandos de voz](voice-design.md) para cualquier objeto que sea interactuable. Para mejorar la capacidad de detección, también puede proporcionar una información sobre herramientas durante el estado de mantener el mouse.<br>
        <br>
        *Image: información sobre herramientas para el comando Voice*
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>Recomendaciones de ajuste de tamaño 

Para asegurarse de que los usuarios puedan tocar fácilmente todos los objetos interactivos, se recomienda asegurarse de que el interactuable cumple un tamaño mínimo (el ángulo visual se mide a menudo en grados de arco visual) en función de la distancia que se coloca del usuario. El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia del usuario. Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](https://elvers.us/perception/visualAngle/).

A continuación se muestran las recomendaciones para tamaños mínimos de contenido interactuable.


### <a name="target-size-for-direct-hand-interaction"></a>Tamaño de destino para la interacción directa

| Posición | Ángulo de visualización | Size |
|---------|---------|---------|
| 45cm  | no menor que 2 ° | 1,6 x 1,6 cm |

![tamaño de destino para la interacción directa](images/TargetSizingNear.jpg)<br>
*Tamaño de destino para la interacción directa*

<br>

### <a name="target-size-for-buttons"></a>Tamaño de destino de los botones

Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay espacio suficiente para contener un icono y un posible texto.

| Posición | Tamaño mínimo |
|---------|---------|
| 45cm  | 3,2 x 3,2 cm |

![tamaño de destino de los botones](images/TargetSizingButtons.png)<br>
*Tamaño de destino de los botones*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Tamaño de destino para la interacción de mano o de rayo
| Posición | Ángulo de visualización | Size |
|---------|---------|---------|
| 2m  | no menor que 1 ° | 3,5 x 3,5 cm |

![tamaño de destino de la interacción de rayo o de una mirada a mano](images/TargetSizingFar.jpg)<br>
*Tamaño de destino para la interacción de mano o de rayo*


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a>Objeto interactuable en MRTK (kit de herramientas de realidad mixta) para unidad

En **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede usar el script [**interactúable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para que los objetos respondan a diversos tipos de Estados de interacción de entrada. Admite varios tipos de temas que permiten definir Estados visuales mediante el control de las propiedades del objeto como el color, el tamaño, el material y el sombreador.

* [Interactuable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Escena de ejemplos de interacción de mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

El sombreador estándar de MixedRealityToolkit proporciona varias opciones, como la **luz de proximidad** , que le ayuda a crear indicaciones visuales y de audio.
* [Sombreador estándar de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>Consulta también

* [Cursores](cursors.md)
* [Rayo de mano](point-and-commit.md)
* [Button](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipula](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Near](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Herramienta](tooltip.md)
* [Tabletas](slate.md)
* [Control deslizante](slider.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)