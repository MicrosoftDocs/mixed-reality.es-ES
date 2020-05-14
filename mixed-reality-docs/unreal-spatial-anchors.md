---
title: Anclajes espaciales en Unreal
description: Guía para el uso de anclajes espaciales en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840144"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="b7b7c-104">Anclajes espaciales en Unreal</span><span class="sxs-lookup"><span data-stu-id="b7b7c-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="b7b7c-105">Los anclajes espaciales se usan para conservar los hologramas en el espacio del mundo real entre sesiones de aplicación.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="b7b7c-106">Aparecen mediante Unreal en forma de elementos ARPin y se guardan en el almacén de anclajes de HoloLens para cargarse en futuras sesiones.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="b7b7c-107">Antes de guardar o cargar anclajes, comprueba que el almacén de anclajes está listo.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="b7b7c-108">Si intentas llamar a cualquiera de las funciones de anclaje de HoloLens antes de que el almacén de anclajes esté listo, la llamada no se completará correctamente.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Almacén de anclajes espaciales listo](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="b7b7c-110">Guardar anclajes</span><span class="sxs-lookup"><span data-stu-id="b7b7c-110">Save Anchors</span></span>

<span data-ttu-id="b7b7c-111">Cuando la aplicación tenga un componente que se necesite anclar en el mundo, se puede guardar en el almacén de anclajes con la siguiente secuencia:</span><span class="sxs-lookup"><span data-stu-id="b7b7c-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Guardar anclaje espacial](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="b7b7c-113">En este caso, vamos a generar un actor en una ubicación conocida. Para hacerlo, crearemos un elemento ARPin con esa ubicación y un nombre basado en la clase del actor, agregaremos el actor al elemento ARPin y guardaremos la marca en el almacén de anclajes de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="b7b7c-114">El nombre del anclaje que elijamos debe ser único, por lo que, en este ejemplo, hemos anexado la marca de tiempo actual.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="b7b7c-115">Si el anclaje se guarda correctamente en el almacén de anclajes, se puede inspeccionar en el portal de dispositivos de HoloLens en System > Map manager > Anchor Files Saved On Device (Sistema > Administrador de mapas > Archivos de anclaje guardados en el dispositivo).</span><span class="sxs-lookup"><span data-stu-id="b7b7c-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="b7b7c-116">Cargar anclajes</span><span class="sxs-lookup"><span data-stu-id="b7b7c-116">Load Anchors</span></span>

<span data-ttu-id="b7b7c-117">Cuando se inicia una aplicación, se puede llamar al siguiente plano técnico para restaurar los componentes en sus ubicaciones de anclaje:</span><span class="sxs-lookup"><span data-stu-id="b7b7c-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![Carga de anclajes espaciales](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="b7b7c-119">En este ejemplo, se recorren en iteración todos los anclajes del almacén, se genera un actor en la identidad y se ancla ese actor al elemento ARPin del almacén.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="b7b7c-120">Es importante generar el actor en la identidad, ya que el anclaje es responsable de cambiar la posición del holograma en el mundo en función de dónde se guardó, de modo que cualquier transformación que se proporcione aquí agregará un desplazamiento al anclaje.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="b7b7c-121">También se consulta el identificador del anclaje para que se puedan generar diferentes actores en función del nombre guardado del anclaje.</span><span class="sxs-lookup"><span data-stu-id="b7b7c-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="b7b7c-122">Quitar anclajes</span><span class="sxs-lookup"><span data-stu-id="b7b7c-122">Remove Anchors</span></span> 

<span data-ttu-id="b7b7c-123">Cuando acabe con un anclaje, se puede borrar todo el almacén de anclajes o bien se pueden quitar anclajes individuales del almacén para que no se incluyan en sesiones futuras:</span><span class="sxs-lookup"><span data-stu-id="b7b7c-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![Quitar anclajes espaciales](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="b7b7c-125">Consulta también</span><span class="sxs-lookup"><span data-stu-id="b7b7c-125">See also</span></span>
* [<span data-ttu-id="b7b7c-126">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="b7b7c-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="b7b7c-127">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="b7b7c-127">Coordinate systems</span></span>](coordinate-systems.md)
