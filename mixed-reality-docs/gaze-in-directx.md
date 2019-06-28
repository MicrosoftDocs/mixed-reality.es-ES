---
title: Mirada principal y de ojo de DirectX
description: Guía del desarrollador para usar mirada principal y seguimiento en las aplicaciones nativas de DirectX de los ojos.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: mirada, mirada principal, head de seguimiento, seguimiento de los ojos, directx, entrada, hologramas
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414407"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>Entrada de DirectX que mirar HEAD y ocular

En Windows Mixed Reality, ojo y una mirada principal entrada se utiliza para determinar lo que está mirando el usuario. Esto se puede usar para los modelos de entrada principales como [head mirada y confirmación](gaze-and-commit.md)y también para proporcionar contexto para los tipos de interacciones. Hay dos tipos de mirada vectores disponibles a través de la API: head mirada y mirada ojos.  Ambos se proporcionan como una de las tres dimensiones ray con un origen y la dirección. Las aplicaciones pueden raycast, a continuación, en su segundo plano o en el mundo real y determine lo que tiene como destino el usuario.

**Head que mirar** representa la dirección en la que apunta head del usuario en. Pensar en esto como la posición y la dirección de avance del propio dispositivo, con la posición que representa el centro, seleccione entre las dos pantallas.  Mirada HEAD está disponible en todos los dispositivos de realidad mixta.

**Mirada ojo** representa la dirección en que se busca la vista del usuario. El origen se encuentra entre la vista del usuario.  Está disponible en dispositivos de realidad mixta que incluyan atento al sistema de seguimiento.

Head y ocular rayos mirada son accesibles a través de la [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. Basta con llamar a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo especificado y [del sistema de coordenadas](coordinate-systems-in-directx.md). Este SpatialPointerPose contiene un origen de mirada principal y la dirección. También contiene un origen de mirada de ojo y una dirección si rastreo ocular está disponible.

## <a name="using-head-gaze"></a>Con una mirada principal

Para obtener acceso a la mirada principal, comience por llamar a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose. Tiene que pasar los parámetros siguientes.
 - Un [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa el sistema de coordenadas deseado para la mirada principal. Esto se representa mediante el *coordinateSystem* variable en el código siguiente. Para obtener más información, visite nuestro [sistemas de coordenadas](coordinate-systems-in-directx.md) Guía del desarrollador.
 - Un [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) que representa la hora exacta de la postura principal solicitado.  Normalmente, usará una marca de tiempo que corresponde a la hora cuando se mostrará el marco actual. Puede obtener esta marca de tiempo de presentación previstos de un [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) objeto, que es accesible a través de la actual [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).  Este objeto HolographicFramePrediction se representa mediante el *predicción* variable en el código siguiente.

 Una vez que tenga un SpatialPointerPose válido, son accesibles como propiedades de la posición principal y la dirección de avance.  El código siguiente muestra cómo obtener acceso a ellos.

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

## <a name="using-eye-gaze"></a>Uso de mirada ojo

La API de mirada ojo es muy similar a la mirada principal.  Usa el mismo [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, que proporciona un rayo de origen y la dirección que se puede raycast frente a la escena.  La única diferencia es que debe habilitar explícitamente el seguimiento de ojo antes de usarlo. Para ello, es preciso realizar dos pasos:
1. Solicitar permiso al usuario para usar el seguimiento de la aplicación de los ojos.
2. Habilitar la capacidad de "Observación Input" en el manifiesto del paquete.

### <a name="requesting-access-to-gaze-input"></a>Solicitar acceso a la entrada que mirar
Cuando la aplicación se está iniciando, llame a [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso a seguimiento de ojos. El sistema solicita al usuario si es necesario y devolver [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) una vez que ha concedido acceso. Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional. El ejemplo siguiente se pone en marcha un std::thread desasociada a esperar el resultado, que se almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.

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
Iniciar un subproceso separado es sólo una opción para controlar las llamadas asincrónicas.  Como alternativa, puede usar el nuevo [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funcionalidad admitida por C++/WinRT.
Este es otro ejemplo que puede solicitar permiso del usuario:
-   EyesPose::IsSupported() permite que la aplicación desencadenar el cuadro de diálogo permiso solo si hay un rastreador de ojos.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Esto es para evitar que emerja una y otra vez la solicitud de permiso.

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


### <a name="declaring-the-gaze-input-capability"></a>Declarar el *que mirar entrada* capacidad

Haga doble clic en el archivo appxmanifest en *el Explorador de soluciones*.  A continuación, navegue hasta la *capacidades* sección y compruebe el *que mirar entrada* capacidad. 

![Capacidad de entrada de mirada](images/gaze-input-capability.png)

Esto agrega las siguientes líneas a la *paquete* sección en el archivo appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Obteniendo el rayo de mirada ojo
Una vez que haya recibido el acceso a ET, es libre para tomar el rayo mirada de ojo de cada fotograma.  Al igual que con la mirada principal, obtenga el [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) mediante una llamada a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo deseado y el sistema de coordenadas. Contiene el SpatialPointerPose un [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) objeto a través de la [ojos](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) propiedad. Esto es distinto de null solo si está habilitado el seguimiento de los ojos. Desde allí puede comprobar si el usuario en el dispositivo tiene un efecto de ojos calibración de seguimiento mediante una llamada a [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  A continuación, use el [que mirar](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) propiedad va a obtener el un [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) que mirar el ojo de contiene una posición y la dirección. La propiedad mirada puede a veces, ser null, así que asegúrese de comprobar esto. Esto puede ocurrir es si un usuario calibrado cierra temporalmente sus ojos.

El código siguiente muestra cómo obtener acceso a rayo mirada ojos.

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

## <a name="correlating-gaze-with-other-inputs"></a>Correlacionar mirada con otras entradas

En ocasiones, es posible que descubra que tiene un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponde con un evento en el pasado. Por ejemplo, si el usuario realiza un aire pulse, la aplicación desee saber lo estaban viendo. Para ello, basta con usar [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el marco de predicción podría ser inexacto tiempo debido a la latencia entre el procesamiento de entrada de sistema y tiempo de visualización. Además, si usa la mirada de ojo para dirigirse a, los ojos tienden a moverse incluso antes de finalizar una acción de confirmación. Esto no supone un problema para un Tap de aire simple, pero resulta más importante al combinar los comandos de voz de larga con movimientos rápidos ojo. Una manera de controlar este escenario es realizar una llamada adicional a [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mediante una marca de tiempo histórico que se corresponde con el evento de entrada.  

Sin embargo, para la entrada que se enruta a través de la SpatialInteractionManager, hay un método más sencillo. El [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tiene su propio [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) función. Llamar a que proporcionará una correlación [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) sin las suposiciones. Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, eche un vistazo a la [las manos y los controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md) documentación.

## <a name="see-also"></a>Vea también
* [Modelo de entrada principal mirada y confirmación](gaze-and-commit.md)
* [Mirada en HoloLens 2](eye-tracking.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
