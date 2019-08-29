---
title: Miras en Unity
description: Fijamente es una forma principal de que los usuarios tengan como destino los hologramas que crea la aplicación en realidad mixta.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: miras hacia abajo, hacia abajo, Unity, holograma, realidad mixta
ms.openlocfilehash: 43e643bac00e3c889b14000331d2ed95014fdcc5
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122040"
---
# <a name="head-gaze-in-unity"></a>Encabezado de la mirada en Unity

[Mirada](gaze.md) es una forma principal de que los usuarios tengan como destino los [hologramas](hologram.md) que crea la aplicación en [realidad mixta](mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementación del encabezado de mira

Conceptualmente, el [encabezado](gaze.md) se implementa mediante la proyección de un rayo desde el encabezado del usuario donde se encuentra el casco, en la dirección hacia delante hacia delante y con la determinación de la colisión del rayo. En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md)principal de Unity, concretamente [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

La llamada a [física. RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado una estructura [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto 3D en el que se produjo la colisión y el otro GameObject el rayo de la punta con el que está en conflicto.

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

Aunque en el ejemplo anterior se muestra cómo hacer un único Raycast en un bucle de actualización para buscar el destino al que apunta el encabezado del usuario, se recomienda hacerlo en un solo objeto que administre el encabezado y en lugar de hacerlo en cualquier objeto que esté potencialmente interesado en el objetos en el que se mira. Esto permite que la aplicación guarde el procesamiento realizando una sola mirada Raycast cada fotograma.

## <a name="visualizing-head-gaze"></a>Visualización del encabezado

Al igual que en el escritorio, donde se usa un puntero del mouse para destinar e interactuar con el contenido, debe implementar un [cursor](cursors.md) que represente el encabezado del usuario. Esto proporciona a los usuarios confianza en lo que están a punto de interactuar.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Mira al principio en el kit de herramientas de realidad mixta V2
Puede obtener acceso a la parte principal del [Administrador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) en MRTK V2.

## <a name="see-also"></a>Vea también
* [Cámara](camera-in-unity.md)
* [Cursores](cursors.md)
* [Entrada de mira](gaze.md)
* [Selección de destinos de la mirada](gaze-targeting.md)
