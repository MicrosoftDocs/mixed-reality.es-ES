---
title: Mirar en Unity
description: Mirada es una manera más sencilla para los usuarios para tener como destino el hologramas que la aplicación se crea en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: mirada, unity, holograma, realidad mixta
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605724"
---
# <a name="gaze-in-unity"></a>Mirar en Unity

[Observación](gaze.md) es una manera más sencilla para que los usuarios de destino la [hologramas](hologram.md) crea la aplicación en [la realidad mixta](mixed-reality.md).

## <a name="implementing-gaze"></a>Implementación de mirada

Conceptualmente, [que mirar](gaze.md) se implementa mediante la proyección de un rayo desde principal del usuario donde los auriculares es, en la dirección de avance se enfrentan y determinar qué que ray está en conflicto con. En Unity, la posición del usuario principal y la dirección se exponen a través de los principales Unity [cámara](camera-in-unity.md), concretamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Una llamada a [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado un [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estructura que contiene información sobre la colisión incluido el punto 3D que se produjo el conflicto y el otro GameObject el rayo mirada entran en conflicto con.

### <a name="example-implement-gaze"></a>Por ejemplo: Implemente mirada

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>Procedimientos recomendados

Aunque el ejemplo anterior muestra cómo hacer una sola raycast en un bucle de actualización para encontrar el destino mirada, se recomienda hacer esto en un único objeto administración mirada en lugar de hacerlo en cualquier objeto que potencialmente está interesado en el objeto que se va a gazed en. Esto permite que la aplicación guarde procesamiento haciendo raycast de una sola mirada cada fotograma.

## <a name="visualizing-gaze"></a>Visualización de mirada

Al igual que en el escritorio donde usar un puntero del mouse de destino e interactuar con el contenido, debe implementar un [cursor](cursors.md) que representa la mirada del usuario. Esto proporciona la confianza de los usuarios en lo que va a interactuar con.

## <a name="gaze-in-mixed-reality-toolkit"></a>En el Kit de herramientas de realidad mixta que mirar
Al importar [MRTK publicar paquetes de Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonar el proyecto desde el [repositorio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), va a buscar un nuevo menú 'Kit de herramientas de realidad mixta' en Unity. En el menú "Configurar", verá el menú 'Aplicar configuración de escena de Mixed Reality'. Al hacer clic en él, quita la cámara de forma predeterminada y agrega los componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), y [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menú MRTK para la instalación de la escena](images/MRTK_Input_Menu.png)<br>
*Menú MRTK para la instalación de la escena*

![Programa de instalación automática de escenas en MRTK](images/MRTK_HowTo_Input1.png)<br>
*Programa de instalación automática de escenas en MRTK*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>Observación de los scripts relacionados en el Kit de herramientas de realidad mixta
Mixto del Kit de herramientas de realidad InputManager prefabricado incluye [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) y [que mirar estabilizador](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs). En [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), puede asignar el Cursor personalizado. De forma predeterminada, se anima [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) se asigna.

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) y [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) se muestra cómo visualizar su mirada al uso de cursores.

## <a name="see-also"></a>Vea también
* [Cámara](camera-in-unity.md)
* [Gaze](gaze.md)
* [Cursores](cursors.md)
* [Mirada destinadas a](gaze-targeting.md)
