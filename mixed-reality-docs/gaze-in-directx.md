---
title: Mira hacia el principio y el ojo en DirectX
description: Guía del desarrollador para usar el seguimiento de la mirada y el ojo en aplicaciones de DirectX nativas.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: miras hacia abajo, hacia abajo, seguimiento del cabezal, seguimiento ocular, DirectX, entrada, hologramas
ms.openlocfilehash: 664657b9ab01530a608e31091823e828cc99d0cd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926560"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Entrada de ojo y mira fijamente en DirectX

En Windows Mixed Reality, se usa la entrada de ojo y mirarnos para determinar lo que el usuario está examinando. Se puede usar para controlar los modelos de entrada principales, como el [encabezado y la confirmación](gaze-and-commit.md), y también para proporcionar contexto para tipos de interacciones. Hay dos tipos de vectores de miración disponibles a través de la API: encabezado y ojo.  Ambos se proporcionan como un rayo tridimensional con un origen y una dirección. A continuación, las aplicaciones pueden Raycast en sus escenas, o en el mundo real, y determinar el destino del usuario.

**Head-fijamente** representa la dirección en la que apunta el encabezado del usuario. Considere esto como la posición y la dirección hacia delante del propio dispositivo, con la posición que representa el punto central entre las dos pantallas. La mirada está disponible en todos los dispositivos de realidad mixta.

**Ojo:** representa la dirección que miran los ojos del usuario. El origen se encuentra entre los ojos del usuario.  Está disponible en dispositivos de realidad mixta que incluyen un sistema de seguimiento ocular.

Se puede acceder a los rayos de mira y hacia la vista a través de la API de [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) . Simplemente llame a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose en la marca de tiempo y el [sistema de coordenadas](coordinate-systems-in-directx.md)especificados. Este SpatialPointerPose contiene el origen y la dirección del encabezado. También contiene un origen y una dirección de mirada si el seguimiento ocular está disponible.

### <a name="device-support"></a>Compatibilidad con dispositivos
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Ofrecen</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Mirada con la cabeza</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Miras hacia abajo</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Uso del encabezado de mira

Para obtener acceso al encabezado de la mirada, empiece llamando a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) para recibir un nuevo objeto SpatialPointerPose. Debe pasar los siguientes parámetros.
 - [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) que representa el sistema de coordenadas deseado del encabezado. Se representa mediante la variable *coordenadas* en el código siguiente. Para obtener más información, visite nuestra guía para desarrolladores de [sistemas de coordenadas](coordinate-systems-in-directx.md) .
 - [Marca](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) de tiempo que representa la hora exacta de la solicitud de encabezado.  Normalmente, usará una marca de tiempo que se corresponda con la hora a la que se mostrará el fotograma actual. Puede obtener esta marca de tiempo de visualización de predicción de un objeto [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que es accesible a través de la [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)actual.  Este objeto HolographicFramePrediction se representa mediante la variable de *predicción* en el código siguiente.

 Una vez que tenga un SpatialPointerPose válido, la posición del encabezado y la dirección hacia delante se pueden obtener como propiedades.  En el código siguiente se muestra cómo obtener acceso a ellos.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Uso de la mirada

Tenga en cuenta que para que los usuarios usen la entrada ocular, cada usuario tiene que pasar por una [calibración de usuario de seguimiento de ojos](calibration.md) la primera vez que usa el dispositivo. La API ocular es muy similar a la punta.
Usa la misma API de [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) , que proporciona un origen y una dirección de rayo que puede Raycast en la escena.  La única diferencia es que debe habilitar explícitamente el seguimiento ocular antes de usarlo. Para ello, debe realizar dos pasos:
1. Solicitar permiso de usuario para usar el seguimiento ocular en la aplicación.
2. Habilite la funcionalidad de "entrada de Miración" en el manifiesto del paquete.

### <a name="requesting-access-to-eye-gaze-input"></a>Solicitud de acceso a la entrada de mirada
Cuando se inicia la aplicación, llame a [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) para solicitar acceso al seguimiento ocular. El sistema solicitará al usuario si es necesario y devolverá [GazeInputAccessStatus:: allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) una vez que se haya concedido el acceso. Se trata de una llamada asincrónica, por lo que requiere un poco de administración adicional. En el ejemplo siguiente se pone en marcha un método STD:: Thread separado para esperar el resultado, que almacena en una variable miembro denominada *m_isEyeTrackingEnabled*.

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
Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas. Como alternativa, puede usar la nueva funcionalidad de [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) compatible con C++/WinRT.
Este es otro ejemplo para pedir permiso de usuario:
-   EyesPose:: IsSupported () permite que la aplicación desencadene el cuadro de diálogo de permiso solo si hay un seguimiento ocular.
-   M_gazeInputAccessStatus GazeInputAccessStatus; Esto es para evitar la acumulación de la solicitud de permiso una y otra vez.

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

### <a name="getting-the-eye-gaze-ray"></a>Obtención del rayo ojo
Una vez que haya recibido el acceso a ET, tendrá la libertad de captar el rayo cada fotograma.
Del mismo modo que con el encabezado de la mirada, obtenga el [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) llamando a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con una marca de tiempo y un sistema de coordenadas deseados. SpatialPointerPose contiene un objeto [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) a través de la propiedad [Eyes](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) . No es null solo si está habilitado el seguimiento ocular. Desde allí, puede comprobar si el usuario del dispositivo tiene una calibración de seguimiento de ojo llamando a [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  A continuación, use la propiedad [fijamente](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) para obtener el [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) que contiene la posición y la dirección de la mirada. A veces, la propiedad fijamente puede ser null, por lo que debe asegurarse de comprobarlo. Esto puede ocurrir si un usuario calibrado cierra temporalmente sus ojos.

En el código siguiente se muestra cómo tener acceso al rayo ojo.

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-is-not-available"></a>Reserva cuando el seguimiento ocular no está disponible
Tal y como se mencionó en nuestros [documentos de diseño de seguimiento ocular](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available), tanto los diseñadores como los desarrolladores deben tener en cuenta que puede haber instancias en las que los datos de seguimiento ocular no estén disponibles para la aplicación.
Hay varias razones por las que, desde un usuario que no se está calibrando, el usuario ha denegado el acceso a sus datos de seguimiento ocular o simplemente interferencias temporales (como manchas en el visor de HoloLens o pelo occluding). Aunque algunas de las API ya se han mencionado en este documento, en el siguiente se proporciona un resumen de cómo detectar que el seguimiento ocular está disponible como referencia rápida: 

* Compruebe que el sistema admite el seguimiento ocular. Llame al *método*siguiente: [Windows. percepción. people. EyesPose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Compruebe que el usuario está calibrado. Llame a la *propiedad*siguiente: [Windows. imception. people. EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid) 

* Compruebe que el usuario ha dado permiso a la aplicación para usar los datos de seguimiento ocular: recupere el _' GazeInputAccessStatus '_ actual. Un ejemplo de cómo hacerlo se explica cómo solicitar el [acceso a la entrada de mirada](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).   

Además, puede que desee comprobar que los datos de seguimiento ocular no están obsoletos agregando un tiempo de espera entre las actualizaciones de datos de seguimiento de ojos recibidos y, de lo contrario, reserva a Head-mira como se describe a continuación.  
Para obtener más información, visite nuestras [consideraciones de diseño de reserva](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Correlacionar miradamente con otras entradas
En ocasiones, es posible que necesite un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) que se corresponda con un evento en el pasado. Por ejemplo, si el usuario realiza una pulsación aérea, es posible que la aplicación desee saber lo que estaba viendo. Con este propósito, simplemente el uso de [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) con el tiempo de fotograma previsto sería incorrecto debido a la latencia entre el procesamiento de la entrada del sistema y el tiempo de presentación. Además, si se usa la mirada ocular para el destino, nuestros ojos tienden a moverse incluso antes de finalizar una acción de confirmación. Se trata de un problema menos importante en el caso de una simple pulsación del aire, pero es más crítico cuando se combinan comandos de voz largos con movimientos oculares rápidos. Una manera de controlar este escenario consiste en realizar una llamada adicional a [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mediante una marca de tiempo histórica que se corresponda con el evento de entrada.  

Sin embargo, para la entrada que enruta a través de SpatialInteractionManager, hay un método más sencillo. [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) tiene su propia función [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) . Llamar a que proporcionará un [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) perfectamente correlacionado sin las conjeturas. Para obtener más información sobre cómo trabajar con SpatialInteractionSourceStates, eche un vistazo a los [controladores de manos y de movimiento de la documentación de DirectX](hands-and-motion-controllers-in-directx.md) .

<br>

## <a name="calibration"></a>Curva
Para que el seguimiento de los ojos funcione con precisión, cada usuario debe realizar un [seguimiento ocular](calibration.md)de la calibración del usuario. Esto permite que el dispositivo ajuste el sistema para una experiencia de visualización más cómoda y de mayor calidad para el usuario y para garantizar un seguimiento de ojo preciso al mismo tiempo. Los desarrolladores no tienen que hacer nada en su extremo para administrar la calibración del usuario. El sistema garantizará que se solicite al usuario que calibre el dispositivo en las siguientes circunstancias:
* El usuario está usando el dispositivo por primera vez
* El usuario previamente decidió salir del proceso de calibración
* El proceso de calibración no se realizó correctamente la última vez que el usuario usaba el dispositivo

Los desarrolladores deben asegurarse de proporcionar soporte técnico adecuado a los usuarios para los que es posible que los datos de seguimiento ocular no estén disponibles. Más información sobre las consideraciones sobre las soluciones de reserva en el [seguimiento de Hololens 2](eye-tracking.md).

<br>

## <a name="see-also"></a>Consulta también
* [Calibración](calibration.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Miras a la vista de HoloLens 2](eye-tracking.md)
* [Miran y confirman el modelo de entrada](gaze-and-commit.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)
