---
title: Mirada principal y de ojo de DirectX
description: Guía del desarrollador para usar mirada principal y seguimiento en las aplicaciones nativas de DirectX de los ojos.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: mirada, mirada principal, head de seguimiento, seguimiento de los ojos, directx, entrada, hologramas
ms.openlocfilehash: ac72c5305527ed2d68945aeb32051cf2246a736e
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453741"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="1f18d-104">Entrada de DirectX que mirar HEAD y ocular</span><span class="sxs-lookup"><span data-stu-id="1f18d-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="1f18d-105">En Windows Mixed Reality, ojo y una mirada principal entrada se utiliza para determinar lo que está mirando el usuario.</span><span class="sxs-lookup"><span data-stu-id="1f18d-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="1f18d-106">Esto se puede usar para los modelos de entrada principales como [head mirada y confirmación](gaze-and-commit.md)y también para proporcionar contexto para los tipos de interacciones.</span><span class="sxs-lookup"><span data-stu-id="1f18d-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="1f18d-107">Hay dos tipos de mirada vectores disponibles a través de la API: head mirada y mirada ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="1f18d-108">Ambos se proporcionan como una de las tres dimensiones ray con un origen y la dirección.</span><span class="sxs-lookup"><span data-stu-id="1f18d-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="1f18d-109">Las aplicaciones pueden raycast, a continuación, en su segundo plano o en el mundo real y determine lo que tiene como destino el usuario.</span><span class="sxs-lookup"><span data-stu-id="1f18d-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="1f18d-110">**Head que mirar** representa la dirección en la que apunta head del usuario en.</span><span class="sxs-lookup"><span data-stu-id="1f18d-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="1f18d-111">Pensar en esto como la posición y la dirección de avance del propio dispositivo, con la posición que representa el centro, seleccione entre las dos pantallas.</span><span class="sxs-lookup"><span data-stu-id="1f18d-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="1f18d-112">Mirada HEAD está disponible en todos los dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1f18d-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="1f18d-113">**Mirada ojo** representa la dirección en que se busca la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="1f18d-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="1f18d-114">El origen se encuentra entre la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="1f18d-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="1f18d-115">Está disponible en dispositivos de realidad mixta que incluyan atento al sistema de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="1f18d-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="1f18d-116">Head y ocular rayos mirada son accesibles a través de la [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span><span class="sxs-lookup"><span data-stu-id="1f18d-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="1f18d-117">Basta con llamar a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo especificado y [del sistema de coordenadas](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="1f18d-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="1f18d-118">Este SpatialPointerPose contiene un origen de mirada principal y la dirección.</span><span class="sxs-lookup"><span data-stu-id="1f18d-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="1f18d-119">También contiene un origen de mirada de ojo y una dirección si rastreo ocular está disponible.</span><span class="sxs-lookup"><span data-stu-id="1f18d-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="1f18d-120">Con una mirada principal</span><span class="sxs-lookup"><span data-stu-id="1f18d-120">Using head gaze</span></span>

<span data-ttu-id="1f18d-121">Para obtener acceso a la mirada principal, comience por llamar a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="1f18d-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="1f18d-122">Tiene que pasar los parámetros siguientes.</span><span class="sxs-lookup"><span data-stu-id="1f18d-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="1f18d-123">Un [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa el sistema de coordenadas deseado para la mirada principal.</span><span class="sxs-lookup"><span data-stu-id="1f18d-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="1f18d-124">Esto se representa mediante el *coordinateSystem* variable en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1f18d-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="1f18d-125">Para obtener más información, visite nuestro [sistemas de coordenadas](coordinate-systems-in-directx.md) Guía del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="1f18d-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="1f18d-126">Un [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) que representa la hora exacta de la postura principal solicitado.</span><span class="sxs-lookup"><span data-stu-id="1f18d-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="1f18d-127">Normalmente, usará una marca de tiempo que corresponde a la hora cuando se mostrará el marco actual.</span><span class="sxs-lookup"><span data-stu-id="1f18d-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="1f18d-128">Puede obtener esta marca de tiempo de presentación previstos de un [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) objeto, que es accesible a través de la actual [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="1f18d-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="1f18d-129">Este objeto HolographicFramePrediction se representa mediante el *predicción* variable en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1f18d-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="1f18d-130">Una vez que tenga un SpatialPointerPose válido, son accesibles como propiedades de la posición principal y la dirección de avance.</span><span class="sxs-lookup"><span data-stu-id="1f18d-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="1f18d-131">El código siguiente muestra cómo obtener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="1f18d-132">Uso de mirada ojo</span><span class="sxs-lookup"><span data-stu-id="1f18d-132">Using eye gaze</span></span>

<span data-ttu-id="1f18d-133">La API de mirada ojo es muy similar a la mirada principal.</span><span class="sxs-lookup"><span data-stu-id="1f18d-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="1f18d-134">Usa el mismo [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, que proporciona un rayo de origen y la dirección que se puede raycast frente a la escena.</span><span class="sxs-lookup"><span data-stu-id="1f18d-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="1f18d-135">La única diferencia es que debe habilitar explícitamente el seguimiento de ojo antes de usarlo.</span><span class="sxs-lookup"><span data-stu-id="1f18d-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="1f18d-136">Para ello, es preciso realizar dos pasos:</span><span class="sxs-lookup"><span data-stu-id="1f18d-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="1f18d-137">Solicitar permiso al usuario para usar el seguimiento de la aplicación de los ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="1f18d-138">Habilitar la capacidad de "Observación Input" en el manifiesto del paquete.</span><span class="sxs-lookup"><span data-stu-id="1f18d-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="1f18d-139">Solicitar acceso a la entrada que mirar</span><span class="sxs-lookup"><span data-stu-id="1f18d-139">Requesting access to gaze input</span></span>
<span data-ttu-id="1f18d-140">Cuando la aplicación se está iniciando, llame a [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso a seguimiento de ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="1f18d-141">El sistema solicita al usuario si es necesario y devolver [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) una vez que ha concedido acceso.</span><span class="sxs-lookup"><span data-stu-id="1f18d-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="1f18d-142">Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional.</span><span class="sxs-lookup"><span data-stu-id="1f18d-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="1f18d-143">El ejemplo siguiente se pone en marcha un std::thread desasociada a esperar el resultado, que se almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="1f18d-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="1f18d-144">Iniciar un subproceso separado es sólo una opción para controlar las llamadas asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="1f18d-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="1f18d-145">Como alternativa, puede usar el nuevo [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funcionalidad admitida por C++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="1f18d-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="1f18d-146">Este es otro ejemplo que puede solicitar permiso del usuario:</span><span class="sxs-lookup"><span data-stu-id="1f18d-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="1f18d-147">EyesPose::IsSupported() permite que la aplicación desencadenar el cuadro de diálogo permiso solo si hay un rastreador de ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="1f18d-148">GazeInputAccessStatus m_gazeInputAccessStatus; Esto es para evitar que emerja una y otra vez la solicitud de permiso.</span><span class="sxs-lookup"><span data-stu-id="1f18d-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="1f18d-149">Declarar el *que mirar entrada* capacidad</span><span class="sxs-lookup"><span data-stu-id="1f18d-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="1f18d-150">Haga doble clic en el archivo appxmanifest en *el Explorador de soluciones*.</span><span class="sxs-lookup"><span data-stu-id="1f18d-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="1f18d-151">A continuación, navegue hasta la *capacidades* sección y compruebe el *que mirar entrada* capacidad.</span><span class="sxs-lookup"><span data-stu-id="1f18d-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Capacidad de entrada de mirada](images/gaze-input-capability.png)

<span data-ttu-id="1f18d-153">Esto agrega las siguientes líneas a la *paquete* sección en el archivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="1f18d-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="1f18d-154">Obteniendo el rayo de mirada ojo</span><span class="sxs-lookup"><span data-stu-id="1f18d-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="1f18d-155">Una vez que haya recibido el acceso a ET, es libre para tomar el rayo mirada de ojo de cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="1f18d-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="1f18d-156">Al igual que con la mirada principal, obtenga el [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) mediante una llamada a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo deseado y el sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="1f18d-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="1f18d-157">Contiene el SpatialPointerPose un [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) objeto a través de la [ojos](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) propiedad.</span><span class="sxs-lookup"><span data-stu-id="1f18d-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="1f18d-158">Esto es distinto de null solo si está habilitado el seguimiento de los ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="1f18d-159">Desde allí puede comprobar si el usuario en el dispositivo tiene un efecto de ojos calibración de seguimiento mediante una llamada a [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="1f18d-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="1f18d-160">A continuación, use el [que mirar](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) propiedad va a obtener el un [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) que mirar el ojo de contiene una posición y la dirección.</span><span class="sxs-lookup"><span data-stu-id="1f18d-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="1f18d-161">La propiedad mirada puede a veces, ser null, así que asegúrese de comprobar esto.</span><span class="sxs-lookup"><span data-stu-id="1f18d-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="1f18d-162">Esto puede ocurrir es si un usuario calibrado cierra temporalmente sus ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="1f18d-163">El código siguiente muestra cómo obtener acceso a rayo mirada ojos.</span><span class="sxs-lookup"><span data-stu-id="1f18d-163">The following code shows how to access the eye gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="1f18d-164">Correlacionar mirada con otras entradas</span><span class="sxs-lookup"><span data-stu-id="1f18d-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="1f18d-165">En ocasiones, es posible que descubra que tiene un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponde con un evento en el pasado.</span><span class="sxs-lookup"><span data-stu-id="1f18d-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="1f18d-166">Por ejemplo, si el usuario realiza un aire pulse, la aplicación desee saber lo estaban viendo.</span><span class="sxs-lookup"><span data-stu-id="1f18d-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="1f18d-167">Para ello, basta con usar [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el marco de predicción podría ser inexacto tiempo debido a la latencia entre el procesamiento de entrada de sistema y tiempo de visualización.</span><span class="sxs-lookup"><span data-stu-id="1f18d-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="1f18d-168">Además, si usa la mirada de ojo para dirigirse a, los ojos tienden a moverse incluso antes de finalizar una acción de confirmación.</span><span class="sxs-lookup"><span data-stu-id="1f18d-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="1f18d-169">Esto no supone un problema para un Tap de aire simple, pero resulta más importante al combinar los comandos de voz de larga con movimientos rápidos ojo.</span><span class="sxs-lookup"><span data-stu-id="1f18d-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="1f18d-170">Una manera de controlar este escenario es realizar una llamada adicional a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mediante una marca de tiempo histórico que se corresponde con el evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="1f18d-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="1f18d-171">Sin embargo, para la entrada que se enruta a través de la SpatialInteractionManager, hay un método más sencillo.</span><span class="sxs-lookup"><span data-stu-id="1f18d-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="1f18d-172">El [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tiene su propio [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) función.</span><span class="sxs-lookup"><span data-stu-id="1f18d-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="1f18d-173">Llamar a que proporcionará una correlación [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) sin las suposiciones.</span><span class="sxs-lookup"><span data-stu-id="1f18d-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="1f18d-174">Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, eche un vistazo a la [las manos y los controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md) documentación.</span><span class="sxs-lookup"><span data-stu-id="1f18d-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f18d-175">Vea también</span><span class="sxs-lookup"><span data-stu-id="1f18d-175">See also</span></span>
* [<span data-ttu-id="1f18d-176">Modelo de entrada principal mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="1f18d-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1f18d-177">Ojo de seguimiento en 2 HoloLens</span><span class="sxs-lookup"><span data-stu-id="1f18d-177">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="1f18d-178">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="1f18d-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="1f18d-179">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="1f18d-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="1f18d-180">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="1f18d-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
