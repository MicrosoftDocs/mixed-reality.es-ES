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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="02d9e-104">Mira hacia abajo en Unity</span><span class="sxs-lookup"><span data-stu-id="02d9e-104">Head gaze in Unity</span></span>

<span data-ttu-id="02d9e-105">[Mirada](gaze.md) es una forma principal de que los usuarios tengan como destino los [hologramas](hologram.md) que crea la aplicación en [realidad mixta](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="02d9e-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="02d9e-106">Implementar encabezado</span><span class="sxs-lookup"><span data-stu-id="02d9e-106">Implementing head gaze</span></span>

<span data-ttu-id="02d9e-107">Conceptualmente, la función de [mirada](gaze.md) se implementa mediante la proyección de un rayo desde el principio del usuario donde se encuentran los auriculares, en la dirección de avance hacia delante y con la determinación de la colisión del rayo.</span><span class="sxs-lookup"><span data-stu-id="02d9e-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="02d9e-108">En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md)principal de Unity, concretamente [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="02d9e-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="02d9e-109">La llamada a [física. RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado una estructura [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto 3D en el que se produjo la colisión y el otro GameObject en el que se colisiona el rayo.</span><span class="sxs-lookup"><span data-stu-id="02d9e-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="02d9e-110">Ejemplo: Implementar encabezado</span><span class="sxs-lookup"><span data-stu-id="02d9e-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="02d9e-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="02d9e-111">Best Practices</span></span>

<span data-ttu-id="02d9e-112">Aunque en el ejemplo anterior se muestra cómo hacer un único Raycast en un bucle de actualización para buscar el destino de la mirada, se recomienda hacer esto en un solo objeto que administre fijamente en lugar de hacerlo en cualquier objeto que esté interesado en el objeto que se mira.</span><span class="sxs-lookup"><span data-stu-id="02d9e-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="02d9e-113">Esto permite que la aplicación guarde el procesamiento realizando una sola mirada Raycast cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="02d9e-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="02d9e-114">Visualizar fijamente</span><span class="sxs-lookup"><span data-stu-id="02d9e-114">Visualizing Gaze</span></span>

<span data-ttu-id="02d9e-115">Al igual que en el escritorio, en el que se usa un puntero del mouse para destinar e interactuar con el contenido, se debe implementar un [cursor](cursors.md) que represente la mirada al usuario.</span><span class="sxs-lookup"><span data-stu-id="02d9e-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="02d9e-116">Esto proporciona a los usuarios confianza en lo que están a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="02d9e-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="02d9e-117">Mira fijamente en el kit de herramientas de realidad mixta V2</span><span class="sxs-lookup"><span data-stu-id="02d9e-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="02d9e-118">Puede acceder a la mirada desde el [Administrador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) en MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="02d9e-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="02d9e-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="02d9e-119">See also</span></span>
* [<span data-ttu-id="02d9e-120">Cámara</span><span class="sxs-lookup"><span data-stu-id="02d9e-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="02d9e-121">Entrada de mira</span><span class="sxs-lookup"><span data-stu-id="02d9e-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="02d9e-122">Cursores</span><span class="sxs-lookup"><span data-stu-id="02d9e-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="02d9e-123">Selección de destinos de la mirada</span><span class="sxs-lookup"><span data-stu-id="02d9e-123">Gaze targeting</span></span>](gaze-targeting.md)
