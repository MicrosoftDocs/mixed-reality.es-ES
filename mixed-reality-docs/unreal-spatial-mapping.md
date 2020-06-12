---
title: Mapeo espacial en Unreal
description: Guía para el uso del mapeo espacial en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: 2bbfc3972acdb9dc7d5ebd23c85ab0ef5532cfb9
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428774"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="03188-104">Mapeo espacial en Unreal</span><span class="sxs-lookup"><span data-stu-id="03188-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="03188-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="03188-105">Overview</span></span>
<span data-ttu-id="03188-106">El mapeo espacial permite colocar objetos sobre superficies del mundo físico mediante la visualización del mundo de alrededor de HoloLens, lo que hace que los hologramas parezcan más reales al usuario.</span><span class="sxs-lookup"><span data-stu-id="03188-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="03188-107">El mapeo espacial también ancla objetos en el mundo del usuario aprovechando las indicaciones detalladas del mundo real. Con ello, se ayuda a convencer al usuario de que estos hologramas están realmente en su espacio; los hologramas que flotan en el espacio o se mueven con el usuario no se verán como reales.</span><span class="sxs-lookup"><span data-stu-id="03188-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="03188-108">Es aconsejable colocar elementos para mayor confort, siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="03188-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="03188-109">Puede encontrar más información sobre la calidad del mapeo espacial, la ubicación, la oclusión, la representación, etc., en el documento [Asignación espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="03188-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="03188-110">Habilitación del mapeo espacial</span><span class="sxs-lookup"><span data-stu-id="03188-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="03188-111">Para habilitar el mapeo espacial en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="03188-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="03188-112">Abra **Editar > Configuración del proyecto** y desplácese hacia abajo hasta la sección **Plataformas**.</span><span class="sxs-lookup"><span data-stu-id="03188-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="03188-113">Seleccione **HoloLens** y marque **Percepción espacial**.</span><span class="sxs-lookup"><span data-stu-id="03188-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="03188-114">Para participar en el mapeo espacial y depurar **MRMesh** en un juego HoloLens:</span><span class="sxs-lookup"><span data-stu-id="03188-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="03188-115">Abra **ARSessionConfig** y expanda la sección **ARSettings > World Mapping (Mapeo del mundo)** .</span><span class="sxs-lookup"><span data-stu-id="03188-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="03188-116">Active **Generate Mesh Data from Tracked Geometry** (Generar datos de malla a partir de la geometría de seguimiento), que indica al complemento de HoloLens que empiece a obtener los datos de mapeo espacial de forma asincrónica y los exponga en Unreal a través de **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="03188-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="03188-117">Marque **Render Mesh Data in Wireframe (Representar datos de malla en contorno reticular)** para mostrar un contorno reticular blanco de cada triángulo de **MRMesh**.</span><span class="sxs-lookup"><span data-stu-id="03188-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Almacén de anclajes espaciales listo](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="03188-119">Mapeo espacial en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="03188-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="03188-120">Puede modificar los parámetros siguientes para actualizar el comportamiento en tiempo de ejecución del mapeo espacial:</span><span class="sxs-lookup"><span data-stu-id="03188-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="03188-121">Abra **Editar > Configuración del proyecto**, desplácese hacia abajo hasta la sección **Plataformas** y seleccione **HoloLens > Spatial Mapping (Mapeo espacial)** :</span><span class="sxs-lookup"><span data-stu-id="03188-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Configuración del proyecto de anclajes espaciales](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="03188-123">**Max Triangles Per Cubic Meter** (Máximo de triángulos por metro cúbico) actualice la densidad de los triángulos en la malla de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="03188-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="03188-124">**Spatial Meshing Volume Size** (Tamaño del volumen de la malla espacial) es el tamaño del cubo alrededor del jugador para representar y actualizar los datos de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="03188-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="03188-125">Si se espera que el entorno en tiempo de ejecución de la aplicación sea elevado, es posible que este valor tenga que ser grande para que coincida con el espacio del mundo real.</span><span class="sxs-lookup"><span data-stu-id="03188-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="03188-126">Por otro lado, este valor puede ser menor si la aplicación solo necesita colocar hologramas en superficies inmediatamente alrededor del usuario.</span><span class="sxs-lookup"><span data-stu-id="03188-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="03188-127">A medida que el usuario se desplaza por el mundo, el volumen de mapeo espacial se moverá con él.</span><span class="sxs-lookup"><span data-stu-id="03188-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="03188-128">Utilización de MRMesh</span><span class="sxs-lookup"><span data-stu-id="03188-128">Working with MRMesh</span></span>
<span data-ttu-id="03188-129">Para obtener acceso a **MRMesh** en tiempo de ejecución:</span><span class="sxs-lookup"><span data-stu-id="03188-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="03188-130">Agregue un componente **ARTrackableNotify** a un actor de Blueprint.</span><span class="sxs-lookup"><span data-stu-id="03188-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Notificaciones supervisadas de AR de anclajes espaciales](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="03188-132">Seleccione el componente **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**.</span><span class="sxs-lookup"><span data-stu-id="03188-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="03188-133">Haga clic en el botón **+** en los eventos que quiera supervisar.</span><span class="sxs-lookup"><span data-stu-id="03188-133">Click the **+** button on the events you want to monitor.</span></span> 

![Eventos de Spatial Anchors](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="03188-135">En este caso, se supervisa el evento **On Add Tracked Geometry** (Al agregar geometría de seguimiento), que busca mallas del mundo válidas que coincidan con los datos de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="03188-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="03188-136">Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="03188-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="03188-137">Puede cambiar el material de la malla en el gráfico de eventos de Blueprint o en C++.</span><span class="sxs-lookup"><span data-stu-id="03188-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="03188-138">En la captura de pantalla siguiente se muestra la ruta de Blueprint:</span><span class="sxs-lookup"><span data-stu-id="03188-138">The screenshot below shows the Blueprint route:</span></span> 

![Ejemplo de anclajes espaciales](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="03188-140">En C++, puede suscribirse al delegado `OnTrackableAdded` para obtener el elemento `ARTrackedGeometry` en cuanto esté disponible, como se muestra en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="03188-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="03188-141">El archivo build.cs del proyecto **debe** contener **AugmentedReality** en la lista **PublicDependencyModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="03188-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="03188-142">Esto incluye **ARBlueprintLibrary.h** y **MRMeshComponent.h**, que permite inspeccionar el componente **MRMesh** de **UARTrackedGeometry**.</span><span class="sxs-lookup"><span data-stu-id="03188-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![Código C++ de ejemplo de anclajes espaciales](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="03188-144">El mapeo espacial no es el único tipo de datos que se muestra a través de **ARTrackedGeometries**.</span><span class="sxs-lookup"><span data-stu-id="03188-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="03188-145">Puede comprobar que `EARObjectClassification` es `World`, lo que significa que se trata de una geometría de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="03188-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="03188-146">Hay delegados similares para eventos actualizados y quitados:</span><span class="sxs-lookup"><span data-stu-id="03188-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="03188-147">`AddOnTrackableRemovedDelegate_Handle`.</span><span class="sxs-lookup"><span data-stu-id="03188-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="03188-148">Puede encontrar la lista completa de eventos en la API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="03188-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="03188-149">Consulta también</span><span class="sxs-lookup"><span data-stu-id="03188-149">See also</span></span>
* [<span data-ttu-id="03188-150">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="03188-150">Spatial mapping</span></span>](spatial-mapping.md)
