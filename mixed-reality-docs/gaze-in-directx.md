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
# <a name="head-and-eye-gaze-input-in-directx"></a>Entrada y ojos miradas en DirectX

En Windows Mixed Reality, se usa la entrada de ojo y mirarnos para determinar lo que el usuario está examinando. Se puede usar para controlar los modelos de entrada principales, como [Head fijamente y commit](gaze-and-commit.md), y también para proporcionar contexto para tipos de interacciones. Hay dos tipos de vectores de miración disponibles a través de la API: encabezado de mira hacia abajo y ojo.  Ambos se proporcionan como un rayo tridimensional con un origen y una dirección. A continuación, las aplicaciones pueden Raycast en sus escenas, o en el mundo real, y determinar el destino del usuario.

**Encabezado mira** la dirección en la que se señala el encabezado del usuario. Considere esto como la posición y la dirección hacia delante del propio dispositivo, con la posición que representa el punto central entre las dos pantallas.  La mirada está disponible en todos los dispositivos de realidad mixta.

**Mira fijamente** representa la dirección en la que miran los ojos del usuario. El origen se encuentra entre los ojos del usuario.  Está disponible en dispositivos de realidad mixta que incluyen un sistema de seguimiento ocular.

Se puede acceder a los rayos de mira hacia la cabeza y el ojo a través de la API de [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . Simplemente llame a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo y el [sistema de coordenadas](coordinate-systems-in-directx.md)especificados. Este SpatialPointerPose contiene un origen y una dirección de encabezado. También contiene un origen y una dirección de ojo si el seguimiento ocular está disponible.

## <a name="using-head-gaze"></a>Uso de la punta

Para obtener acceso al encabezado, empiece por llamar a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose. Debe pasar los siguientes parámetros.
 - [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa el sistema de coordenadas deseado del encabezado. Se representa mediante la variable *coordenadas* en el código siguiente. Para obtener más información, visite nuestra guía para desarrolladores de [sistemas de coordenadas](coordinate-systems-in-directx.md) .
 - [Marca](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) de tiempo que representa la hora exacta de la solicitud de encabezado.  Normalmente, usará una marca de tiempo que se corresponda con la hora a la que se mostrará el fotograma actual. Puede obtener esta marca de tiempo de visualización de predicción de un objeto [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que es accesible a través de la [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)actual.  Este objeto HolographicFramePrediction se representa mediante la  variable de predicción en el código siguiente.

 Una vez que tenga un SpatialPointerPose válido, la posición del encabezado y la dirección hacia delante se pueden obtener como propiedades.  En el código siguiente se muestra cómo obtener acceso a ellos.

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

## <a name="using-eye-gaze"></a>Con ojo mirado

La API ocular es muy similar a la punta.  Usa la misma API de [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que proporciona un origen y una dirección de rayo que puede Raycast en la escena.  La única diferencia es que debe habilitar explícitamente el seguimiento ocular antes de usarlo. Para ello, debe realizar dos pasos:
1. Solicitar permiso de usuario para usar el seguimiento ocular en la aplicación.
2. Habilite la funcionalidad de "entrada de Miración" en el manifiesto del paquete.

### <a name="requesting-access-to-gaze-input"></a>Solicitar acceso a la entrada de mira
Cuando se inicia la aplicación, llame a [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso al seguimiento ocular. El sistema solicitará al usuario si es necesario y devolverá [GazeInputAccessStatus::](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) allowed una vez que se haya concedido el acceso. Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional. En el ejemplo siguiente se pone en marcha un método STD:: Thread separado para esperar el resultado, que almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.

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
Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas.  Como alternativa, puede usar la nueva funcionalidad de [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) admitida C++por/WinRT.
Este es otro ejemplo para pedir permiso de usuario:
-   EyesPose:: IsSupported () permite que la aplicación desencadene el cuadro de diálogo de permiso solo si hay un seguimiento ocular.
-   GazeInputAccessStatus m_gazeInputAccessStatus; Esto es para evitar la acumulación de la solicitud de permiso una y otra vez.

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


### <a name="declaring-the-gaze-input-capability"></a>Declarar la capacidad de *entrada de mira*

Haga doble clic en el archivo appxmanifest en *Explorador de soluciones*.  A continuación, vaya a la sección *funcionalidades* y Compruebe la capacidad de *entrada de mira* . 

![Función de entrada de mirada](images/gaze-input-capability.png)

Esto agrega las líneas siguientes a la sección *Package* del archivo appxmanifest:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Obtención del rayo mira fijamente
Una vez que haya recibido el acceso a ET, tendrá la libertad de captar el rayo en cada fotograma.  Al igual que con la punta de la mirada, obtenga el [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) llamando a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo y un sistema de coordenadas deseados. SpatialPointerPose contiene un objeto [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) a través de la propiedad [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . No es null solo si está habilitado el seguimiento ocular. Desde allí, puede comprobar si el usuario del dispositivo tiene una calibración de seguimiento de ojo llamando a [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  A continuación, use la propiedad [fijamente](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obtener una [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing la posición y la dirección de ojo. A veces, la propiedad fijamente puede ser null, por lo que debe asegurarse de comprobarlo. Esto puede ocurrir si un usuario calibrado cierra temporalmente sus ojos.

En el código siguiente se muestra cómo tener acceso al rayo mira fijamente.

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

## <a name="correlating-gaze-with-other-inputs"></a>Correlacionar miradamente con otras entradas

En ocasiones, es posible que necesite un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponda con un evento en el pasado. Por ejemplo, si el usuario realiza una pulsación aérea, es posible que la aplicación desee saber lo que estaba viendo. Con este propósito, simplemente el uso de [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el tiempo de fotograma previsto sería incorrecto debido a la latencia entre el procesamiento de la entrada del sistema y el tiempo de presentación. Además, si miramos la vista de destino, nuestros ojos tienden a moverse incluso antes de finalizar una acción de confirmación. Se trata de un problema menos importante en el caso de una simple pulsación del aire, pero es más crítico cuando se combinan comandos de voz largos con movimientos oculares rápidos. Una manera de controlar este escenario consiste en realizar una llamada adicional a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mediante una marca de tiempo histórica que se corresponda con el evento de entrada.  

Sin embargo, para la entrada que enruta a través de SpatialInteractionManager, hay un método más sencillo. [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tiene su propia función [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . Llamar a que proporcionará un [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) perfectamente correlacionado sin las conjeturas. Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, eche un vistazo a los [controladores de manos y de movimiento de la documentación de DirectX](hands-and-motion-controllers-in-directx.md) .

## <a name="see-also"></a>Vea también
* [Encabezado y el modelo de entrada de confirmación](gaze-and-commit.md)
* [Miras a la vista de HoloLens 2](eye-tracking.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
