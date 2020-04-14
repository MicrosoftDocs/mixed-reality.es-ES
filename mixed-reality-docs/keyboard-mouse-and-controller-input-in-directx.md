---
title: Teclado, mouse y entrada del controlador en DirectX
description: Explica cómo crear una aplicación para Windows Mixed Reality que usa el teclado, el mouse y los controladores de juegos.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, teclado, Mouse, dispositivo de juego, controladora Xbox, HoloLens, escritorio, tutorial, código de ejemplo
ms.openlocfilehash: 27f1bf72435ce6889ba3f7b83664367a4440b162
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278093"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Teclado, mouse y entrada del controlador en DirectX

Los teclados, los mouse y los controladores de juego pueden ser formas útiles de entrada para dispositivos Windows Mixed Reality. Los teclados y ratones Bluetooth se admiten en HoloLens, para su uso con la depuración de la aplicación o como una forma alternativa de entrada. Windows Mixed Reality también admite auriculares envolventes conectados a equipos, donde los ratones, los teclados y los controladores de juegos han sido históricamente la norma.

Para usar la entrada del teclado en HoloLens, empareje un teclado Bluetooth a su dispositivo o use la entrada virtual a través del portal de dispositivos de Windows. Para usar la entrada del teclado al mismo tiempo que usa un auricular envolvente de realidad mixta de Windows, asigne el foco de entrada a la realidad mixta colocando en el dispositivo o mediante la combinación de teclas de Windows + Y. Tenga en cuenta que las aplicaciones destinadas a HoloLens deben proporcionar funcionalidad sin estos dispositivos conectados.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.

## <a name="subscribe-for-corewindow-input-events"></a>Suscribirse a eventos de entrada de CoreWindow

### <a name="keyboard-input"></a>Entrada de teclado

En la plantilla de aplicación de Windows Holographic, se incluye un controlador de eventos para la entrada de teclado como cualquier otra aplicación de UWP. La aplicación consume los datos de entrada del teclado de la misma forma en Windows Mixed Reality.

Desde AppView. cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Entrada de teclado virtual
En el caso de los auriculares de escritorio envolventes, también puede admitir Teclados virtuales representados por Windows sobre la vista envolvente. Para admitir esto, la aplicación puede implementar **CoreTextEditContext**. Esto permite a Windows comprender el estado de sus propios cuadros de texto presentados por la aplicación, por lo que el teclado virtual puede contribuir correctamente al texto.

Para obtener más información sobre cómo implementar la compatibilidad con CoreTextEditContext, vea el [ejemplo CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Entrada del mouse

También puede usar la entrada del mouse de nuevo a través de los controladores de eventos de entrada de CoreWindow de UWP. Aquí se muestra cómo modificar la plantilla de la aplicación holográfica de Windows para admitir los clics del mouse de la misma manera que los gestos presionados. Después de realizar esta modificación, al hacer clic con el mouse mientras se contenía un dispositivo con auriculares envolvente, cambiará la posición del cubo.

Tenga en cuenta que las aplicaciones UWP también pueden obtener datos XY sin formato para el mouse mediante la API de [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .

Empiece por declarar un nuevo controlador OnPointerPressed en AppView. h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

En AppView. cpp, agregue este código a SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Después, coloque esta definición para OnPointerPressed en la parte inferior del archivo:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

El controlador de eventos que acabamos de agregar es un paso a través de la clase principal de la plantilla. Vamos a modificar la clase principal para que admita este paso. Agregue esta declaración de método público al archivo de encabezado:

```
// Handle mouse input.
       void OnPointerPressed();
```

Necesitará esta variable miembro privada también:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Por último, actualizaremos la clase principal con una nueva lógica para admitir los clics del mouse. Empiece por agregar este controlador de eventos. Asegúrese de actualizar el nombre de clase:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ahora, en el método de actualización, reemplace la lógica existente para obtener una repose de puntero con este:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Vuelva a compilar e implementar. Tenga en cuenta que, al hacer clic con el mouse, se volverá a colocar el cubo en el casco envolvente, o HoloLens, con el mouse Bluetooth conectado.

### <a name="game-controller-support"></a>Compatibilidad con el dispositivo de juego

Los dispositivos de juego pueden ser una forma divertida y cómoda de permitir al usuario controlar una experiencia de Windows Mixed Reality más envolvente.

El primer paso para agregar compatibilidad con dispositivos de juego a la plantilla de aplicación de Windows Holographic es agregar las siguientes declaraciones de miembro privado a la clase de encabezado para el archivo principal:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Inicialice los eventos del controlador de juegos y los controladores de juegos que estén conectados actualmente en el constructor de la clase principal:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Agregue estos controladores de eventos a la clase principal. Asegúrese de actualizar el nombre de clase:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Por último, actualice la lógica de entrada para que reconozca los cambios en el estado del controlador. Aquí, usamos la misma variable m_pointerPressed descrita en la sección anterior para agregar eventos del mouse. Agregue esto al método Update, justo antes de donde comprueba el SpatialPointerPose:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

No olvide anular el registro de los eventos al limpiar la clase principal:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Vuelva a compilar e implementar. Ahora puede adjuntar, o emparejar, un dispositivo de juego y usarlo para cambiar la posición del cubo giratorio.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Directrices importantes para la entrada de teclado y del mouse

Hay algunas diferencias importantes en el modo en que este código se puede usar en Microsoft HoloLens, que es un dispositivo que se basa principalmente en la entrada natural del usuario, frente a lo que está disponible en un equipo con Windows Mixed Reality habilitado.
* No se puede confiar en que la entrada del mouse o del teclado esté presente. Toda la funcionalidad de la aplicación debe funcionar con la mirada, el gesto y la entrada de voz.
* Cuando se adjunta un teclado Bluetooth, puede resultar útil habilitar la entrada del teclado para cualquier texto que la aplicación pueda solicitar. Este puede ser un complemento excelente para el dictado, por ejemplo.
* En lo que respecta al diseño de la aplicación, no confíe en los controles WASD y de apariencia del mouse para el juego. HoloLens está diseñado para que el usuario pueda desplazarse por la habitación. En este caso, el usuario controla la cámara directamente. Una interfaz para impulsar la cámara en torno a la habitación con controles de movimiento y apariencia no proporciona la misma experiencia.
* La entrada mediante teclado puede ser una manera excelente de controlar los aspectos de depuración de la aplicación o el motor de juegos, sobre todo porque el usuario no tendrá que usar el teclado. El cableado es el mismo que se usa con las API de eventos de CoreWindow. En este escenario, puede optar por implementar una manera de configurar la aplicación para que enrute los eventos de teclado a un modo de "depuración de solo entrada" durante las sesiones de depuración.
* Los controladores Bluetooth también funcionan.

## <a name="see-also"></a>Vea también
* [Accesorios de hardware](hardware-accessories.md)
