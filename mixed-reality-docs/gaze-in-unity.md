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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="6b14a-104">Mirada HEAD en Unity</span><span class="sxs-lookup"><span data-stu-id="6b14a-104">Head gaze in Unity</span></span>

<span data-ttu-id="6b14a-105">[Observación](gaze.md) es una manera más sencilla para que los usuarios de destino la [hologramas](hologram.md) crea la aplicación en [Mixed Reality](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="6b14a-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="6b14a-106">Implementación mirada principal</span><span class="sxs-lookup"><span data-stu-id="6b14a-106">Implementing head gaze</span></span>

<span data-ttu-id="6b14a-107">Conceptualmente, [que mirar](gaze.md) se implementa mediante la proyección de un rayo desde principal del usuario donde los auriculares es, en la dirección de avance se enfrentan y determinar qué que ray está en conflicto con.</span><span class="sxs-lookup"><span data-stu-id="6b14a-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="6b14a-108">En Unity, la posición del usuario principal y la dirección se exponen a través de los principales Unity [cámara](camera-in-unity.md), concretamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="6b14a-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="6b14a-109">Una llamada a [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado un [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estructura que contiene información sobre la colisión incluido el punto 3D que se produjo el conflicto y el otro GameObject el rayo mirada entran en conflicto con.</span><span class="sxs-lookup"><span data-stu-id="6b14a-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="6b14a-110">Por ejemplo: Implemente principal mirada</span><span class="sxs-lookup"><span data-stu-id="6b14a-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="6b14a-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="6b14a-111">Best Practices</span></span>

<span data-ttu-id="6b14a-112">Aunque el ejemplo anterior muestra cómo hacer una sola raycast en un bucle de actualización para encontrar el destino mirada, se recomienda hacer esto en un único objeto administración mirada en lugar de hacerlo en cualquier objeto que potencialmente está interesado en el objeto que se va a gazed en.</span><span class="sxs-lookup"><span data-stu-id="6b14a-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="6b14a-113">Esto permite que la aplicación guarde procesamiento haciendo raycast de una sola mirada cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="6b14a-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="6b14a-114">Visualización de mirada</span><span class="sxs-lookup"><span data-stu-id="6b14a-114">Visualizing Gaze</span></span>

<span data-ttu-id="6b14a-115">Al igual que en el escritorio donde usar un puntero del mouse de destino e interactuar con el contenido, debe implementar un [cursor](cursors.md) que representa la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="6b14a-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="6b14a-116">Esto proporciona la confianza de los usuarios en lo que va a interactuar con.</span><span class="sxs-lookup"><span data-stu-id="6b14a-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="6b14a-117">En realidad mixta que mirar Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="6b14a-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="6b14a-118">Puede tener acceso a la mirada desde el [entrada Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="6b14a-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b14a-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="6b14a-119">See also</span></span>
* [<span data-ttu-id="6b14a-120">Cámara</span><span class="sxs-lookup"><span data-stu-id="6b14a-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="6b14a-121">Entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="6b14a-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="6b14a-122">Cursores</span><span class="sxs-lookup"><span data-stu-id="6b14a-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6b14a-123">Selección de destinos de la mirada</span><span class="sxs-lookup"><span data-stu-id="6b14a-123">Gaze targeting</span></span>](gaze-targeting.md)
