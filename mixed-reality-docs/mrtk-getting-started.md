---
title: Introducción a MRTK versión 2
description: Para los nuevos desarrolladores interesados en aprovechar MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, probar, Kit de herramientas de realidad mixta, MRTK versión 2, MRTK, herramientas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750377"
---
# <a name="getting-started-with-mrtk-v2"></a>Introducción a MRTK v2

## <a name="mrtk-getting-started-guide"></a>MRTK Guía de introducción
Consulte la [MRTK Guía de introducción](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obtener información sobre cómo comenzar con MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>¿Qué es el Kit de herramientas de realidad mixta (MRTK)?
El MRTK es un Kit de herramientas increíbles de código abierto que ha estado presente desde el HoloLens publicó por primera vez y no sería donde se encuentra hoy sin el trabajo duro de nuestra comunidad de desarrolladores que han contribuido a él. Durante los últimos 3 años, hemos tenido en cuenta los comentarios de nuestra comunidad de desarrolladores y generado MRTK v2 para las principales preocupaciones de tener en cuenta.  

La versión 2 MRTK con Unity es un kit de desarrollo multiplataforma de código abierto para las aplicaciones de realidad mixta.  MRTK versión 2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, inmersivos (VR) Windows Mixed Reality y OpenVR plataforma. El proyecto está destinado a reducir las barreras de entrada para crear aplicaciones de realidad mixta y contribuir a la Comunidad que todos a medida que crecen. 


Consulte la [portal de documentación MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obtener más información.

## <a name="feature-areas"></a>Áreas de características

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> Sistema de entrada 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Mano de seguimiento (HoloLens 2)" width="105"> Mano de seguimiento (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Seguimiento (HoloLens 2) de los ojos" width="105">
    Seguimiento (HoloLens 2) de los ojos
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comandos de voz" width="105"> Comandos de voz
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Observación + seleccionar (HoloLens (gen 1))" width="105">
    Observación + seleccionar (HoloLens (gen 1))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="Controles de la interfaz de usuario" width="105"> Controles de la interfaz de usuario
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="Solver e interacciones" width="105"> Solver e interacciones
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualización de controlador" width="105"> Visualización de controlador
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Understanding espacial" width="105"> Understanding espacial
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Herramienta de diagnóstico" width="105"> Herramienta de diagnóstico
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador MRTK estándar" width="105"> Sombreador MRTK estándar
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Bloques de interfaz de usuario y la creación de interacción

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botón" width="250"><br>
    **Button**<br>
    Un control de botón que admite varios métodos de entrada, incluyendo mano articulado del 2 de HoloLens <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Cuadro de límite" width="250"><br>
    **Cuadro de límite**<br>
    Interfaz de usuario estándar para manipular objetos en el espacio 3D <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Controlador de manipulación" width="250"><br>
    **Controlador de manipulación**<br>
    Secuencia de comandos para manipular objetos con uno o dos manos <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Pizarra" width="250"><br>
    **Slate** <br>
    Plano 2D de estilo que admite el desplazamiento con la entrada de la mano articulados <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado del sistema" width="250"><br>
    **Teclado del sistema**<br>
    Script de ejemplo de usar el teclado del sistema en Unity <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interactuable" width="250"><br>
     **Interactable** <br>
     Una secuencia de comandos para hacer que los objetos interactuable con estados visuales y compatibilidad de tema <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solver" width="250"><br>
    **Solver** <br>
    Distintos comportamientos de posicionamiento como tag-along, bloqueo de cuerpo, tamaño de la vista constante y superficie magnética de objeto <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Colección de objetos" width="250"><br>
    **Colección de objetos**<br>
    Secuencia de comandos para disponer de una matriz de objetos de una forma tridimensional <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Información sobre herramientas" width="250">  <br>
    **Información sobre herramientas**<br>
    Anotación de la interfaz de usuario con el sistema delimitador/pivot flexible que puede utilizarse para etiquetar el objeto y los controladores de movimiento <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de la aplicación" width="250"><br>
    **Barra de la aplicación**<br>
    Interfaz de usuario para la activación manual del cuadro de límite <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Punteros" width="250"><br>
    **Punteros**<br>
    Obtenga información sobre los distintos tipos de punteros <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualización de la yema del dedo" width="250"><br>
     **Visualización de la yema del dedo**<br>
     Prestación Visual de la yema del dedo que mejora la confianza para la interacción directa <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Slider**<br>
    Control deslizante de la interfaz de usuario para ajustar los valores auxiliar mano directo interacción de seguimiento <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador MRTK estándar" width="250"><br>
    **Sombreador MRTK estándar**<br>
    Sombreador de estándar de MRTK es compatible con diversos elementos de diseño Fluent con rendimiento <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Chaser conjunta de mano" width="250"><br>
     **Chaser conjunta de mano**<br>
     Muestra cómo usar Solver para asociar objetos a los puntos de unión de mano <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Seguimiento de los ojos: Selección de destino" width="250"><br>
    **Seguimiento de los ojos: Selección de destino**<br>
    Combinar los ojos, voz y mano rápidamente y sin esfuerzo seleccionar hologramas a través de la escena de entrada <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Seguimiento de los ojos: Navegación" width="250"><br>
    **Seguimiento de los ojos: Navegación**<br>
    Obtenga información sobre cómo desplazarse por el texto de auto o zoom con fluidez en contenido centrado en función de lo que se trata de <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Seguimiento de los ojos: Mapa térmico" width="250"><br>
    **Seguimiento de los ojos: Mapa térmico**<br>
    Ejemplos para el registro, cargar y visualizar qué usuarios han empezado a en la aplicación <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Requisito mínimo para MRTK v2
* Unity 2018.3.x
* Microsoft Visual Studio 2017 o posterior
* Windows SDK 18362 + 
* Windows 10 1803 o posterior

## <a name="new-with-mrtk-v2"></a>Nuevo con MRTK v2
Queremos hacer hincapié en nuestro compromiso con estas herramientas de plataforma.  De hecho, hemos aprovechado MRTK versión 2 para desarrollar nuestras experiencias de bandeja de entrada, como la experiencia de instalación (OOBE) y nuestra aplicación de aprendizaje de realidad mixta.  También puede esperar ver nuevas capacidades de HoloLens 2 que primero se expone a través de MRTK porque creemos que es la mejor manera de desarrollar en nuestra plataforma. 

### <a name="modular"></a>Modular
Hemos creado, de manera modular, por lo que no es necesario tener cada bit del Kit de herramientas en el proyecto.  Existen realmente algunas ventajas a este.  Mantiene el tamaño del proyecto más pequeños, así como hace que sea más fácil de administrar.  En él, porque se ha creado teniendo objetos programables y está controlada de interfaz, también es posible para reemplazar los componentes que se incluyen con su propio para admitir otros servicios, sistemas y plataformas.


### <a name="cross-platform"></a>Multiplataforma
Hablando de otras plataformas, tiene la compatibilidad multiplataforma.  Y aunque esto no significa que todas las plataformas solo es compatible de fábrica, nos hemos asegurado de que ninguno de los códigos de Kit de herramientas se interrumpirá cuando cambie su destino de compilación para otras plataformas.  La solidez y la extensibilidad con el diseño modular configura en una ruta de acceso válida para poder admitir varias plataformas, como ARCore, ARKit y OpenVR.


### <a name="performant"></a>Alto rendimiento
Trabajar con las plataformas móviles, se construyó con miras al rendimiento.  Esto es muy importante, y deseamos asegurarnos de que las herramientas no se van a funcionar en su contra.


## <a name="see-also"></a>Vea también
* [Guía de introducción de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Documentación de MRTK principal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instalación de las herramientas](install-the-tools.md)
* [Portabilidad de HTK/MRTK a MRTK versión 2](mrtk-porting-guide.md)
