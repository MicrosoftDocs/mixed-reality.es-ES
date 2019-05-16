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
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="3b952-104">Sistemas de coordenadas en DirectX</span><span class="sxs-lookup"><span data-stu-id="3b952-104">Coordinate systems in DirectX</span></span>

<span data-ttu-id="3b952-105">[Sistemas de coordenadas](coordinate-systems.md) forman la base de comprensión espacial ofrecidas por las API de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="3b952-105">[Coordinate systems](coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="3b952-106">Hoy en día había sentado VR o dispositivos de sala de único VR establecer un sistema de coordenadas principal para representar su espacio sometidas a seguimiento.</span><span class="sxs-lookup"><span data-stu-id="3b952-106">Today's seated VR or single-room VR devices establish one primary coordinate system to represent their tracked space.</span></span> <span data-ttu-id="3b952-107">Los dispositivos de Windows Mixed Reality, como HoloLens están diseñados para usarse en entornos de gran tamaño indefinidos, con el dispositivo, detectar y conocer sus alrededores como el usuario le guía en torno a.</span><span class="sxs-lookup"><span data-stu-id="3b952-107">Windows Mixed Reality devices such as HoloLens are designed to be used throughout large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="3b952-108">Esto permite que el dispositivo para adaptarse a mejorar continuamente conocimientos acerca de las salas del usuario, pero los sistemas de coordenadas que cambiará su relación entre sí a través de la duración de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b952-108">This allows the device to adapt to continually-improving knowledge about the user's rooms, but results in coordinate systems that will change their relationship to one another through the lifetime of the app.</span></span> <span data-ttu-id="3b952-109">Windows Mixed Reality admite una amplia gama de dispositivos, que abarcan desde su asiento inmersivos a través de fotogramas de referencia mundo conectado.</span><span class="sxs-lookup"><span data-stu-id="3b952-109">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="3b952-110">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="3b952-110">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="3b952-111">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="3b952-111">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="3b952-112">Sistemas de coordenadas espaciales en Windows</span><span class="sxs-lookup"><span data-stu-id="3b952-112">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="3b952-113">El tipo de núcleo utilizado para razonar sobre sistemas de coordenadas del mundo real en Windows es el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span><span class="sxs-lookup"><span data-stu-id="3b952-113">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="3b952-114">Una instancia de este tipo representa un sistema de coordenadas arbitrario y proporciona un método para obtener una matriz de transformación que puede usar para realizar transformaciones entre dos sistemas de coordenadas sin conocer los detalles de cada uno.</span><span class="sxs-lookup"><span data-stu-id="3b952-114">An instance of this type represents an arbitrary coordinate system and provides a method to get a transformation matrix that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="3b952-115">Los métodos que devuelven información espacial, representado como puntos, rayos o volúmenes en el entorno del usuario, aceptará un parámetro SpatialCoordinateSystem para que pueda decidir el sistema de coordenadas en el que resulta más útil para esas coordenadas que se va a devolver.</span><span class="sxs-lookup"><span data-stu-id="3b952-115">Methods that return spatial information, represented as points, rays, or volumes in the user's surroundings, will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="3b952-116">Las unidades para estas coordenadas siempre será en metros.</span><span class="sxs-lookup"><span data-stu-id="3b952-116">The units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="3b952-117">Un SpatialCoordinateSystem tiene una relación con otros sistemas de coordenadas, las que representan la posición del dispositivo incluidas dinámica.</span><span class="sxs-lookup"><span data-stu-id="3b952-117">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="3b952-118">En cualquier momento, el dispositivo puede ser capaz de encontrar algunos sistemas de coordenadas y otras no.</span><span class="sxs-lookup"><span data-stu-id="3b952-118">At any point in time, the device may be able to locate some coordinate systems and not others.</span></span> <span data-ttu-id="3b952-119">Para la mayoría de los sistemas de coordenadas, la aplicación debe estar lista para controlar los períodos de tiempo durante el cual no se encuentra.</span><span class="sxs-lookup"><span data-stu-id="3b952-119">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="3b952-120">La aplicación no debería crear SpatialCoordinateSystems directamente: en su lugar debe utilizarse a través de la API de percepción.</span><span class="sxs-lookup"><span data-stu-id="3b952-120">Your application should not create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="3b952-121">Existen tres fuentes principales de sistemas de coordenadas en las API de percepción, cada uno de los que se asignan a un concepto que se describe en el [sistemas de coordenadas](coordinate-systems.md) página:</span><span class="sxs-lookup"><span data-stu-id="3b952-121">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](coordinate-systems.md) page:</span></span>
* <span data-ttu-id="3b952-122">Para obtener un marco estático de referencia, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> u obtener uno desde la actual <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="3b952-122">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="3b952-123">Para obtener un anclaje espacial, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span><span class="sxs-lookup"><span data-stu-id="3b952-123">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="3b952-124">Para obtener un marco de referencia adjunta, cree un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span><span class="sxs-lookup"><span data-stu-id="3b952-124">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="3b952-125">Todos los sistemas de coordenadas devueltos por estos objetos son diestros con + arriba + x y a la derecha y + z con versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="3b952-125">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="3b952-126">Puede recordar qué dirección de los puntos de eje z positivo eligiendo los dedos de su mano derecha o izquierda en la dirección del eje x positivo y ellos cURL en la dirección del eje y positivo.</span><span class="sxs-lookup"><span data-stu-id="3b952-126">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="3b952-127">La dirección a la que apunta el pulgar (acercándose o alejándose de ti) es la dirección que el eje z positivo apunta para ese sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="3b952-127">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="3b952-128">La siguiente ilustración muestra estos dos sistemas de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="3b952-128">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="3b952-129">![Sistemas de coordenadas derecho e izquierdos](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="3b952-129">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="3b952-130">*Sistemas de coordenadas derecho e izquierdos*</span><span class="sxs-lookup"><span data-stu-id="3b952-130">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="3b952-131">Para arrancar en un SpatialCoordinateSystem basándose en la posición de un HoloLens, utilice el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> clase para crear cualquier un adjunto o estacionario marco de referencia, como se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="3b952-131">To bootstrap into a SpatialCoordinateSystem based on the position of a HoloLens, use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference, as described in the sections below.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="3b952-132">Hologramas lugar del mundo mediante una fase espacial</span><span class="sxs-lookup"><span data-stu-id="3b952-132">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="3b952-133">El sistema de coordenadas para opacos inmersivos Windows Mixed Reality se tiene acceso con estático <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> propiedad.</span><span class="sxs-lookup"><span data-stu-id="3b952-133">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="3b952-134">Esta API proporciona un sistema de coordenadas, la información acerca de si está colocado el Reproductor o móviles, el límite de un área segura para recorrer en torno a si el Reproductor es móvil, y una indicación de si no los auriculares direccional.</span><span class="sxs-lookup"><span data-stu-id="3b952-134">This API provides a coordinate system, information about whether the player is seated or mobile, the boundary of a safe area for walking around if the player is mobile, and an indication of whether or not the headset is directional.</span></span> <span data-ttu-id="3b952-135">También hay un controlador de eventos para las actualizaciones a la fase espacial.</span><span class="sxs-lookup"><span data-stu-id="3b952-135">There is also an event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="3b952-136">En primer lugar, se obtenga la fase espacial y suscribirse a las actualizaciones:</span><span class="sxs-lookup"><span data-stu-id="3b952-136">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="3b952-137">El código para **inicialización fase espacial**</span><span class="sxs-lookup"><span data-stu-id="3b952-137">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="3b952-138">En el método OnCurrentChanged, la aplicación debe inspeccionar la fase espacial y actualizar en consecuencia la experiencia de Reproductor.</span><span class="sxs-lookup"><span data-stu-id="3b952-138">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience accordingly.</span></span> <span data-ttu-id="3b952-139">En este ejemplo, se proporciona una visualización de los límites de fase, así como la posición de inicio especificada por el usuario y el intervalo de la fase de vista y el intervalo de las propiedades de movimiento.</span><span class="sxs-lookup"><span data-stu-id="3b952-139">In this example, we provide a visualization of the stage boundary, as well as the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="3b952-140">Nos también revertir a nuestro propio sistema de coordenadas inmóvil, cuando no se puede proporcionar una fase.</span><span class="sxs-lookup"><span data-stu-id="3b952-140">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="3b952-141">El código para **actualización fase espacial**</span><span class="sxs-lookup"><span data-stu-id="3b952-141">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="3b952-142">El conjunto de vértices que definen los límites de la fase se proporcionan en el orden de las agujas del reloj.</span><span class="sxs-lookup"><span data-stu-id="3b952-142">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="3b952-143">El shell de Windows Mixed Reality dibuja una barrera en el límite cuando el usuario aproxima a él; es posible que desee triangularize el área transitable para sus propios fines.</span><span class="sxs-lookup"><span data-stu-id="3b952-143">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it; you may wish to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="3b952-144">El siguiente algoritmo puede utilizarse para triangularize la fase.</span><span class="sxs-lookup"><span data-stu-id="3b952-144">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="3b952-145">El código para **triangularization fase espacial**</span><span class="sxs-lookup"><span data-stu-id="3b952-145">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="3b952-146">Hologramas lugar del mundo mediante un marco estático de referencia</span><span class="sxs-lookup"><span data-stu-id="3b952-146">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="3b952-147">El [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) clase representa un marco de referencia que [permanece estacionario](coordinate-systems.md#stationary-frame-of-reference) en relación con el entorno del usuario como el usuario se mueve.</span><span class="sxs-lookup"><span data-stu-id="3b952-147">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="3b952-148">Este marco de referencia da prioridad a las coordenadas de mantener estable cerca del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3b952-148">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="3b952-149">Un uso de clave de un SpatialStationaryFrameOfReference es para que actúe como el sistema de coordenadas universales subyacentes dentro de un motor de representación al representar hologramas.</span><span class="sxs-lookup"><span data-stu-id="3b952-149">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="3b952-150">Para obtener un SpatialStationaryFrameOfReference, use el [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) clase y llamar a [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span><span class="sxs-lookup"><span data-stu-id="3b952-150">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="3b952-151">Desde el código de plantilla de aplicación Windows Holographic:</span><span class="sxs-lookup"><span data-stu-id="3b952-151">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="3b952-152">Marcos de referencia fijos están diseñados para proporcionar una posición en relación con el espacio total con ajuste perfecto.</span><span class="sxs-lookup"><span data-stu-id="3b952-152">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="3b952-153">Posiciones individuales dentro de ese marco de referencia pueden variar ligeramente.</span><span class="sxs-lookup"><span data-stu-id="3b952-153">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="3b952-154">Esto es normal, ya que el dispositivo aprende más sobre el entorno.</span><span class="sxs-lookup"><span data-stu-id="3b952-154">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="3b952-155">Cuando se requiere la posición precisa de hologramas individuales, se debe usar un SpatialAnchor para delimitar el holograma individual a una posición en el mundo real: por ejemplo, un punto el usuario indica para que sea de especial interés.</span><span class="sxs-lookup"><span data-stu-id="3b952-155">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="3b952-156">No se desvíen posiciones de anclaje, pero pueden corregirse; el delimitador utilizará la posición corregida a partir de la siguiente después de que se ha producido la corrección.</span><span class="sxs-lookup"><span data-stu-id="3b952-156">Anchor positions do not drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="3b952-157">Hologramas lugar del mundo mediante delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="3b952-157">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="3b952-158">[Delimitadores espaciales](coordinate-systems.md#spatial-anchors) son una excelente manera de colocar hologramas en una ubicación específica en el mundo real, con el sistema lo que garantiza el delimitador permanece en su lugar con el tiempo.</span><span class="sxs-lookup"><span data-stu-id="3b952-158">[Spatial anchors](coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="3b952-159">En este tema se explica cómo crear y usar un delimitador y cómo trabajar con datos de anclaje.</span><span class="sxs-lookup"><span data-stu-id="3b952-159">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="3b952-160">Puede crear un SpatialAnchor en cualquier posición y orientación en el SpatialCoordinateSystem de su elección.</span><span class="sxs-lookup"><span data-stu-id="3b952-160">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="3b952-161">El dispositivo debe ser capaz de encontrar ese sistema de coordenadas en este momento, y debe el sistema no haya alcanzado su límite de delimitadores espaciales.</span><span class="sxs-lookup"><span data-stu-id="3b952-161">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="3b952-162">Una vez definido, el sistema de coordenadas de un SpatialAnchor ajusta continuamente para conservar la posición exacta y orientación de su ubicación inicial.</span><span class="sxs-lookup"><span data-stu-id="3b952-162">Once defined, the coordinate system of a SpatialAnchor adjusts continually to retain the precise position and orientation of its initial location.</span></span> <span data-ttu-id="3b952-163">A continuación, puede usar este SpatialAnchor para representar hologramas que va a aparecer fijos en el entorno del usuario en esa ubicación exacta.</span><span class="sxs-lookup"><span data-stu-id="3b952-163">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="3b952-164">Los efectos de los ajustes que conservar el delimitador en su lugar se amplía como distancia desde los aumentos de anclaje.</span><span class="sxs-lookup"><span data-stu-id="3b952-164">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="3b952-165">Por lo tanto, debe evitar representar el contenido en relación con un delimitador que es de más de 3 metros de origen del anclaje.</span><span class="sxs-lookup"><span data-stu-id="3b952-165">Therefore, you should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="3b952-166">El [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) propiedad obtiene un sistema de coordenadas que le permite colocar contenido en relación con el delimitador, con la aceleración aplica cuando el dispositivo ajusta la ubicación exacta del anclaje.</span><span class="sxs-lookup"><span data-stu-id="3b952-166">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="3b952-167">Use la [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) propiedad y la correspondiente [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) eventos para administrar estos ajustes usted mismo.</span><span class="sxs-lookup"><span data-stu-id="3b952-167">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="3b952-168">Conservar y compartir los anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="3b952-168">Persist and share spatial anchors</span></span>

<span data-ttu-id="3b952-169">Puede conservar un SpatialAnchor localmente mediante el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) clase y, a continuación, volver a obtener, en una sesión de la aplicación en un futuro en el mismo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3b952-169">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="3b952-170">Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a>, puede crear un anclaje en la nube duraderas desde un SpatialAnchor local, que, a continuación, puede localizar su aplicación a través de varios HoloLens, dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="3b952-170">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3b952-171">Al compartir un anclaje espacial comunes en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="3b952-171">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="3b952-172">Esto permite experiencias compartidas en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="3b952-172">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="3b952-173">También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para la persistencia holograma asincrónica a través de dispositivos Android, iOS y HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3b952-173">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3b952-174">Al compartir un anclaje espacial en la nube duraderas, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes entre sí al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="3b952-174">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="3b952-175">Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">inicio rápido de Azure espacial delimitadores HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="3b952-175">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="3b952-176">Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y localizar los anclajes en HoloLens</a>.</span><span class="sxs-lookup"><span data-stu-id="3b952-176">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="3b952-177">Los tutoriales están disponibles para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS y Android</a> así, lo que le permite compartir los delimitadores de la mismos en todos los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3b952-177">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="3b952-178">Crear SpatialAnchors contenido holográfica</span><span class="sxs-lookup"><span data-stu-id="3b952-178">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="3b952-179">Para este ejemplo de código, hemos modificado Windows Holographic cree la plantilla de aplicación cuando ancla el **Pressed** se detecta el gesto.</span><span class="sxs-lookup"><span data-stu-id="3b952-179">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="3b952-180">El cubo, a continuación, se coloca en el delimitador durante la fase de representación.</span><span class="sxs-lookup"><span data-stu-id="3b952-180">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="3b952-181">Puesto que varios delimitadores son compatibles con la clase auxiliar, podemos colocamos tantos cubos como queremos utilizar este ejemplo de código.</span><span class="sxs-lookup"><span data-stu-id="3b952-181">Since multiple anchors are supported by the helper class, we can place as many cubes as we want using this code sample!</span></span>

<span data-ttu-id="3b952-182">Tenga en cuenta que los identificadores para delimitadores son algo que controlar en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b952-182">Note that the IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="3b952-183">En este ejemplo, hemos creado un esquema de nomenclatura es secuencial en función del número de delimitadores almacenados actualmente en la colección de la aplicación de delimitadores.</span><span class="sxs-lookup"><span data-stu-id="3b952-183">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="3b952-184">De forma asincrónica cargar y almacenar en caché, el SpatialAnchorStore</span><span class="sxs-lookup"><span data-stu-id="3b952-184">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="3b952-185">Veamos cómo escribir una clase SampleSpatialAnchorHelper que ayuda a controlar esta persistencia, incluidos:</span><span class="sxs-lookup"><span data-stu-id="3b952-185">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="3b952-186">Almacenar una colección de delimitadores en memoria, se indexan mediante una clave de Platform:: String.</span><span class="sxs-lookup"><span data-stu-id="3b952-186">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="3b952-187">Cargar los anclajes de SpatialAnchorStore del sistema, que se mantienen separado de la colección en memoria local.</span><span class="sxs-lookup"><span data-stu-id="3b952-187">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="3b952-188">Guardando la colección en memoria local de delimitadores en el SpatialAnchorStore cuando la aplicación opta por hacerlo.</span><span class="sxs-lookup"><span data-stu-id="3b952-188">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="3b952-189">Aquí le mostramos cómo guardar [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objetos en el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="3b952-189">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="3b952-190">Cuando se inicia la clase, se solicita la SpatialAnchorStore asincrónicamente.</span><span class="sxs-lookup"><span data-stu-id="3b952-190">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="3b952-191">Esto implica la E/S del sistema como la API de carga de la tienda y se realiza esta API asincrónica para que la E/S es sin bloqueo.</span><span class="sxs-lookup"><span data-stu-id="3b952-191">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="3b952-192">Se le ofrecerá un SpatialAnchorStore que puede usar para guardar los delimitadores.</span><span class="sxs-lookup"><span data-stu-id="3b952-192">You will be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="3b952-193">Se trata de un IMapView que asocia los valores de clave que son cadenas, con los valores que son SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="3b952-193">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="3b952-194">En nuestro código de ejemplo, se almacena en una variable de miembro de clase privada es accesible a través de una función pública de nuestra clase auxiliar.</span><span class="sxs-lookup"><span data-stu-id="3b952-194">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="3b952-195">No se olvide de enlazar los eventos de suspensiones y reanudaciones para guardar y cargar el almacén de anclaje.</span><span class="sxs-lookup"><span data-stu-id="3b952-195">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="3b952-196">Guardar el contenido en el almacén de anclaje</span><span class="sxs-lookup"><span data-stu-id="3b952-196">Save content to the anchor store</span></span>

<span data-ttu-id="3b952-197">Cuando el sistema suspende la aplicación, deberá guardar los delimitadores espaciales en el almacén de anclaje.</span><span class="sxs-lookup"><span data-stu-id="3b952-197">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="3b952-198">También puede elegir guardar delimitadores en el almacén de anclaje en otras ocasiones, como encontrar para que sea necesario para la implementación de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b952-198">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="3b952-199">Cuando esté listo para intentar guardar los anclajes en memoria en el SpatialAnchorStore, puede recorrer en iteración la colección e intenta guardar cada uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="3b952-199">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="3b952-200">Cargar contenido desde el almacén de anclaje cuando se reanuda la aplicación</span><span class="sxs-lookup"><span data-stu-id="3b952-200">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="3b952-201">Cuando se reanuda la aplicación, o en cualquier momento es necesario para implementaiton de la aplicación, puede restaurar los delimitadores que anteriormente se guardaron en el AnchorStore mediante la transferencia desde IMapView de la tienda de anclaje a su propia base de datos en memoria SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="3b952-201">When your app resumes, or at any other time necessary for your app's implementaiton, you can restore anchors that were previously saved to the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors.</span></span>

<span data-ttu-id="3b952-202">Para restaurar los delimitadores de la SpatialAnchorStore, restaurar cada uno de ellos que interesa a su propia colección en memoria.</span><span class="sxs-lookup"><span data-stu-id="3b952-202">To restore anchors from the SpatialAnchorStore, restore each one that you are interested in to your own in-memory collection.</span></span>

<span data-ttu-id="3b952-203">Necesitará su propia base de datos en memoria de SpatialAnchors; alguna manera de asociar el SpatialAnchors que cree en cadenas.</span><span class="sxs-lookup"><span data-stu-id="3b952-203">You need your own in-memory database of SpatialAnchors; some way to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="3b952-204">En nuestro código de ejemplo, se decide usar un Windows::Foundation::Collections::IMap para almacenar los delimitadores, lo que facilita que se usará el mismo valor de clave y los datos para el SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="3b952-204">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="3b952-205">Un delimitador que se restaura podría no ser localizable inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="3b952-205">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="3b952-206">Por ejemplo, podría ser un delimitador en la misma habitación o en un edificio diferente por completo.</span><span class="sxs-lookup"><span data-stu-id="3b952-206">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="3b952-207">Delimitadores de recuperarse el AnchorStore deben probarse para locatability antes de usarlos.</span><span class="sxs-lookup"><span data-stu-id="3b952-207">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="3b952-208">En este código de ejemplo, recuperamos todos los delimitadores de la AnchorStore.</span><span class="sxs-lookup"><span data-stu-id="3b952-208">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="3b952-209">Esto no es un requisito; la aplicación podría igual de bien elegir un subconjunto determinado de delimitadores mediante el uso de valores de clave de cadena que son significativos para su implementación.</span><span class="sxs-lookup"><span data-stu-id="3b952-209">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="3b952-210">Borrar el almacén de anclaje, cuando sea necesario</span><span class="sxs-lookup"><span data-stu-id="3b952-210">Clear the anchor store, when needed</span></span>

<span data-ttu-id="3b952-211">A veces, debe borrar el estado de la aplicación y escribir nuevos datos.</span><span class="sxs-lookup"><span data-stu-id="3b952-211">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="3b952-212">Así es cómo hacer que con el [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span><span class="sxs-lookup"><span data-stu-id="3b952-212">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="3b952-213">Con nuestra clase auxiliar, no es prácticamente necesario ajustar la función Clear.</span><span class="sxs-lookup"><span data-stu-id="3b952-213">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="3b952-214">Se elige esta opción en nuestra implementación de ejemplo, dado que nuestra clase auxiliar tiene la responsabilidad de propietario de la instancia de SpatialAnchorStore.</span><span class="sxs-lookup"><span data-stu-id="3b952-214">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="3b952-215">Por ejemplo: Relacionados con los sistemas de coordenadas de anclaje para sistemas de coordenadas de marco de referencia estacionarios</span><span class="sxs-lookup"><span data-stu-id="3b952-215">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="3b952-216">Supongamos que tiene un anclaje y desea relacionar algo en el sistema de coordenadas del su anclaje a la SpatialStationaryReferenceFrame que ya esté usando para la mayoría de sus otros contenidos.</span><span class="sxs-lookup"><span data-stu-id="3b952-216">Let's say that you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame that you’re already using for most of your other content.</span></span> <span data-ttu-id="3b952-217">Puede usar [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) para obtener una transformación de sistema de coordenadas del anclaje a la del marco estático referencia:</span><span class="sxs-lookup"><span data-stu-id="3b952-217">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to obtain a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="3b952-218">Este proceso es útil de dos maneras:</span><span class="sxs-lookup"><span data-stu-id="3b952-218">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="3b952-219">Indica si los dos marcos de referencia pueda entender con respecto a otro, y;</span><span class="sxs-lookup"><span data-stu-id="3b952-219">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="3b952-220">Si es así, proporciona una transformación para ir directamente desde un sistema de coordenadas a otro.</span><span class="sxs-lookup"><span data-stu-id="3b952-220">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="3b952-221">Con esta información, tiene un conocimiento de la relación entre los objetos entre los dos marcos de referencia espacial.</span><span class="sxs-lookup"><span data-stu-id="3b952-221">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="3b952-222">Para la representación, a menudo puede obtener mejores resultados mediante la agrupación de objetos según su marco de referencia original o el delimitador.</span><span class="sxs-lookup"><span data-stu-id="3b952-222">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="3b952-223">Realizar un paso de dibujo independiente para cada grupo.</span><span class="sxs-lookup"><span data-stu-id="3b952-223">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="3b952-224">Las matrices de vista son más precisas para los objetos con transformaciones de modelo que se crean inicialmente con el mismo sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="3b952-224">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="3b952-225">Crear hologramas mediante un dispositivo conectado marco de referencia</span><span class="sxs-lookup"><span data-stu-id="3b952-225">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="3b952-226">Hay veces cuando desee representar un holograma que [permanecen adjuntas](coordinate-systems.md#attached-frame-of-reference) a la ubicación del dispositivo, por ejemplo, un panel con un mensaje informativo o información de depuración cuando el dispositivo solo es capaz de determinar su orientación y no es su posición en el espacio.</span><span class="sxs-lookup"><span data-stu-id="3b952-226">There are times when you want to render a hologram that [remains attached](coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="3b952-227">Para lograr esto, usamos un marco de referencia adjunta.</span><span class="sxs-lookup"><span data-stu-id="3b952-227">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="3b952-228">La clase SpatialLocatorAttachedFrameOfReference define los sistemas de coordenadas que son en relación con el dispositivo en lugar de en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="3b952-228">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="3b952-229">Este marco tiene un encabezado fijo con respecto al entorno del usuario que se apunta en la dirección del usuario cuando se creó el marco de referencia.</span><span class="sxs-lookup"><span data-stu-id="3b952-229">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="3b952-230">Desde ese momento, todas las orientaciones en este marco de referencia son con respecto a ese encabezado fijo, incluso cuando el usuario gira el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3b952-230">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="3b952-231">Para HoloLens, el origen del sistema de coordenadas de este fotograma se encuentra en el centro de rotación de la cabeza del usuario, por lo que su posición no se ve afectada por la rotación principal.</span><span class="sxs-lookup"><span data-stu-id="3b952-231">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="3b952-232">La aplicación puede especificar un desplazamiento con respecto a este punto para colocar hologramas delante del usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-232">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="3b952-233">Para obtener un SpatialLocatorAttachedFrameOfReference, utilice la clase SpatialLocator y llamar a CreateAttachedFrameOfReferenceAtCurrentHeading.</span><span class="sxs-lookup"><span data-stu-id="3b952-233">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="3b952-234">Tenga en cuenta que esto se aplica a los dispositivos de la completa gama de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="3b952-234">Note that this applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="3b952-235">Utilice un marco de referencia asociado al dispositivo</span><span class="sxs-lookup"><span data-stu-id="3b952-235">Use a reference frame attached to the device</span></span>

<span data-ttu-id="3b952-236">Estas secciones hablan sobre lo que hemos cambiado en la plantilla de aplicación de Windows Holographic para habilitar un dispositivo conectado marco de referencia mediante esta API.</span><span class="sxs-lookup"><span data-stu-id="3b952-236">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="3b952-237">Tenga en cuenta que funcionará junto con hologramas delimitados o estacionarios Este holograma "conectado" y también se puede usar cuando el dispositivo está temporalmente no se puede buscar su posición en el mundo.</span><span class="sxs-lookup"><span data-stu-id="3b952-237">Note that this "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="3b952-238">En primer lugar, hemos cambiado la plantilla para almacenar un SpatialLocatorAttachedFrameOfReference en lugar de un SpatialStationaryFrameOfReference:</span><span class="sxs-lookup"><span data-stu-id="3b952-238">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="3b952-239">Desde **HolographicTagAlongSampleMain.h**:</span><span class="sxs-lookup"><span data-stu-id="3b952-239">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="3b952-240">Desde **HolographicTagAlongSampleMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="3b952-240">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="3b952-241">Durante la actualización, se obtiene el sistema de coordenadas en la marca de tiempo obtenida con la predicción de marco.</span><span class="sxs-lookup"><span data-stu-id="3b952-241">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="3b952-242">Obtener una postura puntero espaciales y siga la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="3b952-242">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="3b952-243">Queremos que nuestra holograma de ejemplo para seguir al usuario [que mirar](gaze.md), de forma similar a cómo el shell holográfico puede seguir mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-243">We want our example hologram to follow the user's [gaze](gaze.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="3b952-244">Para ello, es necesario obtener el SpatialPointerPose desde la misma marca de tiempo.</span><span class="sxs-lookup"><span data-stu-id="3b952-244">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="3b952-245">Este SpatialPointerPose tiene la información necesaria para colocar el holograma según la [título actual del usuario](gaze-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="3b952-245">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="3b952-246">Por motivos de comodidad, usamos la interpolación lineal ("lerp") para suavizar el cambio de posición de forma que producen durante un período de tiempo.</span><span class="sxs-lookup"><span data-stu-id="3b952-246">For reasons of user comfort, we use linear interpolation ("lerp") to smooth the change in position such that it occurs over a period of time.</span></span> <span data-ttu-id="3b952-247">Esto es más cómodo para el usuario que bloquear el holograma a su mirada.</span><span class="sxs-lookup"><span data-stu-id="3b952-247">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="3b952-248">Lerping que posición del holograma de tag-along también nos permite estabilizar el holograma por amortiguar el movimiento. Si no lo hicimos esta restricción, el usuario vería el holograma vibración debido a lo que normalmente se considera que imperceptibles movimientos de head del usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-248">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement; if we did not do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="3b952-249">Desde **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="3b952-249">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="3b952-250">En el caso de un panel de depuración, puede volver a colocar el holograma desactivar al lado un poco para que no obstruye la vista.</span><span class="sxs-lookup"><span data-stu-id="3b952-250">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it does not obstruct your view.</span></span> <span data-ttu-id="3b952-251">Este es un ejemplo de cómo podría hacer eso.</span><span class="sxs-lookup"><span data-stu-id="3b952-251">Here's an example of how you might do that.</span></span>

<span data-ttu-id="3b952-252">Para **StationaryQuadRenderer::PositionHologram**:</span><span class="sxs-lookup"><span data-stu-id="3b952-252">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="3b952-253">Girar el holograma para enfrentar la cámara</span><span class="sxs-lookup"><span data-stu-id="3b952-253">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="3b952-254">No es suficiente colocar simplemente el holograma, que en este caso es un cuadrado; También nos debemos rotar el objeto para enfrentar el usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-254">It is not enough to simply position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="3b952-255">Tenga en cuenta que este giro se produce en el espacio global, porque este tipo de vallas publicitarias permite el holograma siga siendo una parte del entorno de usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-255">Note that this rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="3b952-256">Vallas publicitarias espacio de la vista no es tan cómodo porque el holograma queda bloqueado para la orientación de la pantalla; en ese caso, también debe interpolar entre las matrices de vista izquierda y derecha con el fin de adquirir una transformación de cartelera de espacio de la vista que no interrumpen la representación estéreo.</span><span class="sxs-lookup"><span data-stu-id="3b952-256">View-space billboarding is not as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices in order to acquire a view-space billboard transform that does not disrupt stereo rendering.</span></span> <span data-ttu-id="3b952-257">En este caso, se gira en los ejes X y Z para afrontar el usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-257">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="3b952-258">Desde **StationaryQuadRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="3b952-258">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="3b952-259">Representar el holograma adjunto</span><span class="sxs-lookup"><span data-stu-id="3b952-259">Render the attached hologram</span></span>

<span data-ttu-id="3b952-260">En este ejemplo, elegimos también representar el holograma en el sistema de coordenadas de la SpatialLocatorAttachedReferenceFrame, que es donde se coloca el holograma.</span><span class="sxs-lookup"><span data-stu-id="3b952-260">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="3b952-261">(Si hubiéramos decidido representar con otro sistema de coordenadas, se deberá adquirir una transformación de sistema de coordenadas del marco de referencia de dispositivo conectado a ese sistema de coordenadas.)</span><span class="sxs-lookup"><span data-stu-id="3b952-261">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="3b952-262">Desde **HolographicTagAlongSampleMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="3b952-262">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="3b952-263">Ya está.</span><span class="sxs-lookup"><span data-stu-id="3b952-263">That's it!</span></span> <span data-ttu-id="3b952-264">El holograma ahora se "chase" una posición que es de 2 metros delante de la dirección de mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="3b952-264">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="3b952-265">Este ejemplo también carga contenido adicional: consulte StationaryQuadRenderer.cpp.</span><span class="sxs-lookup"><span data-stu-id="3b952-265">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="3b952-266">Seguimiento de la pérdida de control</span><span class="sxs-lookup"><span data-stu-id="3b952-266">Handling tracking loss</span></span>

<span data-ttu-id="3b952-267">Cuando el dispositivo no puede encontrar a sí mismo en el mundo, la aplicación experimenta "pérdida de seguimiento".</span><span class="sxs-lookup"><span data-stu-id="3b952-267">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="3b952-268">Windows Mixed Reality apps deben ser capaces de controlar dichas interrupciones para el sistema de seguimiento posicional.</span><span class="sxs-lookup"><span data-stu-id="3b952-268">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="3b952-269">Se pueden observar estas interrupciones y respuestas crean, mediante el evento LocatabilityChanged en el valor predeterminado SpatialLocator.</span><span class="sxs-lookup"><span data-stu-id="3b952-269">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="3b952-270">Desde **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="3b952-270">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="3b952-271">Cuando la aplicación recibe un evento LocatabilityChanged, puede cambiar el comportamiento según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="3b952-271">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="3b952-272">Por ejemplo, en el estado PositionalTrackingInhibited, la aplicación puede pausar el funcionamiento normal y representar un [holograma tag-along](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) que muestra un mensaje de advertencia.</span><span class="sxs-lookup"><span data-stu-id="3b952-272">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="3b952-273">La plantilla de aplicación de Windows Holographic viene con un controlador LocatabilityChanged ya ha creado para usted.</span><span class="sxs-lookup"><span data-stu-id="3b952-273">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="3b952-274">De forma predeterminada, muestra una advertencia en la consola de depuración al seguimiento posicional no está disponible.</span><span class="sxs-lookup"><span data-stu-id="3b952-274">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="3b952-275">Puede agregar código a este controlador para proporcionar una respuesta, según sea necesario desde la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b952-275">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="3b952-276">Desde **AppMain.cpp:**</span><span class="sxs-lookup"><span data-stu-id="3b952-276">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="3b952-277">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="3b952-277">Spatial mapping</span></span>

<span data-ttu-id="3b952-278">El [asignación espacial](spatial-mapping-in-directx.md) API facilitan el uso de sistemas de coordenadas para obtener las transformaciones de modelos de mallas de superficie.</span><span class="sxs-lookup"><span data-stu-id="3b952-278">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b952-279">Vea también</span><span class="sxs-lookup"><span data-stu-id="3b952-279">See also</span></span>
* [<span data-ttu-id="3b952-280">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="3b952-280">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="3b952-281">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="3b952-281">Spatial anchors</span></span>](spatial-anchors.md)
* <span data-ttu-id="3b952-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="3b952-282"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="3b952-283">Mirada principal y de ojo de DirectX</span><span class="sxs-lookup"><span data-stu-id="3b952-283">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="3b952-284">Las manos y los controladores de movimiento de DirectX</span><span class="sxs-lookup"><span data-stu-id="3b952-284">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="3b952-285">Asignación espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="3b952-285">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
