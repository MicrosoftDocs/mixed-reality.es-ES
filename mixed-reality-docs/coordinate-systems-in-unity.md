---
title: Sistemas de coordenadas en Unity
description: Obtenga información sobre cómo compilar experiencias de realidad mixtas colocadas, permanentes, de escala de sala y de gran escala en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, solo orientación, escalado colocado, escalado permanente, escalado de habitación, escalado horizontal, grado de 360, colocada, permanente, habitación, mundo, escala, posición, orientación, Unity, delimitador, anclaje espacial, delimitador mundial, con bloqueo mundial bloqueo mundial, bloqueo de cuerpo, bloqueo de cuerpo, pérdida de seguimiento, localización, límites, recentro
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375772"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="df809-104">Sistemas de coordenadas en Unity</span><span class="sxs-lookup"><span data-stu-id="df809-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="df809-105">Windows Mixed Reality es compatible con aplicaciones a través de una amplia gama de [escalas](coordinate-systems.md), desde aplicaciones de solo orientación y de escalado sentado hasta las aplicaciones a escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="df809-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="df809-106">En HoloLens, puede ir más allá y compilar aplicaciones a gran escala que permitan a los usuarios recorrer más de 5 metros, explorando todo el piso de un edificio y más allá.</span><span class="sxs-lookup"><span data-stu-id="df809-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="df809-107">El primer paso para crear una experiencia de realidad mixta en Unity es determinar la [escala de experiencia](coordinate-systems.md) de destino de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="df809-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="df809-108">Creación de una experiencia de solo orientación o de escalado</span><span class="sxs-lookup"><span data-stu-id="df809-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="df809-109">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="df809-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="df809-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="df809-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="df809-111">Para compilar una experiencia de **solo orientación** o **de escalado original**, debe establecer Unity en el tipo de espacio de seguimiento de la estación.</span><span class="sxs-lookup"><span data-stu-id="df809-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="df809-112">Esto establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="df809-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="df809-113">En el modo de seguimiento estacionario, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparecerá delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="df809-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="df809-114">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="df809-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="df809-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="df809-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="df809-116">En el caso de una **experiencia pura de solo orientación** , como un visor de vídeo de 360 grados (donde las actualizaciones de los cabezales posicionales estropearían la ilusión), puede establecer [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:</span><span class="sxs-lookup"><span data-stu-id="df809-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="df809-117">En el caso de una **experiencia de escalado**inactiva, para permitir que el usuario recentre posteriormente el origen de la caja, puede llamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="df809-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="df809-118">Creación de una experiencia de escalado permanente o a escala de habitación</span><span class="sxs-lookup"><span data-stu-id="df809-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="df809-119">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="df809-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="df809-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="df809-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="df809-121">En el caso de una experiencia de escalado **permanente** o de **escalado de habitación**, deberá colocar contenido en relación con el piso.</span><span class="sxs-lookup"><span data-stu-id="df809-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="df809-122">Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](coordinate-systems.md#spatial-coordinate-systems)** , que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución.</span><span class="sxs-lookup"><span data-stu-id="df809-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="df809-123">Para asegurarse de que Unity funcione con su sistema de coordenadas universal en el nivel inferior, puede establecer Unity en el tipo de espacio de seguimiento de RoomScale y asegurarse de que el conjunto se realiza correctamente:</span><span class="sxs-lookup"><span data-stu-id="df809-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="df809-124">Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del [marco de fase de referencia](coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="df809-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="df809-125">Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de la fase de referencia, probablemente porque el usuario no ha configurado ni siquiera un piso en su entorno.</span><span class="sxs-lookup"><span data-stu-id="df809-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="df809-126">Esto no es habitual, pero puede suceder si la fase se configuró en un salón diferente y el dispositivo se ha trasladado a la habitación actual sin que el usuario configure una nueva fase.</span><span class="sxs-lookup"><span data-stu-id="df809-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="df809-127">Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo.</span><span class="sxs-lookup"><span data-stu-id="df809-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="df809-128">El origen en (0,0) será el lugar específico en el piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección de avance que estaban teniendo lugar durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="df809-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="df809-129">**Espacio de nombres:** *UnityEngine. experimental. XR*</span><span class="sxs-lookup"><span data-stu-id="df809-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="df809-130">**Tipo:** *límite*</span><span class="sxs-lookup"><span data-stu-id="df809-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="df809-131">En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine. experimental. XR. Boundary para obtener un polígono de límite, especificando un tipo de límite de TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="df809-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="df809-132">Si el usuario ha definido un límite (se obtiene una lista de vértices), sabe que es seguro ofrecer una **experiencia de escala de habitación** al usuario, donde puede recorrer la escena que cree.</span><span class="sxs-lookup"><span data-stu-id="df809-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="df809-133">Tenga en cuenta que el sistema representará automáticamente el límite cuando el usuario lo aproxime.</span><span class="sxs-lookup"><span data-stu-id="df809-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="df809-134">No es necesario que la aplicación use este polígono para representar el límite.</span><span class="sxs-lookup"><span data-stu-id="df809-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="df809-135">Sin embargo, puede elegir diseñar los objetos de la escena con este polígono de límite para asegurarse de que el usuario pueda llegar físicamente a esos objetos sin teletransportar:</span><span class="sxs-lookup"><span data-stu-id="df809-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="df809-136">Creación de una experiencia de escala mundial</span><span class="sxs-lookup"><span data-stu-id="df809-136">Building a world-scale experience</span></span>

<span data-ttu-id="df809-137">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="df809-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="df809-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="df809-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="df809-139">En el caso de **experiencias** reales en HoloLens que permitan a los usuarios ir más allá de 5 metros, necesitará nuevas técnicas más allá de las que se usan para experiencias a escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="df809-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="df809-140">Una técnica clave que se va a usar es crear un [delimitador espacial](coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas de forma precisa en el mundo físico, con independencia de cuánto se haya desplazado el usuario y, a continuación, de [volver a buscar esos hologramas en sesiones posteriores](coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="df809-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="df809-141">En Unity, puede crear un delimitador espacial agregando el componente Unity de **WorldAnchor** a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="df809-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="df809-142">Agregar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="df809-142">Adding a World Anchor</span></span>

<span data-ttu-id="df809-143">Para agregar un delimitador mundial, llame a AddComponent<WorldAnchor>() en el objeto de juego con la transformación que quiere delimitar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="df809-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="df809-144">Ya está.</span><span class="sxs-lookup"><span data-stu-id="df809-144">That's it!</span></span> <span data-ttu-id="df809-145">Este objeto de juego se anclará ahora a su ubicación actual en el mundo físico; puede ver que las coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar la alineación física.</span><span class="sxs-lookup"><span data-stu-id="df809-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="df809-146">Use la [persistencia](persistence-in-unity.md) para volver a buscar esta ubicación anclada en una sesión de aplicación futura.</span><span class="sxs-lookup"><span data-stu-id="df809-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="df809-147">Quitar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="df809-147">Removing a World Anchor</span></span>

<span data-ttu-id="df809-148">Si ya no desea que el GameObject esté bloqueado en una ubicación física del mundo y no tiene intención de moverlo a este fotograma, puede llamar simplemente a Destroy en el componente del mundo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="df809-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="df809-149">Si desea trasladar GameObject este fotograma, debe llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="df809-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="df809-150">Mover un GameObject anclado mundial</span><span class="sxs-lookup"><span data-stu-id="df809-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="df809-151">No se puede cambiar GameObject mientras un delimitador internacional está en él.</span><span class="sxs-lookup"><span data-stu-id="df809-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="df809-152">Si necesita trasladar el GameObject de este marco, debe:</span><span class="sxs-lookup"><span data-stu-id="df809-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="df809-153">DestroyImmediate el componente de anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="df809-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="df809-154">Movimiento del GameObject</span><span class="sxs-lookup"><span data-stu-id="df809-154">Move the GameObject</span></span>
3. <span data-ttu-id="df809-155">Agregue un nuevo componente de anclaje mundial a GameObject.</span><span class="sxs-lookup"><span data-stu-id="df809-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="df809-156">Control de los cambios de ubicación</span><span class="sxs-lookup"><span data-stu-id="df809-156">Handling Locatability Changes</span></span>

<span data-ttu-id="df809-157">Es posible que WorldAnchor no se pueda localizar en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="df809-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="df809-158">Si esto ocurre, Unity no actualizará la transformación del objeto delimitado.</span><span class="sxs-lookup"><span data-stu-id="df809-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="df809-159">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="df809-159">This also can change while an app is running.</span></span> <span data-ttu-id="df809-160">Si no se controla el cambio en la localización, el objeto no aparecerá en la ubicación física correcta del mundo.</span><span class="sxs-lookup"><span data-stu-id="df809-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="df809-161">Para recibir notificaciones sobre los cambios de Ubicación:</span><span class="sxs-lookup"><span data-stu-id="df809-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="df809-162">Suscribirse al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="df809-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="df809-163">Controlar el evento</span><span class="sxs-lookup"><span data-stu-id="df809-163">Handle the event</span></span>

<span data-ttu-id="df809-164">Se llamará al evento **OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado que se pueda localizar y que no se pueda localizar.</span><span class="sxs-lookup"><span data-stu-id="df809-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="df809-165">A continuación, controle el evento:</span><span class="sxs-lookup"><span data-stu-id="df809-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="df809-166">A veces, los delimitadores se colocan inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="df809-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="df809-167">En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando se devuelva el<WorldAnchor>de AddComponent ().</span><span class="sxs-lookup"><span data-stu-id="df809-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="df809-168">Como resultado, el evento OnTrackingChanged no se desencadenará.</span><span class="sxs-lookup"><span data-stu-id="df809-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="df809-169">Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="df809-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="df809-170">Compartir delimitadores entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="df809-170">Sharing anchors across devices</span></span>

<span data-ttu-id="df809-171">Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede buscar a continuación en varios dispositivos HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="df809-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="df809-172">Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="df809-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="df809-173">Esto permite compartir experiencias en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="df809-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="df809-174">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="df809-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="df809-175">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="df809-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="df809-176">Consulta también</span><span class="sxs-lookup"><span data-stu-id="df809-176">See Also</span></span>
* [<span data-ttu-id="df809-177">Escalas de experiencia</span><span class="sxs-lookup"><span data-stu-id="df809-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="df809-178">Fase espacial</span><span class="sxs-lookup"><span data-stu-id="df809-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="df809-179">Pérdida de seguimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="df809-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="df809-180">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="df809-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="df809-181">Persistencia en Unity</span><span class="sxs-lookup"><span data-stu-id="df809-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="df809-182">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="df809-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="df809-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="df809-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="df809-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="df809-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>