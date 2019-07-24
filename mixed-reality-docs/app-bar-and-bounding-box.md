---
title: Cuadro de límite y barra de la aplicación
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829682"
---
# <a name="bounding-box-and-app-bar"></a>Cuadro de límite y barra de la aplicación
![El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>¿Cuál es el cuadro de límite?

El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta. Proporciona al usuario una asequibilidad de que el objeto es ajustable actualmente. Las esquinas indican al usuario que el objeto también se puede escalar. Esta prestación visual muestra a los usuarios el área total del objeto, aunque no sea visible fuera de un modo de ajuste. Esto es especialmente importante porque, si no estuviera allí, es posible que un objeto ajustado a otro objeto o superficie parezca que se comporte como si hubiera espacio alrededor que no debiera estar ahí. En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario. Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto. 

![Punto de vista de HoloLens de escalado de un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox.gif)<br>
*Escalado de un objeto a través del cuadro de límite*

Los manipuladores de las esquinas del cuadro de límite siguen un patrón muy entendido para ajustar la escala. 

![Punto de vista de HoloLens de girar un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*Girar un objeto a través del cuadro de límite*


![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)<br>
*Comentarios visuales basados en la proximidad*

Las prestaciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación. Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados. No solo se pueden ajustar y escalar, sino que ahora giran.

* Para el desarrollo de aplicaciones de Unity, consulte [cuadro de límite en el kit de herramientas de realidad mixta (Unity)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) .



## <a name="what-is-the-app-bar"></a>¿Qué es la barra de la aplicación?

La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma. Este patrón se usa normalmente para proporcionar a los usuarios la capacidad de quitar y ajustar los hologramas.

Puesto que este patrón se usa con objetos que están bloqueados por todo el mundo, a medida que un usuario se desplaza por el objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario. Aunque esto no se está desformando, se consigue el mismo resultado; impedir que la posición de un usuario tapaba o bloquee la funcionalidad que, de otro modo, estará disponible desde una ubicación diferente en su entorno.

![Recorrer un holograma. A continuación se muestra la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)<br>
*Desplazarse por un holograma, la barra de la aplicación sigue*

La barra de la aplicación se diseñó principalmente como una manera de administrar objetos colocados en el entorno de un usuario. Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en realidad mixta.

* Para el desarrollo de aplicaciones de Unity, consulte [App bar en el kit de herramientas de realidad mixta (Unity)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) .

## <a name="see-also"></a>Vea también
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Texto en Unity](text-in-unity.md)
* [Colección de objetos](object-collection.md)
* [Indicación del progreso](progress.md)
