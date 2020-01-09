---
title: 'MRTK 101: Cómo usar el kit de herramientas de realidad mixta Unity para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)'
description: Cómo usar el kit de herramientas de realidad mixta Unity para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, kit de herramientas de realidad mixta, Windows Mixed Reality, diseño, aplicación de ejemplo, controles
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623498"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: Cómo usar el kit de herramientas de realidad mixta Unity para interacciones básicas (HoloLens 2, HoloLens, Windows Mixed Reality y Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

Obtenga información sobre cómo usar MRTK para lograr algunos de los patrones de interacción comunes más utilizados en la realidad mixta.

- ¿Cómo simular interacciones de entrada en el editor de Unity?
- Cómo capturar y desplace un objeto
- ¿Cómo se cambia el tamaño de un objeto?
- ¿Cómo se mueve o gira un objeto con precisión?
- Cómo hacer que un objeto responda a los eventos de entrada
- ¿Cómo agregar comentarios visuales?
- ¿Cómo agregar comentarios de audio?
- ¿Cómo se usa el botón de estilo Prefabs de HoloLens 2?
- ¿Cómo hacer que un objeto siga?
- ¿Cómo hacer que un objeto se enfrente?

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>¿Cómo simular interacciones de entrada en el editor de Unity?
MRTK admite la simulación de entrada en el editor. Simplemente ejecute la escena haciendo clic en el botón de reproducción de Unity. Use estas claves para simular la entrada.
Presione las teclas W, a, S y D para desplace la cámara.
Mantenga presionado el botón secundario del mouse y mueva el mouse para buscarlo.
Para mostrar las manos simuladas, presione la barra espaciadora (derecha) o la tecla Mayús izquierda (mano izquierda) para mantener las manos simuladas en la vista, presione la tecla T o Y para girar las manos simuladas, presione Q o E (horizontal)/R o F (vertical)

- [Más información sobre la simulación de entrada en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>Cómo capturar y desplace un objeto
Para hacer que un objeto sea propuesto, asigne estos dos scripts: ManipulationHandler.cs y NearInteractionGrabbable. CS (para captación directa con entrada de seguimiento de mano articulada) ManipulationHandler admite interacciones Near y Far. Puede capturar y trasladar un objeto con la entrada de seguimiento articulado de HoloLens 2 (Near), el rayo de mano (lejano), el rayo del controlador de movimiento (lejano), el cursor de miración de HoloLens & cámara de aire.

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>¿Cómo se cambia el tamaño de un objeto?
ManipulationHandler.cs admite el escalado o la rotación bidireccionales. Esto funciona con varios tipos de entrada, como la entrada de mano articulada de HoloLens 2, la entrada de gestos de la flecha de más de HoloLens y la entrada de gestos de Windows Mixed Reality.

- [Más información sobre el controlador de manipulación en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>¿Cómo se mueve o gira un objeto con precisión?
Asigne BoundingBox.cs a un objeto para usar el cuadro de límite, que es la interfaz para el escalado y la rotación de un objeto. De forma predeterminada, se muestran los controladores y los cables de color azul de HoloLens 1. Para usar controladores animados basados en proximidad de estilo de HoloLens 2, debe asignar Prefabs y materiales. Consulte la [documentación del cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) y la escena de BoundingBoxExamples. Unity para obtener los detalles de configuración.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [Más información sobre el cuadro de límite en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>Cómo hacer que un objeto responda a los eventos de entrada
Asigne PointerHandler.cs a un objeto. En el inspector, podrá usar eventos OnPointerDown (), OnPointerUp (), OnPointerClicked (), OnPointerDragged () para usar estos eventos en un script, implementar IMixedRealityPointerHandler.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Más información sobre el sistema de entrada en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>¿Cómo agregar comentarios visuales?
Asigne Interactable.cs a un objeto. En el inspector, cree un nuevo tema. Mediante el uso de perfiles de tema de interactúas, puede agregar fácilmente comentarios visuales a todos los Estados de interacción de entrada disponibles.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactúable proporciona varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.

- [Más información sobre el interactuable en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Otro bloque de creación importante para los comentarios visuales es el sombreador estándar de MRTK. Con el sombreador estándar de MRTK, puede agregar fácilmente efectos de comentarios visuales como luz de desplazamiento y luz de proximidad. Dado que el sombreador estándar de MRTK realiza un cálculo significativamente menor que el sombreador estándar de Unity, puede crear una experiencia de rendimiento.

Cree un nuevo material y seleccione el "el kit de herramientas de realidad mixta de el sombreador > estándar". O bien, puede elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Más información sobre el sombreador estándar de MRTK en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>¿Cómo agregar comentarios de audio?
Agregue AudioSource a un objeto. A continuación, en los scripts que exponen eventos de entrada (por ejemplo, Interactable.cs o PointerHandler.cs), asigne el objeto al evento y seleccione AudioSource. PlayOneShot (). Puede usar los clips de audio o elegir uno de los recursos de audio de MRTK.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>¿Cómo se usa el botón de estilo Prefabs de HoloLens 2?
MRTK proporciona varios tipos de botones de estilo de Shell (SO) de HoloLens 2. Proporciona comentarios visuales sofisticados, como la luz de proximidad, el cuadro de compresión y un efecto de rizo en la superficie del botón.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

Basta con arrastrar y colocar uno de los botones que se presionan en el estilo de HoloLens 2 recurso prefabricado en la escena. Recurso prefabricado usa Interactable.cs, que se presentó anteriormente. Puede usar eventos expuestos como OnClick () en las acciones que pueden interaccionar para desencadenar.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Más información sobre el botón Prefabs en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>¿Cómo hacer que un objeto siga?
Asigne el script RadialView.cs a un objeto. Forma parte de la serie de scripts de Solver que permite lograr distintos tipos de ubicación de objetos en el espacio 3D. SolverHandler.cs se agregará automáticamente.
A continuación se muestra un ejemplo de la configuración de RadialView para lograr la etiqueta "Follow Lazy" a lo largo del comportamiento como el menú Inicio en el shell de HoloLens. Puede especificar la distancia mínima/máxima y los grados de vista mínimo y máximo. En el ejemplo siguiente se muestra cómo colocar el objeto entre 0,4 m y el intervalo de 0,8 m en 15 °. Ajuste los valores de tiempo de lerp para que la actualización posicional sea más rápida o más lenta.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Más información sobre las resoluciones en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>¿Cómo hacer que un objeto se enfrente?
Asigne el script Billboard.cs a un objeto. Siempre se encontrará con independencia de su posición. Puede especificar la opción del eje dinámico.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


¿Está listo para crear experiencias sorprendentes para la realidad mixta? Visite las páginas siguientes y obtenga más información sobre MRTK y Mixed Reality.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>@Microsoft del diseñador de la experiencia del usuario</td>
</tr>
</table>

## <a name="see-also"></a>Consulta también

* [Kit de herramientas de realidad mixta (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Introducción con MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit a MRTK instrucción de portabilidad](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
