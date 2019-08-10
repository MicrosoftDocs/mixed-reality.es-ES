---
title: Introducción a la versión 2 de MRTK
description: Para los nuevos desarrolladores interesados en aprovechar MRTK
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, test, kit de herramientas de realidad mixta, MRTK versión 2, MRTK, herramientas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: c785498e1533b2117249d3b21952ff56190126c0
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2019
ms.locfileid: "68937084"
---
# <a name="getting-started-with-mrtk-v2"></a>Introducción a MRTK V2

## <a name="mrtk-getting-started-guide"></a>Guía de Introducción de MRTK
Vea la [Guía de introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obtener información sobre cómo empezar a usar MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>¿Qué es el kit de herramientas de realidad mixta (MRTK)?
MRTK es un increíble kit de herramientas de código abierto que ha estado de la primera vez que se lanzó HoloLens, y no sería el lugar en el que se encontraba hoy sin el trabajo de nuestra comunidad de desarrolladores que ha contribuido. Durante los últimos 3 años, hemos escuchado los comentarios de nuestra comunidad de desarrolladores y hemos creado MRTK v2 para tener en cuenta las preocupaciones más importantes.  

MRTK V2 con Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.  La versión 2 de MRTK está pensada para acelerar el desarrollo de aplicaciones que tienen como destino Microsoft HoloLens, auriculares con Windows Mixed Reality inmersivo (VR) y plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad. 


Consulte el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obtener más información.

## <a name="feature-areas"></a>Áreas de características

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="Sistema de entrada" width="105"> Sistema de entrada 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="Seguimiento de mano (HoloLens 2)" width="105"> Seguimiento de mano (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="Seguimiento ocular (HoloLens 2)" width="105">
    Seguimiento ocular (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="Comandos de voz" width="105"> Comandos de voz
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Mira y seleccionar (HoloLens (1ª generación))" width="105">
    Mira y seleccionar (HoloLens (1ª generación))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teletraslado" width="105"> Teletraslado
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
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="Visualización del controlador" width="105"> Visualización del controlador
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="Descripción espacial" width="105"> Descripción espacial
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="Herramienta de diagnóstico" width="105"> Herramienta de diagnóstico
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="Sombreador estándar de MRTK" width="105"> Sombreador estándar de MRTK
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>Bloques de creación de interfaces de usuario e interacción

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="Botón" width="250"><br>
    **Button**<br>
    Control de botón que admite varios métodos de entrada, incluida la mano articulada de HoloLens 2.<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="Cuadro de límite" width="250"><br>
    **Cuadro de límite**<br>
    Interfaz de usuario estándar para manipular objetos en el espacio 3D<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="Controlador de manipulación" width="250"><br>
    **Controlador de manipulación**<br>
    Script para manipular objetos con una o dos manos<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="Tabletas" width="250"><br>
    **Tabletas** <br>
    plano de estilo 2D que admite el desplazamiento con entrada de mano articulada<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="Teclado del sistema" width="250"><br>
    **Teclado del sistema**<br>
    Script de ejemplo de uso del teclado del sistema en Unity<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interactuable" width="250"><br>
     **Interactuable** <br>
     Un script para que los objetos interactúen con los Estados visuales y la compatibilidad con temas<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="Solucionador" width="250"><br>
    **Solucionador** <br>
    Varios comportamientos de posicionamiento de objetos, como etiqueta, el bloqueo del cuerpo, el tamaño de la vista constante y el magnetismo de superficie<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="Colección de objetos" width="250"><br>
    **Colección de objetos**<br>
    Script para diseñar una matriz de objetos en una forma tridimensional<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Información sobre herramientas" width="250">  <br>
    **Herramienta**<br>
    Interfaz de usuario de anotación con sistema de delimitador/dinamización flexible que se puede usar para etiquetar controladores de movimiento y objetos<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="Barra de la aplicación" width="250"><br>
    **Barra de la aplicación**<br>
    Interfaz de usuario para la activación manual del cuadro de límite<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="Punteros" width="250"><br>
    **Punteros**<br>
    Más información sobre los distintos tipos de punteros<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Visualización del dedo" width="250"><br>
     **Visualización del dedo**<br>
     La asequibilidad visual de la mano, lo que mejora la confianza para la interacción directa<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="Slider" width="250"><br>
    **Slider**<br>
    Interfaz de usuario del control deslizante para ajustar los valores que admiten la interacción directa de seguimiento<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="Sombreador estándar de MRTK" width="250"><br>
    **Sombreador estándar de MRTK**<br>
    El sombreador estándar de MRTK admite varios elementos de diseño fluidas con rendimiento<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="Persecución de mano" width="250"><br>
     **Persecución de mano**<br>
     Muestra cómo usar Solver para adjuntar objetos a las uniones a mano<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="Seguimiento ocular: Selección de destino" width="250"><br>
    **Seguimiento ocular: Selección de destino**<br>
    Combine los ojos, la voz y la entrada a mano para seleccionar los hologramas de forma rápida y sencilla a través de la escena<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="Seguimiento ocular: Navegación" width="250"><br>
    **Seguimiento ocular: Explora**<br>
    Obtenga información acerca de Cómo desplazarse por texto automáticamente o acercar el contenido centrado en función de lo que está examinando<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="Seguimiento ocular: Mapa térmico" width="250"><br>
    **Seguimiento ocular: Mapa térmico**<br>
    Ejemplos de registro, carga y visualización de lo que los usuarios han estado examinando en la aplicación<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>Requisito mínimo para MRTK V2
* Unity 2018.4. x
* Microsoft Visual Studio 2017 o posterior
* Windows SDK 18362 + 
* Windows 10 1803 o posterior

## <a name="new-with-mrtk-v2"></a>Novedad con MRTK V2
Queremos someter nuestro compromiso a estas herramientas de plataforma.  De hecho, aprovechamos la versión 2 de MRTK para desarrollar nuestras experiencias de bandeja de entrada, como la experiencia de instalación (OOBE) y nuestra aplicación de aprendizaje de realidad mixta.  También puede esperar ver las nuevas funcionalidades de HoloLens 2 que se exponen por primera vez a través de MRTK porque creemos que es la mejor manera de desarrollar en nuestra plataforma. 

### <a name="modular"></a>Módulos
Se ha creado de forma modular, por lo que no es necesario realizar cada bit del kit de herramientas en el proyecto.  En realidad, hay algunas ventajas.  Permite reducir el tamaño del proyecto, así como facilitar la administración.  Además, dado que se crea con objetos que admiten scripts y está orientado a la interfaz, también es posible reemplazar los componentes que se incluyen por su cuenta, para admitir otros servicios, sistemas y plataformas.


### <a name="cross-platform"></a>Multiplataforma
Hablando de otras plataformas, tiene compatibilidad entre plataformas.  Y aunque esto no significa que todas las plataformas se admitan de forma preestablecida, nos hemos asegurado de que ninguno de los códigos del kit de herramientas se interrumpa al cambiar el destino de compilación a otras plataformas.  La robustez y la extensibilidad con el diseño modular le establecen una buena ruta de acceso para poder admitir varias plataformas, como ARCore, ARKit y OpenVR.


### <a name="performant"></a>Rendimiento
Al trabajar con plataformas móviles, se construyó pensando en el rendimiento.  Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan a trabajar con usted.


## <a name="see-also"></a>Vea también
* [Guía de introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Página principal de la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instalación de las herramientas](install-the-tools.md)
* [Migración de HTK/MRTK a MRTK versión 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
