---
title: Sistemas de coordenadas en DirectX
description: Explica cómo usar los localizadores espaciales, los fotogramas de referencia, los delimitadores espaciales y los sistemas de coordenadas de Windows Mixed Reality, cómo usar SpatialStage, cómo controlar la pérdida de seguimiento, cómo guardar y cargar delimitadores, y cómo realizar la estabilización de la imagen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, localizador espacial, marco de referencia espacial, sistema de coordenadas espaciales, fase espacial, código de ejemplo, estabilización de imágenes, delimitador espacial, almacén de delimitador espacial, pérdida de seguimiento, tutorial
ms.openlocfilehash: a0bce897c1982715af24f0bf7c398cdee10f017f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436226"
---
# <a name="coordinate-systems-in-directx"></a>Sistemas de coordenadas en DirectX

[Los sistemas de coordenadas](coordinate-systems.md) constituyen la base para la comprensión espacial ofrecida por las API de Windows Mixed Reality.

Los dispositivos actuales de VR o de una sola habitación establecen un sistema de coordenadas principal para representar el espacio del que se ha realizado el seguimiento. Los dispositivos de Windows Mixed Reality, como HoloLens, están diseñados para usarse en entornos de gran tamaño sin definir, con el dispositivo que detecta y aprende sobre su entorno a medida que el usuario se recorre. Esto permite que el dispositivo se adapte al conocimiento que se mejora continuamente sobre los salones del usuario, pero que los sistemas de coordenadas cambien su relación entre sí a través de la duración de la aplicación. Windows Mixed Reality es compatible con una amplia gama de dispositivos, desde los auriculares envolventes colocados a través de fotogramas de referencia conectados al mundo.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.

## <a name="spatial-coordinate-systems-in-windows"></a>Sistemas de coordenadas espaciales en Windows

El tipo básico que se usa para los sistemas de coordenadas del mundo real en Windows es el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Una instancia de este tipo representa un sistema de coordenadas arbitrario y proporciona un método para obtener una matriz de transformación que se puede usar para transformar entre dos sistemas de coordenadas sin conocer los detalles de cada uno de ellos.

Los métodos que devuelven información espacial, representados como puntos, rayos o volúmenes en el entorno del usuario, aceptarán un parámetro SpatialCoordinateSystem para permitirle decidir el sistema de coordenadas en el que es más útil para las coordenadas que se van a devolver. Las unidades de estas coordenadas siempre estarán en metros.

Un SpatialCoordinateSystem tiene una relación dinámica con otros sistemas de coordenadas, incluidos los que representan la posición del dispositivo. En cualquier momento, es posible que el dispositivo pueda localizar algunos sistemas de coordenadas y no otros. Para la mayoría de los sistemas de coordenadas, la aplicación debe estar preparada para controlar los períodos de tiempo durante los cuales no se pueden encontrar.

La aplicación no debe crear SpatialCoordinateSystems directamente, sino que se deben usar a través de las API de percepción. Existen tres orígenes principales de sistemas de coordenadas en las API de percepción, cada uno de los cuales se asigna a un concepto descrito en la página [sistemas de coordenadas](coordinate-systems.md) :
* Para obtener un marco estacionario de referencia, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> u obtenga uno de la <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>actual.
* Para obtener un delimitador espacial, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Para obtener un marco de referencia asociado, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Todos los sistemas de coordenadas devueltos por estos objetos son zurdos, con + y hacia arriba, + x a la derecha y + z hacia atrás. Puede recordar en qué dirección apunta el eje z positivo apuntando los dedos de la mano izquierda o derecha en la dirección x positiva y enrollándose en la dirección y positiva. La dirección a la que apunta el pulgar (acercándose o alejándose de ti) es la dirección que el eje z positivo apunta para ese sistema de coordenadas. La siguiente ilustración muestra estos dos sistemas de coordenadas.

![los sistemas de coordenadas del lado izquierdo y derecho](images/left-hand-right-hand.gif)<br>
*Sistemas de coordenadas del lado izquierdo y derecho*

Para arrancar en un SpatialCoordinateSystem en función de la posición de un HoloLens, use la clase <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> para crear un marco de referencia adjunto o estacionario, como se describe en las secciones siguientes.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Colocar hologramas en el mundo mediante una fase espacial

Se tiene acceso al sistema de coordenadas para los auriculares con forma de la realidad mixta de Windows con la que se usa la propiedad estática <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> . Esta API proporciona un sistema de coordenadas, información acerca de si el jugador está sentado o es móvil, el límite de un área segura para desplazarse si el jugador es móvil y una indicación de si el casco es direccional. También hay un controlador de eventos para las actualizaciones de la fase espacial.

En primer lugar, se obtiene la fase espacial y se suscriben las actualizaciones a ella: 

Código para la **inicialización de la fase espacial**

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

En el método OnCurrentChanged, la aplicación debe inspeccionar la fase espacial y actualizar la experiencia del reproductor en consecuencia. En este ejemplo, se proporciona una visualización del límite de la fase, así como la posición inicial especificada por el usuario y el intervalo de vista y intervalo de propiedades de movimiento de la fase. También reviertemos a nuestro propio sistema de coordenadas estacionales, cuando no se puede proporcionar una fase.


Código para la actualización de la **fase espacial**

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

El conjunto de vértices que definen el límite de la fase se proporciona en el orden de las agujas del reloj. El shell de Windows Mixed Reality dibuja una barrera en el límite cuando el usuario la trata; es posible que desee triangular el área que se puede examinar para sus propios fines. El siguiente algoritmo se puede usar para triangular de la fase.


Código para **triangulación en la fase espacial**

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Colocar hologramas en el mundo con un marco estacionario de referencia

La clase [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) representa un marco de referencia que [permanece estacionario](coordinate-systems.md#stationary-frame-of-reference) en relación con el entorno del usuario a medida que el usuario se desplaza. Este marco de referencia prioriza la conservación de las coordenadas al lado del dispositivo. Un uso clave de una SpatialStationaryFrameOfReference es actuar como el sistema de coordenadas universal subyacente dentro de un motor de representación al representar hologramas.

Para obtener un SpatialStationaryFrameOfReference, use la clase [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) y llame a [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

En el código de plantilla de la aplicación Holographic de Windows:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Los fotogramas de referencia estacionarios están diseñados para proporcionar una posición con ajuste perfecto en relación con el espacio global. Las posiciones individuales dentro de ese marco de referencia pueden desplazarse ligeramente. Esto es normal, ya que el dispositivo aprende más sobre el entorno.
* Cuando se requiere una ubicación precisa de hologramas individuales, se debe usar un SpatialAnchor para delimitar el holograma individual a una posición en el mundo real; por ejemplo, un punto que el usuario indica que sea de especial interés. Las posiciones de anclaje no se desplazan, pero se pueden corregir. el delimitador usará la posición corregida a partir del fotograma siguiente después de que se haya realizado la corrección.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Colocar hologramas en el mundo mediante delimitadores espaciales

Los [delimitadores espaciales](coordinate-systems.md#spatial-anchors) son una excelente manera de colocar hologramas en un lugar específico del mundo real, con el sistema que garantiza que el delimitador permanece en su lugar con el tiempo. En este tema se explica cómo crear y usar un delimitador y cómo trabajar con datos de delimitador.

Puede crear un SpatialAnchor en cualquier posición y orientación dentro del SpatialCoordinateSystem de su elección. El dispositivo debe ser capaz de localizar ese sistema de coordenadas en el momento y el sistema no debe haber alcanzado el límite de delimitadores espaciales.

Una vez definido, el sistema de coordenadas de un SpatialAnchor se ajusta continuamente para conservar la posición precisa y la orientación de su ubicación inicial. Después, puede usar esta SpatialAnchor para representar hologramas que aparecerán fijos en el entorno del usuario en esa ubicación exacta.

Los efectos de los ajustes que mantienen el anclaje en su lugar se amplían a medida que el delimitador aumenta. Por lo tanto, debe evitar la representación del contenido en relación con un delimitador que supere los 3 metros del origen de ese delimitador.

La propiedad [coordenadas](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) obtiene un sistema de coordenadas que le permite colocar el contenido en relación con el delimitador, con una aceleración aplicada cuando el dispositivo ajusta la ubicación precisa del delimitador.

Use la propiedad [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) y el evento [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) correspondiente para administrar estos ajustes.

### <a name="persist-and-share-spatial-anchors"></a>Persistencia y uso compartido de delimitadores espaciales

Puede conservar un SpatialAnchor localmente mediante la clase [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) y, a continuación, recuperarlo en una sesión de aplicación futura en el mismo dispositivo HoloLens.

Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a>, puede crear un delimitador de la nube durable desde un SpatialAnchor local, que la aplicación puede ubicar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

También se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia de hologramas asincrónicos en dispositivos Android, iOS y HoloLens.  Al compartir un delimitador espacial en la nube duradera, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, aunque los dispositivos no estén presentes juntos simultáneamente.

Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe la guía de inicio rápido de HoloLens de 5 minutos de <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">delimitadores espaciales de Azure</a>.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y buscar delimitadores en HoloLens</a>.  También hay tutoriales disponibles para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , lo que le permite compartir los mismos delimitadores en todos los dispositivos.

### <a name="create-spatialanchors-for-holographic-content"></a>Crear SpatialAnchors para contenido holográfica

En este ejemplo de código, se modificó la plantilla de aplicación de Windows Holographic para crear delimitadores cuando se detecta el gesto **presionado** . Después, el cubo se coloca en el delimitador durante la fase de representación.

Dado que la clase auxiliar admite varios delimitadores, se pueden colocar tantos cubos como se deseen con este ejemplo de código.

Tenga en cuenta que los identificadores de los delimitadores son algo que usted controla en la aplicación. En este ejemplo, se ha creado un esquema de nomenclatura que es secuencial en función del número de delimitadores almacenados actualmente en la colección de delimitadores de la aplicación.

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Cargar y almacenar en caché de forma asincrónica el SpatialAnchorStore

Veamos cómo escribir una clase SampleSpatialAnchorHelper que ayude a controlar esta persistencia, incluidos:
* Almacenar una colección de delimitadores en memoria, indizada por una clave Platform:: String.
* Cargar delimitadores de la SpatialAnchorStore del sistema, que se mantiene independiente de la colección en memoria local.
* Guardar la colección local en memoria de los delimitadores en el SpatialAnchorStore cuando la aplicación decida hacerlo.

Aquí se muestra cómo guardar objetos [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) en [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Cuando se inicia la clase, se solicita SpatialAnchorStore de forma asincrónica. Esto implica la e/s del sistema, ya que la API carga el almacén de delimitadores y esta API se hace asincrónica para que la e/s no sea de bloqueo.

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

Se le proporcionará un SpatialAnchorStore que puede usar para guardar los delimitadores. Se trata de un IMapView que asocia valores de clave que son cadenas, con valores de datos que son SpatialAnchors. En el código de ejemplo, se almacena en una variable de miembro de clase privada que es accesible a través de una función pública de nuestra clase auxiliar.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>No olvide enlazar los eventos de suspensión y reanudación para guardar y cargar el almacén delimitado.

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

### <a name="save-content-to-the-anchor-store"></a>Guardar el contenido en el almacén delimitado

Cuando el sistema suspende la aplicación, debe guardar los anclajes espaciales en el almacén delimitado. También puede optar por guardar los delimitadores en el almacén de delimitadores en otros momentos, según considere que es necesario para la implementación de la aplicación.

Cuando esté listo para intentar guardar los delimitadores en memoria en SpatialAnchorStore, puede crear un bucle a través de la colección e intentar guardar cada una de ellas.

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Carga de contenido desde el almacén delimitado cuando se reanuda la aplicación

Cuando se reanuda la aplicación, o en cualquier otro momento necesario para el implementaiton de la aplicación, puede restaurar los delimitadores que se guardaron previamente en el AnchorStore si los transfiere de la IMapView de la tienda Premium a su propia base de datos en memoria de SpatialAnchors.

Para restaurar los delimitadores de SpatialAnchorStore, restaure cada uno que le interese en su propia colección en memoria.

Necesita su propia base de datos en memoria de SpatialAnchors; alguna manera de asociar cadenas con el SpatialAnchors que cree. En el código de ejemplo, elegimos usar un Windows:: Foundation:: Collections:: IMap para almacenar los delimitadores, lo que facilita el uso de la misma clave y el mismo valor de datos para el SpatialAnchorStore.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Un delimitador que se restaure podría no ser localizable de inmediato. Por ejemplo, podría tratarse de un delimitador en un salón independiente o en un edificio diferente. Los delimitadores recuperados de AnchorStore deben probarse para encontrar la ubicación antes de usarlos.

<br>

>[!NOTE]
>En este código de ejemplo, recuperamos todos los delimitadores de AnchorStore. Esto no es un requisito; también podría elegir un determinado subconjunto de delimitadores usando valores de clave de cadena que son significativos para su implementación.

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

### <a name="clear-the-anchor-store-when-needed"></a>Borrar el almacén delimitador, cuando sea necesario

A veces, debe borrar el estado de la aplicación y escribir datos nuevos. Aquí se muestra cómo hacerlo con el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Con nuestra clase auxiliar, casi innecesaria para encapsular la función Clear. Decidimos hacerlo en nuestra implementación de ejemplo, porque a nuestra clase auxiliar se le da la responsabilidad de poseer la instancia de SpatialAnchorStore.

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Ejemplo: vinculación de sistemas de coordenadas de anclaje a sistemas de coordenadas de fotogramas de referencia estacionales

Supongamos que tiene un delimitador y quiere relacionar algo en el sistema de coordenadas del delimitador con el SpatialStationaryReferenceFrame que ya está usando para la mayor parte de su contenido. Puede usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obtener una transformación del sistema de coordenadas del delimitador al marco de referencia estacionaria:

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

Este proceso resulta útil de dos maneras:
1. Indica si los dos fotogramas de referencia se pueden entender entre sí, y;
2. En ese caso, proporciona una transformación para pasar directamente de un sistema de coordenadas a otro.

Con esta información, se conoce la relación espacial entre los objetos entre los dos fotogramas de referencia.

Para la representación, a menudo puede obtener mejores resultados mediante la agrupación de objetos según su marco de referencia original o el delimitador. Realice un paso de dibujo independiente para cada grupo. Las matrices de vistas son más precisas para los objetos con transformaciones del modelo que se crean Inicialmente mediante el mismo sistema de coordenadas.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Crear hologramas mediante un marco de referencia conectado al dispositivo

Hay ocasiones en las que desea representar un holograma que [permanece adjunto](coordinate-systems.md#attached-frame-of-reference) a la ubicación del dispositivo, por ejemplo un panel con información de depuración o un mensaje informativo cuando el dispositivo solo puede determinar su orientación y no su posición en Espacia. Para ello, usamos un marco de referencia asociado.

La clase SpatialLocatorAttachedFrameOfReference define los sistemas de coordenadas que son relativos al dispositivo en lugar de al mundo real. Este marco tiene un encabezado fijo en relación con el entorno del usuario que apunta a la dirección a la que estaba situado el usuario cuando se creó el marco de referencia. A partir de entonces, todas las orientaciones de este marco de referencia son relativas a ese título fijo, incluso cuando el usuario gira el dispositivo.

En el caso de HoloLens, el origen del sistema de coordenadas de este fotograma se encuentra en el centro de rotación del encabezado del usuario, de modo que su posición no se ve afectada por la rotación del cabezal. La aplicación puede especificar un desplazamiento relativo a este punto para colocar los hologramas delante del usuario.

Para obtener un SpatialLocatorAttachedFrameOfReference, use la clase SpatialLocator y llame a CreateAttachedFrameOfReferenceAtCurrentHeading.

Tenga en cuenta que esto se aplica a todo el intervalo de dispositivos de Windows Mixed Reality.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Uso de un marco de referencia conectado al dispositivo

En estas secciones se habla sobre lo que hemos cambiado en la plantilla de aplicación de Windows Holographic para habilitar un marco de referencia de dispositivo de referencia mediante esta API. Tenga en cuenta que este holograma "adjunto" funcionará junto con los hologramas fijos o anclados, y también puede usarse cuando el dispositivo no pueda encontrar su posición en el mundo temporalmente.

En primer lugar, hemos cambiado la plantilla para almacenar un SpatialLocatorAttachedFrameOfReference en lugar de un SpatialStationaryFrameOfReference:

Desde **HolographicTagAlongSampleMain. h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Desde **HolographicTagAlongSampleMain. cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Durante la actualización, ahora obtenemos el sistema de coordenadas en la marca de tiempo obtenida de con la predicción de fotogramas.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Obtener una pose de puntero espacial y seguir el

Queremos que el holograma de ejemplo siga la [mirada](gaze-and-commit.md)del usuario, de forma similar a cómo el shell holográfica puede seguir a la mirada del usuario. Para ello, es necesario obtener el SpatialPointerPose de la misma marca de tiempo.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Este SpatialPointerPose tiene la información necesaria para colocar el holograma según el [encabezado actual del usuario](gaze-in-directx.md).

Por motivos de comodidad del usuario, usamos la interpolación lineal ("lerp") para suavizar el cambio en la posición de modo que se produzca durante un período de tiempo. Esto es más cómodo para el usuario que bloquear el holograma a su mirada. Lerping la posición de la etiqueta en el holograma también nos permite estabilizar el holograma mediante la amortiguación del movimiento. Si no se realiza esta amortiguación, el usuario verá la vibración del holograma debido a lo que se suele considerar como movimientos imperceptibles del encabezado del usuario.

Desde **StationaryQuadRenderer::P ositionhologram**:

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
>En el caso de un panel de depuración, puede optar por volver a colocar el holograma en la parte lateral un poco para que no obstruya la vista. Este es un ejemplo de cómo podría hacerlo.

Para **StationaryQuadRenderer::P ositionhologram**:

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>Girar el holograma para que se enfrente a la cámara

No basta con colocar simplemente el holograma, que en este caso es un cuádruple; También debemos girar el objeto para que se enfrente al usuario. Tenga en cuenta que esta rotación se produce en el espacio universal, ya que este tipo de cartelera permite que el holograma siga siendo parte del entorno del usuario. La cartelera de espacio de vista no es tan cómoda porque el holograma se bloquea en la orientación de la pantalla. en ese caso, también tendría que interpolar entre las matrices de la vista izquierda y derecha para adquirir una transformación de la cartelera de espacio de vista que no interrumpa la representación en estéreo. Aquí, giramos en los ejes X y Z para que se enfrente al usuario.

Desde **StationaryQuadRenderer:: Update**:

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

En este ejemplo, también optamos por representar el holograma en el sistema de coordenadas de SpatialLocatorAttachedReferenceFrame, que es donde colocamos el holograma. (Si se hubiera decidido representar con otro sistema de coordenadas, es necesario adquirir una transformación del sistema de coordenadas del fotograma de referencia conectado al dispositivo a ese sistema de coordenadas).

Desde **HolographicTagAlongSampleMain:: Render**:

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

Eso es todo. Ahora, el holograma "persecución" es una posición de 2 metros delante de la dirección del usuario.

>[!NOTE]
>En este ejemplo también se carga contenido adicional; Consulte StationaryQuadRenderer. cpp.

## <a name="handling-tracking-loss"></a>Control de la pérdida de seguimiento

Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento". Las aplicaciones de Windows Mixed Reality deben ser capaces de controlar tales interrupciones en el sistema de seguimiento posicional. Estas interrupciones se pueden observar y las respuestas se crean mediante el evento LocatabilityChanged en el SpatialLocator predeterminado.

Desde **AppMain:: SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Cuando la aplicación recibe un evento LocatabilityChanged, puede cambiar el comportamiento según sea necesario. Por ejemplo, en el estado PositionalTrackingInhibited, la aplicación puede pausar el funcionamiento normal y representar una [etiqueta a lo largo](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) de un holograma que muestre un mensaje de advertencia.

La plantilla de aplicación de Windows Holographic incluye un controlador LocatabilityChanged que ya se ha creado. De forma predeterminada, se muestra una advertencia en la consola de depuración cuando el seguimiento posicional no está disponible. Puede agregar código a este controlador para proporcionar una respuesta según sea necesario desde la aplicación.

Desde **AppMain. cpp:**

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

Las API de [asignación espacial](spatial-mapping-in-directx.md) hacen uso de los sistemas de coordenadas para obtener las transformaciones del modelo para las mallas de superficie.

## <a name="see-also"></a>Consulta también
* [Sistemas de coordenadas](coordinate-systems.md)
* [Delimitadores espaciales](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
