---
title: Miras en Unity
description: Fijamente es una forma principal de que los usuarios tengan como destino los hologramas que crea la aplicación en realidad mixta.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: mira fijamente, Unity, holograma, realidad mixta
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453719"
---
# <a name="head-gaze-in-unity"></a>Mira hacia abajo en Unity

[Mirada](gaze.md) es una forma principal de que los usuarios tengan como destino los [hologramas](hologram.md) que crea la aplicación en [realidad mixta](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementar encabezado

Conceptualmente, la función de [mirada](gaze.md) se implementa mediante la proyección de un rayo desde el principio del usuario donde se encuentran los auriculares, en la dirección de avance hacia delante y con la determinación de la colisión del rayo. En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md)principal de Unity, concretamente [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

La llamada a [física. RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado una estructura [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto 3D en el que se produjo la colisión y el otro GameObject en el que se colisiona el rayo.

### <a name="example-implement-head-gaze"></a>Ejemplo: Implementar encabezado

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

Aunque en el ejemplo anterior se muestra cómo hacer un único Raycast en un bucle de actualización para buscar el destino de la mirada, se recomienda hacer esto en un solo objeto que administre fijamente en lugar de hacerlo en cualquier objeto que esté interesado en el objeto que se mira. Esto permite que la aplicación guarde el procesamiento realizando una sola mirada Raycast cada fotograma.

## <a name="visualizing-gaze"></a>Visualizar fijamente

Al igual que en el escritorio, en el que se usa un puntero del mouse para destinar e interactuar con el contenido, se debe implementar un [cursor](cursors.md) que represente la mirada al usuario. Esto proporciona a los usuarios confianza en lo que están a punto de interactuar.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>Mira fijamente en el kit de herramientas de realidad mixta V2
Puede acceder a la mirada desde el [Administrador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) en MRTK V2.

## <a name="see-also"></a>Vea también
* [Cámara](camera-in-unity.md)
* [Entrada de mira](gaze.md)
* [Cursores](cursors.md)
* [Selección de destinos de la mirada](gaze-targeting.md)
