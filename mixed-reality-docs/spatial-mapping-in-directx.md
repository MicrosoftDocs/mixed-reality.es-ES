---
title: Asignación espacial en DirectX
description: Explica cómo implementar la asignación espacial en la aplicación de DirectX. Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de plataforma Universal de Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixto en realidad, asignación espacial, entorno, interacción, directx, winrt, api, código de ejemplo, UWP, SDK, tutorial
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605791"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="c3a7c-105">Asignación espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="c3a7c-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="c3a7c-106">Este tema describe cómo implementar [asignación espacial](spatial-mapping.md) en la aplicación de DirectX.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="c3a7c-107">Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de plataforma Universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="c3a7c-108">Código de este tema usa el [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) ejemplo de código UWP.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="c3a7c-109">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c3a7c-110">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="c3a7c-111">Introducción al desarrollo de DirectX</span><span class="sxs-lookup"><span data-stu-id="c3a7c-111">DirectX development overview</span></span>

<span data-ttu-id="c3a7c-112">Desarrollo de aplicaciones nativas para la asignación espacial usa las API en el [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="c3a7c-113">Estas API ofrecen control total de la funcionalidad de asignación espacial, de forma análoga directamente a la asignación espacial API expuestas por [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="c3a7c-114">API de percepción</span><span class="sxs-lookup"><span data-stu-id="c3a7c-114">Perception APIs</span></span>

<span data-ttu-id="c3a7c-115">Los tipos primarios proporcionados para el desarrollo de asignación espacial son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="c3a7c-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) proporciona información acerca de las superficies de regiones especificado por la aplicación de espacio cerca del usuario, en forma de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="c3a7c-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describe una sola superficie espacial ordenamientos incluido un identificador único, el volumen y la hora del último cambio de límite.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="c3a7c-118">Proporcionará un SpatialSurfaceMesh asincrónicamente a petición.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="c3a7c-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene parámetros que se usan para personalizar los objetos SpatialSurfaceMesh solicitados desde SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="c3a7c-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa los datos de la malla de una sola superficie espacial.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="c3a7c-121">Los datos de posiciones de los vértices, las normales de vértice y los índices de triángulo se encuentran en los objetos miembro SpatialSurfaceMeshBuffer.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="c3a7c-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) ajusta un único tipo de datos de la malla.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="c3a7c-123">Al desarrollar una aplicación con estas API, el flujo de programa básico tendrá este aspecto (como se muestra en la aplicación de ejemplo que se describe a continuación):</span><span class="sxs-lookup"><span data-stu-id="c3a7c-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="c3a7c-124">**Configurar su SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="c3a7c-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="c3a7c-125">Llame a [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para asegurarse de que el usuario ha dado permiso para la aplicación para usar funciones de asignación espacial del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="c3a7c-126">Crear una instancia de un objeto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="c3a7c-127">Llame a [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar las regiones de espacio en el que desea obtener información sobre las superficies espaciales.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="c3a7c-128">Puede modificar estas regiones en el futuro simplemente vuelva a llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="c3a7c-129">Cada región se especifica mediante un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="c3a7c-130">Registrarse para la [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) evento, que se activará cada vez que hay información nueva acerca de las superficies espaciales en las regiones de espacio que se ha especificado.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="c3a7c-131">**Procesar eventos ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="c3a7c-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="c3a7c-132">En el controlador de eventos, llamar a [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para recibir un mapa de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="c3a7c-133">Utilización de esta asignación, se pueden actualizar los registros de las superficies que espacial [existe en el entorno del usuario](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="c3a7c-134">Para cada objeto SpatialSurfaceInfo, se puede consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) determinar las extensiones espaciales de la superficie, expresada en un [del sistema de coordenadas espacial](coordinate-systems.md) de su elección.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="c3a7c-135">Si decide malla para una superficie espacial de la solicitud, llame al [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="c3a7c-136">Puede proporcionar opciones que especifican la densidad de triángulos deseada y el formato de los datos devueltos de malla.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="c3a7c-137">**Recibir y procesar de malla**</span><span class="sxs-lookup"><span data-stu-id="c3a7c-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="c3a7c-138">Cada llamada a TryComputeLatestMeshAsync will aysnchronously devolver un objeto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="c3a7c-139">De este objeto se pueden acceder a los objetos SpatialSurfaceMeshBuffer independientes para tener acceso a los índices de triángulo, posiciones de los vértices y (si se solicitan) normales de vértice de la malla.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="c3a7c-140">Estos datos estarán en un formato compatible directamente con el [API de Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usa para representar las mallas.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="c3a7c-141">Desde aquí, la aplicación, opcionalmente, puede realizar análisis o [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla y usarla para [representación](spatial-mapping.md#rendering) y física [detalles y colisión](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="c3a7c-142">Un detalle importante que tener en cuenta es que debe aplicar una escala hacia las posiciones de vértices de malla (por ejemplo, en el sombreador de vértices que se usa para representar las mallas) convertirlos de las unidades de entero optimizado en el que se almacenan en el búfer, en metros.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="c3a7c-143">Puede recuperar mediante una llamada a esta escala [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="c3a7c-144">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="c3a7c-144">Troubleshooting</span></span>
* <span data-ttu-id="c3a7c-145">No se olvide de escalar las posiciones de vértices de malla en su sombreador de vértices, mediante la escala devuelta por [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="c3a7c-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="c3a7c-146">Tutorial de ejemplo de código de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="c3a7c-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="c3a7c-147">El [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) ejemplo de código incluye código que puede usar para empezar a cargar las mallas de superficie en la aplicación, incluida la infraestructura para administrar y mallas de superficie de representación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="c3a7c-148">Ahora, analizaremos cómo agregar la funcionalidad de asignación de superficie a la aplicación de DirectX.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="c3a7c-149">Puede agregar este código a su [plantilla de aplicación de Windows Holographic](creating-a-holographic-directx-project.md) proyecto, o bien puede continuar examinando el código de ejemplo mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="c3a7c-150">Este ejemplo de código se basa en la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="c3a7c-151">Configuración de la aplicación para utilizar la funcionalidad de spatialPerception</span><span class="sxs-lookup"><span data-stu-id="c3a7c-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="c3a7c-152">La aplicación debe ser capaz de usar la funcionalidad de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="c3a7c-153">Esto es necesario porque la malla espacial es una representación del entorno del usuario, que puede considerarse datos privados.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="c3a7c-154">Declare esta capacidad en el archivo package.appxmanifest de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="c3a7c-155">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="c3a7c-156">La funcionalidad proviene de la **uap2** espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="c3a7c-157">Para obtener acceso a este espacio de nombres en el manifiesto, incluirla como un *xlmns* atributo el &lt;paquete > elemento.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="c3a7c-158">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="c3a7c-159">Comprobar la compatibilidad de la característica de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="c3a7c-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="c3a7c-160">Windows Mixed Reality admite una amplia gama de dispositivos, incluidos los dispositivos que no admiten la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="c3a7c-161">Si la aplicación puede usar la asignación espacial, o debe usar la asignación espacial, para proporcionar funcionalidad, debe comprobar para asegurarse de que se admite la asignación espacial antes de intentar utilizarlo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="c3a7c-162">Por ejemplo, si la aplicación de realidad mixta requieren asignación espacial, debe mostrar un mensaje a tal efecto si un usuario intenta ejecutarlo en un dispositivo sin asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="c3a7c-163">O bien, la aplicación puede ser capaces de procesar su propio entorno virtual en lugar del entorno del usuario, que proporciona una experiencia similar a lo que sucedería si asignación espacial, no estaba disponible.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="c3a7c-164">En cualquier caso, esta API permite a tener en cuenta cuando no obtener datos de asignación espacial y responder en la forma adecuada de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="c3a7c-165">Para comprobar el dispositivo actual para la compatibilidad con la asignación espacial, primero asegúrese de que el contrato UWP es el nivel 4 o superior y, a continuación, llamar a SpatialSurfaceObserver::IsSupported().</span><span class="sxs-lookup"><span data-stu-id="c3a7c-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="c3a7c-166">Aquí le mostramos cómo hacerlo en el contexto de la [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) ejemplo de código.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="c3a7c-167">Soporte técnico se comprueba justo antes de solicitar acceso.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="c3a7c-168">La API de SpatialSurfaceObserver::IsSupported() está disponible a partir del SDK versión 15063.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="c3a7c-169">Si es necesario, redestinar el proyecto a la versión de la plataforma 15063 antes de usar esta API.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="c3a7c-170">Tenga en cuenta que cuando el contrato UWP es menor que el nivel 4, la aplicación debe continuar como si el dispositivo es capaz de hacer la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="c3a7c-171">Solicitar acceso a los datos de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="c3a7c-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="c3a7c-172">La aplicación necesita solicitar permiso para tener acceso a datos de asignación espacial antes de intentar crear cualquier superficies observadores.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="c3a7c-173">Este es un ejemplo basado en nuestro ejemplo de código de superficie de asignación, con más detalles que proporcionó más adelante en esta página:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="c3a7c-174">Crear un observador de superficie</span><span class="sxs-lookup"><span data-stu-id="c3a7c-174">Create a surface observer</span></span>

<span data-ttu-id="c3a7c-175">El **Windows::Perception::Spatial::Surfaces** espacio de nombres incluye la [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) (clase), que observa el valor de uno o más volúmenes que especifique en un [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="c3a7c-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="c3a7c-176">Use un [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instancia malla de superficie acceder a los datos en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="c3a7c-177">Desde **AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="c3a7c-178">Como se indicó en la sección anterior, debe solicitar acceso a los datos de asignación espacial antes de la aplicación puede usarlo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="c3a7c-179">Este acceso se concede automáticamente el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-179">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="c3a7c-180">A continuación, deberá configurar el observador de superficie para observar un volumen específico de delimitador.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="c3a7c-181">En este caso, observamos un cuadro que tenga 20 x 20 x 5 metros, centrado en el origen del sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="c3a7c-182">Tenga en cuenta que puede establecer varios volúmenes delimitadores en su lugar.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="c3a7c-183">*Este es el pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="c3a7c-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="c3a7c-184">También es posible usar otras formas de delimitadores - como frustum una vista, o un cuadro de límite que no es de eje alineado.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="c3a7c-185">*Este es el pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="c3a7c-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="c3a7c-186">Si la aplicación necesita hacer nada diferente cuando la superficie de asignación de datos no está disponible, puede escribir código para responder al caso donde la [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) no **permitido** , por ejemplo, no se podrá en equipos con dispositivos envolventes puede adjuntados porque no tienen esos dispositivos de hardware para la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="c3a7c-187">Para estos dispositivos, en su lugar, debe confiar en el escenario espacial para obtener información sobre el entorno y la configuración del dispositivo del usuario.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="c3a7c-188">Inicializar y actualizar la colección de malla de superficie</span><span class="sxs-lookup"><span data-stu-id="c3a7c-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="c3a7c-189">Si el observador expuesto se ha creado correctamente, podemos continuar para inicializar la colección de malla de superficie.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="c3a7c-190">En este caso, usamos la API del modelo de extracción para obtener el conjunto actual de superficies observados inmediatamente:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="c3a7c-191">También hay un modelo de inserción disponible para obtener datos de la malla de superficie.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="c3a7c-192">Es libre de diseñar la aplicación utilice solo el modelo de extracción si decide, en cuyo caso deberá sondear en busca de datos con mucha frecuencia: por ejemplo, una vez por fotograma - o durante un período de tiempo específico, como durante la instalación del juego.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="c3a7c-193">Si es así, el código anterior es lo que necesita.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="c3a7c-194">En nuestro ejemplo de código, hemos optado por muestran el uso de ambos modelos con fines pedagógicos.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="c3a7c-195">En este caso, se suscribe a un evento para recibir datos de la malla de superficie actualizada siempre que el sistema reconoce un cambio.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="c3a7c-196">Nuestro ejemplo de código también está configurado para responder a estos eventos.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="c3a7c-197">Veamos cómo hacer esto.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="c3a7c-198">**NOTA:** Esto podría no ser la manera más eficaz para la aplicación controlar los datos de la malla.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="c3a7c-199">Este código está escrito para mayor claridad y no está optimizado.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="c3a7c-200">Los datos de la malla de superficie se proporcionan una asignación de solo lectura que almacena [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objetos mediante [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de clave.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="c3a7c-201">Para procesar estos datos, se buscan primeros para valores de clave que no están en la colección.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="c3a7c-202">Obtener más información sobre cómo se almacenan los datos en nuestra aplicación de ejemplo le mostrará más adelante en este tema.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="c3a7c-203">También tenemos que quitar las mallas de superficie que se encuentran en nuestra colección de malla de superficie, pero que no están en la colección del sistema ya.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="c3a7c-204">Para ello, necesitamos hacer algo parecido a lo contrario de lo que acabamos de agregar y actualizar las mallas; Realizamos un bucle en nuestra aplicación de la colección y compruebe si el **Guid** tenemos está en la colección del sistema.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="c3a7c-205">Si no está en la colección del sistema, se quitará las nuestras.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="c3a7c-206">Desde nuestro controlador de eventos en AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="c3a7c-207">La implementación de la eliminación de la malla en RealtimeSurfaceMeshRenderer.cpp de:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="c3a7c-208">Adquirir y utilizar los búferes de datos de la malla de superficie</span><span class="sxs-lookup"><span data-stu-id="c3a7c-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="c3a7c-209">Obtener la información de la malla de superficie era tan fácil como extraer una recolección de datos y procesamiento de las actualizaciones de esa colección.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="c3a7c-210">Ahora, vamos en los detalles sobre cómo se pueden usar los datos.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="c3a7c-211">En nuestro ejemplo de código, hemos optado por utilizar las mallas de superficie de representación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="c3a7c-212">Se trata de un escenario común para occluding hologramas tras las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="c3a7c-213">También puede representar las mallas, o representar procesado las versiones de ellos, para mostrar al usuario qué áreas de la sala se examinan antes de empezar a proporcionar una funcionalidad de aplicación o juego.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="c3a7c-214">El ejemplo de código inicia el proceso cuando recibe las actualizaciones de la malla de superficie desde el controlador de eventos que se describe en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="c3a7c-215">La línea de código en esta función importante es la llamada para actualizar la superficie *malla*: Llegados a este punto ya hemos procesado la información de la malla, y que se van a obtener los datos de vértice y el índice para su uso según se estime oportuno.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="c3a7c-216">Desde RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="c3a7c-217">Nuestro código de ejemplo está diseñado para que una clase de datos, **SurfaceMesh**, datos de la malla de identificadores de procesamiento y representación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="c3a7c-218">Estos mallas son lo que el **RealtimeSurfaceMeshRenderer** realmente mantiene una asignación de.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="c3a7c-219">Cada uno de ellos tiene una referencia a la SpatialSurfaceMesh que proviene y se usa cada vez que se necesita tener acceso a los búferes de vértice o el índice de la malla, u obtener una transformación de la malla.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="c3a7c-220">Por ahora, se marca la malla como la necesidad de una actualización.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="c3a7c-221">Desde SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="c3a7c-222">Próxima vez que se solicita la malla a dibujarse a sí mismo, comprobará la marca en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="c3a7c-223">Si se necesita una actualización, los búferes de vértices y de índices se actualizará en la GPU.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="c3a7c-224">En primer lugar, se adquieren los búferes de datos sin procesar:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="c3a7c-225">A continuación, creamos los búferes de dispositivo Direct3D con los datos de la malla proporcionados por el HoloLens:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="c3a7c-226">**NOTA:** Para la función auxiliar CreateDirectXBuffer usada en el fragmento de código anterior, vea el ejemplo de código de asignación de la superficie: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="c3a7c-227">Ahora la creación de recursos de dispositivo completada y se considera ser cargados y listos para la actualización y representar la malla.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="c3a7c-228">Actualizar y procesar las mallas de superficie</span><span class="sxs-lookup"><span data-stu-id="c3a7c-228">Update and render surface meshes</span></span>

<span data-ttu-id="c3a7c-229">Nuestra clase SurfaceMesh tiene una función de actualización especializadas.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="c3a7c-230">Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tiene su propia transformación y nuestro ejemplo utiliza el sistema de coordenadas actual para nuestro **SpatialStationaryReferenceFrame** para adquirir la transformación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="c3a7c-231">A continuación, actualiza el búfer de constantes de modelo en la GPU.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-231">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="c3a7c-232">Cuando sea el momento para representar la superficie de mallas, hacemos algún trabajo de preparación antes de representar la colección.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="c3a7c-233">Configuramos la canalización de sombreador para la configuración de representación actual, y configuramos la etapa del ensamblador de entrada.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="c3a7c-234">Tenga en cuenta que la clase auxiliar de cámara holographic **CameraResources.cpp** ya ha configurado el búfer de constantes y proyección de la vista en este momento.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="c3a7c-235">Desde **RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="c3a7c-236">Una vez hecho esto, hemos bucle en nuestra mallas e indicar a cada uno de ellos a dibujarse a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="c3a7c-237">**NOTA:** Este código de ejemplo no está optimizado para usar a algún tipo de caras traseras frustum, pero debe incluir esta característica en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="c3a7c-238">Las mallas individuales son responsables de configurar el búfer de vértices y de índices, stride y el búfer de constantes de transformación de modelo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="c3a7c-239">Al igual que con el cubo girando en la plantilla de aplicación de Windows Holographic, representamos los búferes estereoscópicas mediante la creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="c3a7c-240">Desde **SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-240">From **SurfaceMesh::Draw**:</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="c3a7c-241">Opciones de representación con la superficie de asignación</span><span class="sxs-lookup"><span data-stu-id="c3a7c-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="c3a7c-242">El ejemplo de código de asignación de superficie ofrece código para la representación sólo oclusión de datos de la malla de superficie y para la representación en pantalla de datos de la malla de superficie.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="c3a7c-243">Decide qué ruta de acceso - o bien ambos - dependen de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="c3a7c-244">Le guiaremos a través de ambas configuraciones en este documento.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="c3a7c-245">**Búferes de oclusión de representación de efecto holográfica**</span><span class="sxs-lookup"><span data-stu-id="c3a7c-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="c3a7c-246">Inicie desactivando el destino de presentación de la cámara virtual actual.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="c3a7c-247">Desde AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="c3a7c-248">Se trata de un paso de "representación previa".</span><span class="sxs-lookup"><span data-stu-id="c3a7c-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="c3a7c-249">En este caso, creamos un búfer de oclusión pidiendo el representador de malla para representar solo profundidad.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="c3a7c-250">En esta configuración, no Adjuntamos un destino de presentación y el representador de malla establece la etapa del sombreador de píxeles en **nullptr** para que la GPU no se molesta en dibujar píxeles.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="c3a7c-251">La geometría será rasterizada en el búfer de profundidad y detendrá la canalización de gráficos no existe.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="c3a7c-252">Podemos dibujar hologramas con una prueba de profundidad adicional en el búfer de oclusión de superficie de asignación.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="c3a7c-253">En este ejemplo de código, representamos los píxeles en el cubo de un color diferente si están detrás de una superficie.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="c3a7c-254">Desde AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-254">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="c3a7c-255">Basado en código de SpecialEffectPixelShader.hlsl:</span><span class="sxs-lookup"><span data-stu-id="c3a7c-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="c3a7c-256">**Nota:** Para nuestro **GatherDepthLess** rutina, vea el ejemplo de código de asignación de la superficie: SpecialEffectPixelShader.hlsl.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="c3a7c-257">**Datos de la malla de superficie de representación a la pantalla**</span><span class="sxs-lookup"><span data-stu-id="c3a7c-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="c3a7c-258">También podemos dibujar las mallas expuestas a los búferes de pantalla estéreo.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="c3a7c-259">Hemos optado por dibujar caras completas con la iluminación, pero tiene la libertad dibujar las tramas de alambres, procesar mallas antes de la representación, aplicar un mapa de textura y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="c3a7c-260">En este caso, nuestro ejemplo de código indica el representador de malla para dibujar la colección.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="c3a7c-261">Esta vez no especificamos un paso sólo profundidad, por lo que van a adjuntar a un sombreador de píxeles y completar la canalización de representación con los destinos que se especificó para la cámara virtual actual.</span><span class="sxs-lookup"><span data-stu-id="c3a7c-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="c3a7c-262">Vea también</span><span class="sxs-lookup"><span data-stu-id="c3a7c-262">See also</span></span>
* [<span data-ttu-id="c3a7c-263">Creación de un proyecto de DirectX holográfico</span><span class="sxs-lookup"><span data-stu-id="c3a7c-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="c3a7c-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="c3a7c-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
