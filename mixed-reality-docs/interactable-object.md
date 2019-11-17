---
title: Interactable object
description: A button has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Controls, interaction, ui, ux
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143257"
---
# <a name="interactable-object"></a>Interactable object

![Interactible objects](images/UX/UX_Hero_Interactable.jpg)

A button has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore. Anything can be an **interactable object** that triggers an event. An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air. We still do make use of traditional buttons in certain situation such as in dialog UI. The visual representation of the button depends on the context.

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>Important properties of the interactable object

### <a name="visual-cues"></a>Indicaciones visuales

Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception. Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.

Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with. For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state. This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.

<br>

---

### <a name="far-interactions"></a>Far interactions

For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:

:::row:::
    :::column:::
       ![interactibleobject-states-default](images/interactibleobject-states-default.jpg)<br>
       **Default (Observation) state**<br>
        Default idle state of the object.
    The cursor is not on the object. Hand is not detected.
    :::column-end:::
    :::column:::
       ![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)<br>
        **Targeted (Hover) state**<br>
        When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.
    The cursor is on the object. Hand is detected, ready.
    :::column-end:::
    :::column:::
       ![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)<br>
       **Pressed state**<br>
        When the object is pressed with an air tap gesture, finger press or motion controller's select button.
    The cursor is on the object. Hand is detected, air tapped.
    :::column-end:::
:::row-end:::

<br>

---

You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state. In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons. 

Here is what these states look like on a **holographic button**:

:::row:::
    :::column:::
       ![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)<br>
       **Default (Observation) state**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)<br>
        **Targeted (Hover) state**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)<br>
       **Pressed state**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Near interactions (direct) 

HoloLens 2 supports articulated hand tracking input which allows you to interact with objects. Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it. It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.

Use visual feedback to communicate the following:
* **Default (Observation)** : Default idle state of the object.
* **Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram. 
* **Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is
* **Contact begins**: Change visuals (light, color) to communicate that a touch has occurred
* **Grasped**: Change visuals (light, color) when the object is grasped
* **Contact ends**: Change visuals (light, color) when touch has ended

<br>

---

:::row:::
    :::column:::
        ![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **Hover (Far)**<br>
        Highlighting based on the proximity of the hand.
    :::column-end:::
    :::column:::
        ![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **Hover (Near)**<br>
        Highlight size changes based on the distance to the hand.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Touch / press](images/640px-interactibleobject-states-near-press.jpg)<br>
        **Touch / press**<br>
        Visual plus audio feedback.
    :::column-end:::
    :::column:::
        ![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **Grasp**<br>
        Visual plus audio feedback.
    :::column-end:::
:::row-end:::

<br>

<br>

---

A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:

:::row:::
    :::column:::
        ![Default](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **Default**<br>
    :::column-end:::
    :::column:::
        ![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **Hover**<br>
        Reveal a proximity-based lighting effect.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Función táctil](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **Función táctil**<br>
        Show ripple effect.
    :::column-end:::
    :::column:::
        ![Press](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **Press**<br>
        Move the front plate.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>The "ring" visual cue on HoloLens 2<br>
        On HoloLens 2, there is an additional visual cue which can help the user's perception of depth. A ring near their fingertip shows up and scales down as the fingertip gets closer to the object. The ring eventually converges into a dot when the pressed state is reached. This visual affordance helps the user understand how far they are from the object.<br>
        <br>
        *Video loop: Example of visual feedback based on proximity to a bounding box*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>Audio cues

For direct hand interactions, proper audio feedback can dramatically improve the user experience. Use audio feedback to communicate the following:
* **Contact begins**: Play sound when touch begins
* **Contact ends**: Play sound on touch end
* **Grab begins**: Play sound when grab starts
* **Grab ends**: Play sound when grab ends

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>Comandos de voz<br>
        For any interactable objects, it is important to support alternative interaction options. By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable. To improve discoverability, you can also provide a tooltip during the hover state.<br>
        <br>
        *Image: Tooltip for the voice command*
    :::column-end:::
        :::column:::
       ![voice commanding](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>Sizing recommendations 

To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes. To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).

Below are the recommendations for minimum sizes of interactable content.


### <a name="target-size-for-direct-hand-interaction"></a>Target size for direct hand interaction

| Distance | Viewing angle | Size |
|---------|---------|---------|
| 45cm  | no smaller than 2° | 1.6 x 1.6 cm |

![Target size for direct hand interaction](images/TargetSizingNear.jpg)<br>
*Target size for direct hand interaction*

<br>

### <a name="target-size-for-buttons"></a>Target size for buttons

When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.

| Distance | Tamaño mínimo |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![Target size for the buttons](images/TargetSizingButtons.png)<br>
*Target size for the buttons*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Target size for hand ray or gaze interaction
| Distance | Viewing angle | Size |
|---------|---------|---------|
| 2m  | no smaller than 1° | 3.5 x 3.5 cm |

![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)<br>
*Target size for hand ray or gaze interaction*


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a>Interactable object in MRTK(Mixed Reality Toolkit) for Unit

In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states. It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.

* [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [Hand interaction examples scene](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.
* [MRTK Standard Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a>Consulta también

* [Cursores](cursors.md)
* [Hand ray](point-and-commit.md)
* [Button](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Near menu](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Voice command](voice-input.md)
* [Teclado](keyboard.md)
* [Tooltip](tooltip.md)
* [Slate](slate.md)
* [Control deslizante](slider.md)
* [Shader](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Surface magnetism](surface-magnetism.md)
