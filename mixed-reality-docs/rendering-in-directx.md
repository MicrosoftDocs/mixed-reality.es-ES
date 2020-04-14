---
title: Representación en DirectX
description: Explica la representación holográfica para Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, representación, gráficos 3D, HolographicFrame, bucle de representación, bucle de actualización, tutorial, código de ejemplo, Direct3D
ms.openlocfilehash: a781093e0054a986b81a0e284e03076dd018f8c0
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277513"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="384a6-104">Representación en DirectX</span><span class="sxs-lookup"><span data-stu-id="384a6-104">Rendering in DirectX</span></span>

<span data-ttu-id="384a6-105">Windows Mixed Reality se basa en DirectX para generar experiencias gráficas 3D enriquecidas para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="384a6-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="384a6-106">La abstracción de representación se encuentra justo encima de DirectX y permite que una aplicación tenga en la posición y la orientación de uno o más observadores de una escena holográfica, tal y como lo predice el sistema.</span><span class="sxs-lookup"><span data-stu-id="384a6-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="384a6-107">A continuación, el desarrollador puede localizar sus hologramas en relación con cada cámara, lo que permite que la aplicación represente estos hologramas en varios sistemas de coordenadas espaciales a medida que el usuario se desplaza.</span><span class="sxs-lookup"><span data-stu-id="384a6-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="384a6-108">Nota: en este tutorial se describe la representación holográfica en Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="384a6-108">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="384a6-109">También se proporciona una plantilla de aplicación de Windows mixed reality de Direct3D 12 con la extensión de plantillas de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="384a6-109">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="384a6-110">Actualizar para el marco actual</span><span class="sxs-lookup"><span data-stu-id="384a6-110">Update for the current frame</span></span>

<span data-ttu-id="384a6-111">Para actualizar el estado de la aplicación para los hologramas, una vez por fotograma, la aplicación:</span><span class="sxs-lookup"><span data-stu-id="384a6-111">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="384a6-112">Obtiene un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> del sistema de administración de pantalla.</span><span class="sxs-lookup"><span data-stu-id="384a6-112">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="384a6-113">Actualice la escena con la predicción actual de en la que se mostrará la vista de cámara cuando se complete el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="384a6-113">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="384a6-114">Tenga en cuenta que puede haber más de una cámara para la escena holográfica.</span><span class="sxs-lookup"><span data-stu-id="384a6-114">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="384a6-115">Para representar vistas de cámara holográfica, una vez por fotograma, la aplicación:</span><span class="sxs-lookup"><span data-stu-id="384a6-115">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="384a6-116">Para cada cámara, represente la escena del fotograma actual, usando la vista de cámara y las matrices de proyección del sistema.</span><span class="sxs-lookup"><span data-stu-id="384a6-116">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="384a6-117">Crear un nuevo marco holográfica y obtener su predicción</span><span class="sxs-lookup"><span data-stu-id="384a6-117">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="384a6-118"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tiene información que la aplicación necesita para actualizar y representar el fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="384a6-118">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="384a6-119">La aplicación comienza cada nuevo fotograma llamando al método **CreateNextFrame** .</span><span class="sxs-lookup"><span data-stu-id="384a6-119">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="384a6-120">Cuando se llama a este método, las predicciones se realizan utilizando los datos del sensor más recientes disponibles y se encapsulan en el objeto **CurrentPrediction** .</span><span class="sxs-lookup"><span data-stu-id="384a6-120">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="384a6-121">Se debe usar un nuevo objeto de marco para cada fotograma representado, ya que solo es válido para un momento dado.</span><span class="sxs-lookup"><span data-stu-id="384a6-121">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="384a6-122">La propiedad **CurrentPrediction** contiene información como la posición de la cámara.</span><span class="sxs-lookup"><span data-stu-id="384a6-122">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="384a6-123">La información se extrapola al momento exacto en que se espera que el marco sea visible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="384a6-123">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="384a6-124">El código siguiente se ha extraído de **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="384a6-124">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="384a6-125">Procesar actualizaciones de la cámara</span><span class="sxs-lookup"><span data-stu-id="384a6-125">Process camera updates</span></span>

<span data-ttu-id="384a6-126">Los búferes de reserva pueden cambiar de fotograma a fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-126">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="384a6-127">La aplicación debe validar el búfer de reserva de cada cámara y liberar y volver a crear las vistas de recursos y los búferes de profundidad según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="384a6-127">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="384a6-128">Observe que el conjunto de supuestos de la predicción es la lista autoritativa de cámaras que se usan en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="384a6-128">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="384a6-129">Normalmente, esta lista se usa para iterar en el conjunto de cámaras.</span><span class="sxs-lookup"><span data-stu-id="384a6-129">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="384a6-130">Desde **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="384a6-130">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="384a6-131">De **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="384a6-131">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="384a6-132">Obtención del sistema de coordenadas que se va a usar como base para la representación</span><span class="sxs-lookup"><span data-stu-id="384a6-132">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="384a6-133">Windows Mixed Reality permite que la aplicación cree varios [sistemas de coordenadas](coordinate-systems-in-directx.md) según sea necesario, como el marco de referencia adjunto y el marco de referencia estacionario, que realizan un seguimiento de las ubicaciones del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="384a6-133">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="384a6-134">A continuación, la aplicación puede usar estos sistemas de coordenadas para pensar en dónde representar los hologramas en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-134">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="384a6-135">Cuando se solicitan coordenadas de una API, siempre se pasa el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> en el que se desea expresar esas coordenadas.</span><span class="sxs-lookup"><span data-stu-id="384a6-135">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="384a6-136">Desde **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="384a6-136">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="384a6-137">Estos sistemas de coordenadas se pueden usar para generar matrices de vista estéreo al representar el contenido de la escena.</span><span class="sxs-lookup"><span data-stu-id="384a6-137">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="384a6-138">Desde **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="384a6-138">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="384a6-139">Entrada de movimiento y miración de proceso</span><span class="sxs-lookup"><span data-stu-id="384a6-139">Process gaze and gesture input</span></span>

<span data-ttu-id="384a6-140">La entrada de [mirada](gaze-in-directx.md) y la [mano](hands-and-motion-controllers-in-directx.md) no se basan en el tiempo y, por tanto, no tienen que actualizarse en la función **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="384a6-140">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="384a6-141">Sin embargo, esta entrada es algo que la aplicación debe buscar en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-141">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="384a6-142">Procesar actualizaciones basadas en el tiempo</span><span class="sxs-lookup"><span data-stu-id="384a6-142">Process time-based updates</span></span>

<span data-ttu-id="384a6-143">Cualquier aplicación de representación en tiempo real necesitará alguna manera de procesar las actualizaciones basadas en el tiempo. Proporcionamos una forma de hacerlo en la plantilla de aplicación de Windows Holographic a través de una implementación de **StepTimer** .</span><span class="sxs-lookup"><span data-stu-id="384a6-143">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="384a6-144">Esto es similar a la StepTimer que se proporciona en la plantilla de aplicación para UWP de DirectX 11, por lo que si ya ha examinado la plantilla, debe estar familiarizado con los conocimientos.</span><span class="sxs-lookup"><span data-stu-id="384a6-144">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="384a6-145">Esta clase auxiliar de ejemplo StepTimer es capaz de proporcionar actualizaciones fijas de pasos temporales, así como actualizaciones de pasos temporales variables, y el modo predeterminado es pasos de tiempo variable.</span><span class="sxs-lookup"><span data-stu-id="384a6-145">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="384a6-146">En el caso de la representación holográfica, hemos elegido específicamente no incluir demasiado en la función de temporizador.</span><span class="sxs-lookup"><span data-stu-id="384a6-146">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="384a6-147">Esto se debe a que puede configurarlo para que sea un paso de tiempo fijo, en cuyo caso se podría llamar a más de una vez por fotograma (o no, en absoluto) en algunos fotogramas, y las actualizaciones de datos holográficas deben realizarse una vez por fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-147">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="384a6-148">Desde **AppMain:: Update**:</span><span class="sxs-lookup"><span data-stu-id="384a6-148">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="384a6-149">Colocar y girar los hologramas en el sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="384a6-149">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="384a6-150">Si está trabajando en un único sistema de coordenadas, como hace la plantilla con el **SpatialStationaryReferenceFrame**, este proceso no es diferente de lo que se usa en los gráficos 3D.</span><span class="sxs-lookup"><span data-stu-id="384a6-150">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="384a6-151">Aquí se gira el cubo y se establece la matriz del modelo en relación con la posición en el sistema de coordenadas estacionales.</span><span class="sxs-lookup"><span data-stu-id="384a6-151">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="384a6-152">Desde **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="384a6-152">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

<span data-ttu-id="384a6-153">**Tenga en cuenta los escenarios avanzados:** El cubo giratorio es un ejemplo muy sencillo de cómo colocar un holograma dentro de un solo fotograma de referencia.</span><span class="sxs-lookup"><span data-stu-id="384a6-153">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="384a6-154">También es posible [usar varios SpatialCoordinateSystems](coordinate-systems-in-directx.md) en el mismo fotograma representado al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="384a6-154">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="384a6-155">Actualizar datos de búfer de constantes</span><span class="sxs-lookup"><span data-stu-id="384a6-155">Update constant buffer data</span></span>

<span data-ttu-id="384a6-156">Las transformaciones del modelo para el contenido se actualizan de la forma habitual.</span><span class="sxs-lookup"><span data-stu-id="384a6-156">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="384a6-157">De momento, habrá calculado las transformaciones válidas para el sistema de coordenadas en el que se va a representar.</span><span class="sxs-lookup"><span data-stu-id="384a6-157">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="384a6-158">Desde **SpinningCubeRenderer:: Update**:</span><span class="sxs-lookup"><span data-stu-id="384a6-158">From **SpinningCubeRenderer::Update**:</span></span>

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

<span data-ttu-id="384a6-159">¿Qué ocurre con las transformaciones de visualización y proyección?</span><span class="sxs-lookup"><span data-stu-id="384a6-159">What about view and projection transforms?</span></span> <span data-ttu-id="384a6-160">Para obtener los mejores resultados, queremos esperar hasta que podamos estar casi preparados para las llamadas a Draw antes de obtenerlas.</span><span class="sxs-lookup"><span data-stu-id="384a6-160">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="384a6-161">Representar el marco actual</span><span class="sxs-lookup"><span data-stu-id="384a6-161">Render the current frame</span></span>

<span data-ttu-id="384a6-162">La representación en Windows Mixed Reality no es muy diferente de la representación en una pantalla mono 2D, pero hay algunas diferencias que debe tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="384a6-162">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="384a6-163">Las predicciones de tramas holográficas son importantes.</span><span class="sxs-lookup"><span data-stu-id="384a6-163">Holographic frame predictions are important.</span></span> <span data-ttu-id="384a6-164">Cuanto más se acerque la predicción a la presentación del fotograma, mejor se verán los hologramas.</span><span class="sxs-lookup"><span data-stu-id="384a6-164">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="384a6-165">Windows Mixed Reality controla las vistas de la cámara.</span><span class="sxs-lookup"><span data-stu-id="384a6-165">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="384a6-166">Debe representar cada una de ellas, ya que el marco holográfica las presentará más adelante.</span><span class="sxs-lookup"><span data-stu-id="384a6-166">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="384a6-167">Se recomienda que la representación de estéreo se realice mediante el dibujo con instancias en una matriz de destino de representación.</span><span class="sxs-lookup"><span data-stu-id="384a6-167">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="384a6-168">La plantilla de aplicación holográfica usa el enfoque recomendado del dibujo con instancias en una matriz de destino de representación, que usa una vista de destino de representación en un **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="384a6-168">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="384a6-169">Si desea representar sin usar la creación de instancias de estéreo, tendrá que crear dos RenderTargetViews que no sean de matriz (uno para cada ojo) que cada una de ellas haga referencia a uno de los dos segmentos del **Texture2DArray** proporcionado a la aplicación desde el sistema.</span><span class="sxs-lookup"><span data-stu-id="384a6-169">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="384a6-170">Esto no se recomienda, ya que normalmente es significativamente más lento que el uso de la creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="384a6-170">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="384a6-171">Obtener una predicción HolographicFrame actualizada</span><span class="sxs-lookup"><span data-stu-id="384a6-171">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="384a6-172">La actualización de la predicción de fotogramas mejora la eficacia de la estabilización de imágenes y permite un posicionamiento más preciso de los hologramas debido al tiempo más corto entre la predicción y el momento en el que el usuario puede ver el marco.</span><span class="sxs-lookup"><span data-stu-id="384a6-172">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="384a6-173">Idealmente, actualice la predicción de fotogramas justo antes de la representación.</span><span class="sxs-lookup"><span data-stu-id="384a6-173">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="384a6-174">Representar en cada cámara</span><span class="sxs-lookup"><span data-stu-id="384a6-174">Render to each camera</span></span>

<span data-ttu-id="384a6-175">Bucle en el conjunto de repeticiones de la cámara en la predicción y representar en cada cámara de este conjunto.</span><span class="sxs-lookup"><span data-stu-id="384a6-175">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="384a6-176">**Configurar el paso de representación**</span><span class="sxs-lookup"><span data-stu-id="384a6-176">**Set up your rendering pass**</span></span>

<span data-ttu-id="384a6-177">Windows Mixed Reality usa la representación Stereoscopic para mejorar la ilusión de profundidad y representar stereoscopically, por lo que tanto la pantalla izquierda como la derecha están activas.</span><span class="sxs-lookup"><span data-stu-id="384a6-177">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="384a6-178">Con la representación Stereoscopic hay un desplazamiento entre las dos pantallas, que el cerebro puede conciliar como profundidad real.</span><span class="sxs-lookup"><span data-stu-id="384a6-178">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="384a6-179">En esta sección se describe la representación de Stereoscopic mediante la creación de instancias, mediante el uso de código de la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="384a6-179">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="384a6-180">Cada cámara tiene su propio destino de representación (búfer de reserva) y las matrices de vistas y proyección en el espacio holográfica.</span><span class="sxs-lookup"><span data-stu-id="384a6-180">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="384a6-181">La aplicación tendrá que crear cualquier otro recurso basado en la cámara, como el búfer de profundidad, por cada cámara.</span><span class="sxs-lookup"><span data-stu-id="384a6-181">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="384a6-182">En la plantilla de aplicación de Windows Holographic, se proporciona una clase auxiliar para agrupar estos recursos en DX:: CameraResources.</span><span class="sxs-lookup"><span data-stu-id="384a6-182">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="384a6-183">Empiece por configurar las vistas de destino de representación:</span><span class="sxs-lookup"><span data-stu-id="384a6-183">Start by setting up the render target views:</span></span>

<span data-ttu-id="384a6-184">Desde **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="384a6-184">From **AppMain::Render**:</span></span>

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

<span data-ttu-id="384a6-185">**Usar la predicción para obtener las matrices de vista y proyección de la cámara**</span><span class="sxs-lookup"><span data-stu-id="384a6-185">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="384a6-186">Las matrices de vista y proyección de cada cámara holográfica cambiarán con cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-186">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="384a6-187">Actualice los datos en el búfer de constantes de cada cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="384a6-187">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="384a6-188">Hágalo después de actualizar la predicción y antes de realizar cualquier llamada a Draw para esa cámara.</span><span class="sxs-lookup"><span data-stu-id="384a6-188">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="384a6-189">Desde **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="384a6-189">From **AppMain::Render**:</span></span>

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

<span data-ttu-id="384a6-190">Aquí se muestra cómo se adquieren las matrices de la pose de la cámara.</span><span class="sxs-lookup"><span data-stu-id="384a6-190">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="384a6-191">Durante este proceso, también se obtiene la ventanilla actual de la cámara.</span><span class="sxs-lookup"><span data-stu-id="384a6-191">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="384a6-192">Observe cómo se proporciona un sistema de coordenadas: este es el mismo sistema de coordenadas que se usa para comprender la mirada y es el mismo que se usa para colocar el cubo giratorio.</span><span class="sxs-lookup"><span data-stu-id="384a6-192">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="384a6-193">Desde **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="384a6-193">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

<span data-ttu-id="384a6-194">La ventanilla debe establecerse en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-194">The viewport should be set each frame.</span></span> <span data-ttu-id="384a6-195">Normalmente, el sombreador de vértices (al menos) necesitará tener acceso a los datos de vista o proyección.</span><span class="sxs-lookup"><span data-stu-id="384a6-195">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="384a6-196">Desde **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="384a6-196">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

<span data-ttu-id="384a6-197">**Se representa en el búfer de reserva de la cámara y se confirma el búfer de profundidad**:</span><span class="sxs-lookup"><span data-stu-id="384a6-197">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="384a6-198">Es conveniente comprobar que **TryGetViewTransform** se ha ejecutado correctamente antes de intentar usar los datos de vista o proyección, porque si el sistema de coordenadas no es localizable (por ejemplo, se interrumpió el seguimiento), la aplicación no se puede representar con él para ese marco.</span><span class="sxs-lookup"><span data-stu-id="384a6-198">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="384a6-199">La plantilla solo llama a **Render** en el cubo giratorio Si la clase **CameraResources** indica una actualización correcta.</span><span class="sxs-lookup"><span data-stu-id="384a6-199">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="384a6-200">Para mantener los hologramas donde un desarrollador o un usuario los pone en el mundo, Windows Mixed Reality incluye características para la [estabilización](hologram-stability.md)de la imagen.</span><span class="sxs-lookup"><span data-stu-id="384a6-200">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="384a6-201">La estabilización de imágenes ayuda a ocultar la latencia inherente en una canalización de representación para garantizar las mejores experiencias holográficas para los usuarios. se puede especificar un punto de enfoque para mejorar la estabilización de la imagen aún más, o se puede proporcionar un búfer de profundidad para calcular la estabilización de la imagen optimizada en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="384a6-201">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="384a6-202">Para obtener los mejores resultados, la aplicación debe proporcionar un búfer de profundidad mediante la API de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> .</span><span class="sxs-lookup"><span data-stu-id="384a6-202">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="384a6-203">Windows Mixed Reality puede usar la información de geometría del búfer de profundidad para optimizar la estabilización de la imagen en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="384a6-203">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="384a6-204">La plantilla de aplicación de Windows Holographic confirma el búfer de profundidad de la aplicación de forma predeterminada, lo que ayuda a optimizar la estabilidad del holograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-204">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="384a6-205">Desde **AppMain:: Render**:</span><span class="sxs-lookup"><span data-stu-id="384a6-205">From **AppMain::Render**:</span></span>

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
><span data-ttu-id="384a6-206">Windows procesará la textura de profundidad en la GPU, por lo que debe ser posible usar el búfer de profundidad como un recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="384a6-206">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="384a6-207">El ID3D11Texture2D que cree debe tener un formato sin tipo y debe enlazarse como una vista de recursos del sombreador.</span><span class="sxs-lookup"><span data-stu-id="384a6-207">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="384a6-208">Este es un ejemplo de cómo crear una textura de profundidad que se puede confirmar para la estabilización de la imagen.</span><span class="sxs-lookup"><span data-stu-id="384a6-208">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="384a6-209">Código para la **creación de recursos de búfer de profundidad para CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="384a6-209">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

<span data-ttu-id="384a6-210">**Dibujo de contenido holográfica**</span><span class="sxs-lookup"><span data-stu-id="384a6-210">**Draw holographic content**</span></span>

<span data-ttu-id="384a6-211">La plantilla de aplicación de Windows Holographic representa el contenido en estéreo mediante el uso de la técnica recomendada de dibujar geometría con instancias en un Texture2DArray de tamaño 2.</span><span class="sxs-lookup"><span data-stu-id="384a6-211">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="384a6-212">Echemos un vistazo a la parte de la creación de instancias de este y cómo funciona en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="384a6-212">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="384a6-213">Desde **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="384a6-213">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

<span data-ttu-id="384a6-214">Cada instancia tiene acceso a una matriz de vista/proyección diferente del búfer de constantes.</span><span class="sxs-lookup"><span data-stu-id="384a6-214">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="384a6-215">Esta es la estructura de búfer de constantes, que es simplemente una matriz de 2 matrices.</span><span class="sxs-lookup"><span data-stu-id="384a6-215">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="384a6-216">En **VertexShaderShared. HLSL**, incluido **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="384a6-216">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="384a6-217">El índice de la matriz de destino de representación se debe establecer para cada píxel.</span><span class="sxs-lookup"><span data-stu-id="384a6-217">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="384a6-218">En el siguiente fragmento de código, Output. viewId se asigna a la semántica **SV_RenderTargetArrayIndex** .</span><span class="sxs-lookup"><span data-stu-id="384a6-218">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="384a6-219">Tenga en cuenta que esto requiere compatibilidad con una característica opcional de Direct3D 11,3, que permite establecer la semántica de índice de la matriz de destino de representación desde cualquier fase del sombreador.</span><span class="sxs-lookup"><span data-stu-id="384a6-219">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="384a6-220">Desde **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="384a6-220">From **VPRTVertexShader.hlsl**:</span></span>

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

<span data-ttu-id="384a6-221">En **VertexShaderShared. HLSL**, incluido **VPRTVertexShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="384a6-221">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

<span data-ttu-id="384a6-222">Si desea usar las técnicas de dibujo con instancias existentes con este método de dibujo en una matriz de destino de representación estéreo, lo único que tiene que hacer es dibujar el doble del número de instancias que tiene normalmente.</span><span class="sxs-lookup"><span data-stu-id="384a6-222">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="384a6-223">En el sombreador, divida **Input. instId** por 2 para obtener el identificador de instancia original, que se puede indizar en (por ejemplo,) un búfer de datos por objeto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="384a6-223">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="384a6-224">Nota importante sobre la representación de contenido estéreo en HoloLens</span><span class="sxs-lookup"><span data-stu-id="384a6-224">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="384a6-225">Windows Mixed Reality admite la capacidad de establecer el índice de matriz de destino de representación desde cualquier fase del sombreador; Normalmente, se trata de una tarea que solo podría realizarse en la fase del sombreador de geometría debido a la manera en que se define la semántica para Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="384a6-225">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="384a6-226">Aquí se muestra un ejemplo completo de cómo configurar una canalización de representación con solo las etapas del sombreador de vértices y píxeles establecidos.</span><span class="sxs-lookup"><span data-stu-id="384a6-226">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="384a6-227">El código del sombreador es como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="384a6-227">The shader code is as described above.</span></span>

<span data-ttu-id="384a6-228">Desde **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="384a6-228">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="384a6-229">Nota importante sobre la representación en dispositivos que no sean HoloLens</span><span class="sxs-lookup"><span data-stu-id="384a6-229">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="384a6-230">La configuración del índice de matriz de destino de representación en el sombreador de vértices requiere que el controlador de gráficos admita una característica de Direct3D 11,3 opcional, que es compatible con HoloLens.</span><span class="sxs-lookup"><span data-stu-id="384a6-230">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="384a6-231">Es posible que la aplicación pueda implementar de forma segura solo esa técnica para la representación y que se cumplan todos los requisitos para ejecutarse en Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="384a6-231">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="384a6-232">También puede ser el caso de que quiera usar el emulador de HoloLens, que puede ser una herramienta de desarrollo eficaz para su aplicación holográfica, y que admiten dispositivos con auriculares de gran rendimiento con Windows Mixed Reality que están conectados a equipos con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="384a6-232">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="384a6-233">La compatibilidad con la ruta de representación que no es de HoloLens y, por lo tanto, para todo Windows Mixed Reality, también está integrada en la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="384a6-233">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="384a6-234">En el código de plantilla, encontrará código para permitir que la aplicación holográfica se ejecute en la GPU del equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="384a6-234">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="384a6-235">Este es el modo en que la clase **DeviceResources** comprueba esta compatibilidad de características opcional.</span><span class="sxs-lookup"><span data-stu-id="384a6-235">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="384a6-236">De **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="384a6-236">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="384a6-237">Para admitir la representación sin esta característica opcional, la aplicación debe usar un sombreador de geometría para establecer el índice de la matriz de destino de representación.</span><span class="sxs-lookup"><span data-stu-id="384a6-237">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="384a6-238">Este fragmento de código se agregaría *después* **de VSSetConstantBuffers**y *antes* de **PSSetShader** en el ejemplo de código mostrado en la sección anterior que explica cómo representar el estéreo en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="384a6-238">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="384a6-239">Desde **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="384a6-239">From **SpinningCubeRenderer::Render**:</span></span>

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

<span data-ttu-id="384a6-240">**Nota HLSL**: en este caso, también debe cargar un sombreador de vértices ligeramente modificado que pase el índice de la matriz de destino de representación al sombreador de geometría mediante una semántica de sombreador siempre permitida, como TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="384a6-240">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="384a6-241">El sombreador de geometría no tiene que hacer ningún trabajo; el sombreador de geometría de la plantilla pasa todos los datos, con la excepción del índice de la matriz de destino de representación, que se usa para establecer la semántica SV_RenderTargetArrayIndex.</span><span class="sxs-lookup"><span data-stu-id="384a6-241">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="384a6-242">Código de plantilla de aplicación para **GeometryShader. HLSL**:</span><span class="sxs-lookup"><span data-stu-id="384a6-242">App template code for **GeometryShader.hlsl**:</span></span>

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a><span data-ttu-id="384a6-243">Presente</span><span class="sxs-lookup"><span data-stu-id="384a6-243">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="384a6-244">Habilitación del marco holográfica para presentar la cadena de intercambio</span><span class="sxs-lookup"><span data-stu-id="384a6-244">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="384a6-245">Con Windows Mixed Reality, el sistema controla la cadena de intercambio.</span><span class="sxs-lookup"><span data-stu-id="384a6-245">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="384a6-246">Después, el sistema administra la presentación de fotogramas a cada cámara holográfica para garantizar una experiencia de usuario de alta calidad.</span><span class="sxs-lookup"><span data-stu-id="384a6-246">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="384a6-247">También proporciona una actualización de la ventanilla cada fotograma, para cada cámara, para optimizar aspectos del sistema, como la estabilización de imágenes o la captura de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="384a6-247">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="384a6-248">Por lo tanto, una aplicación holográfica con DirectX no llama a **presente** en una cadena de intercambio de DXGI.</span><span class="sxs-lookup"><span data-stu-id="384a6-248">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="384a6-249">En su lugar, use la clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> para mostrar todos los intercambio de un fotograma una vez que haya terminado de dibujarlo.</span><span class="sxs-lookup"><span data-stu-id="384a6-249">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="384a6-250">De **DeviceResources::P reenviado**:</span><span class="sxs-lookup"><span data-stu-id="384a6-250">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="384a6-251">De forma predeterminada, esta API espera a que el fotograma finalice antes de que se devuelva.</span><span class="sxs-lookup"><span data-stu-id="384a6-251">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="384a6-252">Las aplicaciones holográficas deben esperar a que finalice el fotograma anterior antes de empezar a trabajar en un nuevo fotograma, ya que esto reduce la latencia y permite obtener mejores resultados de las predicciones de fotogramas holográficas.</span><span class="sxs-lookup"><span data-stu-id="384a6-252">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="384a6-253">No es una regla rígida y, si tiene fotogramas que tardan más de una actualización de pantalla en representarse, puede deshabilitar esta espera Si pasa el parámetro HolographicFramePresentWaitBehavior a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="384a6-253">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="384a6-254">En este caso, podría usar un subproceso de representación asincrónico para mantener una carga continua en la GPU.</span><span class="sxs-lookup"><span data-stu-id="384a6-254">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="384a6-255">Tenga en cuenta que la frecuencia de actualización del dispositivo HoloLens es de 60 Hz, donde un fotograma tiene una duración aproximada de 16 ms.</span><span class="sxs-lookup"><span data-stu-id="384a6-255">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="384a6-256">Los auriculares envolventes pueden oscilar entre 60Hz y 90Hz; al actualizar la pantalla a 90 Hz, cada fotograma tendrá una duración aproximada de 11 ms.</span><span class="sxs-lookup"><span data-stu-id="384a6-256">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="384a6-257">Controle los escenarios de DeviceLost en cooperación con HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="384a6-257">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="384a6-258">Las aplicaciones de DirectX 11 normalmente querrán comprobar el valor HRESULT devuelto por la función **present** de la cadena de intercambio de DXGI para averiguar si se produjo un error **DeviceLost** .</span><span class="sxs-lookup"><span data-stu-id="384a6-258">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="384a6-259">La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> se encarga de ello.</span><span class="sxs-lookup"><span data-stu-id="384a6-259">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="384a6-260">Inspeccione el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> que devuelve para averiguar si necesita liberar y volver a crear el dispositivo Direct3D y los recursos basados en dispositivos.</span><span class="sxs-lookup"><span data-stu-id="384a6-260">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

<span data-ttu-id="384a6-261">Tenga en cuenta que si se perdió el dispositivo Direct3D y lo volvió a crear, debe indicar a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> que empiece a usar el nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="384a6-261">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="384a6-262">La cadena de intercambio se volverá a crear para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="384a6-262">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="384a6-263">De **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="384a6-263">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="384a6-264">Una vez que se presenta el fotograma, puede volver al bucle del programa principal y permitir que continúe con el siguiente fotograma.</span><span class="sxs-lookup"><span data-stu-id="384a6-264">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="384a6-265">Equipos de gráficos híbridos y aplicaciones de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="384a6-265">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="384a6-266">**Los** equipos con Windows 10 Creators Update se pueden configurar con GPU discretas e integradas.</span><span class="sxs-lookup"><span data-stu-id="384a6-266">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="384a6-267">Con estos tipos de equipos, Windows elegirá el adaptador al que está conectado el casco.</span><span class="sxs-lookup"><span data-stu-id="384a6-267">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="384a6-268">Las aplicaciones deben asegurarse de que el dispositivo DirectX que crea usa el mismo adaptador.</span><span class="sxs-lookup"><span data-stu-id="384a6-268">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="384a6-269">La mayoría del código de ejemplo de Direct3D general muestra la creación de un dispositivo DirectX mediante el adaptador de hardware predeterminado, que en un sistema híbrido puede no ser el mismo que el usado para el casco.</span><span class="sxs-lookup"><span data-stu-id="384a6-269">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="384a6-270">Para solucionar cualquier problema que esto pueda causar, use el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId ().</span><span class="sxs-lookup"><span data-stu-id="384a6-270">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="384a6-271">Este adapterId se puede usar para seleccionar el DXGIAdapter adecuado mediante IDXGIFactory4. EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="384a6-271">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="384a6-272">De **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="384a6-272">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

<span data-ttu-id="384a6-273">Código para **Actualizar DeviceResources:: CreateDeviceResources para usar IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="384a6-273">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

<span data-ttu-id="384a6-274">**Gráficos y Media Foundation híbridos**</span><span class="sxs-lookup"><span data-stu-id="384a6-274">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="384a6-275">El uso de Media Foundation en sistemas híbridos puede causar problemas en los que el vídeo no se represente o que la textura de vídeo esté dañada.</span><span class="sxs-lookup"><span data-stu-id="384a6-275">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="384a6-276">Esto puede ocurrir porque Media Foundation tiene como valor predeterminado un comportamiento del sistema, como se mencionó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="384a6-276">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="384a6-277">En algunos escenarios, se requiere la creación de un ID3D11Device independiente para admitir el subprocesamiento múltiple y se establecen las marcas de creación correctas.</span><span class="sxs-lookup"><span data-stu-id="384a6-277">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="384a6-278">Al inicializar ID3D11Device, se debe definir D3D11_CREATE_DEVICE_VIDEO_SUPPORT marca como parte de la D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="384a6-278">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="384a6-279">Una vez creado el dispositivo y el contexto, llame a <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar el multithreading.</span><span class="sxs-lookup"><span data-stu-id="384a6-279">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="384a6-280">Para asociar el dispositivo a <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use la función <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .</span><span class="sxs-lookup"><span data-stu-id="384a6-280">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="384a6-281">Código para **asociar un ID3D11Device con IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="384a6-281">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a><span data-ttu-id="384a6-282">Vea también</span><span class="sxs-lookup"><span data-stu-id="384a6-282">See also</span></span>
* [<span data-ttu-id="384a6-283">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="384a6-283">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="384a6-284">Uso del emulador HoloLens</span><span class="sxs-lookup"><span data-stu-id="384a6-284">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
