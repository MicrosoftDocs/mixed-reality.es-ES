---
title: Asignación espacial en Unity
description: Representación y colisión con la geometría del mundo real en su lugar en Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, asignación espacial, representador, Colisionador, malla, exploración, componente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148649"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="8d637-104">Asignación espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="8d637-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="8d637-105">En este tema se describe cómo usar la [asignación espacial](spatial-mapping.md) en el proyecto de Unity, con lo que se recuperan mallas triangulares que representan las superficies del mundo en torno a un dispositivo HoloLens, para la selección de ubicación, la oclusión, el análisis de habitación y mucho más.</span><span class="sxs-lookup"><span data-stu-id="8d637-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="8d637-106">Unity incluye compatibilidad total con la asignación espacial, que se expone a los desarrolladores de las siguientes maneras:</span><span class="sxs-lookup"><span data-stu-id="8d637-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="8d637-107">Componentes de asignación espacial disponibles en MixedRealityToolkit, que proporcionan una ruta de acceso cómoda y rápida para empezar a trabajar con la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="8d637-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="8d637-108">API de asignación espacial de nivel inferior, que proporcionan control total y permiten una personalización específica de la aplicación más sofisticada.</span><span class="sxs-lookup"><span data-stu-id="8d637-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="8d637-109">Para usar la asignación espacial en la aplicación, debe establecerse la funcionalidad spatialPerception en el AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="8d637-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="8d637-110">Establecimiento de la funcionalidad SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="8d637-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="8d637-111">Para que una aplicación consuma datos de asignación espacial, la funcionalidad SpatialPerception debe estar habilitada.</span><span class="sxs-lookup"><span data-stu-id="8d637-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="8d637-112">Cómo habilitar la funcionalidad SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="8d637-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="8d637-113">En el editor de Unity, abra el panel de **configuración del reproductor** (Editar > configuración del proyecto > Player).</span><span class="sxs-lookup"><span data-stu-id="8d637-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="8d637-114">Haga clic en la pestaña **"tienda Windows"**</span><span class="sxs-lookup"><span data-stu-id="8d637-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="8d637-115">Expanda **"configuración de publicación"** y seleccione la funcionalidad **"SpatialPerception"** en la lista **"funcionalidades"** .</span><span class="sxs-lookup"><span data-stu-id="8d637-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="8d637-116">Tenga en cuenta que si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o [establecer manualmente esta funcionalidad en el AppxManifest de Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="8d637-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="8d637-117">La asignación espacial también requiere un MaxVersionTested de al menos 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="8d637-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="8d637-118">En Visual Studio, haga clic con el botón derecho en **Package. appxmanifest** en el explorador de soluciones y seleccione **Ver código** .</span><span class="sxs-lookup"><span data-stu-id="8d637-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="8d637-119">Busque la línea que especifica **TargetDeviceFamily** y cambie **MaxVersionTested = "10.0.10240.0"** por **MaxVersionTested = "10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="8d637-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="8d637-120">**Guarde** el paquete. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="8d637-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="8d637-121">Introducción a los componentes de asignación espacial integrados de Unity</span><span class="sxs-lookup"><span data-stu-id="8d637-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="8d637-122">Unity ofrece 2 componentes para agregar fácilmente la asignación espacial a la aplicación, el representador de **asignación espacial** y el Colisionador de **asignación espacial**.</span><span class="sxs-lookup"><span data-stu-id="8d637-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="8d637-123">Representador de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="8d637-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="8d637-124">El representador de asignación espacial permite la visualización de la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Representador de asignación espacial en Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="8d637-126">Colisionador de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="8d637-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="8d637-127">El Colisionador de asignación espacial permite la interacción de contenido holográfica (o de caracteres), como la física, con la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Colisionador de asignación espacial en Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="8d637-129">Usar los componentes de asignación espacial integrados</span><span class="sxs-lookup"><span data-stu-id="8d637-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="8d637-130">Puede Agregar ambos componentes a la aplicación si desea visualizar y interactuar con las superficies físicas.</span><span class="sxs-lookup"><span data-stu-id="8d637-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="8d637-131">Para usar estos dos componentes en la aplicación de Unity:</span><span class="sxs-lookup"><span data-stu-id="8d637-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="8d637-132">Seleccione un GameObject en el centro del área en la que desea detectar mallas de superficie espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="8d637-133">En la ventana del inspector, **agregue el elemento** > Colisionador de**asignación espacial** del componente**XR** > o el representador de **asignación espacial**.</span><span class="sxs-lookup"><span data-stu-id="8d637-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="8d637-134">Puede encontrar más detalles sobre cómo usar estos componentes en el sitio de <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentación de Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="8d637-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="8d637-135">Ir más allá de los componentes de asignación espacial integrados</span><span class="sxs-lookup"><span data-stu-id="8d637-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="8d637-136">Estos componentes facilitan la tarea de arrastrar y colocar para empezar a trabajar con la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="8d637-137"> Si desea continuar, hay dos rutas principales para explorar:</span><span class="sxs-lookup"><span data-stu-id="8d637-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="8d637-138">Para realizar su propio procesamiento de malla de nivel inferior, consulte la sección siguiente sobre la API de script de asignación espacial de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="8d637-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="8d637-139">Para realizar análisis de malla de nivel superior, consulte la sección siguiente sobre la biblioteca SpatialUnderstanding en <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span><span class="sxs-lookup"><span data-stu-id="8d637-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="8d637-140">Uso de la API de asignación espacial de Unity de bajo nivel</span><span class="sxs-lookup"><span data-stu-id="8d637-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="8d637-141">Si necesita más control de los que obtiene del representador de asignación espacial y los componentes de Colisionador de asignación espacial, puede usar las API de script de asignación espacial de bajo nivel.</span><span class="sxs-lookup"><span data-stu-id="8d637-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="8d637-142">**System.IO** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="8d637-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="8d637-143">**Tipos**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="8d637-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="8d637-144">A continuación se describe el flujo sugerido para una aplicación que usa las API de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="8d637-145">Configuración de los SurfaceObserver</span><span class="sxs-lookup"><span data-stu-id="8d637-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="8d637-146">Cree una instancia de un objeto SurfaceObserver para cada región de espacio definida por la aplicación para la que necesite datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="8d637-147">Especifique la región de espacio para la que cada objeto SurfaceObserver proporcionará los datos mediante una llamada a SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="8d637-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="8d637-148">Para volver a definir la región de espacio en el futuro, simplemente vuelva a llamar a uno de estos métodos.</span><span class="sxs-lookup"><span data-stu-id="8d637-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="8d637-149">Cuando se llama a SurfaceObserver. Update (), debe proporcionar un controlador para cada superficie espacial en la región de espacio de SurfaceObserver para la que el sistema de asignación espacial tiene información nueva.</span><span class="sxs-lookup"><span data-stu-id="8d637-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="8d637-150">El controlador recibe, para una superficie espacial:</span><span class="sxs-lookup"><span data-stu-id="8d637-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="8d637-151">Control de cambios de superficie</span><span class="sxs-lookup"><span data-stu-id="8d637-151">Handling Surface Changes</span></span>

<span data-ttu-id="8d637-152">Hay varios casos principales que se deben controlar.</span><span class="sxs-lookup"><span data-stu-id="8d637-152">There are several main cases to handle.</span></span> <span data-ttu-id="8d637-153">Se ha agregado & actualizado que puede usar la misma ruta de código y se ha quitado.</span><span class="sxs-lookup"><span data-stu-id="8d637-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="8d637-154">En los casos agregados & actualizados en el ejemplo, se agrega u obtiene el GameObject que representa esta malla del diccionario, se crea un struct SurfaceData con los componentes necesarios y, después, se llama a RequestMeshDataAsync para rellenar el GameObject con los datos de la malla y posición en la escena.</span><span class="sxs-lookup"><span data-stu-id="8d637-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="8d637-155">En el caso de que se quite, se quita el GameObject que representa esta malla del diccionario y se destruye.</span><span class="sxs-lookup"><span data-stu-id="8d637-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

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

### <a name="handling-data-ready"></a><span data-ttu-id="8d637-156">Controlar los datos preparados</span><span class="sxs-lookup"><span data-stu-id="8d637-156">Handling Data Ready</span></span>

<span data-ttu-id="8d637-157">El controlador OnDataReady recibe un objeto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="8d637-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="8d637-158">Los objetos WorldAnchor, MeshFilter y (opcionalmente) MeshCollider que contiene reflejan el estado más reciente de la superficie espacial asociada.</span><span class="sxs-lookup"><span data-stu-id="8d637-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="8d637-159">Opcionalmente, realice el análisis y/o el [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla mediante el acceso al miembro de la malla del objeto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="8d637-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="8d637-160">Represente la superficie espacial con la malla más reciente y, opcionalmente, Úsela para las colisiones físicas y raycasts.</span><span class="sxs-lookup"><span data-stu-id="8d637-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="8d637-161">Es importante confirmar que el contenido de SurfaceData no es NULL.</span><span class="sxs-lookup"><span data-stu-id="8d637-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="8d637-162">Iniciar el procesamiento en las actualizaciones</span><span class="sxs-lookup"><span data-stu-id="8d637-162">Start processing on updates</span></span>

<span data-ttu-id="8d637-163">Se debe llamar a SurfaceObserver. Update () en un retraso, no en todos los fotogramas.</span><span class="sxs-lookup"><span data-stu-id="8d637-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="8d637-164">Análisis de malla de nivel superior: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="8d637-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="8d637-165"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> es una colección de código de utilidad útil para el desarrollo holográfica basado en las API de Unity de Holographic.</span><span class="sxs-lookup"><span data-stu-id="8d637-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="8d637-166">Descripción espacial</span><span class="sxs-lookup"><span data-stu-id="8d637-166">Spatial Understanding</span></span>

<span data-ttu-id="8d637-167">Al colocar hologramas en el mundo físico, a menudo es conveniente ir más allá de los planos de malla y de superficie de la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8d637-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="8d637-168">Cuando la selección de ubicación se realiza con procedimientos, es deseable un nivel más alto de comprensión del entorno.</span><span class="sxs-lookup"><span data-stu-id="8d637-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="8d637-169">Normalmente, esto requiere tomar decisiones sobre qué es el suelo, el techo y las paredes.</span><span class="sxs-lookup"><span data-stu-id="8d637-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="8d637-170">Además, la capacidad de optimizar con respecto a un conjunto de restricciones de selección de ubicación para determinar las ubicaciones físicas más deseables de los objetos holográficas.</span><span class="sxs-lookup"><span data-stu-id="8d637-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="8d637-171">Durante el desarrollo de conkers y fragmentos jóvenes, Asobo Studios se enfrentó a este problema en el desarrollo de una sala de Solver para este fin.</span><span class="sxs-lookup"><span data-stu-id="8d637-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="8d637-172">Cada uno de estos juegos tenía necesidades específicas del juego, pero compartimos la tecnología de comprensión espacial básica.</span><span class="sxs-lookup"><span data-stu-id="8d637-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="8d637-173">La biblioteca HoloToolkit. SpatialUnderstanding encapsula esta tecnología, lo que permite encontrar rápidamente espacios vacíos en las paredes, colocar objetos en el límite superior, identificar colocadas para que el carácter quede sentado y una gran cantidad de consultas espaciales.</span><span class="sxs-lookup"><span data-stu-id="8d637-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="8d637-174">Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad.</span><span class="sxs-lookup"><span data-stu-id="8d637-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="8d637-175">El código de C++ Solver se ha encapsulado en un archivo dll de UWP y expuesto a Unity con una colocación en recurso prefabricado incluida en el MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="8d637-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="8d637-176">Descripción de los módulos</span><span class="sxs-lookup"><span data-stu-id="8d637-176">Understanding Modules</span></span>

<span data-ttu-id="8d637-177">Hay tres interfaces principales que expone el módulo: la topología para las consultas simples de superficie y espacial, la forma de detección de objetos y la colocación de objetos de Solver para la colocación basada en restricciones de los conjuntos de objetos.</span><span class="sxs-lookup"><span data-stu-id="8d637-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="8d637-178">Cada una de ellas se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="8d637-178">Each of these is described below.</span></span> <span data-ttu-id="8d637-179">Además de las tres interfaces de módulos principales, se puede usar una interfaz de conversión de rayos para recuperar tipos de superficie etiquetada y se puede copiar una malla Playspace estanco personalizada.</span><span class="sxs-lookup"><span data-stu-id="8d637-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="8d637-180">Conversión de rayos</span><span class="sxs-lookup"><span data-stu-id="8d637-180">Ray Casting</span></span>

<span data-ttu-id="8d637-181">Una vez que se ha analizado y finalizado el salón, las etiquetas se generan internamente para las superficies como el piso, el techo y las paredes.</span><span class="sxs-lookup"><span data-stu-id="8d637-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="8d637-182">La función "PlayspaceRaycast" toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y, en caso afirmativo, información sobre esa superficie en forma de "RaycastResult".</span><span class="sxs-lookup"><span data-stu-id="8d637-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

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

<span data-ttu-id="8d637-183">Internamente, el Raycast se calcula con la representación calculada de 8cm con cubo voxel de Playspace.</span><span class="sxs-lookup"><span data-stu-id="8d637-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="8d637-184">Cada voxel contiene un conjunto de elementos Surface con datos de topología procesados (también conocido como surfels).</span><span class="sxs-lookup"><span data-stu-id="8d637-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="8d637-185">Se comparan los surfels contenidos en la celda voxel intersectada y la mejor coincidencia utilizada para buscar la información de la topología.</span><span class="sxs-lookup"><span data-stu-id="8d637-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="8d637-186">Estos datos de topología contienen la etiqueta devuelta en forma de enumeración "SurfaceTypes", así como el área expuesta de la superficie intersectada.</span><span class="sxs-lookup"><span data-stu-id="8d637-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="8d637-187">En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="8d637-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="8d637-188">En primer lugar, con los colisionadores de Unity.</span><span class="sxs-lookup"><span data-stu-id="8d637-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="8d637-189">En segundo lugar, en la representación mundial del módulo de comprensión.</span><span class="sxs-lookup"><span data-stu-id="8d637-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="8d637-190">Y, por último, los elementos de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="8d637-190">And finally, again UI elements.</span></span> <span data-ttu-id="8d637-191">En esta aplicación, la interfaz de usuario obtiene prioridad, después del resultado de comprensión y, por último, los colisionadores de Unity.</span><span class="sxs-lookup"><span data-stu-id="8d637-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="8d637-192">El SurfaceType se muestra como texto junto al cursor.</span><span class="sxs-lookup"><span data-stu-id="8d637-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="8d637-193">![El tipo de superficie se etiqueta junto al cursor](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8d637-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="8d637-194">*El tipo de superficie se etiqueta junto al cursor*</span><span class="sxs-lookup"><span data-stu-id="8d637-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="8d637-195">Consultas de topología</span><span class="sxs-lookup"><span data-stu-id="8d637-195">Topology Queries</span></span>

<span data-ttu-id="8d637-196">En el archivo DLL, el administrador de topología controla el etiquetado del entorno.</span><span class="sxs-lookup"><span data-stu-id="8d637-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="8d637-197">Como se mencionó anteriormente, gran parte de los datos se almacenan en surfels, contenidos en un volumen de voxel.</span><span class="sxs-lookup"><span data-stu-id="8d637-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="8d637-198">Además, la estructura "PlaySpaceInfos" se usa para almacenar información sobre Playspace, incluida la alineación del mundo (más detalles a continuación), piso y alto del techo.</span><span class="sxs-lookup"><span data-stu-id="8d637-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="8d637-199">La heurística se usa para determinar el piso, el techo y las paredes.</span><span class="sxs-lookup"><span data-stu-id="8d637-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="8d637-200">Por ejemplo, la superficie horizontal más grande y más baja con un área de superficie superior a 1 m2 se considera el piso.</span><span class="sxs-lookup"><span data-stu-id="8d637-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="8d637-201">Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de digitalización también se usa en este proceso.</span><span class="sxs-lookup"><span data-stu-id="8d637-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="8d637-202">Un subconjunto de las consultas expuestas por el administrador de topología se expone a través de la dll.</span><span class="sxs-lookup"><span data-stu-id="8d637-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="8d637-203">Las consultas de topologías expuestas son las siguientes.</span><span class="sxs-lookup"><span data-stu-id="8d637-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="8d637-204">Cada una de las consultas tiene un conjunto de parámetros, específico del tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="8d637-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="8d637-205">En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, el alto mínimo de la ubicación por encima del piso y la cantidad mínima de holgura delante del volumen.</span><span class="sxs-lookup"><span data-stu-id="8d637-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="8d637-206">Todas las medidas están en metros.</span><span class="sxs-lookup"><span data-stu-id="8d637-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="8d637-207">Cada una de estas consultas toma una matriz preasignada de estructuras "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="8d637-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="8d637-208">El parámetro "locationCount" especifica la longitud de la matriz pasada.</span><span class="sxs-lookup"><span data-stu-id="8d637-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="8d637-209">El valor devuelto informa del número de ubicaciones devueltas.</span><span class="sxs-lookup"><span data-stu-id="8d637-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="8d637-210">Este número nunca es mayor que el pasado en el parámetro "locationCount".</span><span class="sxs-lookup"><span data-stu-id="8d637-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="8d637-211">"TopologyResult" contiene la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.</span><span class="sxs-lookup"><span data-stu-id="8d637-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="8d637-212">Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual.</span><span class="sxs-lookup"><span data-stu-id="8d637-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="8d637-213">En el ejemplo se codifican los parámetros de cada una de estas consultas en valores razonables.</span><span class="sxs-lookup"><span data-stu-id="8d637-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="8d637-214">Vea SpaceVisualizer.cs en el código de ejemplo para obtener más ejemplos.</span><span class="sxs-lookup"><span data-stu-id="8d637-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="8d637-215">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="8d637-215">Shape Queries</span></span>

<span data-ttu-id="8d637-216">Dentro del archivo dll, el analizador de formas ("ShapeAnalyzer_W") utiliza el analizador de topología para buscar coincidencias con las formas personalizadas definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="8d637-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="8d637-217">En el ejemplo de Unity se define un conjunto de formas y se exponen los resultados a través del menú de consulta en la aplicación, dentro de la pestaña forma. La intención es que el usuario pueda definir sus propias consultas de forma de objeto y hacer uso de ellas, según las necesidades de su aplicación.</span><span class="sxs-lookup"><span data-stu-id="8d637-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="8d637-218">Tenga en cuenta que el análisis de formas solo funciona en superficies horizontales.</span><span class="sxs-lookup"><span data-stu-id="8d637-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="8d637-219">Por ejemplo, un sofá se define mediante la superficie de asiento plana y la parte superior plana del sofá.</span><span class="sxs-lookup"><span data-stu-id="8d637-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="8d637-220">La consulta de forma busca dos superficies de un tamaño, alto y intervalo de aspecto específicos, con las dos superficies alineadas y conectadas.</span><span class="sxs-lookup"><span data-stu-id="8d637-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="8d637-221">Con la terminología de las API, el asiento del sofá y la parte superior son componentes de forma y los requisitos de alineación son restricciones de componentes de forma.</span><span class="sxs-lookup"><span data-stu-id="8d637-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="8d637-222">A continuación se muestra una consulta de ejemplo definida en el ejemplo de Unity (ShapeDefinition.cs) para objetos "sittable".</span><span class="sxs-lookup"><span data-stu-id="8d637-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

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

<span data-ttu-id="8d637-223">Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumeran las dependencias entre los componentes.</span><span class="sxs-lookup"><span data-stu-id="8d637-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="8d637-224">En este ejemplo se incluyen tres restricciones en una definición de componente único y no hay restricciones de forma entre los componentes (como solo hay un componente).</span><span class="sxs-lookup"><span data-stu-id="8d637-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="8d637-225">En cambio, la forma sofá tiene dos componentes de forma y cuatro restricciones de forma.</span><span class="sxs-lookup"><span data-stu-id="8d637-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="8d637-226">Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="8d637-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="8d637-227">Las funciones de contenedor se proporcionan en el módulo Unity para facilitar la creación de definiciones de formas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8d637-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="8d637-228">La lista completa de restricciones de componente y forma se puede encontrar en "SpatialUnderstandingDll.cs" dentro de las estructuras "ShapeComponentConstraint" y "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="8d637-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="8d637-229">![La forma de rectángulo se encuentra en esta superficie](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8d637-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="8d637-230">*La forma de rectángulo se encuentra en esta superficie*</span><span class="sxs-lookup"><span data-stu-id="8d637-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="8d637-231">Selección de ubicación de objetos</span><span class="sxs-lookup"><span data-stu-id="8d637-231">Object Placement Solver</span></span>

<span data-ttu-id="8d637-232">La selección de ubicación de objetos se puede usar para identificar las ubicaciones ideales en la habitación física para colocar los objetos.</span><span class="sxs-lookup"><span data-stu-id="8d637-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="8d637-233">El Solver encontrará la ubicación más adecuada en función de las reglas y restricciones del objeto.</span><span class="sxs-lookup"><span data-stu-id="8d637-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="8d637-234">Además, las consultas de objeto se conservan hasta que el objeto se quita con llamadas "Solver_RemoveObject" o "Solver_RemoveAllObjects", lo que permite la selección de ubicación de varios objetos restringidos.</span><span class="sxs-lookup"><span data-stu-id="8d637-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="8d637-235">Las consultas de selección de ubicación de objetos constan de tres partes: tipo de ubicación con parámetros, una lista de reglas y una lista de restricciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="8d637-236">Para ejecutar una consulta, use la siguiente API.</span><span class="sxs-lookup"><span data-stu-id="8d637-236">To run a query, use the following API.</span></span>

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

<span data-ttu-id="8d637-237">Esta función toma un nombre de objeto, una definición de ubicación y una lista de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="8d637-238">Los C# contenedores proporcionan funciones auxiliares de construcción para facilitar la creación de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="8d637-239">La definición de ubicación contiene el tipo de consulta, es decir, uno de los siguientes.</span><span class="sxs-lookup"><span data-stu-id="8d637-239">The placement definition contains the query type – that is, one of the following.</span></span>

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

<span data-ttu-id="8d637-240">Cada uno de los tipos de ubicación tiene un conjunto de parámetros únicos para el tipo.</span><span class="sxs-lookup"><span data-stu-id="8d637-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="8d637-241">La estructura "ObjectPlacementDefinition" contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="8d637-242">Por ejemplo, para encontrar un lugar donde colocar un objeto en el piso, puede usar la función siguiente.</span><span class="sxs-lookup"><span data-stu-id="8d637-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="8d637-243">public static ObjectPlacementDefinition Create_OnFloor (Vector3 halfDims) además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="8d637-244">No se pueden infringir las reglas.</span><span class="sxs-lookup"><span data-stu-id="8d637-244">Rules cannot be violated.</span></span> <span data-ttu-id="8d637-245">Las ubicaciones de ubicación posibles que satisfacen el tipo y las reglas se optimizan con el conjunto de restricciones para seleccionar la ubicación de colocación óptima.</span><span class="sxs-lookup"><span data-stu-id="8d637-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="8d637-246">Cada una de las reglas y restricciones se pueden crear mediante las funciones de creación estáticas proporcionadas.</span><span class="sxs-lookup"><span data-stu-id="8d637-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="8d637-247">A continuación se proporciona una función de ejemplo y una función de construcción de restricciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="8d637-248">La siguiente consulta de selección de ubicación de objetos busca un lugar donde colocar un cubo de media metro en el borde de una superficie, lejos de otros objetos colocados anteriormente y cerca del centro de la habitación.</span><span class="sxs-lookup"><span data-stu-id="8d637-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

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

<span data-ttu-id="8d637-249">Si se realiza correctamente, se devuelve una estructura "ObjectPlacementResult" que contiene la posición de colocación, las dimensiones y la orientación.</span><span class="sxs-lookup"><span data-stu-id="8d637-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="8d637-250">Además, la selección de ubicación se agrega a la lista interna de objetos colocados del archivo dll.</span><span class="sxs-lookup"><span data-stu-id="8d637-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="8d637-251">Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto.</span><span class="sxs-lookup"><span data-stu-id="8d637-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="8d637-252">El archivo "LevelSolver.cs" del ejemplo de Unity contiene más consultas de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8d637-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="8d637-253">![Resultados de la colocación del objeto](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8d637-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="8d637-254">*Figura 3: Los cuadros azules de cómo se realiza el resultado de tres consultas en planta con respecto a las reglas de posición de la cámara*</span><span class="sxs-lookup"><span data-stu-id="8d637-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="8d637-255">En la resolución de ubicación de varios objetos necesarios para un escenario de nivel o aplicación, primero se resuelven objetos grandes e indispensables con el fin de maximizar la probabilidad de que se pueda encontrar un espacio.</span><span class="sxs-lookup"><span data-stu-id="8d637-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="8d637-256">El orden de la ubicación es importante.</span><span class="sxs-lookup"><span data-stu-id="8d637-256">Placement order is important.</span></span> <span data-ttu-id="8d637-257">Si no se encuentran colocaciones de objeto, pruebe con menos configuraciones restringidas.</span><span class="sxs-lookup"><span data-stu-id="8d637-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="8d637-258">Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de salón.</span><span class="sxs-lookup"><span data-stu-id="8d637-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="8d637-259">Proceso de detección de salas</span><span class="sxs-lookup"><span data-stu-id="8d637-259">Room Scanning Process</span></span>

<span data-ttu-id="8d637-260">Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de la gama completa de espacios problemáticos, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos.</span><span class="sxs-lookup"><span data-stu-id="8d637-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="8d637-261">Su solución está estructurada en torno a un proceso específico y un conjunto de supuestos, que se resumen a continuación.</span><span class="sxs-lookup"><span data-stu-id="8d637-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="8d637-262">Playspace controlada por el usuario "Painting": durante la fase de análisis, el usuario se mueve y se desplaza por el ritmo de las jugadas, con lo que se pintan las áreas que se deben incluir.</span><span class="sxs-lookup"><span data-stu-id="8d637-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="8d637-263">La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.</span><span class="sxs-lookup"><span data-stu-id="8d637-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="8d637-264">Instalación en casa o en el programa de instalación de Office: las funciones de consulta están diseñadas en torno a superficies planas y paredes en los ángulos correctos.</span><span class="sxs-lookup"><span data-stu-id="8d637-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="8d637-265">Se trata de una limitación flexible.</span><span class="sxs-lookup"><span data-stu-id="8d637-265">This is a soft limitation.</span></span> <span data-ttu-id="8d637-266">Sin embargo, durante la fase de examen, se completa un análisis de eje principal para optimizar la teselación de malla junto con el eje principal y el secundario.</span><span class="sxs-lookup"><span data-stu-id="8d637-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="8d637-267">El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="8d637-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="8d637-268">Llama a las siguientes funciones.</span><span class="sxs-lookup"><span data-stu-id="8d637-268">It calls the following functions.</span></span>

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

<span data-ttu-id="8d637-269">El flujo de análisis, controlado por el comportamiento "SpatialUnderstanding" llama a InitScan y, a continuación, UpdateScan cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="8d637-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="8d637-270">Cuando la consulta de estadísticas notifica una cobertura razonable, se permite al usuario airtap llamar a RequestFinish para indicar el final de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="8d637-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="8d637-271">UpdateScan sigue siendo llamado hasta que su valor devuelto indica que el archivo DLL ha finalizado el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="8d637-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="8d637-272">Descripción de la malla</span><span class="sxs-lookup"><span data-stu-id="8d637-272">Understanding Mesh</span></span>

<span data-ttu-id="8d637-273">La dll de comprensión almacena internamente el Playspace como una cuadrícula de cubos voxel de 8cm de tamaño.</span><span class="sxs-lookup"><span data-stu-id="8d637-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="8d637-274">Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la habitación.</span><span class="sxs-lookup"><span data-stu-id="8d637-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="8d637-275">Internamente, almacena su espacio voxel alineado con estos ejes.</span><span class="sxs-lookup"><span data-stu-id="8d637-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="8d637-276">Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie del volumen voxel.</span><span class="sxs-lookup"><span data-stu-id="8d637-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="8d637-277">![Malla generada generada a partir del volumen voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="8d637-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="8d637-278">*Malla generada generada a partir del volumen voxel*</span><span class="sxs-lookup"><span data-stu-id="8d637-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8d637-279">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="8d637-279">Troubleshooting</span></span>
* <span data-ttu-id="8d637-280">Asegúrese de que ha establecido la funcionalidad [SpatialPerception](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="8d637-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="8d637-281">Cuando se pierde el seguimiento, el siguiente evento OnSurfaceChanged quitará todas las mallas.</span><span class="sxs-lookup"><span data-stu-id="8d637-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="8d637-282">Asignación espacial en el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="8d637-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="8d637-283">Para obtener más información sobre el uso de la asignación espacial con el kit de herramientas de realidad mixta V2, consulte la <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">sección de reconocimiento espacial</a> de los documentos de MRTK.</span><span class="sxs-lookup"><span data-stu-id="8d637-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d637-284">Vea también</span><span class="sxs-lookup"><span data-stu-id="8d637-284">See also</span></span>
* [<span data-ttu-id="8d637-285">MR Spatial 230: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="8d637-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="8d637-286">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="8d637-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="8d637-287">Sistemas de coordenadas de Unity</span><span class="sxs-lookup"><span data-stu-id="8d637-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="8d637-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="8d637-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="8d637-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="8d637-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="8d637-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="8d637-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="8d637-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. Bounds</a></span><span class="sxs-lookup"><span data-stu-id="8d637-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
