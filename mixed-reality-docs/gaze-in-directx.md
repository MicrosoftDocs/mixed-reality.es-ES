---
title: Mira hacia el principio y el ojo en DirectX
description: Guía del desarrollador para usar el seguimiento de la mirada y el ojo en aplicaciones de DirectX nativas.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: mira fijamente, mira hacia abajo, seguimiento del cabezal, seguimiento ocular, DirectX, entrada, hologramas
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414407"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="afc89-104">Entrada y ojos miradas en DirectX</span><span class="sxs-lookup"><span data-stu-id="afc89-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="afc89-105">En Windows Mixed Reality, se usa la entrada de ojo y mirarnos para determinar lo que el usuario está examinando.</span><span class="sxs-lookup"><span data-stu-id="afc89-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="afc89-106">Se puede usar para controlar los modelos de entrada principales, como [Head fijamente y commit](gaze-and-commit.md), y también para proporcionar contexto para tipos de interacciones.</span><span class="sxs-lookup"><span data-stu-id="afc89-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="afc89-107">Hay dos tipos de vectores de miración disponibles a través de la API: encabezado de mira hacia abajo y ojo.</span><span class="sxs-lookup"><span data-stu-id="afc89-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="afc89-108">Ambos se proporcionan como un rayo tridimensional con un origen y una dirección.</span><span class="sxs-lookup"><span data-stu-id="afc89-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="afc89-109">A continuación, las aplicaciones pueden Raycast en sus escenas, o en el mundo real, y determinar el destino del usuario.</span><span class="sxs-lookup"><span data-stu-id="afc89-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="afc89-110">**Encabezado mira** la dirección en la que se señala el encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="afc89-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="afc89-111">Considere esto como la posición y la dirección hacia delante del propio dispositivo, con la posición que representa el punto central entre las dos pantallas.</span><span class="sxs-lookup"><span data-stu-id="afc89-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="afc89-112">La mirada está disponible en todos los dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="afc89-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="afc89-113">**Mira fijamente** representa la dirección en la que miran los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="afc89-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="afc89-114">El origen se encuentra entre los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="afc89-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="afc89-115">Está disponible en dispositivos de realidad mixta que incluyen un sistema de seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="afc89-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="afc89-116">Se puede acceder a los rayos de mira hacia la cabeza y el ojo a través de la API de [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) .</span><span class="sxs-lookup"><span data-stu-id="afc89-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="afc89-117">Simplemente llame a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo y el [sistema de coordenadas](coordinate-systems-in-directx.md)especificados.</span><span class="sxs-lookup"><span data-stu-id="afc89-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="afc89-118">Este SpatialPointerPose contiene un origen y una dirección de encabezado.</span><span class="sxs-lookup"><span data-stu-id="afc89-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="afc89-119">También contiene un origen y una dirección de ojo si el seguimiento ocular está disponible.</span><span class="sxs-lookup"><span data-stu-id="afc89-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="afc89-120">Uso de la punta</span><span class="sxs-lookup"><span data-stu-id="afc89-120">Using head gaze</span></span>

<span data-ttu-id="afc89-121">Para obtener acceso al encabezado, empiece por llamar a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="afc89-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="afc89-122">Debe pasar los siguientes parámetros.</span><span class="sxs-lookup"><span data-stu-id="afc89-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="afc89-123">[SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa el sistema de coordenadas deseado del encabezado.</span><span class="sxs-lookup"><span data-stu-id="afc89-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="afc89-124">Se representa mediante la variable *coordenadas* en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="afc89-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="afc89-125">Para obtener más información, visite nuestra guía para desarrolladores de [sistemas de coordenadas](coordinate-systems-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="afc89-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="afc89-126">[Marca](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) de tiempo que representa la hora exacta de la solicitud de encabezado.</span><span class="sxs-lookup"><span data-stu-id="afc89-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="afc89-127">Normalmente, usará una marca de tiempo que se corresponda con la hora a la que se mostrará el fotograma actual.</span><span class="sxs-lookup"><span data-stu-id="afc89-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="afc89-128">Puede obtener esta marca de tiempo de visualización de predicción de un objeto [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que es accesible a través de la [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)actual.</span><span class="sxs-lookup"><span data-stu-id="afc89-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="afc89-129">Este objeto HolographicFramePrediction se representa mediante la  variable de predicción en el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="afc89-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="afc89-130">Una vez que tenga un SpatialPointerPose válido, la posición del encabezado y la dirección hacia delante se pueden obtener como propiedades.</span><span class="sxs-lookup"><span data-stu-id="afc89-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="afc89-131">En el código siguiente se muestra cómo obtener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="afc89-131">The following code  shows how to access them.</span></span>

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

## <a name="using-eye-gaze"></a><span data-ttu-id="afc89-132">Con ojo mirado</span><span class="sxs-lookup"><span data-stu-id="afc89-132">Using eye gaze</span></span>

<span data-ttu-id="afc89-133">La API ocular es muy similar a la punta.</span><span class="sxs-lookup"><span data-stu-id="afc89-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="afc89-134">Usa la misma API de [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que proporciona un origen y una dirección de rayo que puede Raycast en la escena.</span><span class="sxs-lookup"><span data-stu-id="afc89-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="afc89-135">La única diferencia es que debe habilitar explícitamente el seguimiento ocular antes de usarlo.</span><span class="sxs-lookup"><span data-stu-id="afc89-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="afc89-136">Para ello, debe realizar dos pasos:</span><span class="sxs-lookup"><span data-stu-id="afc89-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="afc89-137">Solicitar permiso de usuario para usar el seguimiento ocular en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="afc89-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="afc89-138">Habilite la funcionalidad de "entrada de Miración" en el manifiesto del paquete.</span><span class="sxs-lookup"><span data-stu-id="afc89-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="afc89-139">Solicitar acceso a la entrada de mira</span><span class="sxs-lookup"><span data-stu-id="afc89-139">Requesting access to gaze input</span></span>
<span data-ttu-id="afc89-140">Cuando se inicia la aplicación, llame a [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso al seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="afc89-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="afc89-141">El sistema solicitará al usuario si es necesario y devolverá [GazeInputAccessStatus::](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) allowed una vez que se haya concedido el acceso.</span><span class="sxs-lookup"><span data-stu-id="afc89-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="afc89-142">Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional.</span><span class="sxs-lookup"><span data-stu-id="afc89-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="afc89-143">En el ejemplo siguiente se pone en marcha un método STD:: Thread separado para esperar el resultado, que almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.</span><span class="sxs-lookup"><span data-stu-id="afc89-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="afc89-144">Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas.</span><span class="sxs-lookup"><span data-stu-id="afc89-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="afc89-145">Como alternativa, puede usar la nueva funcionalidad de [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) admitida C++por/WinRT.</span><span class="sxs-lookup"><span data-stu-id="afc89-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="afc89-146">Este es otro ejemplo para pedir permiso de usuario:</span><span class="sxs-lookup"><span data-stu-id="afc89-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="afc89-147">EyesPose:: IsSupported () permite que la aplicación desencadene el cuadro de diálogo de permiso solo si hay un seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="afc89-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="afc89-148">GazeInputAccessStatus m_gazeInputAccessStatus; Esto es para evitar la acumulación de la solicitud de permiso una y otra vez.</span><span class="sxs-lookup"><span data-stu-id="afc89-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="afc89-149">Declarar la capacidad de *entrada de mira*</span><span class="sxs-lookup"><span data-stu-id="afc89-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="afc89-150">Haga doble clic en el archivo appxmanifest en *Explorador de soluciones*.</span><span class="sxs-lookup"><span data-stu-id="afc89-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="afc89-151">A continuación, vaya a la sección *funcionalidades* y Compruebe la capacidad de *entrada de mira* .</span><span class="sxs-lookup"><span data-stu-id="afc89-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![Función de entrada de mirada](images/gaze-input-capability.png)

<span data-ttu-id="afc89-153">Esto agrega las líneas siguientes a la sección *Package* del archivo appxmanifest:</span><span class="sxs-lookup"><span data-stu-id="afc89-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="afc89-154">Obtención del rayo mira fijamente</span><span class="sxs-lookup"><span data-stu-id="afc89-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="afc89-155">Una vez que haya recibido el acceso a ET, tendrá la libertad de captar el rayo en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="afc89-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="afc89-156">Al igual que con la punta de la mirada, obtenga el [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) llamando a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo y un sistema de coordenadas deseados.</span><span class="sxs-lookup"><span data-stu-id="afc89-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="afc89-157">SpatialPointerPose contiene un objeto [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) a través de la propiedad [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) .</span><span class="sxs-lookup"><span data-stu-id="afc89-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="afc89-158">No es null solo si está habilitado el seguimiento ocular.</span><span class="sxs-lookup"><span data-stu-id="afc89-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="afc89-159">Desde allí, puede comprobar si el usuario del dispositivo tiene una calibración de seguimiento de ojo llamando a [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span><span class="sxs-lookup"><span data-stu-id="afc89-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="afc89-160">A continuación, use la propiedad [fijamente](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obtener una [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing la posición y la dirección de ojo.</span><span class="sxs-lookup"><span data-stu-id="afc89-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="afc89-161">A veces, la propiedad fijamente puede ser null, por lo que debe asegurarse de comprobarlo.</span><span class="sxs-lookup"><span data-stu-id="afc89-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="afc89-162">Esto puede ocurrir si un usuario calibrado cierra temporalmente sus ojos.</span><span class="sxs-lookup"><span data-stu-id="afc89-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="afc89-163">En el código siguiente se muestra cómo tener acceso al rayo mira fijamente.</span><span class="sxs-lookup"><span data-stu-id="afc89-163">The following code shows how to access the eye gaze ray.</span></span>

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

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="afc89-164">Correlacionar miradamente con otras entradas</span><span class="sxs-lookup"><span data-stu-id="afc89-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="afc89-165">En ocasiones, es posible que necesite un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponda con un evento en el pasado.</span><span class="sxs-lookup"><span data-stu-id="afc89-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="afc89-166">Por ejemplo, si el usuario realiza una pulsación aérea, es posible que la aplicación desee saber lo que estaba viendo.</span><span class="sxs-lookup"><span data-stu-id="afc89-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="afc89-167">Con este propósito, simplemente el uso de [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el tiempo de fotograma previsto sería incorrecto debido a la latencia entre el procesamiento de la entrada del sistema y el tiempo de presentación.</span><span class="sxs-lookup"><span data-stu-id="afc89-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="afc89-168">Además, si miramos la vista de destino, nuestros ojos tienden a moverse incluso antes de finalizar una acción de confirmación.</span><span class="sxs-lookup"><span data-stu-id="afc89-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="afc89-169">Se trata de un problema menos importante en el caso de una simple pulsación del aire, pero es más crítico cuando se combinan comandos de voz largos con movimientos oculares rápidos.</span><span class="sxs-lookup"><span data-stu-id="afc89-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="afc89-170">Una manera de controlar este escenario consiste en realizar una llamada adicional a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mediante una marca de tiempo histórica que se corresponda con el evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="afc89-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="afc89-171">Sin embargo, para la entrada que enruta a través de SpatialInteractionManager, hay un método más sencillo.</span><span class="sxs-lookup"><span data-stu-id="afc89-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="afc89-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tiene su propia función [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .</span><span class="sxs-lookup"><span data-stu-id="afc89-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="afc89-173">Llamar a que proporcionará un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfectamente correlacionado sin las conjeturas.</span><span class="sxs-lookup"><span data-stu-id="afc89-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="afc89-174">Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, eche un vistazo a los [controladores de manos y de movimiento de la documentación de DirectX](hands-and-motion-controllers-in-directx.md) .</span><span class="sxs-lookup"><span data-stu-id="afc89-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="afc89-175">Vea también</span><span class="sxs-lookup"><span data-stu-id="afc89-175">See also</span></span>
* [<span data-ttu-id="afc89-176">Encabezado y el modelo de entrada de confirmación</span><span class="sxs-lookup"><span data-stu-id="afc89-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="afc89-177">Miras a la vista de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="afc89-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="afc89-178">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="afc89-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="afc89-179">Entrada de voz en DirectX</span><span class="sxs-lookup"><span data-stu-id="afc89-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="afc89-180">Manos y controladores de movimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="afc89-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
