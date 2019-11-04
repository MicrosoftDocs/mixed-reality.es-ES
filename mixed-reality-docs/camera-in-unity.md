---
title: Cámara en Unity
description: Cómo usar la cámara principal de Unity para el desarrollo de la realidad mixta de Windows para realizar la representación holográfica
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, representación holográfica, Holographic, envolvente, punto de enfoque, búfer de profundidad, solo orientación, posicional, opaco, transparente, clip
ms.openlocfilehash: 1a2e66d5c028109a58ea8682668521f50158add9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436959"
---
# <a name="camera-in-unity"></a>Cámara en Unity

Cuando se gasta un auricular de realidad mixta, se convierte en el centro del mundo holográfica. El componente de [cámara](https://docs.unity3d.com/Manual/class-Camera.html) Unity controlará automáticamente la representación de Stereoscopic y seguirá el movimiento y la rotación del cabezal cuando el proyecto tenga seleccionada la opción "realidad virtual" con "Windows Mixed Reality" como dispositivo (en la otra configuración sección de la configuración del reproductor de la tienda Windows). Esto puede aparecer como "Windows Holographic" en versiones anteriores de Unity.

Sin embargo, para optimizar completamente la calidad visual y la [estabilidad del holograma](hologram-stability.md), debe establecer la configuración de la cámara que se describe a continuación.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, cuando se crea una nueva escena en Unity, contiene una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero no tiene la configuración que se aplica correctamente.

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>Configuración automática de escenas y cámaras con el kit de herramientas de realidad mixta V2

Siga la guía [paso a paso](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para agregar el kit de herramientas de realidad mixta a su proyecto de Unity y se configurará automáticamente el proyecto.

También puede configurar manualmente el proyecto sin MRTK con la guía de la sección siguiente.

## <a name="holographic-vs-immersive-headsets"></a>Auriculares holográfica frente a auriculares envolvente

La configuración predeterminada en el componente de cámara Unity es para las aplicaciones 3D tradicionales que necesitan un fondo similar a SkyBOX, ya que no tienen un mundo real.

* Cuando se ejecuta en un **[auricular envolvente](immersive-headset-hardware-details.md)** , está representando todo lo que ve el usuario y, por lo tanto, es probable que quiera mantener el skybox.
* Sin embargo, cuando se ejecuta en un **casco holográfica** como [HoloLens](hololens-hardware-details.md), el mundo real debe aparecer detrás de todo lo que se representa en la cámara. Para ello, configure el fondo de la cámara para que sea transparente (en HoloLens, la representación en negro es transparente) en lugar de una textura SKYBOX:
    1. Seleccionar la cámara principal en el panel de jerarquías
    2. En el panel Inspector, busque el componente Camera y cambie la lista desplegable Clear flags de SKYBOX a Solid color.
    3. Seleccione el selector de colores de fondo y cambie los valores RGBA a (0, 0, 0, 0)

Puede usar el código de script para determinar en tiempo de ejecución si el casco es inmersivo o Holographic comprobando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).

## <a name="positioning-the-camera"></a>Posicionamiento de la cámara

Es más fácil diseñar la aplicación si se imagina la posición inicial del usuario como (X: 0, Y: 0, Z: 0). Dado que la cámara principal está realizando el seguimiento del movimiento del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.

1. Seleccionar cámara principal en el panel jerarquía
2. En el panel Inspector, busque el componente de transformación y cambie la posición de (X: 0, Y: 1, Z:-10) a (X: 0, Y: 0, Z: 0)

   ![cámara en el panel del inspector en Unity](images/maincamera-350px.png)  
   *Cámara en el panel del inspector en Unity*

## <a name="clip-planes"></a>Planos de recortes

La representación de contenido demasiado cercana al usuario puede resultar incómodo en la realidad mixta. Puede ajustar los [planos de clips cercanos y alejados](hologram-stability.md#hologram-render-distances) en el componente de cámara.

1. Seleccionar la cámara principal en el panel de jerarquías
2. En el panel Inspector, busque los planos de recorte del componente de cámara y cambie el cuadro de texto Near de 0,3 a. 85. El contenido representado aún más cerca puede dar lugar a la molestia del usuario y debe evitarse según las [directrices de distancia de representación](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Varias cámaras

Cuando hay varios componentes de cámara en la escena, Unity sabe qué cámara usar para la representación de Stereoscopic y el seguimiento de los cabezales comprobando qué GameObject tiene la etiqueta MainCamera.

## <a name="recentering-a-seated-experience"></a>Recentro de una experiencia sentada

Si va a crear una [experiencia de escalado original](coordinate-systems.md), puede volver a centrar el origen mundial de Unity en la posición principal del usuario mediante una llamada a **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .

## <a name="reprojection-modes"></a>Modos de Reproyección

Tanto HoloLens como los auriculares envolventes se reproyectan en cada fotograma que representa la aplicación para ajustarse a cualquier predicción de la posición principal real del usuario cuando se emiten las fotos.

De forma predeterminada:

* Los **auriculares envolventes** realizarán una Reproyección posicional, ajustando los hologramas para una predicción inesperada en la posición y la orientación, si la aplicación proporciona un búfer de profundidad para un fotograma determinado.  Si no se proporciona un búfer de profundidad, el sistema solo corregirá errores de predicciones en la orientación.
* Los **auriculares holográficas** como HoloLens realizarán una Reproyección posicional tanto si la aplicación proporciona su búfer de profundidad como si no.  La Reproyección posicional es posible sin búferes de profundidad en HoloLens, ya que la representación suele ser dispersa con un fondo estable proporcionado por el mundo real.

Si sabe que está creando una [experiencia de solo orientación](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) con contenido rígidomente bloqueado por el cuerpo (por ejemplo, contenido de vídeo de 360 grados), puede establecer explícitamente el modo de Reproyección para que sea Orientation solo [estableciendo HolographicSettings. ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) a [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Uso compartido de los búferes de profundidad con Windows

Compartir el búfer de profundidad de la aplicación en Windows cada fotograma proporcionará a la aplicación una de estas dos aumentos en la estabilidad del holograma, en función del tipo de casco que se está representando:

* Los **auriculares envolventes** pueden realizar una Reproyección posicional cuando se proporciona un búfer de profundidad, ajustando los hologramas para una predicción inesperada en la posición y la orientación.
* Los **auriculares holográficas** tienen varios métodos diferentes. HoloLens 1 seleccionará automáticamente un [punto de enfoque](focus-point-in-unity.md) cuando se proporcione un búfer de profundidad, optimizando la estabilidad del holograma a lo largo del plano que intersecta el mayor contenido. HoloLens 2 estabilizará el contenido mediante [LSR de profundidad (vea la sección comentarios)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

Para establecer si la aplicación de Unity proporcionará un búfer de profundidad a Windows:

1. Vaya a **editar** > **configuración del proyecto** > **Player** > **plataforma universal de Windows Tab** > **configuración de XR**.
2. Expanda el elemento **SDK de Windows Mixed Reality** .
3. Active o desactive la casilla **Habilitar uso compartido del búfer de profundidad** .  Se comprobará de forma predeterminada en los proyectos nuevos creados desde que esta característica se agregó a Unity y se desactivará de forma predeterminada para los proyectos anteriores que se actualizaron.

Proporcionar un búfer de profundidad a Windows puede mejorar la calidad visual, siempre y cuando Windows pueda asignar con precisión los valores normalizados de profundidad por píxel en el búfer de profundidad a distancias en metros, con los planos cercanos y lejanos que haya establecido en Unity en la cámara principal.  Si las pasadas de representación controlan los valores de profundidad de maneras típicas, generalmente debería estar bien aquí, aunque las pasadas de representación translúcidas que escriben en el búfer de profundidad mientras se muestran a los píxeles de color existentes pueden confundir la Reproyección.  Si sabe que las fases de representación van a dejar muchos de los píxeles de profundidad finales con valores de profundidad inexactos, es probable que obtenga una mejor calidad visual si desactiva "habilitar el uso compartido del búfer de profundidad".

## <a name="see-also"></a>Consulta también

* [Estabilidad de hologramas](hologram-stability.md)
* [Cámara principal de MixedRealityToolkit. recurso prefabricado](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
