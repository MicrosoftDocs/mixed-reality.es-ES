---
title: Asignación espacial en DirectX
description: Explica cómo implementar la asignación espacial en la aplicación DirectX. Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de Plataforma universal de Windows.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, asignación espacial, entorno, interacción, DirectX, winrt, API, código de ejemplo, UWP, SDK, tutorial
ms.openlocfilehash: 456fcf1c00e23a287a741673e94b3f8d2d2d346c
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375822"
---
# <a name="spatial-mapping-in-directx"></a>Asignación espacial en DirectX

En este tema se describe cómo implementar la [asignación espacial](spatial-mapping.md) en la aplicación DirectX. Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de Plataforma universal de Windows.

En este tema se usa el código del ejemplo de código UWP [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Asignación espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>Información general sobre el desarrollo de DirectX

El desarrollo de aplicaciones nativas para la asignación espacial usa las API del espacio de nombres [Windows. imception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) . Estas API proporcionan control total de la funcionalidad de asignación espacial, de una manera directamente análoga a las API de asignación espacial que expone [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>API de percepción

Los tipos principales proporcionados para el desarrollo de asignación espacial son los siguientes:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) proporciona información sobre las superficies en regiones de espacio especificadas por la aplicación cerca del usuario, en forma de objetos SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describe una sola superficie espacial, que incluye un identificador único, el volumen de límite y la hora del último cambio. Proporcionará un SpatialSurfaceMesh de forma asincrónica cuando se solicite.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene parámetros que se usan para personalizar los objetos SpatialSurfaceMesh solicitados desde SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa los datos de la malla para una sola superficie espacial. Los datos para las posiciones de los vértices, las normales de vértices y los índices de triángulo se encuentran en los objetos SpatialSurfaceMeshBuffer de miembro.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) ajusta un solo tipo de datos de malla.

Al desarrollar una aplicación mediante estas API, el flujo del programa básico tendrá el siguiente aspecto (como se muestra en la aplicación de ejemplo que se describe a continuación):
- **Configuración de SpatialSurfaceObserver**
  - Llame a [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para asegurarse de que el usuario ha concedido permiso a la aplicación para usar las capacidades de asignación espacial del dispositivo.
  - Cree una instancia de un objeto SpatialSurfaceObserver.
  - Llame a [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar las regiones de espacio en las que quiere obtener información sobre las superficies espaciales. Puede modificar estas regiones en el futuro con solo volver a llamar a esta función. Cada región se especifica mediante un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Regístrese para el evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , que se activará siempre que haya nueva información disponible sobre las superficies espaciales en las regiones de espacio que haya especificado.
- **Procesar eventos de ObservedSurfacesChanged**
  - En el controlador de eventos, llame a [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para recibir un mapa de objetos SpatialSurfaceInfo. Con esta asignación, puede actualizar los registros de las superficies espaciales que [existen en el entorno del usuario](spatial-mapping.md#mesh-caching).
  - Para cada objeto SpatialSurfaceInfo, puede consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) para determinar las extensiones espaciales de la superficie, expresada en un [sistema de coordenadas espaciales](coordinate-systems.md) de su elección.
  - Si decide solicitar la malla para una superficie espacial, llame a [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Puede proporcionar opciones que especifiquen la densidad deseada de triángulos y el formato de los datos de malla devueltos.
- **Red de recepción y proceso**
  - Cada llamada a TryComputeLatestMeshAsync aysnchronously devolverá un objeto SpatialSurfaceMesh.
  - A partir de este objeto, puede tener acceso a los objetos SpatialSurfaceMeshBuffer contenidos para tener acceso a los índices de triángulo, las posiciones de los vértices y las normales de vértices (si se solicitan) de la malla. Estos datos estarán en un formato directamente compatible con las [API de Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usadas para representar mallas.
  - Desde aquí, la aplicación puede realizar el análisis o el [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla y usarlo para la [representación](spatial-mapping.md#rendering) y la raycasting física [y la colisión](spatial-mapping.md#raycasting-and-collision).
  - Un detalle importante a tener en cuenta es que debe aplicar una escala a las posiciones del vértice de la malla (por ejemplo, en el sombreador de vértices que se usa para representar las mallas), para convertirlas desde las unidades de enteros optimizadas en las que se almacenan en el búfer, hasta los medidores. Puede recuperar esta escala llamando a [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Solucionar problemas
* No olvide escalar las posiciones de los vértices de malla en el sombreador de vértices mediante la escala devuelta por [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Tutorial de ejemplo de código de asignación espacial

El ejemplo de código de [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) incluye código que puede usar para empezar a cargar mallas de superficie en la aplicación, incluida la infraestructura para la administración y representación de mallas de superficie.

Ahora, veremos cómo agregar funcionalidad de asignación de superficie a la aplicación DirectX. Puede Agregar este código a su proyecto de [plantilla de aplicación de Windows Holographic](creating-a-holographic-directx-project.md) , o bien, puede seguir el código de ejemplo mencionado anteriormente para examinarlo. Este ejemplo de código se basa en la plantilla de aplicación de Windows Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configuración de la aplicación para usar la funcionalidad spatialPerception

La aplicación debe poder usar la capacidad de asignación espacial. Esto es necesario porque la malla espacial es una representación del entorno del usuario, que puede considerarse como datos privados. Declare esta funcionalidad en el archivo package. appxmanifest de la aplicación. A continuación te mostramos un ejemplo:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funcionalidad proviene del espacio de nombres **uap2** . Para obtener acceso a este espacio de nombres en el manifiesto, inclúyalo como un atributo *xlmns* en el elemento &lt;paquete >. A continuación te mostramos un ejemplo:

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Comprobar la compatibilidad de las características de asignación espacial

Windows Mixed Reality es compatible con una amplia gama de dispositivos, incluidos los dispositivos que no admiten la asignación espacial. Si la aplicación puede usar la asignación espacial, o debe usar la asignación espacial, para proporcionar la funcionalidad, debe comprobar para asegurarse de que se admite la asignación espacial antes de intentar usarla. Por ejemplo, si la aplicación de realidad mixta requiere la asignación espacial, debería mostrar un mensaje al efecto si un usuario intenta ejecutarlo en un dispositivo sin asignación espacial. O bien, es posible que la aplicación pueda presentar su propio entorno virtual en lugar del entorno del usuario, lo que proporciona una experiencia similar a lo que sucedería si la asignación espacial estuviera disponible. En cualquier caso, esta API permite que la aplicación tenga en cuenta Cuándo no obtendrá los datos de asignación espacial y responderá de la manera adecuada.

Para comprobar la compatibilidad con la asignación espacial en el dispositivo actual, primero asegúrese de que el contrato UWP se encuentra en el nivel 4 o superior y, a continuación, llame a SpatialSurfaceObserver:: IsSupported (). Aquí se muestra cómo hacerlo en el contexto del ejemplo de código de [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) . La compatibilidad se comprueba justo antes de solicitar acceso.

La API SpatialSurfaceObserver:: IsSupported () está disponible a partir de la versión 15063 del SDK. Si es necesario, redestinar el proyecto a la versión 15063 de la plataforma antes de usar esta API.

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

Tenga en cuenta que cuando el contrato de UWP es inferior al nivel 4, la aplicación debe continuar como si el dispositivo fuera capaz de realizar la asignación espacial.

### <a name="request-access-to-spatial-mapping-data"></a>Solicitar acceso a los datos de asignación espacial

La aplicación necesita solicitar permiso para tener acceso a los datos de asignación espacial antes de intentar crear observadores de superficie. Este es un ejemplo basado en el ejemplo de código de asignación de Surface, con más detalles que se proporcionan más adelante en esta página:

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

### <a name="create-a-surface-observer"></a>Creación de un observador de superficie

El espacio de nombres **Windows::P erception:: Spatial:: Surfaces** incluye la clase [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , que observa uno o más volúmenes que se especifican en un [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Use una instancia de [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) para tener acceso a los datos de malla superficial en tiempo real.

Desde **AppMain. h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Como se indicó en la sección anterior, debe solicitar acceso a los datos de asignación espacial antes de que la aplicación pueda usarlos. Este acceso se concede automáticamente en HoloLens.

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

A continuación, debe configurar el observador de superficie para observar un volumen de límite específico. En este caso, observamos un cuadro que es 20x20x5 metros, centrado en el origen del sistema de coordenadas.

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

Tenga en cuenta que, en su lugar, puede establecer varios volúmenes de límite.

*Este es pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

También es posible usar otras formas de límite, como un frustum de vista, o un cuadro de límite que no esté alineado con el eje.

*Este es pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Si la aplicación necesita hacer algo diferente cuando los datos de la asignación de superficie no están disponibles, puede escribir código para responder al caso en el que no se **permite** el [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) ; por ejemplo, no se permitirá en equipos con dispositivos envolventes conectados porque estos dispositivos no tienen hardware para la asignación espacial. En el caso de estos dispositivos, debe basarse en la fase espacial para obtener información sobre el entorno del usuario y la configuración del dispositivo.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inicializar y actualizar la colección de mallas de Surface

Si el observador de superficie se creó correctamente, podemos continuar para inicializar la colección de malla de Surface. Aquí se usa la API de modelo de extracción para obtener el conjunto actual de superficies observadas de inmediato:

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

También hay un modelo de inserciones disponible para obtener datos de malla de superficie. Puede diseñar la aplicación para que use solo el modelo de extracción si lo desea, en cuyo caso sondeará los datos cada vez, por ejemplo, una vez por fotograma o durante un período de tiempo específico, como durante la configuración del juego. Si es así, el código anterior es lo que necesita.

En nuestro ejemplo de código, decidimos demostrar el uso de ambos modelos con fines pedagógicos. En este caso, se suscribe a un evento para recibir datos de malla superficial actualizados siempre que el sistema reconoce un cambio.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Nuestro ejemplo de código también está configurado para responder a estos eventos. Veamos cómo hacemos esto.

**Nota:** Es posible que esta no sea la forma más eficaz para que la aplicación controle los datos de malla. Este código se escribe para mayor claridad y no está optimizado.

Los datos de la malla de superficie se proporcionan en un mapa de solo lectura que almacena los objetos [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) mediante [Platform:: GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de clave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Para procesar estos datos, buscamos primero los valores de clave que no están en nuestra colección. Más adelante en este tema se mostrarán los detalles sobre cómo se almacenan los datos en la aplicación de ejemplo.

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

También tenemos que quitar las mallas de superficie que se encuentran en la colección de mallas de Surface, pero que ya no están en la colección de sistemas. Para ello, es necesario hacer algo similar a lo que se acaba de decir para agregar y actualizar las mallas. se crea un bucle en la colección de la aplicación y se comprueba si el **GUID** que tenemos está en la colección del sistema. Si no está en la colección del sistema, lo quitamos de nuestra.

Desde nuestro controlador de eventos en AppMain. cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

La implementación de la eliminación de mallas en RealtimeSurfaceMeshRenderer. cpp:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Adquisición y uso de búferes de datos de malla de superficie

Obtener la información de la malla de superficie era tan sencillo como extraer una recopilación de datos y procesar las actualizaciones en esa colección. Ahora, entraremos en detalles sobre cómo puede usar los datos.

En nuestro ejemplo de código, decidimos usar las mallas de superficie para la representación. Este es un escenario común para los hologramas de occluding detrás de las superficies del mundo real. También puede representar las mallas, o presentar versiones procesadas de ellas, para mostrar al usuario qué áreas de la sala se analizan antes de empezar a proporcionar la funcionalidad de la aplicación o el juego.

En el ejemplo de código se inicia el proceso cuando recibe actualizaciones de malla de superficie del controlador de eventos que se ha descrito en la sección anterior. La línea de código importante en esta función es la llamada para actualizar la *malla*de la superficie: en este momento ya hemos procesado la información de la malla y estamos a punto de obtener los datos de los vértices y del índice para su uso, como se observa.

Desde RealtimeSurfaceMeshRenderer. cpp:

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

Nuestro código de ejemplo está diseñado para que una clase de datos, **SurfaceMesh**, controle el procesamiento y la representación de datos de malla. Estas mallas son lo que el **RealtimeSurfaceMeshRenderer** mantiene realmente un mapa. Cada una de ellas tiene una referencia a la SpatialSurfaceMesh de la que procede y la usamos siempre que necesitamos acceder al vértice de la malla o a los búferes de índice, u obtener una transformación para la malla. Por ahora, marcamos la malla como necesaria para una actualización.

Desde SurfaceMesh. cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

La próxima vez que se pida que se dibuje la malla, comprobará primero la marca. Si se necesita una actualización, los búferes de vértices y de índices se actualizarán en la GPU.

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

En primer lugar, se adquieren los búferes de datos sin procesar:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

A continuación, creamos búferes de dispositivo Direct3D con los datos de la malla que proporciona HoloLens:

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

**Nota:** Para la función auxiliar CreateDirectXBuffer utilizada en el fragmento de código anterior, vea el ejemplo de código de asignación de superficie: SurfaceMesh. cpp, GetDataFromIBuffer. h. Ahora se ha completado la creación de recursos de dispositivo y se considera que la malla está cargada y lista para su actualización y representación.

### <a name="update-and-render-surface-meshes"></a>Actualización y representación de mallas de superficie

Nuestra clase SurfaceMesh tiene una función de actualización especializada. Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tiene su propia transformación y en nuestro ejemplo se usa el sistema de coordenadas actual para que nuestro **SpatialStationaryReferenceFrame** adquiera la transformación. A continuación, actualiza el búfer de constantes del modelo en la GPU.

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

Cuando es el momento de representar mallas de superficie, realizamos algún trabajo de preparación antes de representar la colección. Se configura la canalización del sombreador para la configuración de representación actual y se configura la etapa del ensamblador de entrada. Tenga en cuenta que la clase de aplicación auxiliar de cámara holográfica **CameraResources. cpp** ya ha configurado el búfer de constantes de vista/proyección en este momento.

Desde **RealtimeSurfaceMeshRenderer:: Render**:

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

Una vez hecho esto, se crea un bucle en nuestras mallas y se indica a cada uno que se dibuje a sí mismo. **Nota:** Este código de ejemplo no está optimizado para usar cualquier tipo de selección de frustum, pero debe incluir esta característica en la aplicación.

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

Las mallas individuales son responsables de configurar el búfer de vértices y de índices, STRIDE y el búfer de constantes de transformación de modelo. Al igual que con el cubo giratorio en la plantilla de aplicación de Windows Holographic, se representan en búferes de Stereoscopic mediante la creación de instancias.

Desde **SurfaceMesh::D RAW**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Opciones de representación con asignación de superficie

El ejemplo de código de asignación de superficie ofrece código para la representación solo de oclusión de datos de malla de superficie y para la representación en pantalla de datos de malla de superficie. La ruta de acceso que elija o ambas dependerá de su aplicación. Analizaremos ambas configuraciones en este documento.

**Representación de búferes de oclusión para el efecto holográfica**

Empiece por borrar la vista de destino de representación de la cámara virtual actual.

Desde AppMain. cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Se trata de un paso de "representación previa". En este caso, se crea un búfer de oclusión solicitando que el representador de la malla represente solo la profundidad. En esta configuración, no adjuntamos una vista de destino de representación y el representador de malla establece la etapa del sombreador de píxeles en **nullptr** para que la GPU no se moleste en dibujar píxeles. La geometría se rasterizará en el búfer de profundidad y la canalización de gráficos se detendrá allí.

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

Podemos dibujar hologramas con una prueba de profundidad adicional en el búfer de oclusión de asignación de superficie. En este ejemplo de código, se representan píxeles en el cubo con un color diferente si están detrás de una superficie.

Desde AppMain. cpp:

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

En función del código de SpecialEffectPixelShader. HLSL:

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

**Nota:** Para nuestra rutina **GatherDepthLess** , consulte el ejemplo de código de asignación de superficie: SpecialEffectPixelShader. HLSL.

**Representación de datos de malla de superficie en la pantalla**

También podemos dibujar las mallas de superficie en los búferes de pantalla estéreo. Decidimos dibujar caras completas con iluminación, pero tiene la libertad de dibujar tramas, procesar mallas antes de la representación, aplicar un mapa de textura, etc.

Aquí, nuestro ejemplo de código indica al representador de malla que dibuje la colección. Esta vez no se especifica un paso de solo profundidad, por lo que se conectará un sombreador de píxeles y se completará la canalización de representación mediante los destinos que se especificaron para la cámara virtual actual.

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Vea también
* [Creación de un proyecto de DirectX holográfico](creating-a-holographic-directx-project.md)
* [Windows. Perception. Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
