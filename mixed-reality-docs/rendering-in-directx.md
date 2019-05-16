---
title: Representación de DirectX
description: Explica la representación holographic para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, representación, gráficos 3D, HolographicFrame, representar el bucle, el bucle de actualización, el tutorial, código de ejemplo
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629035"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="f6604-104">Representación de DirectX</span><span class="sxs-lookup"><span data-stu-id="f6604-104">Rendering in DirectX</span></span>

<span data-ttu-id="f6604-105">Windows Mixed Reality se basa en DirectX para producir enriquecido, experiencias de gráficos 3D para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="f6604-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="f6604-106">La abstracción de representación se encuentra justo encima de DirectX y permite un motivo de la aplicación sobre la posición y orientación de uno o varios observadores de una escena holográfica, como previstos por el sistema.</span><span class="sxs-lookup"><span data-stu-id="f6604-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="f6604-107">El desarrollador, a continuación, puede buscar sus hologramas en relación con cada cámara, lo que la aplicación permite representar estos hologramas en varios sistemas de coordenadas espaciales cuando el usuario se mueve en torno a.</span><span class="sxs-lookup"><span data-stu-id="f6604-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="f6604-108">Actualización para el marco actual</span><span class="sxs-lookup"><span data-stu-id="f6604-108">Update for the current frame</span></span>

<span data-ttu-id="f6604-109">Para actualizar el estado de la aplicación para hologramas, una vez por fotograma de la aplicación hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f6604-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="f6604-110">Obtener un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> desde el sistema de administración de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="f6604-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="f6604-111">Actualice la escena con la predicción de dónde estará la vista de la cámara cuando se completa la representación actual.</span><span class="sxs-lookup"><span data-stu-id="f6604-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="f6604-112">Tenga en cuenta que puede haber más de una cámara de la escena holográfica.</span><span class="sxs-lookup"><span data-stu-id="f6604-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="f6604-113">Para representar a las vistas de cámara holográfica, una vez por fotograma de la aplicación hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f6604-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="f6604-114">Por cada cámara, representar la escena para el marco actual, con las matrices de vista y proyección de cámara desde el sistema.</span><span class="sxs-lookup"><span data-stu-id="f6604-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="f6604-115">Crear un nuevo marco holográfico y obtenga su predicción</span><span class="sxs-lookup"><span data-stu-id="f6604-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="f6604-116">El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tiene información que necesita la aplicación con el fin de actualizar y representar el fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="f6604-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="f6604-117">Cada nuevo fotograma inicia la aplicación mediante una llamada a la **CreateNextFrame** método.</span><span class="sxs-lookup"><span data-stu-id="f6604-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="f6604-118">Cuando se llama a este método, se realizan predicciones con los datos de sensor más recientes disponibles y, a continuación, encapsulados en **CurrentPrediction** objeto.</span><span class="sxs-lookup"><span data-stu-id="f6604-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="f6604-119">Debe usarse un nuevo objeto de marco para cada fotograma representado como solo es válido para un momento dado.</span><span class="sxs-lookup"><span data-stu-id="f6604-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="f6604-120">El **CurrentPrediction** propiedad contiene información como la posición de la cámara.</span><span class="sxs-lookup"><span data-stu-id="f6604-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="f6604-121">Se extrapoló la información en el momento exacto en el tiempo cuando el marco se espera que sea visible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="f6604-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="f6604-122">El código siguiente es un extracto del **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f6604-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="f6604-123">Procesar las actualizaciones de cámara</span><span class="sxs-lookup"><span data-stu-id="f6604-123">Process camera updates</span></span>

<span data-ttu-id="f6604-124">Los búferes de reserva pueden cambiar de fotograma a fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="f6604-125">Necesidades de su aplicación para validar la parte posterior de búferes por cada cámara y liberarán y volver a crear vistas de recursos y búferes de profundidad según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="f6604-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="f6604-126">Tenga en cuenta que el conjunto de plantea en la predicción es la lista autoritativa de cámaras que se usan en el marco actual.</span><span class="sxs-lookup"><span data-stu-id="f6604-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="f6604-127">Por lo general, use esta lista para recorrer en iteración en el conjunto de cámaras.</span><span class="sxs-lookup"><span data-stu-id="f6604-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="f6604-128">Desde **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f6604-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="f6604-129">Desde **DeviceResources::EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="f6604-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="f6604-130">Obtener el sistema de coordenadas que se usará como base para la representación</span><span class="sxs-lookup"><span data-stu-id="f6604-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="f6604-131">Windows Mixed Reality, la aplicación podrá crear diversos [sistemas de coordenadas](coordinate-systems-in-directx.md) según sea necesario, por ejemplo, el marco de referencia adjunta y el marco de referencia inmóvil, que realizar un seguimiento de las ubicaciones del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="f6604-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="f6604-132">La aplicación, a continuación, puede usar estos sistemas de coordenadas para razonar sobre dónde representar hologramas cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="f6604-133">Al solicitar las coordenadas de una API, siempre se pasará en el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro de la que desea que esas coordenadas para expresarse.</span><span class="sxs-lookup"><span data-stu-id="f6604-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="f6604-134">Desde **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f6604-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="f6604-135">Estos sistemas de coordenadas, a continuación, puede utilizarse para generar las matrices de vista estéreo al representar el contenido de la escena.</span><span class="sxs-lookup"><span data-stu-id="f6604-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="f6604-136">Desde **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f6604-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="f6604-137">Mirada de proceso y el gesto de entrada</span><span class="sxs-lookup"><span data-stu-id="f6604-137">Process gaze and gesture input</span></span>

<span data-ttu-id="f6604-138">[Observación](gaze-in-directx.md) y [mano](hands-and-motion-controllers-in-directx.md) no están basados en tiempo de entrada y, por tanto, no es necesario actualizar en el **StepTimer** función.</span><span class="sxs-lookup"><span data-stu-id="f6604-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="f6604-139">Sin embargo, esta entrada es algo que la aplicación debe consultar cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="f6604-140">Actualizaciones basadas en tiempo de proceso</span><span class="sxs-lookup"><span data-stu-id="f6604-140">Process time-based updates</span></span>

<span data-ttu-id="f6604-141">Cualquier aplicación de representación en tiempo real necesitará alguna manera para procesar las actualizaciones de duración definida; se proporciona una manera de hacerlo en la plantilla de aplicación de Windows Holographic a través de un **StepTimer** implementación.</span><span class="sxs-lookup"><span data-stu-id="f6604-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="f6604-142">Esto es similar a la StepTimer proporcionado en la plantilla de aplicación para UWP de DirectX 11, por lo que si ya ha observado en esa plantilla debería estar en tierra familiar.</span><span class="sxs-lookup"><span data-stu-id="f6604-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="f6604-143">Esta clase de aplicación auxiliar de ejemplo StepTimer es capaz de proporcionar actualizaciones de incremento de tiempo fijas, así como las actualizaciones de incremento de tiempo variable y el modo predeterminado es pasos de tiempo variable.</span><span class="sxs-lookup"><span data-stu-id="f6604-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="f6604-144">En el caso de representación holográfica, hemos elegido específicamente no poner demasiado en la función de temporizador.</span><span class="sxs-lookup"><span data-stu-id="f6604-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="f6604-145">Esto es porque se puede configurar para que sea un incremento de tiempo fijo, en cuyo caso se podría llamarse más de una vez por fotograma: o no en absoluto, para algunos marcos: y las actualizaciones de los datos holográfica deben ocurrir una vez por fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="f6604-146">Desde **AppMain::Update**:</span><span class="sxs-lookup"><span data-stu-id="f6604-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="f6604-147">Posición y giro hologramas en su sistema de coordenadas</span><span class="sxs-lookup"><span data-stu-id="f6604-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="f6604-148">Si está trabajando en un único sistema de coordenadas, que hace la plantilla con el **SpatialStationaryReferenceFrame**, este proceso no es diferente de lo que está en caso contrario, se usan para en gráficos 3D.</span><span class="sxs-lookup"><span data-stu-id="f6604-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="f6604-149">En este caso, se gira el cubo y establecer la matriz de modelo con respecto a la posición en el sistema de coordenadas estacionaria.</span><span class="sxs-lookup"><span data-stu-id="f6604-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="f6604-150">Desde **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="f6604-150">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="f6604-151">**Tenga en cuenta sobre escenarios avanzados:** El cubo girando es un ejemplo muy sencillo de cómo colocar un holograma dentro de un marco de referencia único.</span><span class="sxs-lookup"><span data-stu-id="f6604-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="f6604-152">También es posible [usar varios SpatialCoordinateSystems](coordinate-systems-in-directx.md) en el mismo marco representado, al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="f6604-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="f6604-153">Actualizar los datos del búfer de constantes</span><span class="sxs-lookup"><span data-stu-id="f6604-153">Update constant buffer data</span></span>

<span data-ttu-id="f6604-154">Transformaciones de modelo para el contenido se actualizan como de costumbre.</span><span class="sxs-lookup"><span data-stu-id="f6604-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="f6604-155">En este momento, habrán calculado transformaciones válidas para el sistema de coordenadas que se podrá representar en.</span><span class="sxs-lookup"><span data-stu-id="f6604-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="f6604-156">Desde **SpinningCubeRenderer::Update**:</span><span class="sxs-lookup"><span data-stu-id="f6604-156">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="f6604-157">¿Qué sucede con las transformaciones de proyección y de vista?</span><span class="sxs-lookup"><span data-stu-id="f6604-157">What about view and projection transforms?</span></span> <span data-ttu-id="f6604-158">Para obtener mejores resultados, quiere esperar hasta que se está casi listos para nuestras llamadas a draw antes de abordar estos.</span><span class="sxs-lookup"><span data-stu-id="f6604-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="f6604-159">Representar el fotograma actual</span><span class="sxs-lookup"><span data-stu-id="f6604-159">Render the current frame</span></span>

<span data-ttu-id="f6604-160">Representación con Windows Mixed Reality no es muy diferente de la representación en una pantalla 2D mono, pero hay algunas diferencias que debe tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="f6604-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="f6604-161">Predicciones de marco holográfica son importantes.</span><span class="sxs-lookup"><span data-stu-id="f6604-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="f6604-162">Cuanto más se acerque la predicción es cuando se presenta el fotograma, mejor será sus hologramas.</span><span class="sxs-lookup"><span data-stu-id="f6604-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="f6604-163">Windows Mixed Reality controla las vistas de la cámara.</span><span class="sxs-lookup"><span data-stu-id="f6604-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="f6604-164">Necesario representar a cada una de ellas, porque el marco holográfico va a presentar ellos automáticamente más tarde.</span><span class="sxs-lookup"><span data-stu-id="f6604-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="f6604-165">Se recomienda llevar a cabo mediante el dibujo con instancias a una matriz de destino de representación representación estéreo.</span><span class="sxs-lookup"><span data-stu-id="f6604-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="f6604-166">La plantilla de aplicación holográfica usa el enfoque recomendado de dibujo con instancias a una matriz de destino de representación, que usa un destino de presentación en un **Texture2DArray**.</span><span class="sxs-lookup"><span data-stu-id="f6604-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="f6604-167">Si desea procesar sin usar la creación de instancias estéreo, deberá crear dos RenderTargetViews no matriciales (uno para cada ojo) cada referencia de los dos intervalos de la **Texture2DArray** proporcionado a la aplicación desde el sistema.</span><span class="sxs-lookup"><span data-stu-id="f6604-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="f6604-168">No se recomienda ya que normalmente es significativamente más lenta que la creación de instancias.</span><span class="sxs-lookup"><span data-stu-id="f6604-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="f6604-169">Obtener una predicción HolographicFrame actualizada</span><span class="sxs-lookup"><span data-stu-id="f6604-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="f6604-170">Actualizando la predicción de marco mejora la eficacia de estabilización de la imagen y permite una posición más precisas de hologramas debido al tiempo más corto entre la predicción y cuando el marco está visible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="f6604-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="f6604-171">Lo ideal es que actualice su predicción marco antes de la representación.</span><span class="sxs-lookup"><span data-stu-id="f6604-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="f6604-172">Representar a cada cámara</span><span class="sxs-lookup"><span data-stu-id="f6604-172">Render to each camera</span></span>

<span data-ttu-id="f6604-173">Bucle en el conjunto de cámara plantea en la predicción y representar a cada cámara en este conjunto.</span><span class="sxs-lookup"><span data-stu-id="f6604-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="f6604-174">**Configurar la fase de representación**</span><span class="sxs-lookup"><span data-stu-id="f6604-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="f6604-175">Windows Mixed Reality usa la representación estereoscópica para mejorar la ilusión de profundidad y representar estereoscópicamente, por lo que están activas la izquierda y la visualización adecuada.</span><span class="sxs-lookup"><span data-stu-id="f6604-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="f6604-176">Con la representación estereoscópica hay un desplazamiento entre las dos pantallas, que se puede conciliar el cerebro como profundidad real.</span><span class="sxs-lookup"><span data-stu-id="f6604-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="f6604-177">Esta sección abarca estereoscópica representación mediante la creación de instancias utilizando el código de la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="f6604-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="f6604-178">Cada cámara tiene su propia representación matrices de destino (búfer de reserva) y la vista y proyección, en el espacio holográfico.</span><span class="sxs-lookup"><span data-stu-id="f6604-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="f6604-179">La aplicación necesitará crear otros basado en la cámara recursos - por ejemplo, el búfer de profundidad - en una base por cada cámara.</span><span class="sxs-lookup"><span data-stu-id="f6604-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="f6604-180">En la plantilla de aplicación Windows Holographic, proporcionamos una clase auxiliar para agrupar estos recursos en DX::CameraResources.</span><span class="sxs-lookup"><span data-stu-id="f6604-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="f6604-181">Iniciar mediante la configuración de las vistas de destino de representación:</span><span class="sxs-lookup"><span data-stu-id="f6604-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="f6604-182">Desde **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="f6604-182">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="f6604-183">**Use la predicción para obtener la vista y matrices de proyección de la cámara**</span><span class="sxs-lookup"><span data-stu-id="f6604-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="f6604-184">Las matrices de proyección y de vista para cada cámara holográfica cambiará con cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="f6604-185">Actualizar los datos en el búfer de constantes para cada cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="f6604-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="f6604-186">Hacer esto después de actualizar la predicción, y antes de realizar llamadas de cualquier dibujo para que la cámara.</span><span class="sxs-lookup"><span data-stu-id="f6604-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="f6604-187">Desde **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="f6604-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="f6604-188">En este caso, se muestra cómo se adquieren las matrices de la postura de cámara.</span><span class="sxs-lookup"><span data-stu-id="f6604-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="f6604-189">Durante este proceso también obtenemos la ventanilla actual para la cámara.</span><span class="sxs-lookup"><span data-stu-id="f6604-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="f6604-190">Tenga en cuenta cómo se proporciona un sistema de coordenadas: Esto es el mismo sistema de coordenadas que se usa para comprender la mirada, y es lo mismo se utiliza para situar el cubo girando.</span><span class="sxs-lookup"><span data-stu-id="f6604-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="f6604-191">Desde **CameraResources::UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f6604-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="f6604-192">La ventanilla se debe establecer en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-192">The viewport should be set each frame.</span></span> <span data-ttu-id="f6604-193">(Como mínimo) el sombreador de vértices normalmente tendrá acceso a los datos de vista o proyección.</span><span class="sxs-lookup"><span data-stu-id="f6604-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="f6604-194">Desde **CameraResources::AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f6604-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="f6604-195">**Representar en el búfer de reserva de cámara y confirmar el búfer de profundidad**:</span><span class="sxs-lookup"><span data-stu-id="f6604-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="f6604-196">Es una buena idea comprobar que **TryGetViewTransform** se realizó correctamente antes de intentar usar los datos de vista y proyección, porque si el sistema de coordenadas no es localizable (por ejemplo, se ha interrumpido el seguimiento) no se puede representar la aplicación con él para que marco.</span><span class="sxs-lookup"><span data-stu-id="f6604-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="f6604-197">Solo se llama la plantilla **representar** en el cubo girando si el **CameraResources** clase indica una actualización correcta.</span><span class="sxs-lookup"><span data-stu-id="f6604-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="f6604-198">Para mantener hologramas donde un desarrollador o un usuario coloca en el mundo, Windows Mixed Reality incluye características para [estabilización de la imagen](hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="f6604-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="f6604-199">Estabilización de imagen le ayuda a ocultar la latencia inherente en una canalización de representación para garantizar la experiencia holográfica mejor para los usuarios; se puede especificar un punto de enfoque para mejorar aún más la estabilización de imagen o se puede proporcionar un búfer de profundidad calcular optimizado estabilización de la imagen en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="f6604-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="f6604-200">Para obtener mejores resultados, la aplicación debe proporcionar un búfer de profundidad mediante el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span><span class="sxs-lookup"><span data-stu-id="f6604-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="f6604-201">Windows Mixed Reality, a continuación, puede usar información de geometría desde el búfer de profundidad para optimizar la estabilización de la imagen en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="f6604-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="f6604-202">La plantilla de aplicación de Windows Holographic confirma el búfer de profundidad de la aplicación de forma predeterminada, ayudar a optimizar la estabilidad holograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="f6604-203">Desde **AppMain::Render**:</span><span class="sxs-lookup"><span data-stu-id="f6604-203">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="f6604-204">Windows procesará la textura de profundidad en la GPU, por lo que debe ser posible usar el búfer de profundidad como un recurso de sombreador.</span><span class="sxs-lookup"><span data-stu-id="f6604-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="f6604-205">El ID3D11Texture2D que cree debe tener un formato sin tipo y debe estar enlazado como una vista de recursos del sombreador.</span><span class="sxs-lookup"><span data-stu-id="f6604-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="f6604-206">Este es un ejemplo de cómo crear una textura de profundidad de la que se puede asignar para la estabilización de la imagen.</span><span class="sxs-lookup"><span data-stu-id="f6604-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="f6604-207">El código para **creación de recursos de búfer de profundidad para CommitDirect3D11DepthBuffer**:</span><span class="sxs-lookup"><span data-stu-id="f6604-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="f6604-208">**Dibujar contenido holográfica**</span><span class="sxs-lookup"><span data-stu-id="f6604-208">**Draw holographic content**</span></span>

<span data-ttu-id="f6604-209">La plantilla de aplicación de Windows Holographic representa contenido en estéreo mediante el uso de la técnica recomendada de geometría con instancias de dibujo a un Texture2DArray de tamaño 2.</span><span class="sxs-lookup"><span data-stu-id="f6604-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="f6604-210">Echemos un vistazo a la creación de instancias parte de esto y cómo funciona con Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f6604-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="f6604-211">Desde **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="f6604-211">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="f6604-212">Cada instancia tiene acceso a una matriz de vista y proyección diferentes desde el búfer de constantes.</span><span class="sxs-lookup"><span data-stu-id="f6604-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="f6604-213">Aquí es la estructura de búfer de constantes, que es simplemente una matriz de matrices de 2.</span><span class="sxs-lookup"><span data-stu-id="f6604-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="f6604-214">Desde **VertexShaderShared.hlsl**, que se incluye por **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f6604-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="f6604-215">El índice de la matriz de destino de representación debe establecerse para cada píxel.</span><span class="sxs-lookup"><span data-stu-id="f6604-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="f6604-216">En el siguiente fragmento de código, output.viewId se asigna a la **SV_RenderTargetArrayIndex** semántico.</span><span class="sxs-lookup"><span data-stu-id="f6604-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="f6604-217">Tenga en cuenta que esto requiere soporte técnico para una característica opcional de Direct3D 11.3, lo que permite que el índice de la matriz de destino de representación semántica debe establecerse en cualquier etapa del sombreador.</span><span class="sxs-lookup"><span data-stu-id="f6604-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="f6604-218">Desde **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f6604-218">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="f6604-219">Desde **VertexShaderShared.hlsl**, que se incluye por **VPRTVertexShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f6604-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="f6604-220">Si desea usar la instancia existente técnicas de dibujos con este método para dibujar en un equipo estéreo de representan la matriz de destino, lo único que debe hacer es dibujar dos veces el número de instancias que tiene normalmente.</span><span class="sxs-lookup"><span data-stu-id="f6604-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="f6604-221">En el sombreado, dividir **input.instId** por 2 para obtener el identificador de instancia original, que se pueden indizar (por ejemplo) un búfer de datos por objeto: `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="f6604-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="f6604-222">Nota importante sobre cómo representar contenido estéreo en HoloLens</span><span class="sxs-lookup"><span data-stu-id="f6604-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="f6604-223">Windows Mixed Reality admite la capacidad para establecer el índice de la matriz de destino de representación en cualquier etapa del sombreador; Normalmente, esta es una tarea que solo se podía activar en la etapa del sombreador de geometría debido a la manera en que se define la semántica de Direct3D 11.</span><span class="sxs-lookup"><span data-stu-id="f6604-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="f6604-224">En este caso, se muestra un ejemplo completo de cómo configurar una canalización de representación con solo lo vértices y píxeles sombreador fases conjunto.</span><span class="sxs-lookup"><span data-stu-id="f6604-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="f6604-225">El código del sombreador es como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f6604-225">The shader code is as described above.</span></span>

<span data-ttu-id="f6604-226">Desde **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="f6604-226">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="f6604-227">Nota importante acerca de la representación en los dispositivos que no sean HoloLens</span><span class="sxs-lookup"><span data-stu-id="f6604-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="f6604-228">Establecer el índice de la matriz de destino de representación en el sombreador de vértices, es necesario que el controlador de gráficos admite una característica opcional de Direct3D 11.3, que es compatible con HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f6604-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="f6604-229">La aplicación puede ser capaz de implementar sólo esa técnica para la representación de forma segura y se cumplirá todos los requisitos para que se ejecutan en el Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f6604-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="f6604-230">Puede ser el caso de que desea usar el emulador de HoloLens, que puede ser una herramienta de desarrollo eficaz para su aplicación holográfica - y admitir Windows Mixed Reality auriculares envolventes dispositivos que están conectados a equipos con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f6604-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="f6604-231">Compatibilidad con la ruta de acceso de la representación no HoloLens - y por lo tanto, para todas las de Windows Mixed Reality: también se integra en la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="f6604-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="f6604-232">En el código de plantilla, encontrará el código para habilitar la aplicación holográfica se ejecute en la GPU en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f6604-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="f6604-233">Este es el modo **DeviceResources** comprobaciones de compatibilidad con esta característica opcional de clases.</span><span class="sxs-lookup"><span data-stu-id="f6604-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="f6604-234">Desde **DeviceResources::CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="f6604-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="f6604-235">Para admitir la representación sin esta característica opcional, la aplicación debe usar a un sombreador de geometría para establecer el índice de la matriz de destino de representación.</span><span class="sxs-lookup"><span data-stu-id="f6604-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="f6604-236">Este fragmento de código se agregarían *después* **VSSetConstantBuffers**, y *antes* **PSSetShader** en el ejemplo de código se muestra en la anterior sección que explica cómo representar estéreo en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f6604-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="f6604-237">Desde **SpinningCubeRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="f6604-237">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="f6604-238">**NOTA DE HLSL**: En este caso, también se debe cargar a un sombreador de vértices ligeramente modificada que pasa el índice de la matriz de destino de representación para el sombreador de geometría utilizando a un sombreador siempre permite semántico, como TEXCOORD0.</span><span class="sxs-lookup"><span data-stu-id="f6604-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="f6604-239">No tiene que hacer nada; el sombreador de geometría el sombreador de geometría de la plantilla que se pasa a través de todos los datos, excepto el índice de matriz de destino de representación, que se usa para establecer el SV_RenderTargetArrayIndex semántico.</span><span class="sxs-lookup"><span data-stu-id="f6604-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="f6604-240">Código de plantilla de aplicación para **GeometryShader.hlsl**:</span><span class="sxs-lookup"><span data-stu-id="f6604-240">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="f6604-241">Presentar</span><span class="sxs-lookup"><span data-stu-id="f6604-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="f6604-242">Habilitar el marco holográfico presentar la cadena de intercambio</span><span class="sxs-lookup"><span data-stu-id="f6604-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="f6604-243">Con Windows Mixed Reality, el sistema controla la cadena de intercambio.</span><span class="sxs-lookup"><span data-stu-id="f6604-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="f6604-244">El sistema, a continuación, administra la presentación fotogramas a cada cámara holográfica para garantizar una experiencia de usuario de alta calidad.</span><span class="sxs-lookup"><span data-stu-id="f6604-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="f6604-245">También proporciona una actualización de la ventanilla cada fotograma por cada cámara, para optimizar los aspectos del sistema, como la estabilización de imagen o capturar de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f6604-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="f6604-246">Por lo tanto, no llame una aplicación holográfica usando DirectX **presente** cadena de intercambio en un DXGI.</span><span class="sxs-lookup"><span data-stu-id="f6604-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="f6604-247">En su lugar, usa el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> clase presentar todas las cadenas de intercambio para un marco de una vez que haya terminado dibujarlo.</span><span class="sxs-lookup"><span data-stu-id="f6604-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="f6604-248">Desde **DeviceResources::Present**:</span><span class="sxs-lookup"><span data-stu-id="f6604-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="f6604-249">De forma predeterminada, esta API espera para que el marco finalizar antes de devolver.</span><span class="sxs-lookup"><span data-stu-id="f6604-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="f6604-250">Aplicaciones holográficas deben esperar el fotograma anterior finalice antes de empezar a trabajar en un nuevo marco, ya que esto reduce la latencia y permite obtener mejores resultados de las predicciones de marco holográfica.</span><span class="sxs-lookup"><span data-stu-id="f6604-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="f6604-251">Esto no es una regla de disco dura y, si tiene marcos que tarden más de actualización de una pantalla para representar pueden deshabilitar esta espera pasando el parámetro HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span><span class="sxs-lookup"><span data-stu-id="f6604-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="f6604-252">En este caso, es probable que usaría un subproceso de representación asincrónica con el fin de mantener una carga continua en la GPU.</span><span class="sxs-lookup"><span data-stu-id="f6604-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="f6604-253">Tenga en cuenta que la frecuencia de actualización del dispositivo HoloLens es de 60hz, donde un fotograma tiene una duración de 16 ms aproximadamente.</span><span class="sxs-lookup"><span data-stu-id="f6604-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="f6604-254">Dispositivos de auricular envolventes pueden oscilar entre 60hz y 90hz; al actualizar la presentación a 90 hz, cada fotograma tendrá una duración de 11 ms aproximadamente.</span><span class="sxs-lookup"><span data-stu-id="f6604-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="f6604-255">Controlar los escenarios de DeviceLost en cooperación con el HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="f6604-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="f6604-256">Las aplicaciones de DirectX 11 normalmente desea comprobar el HRESULT devuelto por la cadena de intercambio DXGI **presente** función para averiguar si se ha producido un **DeviceLost** error.</span><span class="sxs-lookup"><span data-stu-id="f6604-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="f6604-257">El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> clase encarga de ello.</span><span class="sxs-lookup"><span data-stu-id="f6604-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="f6604-258">Inspeccionar el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> devuelve para averiguar si necesita liberar y volver a crear el dispositivo Direct3D y los recursos basados en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f6604-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="f6604-259">Tenga en cuenta que si se ha perdido el dispositivo Direct3D y vuelva a crearla, tendrá que indicar a la <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para empezar a usar el nuevo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f6604-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="f6604-260">Se volverá a la cadena de intercambio para este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f6604-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="f6604-261">Desde **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="f6604-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="f6604-262">Una vez que se presenta el fotograma, puede volver al bucle principal del programa y permitir que pueda seguir el siguiente fotograma.</span><span class="sxs-lookup"><span data-stu-id="f6604-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="f6604-263">Los equipos de gráficos híbridos y aplicaciones de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f6604-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="f6604-264">Windows 10 Creators Update PC pueden configurarse con **ambos** GPU discretas e integradas.</span><span class="sxs-lookup"><span data-stu-id="f6604-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="f6604-265">Con estos tipos de equipos, Windows elegirá el adaptador a que está conectado el auricular.</span><span class="sxs-lookup"><span data-stu-id="f6604-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="f6604-266">Las aplicaciones deben asegurarse de crea el dispositivo de DirectX utiliza el mismo adaptador.</span><span class="sxs-lookup"><span data-stu-id="f6604-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="f6604-267">Código de ejemplo Direct3D más general muestra cómo crear un dispositivo de DirectX con el adaptador de hardware de forma predeterminada, que, en un sistema híbrido, no puede ser el mismo que el utilizado para los auriculares.</span><span class="sxs-lookup"><span data-stu-id="f6604-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="f6604-268">Para solucionar cualquier problema que esto puede provocar, utilice el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> desde <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId().</span><span class="sxs-lookup"><span data-stu-id="f6604-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="f6604-269">Este adapterId, a continuación, puede utilizarse para seleccionar el derecho DXGIAdapter mediante IDXGIFactory4.EnumAdapterByLuid.</span><span class="sxs-lookup"><span data-stu-id="f6604-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="f6604-270">Desde **DeviceResources::InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="f6604-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="f6604-271">Escribir código para **actualizar DeviceResources::CreateDeviceResources para usar IDXGIAdapter**</span><span class="sxs-lookup"><span data-stu-id="f6604-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="f6604-272">**Gráficos híbridos y Media Foundation**</span><span class="sxs-lookup"><span data-stu-id="f6604-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="f6604-273">Uso de Media Foundation en sistemas híbridos puede producir problemas cuando no se representará el vídeo o textura de vídeo está dañado.</span><span class="sxs-lookup"><span data-stu-id="f6604-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="f6604-274">Esto puede ocurrir porque Media Foundation esté de forma predeterminada un comportamiento del sistema, como se mencionó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f6604-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="f6604-275">En algunos escenarios, es necesario para la compatibilidad con subprocesamiento múltiple y la creación correcta se establecen marcas de crear un ID3D11Device independiente.</span><span class="sxs-lookup"><span data-stu-id="f6604-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="f6604-276">Al inicializar el ID3D11Device, marca D3D11_CREATE_DEVICE_VIDEO_SUPPORT debe definirse como parte de la D3D11_CREATE_DEVICE_FLAG.</span><span class="sxs-lookup"><span data-stu-id="f6604-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="f6604-277">Una vez creado el dispositivo y el contexto, llame a <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar el multithreading.</span><span class="sxs-lookup"><span data-stu-id="f6604-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="f6604-278">Para asociar el dispositivo con el <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, utilice el <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> función.</span><span class="sxs-lookup"><span data-stu-id="f6604-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="f6604-279">Escribir código para **asociar un ID3D11Device IMFDXGIDeviceManager**:</span><span class="sxs-lookup"><span data-stu-id="f6604-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f6604-280">Vea también</span><span class="sxs-lookup"><span data-stu-id="f6604-280">See also</span></span>
* [<span data-ttu-id="f6604-281">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="f6604-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="f6604-282">Uso del emulador HoloLens</span><span class="sxs-lookup"><span data-stu-id="f6604-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
