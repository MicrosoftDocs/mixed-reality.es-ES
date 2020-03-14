---
title: Representación en DirectX
description: Explica la representación holográfica para Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, representación, gráficos 3D, HolographicFrame, bucle de representación, bucle de actualización, tutorial, código de ejemplo, Direct3D
ms.openlocfilehash: 6b2e2dca9115d7093e94019d5ed91201f6ee3424
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375982"
---
# <a name="rendering-in-directx"></a>Representación en DirectX

Windows Mixed Reality se basa en DirectX para generar experiencias gráficas 3D enriquecidas para los usuarios. La abstracción de representación se encuentra justo encima de DirectX y permite que una aplicación tenga en la posición y la orientación de uno o más observadores de una escena holográfica, tal y como lo predice el sistema. A continuación, el desarrollador puede localizar sus hologramas en relación con cada cámara, lo que permite que la aplicación represente estos hologramas en varios sistemas de coordenadas espaciales a medida que el usuario se desplaza.

Nota: en este tutorial se describe la representación holográfica en Direct3D 11. También se proporciona una plantilla de aplicación de Windows mixed reality de Direct3D 12 con la extensión de plantillas de aplicación de realidad mixta.

## <a name="update-for-the-current-frame"></a>Actualizar para el marco actual

Para actualizar el estado de la aplicación para los hologramas, una vez por fotograma, la aplicación:
* Obtiene un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> del sistema de administración de pantalla.
* Actualice la escena con la predicción actual de en la que se mostrará la vista de cámara cuando se complete el procesamiento. Tenga en cuenta que puede haber más de una cámara para la escena holográfica.

Para representar vistas de cámara holográfica, una vez por fotograma, la aplicación:
* Para cada cámara, represente la escena del fotograma actual, usando la vista de cámara y las matrices de proyección del sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Crear un nuevo marco holográfica y obtener su predicción

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tiene información que la aplicación necesita para actualizar y representar el fotograma actual. La aplicación comienza cada nuevo fotograma llamando al método **CreateNextFrame** . Cuando se llama a este método, las predicciones se realizan utilizando los datos del sensor más recientes disponibles y se encapsulan en el objeto **CurrentPrediction** .

Se debe usar un nuevo objeto de marco para cada fotograma representado, ya que solo es válido para un momento dado. La propiedad **CurrentPrediction** contiene información como la posición de la cámara. La información se extrapola al momento exacto en que se espera que el marco sea visible para el usuario.

El código siguiente se ha extraído de **AppMain:: Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Procesar actualizaciones de la cámara

Los búferes de reserva pueden cambiar de fotograma a fotograma. La aplicación debe validar el búfer de reserva de cada cámara y liberar y volver a crear las vistas de recursos y los búferes de profundidad según sea necesario. Observe que el conjunto de supuestos de la predicción es la lista autoritativa de cámaras que se usan en el marco actual. Normalmente, esta lista se usa para iterar en el conjunto de cámaras.

Desde **AppMain:: Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

De **DeviceResources:: EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Obtención del sistema de coordenadas que se va a usar como base para la representación

Windows Mixed Reality permite que la aplicación cree varios [sistemas de coordenadas](coordinate-systems-in-directx.md) según sea necesario, como el marco de referencia adjunto y el marco de referencia estacionario, que realizan un seguimiento de las ubicaciones del mundo físico. A continuación, la aplicación puede usar estos sistemas de coordenadas para pensar en dónde representar los hologramas en cada fotograma. Cuando se solicitan coordenadas de una API, siempre se pasa el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> en el que se desea expresar esas coordenadas.

Desde **AppMain:: Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Estos sistemas de coordenadas se pueden usar para generar matrices de vista estéreo al representar el contenido de la escena.

Desde **CameraResources:: UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Entrada de movimiento y miración de proceso

La entrada de [mirada](gaze-in-directx.md) y la [mano](hands-and-motion-controllers-in-directx.md) no se basan en el tiempo y, por tanto, no tienen que actualizarse en la función **StepTimer** . Sin embargo, esta entrada es algo que la aplicación debe buscar en cada fotograma.

### <a name="process-time-based-updates"></a>Procesar actualizaciones basadas en el tiempo

Cualquier aplicación de representación en tiempo real necesitará alguna manera de procesar las actualizaciones basadas en el tiempo. Proporcionamos una forma de hacerlo en la plantilla de aplicación de Windows Holographic a través de una implementación de **StepTimer** . Esto es similar a la StepTimer que se proporciona en la plantilla de aplicación para UWP de DirectX 11, por lo que si ya ha examinado la plantilla, debe estar familiarizado con los conocimientos. Esta clase auxiliar de ejemplo StepTimer es capaz de proporcionar actualizaciones fijas de pasos temporales, así como actualizaciones de pasos temporales variables, y el modo predeterminado es pasos de tiempo variable.

En el caso de la representación holográfica, hemos elegido específicamente no incluir demasiado en la función de temporizador. Esto se debe a que puede configurarlo para que sea un paso de tiempo fijo, en cuyo caso se podría llamar a más de una vez por fotograma (o no, en absoluto) en algunos fotogramas, y las actualizaciones de datos holográficas deben realizarse una vez por fotograma.


Desde **AppMain:: Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Colocar y girar los hologramas en el sistema de coordenadas

Si está trabajando en un único sistema de coordenadas, como hace la plantilla con el **SpatialStationaryReferenceFrame**, este proceso no es diferente de lo que se usa en los gráficos 3D. Aquí se gira el cubo y se establece la matriz del modelo en relación con la posición en el sistema de coordenadas estacionales.

Desde **SpinningCubeRenderer:: Update**:

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

**Tenga en cuenta los escenarios avanzados:** El cubo giratorio es un ejemplo muy sencillo de cómo colocar un holograma dentro de un solo fotograma de referencia. También es posible [usar varios SpatialCoordinateSystems](coordinate-systems-in-directx.md) en el mismo fotograma representado al mismo tiempo.

### <a name="update-constant-buffer-data"></a>Actualizar datos de búfer de constantes

Las transformaciones del modelo para el contenido se actualizan de la forma habitual. De momento, habrá calculado las transformaciones válidas para el sistema de coordenadas en el que se va a representar.

Desde **SpinningCubeRenderer:: Update**:

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

¿Qué ocurre con las transformaciones de visualización y proyección? Para obtener los mejores resultados, queremos esperar hasta que podamos estar casi preparados para las llamadas a Draw antes de obtenerlas.

## <a name="render-the-current-frame"></a>Representar el marco actual

La representación en Windows Mixed Reality no es muy diferente de la representación en una pantalla mono 2D, pero hay algunas diferencias que debe tener en cuenta:
* Las predicciones de tramas holográficas son importantes. Cuanto más se acerque la predicción a la presentación del fotograma, mejor se verán los hologramas.
* Windows Mixed Reality controla las vistas de la cámara. Debe representar cada una de ellas, ya que el marco holográfica las presentará más adelante.
* Se recomienda que la representación de estéreo se realice mediante el dibujo con instancias en una matriz de destino de representación. La plantilla de aplicación holográfica usa el enfoque recomendado del dibujo con instancias en una matriz de destino de representación, que usa una vista de destino de representación en un **Texture2DArray**.
* Si desea representar sin usar la creación de instancias de estéreo, tendrá que crear dos RenderTargetViews que no sean de matriz (uno para cada ojo) que cada una de ellas haga referencia a uno de los dos segmentos del **Texture2DArray** proporcionado a la aplicación desde el sistema. Esto no se recomienda, ya que normalmente es significativamente más lento que el uso de la creación de instancias.

### <a name="get-an-updated-holographicframe-prediction"></a>Obtener una predicción HolographicFrame actualizada

La actualización de la predicción de fotogramas mejora la eficacia de la estabilización de imágenes y permite un posicionamiento más preciso de los hologramas debido al tiempo más corto entre la predicción y el momento en el que el usuario puede ver el marco. Idealmente, actualice la predicción de fotogramas justo antes de la representación.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Representar en cada cámara

Bucle en el conjunto de repeticiones de la cámara en la predicción y representar en cada cámara de este conjunto.

**Configurar el paso de representación**

Windows Mixed Reality usa la representación Stereoscopic para mejorar la ilusión de profundidad y representar stereoscopically, por lo que tanto la pantalla izquierda como la derecha están activas. Con la representación Stereoscopic hay un desplazamiento entre las dos pantallas, que el cerebro puede conciliar como profundidad real. En esta sección se describe la representación de Stereoscopic mediante la creación de instancias, mediante el uso de código de la plantilla de aplicación de Windows Holographic.

Cada cámara tiene su propio destino de representación (búfer de reserva) y las matrices de vistas y proyección en el espacio holográfica. La aplicación tendrá que crear cualquier otro recurso basado en la cámara, como el búfer de profundidad, por cada cámara. En la plantilla de aplicación de Windows Holographic, se proporciona una clase auxiliar para agrupar estos recursos en DX:: CameraResources. Empiece por configurar las vistas de destino de representación:

Desde **AppMain:: Render**:

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

**Usar la predicción para obtener las matrices de vista y proyección de la cámara**

Las matrices de vista y proyección de cada cámara holográfica cambiarán con cada fotograma. Actualice los datos en el búfer de constantes de cada cámara holográfica. Hágalo después de actualizar la predicción y antes de realizar cualquier llamada a Draw para esa cámara.

Desde **AppMain:: Render**:

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

Aquí se muestra cómo se adquieren las matrices de la pose de la cámara. Durante este proceso, también se obtiene la ventanilla actual de la cámara. Observe cómo se proporciona un sistema de coordenadas: este es el mismo sistema de coordenadas que se usa para comprender la mirada y es el mismo que se usa para colocar el cubo giratorio.


Desde **CameraResources:: UpdateViewProjectionBuffer**:

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

La ventanilla debe establecerse en cada fotograma. Normalmente, el sombreador de vértices (al menos) necesitará tener acceso a los datos de vista o proyección.


Desde **CameraResources:: AttachViewProjectionBuffer**:

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

**Se representa en el búfer de reserva de la cámara y se confirma el búfer de profundidad**:

Es conveniente comprobar que **TryGetViewTransform** se ha ejecutado correctamente antes de intentar usar los datos de vista o proyección, porque si el sistema de coordenadas no es localizable (por ejemplo, se interrumpió el seguimiento), la aplicación no se puede representar con él para ese marco. La plantilla solo llama a **Render** en el cubo giratorio Si la clase **CameraResources** indica una actualización correcta.

Para mantener los hologramas donde un desarrollador o un usuario los pone en el mundo, Windows Mixed Reality incluye características para la [estabilización](hologram-stability.md)de la imagen. La estabilización de imágenes ayuda a ocultar la latencia inherente en una canalización de representación para garantizar las mejores experiencias holográficas para los usuarios. se puede especificar un punto de enfoque para mejorar la estabilización de la imagen aún más, o se puede proporcionar un búfer de profundidad para calcular la estabilización de la imagen optimizada en tiempo real.

Para obtener los mejores resultados, la aplicación debe proporcionar un búfer de profundidad mediante la API de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> . Windows Mixed Reality puede usar la información de geometría del búfer de profundidad para optimizar la estabilización de la imagen en tiempo real. La plantilla de aplicación de Windows Holographic confirma el búfer de profundidad de la aplicación de forma predeterminada, lo que ayuda a optimizar la estabilidad del holograma.

Desde **AppMain:: Render**:

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
>Windows procesará la textura de profundidad en la GPU, por lo que debe ser posible usar el búfer de profundidad como un recurso de sombreador. El ID3D11Texture2D que cree debe tener un formato sin tipo y debe enlazarse como una vista de recursos del sombreador. Este es un ejemplo de cómo crear una textura de profundidad que se puede confirmar para la estabilización de la imagen.

Código para la **creación de recursos de búfer de profundidad para CommitDirect3D11DepthBuffer**:

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

**Dibujo de contenido holográfica**

La plantilla de aplicación de Windows Holographic representa el contenido en estéreo mediante el uso de la técnica recomendada de dibujar geometría con instancias en un Texture2DArray de tamaño 2. Echemos un vistazo a la parte de la creación de instancias de este y cómo funciona en Windows Mixed Reality.

Desde **SpinningCubeRenderer:: Render**:

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

Cada instancia tiene acceso a una matriz de vista/proyección diferente del búfer de constantes. Esta es la estructura de búfer de constantes, que es simplemente una matriz de 2 matrices.

En **VertexShaderShared. HLSL**, incluido **VPRTVertexShader. HLSL**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

El índice de la matriz de destino de representación se debe establecer para cada píxel. En el siguiente fragmento de código, Output. viewId se asigna a la semántica **SV_RenderTargetArrayIndex** . Tenga en cuenta que esto requiere compatibilidad con una característica opcional de Direct3D 11,3, que permite establecer la semántica de índice de la matriz de destino de representación desde cualquier fase del sombreador.

Desde **VPRTVertexShader. HLSL**:

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

En **VertexShaderShared. HLSL**, incluido **VPRTVertexShader. HLSL**:

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

Si desea usar las técnicas de dibujo con instancias existentes con este método de dibujo en una matriz de destino de representación estéreo, lo único que tiene que hacer es dibujar el doble del número de instancias que tiene normalmente. En el sombreador, divida **Input. instId** por 2 para obtener el identificador de instancia original, que se puede indizar en (por ejemplo,) un búfer de datos por objeto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Nota importante sobre la representación de contenido estéreo en HoloLens

Windows Mixed Reality admite la capacidad de establecer el índice de matriz de destino de representación desde cualquier fase del sombreador; Normalmente, se trata de una tarea que solo podría realizarse en la fase del sombreador de geometría debido a la manera en que se define la semántica para Direct3D 11. Aquí se muestra un ejemplo completo de cómo configurar una canalización de representación con solo las etapas del sombreador de vértices y píxeles establecidos. El código del sombreador es como se describió anteriormente.

Desde **SpinningCubeRenderer:: Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Nota importante sobre la representación en dispositivos que no sean HoloLens

La configuración del índice de matriz de destino de representación en el sombreador de vértices requiere que el controlador de gráficos admita una característica de Direct3D 11,3 opcional, que es compatible con HoloLens. Es posible que la aplicación pueda implementar de forma segura solo esa técnica para la representación y que se cumplan todos los requisitos para ejecutarse en Microsoft HoloLens.

También puede ser el caso de que quiera usar el emulador de HoloLens, que puede ser una herramienta de desarrollo eficaz para su aplicación holográfica, y que admiten dispositivos con auriculares de gran rendimiento con Windows Mixed Reality que están conectados a equipos con Windows 10. La compatibilidad con la ruta de representación que no es de HoloLens y, por lo tanto, para todo Windows Mixed Reality, también está integrada en la plantilla de aplicación de Windows Holographic. En el código de plantilla, encontrará código para permitir que la aplicación holográfica se ejecute en la GPU del equipo de desarrollo. Este es el modo en que la clase **DeviceResources** comprueba esta compatibilidad de características opcional.

De **DeviceResources:: CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Para admitir la representación sin esta característica opcional, la aplicación debe usar un sombreador de geometría para establecer el índice de la matriz de destino de representación. Este fragmento de código se agregaría *después* **de VSSetConstantBuffers**y *antes* de **PSSetShader** en el ejemplo de código mostrado en la sección anterior que explica cómo representar el estéreo en HoloLens.

Desde **SpinningCubeRenderer:: Render**:

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

**Nota HLSL**: en este caso, también debe cargar un sombreador de vértices ligeramente modificado que pase el índice de la matriz de destino de representación al sombreador de geometría mediante una semántica de sombreador siempre permitida, como TEXCOORD0. El sombreador de geometría no tiene que hacer ningún trabajo; el sombreador de geometría de la plantilla pasa todos los datos, con la excepción del índice de la matriz de destino de representación, que se usa para establecer la semántica SV_RenderTargetArrayIndex.

Código de plantilla de aplicación para **GeometryShader. HLSL**:

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

## <a name="present"></a>Presente

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Habilitación del marco holográfica para presentar la cadena de intercambio

Con Windows Mixed Reality, el sistema controla la cadena de intercambio. Después, el sistema administra la presentación de fotogramas a cada cámara holográfica para garantizar una experiencia de usuario de alta calidad. También proporciona una actualización de la ventanilla cada fotograma, para cada cámara, para optimizar aspectos del sistema, como la estabilización de imágenes o la captura de realidad mixta. Por lo tanto, una aplicación holográfica con DirectX no llama a **presente** en una cadena de intercambio de DXGI. En su lugar, use la clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> para mostrar todos los intercambio de un fotograma una vez que haya terminado de dibujarlo.

De **DeviceResources::P reenviado**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

De forma predeterminada, esta API espera a que el fotograma finalice antes de que se devuelva. Las aplicaciones holográficas deben esperar a que finalice el fotograma anterior antes de empezar a trabajar en un nuevo fotograma, ya que esto reduce la latencia y permite obtener mejores resultados de las predicciones de fotogramas holográficas. No es una regla rígida y, si tiene fotogramas que tardan más de una actualización de pantalla en representarse, puede deshabilitar esta espera Si pasa el parámetro HolographicFramePresentWaitBehavior a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. En este caso, podría usar un subproceso de representación asincrónico para mantener una carga continua en la GPU. Tenga en cuenta que la frecuencia de actualización del dispositivo HoloLens es de 60 Hz, donde un fotograma tiene una duración aproximada de 16 ms. Los auriculares envolventes pueden oscilar entre 60Hz y 90Hz; al actualizar la pantalla a 90 Hz, cada fotograma tendrá una duración aproximada de 11 ms.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Controle los escenarios de DeviceLost en cooperación con HolographicFrame

Las aplicaciones de DirectX 11 normalmente querrán comprobar el valor HRESULT devuelto por la función **present** de la cadena de intercambio de DXGI para averiguar si se produjo un error **DeviceLost** . La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> se encarga de ello. Inspeccione el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> que devuelve para averiguar si necesita liberar y volver a crear el dispositivo Direct3D y los recursos basados en dispositivos.

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

Tenga en cuenta que si se perdió el dispositivo Direct3D y lo volvió a crear, debe indicar a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> que empiece a usar el nuevo dispositivo. La cadena de intercambio se volverá a crear para este dispositivo.

De **DeviceResources:: InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Una vez que se presenta el fotograma, puede volver al bucle del programa principal y permitir que continúe con el siguiente fotograma.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Equipos de gráficos híbridos y aplicaciones de realidad mixta

**Los** equipos con Windows 10 Creators Update se pueden configurar con GPU discretas e integradas. Con estos tipos de equipos, Windows elegirá el adaptador al que está conectado el casco. Las aplicaciones deben asegurarse de que el dispositivo DirectX que crea usa el mismo adaptador.

La mayoría del código de ejemplo de Direct3D general muestra la creación de un dispositivo DirectX mediante el adaptador de hardware predeterminado, que en un sistema híbrido puede no ser el mismo que el usado para el casco.

Para solucionar cualquier problema que esto pueda causar, use el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> de <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId () o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId (). Este adapterId se puede usar para seleccionar el DXGIAdapter adecuado mediante IDXGIFactory4. EnumAdapterByLuid.

De **DeviceResources:: InitializeUsingHolographicSpace**:

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

Código para **Actualizar DeviceResources:: CreateDeviceResources para usar IDXGIAdapter**

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

**Gráficos y Media Foundation híbridos**

El uso de Media Foundation en sistemas híbridos puede causar problemas en los que el vídeo no se represente o que la textura de vídeo esté dañada. Esto puede ocurrir porque Media Foundation tiene como valor predeterminado un comportamiento del sistema, como se mencionó anteriormente. En algunos escenarios, se requiere la creación de un ID3D11Device independiente para admitir el subprocesamiento múltiple y se establecen las marcas de creación correctas.

Al inicializar ID3D11Device, se debe definir D3D11_CREATE_DEVICE_VIDEO_SUPPORT marca como parte de la D3D11_CREATE_DEVICE_FLAG. Una vez creado el dispositivo y el contexto, llame a <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar el multithreading. Para asociar el dispositivo a <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use la función <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: ResetDevice</a> .

Código para **asociar un ID3D11Device con IMFDXGIDeviceManager**:

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

## <a name="see-also"></a>Vea también
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
