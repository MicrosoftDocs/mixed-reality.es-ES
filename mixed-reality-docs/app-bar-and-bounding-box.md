---
title: Cuadro de límite y barra de la aplicación
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite
ms.openlocfilehash: f09187bc2a3969a8f844711052e15433f5449d6d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437055"
---
# <a name="bounding-box-and-app-bar"></a>Cuadro de límite y barra de la aplicación
![El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/640px-boundingbox-hero.jpg)<br>

<br>

---

## <a name="what-is-the-bounding-box"></a>¿Cuál es el cuadro de límite?

El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta. Proporciona al usuario una asequibilidad de que el objeto es ajustable actualmente. En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario. Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Escalado de un objeto<br>
        Las esquinas del cuadro de límite indican al usuario que el objeto se puede escalar. Los identificadores siguen un patrón muy entendido para ajustar la escala. Esta prestación visual muestra a los usuarios el área total del objeto, aunque no sea visible fuera de un modo de ajuste. Esto es especialmente importante porque, si no estuviera allí, es posible que un objeto ajustado a otro objeto o superficie parezca que se comporte como si hubiera espacio alrededor que no debiera estar ahí.<br>
        <br>
        *Bucle de vídeo: escalado de un objeto a través del cuadro de límite*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![punto de vista de HoloLens de escalado de un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Girar un objeto<br>
        Las prestaciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación. Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados. No solo se pueden ajustar y escalar, sino que ahora giran.<br>
        <br>
        *Bucle de vídeo: girar un objeto a través del cuadro de límite*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![punto de vista de HoloLens de girar un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Comentarios visuales sobre la proximidad en HoloLens 2<br>
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

**Para el desarrollo de aplicaciones de Unity, consulte [cuadro de límite en el kit de herramientas de realidad mixta (Unity).](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>¿Qué es la barra de la aplicación?

La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma. Este patrón se usa normalmente para proporcionar a los usuarios la capacidad de quitar y ajustar los hologramas. La barra de la aplicación se diseñó principalmente como una manera de administrar objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en realidad mixta.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barra de la aplicación sigue al usuario<br>
        Puesto que este patrón se usa con objetos que están bloqueados por todo el mundo, a medida que un usuario se desplaza por el objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario. Aunque esto no se está desformando, se consigue el mismo resultado; impedir que la posición de un usuario tapaba o bloquee la funcionalidad que, de otro modo, estará disponible desde una ubicación diferente en su entorno. <br>
        <br>
        *Bucle de vídeo: desplazarse por un holograma, la barra de la aplicación sigue*
    :::column-end:::
        :::column:::
        espacio ![](images/spacer-20x582.png)<br>
       ![recorrer un holograma. A continuación se muestra la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>



**Para el desarrollo de aplicaciones de Unity, consulte [App bar en el kit de herramientas de realidad mixta (Unity).](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)**

<br>

---

## <a name="see-also"></a>Consulta también
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Texto en Unity](text-in-unity.md)
* [Colección de objetos](object-collection.md)
* [Indicación del progreso](progress.md)
