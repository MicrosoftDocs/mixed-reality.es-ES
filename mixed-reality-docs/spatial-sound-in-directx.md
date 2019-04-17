---
title: Sonido espacial en DirectX
description: Agregar sonido espacial a las aplicaciones de Windows Mixed Reality basadas en DirectX utilizando las bibliotecas de audio XAudio2 y xAPO.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixto en realidad, sonido espacial, aplicaciones, nivel bajo, XAudio2 xAPO, biblioteca de audio, tutorial, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605792"
---
# <a name="spatial-sound-in-directx"></a>Sonido espacial en DirectX

Agregar sonido espacial a las aplicaciones de Windows Mixed Reality basadas en DirectX utilizando el [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) y [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) bibliotecas de audio.

Este tema usa código de ejemplo desde el HolographicHRTFAudioSample.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="overview-of-head-relative-spatial-sound"></a>Información general del sonido espacial relativa de Head

Sonido espacial se implementa como un **el objeto de procesamiento de audio (APO)** que usa un **head relacionados con la función de transferencia (HRTF)** filtrar *spatialize* una secuencia de audio normal.

Incluir estos archivos de encabezado en pch.h para tener acceso a la API de audio:
* XAudio2.h
* xapo.h
* hrtfapoapi.h

Para configurar el sonido espacial:
1. Llame a [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) para inicializar una nueva APO para audio HRTF.
2. Asignar el [parámetros HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) y [entorno HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) para definir las características de la APO espacial de sonido acústicas.
3. Configurar el motor de XAudio2 para su procesamiento HRTF.
4. Crear un [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) objeto y llamar a [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>La implementación de la aplicación de DirectX HRTF y sonido espacial

Puede lograr una variedad de efectos al configurar el APO HRTF con entornos y parámetros diferentes. Use el siguiente código para explorar las posibilidades. Descargue el ejemplo de código de plataforma Universal de Windows desde aquí: [Ejemplo espacial de sonido](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Tipos auxiliares están disponibles en estos archivos:
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carga los archivos de audio con Media Foundation y [IMFSourceReader interfaz](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa el **SetupXAudio2** esa función para inicializar XAudio2 para su procesamiento HRTF.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Agregar sonido espacial para un origen de multidireccionales

Algunos hologramas en el entorno del usuario emiten sonido por igual en todas las direcciones. El código siguiente muestra cómo inicializar un APO para emitir un sonido multidireccionales. En este ejemplo, aplicamos este concepto en el cubo girando de la plantilla de aplicación de Windows Holographic. Para obtener el código completo, vea [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**Motor de la ventana espacial sonido solo admite 48 samplerate k para la reproducción. La mayoría de los programas de middleware, como Unity, convertirán automáticamente los archivos de sonido en el formato deseado, pero si empieza a trabajar en niveles inferiores en el sistema de audio o realizar su propia, esto es muy importante recordar evitar bloqueos o un comportamiento no deseado, como Error del sistema HRTF.**

En primer lugar, debemos inicializar la APO. En nuestra aplicación de ejemplo holográfica, elegimos hacerlo una vez que tenemos la **HolographicSpace**.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

La implementación de Initialize, desde *OmnidirectionalSound.cpp*:

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

Después de configura el APO HRTF, llame a [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) en la voz de origen para reproducir el audio. En nuestra aplicación de ejemplo, elegimos colocarlo en un bucle para que pueda continuar para oír el sonido que provienen del cubo.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Desde *OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Ahora, cada vez que se actualiza el marco, necesitamos actualizar la posición del holograma en relación con el propio dispositivo. Esto es porque la HRTF posiciones siempre se expresan con respecto a la cabeza del usuario, incluida la posición principal y la orientación.

Para hacer esto en un HolographicSpace, necesitamos construir una matriz de transformación de nuestro sistema de coordenadas SpatialStationaryFrameOfReference a un sistema de coordenadas que se fija en el propio dispositivo.

From *HolographicHrtfAudioSampleMain::Update()*:

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

La posición de la HRTF se aplica directamente a la APO sonido por la clase de aplicación auxiliar OmnidirectionalSound.

Desde *OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

Ya está. Siga leyendo para obtener más información sobre lo que puede hacer con audio HRTF y Windows Holographic.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Inicializar espacial sonido para un origen direccional

Algunos hologramas en el entorno del usuario emiten sonido principalmente en una dirección. Este patrón de sonido se denomina *hipercardiode* porque parece un corazón de dibujos animados. El código siguiente muestra cómo inicializar un APO para emitir direccional sonido. Para obtener el código completo, vea [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

Después de configura el APO HRTF, llame a [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) en la voz de origen para reproducir el audio.

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a>Implementar decadencia personalizado

Puede invalidar la velocidad a la que un sonido espacial decaiga con la distancia o a qué distancia corta por completo. Para implementar un comportamiento personalizado decadencia en un sonido espacial, rellenar un [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) y asígnelo a la **distanceDecay** campo un [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) antes de pasarlo a la [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) función.

Agregue el código siguiente a la **inicializar** mostrado anteriormente para especificar el comportamiento personalizado de decadencia de método. Para obtener el código completo, vea [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
