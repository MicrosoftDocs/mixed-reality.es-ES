---
title: Asignación espacial en Unity
description: Representación y chocar con la geometría del mundo real que le rodea en Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, asignación espacial, representador, colisionador, malla, el análisis, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148649"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="be82b-104">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="be82b-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="be82b-105">Este tema describe cómo usar [asignación espacial](spatial-mapping.md) en el proyecto de Unity, recuperar las mallas de triangulares que representan las superficies del mundo en torno a un dispositivo HoloLens, para la colocación, oclusión, análisis de la sala y mucho más.</span><span class="sxs-lookup"><span data-stu-id="be82b-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="be82b-106">Unity es totalmente compatible con la asignación espacial, que se expone a los desarrolladores de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="be82b-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="be82b-107">Asignación de componentes disponibles en el MixedRealityToolkit espaciales, que proporcionan una ruta cómoda y rápida para comenzar con la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="be82b-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="be82b-108">Asignación espacial de nivel inferior API, que proporcionan un completo control y permiten la personalización específica de aplicación más sofisticada</span><span class="sxs-lookup"><span data-stu-id="be82b-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="be82b-109">Para usar asignación espacial en la aplicación, la capacidad de spatialPerception debe establecerse en su AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="be82b-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="be82b-110">Establecer la capacidad de SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="be82b-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="be82b-111">En el orden de una aplicación consumir datos de asignación espacial, debe habilitarse la capacidad de SpatialPerception.</span><span class="sxs-lookup"><span data-stu-id="be82b-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="be82b-112">Cómo habilitar la funcionalidad de SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="be82b-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="be82b-113">En el Editor de Unity, abra el **"Configuración del Reproductor"** panel (Editar > configuración del proyecto > Reproductor)</span><span class="sxs-lookup"><span data-stu-id="be82b-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="be82b-114">Haga clic en el **"Windows Store"** ficha</span><span class="sxs-lookup"><span data-stu-id="be82b-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="be82b-115">Expanda **"Configuración de publicación"** y compruebe el **"SpatialPerception"** capacidad en el **"Capacidades"** lista</span><span class="sxs-lookup"><span data-stu-id="be82b-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="be82b-116">Tenga en cuenta que si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o manualmente [establecer esta funcionalidad en el AppxManifest en Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="be82b-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="be82b-117">Asignación espacial también requiere un MaxVersionTested de al menos 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="be82b-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="be82b-118">En Visual Studio, haga clic en **Package.appxmanifest** en el Explorador de soluciones y seleccione **ver código**</span><span class="sxs-lookup"><span data-stu-id="be82b-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="be82b-119">Busque la línea especifica **TargetDeviceFamily** y cambiar **MaxVersionTested = "10.0.10240.0"** a **MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="be82b-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="be82b-120">**Guardar** Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="be82b-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="be82b-121">Introducción a los componentes de asignación espacial integradas de Unity</span><span class="sxs-lookup"><span data-stu-id="be82b-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="be82b-122">Unity ofrece 2 componentes para agregar fácilmente la asignación espacial a su aplicación, **representador de asignación espacial** y **espacial Colisionador asignación**.</span><span class="sxs-lookup"><span data-stu-id="be82b-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="be82b-123">Representador de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="be82b-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="be82b-124">El representador de asignación espacial permite la visualización de la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="be82b-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Asignación espacial representador en Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="be82b-126">Asignación espacial Colisionador</span><span class="sxs-lookup"><span data-stu-id="be82b-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="be82b-127">Permite el Colisionador asignación espacial holográfica contenido (o carácter) interacción, como física, con la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="be82b-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Asignación espacial Colisionador en Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="be82b-129">Con los componentes integrados asignación espacial</span><span class="sxs-lookup"><span data-stu-id="be82b-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="be82b-130">Puede agregar ambos componentes a la aplicación si desea que tanto visualizar e interactuar con las superficies físico.</span><span class="sxs-lookup"><span data-stu-id="be82b-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="be82b-131">Para usar estos dos componentes en la aplicación de Unity:</span><span class="sxs-lookup"><span data-stu-id="be82b-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="be82b-132">Seleccione un GameObject en el centro del área en la que le gustaría detectar las mallas de superficie espaciales.</span><span class="sxs-lookup"><span data-stu-id="be82b-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="be82b-133">En la ventana del Inspector, **Agregar componente** > **XR** > **Colisionador asignación espacial** o **espacial Representador de asignación**.</span><span class="sxs-lookup"><span data-stu-id="be82b-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="be82b-134">Puede encontrar más detalles sobre cómo usar estos componentes en el <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">sitio de documentación de Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="be82b-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="be82b-135">Ir más allá de los componentes integrados asignación espacial</span><span class="sxs-lookup"><span data-stu-id="be82b-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="be82b-136">Estos componentes facilitan arrastrar y colocar fácil empezar a trabajar con la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="be82b-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="be82b-137"> Cuando desea ir más allá, hay dos formas de explorar:</span><span class="sxs-lookup"><span data-stu-id="be82b-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="be82b-138">Para realizar el procesamiento de la malla de nivel inferior, vea la sección siguiente sobre el script de bajo nivel de asignación espacial API.</span><span class="sxs-lookup"><span data-stu-id="be82b-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="be82b-139">Para realizar análisis de malla de nivel superior, consulte la sección acerca de la biblioteca SpatialUnderstanding en <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="be82b-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="be82b-140">Utilizando el Unity espacial asignación de API de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="be82b-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="be82b-141">Si necesita más control que obtendrá de los componentes de representador asignación espacial y Colisionador asignación espacial, puede usar el script de asignación espacial bajo nivel API.</span><span class="sxs-lookup"><span data-stu-id="be82b-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="be82b-142">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="be82b-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="be82b-143">**Tipos**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="be82b-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="be82b-144">El siguiente es un esquema del flujo sugerido para una aplicación que utiliza la API de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="be82b-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="be82b-145">Configurar la SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="be82b-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="be82b-146">Crear una instancia de un objeto SurfaceObserver para cada región definida por la aplicación de espacio que necesita datos de asignación espacial para.</span><span class="sxs-lookup"><span data-stu-id="be82b-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="be82b-147">Especificar la región del espacio que cada objeto SurfaceObserver proporcionará datos para llamar al método SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="be82b-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="be82b-148">Basta con volver a llamar a uno de estos métodos puede volver a definir la región de espacio en el futuro.</span><span class="sxs-lookup"><span data-stu-id="be82b-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="be82b-149">Cuando se llama a SurfaceObserver.Update(), debe proporcionar un controlador para cada superficie espacial en región del SurfaceObserver de espacio que el sistema de asignación espacial tiene nueva información de.</span><span class="sxs-lookup"><span data-stu-id="be82b-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="be82b-150">El controlador recibe de una superficie espacial:</span><span class="sxs-lookup"><span data-stu-id="be82b-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="be82b-151">Control de cambios superficiales</span><span class="sxs-lookup"><span data-stu-id="be82b-151">Handling Surface Changes</span></span>

<span data-ttu-id="be82b-152">Hay varios casos principales para controlar.</span><span class="sxs-lookup"><span data-stu-id="be82b-152">There are several main cases to handle.</span></span> <span data-ttu-id="be82b-153">Agregar & actualizado que puede usar la misma ruta de acceso y se eliminan de código.</span><span class="sxs-lookup"><span data-stu-id="be82b-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="be82b-154">En los casos Added & actualizado en el ejemplo, se agrega u obtener el GameObject que representa esto de malla del diccionario, creación de un struct SurfaceData con los componentes necesarios y luego llamar a RequestMeshDataAsync para rellenar el GameObject con los datos de la malla y posición en la escena.</span><span class="sxs-lookup"><span data-stu-id="be82b-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="be82b-155">En el caso de quitado, se quita el GameObject que representa esta malla del diccionario y destruirlo.</span><span class="sxs-lookup"><span data-stu-id="be82b-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="be82b-156">Listas de control de datos</span><span class="sxs-lookup"><span data-stu-id="be82b-156">Handling Data Ready</span></span>

<span data-ttu-id="be82b-157">El controlador de OnDataReady recibe un objeto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="be82b-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="be82b-158">El WorldAnchor, MeshFilter y (opcionalmente) MeshCollider objetos que contiene reflejan el estado más reciente de la superficie espacial asociado.</span><span class="sxs-lookup"><span data-stu-id="be82b-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="be82b-159">Opcionalmente, realizar análisis o [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla mediante el acceso a los miembros de malla del objeto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="be82b-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="be82b-160">Representar la superficie espacial con la malla más reciente y (opcionalmente) se utiliza para conflictos de leyes físicas y raycasts.</span><span class="sxs-lookup"><span data-stu-id="be82b-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="be82b-161">Es importante confirmar que el contenido de la SurfaceData no es null.</span><span class="sxs-lookup"><span data-stu-id="be82b-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="be82b-162">Iniciar el procesamiento de las actualizaciones</span><span class="sxs-lookup"><span data-stu-id="be82b-162">Start processing on updates</span></span>

<span data-ttu-id="be82b-163">SurfaceObserver.Update() debe llamarse en un retraso, no en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="be82b-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="be82b-164">Análisis de la malla de nivel superior: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="be82b-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="be82b-165">El <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> es una colección de código de la utilidad de ayuda para el desarrollo holográfico basado las API de Unity holográfica.</span><span class="sxs-lookup"><span data-stu-id="be82b-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="be82b-166">Understanding espacial</span><span class="sxs-lookup"><span data-stu-id="be82b-166">Spatial Understanding</span></span>

<span data-ttu-id="be82b-167">Al colocar hologramas en el mundo físico suele ser deseable para ir más allá de la asignación espacial de la malla y planos de la superficie.</span><span class="sxs-lookup"><span data-stu-id="be82b-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="be82b-168">Cuando la selección de ubicación se realiza mediante procedimientos, es deseable un mayor nivel de comprensión del entorno.</span><span class="sxs-lookup"><span data-stu-id="be82b-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="be82b-169">Esto requiere generalmente tomar decisiones sobre las novedades de las paredes, ceiling y floor.</span><span class="sxs-lookup"><span data-stu-id="be82b-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="be82b-170">Además, la capacidad de optimizar con un conjunto de restricciones de colocación para determinar las ubicaciones físicas más conveniente para los objetos holográficas.</span><span class="sxs-lookup"><span data-stu-id="be82b-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="be82b-171">Durante el desarrollo de fragmentos y Conker Young, Asobo Studios que afrontar este problema sin rodeos, desarrollo de un solucionador de espacio para este propósito.</span><span class="sxs-lookup"><span data-stu-id="be82b-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="be82b-172">Cada uno de estos juegos tenía juego necesidades específicas, pero comparten core espacial descripción de la tecnología.</span><span class="sxs-lookup"><span data-stu-id="be82b-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="be82b-173">Coloca el HoloToolkit.SpatialUnderstanding biblioteca encapsula esta tecnología, lo que permite que a rápidamente buscar espacios en blanco en las paredes, los objetos de contexto en el techo, identificar para carácter estar sentado y un sinnúmero de otras consultas espaciales descripción.</span><span class="sxs-lookup"><span data-stu-id="be82b-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="be82b-174">Todo el código fuente se incluye, lo que permite personalizar según sus necesidades y compartir sus mejoras con la Comunidad.</span><span class="sxs-lookup"><span data-stu-id="be82b-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="be82b-175">El código para el C++ solver se ha ajustado en un archivo dll UWP y expuestos a Unity con una disminución en el prefabricado verá dentro de la MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="be82b-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="be82b-176">Módulos de descripción</span><span class="sxs-lookup"><span data-stu-id="be82b-176">Understanding Modules</span></span>

<span data-ttu-id="be82b-177">Hay tres interfaces principales expuestas por el módulo: topología de superficie simple y consultas espaciales, forma para la detección de objeto y el Solucionador de selección de ubicación del objeto para la colocación de restricción en función de los conjuntos de objetos.</span><span class="sxs-lookup"><span data-stu-id="be82b-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="be82b-178">Cada una de ellas se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="be82b-178">Each of these is described below.</span></span> <span data-ttu-id="be82b-179">Además de las tres interfaces de módulo principal, una interfaz de la conversión de ray puede usarse para recuperar tipos de superficie con etiquetas y una malla playspace estanca personalizados se puede copiar.</span><span class="sxs-lookup"><span data-stu-id="be82b-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="be82b-180">Ray conversión</span><span class="sxs-lookup"><span data-stu-id="be82b-180">Ray Casting</span></span>

<span data-ttu-id="be82b-181">Después de haber analizado y finaliza la sala, las etiquetas se hayan generado internamente para superficies como paredes, ceiling y floor.</span><span class="sxs-lookup"><span data-stu-id="be82b-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="be82b-182">El "PlayspaceRaycast" función toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y si es así, la información sobre la que se muestran en forma de un "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="be82b-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="be82b-183">Internamente, el raycast es calculado con respecto a la representación de voxel calculada 8cm al cubo de la playspace.</span><span class="sxs-lookup"><span data-stu-id="be82b-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="be82b-184">Cada voxel contiene un conjunto de elementos de superficie con datos de la topología procesados (también conocido como surfels).</span><span class="sxs-lookup"><span data-stu-id="be82b-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="be82b-185">Se comparan los surfels dentro de la celda voxel intersectado y la mejor coincidencia utilizada para buscar la información de topología.</span><span class="sxs-lookup"><span data-stu-id="be82b-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="be82b-186">Estos datos de la topología contienen el etiquetado devuelto en el formulario de la enumeración "SurfaceTypes", así como el área expuesta de la superficie de intersección.</span><span class="sxs-lookup"><span data-stu-id="be82b-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="be82b-187">En el ejemplo de Unity, el cursor convierte un rayo cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="be82b-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="be82b-188">En primer lugar, con colisionadores de Unity.</span><span class="sxs-lookup"><span data-stu-id="be82b-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="be82b-189">En segundo lugar, con representación de mundo del módulo de la descripción.</span><span class="sxs-lookup"><span data-stu-id="be82b-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="be82b-190">Y por último, vuelva a elementos de IU.</span><span class="sxs-lookup"><span data-stu-id="be82b-190">And finally, again UI elements.</span></span> <span data-ttu-id="be82b-191">En esta aplicación, la interfaz de usuario obtiene la prioridad, a continuación el resultado de la descripción y, por último, colisionadores de Unity.</span><span class="sxs-lookup"><span data-stu-id="be82b-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="be82b-192">El SurfaceType se notifica como texto situado junto al cursor.</span><span class="sxs-lookup"><span data-stu-id="be82b-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="be82b-193">![Tipo de superficie tiene la etiqueta situado junto al cursor](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="be82b-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="be82b-194">*Tipo de superficie tiene la etiqueta situado junto al cursor*</span><span class="sxs-lookup"><span data-stu-id="be82b-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="be82b-195">Consultas de topología</span><span class="sxs-lookup"><span data-stu-id="be82b-195">Topology Queries</span></span>

<span data-ttu-id="be82b-196">En el archivo DLL, el Administrador de la topología controla etiquetado del entorno.</span><span class="sxs-lookup"><span data-stu-id="be82b-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="be82b-197">Como se mencionó anteriormente, gran parte de los datos se almacena en surfels, dentro de un volumen voxel.</span><span class="sxs-lookup"><span data-stu-id="be82b-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="be82b-198">Además, la estructura "PlaySpaceInfos" se usa para almacenar información sobre la playspace, incluida la alineación del mundo (más detalles en este tema), floor y ceiling de alto.</span><span class="sxs-lookup"><span data-stu-id="be82b-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="be82b-199">Se utiliza la heurística para determinar las paredes, ceiling y floor.</span><span class="sxs-lookup"><span data-stu-id="be82b-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="be82b-200">Por ejemplo, la superficie más grande y más baja horizontal con más de 1 área expuesta de m2 se considera el suelo.</span><span class="sxs-lookup"><span data-stu-id="be82b-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="be82b-201">Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de análisis también se usa en este proceso.</span><span class="sxs-lookup"><span data-stu-id="be82b-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="be82b-202">Un subconjunto de consultas expuestas por el Administrador de topología se exponen fuera a través de la dll.</span><span class="sxs-lookup"><span data-stu-id="be82b-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="be82b-203">Las consultas de topología expuestas son los siguientes.</span><span class="sxs-lookup"><span data-stu-id="be82b-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="be82b-204">Cada una de las consultas tiene un conjunto de parámetros, el tipo de consulta específicos.</span><span class="sxs-lookup"><span data-stu-id="be82b-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="be82b-205">En el ejemplo siguiente, el usuario especifica el alto mínimo anc & ho del volumen deseado, el alto mínimo de la selección de ubicación por encima el suelo y la cantidad mínima de limpieza delante el volumen.</span><span class="sxs-lookup"><span data-stu-id="be82b-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="be82b-206">Todas las medidas son en metros.</span><span class="sxs-lookup"><span data-stu-id="be82b-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="be82b-207">Cada una de estas consultas toma una matriz de estructuras "TopologyResult" preasignada.</span><span class="sxs-lookup"><span data-stu-id="be82b-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="be82b-208">El parámetro "locationCount" especifica la longitud de la matriz pasada.</span><span class="sxs-lookup"><span data-stu-id="be82b-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="be82b-209">El valor devuelto indica el número de ubicaciones devueltas.</span><span class="sxs-lookup"><span data-stu-id="be82b-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="be82b-210">Este número nunca es mayor que ha pasado en el parámetro "locationCount".</span><span class="sxs-lookup"><span data-stu-id="be82b-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="be82b-211">El "TopologyResult" contiene la posición central de las dimensiones del espacio se encuentra, la dirección opuesta (es decir, normal) y el volumen devuelto.</span><span class="sxs-lookup"><span data-stu-id="be82b-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="be82b-212">Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculado a un botón en el panel de interfaz de usuario virtual.</span><span class="sxs-lookup"><span data-stu-id="be82b-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="be82b-213">El disco duro de ejemplo códigos de los parámetros para cada una de estas consultas para valores razonables.</span><span class="sxs-lookup"><span data-stu-id="be82b-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="be82b-214">En el código de ejemplo para obtener más ejemplos, consulte SpaceVisualizer.cs.</span><span class="sxs-lookup"><span data-stu-id="be82b-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="be82b-215">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="be82b-215">Shape Queries</span></span>

<span data-ttu-id="be82b-216">Dentro de la dll, el analizador de forma ("ShapeAnalyzer_W") usa el analizador de topología para coincidir con las formas personalizadas definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="be82b-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="be82b-217">El ejemplo de Unity define un conjunto de formas y muestra los resultados de salida a través del menú de la consulta en la aplicación, dentro de la pestaña de la forma. La intención es que el usuario puede definir sus propias consultas de forma de objeto y asegúrese de usar de ellas, según sea necesario para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="be82b-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="be82b-218">Tenga en cuenta que el análisis de forma funciona en las superficies horizontales.</span><span class="sxs-lookup"><span data-stu-id="be82b-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="be82b-219">Por ejemplo, un sofá, se define por la superficie del asiento sin formato y la parte superior plana de vuelta el sofá.</span><span class="sxs-lookup"><span data-stu-id="be82b-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="be82b-220">La consulta shape busca dos superficies de un intervalo de tamaño, el alto y el aspecto específico, con las dos superficies alineado y conectado.</span><span class="sxs-lookup"><span data-stu-id="be82b-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="be82b-221">Con la terminología de API, el sofá puesto y el back-superior son componentes de la forma y los requisitos de alineación son las restricciones de componentes de forma.</span><span class="sxs-lookup"><span data-stu-id="be82b-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="be82b-222">Una consulta de ejemplo que se define en el ejemplo de Unity (ShapeDefinition.cs), para los objetos "sittable" es el siguiente.</span><span class="sxs-lookup"><span data-stu-id="be82b-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="be82b-223">Cada consulta shape se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componente y un conjunto de restricciones de forma que enumerar las dependencias entre los componentes.</span><span class="sxs-lookup"><span data-stu-id="be82b-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="be82b-224">En este ejemplo incluye tres restricciones en una definición de componente único y sin restricciones de forma entre los componentes (como hay solo un componente).</span><span class="sxs-lookup"><span data-stu-id="be82b-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="be82b-225">En cambio, la forma del sofá tiene dos componentes de la forma y cuatro de las restricciones de forma.</span><span class="sxs-lookup"><span data-stu-id="be82b-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="be82b-226">Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="be82b-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="be82b-227">Se proporcionan funciones de contenedor en el módulo de Unity para la creación fácil de definiciones de forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="be82b-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="be82b-228">Encontrará la lista completa de las restricciones de componente y la forma de "SpatialUnderstandingDll.cs" dentro de la "ShapeComponentConstraint" y las estructuras de "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="be82b-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="be82b-229">![Forma de rectángulo se encuentra en esta superficie](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="be82b-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="be82b-230">*Forma de rectángulo se encuentra en esta superficie*</span><span class="sxs-lookup"><span data-stu-id="be82b-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="be82b-231">Solucionador de selección de ubicación del objeto</span><span class="sxs-lookup"><span data-stu-id="be82b-231">Object Placement Solver</span></span>

<span data-ttu-id="be82b-232">El Solucionador de selección de ubicación del objeto puede utilizarse para identificar las ubicaciones ideales en la sala física para colocar los objetos.</span><span class="sxs-lookup"><span data-stu-id="be82b-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="be82b-233">El solucionador encontrará que el que mejor ajusta según las reglas de objeto y las restricciones de ubicación.</span><span class="sxs-lookup"><span data-stu-id="be82b-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="be82b-234">Además, las consultas de objeto se mantienen hasta que se quita el objeto con "Solver_RemoveObject" o "Solver_RemoveAllObjects", lo que permite las llamadas restringido de colocación de varios objetos.</span><span class="sxs-lookup"><span data-stu-id="be82b-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="be82b-235">Las consultas de selección de ubicación de los objetos se componen de tres partes: un tipo de colocación con parámetros, una lista de reglas y una lista de restricciones.</span><span class="sxs-lookup"><span data-stu-id="be82b-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="be82b-236">Para ejecutar una consulta, use la siguiente API.</span><span class="sxs-lookup"><span data-stu-id="be82b-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="be82b-237">Esta función toma un nombre de objeto, definición de la selección de ubicación y una lista de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="be82b-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="be82b-238">El C# contenedores proporciona construcción funciones auxiliares para facilitar la construcción de la regla y la restricción.</span><span class="sxs-lookup"><span data-stu-id="be82b-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="be82b-239">La definición de la selección de ubicación contiene el tipo de consulta: es decir, uno de los siguientes.</span><span class="sxs-lookup"><span data-stu-id="be82b-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="be82b-240">Cada uno de los tipos de posición tiene un conjunto de parámetros únicos para el tipo.</span><span class="sxs-lookup"><span data-stu-id="be82b-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="be82b-241">La estructura de "ObjectPlacementDefinition" contiene un conjunto de funciones auxiliares estáticos para crear estas definiciones.</span><span class="sxs-lookup"><span data-stu-id="be82b-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="be82b-242">Por ejemplo, para encontrar un lugar para colocar un objeto en el suelo, puede usar la función siguiente.</span><span class="sxs-lookup"><span data-stu-id="be82b-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="be82b-243">público estático ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) además de para el tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="be82b-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="be82b-244">No se puede infringir las reglas.</span><span class="sxs-lookup"><span data-stu-id="be82b-244">Rules cannot be violated.</span></span> <span data-ttu-id="be82b-245">Ubicaciones posibles de la selección de ubicación que cumplen el tipo y las reglas están optimizadas, a continuación, en el conjunto de restricciones con el fin de seleccionar la ubicación de la ubicación óptima.</span><span class="sxs-lookup"><span data-stu-id="be82b-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="be82b-246">Cada una de las reglas y restricciones se puede crear las funciones de creación estático proporcionado.</span><span class="sxs-lookup"><span data-stu-id="be82b-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="be82b-247">A continuación, se proporciona una función de construcción de restricción y regla de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="be82b-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="be82b-248">El siguiente objeto de consulta de selección de ubicación está buscando un lugar para colocar un cubo de la mitad del medidor en el borde de una superficie, fuera de sí previamente colocar objetos y cerca del centro de la sala de.</span><span class="sxs-lookup"><span data-stu-id="be82b-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="be82b-249">Si se realiza correctamente, una estructura de "ObjectPlacementResult" que contiene la posición de colocación, dimensiones y la orientación se devuelve.</span><span class="sxs-lookup"><span data-stu-id="be82b-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="be82b-250">Además, la selección de ubicación se agrega a la lista interna de la dll de objetos colocados.</span><span class="sxs-lookup"><span data-stu-id="be82b-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="be82b-251">Las consultas posteriores de la selección de ubicación tendrá este objeto en la cuenta.</span><span class="sxs-lookup"><span data-stu-id="be82b-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="be82b-252">El archivo "LevelSolver.cs" en el ejemplo de Unity contiene más de las consultas de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="be82b-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="be82b-253">![Resultados de la posición de los objetos](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="be82b-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="be82b-254">*Figura 3: Cuadros de selección azul cómo el resultado de lugar tres participar en las consultas con fuera de las reglas de posición de cámara*</span><span class="sxs-lookup"><span data-stu-id="be82b-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="be82b-255">Al resolver para la ubicación de colocación de varios objetos necesarios para un escenario de aplicación o nivel, resolver primero objetos indispensables y de gran tamaño con el fin de maximizar la probabilidad de que se puede encontrar un espacio.</span><span class="sxs-lookup"><span data-stu-id="be82b-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="be82b-256">Es importante el orden de selección de ubicación.</span><span class="sxs-lookup"><span data-stu-id="be82b-256">Placement order is important.</span></span> <span data-ttu-id="be82b-257">Si no se puede encontrar las selecciones de ubicación del objeto, intente configuraciones menos restringidas.</span><span class="sxs-lookup"><span data-stu-id="be82b-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="be82b-258">Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de espacio.</span><span class="sxs-lookup"><span data-stu-id="be82b-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="be82b-259">Proceso de exploración de sala</span><span class="sxs-lookup"><span data-stu-id="be82b-259">Room Scanning Process</span></span>

<span data-ttu-id="be82b-260">Mientras la solución de asignación espacial proporcionada por el HoloLens está diseñada para ser lo suficientemente genéricos como para satisfacer las necesidades de toda la gama de espacios del problema, el módulo de comprensión espaciales se generó para admitir las necesidades de dos juegos específicos.</span><span class="sxs-lookup"><span data-stu-id="be82b-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="be82b-261">Su solución está estructurada en torno a un proceso específico y un conjunto de supuestos, resumida a continuación.</span><span class="sxs-lookup"><span data-stu-id="be82b-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="be82b-262">Controlada por playspace "pintar" – durante la fase de análisis, el usuario, el usuario se mueve y mira alrededor reproduce el ritmo, pintar eficazmente las áreas que deben incluirse.</span><span class="sxs-lookup"><span data-stu-id="be82b-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="be82b-263">La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.</span><span class="sxs-lookup"><span data-stu-id="be82b-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="be82b-264">En el interior de inicio o de instalación de office: la consulta de funciones están diseñadas en torno a las superficies planas y paredes ángulos rectos.</span><span class="sxs-lookup"><span data-stu-id="be82b-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="be82b-265">Esta es una limitación temporal.</span><span class="sxs-lookup"><span data-stu-id="be82b-265">This is a soft limitation.</span></span> <span data-ttu-id="be82b-266">Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo del eje principal y secundaria.</span><span class="sxs-lookup"><span data-stu-id="be82b-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="be82b-267">El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="be82b-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="be82b-268">Llama a las funciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="be82b-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="be82b-269">El flujo de análisis controlado por el comportamiento de "SpatialUnderstanding" llama InitScan, a continuación, UpdateScan cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="be82b-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="be82b-270">Cuando informa de la consulta de estadísticas de cobertura razonable, se permite al usuario airtap para llamar a RequestFinish para indicar el final de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="be82b-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="be82b-271">UpdateScan continúa llamada hasta que devueltos es el valor indica que el archivo dll ha completado el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="be82b-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="be82b-272">Malla de descripción</span><span class="sxs-lookup"><span data-stu-id="be82b-272">Understanding Mesh</span></span>

<span data-ttu-id="be82b-273">El archivo dll de la descripción almacena internamente el playspace como una cuadrícula de 8cm tamaño voxel cubos.</span><span class="sxs-lookup"><span data-stu-id="be82b-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="be82b-274">Durante la parte inicial del análisis, se completa un análisis del componente principal para determinar los ejes de la sala.</span><span class="sxs-lookup"><span data-stu-id="be82b-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="be82b-275">Internamente, almacena su espacio voxel alineado para estos ejes.</span><span class="sxs-lookup"><span data-stu-id="be82b-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="be82b-276">Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie desde el volumen voxel.</span><span class="sxs-lookup"><span data-stu-id="be82b-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="be82b-277">![Malla generado producidos desde el volumen voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="be82b-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="be82b-278">*Malla generado producidos desde el volumen voxel*</span><span class="sxs-lookup"><span data-stu-id="be82b-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="be82b-279">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="be82b-279">Troubleshooting</span></span>
* <span data-ttu-id="be82b-280">Asegúrese de que ha establecido la [SpatialPerception](#setting-the-spatialperception-capability) capacidad</span><span class="sxs-lookup"><span data-stu-id="be82b-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="be82b-281">Cuando se pierde el seguimiento, el siguiente evento OnSurfaceChanged quitará todas las mallas.</span><span class="sxs-lookup"><span data-stu-id="be82b-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="be82b-282">Asignación espacial en el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="be82b-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="be82b-283">Para obtener más información sobre el uso de la asignación espacial con el Kit de herramientas de realidad mixta v2, consulte el <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sección reconocimiento espacial</a> de los documentos MRTK.</span><span class="sxs-lookup"><span data-stu-id="be82b-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="be82b-284">Vea también</span><span class="sxs-lookup"><span data-stu-id="be82b-284">See also</span></span>
* [<span data-ttu-id="be82b-285">MR Spatial 230: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="be82b-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="be82b-286">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="be82b-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="be82b-287">Sistemas de coordenadas de Unity</span><span class="sxs-lookup"><span data-stu-id="be82b-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="be82b-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="be82b-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="be82b-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="be82b-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="be82b-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="be82b-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="be82b-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="be82b-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
