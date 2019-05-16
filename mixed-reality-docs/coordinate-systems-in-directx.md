---
title: Sistemas de coordenadas en DirectX
description: Explica cómo usar los localizadores espaciales Windows Mixed Reality, marcos de referencia, delimitadores espaciales y los sistemas de coordenadas, cómo usar el SpatialStage, cómo controlar la pérdida de seguimiento, cómo guardar y cargar los anclajes y cómo estabilización de la imagen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixto en realidad, localizador espacial, el marco de referencia espacial, sistema de coordenadas espacial, fase espacial, ejemplo de código, estabilización de imagen, delimitador espacial, tienda Premium espacial, pérdida de seguimiento, tutorial
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628972"
---
# <a name="coordinate-systems-in-directx"></a>Sistemas de coordenadas en DirectX

[Sistemas de coordenadas](coordinate-systems.md) forman la base de comprensión espacial ofrecidas por las API de realidad mixta de Windows.

Hoy en día había sentado VR o dispositivos de sala de único VR establecer un sistema de coordenadas principal para representar su espacio sometidas a seguimiento. Los dispositivos de Windows Mixed Reality, como HoloLens están diseñados para usarse en entornos de gran tamaño indefinidos, con el dispositivo, detectar y conocer sus alrededores como el usuario le guía en torno a. Esto permite que el dispositivo para adaptarse a mejorar continuamente conocimientos acerca de las salas del usuario, pero los sistemas de coordenadas que cambiará su relación entre sí a través de la duración de la aplicación. Windows Mixed Reality admite una amplia gama de dispositivos, que abarcan desde su asiento inmersivos a través de fotogramas de referencia mundo conectado.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemas de coordenadas espaciales en Windows

El tipo de núcleo utilizado para razonar sobre sistemas de coordenadas del mundo real en Windows es el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Una instancia de este tipo representa un sistema de coordenadas arbitrario y proporciona un método para obtener una matriz de transformación que puede usar para realizar transformaciones entre dos sistemas de coordenadas sin conocer los detalles de cada uno.

Los métodos que devuelven información espacial, representado como puntos, rayos o volúmenes en el entorno del usuario, aceptará un parámetro SpatialCoordinateSystem para que pueda decidir el sistema de coordenadas en el que resulta más útil para esas coordenadas que se va a devolver. Las unidades para estas coordenadas siempre será en metros.

Un SpatialCoordinateSystem tiene una relación con otros sistemas de coordenadas, las que representan la posición del dispositivo incluidas dinámica. En cualquier momento, el dispositivo puede ser capaz de encontrar algunos sistemas de coordenadas y otras no. Para la mayoría de los sistemas de coordenadas, la aplicación debe estar lista para controlar los períodos de tiempo durante el cual no se encuentra.

La aplicación no debería crear SpatialCoordinateSystems directamente: en su lugar debe utilizarse a través de la API de percepción. Existen tres fuentes principales de sistemas de coordenadas en las API de percepción, cada uno de los que se asignan a un concepto que se describe en el [sistemas de coordenadas](coordinate-systems.md) página:
* Para obtener un marco estático de referencia, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> u obtener uno desde la actual <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.
* Para obtener un anclaje espacial, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Para obtener un marco de referencia adjunta, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Todos los sistemas de coordenadas devueltos por estos objetos son diestros con + arriba + x y a la derecha y + z con versiones anteriores. Puede recordar qué dirección de los puntos de eje z positivo eligiendo los dedos de su mano derecha o izquierda en la dirección del eje x positivo y ellos cURL en la dirección del eje y positivo. La dirección a la que apunta el pulgar (acercándose o alejándose de ti) es la dirección que el eje z positivo apunta para ese sistema de coordenadas. La siguiente ilustración muestra estos dos sistemas de coordenadas.

![Sistemas de coordenadas derecho e izquierdos](images/left-hand-right-hand.gif)<br>
*Sistemas de coordenadas derecho e izquierdos*

Para arrancar en un SpatialCoordinateSystem basándose en la posición de un HoloLens, utilice el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> clase para crear cualquier un adjunto o estacionario marco de referencia, como se describe en las secciones siguientes.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Hologramas lugar del mundo mediante una fase espacial

El sistema de coordenadas para opacos inmersivos Windows Mixed Reality se tiene acceso con estático <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> propiedad. Esta API proporciona un sistema de coordenadas, la información acerca de si está colocado el Reproductor o móviles, el límite de un área segura para recorrer en torno a si el Reproductor es móvil, y una indicación de si no los auriculares direccional. También hay un controlador de eventos para las actualizaciones a la fase espacial.

En primer lugar, se obtenga la fase espacial y suscribirse a las actualizaciones: 

El código para **inicialización fase espacial**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

En el método OnCurrentChanged, la aplicación debe inspeccionar la fase espacial y actualizar en consecuencia la experiencia de Reproductor. En este ejemplo, se proporciona una visualización de los límites de fase, así como la posición de inicio especificada por el usuario y el intervalo de la fase de vista y el intervalo de las propiedades de movimiento. Nos también revertir a nuestro propio sistema de coordenadas inmóvil, cuando no se puede proporcionar una fase.


El código para **actualización fase espacial**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

El conjunto de vértices que definen los límites de la fase se proporcionan en el orden de las agujas del reloj. El shell de Windows Mixed Reality dibuja una barrera en el límite cuando el usuario aproxima a él; es posible que desee triangularize el área transitable para sus propios fines. El siguiente algoritmo puede utilizarse para triangularize la fase.


El código para **triangularization fase espacial**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Hologramas lugar del mundo mediante un marco estático de referencia

El [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) clase representa un marco de referencia que [permanece estacionario](coordinate-systems.md#stationary-frame-of-reference) en relación con el entorno del usuario como el usuario se mueve. Este marco de referencia da prioridad a las coordenadas de mantener estable cerca del dispositivo. Un uso de clave de un SpatialStationaryFrameOfReference es para que actúe como el sistema de coordenadas universales subyacentes dentro de un motor de representación al representar hologramas.

Para obtener un SpatialStationaryFrameOfReference, use el [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) clase y llamar a [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

Desde el código de plantilla de aplicación Windows Holographic:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Marcos de referencia fijos están diseñados para proporcionar una posición en relación con el espacio total con ajuste perfecto. Posiciones individuales dentro de ese marco de referencia pueden variar ligeramente. Esto es normal, ya que el dispositivo aprende más sobre el entorno.
* Cuando se requiere la posición precisa de hologramas individuales, se debe usar un SpatialAnchor para delimitar el holograma individual a una posición en el mundo real: por ejemplo, un punto el usuario indica para que sea de especial interés. No se desvíen posiciones de anclaje, pero pueden corregirse; el delimitador utilizará la posición corregida a partir de la siguiente después de que se ha producido la corrección.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Hologramas lugar del mundo mediante delimitadores espaciales

[Delimitadores espaciales](coordinate-systems.md#spatial-anchors) son una excelente manera de colocar hologramas en una ubicación específica en el mundo real, con el sistema lo que garantiza el delimitador permanece en su lugar con el tiempo. En este tema se explica cómo crear y usar un delimitador y cómo trabajar con datos de anclaje.

Puede crear un SpatialAnchor en cualquier posición y orientación en el SpatialCoordinateSystem de su elección. El dispositivo debe ser capaz de encontrar ese sistema de coordenadas en este momento, y debe el sistema no haya alcanzado su límite de delimitadores espaciales.

Una vez definido, el sistema de coordenadas de un SpatialAnchor ajusta continuamente para conservar la posición exacta y orientación de su ubicación inicial. A continuación, puede usar este SpatialAnchor para representar hologramas que va a aparecer fijos en el entorno del usuario en esa ubicación exacta.

Los efectos de los ajustes que conservar el delimitador en su lugar se amplía como distancia desde los aumentos de anclaje. Por lo tanto, debe evitar representar el contenido en relación con un delimitador que es de más de 3 metros de origen del anclaje.

El [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) propiedad obtiene un sistema de coordenadas que le permite colocar contenido en relación con el delimitador, con la aceleración aplica cuando el dispositivo ajusta la ubicación exacta del anclaje.

Use la [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) propiedad y la correspondiente [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) eventos para administrar estos ajustes usted mismo.

### <a name="persist-and-share-spatial-anchors"></a>Conservar y compartir los anclajes espaciales

Puede conservar un SpatialAnchor localmente mediante el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) clase y, a continuación, volver a obtener, en una sesión de la aplicación en un futuro en el mismo dispositivo HoloLens.

Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a>, puede crear un anclaje en la nube duraderas desde un SpatialAnchor local, que, a continuación, puede localizar su aplicación a través de varios HoloLens, dispositivos iOS y Android.  Al compartir un anclaje espacial comunes en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite experiencias compartidas en tiempo real.

También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para la persistencia holograma asincrónica a través de dispositivos Android, iOS y HoloLens.  Al compartir un anclaje espacial en la nube duraderas, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes entre sí al mismo tiempo.

Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">inicio rápido de Azure espacial delimitadores HoloLens</a>.

Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y localizar los anclajes en HoloLens</a>.  Los tutoriales están disponibles para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS y Android</a> así, lo que le permite compartir los delimitadores de la mismos en todos los dispositivos.

### <a name="create-spatialanchors-for-holographic-content"></a>Crear SpatialAnchors contenido holográfica

Para este ejemplo de código, hemos modificado Windows Holographic cree la plantilla de aplicación cuando ancla el **Pressed** se detecta el gesto. El cubo, a continuación, se coloca en el delimitador durante la fase de representación.

Puesto que varios delimitadores son compatibles con la clase auxiliar, podemos colocamos tantos cubos como queremos utilizar este ejemplo de código.

Tenga en cuenta que los identificadores para delimitadores son algo que controlar en la aplicación. En este ejemplo, hemos creado un esquema de nomenclatura es secuencial en función del número de delimitadores almacenados actualmente en la colección de la aplicación de delimitadores.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>De forma asincrónica cargar y almacenar en caché, el SpatialAnchorStore

Veamos cómo escribir una clase SampleSpatialAnchorHelper que ayuda a controlar esta persistencia, incluidos:
* Almacenar una colección de delimitadores en memoria, se indexan mediante una clave de Platform:: String.
* Cargar los anclajes de SpatialAnchorStore del sistema, que se mantienen separado de la colección en memoria local.
* Guardando la colección en memoria local de delimitadores en el SpatialAnchorStore cuando la aplicación opta por hacerlo.

Aquí le mostramos cómo guardar [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objetos en el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Cuando se inicia la clase, se solicita la SpatialAnchorStore asincrónicamente. Esto implica la E/S del sistema como la API de carga de la tienda y se realiza esta API asincrónica para que la E/S es sin bloqueo.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Se le ofrecerá un SpatialAnchorStore que puede usar para guardar los delimitadores. Se trata de un IMapView que asocia los valores de clave que son cadenas, con los valores que son SpatialAnchors. En nuestro código de ejemplo, se almacena en una variable de miembro de clase privada es accesible a través de una función pública de nuestra clase auxiliar.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>No se olvide de enlazar los eventos de suspensiones y reanudaciones para guardar y cargar el almacén de anclaje.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Guardar el contenido en el almacén de anclaje

Cuando el sistema suspende la aplicación, deberá guardar los delimitadores espaciales en el almacén de anclaje. También puede elegir guardar delimitadores en el almacén de anclaje en otras ocasiones, como encontrar para que sea necesario para la implementación de la aplicación.

Cuando esté listo para intentar guardar los anclajes en memoria en el SpatialAnchorStore, puede recorrer en iteración la colección e intenta guardar cada uno de ellos.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Cargar contenido desde el almacén de anclaje cuando se reanuda la aplicación

Cuando se reanuda la aplicación, o en cualquier momento es necesario para implementaiton de la aplicación, puede restaurar los delimitadores que anteriormente se guardaron en el AnchorStore mediante la transferencia desde IMapView de la tienda de anclaje a su propia base de datos en memoria SpatialAnchors.

Para restaurar los delimitadores de la SpatialAnchorStore, restaurar cada uno de ellos que interesa a su propia colección en memoria.

Necesitará su propia base de datos en memoria de SpatialAnchors; alguna manera de asociar el SpatialAnchors que cree en cadenas. En nuestro código de ejemplo, se decide usar un Windows::Foundation::Collections::IMap para almacenar los delimitadores, lo que facilita que se usará el mismo valor de clave y los datos para el SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Un delimitador que se restaura podría no ser localizable inmediatamente. Por ejemplo, podría ser un delimitador en la misma habitación o en un edificio diferente por completo. Delimitadores de recuperarse el AnchorStore deben probarse para locatability antes de usarlos.

<br>

>[!NOTE]
>En este código de ejemplo, recuperamos todos los delimitadores de la AnchorStore. Esto no es un requisito; la aplicación podría igual de bien elegir un subconjunto determinado de delimitadores mediante el uso de valores de clave de cadena que son significativos para su implementación.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Borrar el almacén de anclaje, cuando sea necesario

A veces, debe borrar el estado de la aplicación y escribir nuevos datos. Así es cómo hacer que con el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Con nuestra clase auxiliar, no es prácticamente necesario ajustar la función Clear. Se elige esta opción en nuestra implementación de ejemplo, dado que nuestra clase auxiliar tiene la responsabilidad de propietario de la instancia de SpatialAnchorStore.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Por ejemplo: Relacionados con los sistemas de coordenadas de anclaje para sistemas de coordenadas de marco de referencia estacionarios

Supongamos que tiene un anclaje y desea relacionar algo en el sistema de coordenadas del su anclaje a la SpatialStationaryReferenceFrame que ya esté usando para la mayoría de sus otros contenidos. Puede usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obtener una transformación de sistema de coordenadas del anclaje a la del marco estático referencia:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Este proceso es útil de dos maneras:
1. Indica si los dos marcos de referencia pueda entender con respecto a otro, y;
2. Si es así, proporciona una transformación para ir directamente desde un sistema de coordenadas a otro.

Con esta información, tiene un conocimiento de la relación entre los objetos entre los dos marcos de referencia espacial.

Para la representación, a menudo puede obtener mejores resultados mediante la agrupación de objetos según su marco de referencia original o el delimitador. Realizar un paso de dibujo independiente para cada grupo. Las matrices de vista son más precisas para los objetos con transformaciones de modelo que se crean inicialmente con el mismo sistema de coordenadas.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Crear hologramas mediante un dispositivo conectado marco de referencia

Hay veces cuando desee representar un holograma que [permanecen adjuntas](coordinate-systems.md#attached-frame-of-reference) a la ubicación del dispositivo, por ejemplo, un panel con un mensaje informativo o información de depuración cuando el dispositivo solo es capaz de determinar su orientación y no es su posición en el espacio. Para lograr esto, usamos un marco de referencia adjunta.

La clase SpatialLocatorAttachedFrameOfReference define los sistemas de coordenadas que son en relación con el dispositivo en lugar de en el mundo real. Este marco tiene un encabezado fijo con respecto al entorno del usuario que se apunta en la dirección del usuario cuando se creó el marco de referencia. Desde ese momento, todas las orientaciones en este marco de referencia son con respecto a ese encabezado fijo, incluso cuando el usuario gira el dispositivo.

Para HoloLens, el origen del sistema de coordenadas de este fotograma se encuentra en el centro de rotación de la cabeza del usuario, por lo que su posición no se ve afectada por la rotación principal. La aplicación puede especificar un desplazamiento con respecto a este punto para colocar hologramas delante del usuario.

Para obtener un SpatialLocatorAttachedFrameOfReference, utilice la clase SpatialLocator y llamar a CreateAttachedFrameOfReferenceAtCurrentHeading.

Tenga en cuenta que esto se aplica a los dispositivos de la completa gama de Windows Mixed Reality.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Utilice un marco de referencia asociado al dispositivo

Estas secciones hablan sobre lo que hemos cambiado en la plantilla de aplicación de Windows Holographic para habilitar un dispositivo conectado marco de referencia mediante esta API. Tenga en cuenta que funcionará junto con hologramas delimitados o estacionarios Este holograma "conectado" y también se puede usar cuando el dispositivo está temporalmente no se puede buscar su posición en el mundo.

En primer lugar, hemos cambiado la plantilla para almacenar un SpatialLocatorAttachedFrameOfReference en lugar de un SpatialStationaryFrameOfReference:

Desde **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Desde **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante la actualización, se obtiene el sistema de coordenadas en la marca de tiempo obtenida con la predicción de marco.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Obtener una postura puntero espaciales y siga la mirada del usuario

Queremos que nuestra holograma de ejemplo para seguir al usuario [que mirar](gaze.md), de forma similar a cómo el shell holográfico puede seguir mirada del usuario. Para ello, es necesario obtener el SpatialPointerPose desde la misma marca de tiempo.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Este SpatialPointerPose tiene la información necesaria para colocar el holograma según la [título actual del usuario](gaze-in-directx.md).

Por motivos de comodidad, usamos la interpolación lineal ("lerp") para suavizar el cambio de posición de forma que producen durante un período de tiempo. Esto es más cómodo para el usuario que bloquear el holograma a su mirada. Lerping que posición del holograma de tag-along también nos permite estabilizar el holograma por amortiguar el movimiento. Si no lo hicimos esta restricción, el usuario vería el holograma vibración debido a lo que normalmente se considera que imperceptibles movimientos de head del usuario.

Desde **StationaryQuadRenderer::PositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>En el caso de un panel de depuración, puede volver a colocar el holograma desactivar al lado un poco para que no obstruye la vista. Este es un ejemplo de cómo podría hacer eso.

Para **StationaryQuadRenderer::PositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Girar el holograma para enfrentar la cámara

No es suficiente colocar simplemente el holograma, que en este caso es un cuadrado; También nos debemos rotar el objeto para enfrentar el usuario. Tenga en cuenta que este giro se produce en el espacio global, porque este tipo de vallas publicitarias permite el holograma siga siendo una parte del entorno de usuario. Vallas publicitarias espacio de la vista no es tan cómodo porque el holograma queda bloqueado para la orientación de la pantalla; en ese caso, también debe interpolar entre las matrices de vista izquierda y derecha con el fin de adquirir una transformación de cartelera de espacio de la vista que no interrumpen la representación estéreo. En este caso, se gira en los ejes X y Z para afrontar el usuario.

Desde **StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Representar el holograma adjunto

En este ejemplo, elegimos también representar el holograma en el sistema de coordenadas de la SpatialLocatorAttachedReferenceFrame, que es donde se coloca el holograma. (Si hubiéramos decidido representar con otro sistema de coordenadas, se deberá adquirir una transformación de sistema de coordenadas del marco de referencia de dispositivo conectado a ese sistema de coordenadas.)

Desde **HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Ya está. El holograma ahora se "chase" una posición que es de 2 metros delante de la dirección de mirada del usuario.

>[!NOTE]
>Este ejemplo también carga contenido adicional: consulte StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Seguimiento de la pérdida de control

Cuando el dispositivo no puede encontrar a sí mismo en el mundo, la aplicación experimenta "pérdida de seguimiento". Windows Mixed Reality apps deben ser capaces de controlar dichas interrupciones para el sistema de seguimiento posicional. Se pueden observar estas interrupciones y respuestas crean, mediante el evento LocatabilityChanged en el valor predeterminado SpatialLocator.

Desde **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Cuando la aplicación recibe un evento LocatabilityChanged, puede cambiar el comportamiento según sea necesario. Por ejemplo, en el estado PositionalTrackingInhibited, la aplicación puede pausar el funcionamiento normal y representar un [holograma tag-along](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) que muestra un mensaje de advertencia.

La plantilla de aplicación de Windows Holographic viene con un controlador LocatabilityChanged ya ha creado para usted. De forma predeterminada, muestra una advertencia en la consola de depuración al seguimiento posicional no está disponible. Puede agregar código a este controlador para proporcionar una respuesta, según sea necesario desde la aplicación.

Desde **AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Asignación espacial

El [asignación espacial](spatial-mapping-in-directx.md) API facilitan el uso de sistemas de coordenadas para obtener las transformaciones de modelos de mallas de superficie.

## <a name="see-also"></a>Vea también
* [Sistemas de coordenadas](coordinate-systems.md)
* [Delimitadores espaciales](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Mirada principal y de ojo de DirectX](gaze-in-directx.md)
* [Las manos y los controladores de movimiento de DirectX](hands-and-motion-controllers-in-directx.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
