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
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="d4b25-104">Sonido espacial en DirectX</span><span class="sxs-lookup"><span data-stu-id="d4b25-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="d4b25-105">Agregar sonido espacial a las aplicaciones de Windows Mixed Reality basadas en DirectX utilizando el [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) y [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) bibliotecas de audio.</span><span class="sxs-lookup"><span data-stu-id="d4b25-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="d4b25-106">Este tema usa código de ejemplo desde el HolographicHRTFAudioSample.</span><span class="sxs-lookup"><span data-stu-id="d4b25-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="d4b25-107">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="d4b25-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="d4b25-108">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="d4b25-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="d4b25-109">Información general del sonido espacial relativa de Head</span><span class="sxs-lookup"><span data-stu-id="d4b25-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="d4b25-110">Sonido espacial se implementa como un **el objeto de procesamiento de audio (APO)** que usa un **head relacionados con la función de transferencia (HRTF)** filtrar *spatialize* una secuencia de audio normal.</span><span class="sxs-lookup"><span data-stu-id="d4b25-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="d4b25-111">Incluir estos archivos de encabezado en pch.h para tener acceso a la API de audio:</span><span class="sxs-lookup"><span data-stu-id="d4b25-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="d4b25-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="d4b25-112">XAudio2.h</span></span>
* <span data-ttu-id="d4b25-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="d4b25-113">xapo.h</span></span>
* <span data-ttu-id="d4b25-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="d4b25-114">hrtfapoapi.h</span></span>

<span data-ttu-id="d4b25-115">Para configurar el sonido espacial:</span><span class="sxs-lookup"><span data-stu-id="d4b25-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="d4b25-116">Llame a [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) para inicializar una nueva APO para audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="d4b25-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="d4b25-117">Asignar el [parámetros HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) y [entorno HRTF](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) para definir las características de la APO espacial de sonido acústicas.</span><span class="sxs-lookup"><span data-stu-id="d4b25-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="d4b25-118">Configurar el motor de XAudio2 para su procesamiento HRTF.</span><span class="sxs-lookup"><span data-stu-id="d4b25-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="d4b25-119">Crear un [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) objeto y llamar a [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="d4b25-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="d4b25-120">La implementación de la aplicación de DirectX HRTF y sonido espacial</span><span class="sxs-lookup"><span data-stu-id="d4b25-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="d4b25-121">Puede lograr una variedad de efectos al configurar el APO HRTF con entornos y parámetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="d4b25-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="d4b25-122">Use el siguiente código para explorar las posibilidades.</span><span class="sxs-lookup"><span data-stu-id="d4b25-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="d4b25-123">Descargue el ejemplo de código de plataforma Universal de Windows desde aquí: [Ejemplo espacial de sonido](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="d4b25-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="d4b25-124">Tipos auxiliares están disponibles en estos archivos:</span><span class="sxs-lookup"><span data-stu-id="d4b25-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="d4b25-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Carga los archivos de audio con Media Foundation y [IMFSourceReader interfaz](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="d4b25-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="d4b25-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementa el **SetupXAudio2** esa función para inicializar XAudio2 para su procesamiento HRTF.</span><span class="sxs-lookup"><span data-stu-id="d4b25-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="d4b25-127">Agregar sonido espacial para un origen de multidireccionales</span><span class="sxs-lookup"><span data-stu-id="d4b25-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="d4b25-128">Algunos hologramas en el entorno del usuario emiten sonido por igual en todas las direcciones.</span><span class="sxs-lookup"><span data-stu-id="d4b25-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="d4b25-129">El código siguiente muestra cómo inicializar un APO para emitir un sonido multidireccionales.</span><span class="sxs-lookup"><span data-stu-id="d4b25-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="d4b25-130">En este ejemplo, aplicamos este concepto en el cubo girando de la plantilla de aplicación de Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="d4b25-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="d4b25-131">Para obtener el código completo, vea [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="d4b25-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="d4b25-132">**Motor de la ventana espacial sonido solo admite 48 samplerate k para la reproducción. La mayoría de los programas de middleware, como Unity, convertirán automáticamente los archivos de sonido en el formato deseado, pero si empieza a trabajar en niveles inferiores en el sistema de audio o realizar su propia, esto es muy importante recordar evitar bloqueos o un comportamiento no deseado, como Error del sistema HRTF.**</span><span class="sxs-lookup"><span data-stu-id="d4b25-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="d4b25-133">En primer lugar, debemos inicializar la APO.</span><span class="sxs-lookup"><span data-stu-id="d4b25-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="d4b25-134">En nuestra aplicación de ejemplo holográfica, elegimos hacerlo una vez que tenemos la **HolographicSpace**.</span><span class="sxs-lookup"><span data-stu-id="d4b25-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="d4b25-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="d4b25-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="d4b25-136">La implementación de Initialize, desde *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="d4b25-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="d4b25-137">Después de configura el APO HRTF, llame a [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) en la voz de origen para reproducir el audio.</span><span class="sxs-lookup"><span data-stu-id="d4b25-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="d4b25-138">En nuestra aplicación de ejemplo, elegimos colocarlo en un bucle para que pueda continuar para oír el sonido que provienen del cubo.</span><span class="sxs-lookup"><span data-stu-id="d4b25-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="d4b25-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="d4b25-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="d4b25-140">Desde *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="d4b25-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="d4b25-141">Ahora, cada vez que se actualiza el marco, necesitamos actualizar la posición del holograma en relación con el propio dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d4b25-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="d4b25-142">Esto es porque la HRTF posiciones siempre se expresan con respecto a la cabeza del usuario, incluida la posición principal y la orientación.</span><span class="sxs-lookup"><span data-stu-id="d4b25-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="d4b25-143">Para hacer esto en un HolographicSpace, necesitamos construir una matriz de transformación de nuestro sistema de coordenadas SpatialStationaryFrameOfReference a un sistema de coordenadas que se fija en el propio dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d4b25-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="d4b25-144">From *HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="d4b25-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="d4b25-145">La posición de la HRTF se aplica directamente a la APO sonido por la clase de aplicación auxiliar OmnidirectionalSound.</span><span class="sxs-lookup"><span data-stu-id="d4b25-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="d4b25-146">Desde *OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="d4b25-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="d4b25-147">Ya está.</span><span class="sxs-lookup"><span data-stu-id="d4b25-147">That's it!</span></span> <span data-ttu-id="d4b25-148">Siga leyendo para obtener más información sobre lo que puede hacer con audio HRTF y Windows Holographic.</span><span class="sxs-lookup"><span data-stu-id="d4b25-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="d4b25-149">Inicializar espacial sonido para un origen direccional</span><span class="sxs-lookup"><span data-stu-id="d4b25-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="d4b25-150">Algunos hologramas en el entorno del usuario emiten sonido principalmente en una dirección.</span><span class="sxs-lookup"><span data-stu-id="d4b25-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="d4b25-151">Este patrón de sonido se denomina *hipercardiode* porque parece un corazón de dibujos animados.</span><span class="sxs-lookup"><span data-stu-id="d4b25-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="d4b25-152">El código siguiente muestra cómo inicializar un APO para emitir direccional sonido.</span><span class="sxs-lookup"><span data-stu-id="d4b25-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="d4b25-153">Para obtener el código completo, vea [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="d4b25-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="d4b25-154">Después de configura el APO HRTF, llame a [iniciar](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) en la voz de origen para reproducir el audio.</span><span class="sxs-lookup"><span data-stu-id="d4b25-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="d4b25-155">Implementar decadencia personalizado</span><span class="sxs-lookup"><span data-stu-id="d4b25-155">Implement custom decay</span></span>

<span data-ttu-id="d4b25-156">Puede invalidar la velocidad a la que un sonido espacial decaiga con la distancia o a qué distancia corta por completo.</span><span class="sxs-lookup"><span data-stu-id="d4b25-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="d4b25-157">Para implementar un comportamiento personalizado decadencia en un sonido espacial, rellenar un [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) y asígnelo a la **distanceDecay** campo un [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) antes de pasarlo a la [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) función.</span><span class="sxs-lookup"><span data-stu-id="d4b25-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="d4b25-158">Agregue el código siguiente a la **inicializar** mostrado anteriormente para especificar el comportamiento personalizado de decadencia de método.</span><span class="sxs-lookup"><span data-stu-id="d4b25-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="d4b25-159">Para obtener el código completo, vea [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="d4b25-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
