---
title: Cámara en Unity
description: Cómo usar el desarrollo de Main cámara para Windows Mixed Reality de Unity para realizar la representación holográfica
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, representación holográfica, punto de enfoque holográfica y envolventes, búfer de profundidad, sólo orientación, posicional, opaco, transparente, clip
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597778"
---
# <a name="camera-in-unity"></a>Cámara en Unity

Al usar auriculares de realidad mixta, se convierte en el centro de su mundo holográfica. El Unity [cámara](http://docs.unity3d.com/Manual/class-Camera.html) componente controlará automáticamente representación estereoscópica y seguirá el movimiento y la rotación cuando el proyecto tiene "Virtual realidad admite" seleccionado con "Windows Mixed Reality" como el dispositivo (en la sección otras opciones de configuración de la configuración del Reproductor de Windows Store). Esto puede aparecer como "Windows Holographic" en versiones anteriores de Unity.

Sin embargo, a optimizar totalmente calidad visual y [estabilidad holograma](hologram-stability.md), debe establecer la configuración de la cámara se describe a continuación.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, cuando se crea una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente de la cámara, pero no tiene la configuración a continuación se aplican correctamente.

## <a name="holographic-vs-immersive-headsets"></a>Holográfica frente a inmersivos

La configuración predeterminada en el componente de la cámara de Unity es para aplicaciones de 3D tradicionales que necesitan un fondo skybox similar a cuando no tengan un mundo real.
* Cuando se ejecuta en un  **[auriculares envolventes](immersive-headset-hardware-details.md)**, está representando todo lo que ve el usuario y, por lo tanto probablemente deseará mantener skybox.
* Sin embargo, cuando se ejecuta en un **auriculares holográfica** como [HoloLens](hololens-hardware-details.md), debería aparecer el mundo real detrás de todo lo que la cámara representa. Para ello, establecer el fondo de la cámara para ser transparentes (en HoloLens, negro se representa como transparente) en lugar de una textura Skybox:
    1. Seleccione la cámara principal en el panel de jerarquía
    2. En el panel del Inspector, busque el componente de cámara y cambiar la lista desplegable de borrar las marcas de Skybox a Color sólido
    3. Seleccione el selector de color de fondo y cambie los valores RGBA (0, 0, 0, 0)

Puede usar el código de script para determinar en tiempo de ejecución para comprobar si los auriculares es envolvente u holográfica [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).


## <a name="positioning-the-camera"></a>Colocación de la cámara

Será más fácil diseñar la aplicación si imaginar la posición inicial del usuario como (X: 0, Y: 0, Z: 0). Puesto que la cámara principal está realizando el seguimiento movimiento del encabezado del usuario, se puede establecer la posición inicial del usuario al establecer la posición inicial de la cámara principal.
1. Seleccione la cámara principal en el panel de jerarquía
2. En el panel del Inspector, busque el componente de transformación y cambiar la posición de (X: 0, Y: 1, Z: -10) a (X: 0, Y: 0, Z: 0)

   ![Cámara en el panel del Inspector de Unity](images/maincamera-350px.png)<br>
   *Cámara en el panel del Inspector de Unity*

## <a name="clip-planes"></a>Planos de recorte

Representar contenido demasiado al usuario puede ser incómodo en realidad mixta. Puede ajustar el [casi y ahora los planos de recorte](hologram-stability.md#hologram-render-distances) en el componente de la cámara.
1. Seleccione la cámara principal en el panel de jerarquía
2. En el panel del Inspector, busque los planos de recorte del componente de cámara y cambie el cuadro de texto casi de 0,3 a.85. Contenido procesado más estrechas puede provocar malestar de usuario y debe evitarse por la [representar instrucciones distancia](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Varias de las cámaras

Cuando hay varios componentes de la cámara en la escena, Unity sabe qué cámara que se usará para la representación estereoscópica y seguimiento principal Comprobando qué GameObject tiene la etiqueta MainCamera.

## <a name="recentering-a-seated-experience"></a>Alabeo una experiencia de su asiento

Si está creando un [escala asentada experiencia](coordinate-systems.md), puede origin de mundo de Unity centrar en la posición del usuario actual principal mediante una llamada a la **[XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** método.

## <a name="reprojection-modes"></a>Modos de reprojection

HoloLens e inmersivos se reproject cada fotograma que representa la aplicación para ajustar de cualquier predicción de la posición del usuario real principal cuando se emiten photons.

De forma predeterminada:

* **Inmersivos** llevará a cabo reprojection posicional, ajustar sus hologramas de predicción en la posición y orientación, si la aplicación proporciona un búfer de profundidad un período determinado.  Si no se proporciona un búfer de profundidad, el sistema solo corregirá equivocadas de ramas en orientación.
* **Auriculares holográficas** como HoloLens llevará a cabo reprojection posicional si la aplicación proporciona su búfer de profundidad o no.  Reprojection posicional es posible sin búferes de profundidad en HoloLens como representación a menudo es dispersa con un fondo estable proporcionado por el mundo real.

Si sabe que está creando un [experiencia sólo orientación](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) con contenido bloqueado rígidamente en el cuerpo (contenido de vídeo, por ejemplo, de 360 grados), puede establecer explícitamente el modo de reprojection sea orientación solo estableciendo [ HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) a [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Uso compartido de los búferes de profundidad con Windows

Uso compartido de búfer de profundidad de la aplicación para cada fotograma proporcionará la aplicación uno de dos aumenta en la estabilidad de holograma, según el tipo de auriculares de Windows está representación para:
* **Inmersivos** puede realizar reprojection posicional cuando se proporciona un búfer de profundidad, ajustar sus hologramas de predicción en la posición y orientación.
* **Auriculares holográficas** como HoloLens seleccionará automáticamente un [centrarse punto](focus-point-in-unity.md) cuando se proporciona un búfer de profundidad, optimizar la estabilidad holograma a lo largo del plano que forma una intersección con el contenido más.

Para establecer si la aplicación de Unity proporcionará un búfer de profundidad en Windows:
1. Vaya a **editar** > **configuración del proyecto** > **Reproductor** > **ficha Universal Windows Platform**  >  **XR configuración**.
2. Expanda el **Windows Mixed Reality SDK** elemento.
3. Active o desactive el **Habilitar uso compartido de búfer de profundidad** casilla de verificación.  Esto se comprobará de forma predeterminada en los proyectos nuevos creados, ya que esta característica se agregó a Unity y estará desactivada de forma predeterminada para los proyectos anteriores que se han actualizado.

Proporcionar un búfer de profundidad a Windows puede mejorar la calidad visual, siempre y cuando Windows pueden asignar con precisión los valores de la profundidad normalizada por píxel en el búfer de profundidad a las distancias en metros, con los planos far y near que ha establecido en Unity en la cámara principal.  Si la representación pasa la profundidad del identificador de valores de las formas más habituales, por lo general estará bien aquí, aunque render translúcido pasa que escriben en el búfer de profundidad al que se muestra a través de las existentes píxeles de color pueden confundir el reprojection.  Si sabe que las pasadas de representación deje muchos de los píxeles de profundidad final con valores de profundidad imprecisos, es probable que obtenga una mejor calidad visual, desactive la casilla "Habilitar profundidad búfer compartiendo".

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>Programa de instalación automática de escenas de mixed Reality del Kit de herramientas
Al importar [MRTK publicar paquetes de Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonar el proyecto desde el [repositorio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), va a buscar un nuevo menú 'Kit de herramientas de realidad mixta' en Unity. En el menú "Configurar", verá el menú 'Aplicar configuración de escena de Mixed Reality'. Al hacer clic en él, quita la cámara de forma predeterminada y agrega los componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), y [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menú MRTK para la instalación de la escena](images/MRTK_Input_Menu.png)<br>
*Menú MRTK para la instalación de la escena*

![Programa de instalación automática de escenas en MRTK](images/MRTK_HowTo_Input1.png)<br>
*Programa de instalación automática de escenas en MRTK*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefabricado
Puede agregar también manualmente desde el panel de proyecto. Puede encontrar estos componentes como prefabricados. Al buscar **MixedRealityCamera**, podrá ver dos prefabricados cámara diferente. La diferencia es que **MixedRealityCamera** es la cámara solo prefabricado, mientras que **MixedRealityCameraParent** incluye componentes adicionales para el inmersivos como Teleportation, movimiento Controlador y límites.

![Cámara prefabricados en MRTK](images/MRTK_HowTo_Input2.png)<br>
*Cámara prefabricados en MRTK*

**MixedRealtyCamera** admite HoloLens y auriculares envolventes. Detecta el tipo de dispositivo y optimiza las propiedades como borrar las marcas y Skybox. A continuación, encontrará algunas de las propiedades útiles que puede personalizar como Cursor personalizado, los modelos de controlador de movimiento y el suelo.

![Propiedades para el controlador de movimiento de Cursor y Floor](images/MRTK_HowTo_Input3.png)<br>
*Propiedades para el controlador de movimiento de Cursor y Floor*

## <a name="see-also"></a>Vea también
* [Estabilidad holograma](hologram-stability.md)
* [Camera.prefab MixedRealityToolkit principal](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
