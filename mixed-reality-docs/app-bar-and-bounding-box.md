---
title: Cuadro de límite y barra de la aplicación
description: The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite
ms.openlocfilehash: e4f519cba459efac25f6c1370b07fcda4def30a1
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143174"
---
# <a name="bounding-box-and-app-bar"></a>Cuadro de límite y barra de la aplicación
![límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/UX/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>¿Cuál es el cuadro de límite?

El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta. Proporciona al usuario una asequibilidad de que el objeto es ajustable actualmente. En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario. It shows visual feedback to help the user perceive the distance from the object.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Scaling an object<br>
        The corners of the bounding box tell the user that the object can scale. The handles follow a widely understood pattern for adjusting scale. This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode. This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.<br>
        <br>
        *Video loop: Scaling an object via bounding box*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotating an object<br>
        The vertical rectangular affordances on the edges of the bounding box are rotation indicators. This gives the user more fine adjustment over their placed holograms. Not only can they adjust and scale, but now rotate as well.<br>
        <br>
        *Video loop: Rotating an object via bounding box*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Visual feedback on hand proximity on HoloLens 2<br>
        On HoloLens 2, there is an additional visual cue which can help the user's perception of depth. A ring near their fingertip shows up and scales down as the fingertip gets closer to the object. The ring eventually converges into a dot when the pressed state is reached. This visual affordance helps the user understand how far they are from the object.<br>
        <br>
        *Video loop: Example of visual feedback based on proximity to a bounding box*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>What is the App bar?

The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds. This pattern is commonly used to give users the ability to remove and adjust holograms. The App bar was designed primarily as a way to manage placed objects in a user's environment. Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>The App bar follows the user<br>
        Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user. While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment. <br>
        <br>
        *Video loop: Walking around a hologram, the App bar follows*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![Walking around a hologram. The App bar follows.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a>Bounding box in MRTK(Mixed Reality Toolkit) for Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar. You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.

* [MRTK - Bounding Box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


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
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
