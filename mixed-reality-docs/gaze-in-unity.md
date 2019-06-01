---
title: Mirar en Unity
description: Mirada es una manera más sencilla para los usuarios para tener como destino el hologramas que la aplicación se crea en realidad mixta.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: mirada, unity, holograma, realidad mixta
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453719"
---
# <a name="head-gaze-in-unity"></a>Mirada HEAD en Unity

[Observación](gaze.md) es una manera más sencilla para que los usuarios de destino la [hologramas](hologram.md) crea la aplicación en [Mixed Reality](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementación mirada principal

Conceptualmente, [que mirar](gaze.md) se implementa mediante la proyección de un rayo desde principal del usuario donde los auriculares es, en la dirección de avance se enfrentan y determinar qué que ray está en conflicto con. En Unity, la posición del usuario principal y la dirección se exponen a través de los principales Unity [cámara](camera-in-unity.md), concretamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

Una llamada a [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado un [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estructura que contiene información sobre la colisión incluido el punto 3D que se produjo el conflicto y el otro GameObject el rayo mirada entran en conflicto con.

### <a name="example-implement-head-gaze"></a>Por ejemplo: Implemente principal mirada

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

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>En realidad mixta que mirar Toolkit v2
Puede tener acceso a la mirada desde el [entrada Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2.

## <a name="see-also"></a>Vea también
* [Cámara](camera-in-unity.md)
* [Entrada de mirada](gaze.md)
* [Cursores](cursors.md)
* [Selección de destinos de la mirada](gaze-targeting.md)
