---
title: Mapeo espacial en Unreal
description: Guía para el uso del mapeo espacial en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840084"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="3b1ab-104">Mapeo espacial en Unreal</span><span class="sxs-lookup"><span data-stu-id="3b1ab-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="3b1ab-105">Para habilitar el mapeo espacial en HoloLens, comprueba que la funcionalidad “Spatial Perception” (Percepción espacial) esté activada en el editor de Unreal en Project Settings > Platform > HoloLens > Capabilities (Configuración del proyecto > Plataforma > HoloLens > Funcionalidades).</span><span class="sxs-lookup"><span data-stu-id="3b1ab-105">To enable spatial mapping on HoloLens, ensure that the “Spatial Perception” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="3b1ab-106">Para optar por recibir el uso de mapeo espacial en un juego de HoloLens, habilita “Generate Mesh Data from Tracked Geometry” (Generar datos de malla a partir de la geometría del seguimiento) en ARSessionConfig.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-106">To opt into using spatial mapping in a HoloLens game, enable the “Generate Mesh Data from Tracked Geometry” in the ARSessionConfig.</span></span>  <span data-ttu-id="3b1ab-107">A continuación, el complemento de HoloLens recibirá de forma asincrónica los datos de mapeo espacial y los mostrará en Unreal mediante MRMesh.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-107">The HoloLens plugin will then asynchronously get spatial mapping data and surface it to Unreal through the MRMesh.</span></span> 

![Almacén de anclajes espaciales listo](images/unreal-spatialmapping-arsettings.PNG)

<span data-ttu-id="3b1ab-109">Para ver una visualización de depuración de la malla de mapeo espacial, habilita la casilla "Render Mesh Data in Wireframe" (Representar los datos de malla en trama de alambres) para ver un contorno de alambres en blanco de cada triángulo de MRMesh.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-109">To see a debug visualization of the spatial mapping mesh, enable the “Render Mesh Data in Wireframe” checkbox in the ARSessionConfig to see a white wireframe outline of every triangle in the MRMesh.</span></span> 

<span data-ttu-id="3b1ab-110">En Project Settings > Platform > HoloLens > Spatial Mapping (Configuración de proyectos > Plataforma > HoloLens > Mapeo espacial), se pueden modificar los parámetros siguientes para actualizar el comportamiento en tiempo de ejecución de el mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-110">In Project Settings > Platform > HoloLens > Spatial Mapping, the following parameters can be modified to update spatial mapping’s runtime behavior:</span></span> 

![Configuración del proyecto de anclajes espaciales](images/unreal-spatialmapping-projectsettings.PNG)

<span data-ttu-id="3b1ab-112">Max Triangles Per Cubic Meter (Máximo de triángulos por metro cúbico) actualizará la densidad de los triángulos en la malla de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-112">Max Triangles Per Cubic Meter will update the density of the triangles in the spatial mapping mesh.</span></span>  <span data-ttu-id="3b1ab-113">Spatial Meshing Volume Size (Tamaño del volumen de la malla espacial) indica el tamaño del cubo alrededor del juego para representar y actualizar los datos de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-113">Spatial Meshing Volume Size indicates the size of the cube around the player to render and update spatial mapping data.</span></span>  <span data-ttu-id="3b1ab-114">Si se espera que el entorno en tiempo de ejecución de la aplicación sea elevado, es posible que este campo tenga que ser grande para que coincida con el espacio del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-114">If the expected application runtime environment is expected to be large, this field may need to be large to match the real-world space.</span></span>  <span data-ttu-id="3b1ab-115">Por el contrario, si la aplicación solo necesita colocar hologramas en superficies inmediatamente alrededor del usuario, este campo puede ser más pequeño.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-115">Conversely, if the application only needs to place holograms on surfaces immediately around the user, this field can be smaller.</span></span>  <span data-ttu-id="3b1ab-116">A medida que el usuario se desplaza por el mundo, el volumen de mapeo espacial se moverá con él.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-116">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

<span data-ttu-id="3b1ab-117">Para obtener acceso a MRMesh en tiempo de ejecución, agrega primero un componente de notificación supervisable de AR a un actor de plano técnico:</span><span class="sxs-lookup"><span data-stu-id="3b1ab-117">To get access to the MRMesh at runtime, first add an AR Trackable Notify Component to a Blueprint actor:</span></span> 

![Notificaciones supervisadas de AR de anclajes espaciales](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="3b1ab-119">A continuación, ve a los detalles del componente y haz clic en el botón verde "+" de los eventos que se van a supervisar.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-119">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span> 

![Eventos de Spatial Anchors](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="3b1ab-121">En este caso, supervisamos el evento On Add Tracked Geometry (Al agregar geometría con seguimiento) en busca de mallas del mundo válidas que se correspondan con los datos de mapeo espacial y se cambia el material de la malla:</span><span class="sxs-lookup"><span data-stu-id="3b1ab-121">In this case we monitor the On Add Tracked Geometry event looking for valid world meshes which correspond to spatial mapping data, and change the mesh’s material:</span></span> 

![Ejemplo de anclajes espaciales](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="3b1ab-123">En C++, se puede suscribir al delegado OnTrackableAdded para obtener ARTrackedGeometry en cuanto esté disponible.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-123">In C++, we can subscribe to the OnTrackableAdded delegate to get the ARTrackedGeometry as soon as it is available.</span></span>  <span data-ttu-id="3b1ab-124">Hay delegados similares para eventos actualizados y quitados: AddOnTrackableUpdatedDelegate_Handle y AddOnTrackableRemovedDelegate_Handle.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-124">There are similar delegates for updated and removed events: AddOnTrackableUpdatedDelegate_Handle and AddOnTrackableRemovedDelegate_Handle.</span></span> 

![Código C++ de ejemplo de anclajes espaciales](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="3b1ab-126">El elemento build.cs del proyecto debe tener "AugmentedReality" en la lista PublicDependencyModuleNames para incluir “ARBlueprintLibrary.h” y “MRMesh” para inspeccionar el componente MRMesh de UARTrackedGeometry.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-126">The project’s build.cs must have “AugmentedReality” in the PublicDependencyModuleNames list to include “ARBlueprintLibrary.h” and “MRMesh” to inspect the MRMesh component of the UARTrackedGeometry.</span></span> 

<span data-ttu-id="3b1ab-127">El mapeo espacial no es el único tipo de datos que se muestra mediante ARTrackedGeometries, por lo que primero comprobamos que el valor de EARObjectClassification es World (Mundo), lo que indica que se trata de una geometría de mapeo espacial.</span><span class="sxs-lookup"><span data-stu-id="3b1ab-127">Spatial mapping is not the only type of data that gets surfaced through ARTrackedGeometries, so we first check that the EARObjectClassification is World, which indicates that this is spatial mapping geometry.</span></span> 

## <a name="see-also"></a><span data-ttu-id="3b1ab-128">Consulta también</span><span class="sxs-lookup"><span data-stu-id="3b1ab-128">See also</span></span>
* [<span data-ttu-id="3b1ab-129">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="3b1ab-129">Spatial mapping</span></span>](spatial-mapping.md)
