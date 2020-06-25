---
title: Visualización de malla espacial
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidad mixta, HoloLens, controles de IU, interacción, UI, experiencia de usuario, diseño de la experiencia del usuario, interfaz de usuario espacial, interacción espacial, interfaz de usuario 3D, UX en 3D
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346134"
---
# <a name="spatial-mesh"></a>Malla espacial

![Malla espacial](images/UX/MRTK_PulseShader_SpatialMesh.gif)

A través de la visualización de malla espacial, el usuario puede obtener información sobre cómo un dispositivo percibe y entiende el entorno físico. Además de proporcionar el contexto espacial, la visualización correcta de la malla espacial puede crear una experiencia agradables y mágica.  

## <a name="design-guideline"></a>Directrices de diseño
Dado que es importante permitir que el usuario se Centre e interactúe con el contenido, la visualización continua y repetida de la malla espacial en segundo plano podría ser distraer. Se recomienda visualizar el entorno de forma moderada, ya sea una sola vez en el inicio inicial o cuando el usuario muestra claramente la intención de ver la malla ambiental mediante el destino y el espacio de punteo aéreo. Puede observar este comportamiento en el shell de HoloLens.
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualización de malla espacial en MRTK (kit de herramientas de realidad mixta) para Unity
MRTK proporciona varios materiales para la visualización de la malla espacial.

- **MRTK_Wireframe. MAT, MRTK_Wireframe. MAT**: material de malla espacial estático predeterminado que muestra los contornos de la malla sin animación. Este material es útil para la depuración, ya que muestra todas las geometrías espaciales de la malla. Sin embargo, no se recomienda para la producción.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. MAT**: este material proporciona un efecto de pulso animado en la malla espacial. Puede usar este material para visualizar el entorno en un momento concreto de su experiencia o en la entrada de punteo de aire del usuario. Consulte **PulseShaderExamples. Unity** Scene para ver los ejemplos.
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Para más información, consulte [MRTK-Spatial awareing](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) y [MRTK-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .

<br>

---

## <a name="see-also"></a>Vea también

* [Cursores](cursors.md)
* [Haces de mano](point-and-commit.md)
* [Botón](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipulación](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Cerca](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Información sobre herramientas](tooltip.md)
* [Claqueta](slate.md)
* [Control deslizante](slider.md)
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
