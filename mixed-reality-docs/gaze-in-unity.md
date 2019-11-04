---
title: Miras en Unity
description: Fijamente es una forma principal de que los usuarios tengan como destino los hologramas que crea la aplicación en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: miras hacia abajo, hacia abajo, Unity, holograma, realidad mixta
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435294"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="0a81c-104">Encabezado de la mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="0a81c-104">Head-gaze in Unity</span></span>

<span data-ttu-id="0a81c-105">[Fijamente](gaze-and-commit.md) es una forma principal de que los usuarios tengan como destino los [hologramas](hologram.md) que crea la aplicación en [realidad mixta](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="0a81c-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="0a81c-106">Implementación del encabezado de mira</span><span class="sxs-lookup"><span data-stu-id="0a81c-106">Implementing head-gaze</span></span>

<span data-ttu-id="0a81c-107">Conceptualmente, el [encabezado](gaze-and-commit.md) se implementa mediante la proyección de un rayo desde el encabezado del usuario donde se encuentra el casco, en la dirección hacia delante hacia delante y con la determinación de la colisión del rayo.</span><span class="sxs-lookup"><span data-stu-id="0a81c-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="0a81c-108">En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md)principal de Unity, concretamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="0a81c-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="0a81c-109">La llamada a [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado una estructura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto 3D en el que se produjo la colisión y el otro GameObject el rayo de la punta con el que está en conflicto.</span><span class="sxs-lookup"><span data-stu-id="0a81c-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="0a81c-110">Ejemplo: implementación de la cabeza de mira</span><span class="sxs-lookup"><span data-stu-id="0a81c-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="0a81c-111">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="0a81c-111">Best practices</span></span>

<span data-ttu-id="0a81c-112">Aunque en el ejemplo anterior se muestra cómo hacer un único Raycast en un bucle de actualización para buscar el destino al que apunta el encabezado del usuario, se recomienda hacerlo en un solo objeto que administre el encabezado y en lugar de hacerlo en cualquier objeto que esté potencialmente interesado en el objetos en el que se mira.</span><span class="sxs-lookup"><span data-stu-id="0a81c-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="0a81c-113">Esto permite que la aplicación guarde el procesamiento realizando una sola mirada Raycast cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="0a81c-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="0a81c-114">Visualización del encabezado</span><span class="sxs-lookup"><span data-stu-id="0a81c-114">Visualizing head-gaze</span></span>

<span data-ttu-id="0a81c-115">Al igual que en el escritorio, donde se usa un puntero del mouse para destinar e interactuar con el contenido, debe implementar un [cursor](cursors.md) que represente el encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="0a81c-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="0a81c-116">Esto proporciona a los usuarios confianza en lo que están a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="0a81c-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="0a81c-117">Mira al principio en el kit de herramientas de realidad mixta V2</span><span class="sxs-lookup"><span data-stu-id="0a81c-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="0a81c-118">Puede obtener acceso a la parte principal del [Administrador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) en MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="0a81c-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a81c-119">Consulta también</span><span class="sxs-lookup"><span data-stu-id="0a81c-119">See also</span></span>
* [<span data-ttu-id="0a81c-120">Cámara</span><span class="sxs-lookup"><span data-stu-id="0a81c-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="0a81c-121">Cursores</span><span class="sxs-lookup"><span data-stu-id="0a81c-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="0a81c-122">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="0a81c-122">Head-gaze and commit</span></span>](gaze-and-commit.md)
