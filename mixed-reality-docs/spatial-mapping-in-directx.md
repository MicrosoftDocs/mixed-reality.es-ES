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
# <a name="spatial-mapping-in-directx"></a>Asignación espacial en DirectX

Este tema describe cómo implementar [asignación espacial](spatial-mapping.md) en la aplicación de DirectX. Esto incluye una explicación detallada de la aplicación de ejemplo de asignación espacial que se incluye con el SDK de plataforma Universal de Windows.

Código de este tema usa el [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) ejemplo de código UWP.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="directx-development-overview"></a>Introducción al desarrollo de DirectX

Desarrollo de aplicaciones nativas para la asignación espacial usa las API en el [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) espacio de nombres. Estas API ofrecen control total de la funcionalidad de asignación espacial, de forma análoga directamente a la asignación espacial API expuestas por [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>API de percepción

Los tipos primarios proporcionados para el desarrollo de asignación espacial son los siguientes:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) proporciona información acerca de las superficies de regiones especificado por la aplicación de espacio cerca del usuario, en forma de objetos SpatialSurfaceInfo.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describe una sola superficie espacial ordenamientos incluido un identificador único, el volumen y la hora del último cambio de límite. Proporcionará un SpatialSurfaceMesh asincrónicamente a petición.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contiene parámetros que se usan para personalizar los objetos SpatialSurfaceMesh solicitados desde SpatialSurfaceInfo.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa los datos de la malla de una sola superficie espacial. Los datos de posiciones de los vértices, las normales de vértice y los índices de triángulo se encuentran en los objetos miembro SpatialSurfaceMeshBuffer.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) ajusta un único tipo de datos de la malla.

Al desarrollar una aplicación con estas API, el flujo de programa básico tendrá este aspecto (como se muestra en la aplicación de ejemplo que se describe a continuación):
- **Configurar su SpatialSurfaceObserver**
  - Llame a [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para asegurarse de que el usuario ha dado permiso para la aplicación para usar funciones de asignación espacial del dispositivo.
  - Crear una instancia de un objeto SpatialSurfaceObserver.
  - Llame a [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar las regiones de espacio en el que desea obtener información sobre las superficies espaciales. Puede modificar estas regiones en el futuro simplemente vuelva a llamar a esta función. Cada región se especifica mediante un [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Registrarse para la [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) evento, que se activará cada vez que hay información nueva acerca de las superficies espaciales en las regiones de espacio que se ha especificado.
- **Procesar eventos ObservedSurfacesChanged**
  - En el controlador de eventos, llamar a [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para recibir un mapa de objetos SpatialSurfaceInfo. Utilización de esta asignación, se pueden actualizar los registros de las superficies que espacial [existe en el entorno del usuario](spatial-mapping.md#mesh-caching).
  - Para cada objeto SpatialSurfaceInfo, se puede consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) determinar las extensiones espaciales de la superficie, expresada en un [del sistema de coordenadas espacial](coordinate-systems.md) de su elección.
  - Si decide malla para una superficie espacial de la solicitud, llame al [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Puede proporcionar opciones que especifican la densidad de triángulos deseada y el formato de los datos devueltos de malla.
- **Recibir y procesar de malla**
  - Cada llamada a TryComputeLatestMeshAsync will aysnchronously devolver un objeto SpatialSurfaceMesh.
  - De este objeto se pueden acceder a los objetos SpatialSurfaceMeshBuffer independientes para tener acceso a los índices de triángulo, posiciones de los vértices y (si se solicitan) normales de vértice de la malla. Estos datos estarán en un formato compatible directamente con el [API de Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usa para representar las mallas.
  - Desde aquí, la aplicación, opcionalmente, puede realizar análisis o [procesamiento](spatial-mapping.md#mesh-processing) de los datos de la malla y usarla para [representación](spatial-mapping.md#rendering) y física [detalles y colisión](spatial-mapping.md#raycasting-and-collision).
  - Un detalle importante que tener en cuenta es que debe aplicar una escala hacia las posiciones de vértices de malla (por ejemplo, en el sombreador de vértices que se usa para representar las mallas) convertirlos de las unidades de entero optimizado en el que se almacenan en el búfer, en metros. Puede recuperar mediante una llamada a esta escala [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Solución de problemas
* No se olvide de escalar las posiciones de vértices de malla en su sombreador de vértices, mediante la escala devuelta por [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Tutorial de ejemplo de código de asignación espacial

El [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) ejemplo de código incluye código que puede usar para empezar a cargar las mallas de superficie en la aplicación, incluida la infraestructura para administrar y mallas de superficie de representación.

Ahora, analizaremos cómo agregar la funcionalidad de asignación de superficie a la aplicación de DirectX. Puede agregar este código a su [plantilla de aplicación de Windows Holographic](creating-a-holographic-directx-project.md) proyecto, o bien puede continuar examinando el código de ejemplo mencionado anteriormente. Este ejemplo de código se basa en la plantilla de aplicación de Windows Holographic.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configuración de la aplicación para utilizar la funcionalidad de spatialPerception

La aplicación debe ser capaz de usar la funcionalidad de asignación espacial. Esto es necesario porque la malla espacial es una representación del entorno del usuario, que puede considerarse datos privados. Declare esta capacidad en el archivo package.appxmanifest de la aplicación. Por ejemplo:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funcionalidad proviene de la **uap2** espacio de nombres. Para obtener acceso a este espacio de nombres en el manifiesto, incluirla como un *xlmns* atributo el &lt;paquete > elemento. Por ejemplo:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Comprobar la compatibilidad de la característica de asignación espacial

Windows Mixed Reality admite una amplia gama de dispositivos, incluidos los dispositivos que no admiten la asignación espacial. Si la aplicación puede usar la asignación espacial, o debe usar la asignación espacial, para proporcionar funcionalidad, debe comprobar para asegurarse de que se admite la asignación espacial antes de intentar utilizarlo. Por ejemplo, si la aplicación de realidad mixta requieren asignación espacial, debe mostrar un mensaje a tal efecto si un usuario intenta ejecutarlo en un dispositivo sin asignación espacial. O bien, la aplicación puede ser capaces de procesar su propio entorno virtual en lugar del entorno del usuario, que proporciona una experiencia similar a lo que sucedería si asignación espacial, no estaba disponible. En cualquier caso, esta API permite a tener en cuenta cuando no obtener datos de asignación espacial y responder en la forma adecuada de la aplicación.

Para comprobar el dispositivo actual para la compatibilidad con la asignación espacial, primero asegúrese de que el contrato UWP es el nivel 4 o superior y, a continuación, llamar a SpatialSurfaceObserver::IsSupported(). Aquí le mostramos cómo hacerlo en el contexto de la [asignación espacial holográfica](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) ejemplo de código. Soporte técnico se comprueba justo antes de solicitar acceso.

La API de SpatialSurfaceObserver::IsSupported() está disponible a partir del SDK versión 15063. Si es necesario, redestinar el proyecto a la versión de la plataforma 15063 antes de usar esta API.

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

Tenga en cuenta que cuando el contrato UWP es menor que el nivel 4, la aplicación debe continuar como si el dispositivo es capaz de hacer la asignación espacial.

### <a name="request-access-to-spatial-mapping-data"></a>Solicitar acceso a los datos de asignación espacial

La aplicación necesita solicitar permiso para tener acceso a datos de asignación espacial antes de intentar crear cualquier superficies observadores. Este es un ejemplo basado en nuestro ejemplo de código de superficie de asignación, con más detalles que proporcionó más adelante en esta página:

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

### <a name="create-a-surface-observer"></a>Crear un observador de superficie

El **Windows::Perception::Spatial::Surfaces** espacio de nombres incluye la [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) (clase), que observa el valor de uno o más volúmenes que especifique en un [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Use un [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instancia malla de superficie acceder a los datos en tiempo real.

Desde **AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Como se indicó en la sección anterior, debe solicitar acceso a los datos de asignación espacial antes de la aplicación puede usarlo. Este acceso se concede automáticamente el HoloLens.

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

A continuación, deberá configurar el observador de superficie para observar un volumen específico de delimitador. En este caso, observamos un cuadro que tenga 20 x 20 x 5 metros, centrado en el origen del sistema de coordenadas.

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

Tenga en cuenta que puede establecer varios volúmenes delimitadores en su lugar.

*Este es el pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

También es posible usar otras formas de delimitadores - como frustum una vista, o un cuadro de límite que no es de eje alineado.

*Este es el pseudocódigo:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Si la aplicación necesita hacer nada diferente cuando la superficie de asignación de datos no está disponible, puede escribir código para responder al caso donde la [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) no **permitido** , por ejemplo, no se podrá en equipos con dispositivos envolventes puede adjuntados porque no tienen esos dispositivos de hardware para la asignación espacial. Para estos dispositivos, en su lugar, debe confiar en el escenario espacial para obtener información sobre el entorno y la configuración del dispositivo del usuario.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Inicializar y actualizar la colección de malla de superficie

Si el observador expuesto se ha creado correctamente, podemos continuar para inicializar la colección de malla de superficie. En este caso, usamos la API del modelo de extracción para obtener el conjunto actual de superficies observados inmediatamente:

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

También hay un modelo de inserción disponible para obtener datos de la malla de superficie. Es libre de diseñar la aplicación utilice solo el modelo de extracción si decide, en cuyo caso deberá sondear en busca de datos con mucha frecuencia: por ejemplo, una vez por fotograma - o durante un período de tiempo específico, como durante la instalación del juego. Si es así, el código anterior es lo que necesita.

En nuestro ejemplo de código, hemos optado por muestran el uso de ambos modelos con fines pedagógicos. En este caso, se suscribe a un evento para recibir datos de la malla de superficie actualizada siempre que el sistema reconoce un cambio.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Nuestro ejemplo de código también está configurado para responder a estos eventos. Veamos cómo hacer esto.

**NOTA:** Esto podría no ser la manera más eficaz para la aplicación controlar los datos de la malla. Este código está escrito para mayor claridad y no está optimizado.

Los datos de la malla de superficie se proporcionan una asignación de solo lectura que almacena [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objetos mediante [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de clave.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Para procesar estos datos, se buscan primeros para valores de clave que no están en la colección. Obtener más información sobre cómo se almacenan los datos en nuestra aplicación de ejemplo le mostrará más adelante en este tema.

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

También tenemos que quitar las mallas de superficie que se encuentran en nuestra colección de malla de superficie, pero que no están en la colección del sistema ya. Para ello, necesitamos hacer algo parecido a lo contrario de lo que acabamos de agregar y actualizar las mallas; Realizamos un bucle en nuestra aplicación de la colección y compruebe si el **Guid** tenemos está en la colección del sistema. Si no está en la colección del sistema, se quitará las nuestras.

Desde nuestro controlador de eventos en AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

La implementación de la eliminación de la malla en RealtimeSurfaceMeshRenderer.cpp de:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Adquirir y utilizar los búferes de datos de la malla de superficie

Obtener la información de la malla de superficie era tan fácil como extraer una recolección de datos y procesamiento de las actualizaciones de esa colección. Ahora, vamos en los detalles sobre cómo se pueden usar los datos.

En nuestro ejemplo de código, hemos optado por utilizar las mallas de superficie de representación. Se trata de un escenario común para occluding hologramas tras las superficies del mundo real. También puede representar las mallas, o representar procesado las versiones de ellos, para mostrar al usuario qué áreas de la sala se examinan antes de empezar a proporcionar una funcionalidad de aplicación o juego.

El ejemplo de código inicia el proceso cuando recibe las actualizaciones de la malla de superficie desde el controlador de eventos que se describe en la sección anterior. La línea de código en esta función importante es la llamada para actualizar la superficie *malla*: Llegados a este punto ya hemos procesado la información de la malla, y que se van a obtener los datos de vértice y el índice para su uso según se estime oportuno.

Desde RealtimeSurfaceMeshRenderer.cpp:

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

Nuestro código de ejemplo está diseñado para que una clase de datos, **SurfaceMesh**, datos de la malla de identificadores de procesamiento y representación. Estos mallas son lo que el **RealtimeSurfaceMeshRenderer** realmente mantiene una asignación de. Cada uno de ellos tiene una referencia a la SpatialSurfaceMesh que proviene y se usa cada vez que se necesita tener acceso a los búferes de vértice o el índice de la malla, u obtener una transformación de la malla. Por ahora, se marca la malla como la necesidad de una actualización.

Desde SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Próxima vez que se solicita la malla a dibujarse a sí mismo, comprobará la marca en primer lugar. Si se necesita una actualización, los búferes de vértices y de índices se actualizará en la GPU.

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

A continuación, creamos los búferes de dispositivo Direct3D con los datos de la malla proporcionados por el HoloLens:

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

**NOTA:** Para la función auxiliar CreateDirectXBuffer usada en el fragmento de código anterior, vea el ejemplo de código de asignación de la superficie: SurfaceMesh.cpp, GetDataFromIBuffer.h. Ahora la creación de recursos de dispositivo completada y se considera ser cargados y listos para la actualización y representar la malla.

### <a name="update-and-render-surface-meshes"></a>Actualizar y procesar las mallas de superficie

Nuestra clase SurfaceMesh tiene una función de actualización especializadas. Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tiene su propia transformación y nuestro ejemplo utiliza el sistema de coordenadas actual para nuestro **SpatialStationaryReferenceFrame** para adquirir la transformación. A continuación, actualiza el búfer de constantes de modelo en la GPU.

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

Cuando sea el momento para representar la superficie de mallas, hacemos algún trabajo de preparación antes de representar la colección. Configuramos la canalización de sombreador para la configuración de representación actual, y configuramos la etapa del ensamblador de entrada. Tenga en cuenta que la clase auxiliar de cámara holographic **CameraResources.cpp** ya ha configurado el búfer de constantes y proyección de la vista en este momento.

Desde **RealtimeSurfaceMeshRenderer::Render**:

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

Una vez hecho esto, hemos bucle en nuestra mallas e indicar a cada uno de ellos a dibujarse a sí mismo. **NOTA:** Este código de ejemplo no está optimizado para usar a algún tipo de caras traseras frustum, pero debe incluir esta característica en la aplicación.

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

Las mallas individuales son responsables de configurar el búfer de vértices y de índices, stride y el búfer de constantes de transformación de modelo. Al igual que con el cubo girando en la plantilla de aplicación de Windows Holographic, representamos los búferes estereoscópicas mediante la creación de instancias.

Desde **SurfaceMesh::Draw**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Opciones de representación con la superficie de asignación

El ejemplo de código de asignación de superficie ofrece código para la representación sólo oclusión de datos de la malla de superficie y para la representación en pantalla de datos de la malla de superficie. Decide qué ruta de acceso - o bien ambos - dependen de la aplicación. Le guiaremos a través de ambas configuraciones en este documento.

**Búferes de oclusión de representación de efecto holográfica**

Inicie desactivando el destino de presentación de la cámara virtual actual.

Desde AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Se trata de un paso de "representación previa". En este caso, creamos un búfer de oclusión pidiendo el representador de malla para representar solo profundidad. En esta configuración, no Adjuntamos un destino de presentación y el representador de malla establece la etapa del sombreador de píxeles en **nullptr** para que la GPU no se molesta en dibujar píxeles. La geometría será rasterizada en el búfer de profundidad y detendrá la canalización de gráficos no existe.

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

Podemos dibujar hologramas con una prueba de profundidad adicional en el búfer de oclusión de superficie de asignación. En este ejemplo de código, representamos los píxeles en el cubo de un color diferente si están detrás de una superficie.

Desde AppMain.cpp:

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

Basado en código de SpecialEffectPixelShader.hlsl:

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

**Nota:** Para nuestro **GatherDepthLess** rutina, vea el ejemplo de código de asignación de la superficie: SpecialEffectPixelShader.hlsl.

**Datos de la malla de superficie de representación a la pantalla**

También podemos dibujar las mallas expuestas a los búferes de pantalla estéreo. Hemos optado por dibujar caras completas con la iluminación, pero tiene la libertad dibujar las tramas de alambres, procesar mallas antes de la representación, aplicar un mapa de textura y así sucesivamente.

En este caso, nuestro ejemplo de código indica el representador de malla para dibujar la colección. Esta vez no especificamos un paso sólo profundidad, por lo que van a adjuntar a un sombreador de píxeles y completar la canalización de representación con los destinos que se especificó para la cámara virtual actual.

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

## <a name="see-also"></a>Vea también
* [Creación de un proyecto de DirectX holográfico](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
