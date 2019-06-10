---
title: Barra de la aplicación y el rectángulo de selección
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestra en la parte inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, barra, cuadro de límite de aplicaciones
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813861"
---
# <a name="bounding-box-and-app-bar"></a>Barra de la aplicación y de cuadro de límite
![Rectángulo de selección es la interfaz estándar para la manipulación del objeto en la realidad mixta.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>¿Qué es el cuadro de límite?

Rectángulo de selección es la interfaz estándar para la manipulación del objeto en la realidad mixta. Proporciona al usuario una prestación que el objeto está actualmente ajustable. Las esquinas indican al usuario que también puede escalar el objeto. Esta prestación visual muestra a los usuarios la superficie total del objeto, incluso si no está visible fuera de un modo de ajuste. Esto es especialmente importante porque si no fuese allí, puede aparecer un objeto que se ajustan a otro objeto o la superficie se comporte como si no hay espacio alrededor de ella que no debería estar allí. En HoloLens 2, el rectángulo de selección funciona con la manipulación directa de mano y responde a la proximidad del dedo del usuario. Muestra los comentarios visuales para ayudar al usuario percibir la distancia desde el objeto. 

![HoloLens punto de vista de un objeto mediante el cuadro de límite de escalado](images/HoloLens2_BoundingBox.gif)<br>
*Escalar un objeto mediante el cuadro de límite*

Los identificadores en las esquinas del cuadro de límite siguen un patrón ampliamente conocido por el ajuste de escala. 

![HoloLens punto de vista de girar un objeto mediante el cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Girar un objeto mediante el cuadro de límite*


![Comentarios visuales en la proximidad de mano](images/HoloLens2_Proximity.gif)<br>
*Comentarios visuales basados en la proximidad*

La factibilidad rectangular vertical de los bordes del cuadro de límite es indicadores de rotación. Esto proporciona al usuario más ajuste fino sobre sus hologramas colocados. No sólo pueden ajustar y escalar, pero ahora también girar.

* Para el desarrollo de aplicaciones de Unity, vea [caja en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>¿Qué es la barra de aplicaciones?

La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestra en la parte inferior de los límites de un holograma. Este patrón normalmente se usa para proporcionar a los usuarios la capacidad de quitar y ajustar hologramas.

Puesto que este patrón se usa con objetos que son world bloqueado, como un usuario se mueve alrededor del objeto en que la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario. Aunque esto no es vallas publicitarias, consigue eficazmente el mismo resultado; impide la posición a occlude de un usuario o la funcionalidad de bloqueo que podría estar disponible desde una ubicación diferente en su entorno.

![Desplazarse un holograma. Sigue la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)<br>
*Desplazarse un holograma, sigue la barra de aplicaciones*

La barra de la aplicación se diseñó principalmente como una manera de administrar los objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo están orientadas a objetos en la realidad mixta.

* Para el desarrollo de aplicaciones de Unity, vea [barra de la aplicación en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>Vea también
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Texto en Unity](text-in-unity.md)
* [Colección de objetos](object-collection.md)
* [Indicación del progreso](progress.md)
