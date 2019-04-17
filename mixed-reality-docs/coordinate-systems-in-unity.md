---
title: Sistemas de coordenadas en Unity
description: Aprenda a crear su asiento permanente, sala de escalado y escalado del mundo mixto realidad experiencias en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, del sistema de coordenadas espacial, sólo orientación, sentado a escala, escala permanente, sala-escala, escala mundial, colocada de 360 grados, permanente, sala, mundo, escala, posición, orientación, Unity, delimitador, delimitador espacial, delimitador del mundo, bloqueado contra el mundo, mundo de bloqueo, bloqueado de cuerpo, cuerpo de bloqueo, seguimiento de pérdida, locatability, los límites indicados, centrar
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605774"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="5cd7f-104">Sistemas de coordenadas en Unity</span><span class="sxs-lookup"><span data-stu-id="5cd7f-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="5cd7f-105">Windows Mixed Reality es compatible con aplicaciones en una amplia gama de [experimentar escalas](coordinate-systems.md), desde aplicaciones sólo orientación y asentada de escala de seguridad a través de aplicaciones de escala de la sala.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="5cd7f-106">En HoloLens, puede avanzar y compilar aplicaciones a escala mundial que permiten a los usuarios recorrer más allá de 5 metros, exploración de toda una planta de un edificio y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="5cd7f-107">Es el primer paso para crear una experiencia de realidad mixta en Unity determinar qué [experimentar escala](coordinate-systems.md) destino de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="5cd7f-108">Creación de una experiencia sólo orientación o asentada de escala</span><span class="sxs-lookup"><span data-stu-id="5cd7f-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="5cd7f-109">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5cd7f-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="5cd7f-111">Para crear un **sólo orientación** o **escala asentada experiencia**, debe establecer Unity en el diseño de fondo el tipo de espacio de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="5cd7f-112">Esto establece el sistema de coordenadas de Unity para realizar un seguimiento el [marco estático de referencia](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="5cd7f-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="5cd7f-113">En el modo de seguimiento inmóvil, se coloca el contenido en el editor justo delante de la ubicación predeterminada de la cámara (hacia delante es -Z) aparecerá delante del usuario cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="5cd7f-114">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5cd7f-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="5cd7f-116">Para una pura **experiencia sólo orientación** como un visor de vídeo de 360 grados (donde posicionales actualizaciones principales serían dañen la ilusión), a continuación, puede establecer [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="5cd7f-117">Para un **escala asentada experiencia**, para permitir al usuario más adelante centrar el origen de su asiento, puede llamar a la [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) método:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="5cd7f-118">Creación de una experiencia de escala permanente o sala de escala</span><span class="sxs-lookup"><span data-stu-id="5cd7f-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="5cd7f-119">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5cd7f-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="5cd7f-121">Para un **permanente escala** o **experiencia sala escala**, deberá colocar contenido en relación con el límite inferior.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="5cd7f-122">Razonar el usuario floor utilizando el  **[fase espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa el usuario definidas por el origen del nivel del suelo y límite de espacio opcional, configurar durante la primera ejecución.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="5cd7f-123">Para asegurarse de que Unity está funcionando con su sistema de coordenadas universales a nivel del suelo, puede establecer si Unity para el tipo de espacio de seguimiento de RoomScale y asegúrese de que el conjunto correctamente:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="5cd7f-124">Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universales para realizar un seguimiento el [fase marco de referencia](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="5cd7f-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="5cd7f-125">Si devuelve false SetTrackingSpaceType, Unity no pudo cambiar a fase marco de referencia, probablemente porque el usuario no ha configurado incluso un piso en su entorno.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="5cd7f-126">Esto no es habitual, pero puede ocurrir si el escenario se ha configurado en una sala diferente y el dispositivo se ha movido a la sala actual sin que el usuario que configura una nueva fase.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="5cd7f-127">Una vez que la aplicación establece correctamente el tipo de espacio, contenido colocado en la y de seguimiento de RoomScale = 0 plano aparecerá en el suelo.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="5cd7f-128">El origen en (0, 0, 0) será la ubicación específica en el suelo donde puede levantar el usuario durante la instalación de la sala, con -Z que representa la dirección de avance que se enfrentan durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="5cd7f-129">**Namespace:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="5cd7f-130">**Tipo:** *Límite*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="5cd7f-131">En el código de script, puede, a continuación, llame al método TryGetGeometry para usted es el tipo de UnityEngine.Experimental.XR.Boundary para obtener un polígono límites, especificar un tipo de límite de TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="5cd7f-132">Si el usuario ha definido un límite (obtener una lista de vértices), sabrá que es segura entregar un **experiencia sala escala** al usuario, donde puede guían por la escena crear.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="5cd7f-133">Tenga en cuenta que el sistema automáticamente se representará el límite cuando el usuario se aproxima a él.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="5cd7f-134">La aplicación no necesita usar este polígono para representar el límite de sí mismo.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="5cd7f-135">Sin embargo, puede elegir disponer de los objetos de la escena con este polígono límites, para asegurarse de que el usuario físicamente puede llegar a esos objetos sin teleporting:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="5cd7f-136">Creación de una experiencia del mundo a escala</span><span class="sxs-lookup"><span data-stu-id="5cd7f-136">Building a world-scale experience</span></span>

<span data-ttu-id="5cd7f-137">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="5cd7f-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="5cd7f-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="5cd7f-139">Para true **experiencias del mundo a escala** en HoloLens que permiten a los usuarios consultar más allá de 5 metros, necesitará nuevas técnicas más allá de los que se usan para experiencias de escala de la sala.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="5cd7f-140">Es una técnica clave que se va a usar crear un [delimitador espacial](coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas exactamente en lugar del mundo físico, independientemente de cuánto ha trasladado el usuario y, a continuación, [encontrar esos hologramas nuevo en versiones posteriores sesiones](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="5cd7f-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="5cd7f-141">En Unity, cree un anclaje espacial agregando el **WorldAnchor** componente Unity a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="5cd7f-142">Agregar un anclaje del mundo</span><span class="sxs-lookup"><span data-stu-id="5cd7f-142">Adding a World Anchor</span></span>

<span data-ttu-id="5cd7f-143">Para agregar un anclaje del mundo, llame AddComponent<WorldAnchor>() en el objeto de juego con la transformación que desean fijar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="5cd7f-144">Ya está.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-144">That's it!</span></span> <span data-ttu-id="5cd7f-145">Este objeto de juego ahora se anclará a su ubicación actual en el mundo físico, puede ver sus coordenadas universales de Unity ajustar ligeramente con el tiempo para asegurarse de que alineación físico.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="5cd7f-146">Use [persistencia](persistence-in-unity.md) encontrarlo delimitados ubicación nuevo en una sesión de la aplicación en un futuro.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="5cd7f-147">Eliminación de un anclaje del mundo</span><span class="sxs-lookup"><span data-stu-id="5cd7f-147">Removing a World Anchor</span></span>

<span data-ttu-id="5cd7f-148">Si ya no desea que el GameObject bloqueado en una ubicación del mundo físico y no tiene intención de moverlo este marco, simplemente puede llamar Destroy en el componente de anclaje del mundo.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="5cd7f-149">Si desea mover el GameObject este marco, deberá llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="5cd7f-150">Mover un mundo anclada GameObject</span><span class="sxs-lookup"><span data-stu-id="5cd7f-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="5cd7f-151">No se pueden mover del GameObject mientras un anclaje del mundo está en ella.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="5cd7f-152">Si necesita mover el GameObject este marco, es preciso:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="5cd7f-153">El componente de anclaje del mundo DestroyImmediate</span><span class="sxs-lookup"><span data-stu-id="5cd7f-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="5cd7f-154">Mover el GameObject</span><span class="sxs-lookup"><span data-stu-id="5cd7f-154">Move the GameObject</span></span>
3. <span data-ttu-id="5cd7f-155">Agregue un nuevo componente de anclaje del mundo para el GameObject.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="5cd7f-156">Gestionar los cambios de Locatability</span><span class="sxs-lookup"><span data-stu-id="5cd7f-156">Handling Locatability Changes</span></span>

<span data-ttu-id="5cd7f-157">Un WorldAnchor puede no ser localizable en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="5cd7f-158">Si esto sucede, Unity no va a actualizar la transformación del objeto anclado.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="5cd7f-159">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-159">This also can change while an app is running.</span></span> <span data-ttu-id="5cd7f-160">Error al controlar el cambio en locatability hará que el objeto que no aparezca en la ubicación física adecuada en el mundo.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="5cd7f-161">Para recibir notificaciones sobre cambios locatability:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="5cd7f-162">Suscribirse al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="5cd7f-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="5cd7f-163">Controlar el evento</span><span class="sxs-lookup"><span data-stu-id="5cd7f-163">Handle the event</span></span>

<span data-ttu-id="5cd7f-164">El **OnTrackingChanged** evento se llamará siempre que el delimitador espacial subyacente cambia entre un estado de ser localizable frente a no ser localizable.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="5cd7f-165">A continuación, controlar el evento:</span><span class="sxs-lookup"><span data-stu-id="5cd7f-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="5cd7f-166">A veces los delimitadores se encuentran inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="5cd7f-167">En este caso, se establecerá en true cuando esta propiedad isLocated del delimitador de AddComponent<WorldAnchor>() devuelve.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="5cd7f-168">Como resultado, no se desencadenará el evento OnTrackingChanged.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="5cd7f-169">Un modelo limpio sería llamar a su controlador OnTrackingChanged con el estado inicial de IsLocated después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="5cd7f-170">Uso compartido de los anclajes en todos los dispositivos</span><span class="sxs-lookup"><span data-stu-id="5cd7f-170">Sharing anchors across devices</span></span>

<span data-ttu-id="5cd7f-171">Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para crear un anclaje en la nube duraderas desde un WorldAnchor local, que, a continuación, puede localizar su aplicación a través de varios HoloLens, dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="5cd7f-172">Al compartir un anclaje espacial comunes en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="5cd7f-173">Esto permite experiencias compartidas en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="5cd7f-174">Para empezar a crear experiencias compartidas en Unity, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guías de inicio rápido de Azure espacial delimitadores Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="5cd7f-175">Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y localizar los anclajes en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="5cd7f-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cd7f-176">Vea también</span><span class="sxs-lookup"><span data-stu-id="5cd7f-176">See Also</span></span>
* [<span data-ttu-id="5cd7f-177">Escalas de la experiencia</span><span class="sxs-lookup"><span data-stu-id="5cd7f-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="5cd7f-178">Fase espacial</span><span class="sxs-lookup"><span data-stu-id="5cd7f-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="5cd7f-179">Seguimiento de la pérdida en Unity</span><span class="sxs-lookup"><span data-stu-id="5cd7f-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="5cd7f-180">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="5cd7f-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="5cd7f-181">Persistencia en Unity</span><span class="sxs-lookup"><span data-stu-id="5cd7f-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="5cd7f-182">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="5cd7f-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="5cd7f-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure delimitadores espaciales</a></span><span class="sxs-lookup"><span data-stu-id="5cd7f-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="5cd7f-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Delimitadores espaciales Azure SDK para Unity</a></span><span class="sxs-lookup"><span data-stu-id="5cd7f-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>