---
title: Anclajes espaciales en Unreal
description: Guía para el uso de anclajes espaciales en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors
ms.openlocfilehash: 1100704cae40de1997eb869bfc6c82bba3d0dc6e
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428733"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="bae8c-104">Anclajes espaciales en Unreal</span><span class="sxs-lookup"><span data-stu-id="bae8c-104">Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="bae8c-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="bae8c-105">Overview</span></span>

<span data-ttu-id="bae8c-106">Los anclajes espaciales se usan para guardar los hologramas en el espacio del mundo real entre sesiones de aplicación.</span><span class="sxs-lookup"><span data-stu-id="bae8c-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="bae8c-107">Aparecen mediante Unreal en forma de elementos **ARPin** y se guardan en el almacén de anclajes de HoloLens, que se carga en futuras sesiones.</span><span class="sxs-lookup"><span data-stu-id="bae8c-107">These get surfaced through Unreal as **ARPin**s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> 

## <a name="checking-the-anchor-store"></a><span data-ttu-id="bae8c-108">Comprobación del almacén de anclajes</span><span class="sxs-lookup"><span data-stu-id="bae8c-108">Checking the anchor store</span></span>

<span data-ttu-id="bae8c-109">Antes de guardar o cargar anclajes, debe comprobar si el almacén de anclajes está listo.</span><span class="sxs-lookup"><span data-stu-id="bae8c-109">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="bae8c-110">Si se llama a cualquiera de las funciones de anclaje de HoloLens antes de que el almacén de anclajes esté listo, la llamada no se completará correctamente.</span><span class="sxs-lookup"><span data-stu-id="bae8c-110">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Almacén de anclajes espaciales listo](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="bae8c-112">Guardar anclajes</span><span class="sxs-lookup"><span data-stu-id="bae8c-112">Saving anchors</span></span>

<span data-ttu-id="bae8c-113">Cuando la aplicación tenga un componente que se necesite anclar en el mundo, se puede guardar en el almacén de anclajes con la siguiente secuencia:</span><span class="sxs-lookup"><span data-stu-id="bae8c-113">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Guardar anclaje espacial](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="bae8c-115">Desglose:</span><span class="sxs-lookup"><span data-stu-id="bae8c-115">Breaking this down:</span></span>
1. <span data-ttu-id="bae8c-116">Genere un actor en una ubicación conocida.</span><span class="sxs-lookup"><span data-stu-id="bae8c-116">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="bae8c-117">Cree un elemento **ARPin** con esa ubicación y un nombre basado en la clase del actor.</span><span class="sxs-lookup"><span data-stu-id="bae8c-117">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="bae8c-118">Agregue el actor al elemento **ARPin** y guarde el marcador en el almacén de anclajes de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bae8c-118">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="bae8c-119">El nombre del anclaje que elija debe ser único, en este ejemplo, es la marca de tiempo actual.</span><span class="sxs-lookup"><span data-stu-id="bae8c-119">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="bae8c-120">Si el anclaje se guarda correctamente en el almacén de anclajes, se puede inspeccionar en el portal de dispositivos de HoloLens en **System > Map manager > Anchor Files Saved On Device** (Sistema > Administrador de mapas > Archivos de anclajes guardados en el dispositivo).</span><span class="sxs-lookup"><span data-stu-id="bae8c-120">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="bae8c-121">Carga de anclajes</span><span class="sxs-lookup"><span data-stu-id="bae8c-121">Loading anchors</span></span>

<span data-ttu-id="bae8c-122">Cuando se inicia una aplicación, se puede usar el siguiente plano técnico para restaurar los componentes en sus ubicaciones de anclaje:</span><span class="sxs-lookup"><span data-stu-id="bae8c-122">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Carga de anclajes espaciales](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="bae8c-124">Desglose:</span><span class="sxs-lookup"><span data-stu-id="bae8c-124">Breaking this down:</span></span>
1. <span data-ttu-id="bae8c-125">Recorra en iteración todos los anclajes del almacén de anclajes.</span><span class="sxs-lookup"><span data-stu-id="bae8c-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="bae8c-126">Genere un actor en la identidad.</span><span class="sxs-lookup"><span data-stu-id="bae8c-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="bae8c-127">Marque ese actor en **ARPin** en el almacén de anclajes.</span><span class="sxs-lookup"><span data-stu-id="bae8c-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="bae8c-128">Es importante generar el actor en la identidad, ya que el anclaje es responsable de cambiar la posición del holograma en el mundo en función de dónde se guardó.</span><span class="sxs-lookup"><span data-stu-id="bae8c-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="bae8c-129">Cualquier transformación que se proporcione aquí agregará un desplazamiento al anclaje.</span><span class="sxs-lookup"><span data-stu-id="bae8c-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="bae8c-130">También se consulta el identificador del anclaje para que se puedan generar diferentes actores en función del nombre guardado del anclaje.</span><span class="sxs-lookup"><span data-stu-id="bae8c-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="bae8c-131">Eliminación de anclajes</span><span class="sxs-lookup"><span data-stu-id="bae8c-131">Removing anchors</span></span> 

<span data-ttu-id="bae8c-132">Cuando haya terminado con un anclaje, puede borrar delimitadores individuales o todo el almacén de anclajes con los componentes **Remove ARPin from WMRAnchor Store** (Quitar ARPin del almacén WMRAnchor) y **Remove All ARPins from WMRAnchor Store** (Quitar todos los ARPin del almacén WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="bae8c-132">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Quitar anclajes espaciales](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="bae8c-134">Tenga en cuenta que Spatial Anchors todavía están en versión beta, por lo que debe asegurarse de consultar la información y las características actualizadas.</span><span class="sxs-lookup"><span data-stu-id="bae8c-134">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="see-also"></a><span data-ttu-id="bae8c-135">Consulta también</span><span class="sxs-lookup"><span data-stu-id="bae8c-135">See also</span></span>
* [<span data-ttu-id="bae8c-136">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="bae8c-136">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="bae8c-137">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="bae8c-137">Coordinate systems</span></span>](coordinate-systems.md)
