---
title: 'MRTK 101: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)'
description: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, design, sample app, controls
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028309"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: Uso de Unity con Mixed Reality Toolkit para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

Aprende a usar MRTK para lograr algunos de los patrones de interacción comunes más usados en la realidad mixta.

- ¿Cómo simular interacciones de entrada en el editor de Unity?
- ¿Cómo agarrar y desplazar un objeto?
- ¿Cómo cambiar el tamaño de un objeto?
- ¿Cómo mover o girar un objeto con precisión?
- ¿Cómo conseguir que un objeto responda a eventos de entrada?
- ¿Cómo agregar comentarios visuales?
- ¿Cómo agregar comentarios de audio?
- ¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?
- ¿Cómo hacer que un objeto te siga?
- ¿Cómo hacer que un objeto se ponga delante de ti?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>¿Cómo simular interacciones de entrada en el editor de Unity?
MRTK admite la simulación de entrada en el editor. Simplemente, ejecuta la escena haciendo clic en el botón de juego de Unity. Usa estas claves para simular la entrada.
Presiona las teclas W, A, S y D para mover la cámara.
Mantén presionado el botón derecho del ratón y muévelo para mirar alrededor.
Para mostrar las manos simuladas, presiona la barra espaciadora (mano derecha) o la tecla Mayús izquierda (mano izquierda). Para mantener las manos simuladas en la vista, presiona la tecla T o Y. Para girar las manos simuladas, presiona Q o E (horizontal)/R o F (vertical).

- [Más información sobre la simulación de entrada en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>¿Cómo agarrar y mover un objeto?
Para que un objeto se pueda agarrar, asigna estos dos scripts: ManipulationHandler.cs y NearInteractionGrabbable.cs (para captación directa con entrada de seguimiento de manos articulada). ManipulationHandler admite interacciones cercanas y lejanas. Puedes agarrar y mover un objeto con la entrada de seguimiento de manos articulada de HoloLens 2 (cercana), el haz de mano (lejana), el cursor del controlador de movimiento (lejano), el cursor de mirada de HoloLens y el toque en el aire (lejana).

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>¿Cómo cambiar el tamaño de un objeto?
ManipulationHandler.cs admite el escalado o la rotación con dos manos. Esto funciona con varios tipos de entrada, como la entrada de manos articulada de HoloLens 2, la entrada de mirada y gestos de HoloLens 1 y la entrada del controlador de movimiento del casco envolvente de Windows Mixed Reality.

- [Más información sobre el controlador de manipulación en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>¿Cómo mover o girar un objeto con precisión?
Asigna BoundingBox.cs a un objeto para usar el cuadro de límite, que es la interfaz para escalar y girar un objeto. De forma predeterminada, se muestran los controladores y los cables de color azul del estilo de HoloLens 1. Para usar controladores animados basados en proximidad del estilo de HoloLens 2, debes asignar objetos prefabricados y materiales. Consulta la [documentación del cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) y la escena de BoundingBoxExamples.unity para obtener los detalles de configuración.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Más información sobre los cuadros de límite en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>¿Cómo conseguir que un objeto responda a eventos de entrada?
Asigna PointerHandler.cs a un objeto. En el inspector, podrás usar los eventos OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Para usarlos en un script, implementa IMixedRealityPointerHandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Más información sobre el sistema de entrada en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>¿Cómo agregar comentarios visuales?
Asigna Interactable.cs a un objeto. En el inspector, crea un tema. Mediante el uso de perfiles de tema interactuables, puedes agregar comentarios visuales a todos los estados de interacción de entrada disponibles.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Los elementos interactuables proporcionan varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.

- [Más información sobre los elementos interactuables en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Otro bloque de creación importante para los comentarios visuales es el sombreador estándar de MRTK. Con el sombreador estándar de MRTK, puedes agregar fácilmente efectos de comentarios visuales, como luz de desplazamiento y de proximidad. Dado que el sombreador estándar de MRTK realiza un cálculo significativamente menor que el sombreador estándar de Unity, puedes crear una experiencia de rendimiento.

Crea un nuevo material y selecciona el sombreador "Mixed Reality Toolkit > Standard (Estándar)". También puedes elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Más información sobre el sombreador estándar de MRTK en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>¿Cómo agregar comentarios de audio?
Agrega AudioSource a un objeto. A continuación, en los scripts que exponen eventos de entrada (p. ej., Interactable.cs o PointerHandler.cs), asigna el objeto al evento y selecciona AudioSource.PlayOneShot(). Puedes usar los clips de audio o elegir uno de los recursos de audio de MRTK.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?
MRTK proporciona varios tipos de botones de estilo de Shell (SO) de HoloLens 2. Proporciona comentarios visuales sofisticados, como la luz de proximidad, el cuadro de compresión y un efecto de rizado en la superficie del botón.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Basta con arrastrar y colocar uno de los objetos prefabricados de botón presionable del estilo de HoloLens 2 a la escena. El objeto prefabricado usa Interactable.cs, que se presentó anteriormente. Puedes usar eventos expuestos como OnClick() en el objeto interactuable para desencadenar acciones.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Más información sobre los objetos prefabricados de botón en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>¿Cómo hacer que un objeto te siga?
Asigna el script RadialView.cs a un objeto. Forma parte de la serie de scripts del solucionador que permite lograr distintos tipos de selección de ubicación de objetos en el espacio 3D. SolverHandler.cs se agregará automáticamente.
A continuación se incluye un ejemplo de configuración de RadialView para lograr el comportamiento y la etiqueta "lazy follow" (seguimiento diferido), como el menú Inicio del shell de HoloLens. Puedes especificar la distancia mínima/máxima y los grados de vista mínimos y máximos. En el ejemplo siguiente se muestra cómo colocar el objeto en un intervalo entre 0,4 m y 0,8 m en 15°. Ajusta los valores de tiempo de Lerp para que la actualización posicional sea más rápida o más lenta.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Más información sobre los solucionadores en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>¿Cómo hacer que un objeto se ponga delante de ti?
Asigna el script Billboard.cs a un objeto. Siempre se situará delante de ti, independientemente de tu posición. Puedes especificar la opción del eje dinámico.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


¿Estás listo para crear experiencias sorprendentes para la realidad mixta? Visita las páginas siguientes y obtén más información sobre MRTK y Mixed Reality.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulta también

* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Guía de portabilidad de HoloToolkit a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
