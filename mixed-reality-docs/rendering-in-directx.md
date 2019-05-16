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
# <a name="rendering-in-directx"></a>Representación de DirectX

Windows Mixed Reality se basa en DirectX para producir enriquecido, experiencias de gráficos 3D para los usuarios. La abstracción de representación se encuentra justo encima de DirectX y permite un motivo de la aplicación sobre la posición y orientación de uno o varios observadores de una escena holográfica, como previstos por el sistema. El desarrollador, a continuación, puede buscar sus hologramas en relación con cada cámara, lo que la aplicación permite representar estos hologramas en varios sistemas de coordenadas espaciales cuando el usuario se mueve en torno a.

## <a name="update-for-the-current-frame"></a>Actualización para el marco actual

Para actualizar el estado de la aplicación para hologramas, una vez por fotograma de la aplicación hará lo siguiente:
* Obtener un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> desde el sistema de administración de la pantalla.
* Actualice la escena con la predicción de dónde estará la vista de la cámara cuando se completa la representación actual. Tenga en cuenta que puede haber más de una cámara de la escena holográfica.

Para representar a las vistas de cámara holográfica, una vez por fotograma de la aplicación hará lo siguiente:
* Por cada cámara, representar la escena para el marco actual, con las matrices de vista y proyección de cámara desde el sistema.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>Crear un nuevo marco holográfico y obtenga su predicción

El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> tiene información que necesita la aplicación con el fin de actualizar y representar el fotograma actual. Cada nuevo fotograma inicia la aplicación mediante una llamada a la **CreateNextFrame** método. Cuando se llama a este método, se realizan predicciones con los datos de sensor más recientes disponibles y, a continuación, encapsulados en **CurrentPrediction** objeto.

Debe usarse un nuevo objeto de marco para cada fotograma representado como solo es válido para un momento dado. El **CurrentPrediction** propiedad contiene información como la posición de la cámara. Se extrapoló la información en el momento exacto en el tiempo cuando el marco se espera que sea visible para el usuario.

El código siguiente es un extracto del **AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>Procesar las actualizaciones de cámara

Los búferes de reserva pueden cambiar de fotograma a fotograma. Necesidades de su aplicación para validar la parte posterior de búferes por cada cámara y liberarán y volver a crear vistas de recursos y búferes de profundidad según sea necesario. Tenga en cuenta que el conjunto de plantea en la predicción es la lista autoritativa de cámaras que se usan en el marco actual. Por lo general, use esta lista para recorrer en iteración en el conjunto de cámaras.

Desde **AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

Desde **DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>Obtener el sistema de coordenadas que se usará como base para la representación

Windows Mixed Reality, la aplicación podrá crear diversos [sistemas de coordenadas](coordinate-systems-in-directx.md) según sea necesario, por ejemplo, el marco de referencia adjunta y el marco de referencia inmóvil, que realizar un seguimiento de las ubicaciones del mundo físico. La aplicación, a continuación, puede usar estos sistemas de coordenadas para razonar sobre dónde representar hologramas cada fotograma. Al solicitar las coordenadas de una API, siempre se pasará en el <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> dentro de la que desea que esas coordenadas para expresarse.

Desde **AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

Estos sistemas de coordenadas, a continuación, puede utilizarse para generar las matrices de vista estéreo al representar el contenido de la escena.

Desde **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>Mirada de proceso y el gesto de entrada

[Observación](gaze-in-directx.md) y [mano](hands-and-motion-controllers-in-directx.md) no están basados en tiempo de entrada y, por tanto, no es necesario actualizar en el **StepTimer** función. Sin embargo, esta entrada es algo que la aplicación debe consultar cada fotograma.

### <a name="process-time-based-updates"></a>Actualizaciones basadas en tiempo de proceso

Cualquier aplicación de representación en tiempo real necesitará alguna manera para procesar las actualizaciones de duración definida; se proporciona una manera de hacerlo en la plantilla de aplicación de Windows Holographic a través de un **StepTimer** implementación. Esto es similar a la StepTimer proporcionado en la plantilla de aplicación para UWP de DirectX 11, por lo que si ya ha observado en esa plantilla debería estar en tierra familiar. Esta clase de aplicación auxiliar de ejemplo StepTimer es capaz de proporcionar actualizaciones de incremento de tiempo fijas, así como las actualizaciones de incremento de tiempo variable y el modo predeterminado es pasos de tiempo variable.

En el caso de representación holográfica, hemos elegido específicamente no poner demasiado en la función de temporizador. Esto es porque se puede configurar para que sea un incremento de tiempo fijo, en cuyo caso se podría llamarse más de una vez por fotograma: o no en absoluto, para algunos marcos: y las actualizaciones de los datos holográfica deben ocurrir una vez por fotograma.


Desde **AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>Posición y giro hologramas en su sistema de coordenadas

Si está trabajando en un único sistema de coordenadas, que hace la plantilla con el **SpatialStationaryReferenceFrame**, este proceso no es diferente de lo que está en caso contrario, se usan para en gráficos 3D. En este caso, se gira el cubo y establecer la matriz de modelo con respecto a la posición en el sistema de coordenadas estacionaria.

Desde **SpinningCubeRenderer::Update**:

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

**Tenga en cuenta sobre escenarios avanzados:** El cubo girando es un ejemplo muy sencillo de cómo colocar un holograma dentro de un marco de referencia único. También es posible [usar varios SpatialCoordinateSystems](coordinate-systems-in-directx.md) en el mismo marco representado, al mismo tiempo.

### <a name="update-constant-buffer-data"></a>Actualizar los datos del búfer de constantes

Transformaciones de modelo para el contenido se actualizan como de costumbre. En este momento, habrán calculado transformaciones válidas para el sistema de coordenadas que se podrá representar en.

Desde **SpinningCubeRenderer::Update**:

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

¿Qué sucede con las transformaciones de proyección y de vista? Para obtener mejores resultados, quiere esperar hasta que se está casi listos para nuestras llamadas a draw antes de abordar estos.

## <a name="render-the-current-frame"></a>Representar el fotograma actual

Representación con Windows Mixed Reality no es muy diferente de la representación en una pantalla 2D mono, pero hay algunas diferencias que debe tener en cuenta:
* Predicciones de marco holográfica son importantes. Cuanto más se acerque la predicción es cuando se presenta el fotograma, mejor será sus hologramas.
* Windows Mixed Reality controla las vistas de la cámara. Necesario representar a cada una de ellas, porque el marco holográfico va a presentar ellos automáticamente más tarde.
* Se recomienda llevar a cabo mediante el dibujo con instancias a una matriz de destino de representación representación estéreo. La plantilla de aplicación holográfica usa el enfoque recomendado de dibujo con instancias a una matriz de destino de representación, que usa un destino de presentación en un **Texture2DArray**.
* Si desea procesar sin usar la creación de instancias estéreo, deberá crear dos RenderTargetViews no matriciales (uno para cada ojo) cada referencia de los dos intervalos de la **Texture2DArray** proporcionado a la aplicación desde el sistema. No se recomienda ya que normalmente es significativamente más lenta que la creación de instancias.

### <a name="get-an-updated-holographicframe-prediction"></a>Obtener una predicción HolographicFrame actualizada

Actualizando la predicción de marco mejora la eficacia de estabilización de la imagen y permite una posición más precisas de hologramas debido al tiempo más corto entre la predicción y cuando el marco está visible para el usuario. Lo ideal es que actualice su predicción marco antes de la representación.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>Representar a cada cámara

Bucle en el conjunto de cámara plantea en la predicción y representar a cada cámara en este conjunto.

**Configurar la fase de representación**

Windows Mixed Reality usa la representación estereoscópica para mejorar la ilusión de profundidad y representar estereoscópicamente, por lo que están activas la izquierda y la visualización adecuada. Con la representación estereoscópica hay un desplazamiento entre las dos pantallas, que se puede conciliar el cerebro como profundidad real. Esta sección abarca estereoscópica representación mediante la creación de instancias utilizando el código de la plantilla de aplicación de Windows Holographic.

Cada cámara tiene su propia representación matrices de destino (búfer de reserva) y la vista y proyección, en el espacio holográfico. La aplicación necesitará crear otros basado en la cámara recursos - por ejemplo, el búfer de profundidad - en una base por cada cámara. En la plantilla de aplicación Windows Holographic, proporcionamos una clase auxiliar para agrupar estos recursos en DX::CameraResources. Iniciar mediante la configuración de las vistas de destino de representación:

Desde **AppMain::Render**:

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

**Use la predicción para obtener la vista y matrices de proyección de la cámara**

Las matrices de proyección y de vista para cada cámara holográfica cambiará con cada fotograma. Actualizar los datos en el búfer de constantes para cada cámara holográfica. Hacer esto después de actualizar la predicción, y antes de realizar llamadas de cualquier dibujo para que la cámara.

Desde **AppMain::Render**:

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

En este caso, se muestra cómo se adquieren las matrices de la postura de cámara. Durante este proceso también obtenemos la ventanilla actual para la cámara. Tenga en cuenta cómo se proporciona un sistema de coordenadas: Esto es el mismo sistema de coordenadas que se usa para comprender la mirada, y es lo mismo se utiliza para situar el cubo girando.


Desde **CameraResources::UpdateViewProjectionBuffer**:

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

La ventanilla se debe establecer en cada fotograma. (Como mínimo) el sombreador de vértices normalmente tendrá acceso a los datos de vista o proyección.


Desde **CameraResources::AttachViewProjectionBuffer**:

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

**Representar en el búfer de reserva de cámara y confirmar el búfer de profundidad**:

Es una buena idea comprobar que **TryGetViewTransform** se realizó correctamente antes de intentar usar los datos de vista y proyección, porque si el sistema de coordenadas no es localizable (por ejemplo, se ha interrumpido el seguimiento) no se puede representar la aplicación con él para que marco. Solo se llama la plantilla **representar** en el cubo girando si el **CameraResources** clase indica una actualización correcta.

Para mantener hologramas donde un desarrollador o un usuario coloca en el mundo, Windows Mixed Reality incluye características para [estabilización de la imagen](hologram-stability.md). Estabilización de imagen le ayuda a ocultar la latencia inherente en una canalización de representación para garantizar la experiencia holográfica mejor para los usuarios; se puede especificar un punto de enfoque para mejorar aún más la estabilización de imagen o se puede proporcionar un búfer de profundidad calcular optimizado estabilización de la imagen en tiempo real.

Para obtener mejores resultados, la aplicación debe proporcionar un búfer de profundidad mediante el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API. Windows Mixed Reality, a continuación, puede usar información de geometría desde el búfer de profundidad para optimizar la estabilización de la imagen en tiempo real. La plantilla de aplicación de Windows Holographic confirma el búfer de profundidad de la aplicación de forma predeterminada, ayudar a optimizar la estabilidad holograma.

Desde **AppMain::Render**:

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
>Windows procesará la textura de profundidad en la GPU, por lo que debe ser posible usar el búfer de profundidad como un recurso de sombreador. El ID3D11Texture2D que cree debe tener un formato sin tipo y debe estar enlazado como una vista de recursos del sombreador. Este es un ejemplo de cómo crear una textura de profundidad de la que se puede asignar para la estabilización de la imagen.

El código para **creación de recursos de búfer de profundidad para CommitDirect3D11DepthBuffer**:

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

**Dibujar contenido holográfica**

La plantilla de aplicación de Windows Holographic representa contenido en estéreo mediante el uso de la técnica recomendada de geometría con instancias de dibujo a un Texture2DArray de tamaño 2. Echemos un vistazo a la creación de instancias parte de esto y cómo funciona con Windows Mixed Reality.

Desde **SpinningCubeRenderer::Render**:

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

Cada instancia tiene acceso a una matriz de vista y proyección diferentes desde el búfer de constantes. Aquí es la estructura de búfer de constantes, que es simplemente una matriz de matrices de 2.

Desde **VertexShaderShared.hlsl**, que se incluye por **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

El índice de la matriz de destino de representación debe establecerse para cada píxel. En el siguiente fragmento de código, output.viewId se asigna a la **SV_RenderTargetArrayIndex** semántico. Tenga en cuenta que esto requiere soporte técnico para una característica opcional de Direct3D 11.3, lo que permite que el índice de la matriz de destino de representación semántica debe establecerse en cualquier etapa del sombreador.

Desde **VPRTVertexShader.hlsl**:

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

Desde **VertexShaderShared.hlsl**, que se incluye por **VPRTVertexShader.hlsl**:

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

Si desea usar la instancia existente técnicas de dibujos con este método para dibujar en un equipo estéreo de representan la matriz de destino, lo único que debe hacer es dibujar dos veces el número de instancias que tiene normalmente. En el sombreado, dividir **input.instId** por 2 para obtener el identificador de instancia original, que se pueden indizar (por ejemplo) un búfer de datos por objeto: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>Nota importante sobre cómo representar contenido estéreo en HoloLens

Windows Mixed Reality admite la capacidad para establecer el índice de la matriz de destino de representación en cualquier etapa del sombreador; Normalmente, esta es una tarea que solo se podía activar en la etapa del sombreador de geometría debido a la manera en que se define la semántica de Direct3D 11. En este caso, se muestra un ejemplo completo de cómo configurar una canalización de representación con solo lo vértices y píxeles sombreador fases conjunto. El código del sombreador es como se describió anteriormente.

Desde **SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>Nota importante acerca de la representación en los dispositivos que no sean HoloLens

Establecer el índice de la matriz de destino de representación en el sombreador de vértices, es necesario que el controlador de gráficos admite una característica opcional de Direct3D 11.3, que es compatible con HoloLens. La aplicación puede ser capaz de implementar sólo esa técnica para la representación de forma segura y se cumplirá todos los requisitos para que se ejecutan en el Microsoft HoloLens.

Puede ser el caso de que desea usar el emulador de HoloLens, que puede ser una herramienta de desarrollo eficaz para su aplicación holográfica - y admitir Windows Mixed Reality auriculares envolventes dispositivos que están conectados a equipos con Windows 10. Compatibilidad con la ruta de acceso de la representación no HoloLens - y por lo tanto, para todas las de Windows Mixed Reality: también se integra en la plantilla de aplicación de Windows Holographic. En el código de plantilla, encontrará el código para habilitar la aplicación holográfica se ejecute en la GPU en el equipo de desarrollo. Este es el modo **DeviceResources** comprobaciones de compatibilidad con esta característica opcional de clases.

Desde **DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

Para admitir la representación sin esta característica opcional, la aplicación debe usar a un sombreador de geometría para establecer el índice de la matriz de destino de representación. Este fragmento de código se agregarían *después* **VSSetConstantBuffers**, y *antes* **PSSetShader** en el ejemplo de código se muestra en la anterior sección que explica cómo representar estéreo en HoloLens.

Desde **SpinningCubeRenderer::Render**:

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

**NOTA DE HLSL**: En este caso, también se debe cargar a un sombreador de vértices ligeramente modificada que pasa el índice de la matriz de destino de representación para el sombreador de geometría utilizando a un sombreador siempre permite semántico, como TEXCOORD0. No tiene que hacer nada; el sombreador de geometría el sombreador de geometría de la plantilla que se pasa a través de todos los datos, excepto el índice de matriz de destino de representación, que se usa para establecer el SV_RenderTargetArrayIndex semántico.

Código de plantilla de aplicación para **GeometryShader.hlsl**:

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

## <a name="present"></a>Presentar

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Habilitar el marco holográfico presentar la cadena de intercambio

Con Windows Mixed Reality, el sistema controla la cadena de intercambio. El sistema, a continuación, administra la presentación fotogramas a cada cámara holográfica para garantizar una experiencia de usuario de alta calidad. También proporciona una actualización de la ventanilla cada fotograma por cada cámara, para optimizar los aspectos del sistema, como la estabilización de imagen o capturar de realidad mixta. Por lo tanto, no llame una aplicación holográfica usando DirectX **presente** cadena de intercambio en un DXGI. En su lugar, usa el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> clase presentar todas las cadenas de intercambio para un marco de una vez que haya terminado dibujarlo.

Desde **DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

De forma predeterminada, esta API espera para que el marco finalizar antes de devolver. Aplicaciones holográficas deben esperar el fotograma anterior finalice antes de empezar a trabajar en un nuevo marco, ya que esto reduce la latencia y permite obtener mejores resultados de las predicciones de marco holográfica. Esto no es una regla de disco dura y, si tiene marcos que tarden más de actualización de una pantalla para representar pueden deshabilitar esta espera pasando el parámetro HolographicFramePresentWaitBehavior <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>. En este caso, es probable que usaría un subproceso de representación asincrónica con el fin de mantener una carga continua en la GPU. Tenga en cuenta que la frecuencia de actualización del dispositivo HoloLens es de 60hz, donde un fotograma tiene una duración de 16 ms aproximadamente. Dispositivos de auricular envolventes pueden oscilar entre 60hz y 90hz; al actualizar la presentación a 90 hz, cada fotograma tendrá una duración de 11 ms aproximadamente.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>Controlar los escenarios de DeviceLost en cooperación con el HolographicFrame

Las aplicaciones de DirectX 11 normalmente desea comprobar el HRESULT devuelto por la cadena de intercambio DXGI **presente** función para averiguar si se ha producido un **DeviceLost** error. El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> clase encarga de ello. Inspeccionar el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> devuelve para averiguar si necesita liberar y volver a crear el dispositivo Direct3D y los recursos basados en el dispositivo.

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

Tenga en cuenta que si se ha perdido el dispositivo Direct3D y vuelva a crearla, tendrá que indicar a la <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> para empezar a usar el nuevo dispositivo. Se volverá a la cadena de intercambio para este dispositivo.

Desde **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

Una vez que se presenta el fotograma, puede volver al bucle principal del programa y permitir que pueda seguir el siguiente fotograma.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>Los equipos de gráficos híbridos y aplicaciones de realidad mixta

Windows 10 Creators Update PC pueden configurarse con **ambos** GPU discretas e integradas. Con estos tipos de equipos, Windows elegirá el adaptador a que está conectado el auricular. Las aplicaciones deben asegurarse de crea el dispositivo de DirectX utiliza el mismo adaptador.

Código de ejemplo Direct3D más general muestra cómo crear un dispositivo de DirectX con el adaptador de hardware de forma predeterminada, que, en un sistema híbrido, no puede ser el mismo que el utilizado para los auriculares.

Para solucionar cualquier problema que esto puede provocar, utilice el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> desde <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>. PrimaryAdapterId() o <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId(). Este adapterId, a continuación, puede utilizarse para seleccionar el derecho DXGIAdapter mediante IDXGIFactory4.EnumAdapterByLuid.

Desde **DeviceResources::InitializeUsingHolographicSpace**:

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

Escribir código para **actualizar DeviceResources::CreateDeviceResources para usar IDXGIAdapter**

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

**Gráficos híbridos y Media Foundation**

Uso de Media Foundation en sistemas híbridos puede producir problemas cuando no se representará el vídeo o textura de vídeo está dañado. Esto puede ocurrir porque Media Foundation esté de forma predeterminada un comportamiento del sistema, como se mencionó anteriormente. En algunos escenarios, es necesario para la compatibilidad con subprocesamiento múltiple y la creación correcta se establecen marcas de crear un ID3D11Device independiente.

Al inicializar el ID3D11Device, marca D3D11_CREATE_DEVICE_VIDEO_SUPPORT debe definirse como parte de la D3D11_CREATE_DEVICE_FLAG. Una vez creado el dispositivo y el contexto, llame a <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> para habilitar el multithreading. Para asociar el dispositivo con el <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, utilice el <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> función.

Escribir código para **asociar un ID3D11Device IMFDXGIDeviceManager**:

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
