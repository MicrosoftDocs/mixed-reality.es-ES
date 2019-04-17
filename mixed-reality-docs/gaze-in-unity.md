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
# <a name="gaze-in-unity"></a><span data-ttu-id="7426d-104">Mirar en Unity</span><span class="sxs-lookup"><span data-stu-id="7426d-104">Gaze in Unity</span></span>

<span data-ttu-id="7426d-105">[Observación](gaze.md) es una manera más sencilla para que los usuarios de destino la [hologramas](hologram.md) crea la aplicación en [la realidad mixta](mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="7426d-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="7426d-106">Implementación de mirada</span><span class="sxs-lookup"><span data-stu-id="7426d-106">Implementing Gaze</span></span>

<span data-ttu-id="7426d-107">Conceptualmente, [que mirar](gaze.md) se implementa mediante la proyección de un rayo desde principal del usuario donde los auriculares es, en la dirección de avance se enfrentan y determinar qué que ray está en conflicto con.</span><span class="sxs-lookup"><span data-stu-id="7426d-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="7426d-108">En Unity, la posición del usuario principal y la dirección se exponen a través de los principales Unity [cámara](camera-in-unity.md), concretamente [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ Transform.Position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="7426d-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="7426d-109">Una llamada a [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) da como resultado un [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) estructura que contiene información sobre la colisión incluido el punto 3D que se produjo el conflicto y el otro GameObject el rayo mirada entran en conflicto con.</span><span class="sxs-lookup"><span data-stu-id="7426d-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="7426d-110">Por ejemplo: Implemente mirada</span><span class="sxs-lookup"><span data-stu-id="7426d-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="7426d-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="7426d-111">Best Practices</span></span>

<span data-ttu-id="7426d-112">Aunque el ejemplo anterior muestra cómo hacer una sola raycast en un bucle de actualización para encontrar el destino mirada, se recomienda hacer esto en un único objeto administración mirada en lugar de hacerlo en cualquier objeto que potencialmente está interesado en el objeto que se va a gazed en.</span><span class="sxs-lookup"><span data-stu-id="7426d-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="7426d-113">Esto permite que la aplicación guarde procesamiento haciendo raycast de una sola mirada cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="7426d-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="7426d-114">Visualización de mirada</span><span class="sxs-lookup"><span data-stu-id="7426d-114">Visualizing Gaze</span></span>

<span data-ttu-id="7426d-115">Al igual que en el escritorio donde usar un puntero del mouse de destino e interactuar con el contenido, debe implementar un [cursor](cursors.md) que representa la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="7426d-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="7426d-116">Esto proporciona la confianza de los usuarios en lo que va a interactuar con.</span><span class="sxs-lookup"><span data-stu-id="7426d-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="7426d-117">En el Kit de herramientas de realidad mixta que mirar</span><span class="sxs-lookup"><span data-stu-id="7426d-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="7426d-118">Al importar [MRTK publicar paquetes de Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonar el proyecto desde el [repositorio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), va a buscar un nuevo menú 'Kit de herramientas de realidad mixta' en Unity.</span><span class="sxs-lookup"><span data-stu-id="7426d-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="7426d-119">En el menú "Configurar", verá el menú 'Aplicar configuración de escena de Mixed Reality'.</span><span class="sxs-lookup"><span data-stu-id="7426d-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="7426d-120">Al hacer clic en él, quita la cámara de forma predeterminada y agrega los componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), y [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span><span class="sxs-lookup"><span data-stu-id="7426d-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="7426d-121">![Menú MRTK para la instalación de la escena](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="7426d-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="7426d-122">*Menú MRTK para la instalación de la escena*</span><span class="sxs-lookup"><span data-stu-id="7426d-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="7426d-123">![Programa de instalación automática de escenas en MRTK](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="7426d-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="7426d-124">*Programa de instalación automática de escenas en MRTK*</span><span class="sxs-lookup"><span data-stu-id="7426d-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="7426d-125">Observación de los scripts relacionados en el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="7426d-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="7426d-126">Mixto del Kit de herramientas de realidad InputManager prefabricado incluye [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) y [que mirar estabilizador](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span><span class="sxs-lookup"><span data-stu-id="7426d-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="7426d-127">En [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), puede asignar el Cursor personalizado.</span><span class="sxs-lookup"><span data-stu-id="7426d-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="7426d-128">De forma predeterminada, se anima [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) se asigna.</span><span class="sxs-lookup"><span data-stu-id="7426d-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="7426d-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) y [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) se muestra cómo visualizar su mirada al uso de cursores.</span><span class="sxs-lookup"><span data-stu-id="7426d-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="7426d-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="7426d-130">See also</span></span>
* [<span data-ttu-id="7426d-131">Cámara</span><span class="sxs-lookup"><span data-stu-id="7426d-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="7426d-132">Gaze</span><span class="sxs-lookup"><span data-stu-id="7426d-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="7426d-133">Cursores</span><span class="sxs-lookup"><span data-stu-id="7426d-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7426d-134">Mirada destinadas a</span><span class="sxs-lookup"><span data-stu-id="7426d-134">Gaze targeting</span></span>](gaze-targeting.md)
