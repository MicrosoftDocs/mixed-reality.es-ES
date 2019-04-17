---
title: Persistencia en Unity
description: Persistencia permite a los usuarios anclar hologramas individuales o un área de trabajo siempre que sea que deseen y, a continuación, busque, donde espera durante varias usa de la aplicación.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistencia, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605779"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="2d825-104">Persistencia en Unity</span><span class="sxs-lookup"><span data-stu-id="2d825-104">Persistence in Unity</span></span>

<span data-ttu-id="2d825-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="2d825-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="2d825-106">**Clase:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="2d825-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="2d825-107">El WorldAnchorStore es la clave para crear experiencias holográficas donde hologramas permanecen en posiciones específicas reales entre las instancias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2d825-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="2d825-108">Esto le permite a los usuarios anclan hologramas individuales o un área de trabajo donde desee y, a continuación, más adelante le resulte donde esperan a lo largo de muchos usos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2d825-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="2d825-109">Cómo conservar hologramas entre sesiones</span><span class="sxs-lookup"><span data-stu-id="2d825-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="2d825-110">El WorldAnchorStore le permitirá conservar la ubicación del WorldAnchor entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="2d825-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="2d825-111">Para conservar realmente hologramas entre sesiones, deberá por separado al realizar un seguimiento de los GameObjects que utilice un delimitador de mundo determinado.</span><span class="sxs-lookup"><span data-stu-id="2d825-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="2d825-112">A menudo tiene sentido crear una raíz de GameObject con un anclaje del mundo y tener elementos secundarios hologramas delimitadas por él con un desplazamiento de posición local.</span><span class="sxs-lookup"><span data-stu-id="2d825-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="2d825-113">Para cargar hologramas de sesiones anteriores:</span><span class="sxs-lookup"><span data-stu-id="2d825-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="2d825-114">Obtener el WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="2d825-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="2d825-115">Cargar datos relacionados con el delimitador del mundo que proporciona el identificador del delimitador en el mundo de la aplicación</span><span class="sxs-lookup"><span data-stu-id="2d825-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="2d825-116">Cargar un anclaje del mundo desde su Id.</span><span class="sxs-lookup"><span data-stu-id="2d825-116">Load a world anchor from its id</span></span>

<span data-ttu-id="2d825-117">Para guardar hologramas para sesiones futuras:</span><span class="sxs-lookup"><span data-stu-id="2d825-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="2d825-118">Obtener el WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="2d825-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="2d825-119">Guardar un anclaje del mundo especificando un identificador</span><span class="sxs-lookup"><span data-stu-id="2d825-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="2d825-120">Guardar datos relacionados con el delimitador del mundo junto con un identificador de la aplicación</span><span class="sxs-lookup"><span data-stu-id="2d825-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="2d825-121">Introducción a la WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="2d825-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="2d825-122">Queremos mantener una referencia a la WorldAnchorStore en torno a por lo que sabemos que estamos preparados ir cuando desea realizar una operación.</span><span class="sxs-lookup"><span data-stu-id="2d825-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="2d825-123">Puesto que es una llamada asincrónica, potencialmente tan pronto como inicio, que queremos llamar</span><span class="sxs-lookup"><span data-stu-id="2d825-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="2d825-124">En este caso, StoreLoaded es nuestro controlador para cuando haya terminado de cargarse el WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="2d825-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="2d825-125">Ahora tenemos una referencia a la WorldAnchorStore que usaremos para guardar y cargar los delimitadores de mundo específico.</span><span class="sxs-lookup"><span data-stu-id="2d825-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="2d825-126">Guardar un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="2d825-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="2d825-127">Para guardar, simplemente tenemos lo que se va a guardar y pasarlo en el WorldAnchor obtuvimos antes cuando desea guardar el nombre.</span><span class="sxs-lookup"><span data-stu-id="2d825-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="2d825-128">Nota: al intentar guardar dos anclajes en la misma cadena se producirá un error (almacén. Guardar se devolverá false).</span><span class="sxs-lookup"><span data-stu-id="2d825-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="2d825-129">Es preciso eliminar el anterior guardar antes de guardar una nueva:</span><span class="sxs-lookup"><span data-stu-id="2d825-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="2d825-130">Cargar un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="2d825-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="2d825-131">Y para cargar:</span><span class="sxs-lookup"><span data-stu-id="2d825-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="2d825-132">Además, podemos usar almacén. Delete() para quitar un delimitador que se guardó anteriormente y el almacén. Clear() para quitar todos los datos previamente guardados.</span><span class="sxs-lookup"><span data-stu-id="2d825-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="2d825-133">Enumerar los anclajes de existentes</span><span class="sxs-lookup"><span data-stu-id="2d825-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="2d825-134">Para descubrir los delimitadores almacenados previamente, llame a GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="2d825-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="2d825-135">Conservar hologramas para varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="2d825-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="2d825-136">Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para crear un anclaje en la nube duraderas desde un WorldAnchor local, lo que la aplicación, a continuación, puede ubicar a través de varios HoloLens, dispositivos iOS y Android, incluso si esos dispositivos no están presentes en el mismo hora.</span><span class="sxs-lookup"><span data-stu-id="2d825-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="2d825-137">Dado que los anclajes en la nube son persistentes, varios dispositivos con el tiempo pueden cada ver contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="2d825-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="2d825-138">Para empezar a crear experiencias compartidas en Unity, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guías de inicio rápido de Azure espacial delimitadores Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="2d825-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2d825-139">Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y localizar los anclajes en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="2d825-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d825-140">Vea también</span><span class="sxs-lookup"><span data-stu-id="2d825-140">See Also</span></span>
* [<span data-ttu-id="2d825-141">Persistencia de anclaje espacial</span><span class="sxs-lookup"><span data-stu-id="2d825-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="2d825-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure delimitadores espaciales</a></span><span class="sxs-lookup"><span data-stu-id="2d825-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2d825-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Delimitadores espaciales Azure SDK para Unity</a></span><span class="sxs-lookup"><span data-stu-id="2d825-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
