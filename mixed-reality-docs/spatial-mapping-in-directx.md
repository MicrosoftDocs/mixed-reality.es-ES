---
title: Asignación espacial en DirectX
description: Explica cómo implementar la asignación espacial en la aplicación DirectX. Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de Plataforma universal de Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, asignación espacial, entorno, interacción, DirectX, winrt, API, código de ejemplo, UWP, SDK, tutorial
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550694"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="7274e-105">Asignación espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="7274e-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="7274e-106">En este tema se describe cómo implementar la [asignación espacial](spatial-mapping.md) en la aplicación DirectX.</span><span class="sxs-lookup"><span data-stu-id="7274e-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="7274e-107">Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de Plataforma universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="7274e-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="7274e-108">En este tema se usa el código del ejemplo de código UWP [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="7274e-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="7274e-109">Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="7274e-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7274e-110">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="7274e-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="7274e-111">Información general sobre el desarrollo de DirectX</span><span class="sxs-lookup"><span data-stu-id="7274e-111">DirectX development overview</span></span>

<span data-ttu-id="7274e-112">El desarrollo de aplicaciones nativas para la asignación espacial usa las API del espacio de nombres [Windows. imception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) .</span><span class="sxs-lookup"><span data-stu-id="7274e-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="7274e-113">Estas API proporcionan control total de la funcionalidad de asignación espacial, de una manera directamente análoga a las API de asignación espacial que expone [Unity](spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="7274e-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="7274e-114">API de percepción</span><span class="sxs-lookup"><span data-stu-id="7274e-114">Perception APIs</span></span>

<span data-ttu-id="7274e-115">Los tipos principales proporcionados para el desarrollo de asignación espacial son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="7274e-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="7274e-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) proporciona información sobre las superficies en regiones de espacio especificadas por la aplicación cerca del usuario, en forma de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="7274e-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="7274e-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describe una sola superficie espacial, que incluye un identificador único, el volumen de límite y la hora del último cambio.</span><span class="sxs-lookup"><span data-stu-id="7274e-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="7274e-118">Proporcionará un SpatialSurfaceMesh de forma asincrónica cuando se solicite.</span><span class="sxs-lookup"><span data-stu-id="7274e-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="7274e-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene parámetros que se usan para personalizar los objetos SpatialSurfaceMesh solicitados desde SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="7274e-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="7274e-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa los datos de la malla para una sola superficie espacial.</span><span class="sxs-lookup"><span data-stu-id="7274e-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="7274e-121">Los datos para las posiciones de los vértices, las normales de vértices y los índices de triángulo se encuentran en los objetos SpatialSurfaceMeshBuffer de miembro.</span><span class="sxs-lookup"><span data-stu-id="7274e-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="7274e-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) ajusta un solo tipo de datos de malla.</span><span class="sxs-lookup"><span data-stu-id="7274e-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="7274e-123">Al desarrollar una aplicación mediante estas API, el flujo del programa básico tendrá el siguiente aspecto (como se muestra en la aplicación de ejemplo que se describe a continuación):</span><span class="sxs-lookup"><span data-stu-id="7274e-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="7274e-124">**Configuración de SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="7274e-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="7274e-125">Llame a [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para asegurarse de que el usuario ha concedido permiso a la aplicación para usar las capacidades de asignación espacial del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7274e-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="7274e-126">Cree una instancia de un objeto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="7274e-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="7274e-127">Llame a [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar las regiones de espacio en las que quiere obtener información sobre las superficies espaciales.</span><span class="sxs-lookup"><span data-stu-id="7274e-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="7274e-128">Puede modificar estas regiones en el futuro con solo volver a llamar a esta función.</span><span class="sxs-lookup"><span data-stu-id="7274e-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="7274e-129">Cada región se especifica mediante un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="7274e-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="7274e-130">Regístrese para el evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , que se activará siempre que haya nueva información disponible sobre las superficies espaciales en las regiones de espacio que haya especificado.</span><span class="sxs-lookup"><span data-stu-id="7274e-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="7274e-131">**Procesar eventos de ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="7274e-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="7274e-132">En el controlador de eventos, llame a [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para recibir un mapa de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="7274e-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="7274e-133">Con esta asignación, puede actualizar los registros de las superficies espaciales que [existen en el entorno del usuario](spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="7274e-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="7274e-134">Para cada objeto SpatialSurfaceInfo, puede consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) para determinar las extensiones espaciales de la superficie, expresada en un [sistema de coordenadas espaciales](coordinate-systems.md) de su elección.</span><span class="sxs-lookup"><span data-stu-id="7274e-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="7274e-135">Si decide solicitar la malla para una superficie espacial, llame a [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="7274e-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="7274e-136">Puede proporcionar opciones que especifiquen la densidad deseada de triángulos y el formato de los datos de malla devueltos.</span><span class="sxs-lookup"><span data-stu-id="7274e-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="7274e-137">**Red de recepción y proceso**</span><span class="sxs-lookup"><span data-stu-id="7274e-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="7274e-138">Cada llamada a TryComputeLatestMeshAsync aysnchronously devolverá un objeto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="7274e-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="7274e-139">A partir de este objeto, puede tener acceso a los objetos SpatialSurfaceMeshBuffer contenidos para tener acceso a los índices de triángulo, las posiciones de los vértices y las normales de vértices (si se solicitan) de la malla.</span><span class="sxs-lookup"><span data-stu-id="7274e-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="7274e-140">Estos datos estarán en un formato directamente compatible con las [API de Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usadas para representar mallas.</span><span class="sxs-lookup"><span data-stu-id="7274e-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="7274e-141">Desde aquí, la aplicación puede realizar el análisis o el [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla y usarlo para la [representación](spatial-mapping.md#rendering) y la raycasting física [y la colisión](spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="7274e-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="7274e-142">Un detalle importante a tener en cuenta es que debe aplicar una escala a las posiciones del vértice de la malla (por ejemplo, en el sombreador de vértices que se usa para representar las mallas), para convertirlas desde las unidades de enteros optimizadas en las que se almacenan en el búfer, hasta los medidores.</span><span class="sxs-lookup"><span data-stu-id="7274e-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="7274e-143">Puede recuperar esta escala llamando a [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="7274e-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="7274e-144">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="7274e-144">Troubleshooting</span></span>
* <span data-ttu-id="7274e-145">No olvide escalar las posiciones de los vértices de malla en el sombreador de vértices mediante la escala devuelta por [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="7274e-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="7274e-146">Tutorial de ejemplo de código de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="7274e-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="7274e-147">El ejemplo de código de [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) incluye código que puede usar para empezar a cargar mallas de superficie en la aplicación, incluida la infraestructura para la administración y representación de mallas de superficie.</span><span class="sxs-lookup"><span data-stu-id="7274e-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="7274e-148">Ahora, veremos cómo agregar funcionalidad de asignación de superficie a la aplicación DirectX.</span><span class="sxs-lookup"><span data-stu-id="7274e-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="7274e-149">Puede Agregar este código a su proyecto de [plantilla de aplicación de Windows Holographic](creating-a-holographic-directx-project.md) , o bien, puede seguir el código de ejemplo mencionado anteriormente para examinarlo.</span><span class="sxs-lookup"><span data-stu-id="7274e-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="7274e-150">Este ejemplo de código se basa en la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="7274e-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="7274e-151">Configuración de la aplicación para usar la funcionalidad spatialPerception</span><span class="sxs-lookup"><span data-stu-id="7274e-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="7274e-152">La aplicación debe poder usar la capacidad de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="7274e-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="7274e-153">Esto es necesario porque la malla espacial es una representación del entorno del usuario, que puede considerarse como datos privados.</span><span class="sxs-lookup"><span data-stu-id="7274e-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="7274e-154">Declare esta funcionalidad en el archivo package. appxmanifest de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7274e-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="7274e-155">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7274e-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="7274e-156">La funcionalidad proviene del espacio de nombres **uap2** .</span><span class="sxs-lookup"><span data-stu-id="7274e-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="7274e-157">Para obtener acceso a este espacio de nombres en el manifiesto, inclúyalo como un atributo *xlmns* en &lt;el elemento > del paquete.</span><span class="sxs-lookup"><span data-stu-id="7274e-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="7274e-158">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7274e-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="7274e-159">Comprobar la compatibilidad de las características de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="7274e-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="7274e-160">Windows Mixed Reality es compatible con una amplia gama de dispositivos, incluidos los dispositivos que no admiten la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="7274e-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="7274e-161">Si la aplicación puede usar la asignación espacial, o debe usar la asignación espacial, para proporcionar la funcionalidad, debe comprobar para asegurarse de que se admite la asignación espacial antes de intentar usarla.</span><span class="sxs-lookup"><span data-stu-id="7274e-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="7274e-162">Por ejemplo, si la aplicación de realidad mixta requiere la asignación espacial, debería mostrar un mensaje al efecto si un usuario intenta ejecutarlo en un dispositivo sin asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="7274e-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="7274e-163">O bien, es posible que la aplicación pueda presentar su propio entorno virtual en lugar del entorno del usuario, lo que proporciona una experiencia similar a lo que sucedería si la asignación espacial estuviera disponible.</span><span class="sxs-lookup"><span data-stu-id="7274e-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="7274e-164">En cualquier caso, esta API permite que la aplicación tenga en cuenta Cuándo no obtendrá los datos de asignación espacial y responderá de la manera adecuada.</span><span class="sxs-lookup"><span data-stu-id="7274e-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="7274e-165">Para comprobar la compatibilidad con la asignación espacial en el dispositivo actual, primero asegúrese de que el contrato UWP se encuentra en el nivel 4 o superior y, a continuación, llame a SpatialSurfaceObserver:: IsSupported ().</span><span class="sxs-lookup"><span data-stu-id="7274e-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="7274e-166">Aquí se muestra cómo hacerlo en el contexto del ejemplo de código de [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="7274e-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="7274e-167">La compatibilidad se comprueba justo antes de solicitar acceso.</span><span class="sxs-lookup"><span data-stu-id="7274e-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="7274e-168">La API SpatialSurfaceObserver:: IsSupported () está disponible a partir de la versión 15063 del SDK.</span><span class="sxs-lookup"><span data-stu-id="7274e-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="7274e-169">Si es necesario, redestinar el proyecto a la versión 15063 de la plataforma antes de usar esta API.</span><span class="sxs-lookup"><span data-stu-id="7274e-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="7274e-170">Tenga en cuenta que cuando el contrato de UWP es inferior al nivel 4, la aplicación debe continuar como si el dispositivo fuera capaz de realizar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="7274e-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="7274e-171">Solicitar acceso a los datos de asignación espacial</span><span class="sxs-lookup"><span data-stu-id="7274e-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="7274e-172">La aplicación necesita solicitar permiso para tener acceso a los datos de asignación espacial antes de intentar crear observadores de superficie.</span><span class="sxs-lookup"><span data-stu-id="7274e-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="7274e-173">Este es un ejemplo basado en el ejemplo de código de asignación de Surface, con más detalles que se proporcionan más adelante en esta página:</span><span class="sxs-lookup"><span data-stu-id="7274e-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="7274e-174">Creación de un observador de superficie</span><span class="sxs-lookup"><span data-stu-id="7274e-174">Create a surface observer</span></span>

<span data-ttu-id="7274e-175">El espacio de nombres **Windows::P erception:: Spatial:: Surfaces** incluye la clase [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , que observa uno o más volúmenes que se especifican en un [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="7274e-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="7274e-176">Use una instancia de [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) para tener acceso a los datos de malla superficial en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="7274e-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="7274e-177">Desde **AppMain. h**:</span><span class="sxs-lookup"><span data-stu-id="7274e-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="7274e-178">Como se indicó en la sección anterior, debe solicitar acceso a los datos de asignación espacial antes de que la aplicación pueda usarlos.</span><span class="sxs-lookup"><span data-stu-id="7274e-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="7274e-179">Este acceso se concede automáticamente en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7274e-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="7274e-180">A continuación, debe configurar el observador de superficie para observar un volumen de límite específico.</span><span class="sxs-lookup"><span data-stu-id="7274e-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="7274e-181">En este caso, observamos un cuadro que es 20x20x5 metros, centrado en el origen del sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="7274e-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="7274e-182">Tenga en cuenta que, en su lugar, puede establecer varios volúmenes de límite.</span><span class="sxs-lookup"><span data-stu-id="7274e-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="7274e-183">*Este es pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="7274e-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="7274e-184">También es posible usar otras formas de límite, como un frustum de vista, o un cuadro de límite que no esté alineado con el eje.</span><span class="sxs-lookup"><span data-stu-id="7274e-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="7274e-185">*Este es pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="7274e-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="7274e-186">Si la aplicación tiene que hacer algo diferente cuando los datos de la asignación de superficie no están disponibles, puede escribir código para responder al caso en el que no se **permite** el [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) ; por ejemplo, no se permitirá en equipos con acceso envolvente dispositivos conectados porque estos dispositivos no tienen hardware para la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="7274e-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="7274e-187">En el caso de estos dispositivos, debe basarse en la fase espacial para obtener información sobre el entorno del usuario y la configuración del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7274e-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="7274e-188">Inicializar y actualizar la colección de mallas de Surface</span><span class="sxs-lookup"><span data-stu-id="7274e-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="7274e-189">Si el observador de superficie se creó correctamente, podemos continuar para inicializar la colección de malla de Surface.</span><span class="sxs-lookup"><span data-stu-id="7274e-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="7274e-190">Aquí se usa la API de modelo de extracción para obtener el conjunto actual de superficies observadas de inmediato:</span><span class="sxs-lookup"><span data-stu-id="7274e-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="7274e-191">También hay un modelo de inserciones disponible para obtener datos de malla de superficie.</span><span class="sxs-lookup"><span data-stu-id="7274e-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="7274e-192">Puede diseñar la aplicación para que use solo el modelo de extracción si lo desea, en cuyo caso sondeará los datos cada vez, por ejemplo, una vez por fotograma o durante un período de tiempo específico, como durante la configuración del juego.</span><span class="sxs-lookup"><span data-stu-id="7274e-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="7274e-193">Si es así, el código anterior es lo que necesita.</span><span class="sxs-lookup"><span data-stu-id="7274e-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="7274e-194">En nuestro ejemplo de código, decidimos demostrar el uso de ambos modelos con fines pedagógicos.</span><span class="sxs-lookup"><span data-stu-id="7274e-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="7274e-195">En este caso, se suscribe a un evento para recibir datos de malla superficial actualizados siempre que el sistema reconoce un cambio.</span><span class="sxs-lookup"><span data-stu-id="7274e-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="7274e-196">Nuestro ejemplo de código también está configurado para responder a estos eventos.</span><span class="sxs-lookup"><span data-stu-id="7274e-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="7274e-197">Veamos cómo hacemos esto.</span><span class="sxs-lookup"><span data-stu-id="7274e-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="7274e-198">**NOTA:** Es posible que esta no sea la forma más eficaz para que la aplicación controle los datos de malla.</span><span class="sxs-lookup"><span data-stu-id="7274e-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="7274e-199">Este código se escribe para mayor claridad y no está optimizado.</span><span class="sxs-lookup"><span data-stu-id="7274e-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="7274e-200">Los datos de la malla de superficie se proporcionan en un mapa de solo lectura que almacena los objetos [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) mediante [Platform:: GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de clave.</span><span class="sxs-lookup"><span data-stu-id="7274e-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="7274e-201">Para procesar estos datos, buscamos primero los valores de clave que no están en nuestra colección.</span><span class="sxs-lookup"><span data-stu-id="7274e-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="7274e-202">Más adelante en este tema se mostrarán los detalles sobre cómo se almacenan los datos en la aplicación de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7274e-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="7274e-203">También tenemos que quitar las mallas de superficie que se encuentran en la colección de mallas de Surface, pero que ya no están en la colección de sistemas.</span><span class="sxs-lookup"><span data-stu-id="7274e-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="7274e-204">Para ello, es necesario hacer algo similar a lo que se acaba de decir para agregar y actualizar las mallas. se crea un bucle en la colección de la aplicación y se comprueba si el **GUID** que tenemos está en la colección del sistema.</span><span class="sxs-lookup"><span data-stu-id="7274e-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="7274e-205">Si no está en la colección del sistema, lo quitamos de nuestra.</span><span class="sxs-lookup"><span data-stu-id="7274e-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="7274e-206">Desde nuestro controlador de eventos en AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="7274e-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="7274e-207">La implementación de la eliminación de mallas en RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="7274e-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="7274e-208">Adquisición y uso de búferes de datos de malla de superficie</span><span class="sxs-lookup"><span data-stu-id="7274e-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="7274e-209">Obtener la información de la malla de superficie era tan sencillo como extraer una recopilación de datos y procesar las actualizaciones en esa colección.</span><span class="sxs-lookup"><span data-stu-id="7274e-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="7274e-210">Ahora, entraremos en detalles sobre cómo puede usar los datos.</span><span class="sxs-lookup"><span data-stu-id="7274e-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="7274e-211">En nuestro ejemplo de código, decidimos usar las mallas de superficie para la representación.</span><span class="sxs-lookup"><span data-stu-id="7274e-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="7274e-212">Este es un escenario común para los hologramas de occluding detrás de las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="7274e-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="7274e-213">También puede representar las mallas, o presentar versiones procesadas de ellas, para mostrar al usuario qué áreas de la sala se analizan antes de empezar a proporcionar la funcionalidad de la aplicación o el juego.</span><span class="sxs-lookup"><span data-stu-id="7274e-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="7274e-214">En el ejemplo de código se inicia el proceso cuando recibe actualizaciones de malla de superficie del controlador de eventos que se ha descrito en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="7274e-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="7274e-215">La línea de código importante en esta función es la llamada para actualizar la *malla*de la superficie: en este momento ya hemos procesado la información de la malla y estamos a punto de obtener los datos de los vértices y del índice para su uso, como se observa.</span><span class="sxs-lookup"><span data-stu-id="7274e-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="7274e-216">Desde RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="7274e-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="7274e-217">Nuestro código de ejemplo está diseñado para que una clase de datos, **SurfaceMesh**, controle el procesamiento y la representación de datos de malla.</span><span class="sxs-lookup"><span data-stu-id="7274e-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="7274e-218">Estas mallas son lo que el **RealtimeSurfaceMeshRenderer** mantiene realmente un mapa.</span><span class="sxs-lookup"><span data-stu-id="7274e-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="7274e-219">Cada una de ellas tiene una referencia a la SpatialSurfaceMesh de la que procede y la usamos siempre que necesitamos acceder al vértice de la malla o a los búferes de índice, u obtener una transformación para la malla.</span><span class="sxs-lookup"><span data-stu-id="7274e-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="7274e-220">Por ahora, marcamos la malla como necesaria para una actualización.</span><span class="sxs-lookup"><span data-stu-id="7274e-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="7274e-221">Desde SurfaceMesh. cpp:</span><span class="sxs-lookup"><span data-stu-id="7274e-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="7274e-222">La próxima vez que se pida que se dibuje la malla, comprobará primero la marca.</span><span class="sxs-lookup"><span data-stu-id="7274e-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="7274e-223">Si se necesita una actualización, los búferes de vértices y de índices se actualizarán en la GPU.</span><span class="sxs-lookup"><span data-stu-id="7274e-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="7274e-224">En primer lugar, se adquieren los búferes de datos sin procesar:</span><span class="sxs-lookup"><span data-stu-id="7274e-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="7274e-225">A continuación, creamos búferes de dispositivo Direct3D con los datos de la malla que proporciona HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7274e-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="7274e-226">**NOTA:** Para la función auxiliar CreateDirectXBuffer utilizada en el fragmento de código anterior, vea el ejemplo de código de asignación de superficie: SurfaceMesh. cpp, GetDataFromIBuffer. h.</span><span class="sxs-lookup"><span data-stu-id="7274e-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="7274e-227">Ahora se ha completado la creación de recursos de dispositivo y se considera que la malla está cargada y lista para su actualización y representación.</span><span class="sxs-lookup"><span data-stu-id="7274e-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="7274e-228">Actualización y representación de mallas de superficie</span><span class="sxs-lookup"><span data-stu-id="7274e-228">Update and render surface meshes</span></span>

<span data-ttu-id="7274e-229">Nuestra clase SurfaceMesh tiene una función de actualización especializada.</span><span class="sxs-lookup"><span data-stu-id="7274e-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="7274e-230">Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tiene su propia transformación y en nuestro ejemplo se usa el sistema de coordenadas actual para que nuestro **SpatialStationaryReferenceFrame** adquiera la transformación.</span><span class="sxs-lookup"><span data-stu-id="7274e-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="7274e-231">A continuación, actualiza el búfer de constantes del modelo en la GPU.</span><span class="sxs-lookup"><span data-stu-id="7274e-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="7274e-232">Cuando es el momento de representar mallas de superficie, realizamos algún trabajo de preparación antes de representar la colección.</span><span class="sxs-lookup"><span data-stu-id="7274e-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="7274e-233">Se configura la canalización del sombreador para la configuración de representación actual y se configura la etapa del ensamblador de entrada.</span><span class="sxs-lookup"><span data-stu-id="7274e-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="7274e-234">Tenga en cuenta que la clase de aplicación auxiliar de cámara holográfica **CameraResources. cpp** ya ha configurado el búfer de constantes de vista/proyección en este momento.</span><span class="sxs-lookup"><span data-stu-id="7274e-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="7274e-235">Desde **RealtimeSurfaceMeshRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="7274e-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="7274e-236">Una vez hecho esto, se crea un bucle en nuestras mallas y se indica a cada uno que se dibuje a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="7274e-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="7274e-237">**NOTA:** Este código de ejemplo no está optimizado para usar cualquier tipo de selección de frustum, pero debe incluir esta característica en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7274e-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="7274e-238">Las mallas individuales son responsables de configurar el búfer de vértices y de índices, STRIDE y el búfer de constantes de transformación de modelo.</span><span class="sxs-lookup"><span data-stu-id="7274e-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="7274e-239">Al igual que con el cubo giratorio en la plantilla de aplicación de Windows Holographic, se representan en búferes de Stereoscopic mediante la creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="7274e-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="7274e-240">Desde **SurfaceMesh::D RAW**:</span><span class="sxs-lookup"><span data-stu-id="7274e-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="7274e-241">Opciones de representación con asignación de superficie</span><span class="sxs-lookup"><span data-stu-id="7274e-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="7274e-242">El ejemplo de código de asignación de superficie ofrece código para la representación solo de oclusión de datos de malla de superficie y para la representación en pantalla de datos de malla de superficie.</span><span class="sxs-lookup"><span data-stu-id="7274e-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="7274e-243">La ruta de acceso que elija o ambas dependerá de su aplicación.</span><span class="sxs-lookup"><span data-stu-id="7274e-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="7274e-244">Analizaremos ambas configuraciones en este documento.</span><span class="sxs-lookup"><span data-stu-id="7274e-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="7274e-245">**Representación de búferes de oclusión para el efecto holográfica**</span><span class="sxs-lookup"><span data-stu-id="7274e-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="7274e-246">Empiece por borrar la vista de destino de representación de la cámara virtual actual.</span><span class="sxs-lookup"><span data-stu-id="7274e-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="7274e-247">Desde AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="7274e-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="7274e-248">Se trata de un paso de "representación previa".</span><span class="sxs-lookup"><span data-stu-id="7274e-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="7274e-249">En este caso, se crea un búfer de oclusión solicitando que el representador de la malla represente solo la profundidad.</span><span class="sxs-lookup"><span data-stu-id="7274e-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="7274e-250">En esta configuración, no adjuntamos una vista de destino de representación y el representador de malla establece la etapa del sombreador de píxeles en **nullptr** para que la GPU no se moleste en dibujar píxeles.</span><span class="sxs-lookup"><span data-stu-id="7274e-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="7274e-251">La geometría se rasterizará en el búfer de profundidad y la canalización de gráficos se detendrá allí.</span><span class="sxs-lookup"><span data-stu-id="7274e-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="7274e-252">Podemos dibujar hologramas con una prueba de profundidad adicional en el búfer de oclusión de asignación de superficie.</span><span class="sxs-lookup"><span data-stu-id="7274e-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="7274e-253">En este ejemplo de código, se representan píxeles en el cubo con un color diferente si están detrás de una superficie.</span><span class="sxs-lookup"><span data-stu-id="7274e-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="7274e-254">Desde AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="7274e-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="7274e-255">En función del código de SpecialEffectPixelShader. HLSL:</span><span class="sxs-lookup"><span data-stu-id="7274e-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="7274e-256">**Nota:** Para nuestra rutina **GatherDepthLess** , consulte el ejemplo de código de asignación de superficie: SpecialEffectPixelShader. HLSL.</span><span class="sxs-lookup"><span data-stu-id="7274e-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="7274e-257">**Representación de datos de malla de superficie en la pantalla**</span><span class="sxs-lookup"><span data-stu-id="7274e-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="7274e-258">También podemos dibujar las mallas de superficie en los búferes de pantalla estéreo.</span><span class="sxs-lookup"><span data-stu-id="7274e-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="7274e-259">Decidimos dibujar caras completas con iluminación, pero tiene la libertad de dibujar tramas, procesar mallas antes de la representación, aplicar un mapa de textura, etc.</span><span class="sxs-lookup"><span data-stu-id="7274e-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="7274e-260">Aquí, nuestro ejemplo de código indica al representador de malla que dibuje la colección.</span><span class="sxs-lookup"><span data-stu-id="7274e-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="7274e-261">Esta vez no se especifica un paso de solo profundidad, por lo que se conectará un sombreador de píxeles y se completará la canalización de representación mediante los destinos que se especificaron para la cámara virtual actual.</span><span class="sxs-lookup"><span data-stu-id="7274e-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7274e-262">Vea también</span><span class="sxs-lookup"><span data-stu-id="7274e-262">See also</span></span>
* [<span data-ttu-id="7274e-263">Creación de un proyecto de DirectX holográfico</span><span class="sxs-lookup"><span data-stu-id="7274e-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="7274e-264">Windows. Perception. Spatial API</span><span class="sxs-lookup"><span data-stu-id="7274e-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
