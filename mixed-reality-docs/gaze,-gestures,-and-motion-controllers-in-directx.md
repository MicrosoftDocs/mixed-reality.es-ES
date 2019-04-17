---
title: Mirada, gestos y controladores de movimiento de DirectX
description: Combinación de entrada procedentes de mirada, gestos y los controladores de movimiento, puede habilitar un usuario coloque un holograma en su aplicación.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: observación, gestos, los controladores de movimiento, directx, entrada, hologramas
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605782"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>Mirada, gestos y controladores de movimiento de DirectX

Si va a compilar directamente en la parte superior de la plataforma, tendrá que controlar la entrada procedente del usuario - como donde el usuario examina a través de [mirada principal](gaze.md) y el usuario que ha seleccionado con [gestos](gestures.md) o [motion controladores](motion-controllers.md). Combinación de estas formas de entrada, puede que los usuarios puedan colocar un [holograma](hologram.md) en la aplicación. El [plantilla de aplicación holográfica](creating-a-holographic-directx-project.md) tiene un ejemplo sencillo de usar.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="gaze-input"></a>Entrada de mirada

Para obtener acceso a los usuarios [mirada principal](gaze.md), usa el [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) tipo. La plantilla de aplicación holográfica incluye código básico para mirada de descripción. Este código proporciona un vector que señala hacia delante entre la vista del usuario, teniendo en cuenta posición del dispositivo y la orientación en un determinado [del sistema de coordenadas](coordinate-systems-in-directx.md).




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

Puede encontrar pregunta: "Pero donde el sistema de coordenadas proviene?"

Vamos a responder esa pregunta. En nuestro AppMain **actualización** función, se procesa un evento de entrada espacial mediante la adquisición en relación con el sistema de coordenadas para nuestro StationaryFrameOfReference. Recuerde que se creó el StationaryFrameOfReference cuando se configura el [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), y se ha adquirido el sistema de coordenadas del principio de [actualización](rendering-in-directx.md).




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

Tenga en cuenta que los datos está asociados a un estado de puntero de algún tipo. Esto se obtiene de un evento de entrada espacial. El objeto de datos del evento incluye un sistema de coordenadas, por lo que siempre se puede relacionar la dirección mirada en el momento del evento con cualquier sistema de coordenadas espacial necesita. De hecho, debe hacerlo con el fin de obtener la postura de puntero.

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="gesture-and-motion-controller-input"></a>Controlador de gestos y movimiento de entrada

En Windows Mixed Reality, tanto entregar [gestos](gestures.md) y [controladores de movimiento](motion-controllers.md) se controlan a través de la misma espacial entrada API, se encuentra en la [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) espacio de nombres. Esto le permite controlar fácilmente acciones comunes como **seleccione** presiona la misma manera a través de las manos y los controladores de movimiento.

Hay dos niveles de API que puede tener como destino al administrar los controladores de movimiento o de gestos en realidad mixta:
* [Interacciones](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) y [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), que se accede mediante un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [Los gestos compuestos](gestures.md#composite-gestures) ([pulsado](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), mantenga, manipulación, navegación), que se accede mediante un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>Interacciones de SELECT/menú/comprensión o panel táctil o tecla de navegación: SpatialInteractionManager

Para detectar las presiones de bajo nivel, versiones y actualizaciones a través de las manos y los dispositivos de entrada en Windows Mixed Reality, se inicia desde un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx). El SpatialInteractionManager tiene un evento que informa a la aplicación cuando una mano o el controlador de movimiento ha detectado la entrada.

Hay tres tipos de clave de SpatialInteractionSource, cada uno representado por un valor diferente de SpatialInteractionSourceKind:
* **Mano** representa mano detectadas de un usuario. Orígenes de mano sólo están disponibles en HoloLens.
* **Controlador** representa un controlador de movimiento emparejado. Los controladores de movimiento pueden ofrecer una variedad de capacidades, por ejemplo: Seleccione los desencadenadores, los botones de menú, botones de comprensión, touchpads y sticks analógicos.
* **Voz** representa la voz del usuario hablando palabras clave del sistema detectado. Esto inyectar un presione Select y de versión cada vez que el usuario dice "Select".

Para detectar pulsaciones a través de cualquiera de estos orígenes de interacción, puede controlar el evento SourcePressed en SpatialInteractionManager en SpatialInputHandler.cpp:


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

Este evento presionado se envía a la aplicación de forma asincrónica. La aplicación o el motor de juego que desee realizar el procesamiento inmediatamente o puede que desee poner en cola los datos del evento en su rutina de procesamiento de entrada.

La plantilla incluye una clase auxiliar para ayudarle a comenzar. Esta plantilla forgoes cualquier procesamiento por motivos de simplicidad del diseño. Realiza un seguimiento de la clase auxiliar si uno o más **Pressed** eventos se han producido desde la última **actualización** llamar. Desde SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

Si es así, devuelve el [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) para el evento de entrada más reciente durante la actualización siguiente. Desde SpatialInputHandler.cpp:




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

Tenga en cuenta que el código anterior tratará todos presiona del mismo modo, si el usuario está realizando un elemento principal **seleccione** presione o una base de datos secundaria **menú** o **sujete** presione. El **seleccione** press es una forma principal de interacción compatible entre manos, movimiento de los controladores y voz, activen mediante una mano realizar una derivación de aire, un controlador de movimiento con su desencadenador/botón primario presionado o el usuario voz diciendo "Select". Seleccionadas pulsaciones representan la intención del usuario para activar el holograma que como destino.

Para analizar qué tipo de prensa se está produciendo, modificaremos el controlador de eventos SpatialInteractionManager::SourceUpdated. Nuestro código detectará presiones de comprensión (si está disponible) y usarlos para volver a colocar el cubo. Si no está disponible la comprensión, usaremos pulsaciones seleccionadas en su lugar.

Agregue las siguientes declaraciones de miembro privado para SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Abra SpatialInputHandler.cpp. Agregar el registro de eventos siguiente al constructor: 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

Este es el código de controlador de eventos. Si el origen de entrada está experimentando una idea, se almacenará la postura de puntero para el bucle de actualización siguiente. En caso contrario, comprobará pulsación de una selección en su lugar. Desde SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

Asegúrese de que se va a anular el controlador de eventos en el destructor. Desde SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

Volver a compilar y, a continuación, volver a implementar. El proyecto de plantilla debería poder reconocer las interacciones de comprensión para volver a colocar el cubo girando.

La API SpatialInteractionSource es compatible con controladores con una amplia gama de capacidades. En el ejemplo mostrado anteriormente, comprobamos si se admite la comprensión antes de intentar utilizarlo. El SpatialInteractionSource admite las siguientes características opcionales más allá de los comunes **seleccione** presione:
* **Botón de menú:** Comprobar compatibilidad inspeccionando la propiedad IsMenuSupported. Cuando se admita, compruebe el [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propiedad para averiguar si el botón está presionada.
* **Sujete el botón:** Comprobar compatibilidad inspeccionando la propiedad IsGraspSupported. Cuando se admita, compruebe el [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propiedad para averiguar si se activa la comprensión.

Para los controladores, el SpatialInteractionSource tiene una propiedad de controlador con capacidades adicionales.
* **HasThumbstick:** Si es true, el controlador tiene una tecla de navegación. Inspeccionar el [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) propiedad de la SpatialInteractionSourceState para adquirir la tecla de navegación x y los valores y (ThumbstickX y ThumbstickY), así como su estado presionado (IsThumbstickPressed).
* **HasTouchpad:** Si es true, el controlador tiene un panel táctil. Inspeccionar la propiedad ControllerProperties de la SpatialInteractionSourceState para adquirir el panel táctil x e y valores (TouchpadX y TouchpadY) y para saber si el usuario toca la almohadilla (IsTouchpadTouched) y si presiona el panel táctil hacia abajo () IsTouchpadPressed).
* **SimpleHapticsController:** Para el controlador de la API de SimpleHapticsController le permite inspeccionar las capacidades de haptics del controlador, y también permite controlar comentarios hápticos.

Tenga en cuenta que el intervalo de pantalla táctil y la tecla de navegación de -1 a 1 para ambos ejes (de abajo a arriba y de izquierda a derecha). El intervalo para el desencadenador analógico, que se obtiene acceso mediante la propiedad SpatialInteractionSourceState::SelectPressedValue, tiene un intervalo de 0 a 1. Un valor de 1 se correlaciona con IsSelectPressed igual a true. cualquier otro valor se correlaciona con IsSelectPressed igual a false.

Tenga en cuenta que para una mano y un controlador, utilizando SpatialInteractionSourceState::Properties::TryGetLocation proporcionará la posición del usuario disponible, esto es distinto de la postura de puntero que representa a ray señalador del controlador. Si desea que se va a dibujar algo en la ubicación de la mano, utilice TryGetLocation. Si desea raycast desde la punta del controlador, obtenga señalador rayo de TryGetInteractionSourcePose en el SpatialPointerPose.

También puede usar los otros eventos en SpatialInteractionManager como SourceDetected y SourceLost, reaccionar cuando manos ENTRAR o salir de la vista del dispositivo o cuando mueve de dentro o fuera de la posición lista (dedo de índice se genera con palm hacia delante) o al movimiento controladores para activar o desactivar o están emparejados/no emparejados.

### <a name="grip-pose-vs-pointing-pose"></a>Postura de control frente a la postura señalador

Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma, con el diseño de cada controlador que se diferencia en su relación entre la posición del usuario mano y natural "Reenviar" dirección de que las aplicaciones debe utilizar para que apunte al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de plantea que puede investigar para cada origen de interacción:
* El **control postura**, que representa la ubicación de la palma de una mano detectada por un HoloLens, o bien la palma que contiene un controlador de movimiento.
    * En inmersivos, esta postura mejor se usa para representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo.
    * El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control.
    * El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)
    * El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.
    * El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.
    * Puede tener acceso a la postura de control a través de [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* El **puntero postura**, que representa la punta del controlador que señala hacia delante.
    * Esta postura está concebida para raycast cuando **apuntando a la interfaz de usuario** cuando está representando el propio modelo de controlador.
    * Puede tener acceso a la postura de puntero a través de [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

### <a name="composite-gestures-spatialgesturerecognizer"></a>Gestos compuestos: SpatialGestureRecognizer

Un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpreta las interacciones del usuario de las manos, controladores de movimiento y el comando de voz "Select" a los eventos de gestos espacial expuesta, qué destino de los usuarios mediante su mirada principal.

Gestos espaciales constituyen una clave de entrada para las aplicaciones de Windows Mixed Reality. Mediante el enrutamientos interacciones desde el SpatialInteractionManager a SpatialGestureRecognizer de un holograma, las aplicaciones pueden detectar eventos Tap, suspensión, manipulación y navegación uniformemente entre manos, voz y dispositivos de entrada espaciales, sin tener que controlar las pulsaciones y libera manualmente.

SpatialGestureRecognizer realiza solo la anulación de ambigüedades mínimo entre el conjunto de gestos que solicitan. Por ejemplo, si se solicita solo Tap, el usuario puede presionada su dedo como deseen y todavía se producirá una derivación. Si se solicita tanto pulsado, después de aproximadamente un segundo de mantener presionado su dedo, el gesto se promoverá a una suspensión y ya no se producirá un punteo.

Para usar SpatialGestureRecognizer, controlar el SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) agarre el SpatialPointerPose expuesto allí y eventos. Usar ray de mirada principal del usuario desde esta postura para formar una intersección con el hologramas y superficie mallas en el entorno del usuario, con el fin de determinar lo que va a interactuar con el usuario. A continuación, enrutar la SpatialInteraction en los argumentos de evento SpatialGestureRecognizer del holograma de destino, mediante su [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) método. Esto inicia la interpretación de esa interacción según la [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) establecer en ese módulo de reconocimiento, o en tiempo de creación - [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

En HoloLens, las interacciones y gestos generalmente deben derivar sus destinatarios de mirada principal del usuario, en lugar de intentar para representar o interactuar directamente en la ubicación de la mano. Una vez que se ha iniciado una interacción, los movimientos relativos de la mano pueden utilizarse para controlar el movimiento, al igual que con el gesto de manipulación o exploración.

## <a name="see-also"></a>Vea también
* [Gaze](gaze.md)
* [Gestos](gestures.md)
* [Controladores de movimiento](motion-controllers.md)
