---
title: Barra de la aplicación y el rectángulo de selección
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestra en la parte inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, barra, cuadro de límite de aplicaciones
ms.openlocfilehash: bdce92e00193230d1f7a487f11ef0487f1d6657c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602078"
---
# <a name="bounding-box-and-app-bar"></a>Barra de la aplicación y de cuadro de límite
![Rectángulo de selección es la interfaz estándar para la manipulación del objeto en la realidad mixta.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>¿Qué es el cuadro de límite?

Rectángulo de selección es la interfaz estándar para la manipulación del objeto en la realidad mixta. Proporciona al usuario una prestación que el objeto está actualmente ajustable. Las esquinas indican al usuario que también puede escalar el objeto. Esta prestación visual muestra a los usuarios la superficie total del objeto, incluso si no está visible fuera de un modo de ajuste. Esto es especialmente importante porque si no fuese allí, puede aparecer un objeto que se ajustan a otro objeto o la superficie se comporte como si no hay espacio alrededor de ella que no debería estar allí. En HoloLens 2, el rectángulo de selección responde a proximidad del dedo del usuario. Muestra los comentarios visuales para ayudar a percibir la distancia desde el objeto. 

![HoloLens punto de vista de un objeto mediante el cuadro de límite de escalado](images/bounding-box-scale.gif)<br>
*Escalar un objeto mediante el cuadro de límite*

Las esquinas como cubo del cuadro de límite siguen un patrón ampliamente conocido por el ajuste de escala. Junto con la acción explícita de colocar un objeto en "ajustar el modo" está claro que pueden tanto mover el objeto, pero también lo escalar en su entorno.

![HoloLens punto de vista de girar un objeto mediante el cuadro de límite](images/bounding-box-rotate.gif)<br>
*Girar un objeto mediante el cuadro de límite*

La factibilidad esférica en los bordes del cuadro de límite es indicadores de rotación. Esto proporciona al usuario más ajuste fino sobre sus hologramas colocados. No sólo pueden ajustar y escalar, pero ahora también girar.

* Para el desarrollo de aplicaciones de Unity, vea [caja en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="what-is-the-app-bar"></a>¿Qué es la barra de aplicaciones?

La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestra en la parte inferior de los límites de un holograma. Este patrón normalmente se usa para proporcionar a los usuarios la capacidad de quitar y ajustar hologramas.

Puesto que este patrón se usa con objetos que son world bloqueado, como un usuario se mueve alrededor del objeto en que la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario. Aunque esto no es vallas publicitarias, consigue eficazmente el mismo resultado; impide la posición a occlude de un usuario o la funcionalidad de bloqueo que podría estar disponible desde una ubicación diferente en su entorno.

![Desplazarse un holograma. Sigue la barra de la aplicación.](images/holobar-followuser.gif)<br>
*Desplazarse un holograma, sigue la barra de aplicaciones*

La barra de la aplicación se diseñó principalmente como una manera de administrar los objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo están orientadas a objetos en la realidad mixta.

* Para el desarrollo de aplicaciones de Unity, vea [barra de la aplicación en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Vea también
* [Cuadro de límite en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)
* [Barra de la aplicación en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)
* [Objeto interactuable](interactable-object.md)
* [Texto en Unity](text-in-unity.md)
* [Colección de objetos](object-collection.md)
* [Mostrar progreso](progress.md)
