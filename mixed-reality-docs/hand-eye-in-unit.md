---
title: Seguimiento de manos y ojos articulados en Unity
description: Hay dos formas clave de tomar medidas en su mirada en Unity, gestos de mano y controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimiento, Unity, mirados, entrada
ms.openlocfilehash: b83c4904031338fd6f3e8457238bb76f1c7e7eff
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181955"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Seguimiento de manos y ojos articulados en Unity

HoloLens 2 presentó algunas nuevas funcionalidades emocionantes: seguimiento de manos y ojos articulados.

La manera más sencilla de aprovechar la nueva funcionalidad en Unity es a través de MRTK V2. También hay algunas escenas de ejemplo que le ayudarán a empezar.

* [Introducción a la mano articulada en MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
* [Introducción al seguimiento ocular en MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk-v2"></a>Bloques de creación que admiten manos, ojos y otros en MRTK V2

MRTK V2 proporciona un conjunto de controles de interfaz de usuario y bloques de creación para ayudarle a acelerar el desarrollo.

|  [botón](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) de [![botón](images/MRTK_Button_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) | [![](images/MRTK_BoundingBox_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) del cuadro de límite | [controlador de manipulación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) de [![manipuladores](images/MRTK_Manipulation_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) |
|:--- | :--- | :--- |
| Un control de botón que admite varios métodos de entrada, incluido HoloLens2's articulado | Interfaz de usuario estándar para manipular objetos en el espacio 3D | Script para manipular objetos con una o dos manos |
|  [![Pizarra](images/MRTK_Slate_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) [Pizarra](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html) | [teclado del sistema](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) de [teclado del sistema![](images/MRTK_SystemKeyboard_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html) | [![Interactuable](images/InteractableExamples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) [Interactuable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) |
| plano de estilo 2D que admite el desplazamiento con entrada de mano articulada | Script de ejemplo de uso del teclado del sistema en Unity  | Un script para que los objetos interactúen con los Estados visuales y la compatibilidad con temas |
|  [![Solucionador](images/MRTK_Solver_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) [Solucionador](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) | [colección de objetos](images/MRTK_ObjectCollection_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) [colección de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)![ | [información](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) sobre herramientas de [![ToolTip](images/MRTK_Tooltip_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html) |
| Varios comportamientos de posicionamiento de objetos, como etiqueta, el bloqueo del cuerpo, el tamaño de la vista constante y el magnetismo de superficie | Script para diseñar una matriz de objetos en una forma tridimensional | Interfaz de usuario de anotación con sistema de delimitador/dinamización flexible que se puede utilizar para etiquetar los controladores de movimiento y el objeto. |
|  [![](images/MRTK_AppBar_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) [barra](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) de la aplicación de la barra de aplicaciones | [![Punteros](images/MRTK_Pointer_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) [Punteros](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html) | [visualización](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html) del dedo de [visualización](images/MRTK_FingertipVisualization_Main.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html)  ![ |
| Interfaz de usuario para la activación manual del cuadro de límite | Más información sobre los distintos tipos de punteros | La asequibilidad visual de la mano, lo que mejora la confianza para la interacción directa |
|  [seguimiento ocular de![:](images/mrtk_et_targetselect.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) [seguimiento ocular](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) de selección de destino: selección de destino | [seguimiento ocular de![:](images/mrtk_et_navigation.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) [seguimiento de navegación ocular: navegación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) | [seguimiento ocular de![:](images/mrtk_et_heatmaps.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) seguimiento de la vista de mapa térmico [: mapa térmico](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html) |
| Combine los ojos, la voz y la entrada a mano para seleccionar los hologramas de forma rápida y sencilla a través de la escena | Obtenga información acerca de Cómo desplazarse por texto automáticamente o acercar el contenido centrado en función de lo que está examinando| Ejemplos de registro, carga y visualización de lo que los usuarios han estado examinando en la aplicación |

## <a name="example-scenes"></a>Escenas de ejemplo

Explore los distintos tipos de interacciones y controles de interfaz de usuario en [esta escena de ejemplo](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)en MRTK.

Puede encontrar otras escenas de ejemplo en la carpeta **assets/MixedRealityToolkit. examples/demos**del [Kit de herramientas de realidad mixta en github](https://github.com/Microsoft/MixedRealityToolkit-Unity) .

[![escena de ejemplo](images/MRTK_Examples.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandInteractionExamples.html)

## <a name="see-also"></a>Consulta también

* [Interacción basada en ojos] (eye-gaze-interaction.md)
* [Seguimiento de los ojos en HoloLens 2] (eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Controladores de movimiento](motion-controllers.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
