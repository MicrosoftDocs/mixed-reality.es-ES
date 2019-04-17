---
title: Teclado, mouse y entrada del controlador de DirectX
description: Explica cómo crear una aplicación para Windows Mixed Reality que usa dispositivos de juego, mouse y teclado.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, teclado, mouse, dispositivo de juego, mando de xbox, HoloLens, escritorio, el tutorial, el código de ejemplo
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605781"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Teclado, mouse y entrada del controlador de DirectX

Teclados, mouse y dispositivos de juego pueden ser útiles formularios de entrada para dispositivos Windows Mixed Reality. Mouse y teclados de Bluetooth se admite en HoloLens, para su uso con la depuración de la aplicación o como una forma alternativa de entrada. Windows Mixed Reality también admite inmersivos conectados a PC - donde los controladores de juego, teclados y ratones históricamente han sido la norma.

Usar entradas mediante teclado en HoloLens, par un teclado Bluetooth al dispositivo o entrada virtual a través de la Windows Device Portal. Para usar la entrada de teclado cuando se usan un auricular envolvente de Windows Mixed Reality, asigne foco de entrada a la realidad mixta colocar en el dispositivo o utilizando la tecla Windows + Y combinación de teclado. Tenga en cuenta que las aplicaciones destinadas a HoloLens deben proporcionar una funcionalidad sin estos dispositivos conectados.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="subscribe-for-corewindow-input-events"></a>Suscribirse a eventos de entrada de CoreWindow

### <a name="keyboard-input"></a>Entrada de teclado

En la plantilla de aplicación de Windows Holographic, incluimos un controlador de eventos para la entrada de teclado al igual que cualquier otra aplicación UWP. La aplicación consume datos de entrada de teclado de la misma manera en Windows Mixed Reality.

Desde AppView.cpp:

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

### <a name="virtual-keyboard-input"></a>Entradas mediante teclado virtual
Para el escritorio inmersivos también pueden admitir teclados virtuales representados por Windows a través de la vista envolvente. Para admitir esto, puede implementar la aplicación **CoreTextEditContext**. Esto permite que Windows comprender el estado de sus propios cuadros de texto de la aplicación representó, por lo que el teclado virtual correctamente puede contribuir en el texto no existe.

Para obtener más información sobre la implementación de soporte técnico de CoreTextEditContext, consulte el [CoreTextEditContext ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Entrada de mouse

También puede usar la entrada del mouse, nuevamente a través de los controladores de eventos de entrada de CoreWindow de UWP. Aquí le explicamos cómo modificar la plantilla de aplicación de Windows Holographic para admitir los clics del mouse en los gestos mismos manera como presionados. Después de realizar esta modificación, un clic del mouse mientras el exceso de un dispositivo de auriculares envolventes volverá a colocarse el cubo.

Tenga en cuenta que las aplicaciones para UWP también pueden obtener datos XY sin procesar para el mouse mediante el [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.

Comience por declarar un nuevo controlador OnPointerPressed en AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

En AppView.cpp, agregue este código al SetWindow:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

A continuación, poner esta definición para OnPointerPressed en la parte inferior del archivo:

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

Acaba de agregar el controlador de eventos es un acceso directo a la clase de plantilla principal. Vamos a modificar la clase principal para admitir este paso a través. Agregue esta declaración de método público para el archivo de encabezado:

```
// Handle mouse input.
       void OnPointerPressed();
```

Necesitará esta variable de miembro privado:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Por último, la clase principal se actualizará con la nueva lógica para admitir los clics del mouse. Empiece agregando este controlador de eventos. Asegúrese de actualizar el nombre de clase:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ahora, en el método de actualización, reemplace la lógica existente para obtener una postura de puntero con esto:

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

Vuelva a compilar y volver a implementar. Tenga en cuenta que el clic del mouse ahora volverá a colocarse el cubo en la envolvente auriculares - o HoloLens con el mouse bluetooth adjuntado.

### <a name="game-controller-support"></a>Compatibilidad del dispositivo de juego

Dispositivos de juego pueden ser una manera práctica y cómoda de permitir que al usuario para controlar una experiencia de Windows Mixed Reality envolvente.

Es el primer paso para agregar compatibilidad con dispositivos de juego en la plantilla de aplicación de Windows Holographic, agregue las siguientes declaraciones de miembro privado a la clase de encabezado para el archivo principal:

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

Inicializar los eventos de gamepad y cualquier configuración de los controles que está conectados actualmente, en el constructor para la clase principal:

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

Agregar estos controladores de eventos a la clase principal. Asegúrese de actualizar el nombre de clase:

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

Por último, actualice la lógica de entrada para que reconozca los cambios de estado del controlador. En este caso, usamos la misma variable m_pointerPressed descrita en la sección anterior para agregar los eventos del mouse. Agregue lo siguiente al método Update, justo antes de que busca el SpatialPointerPose:

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

No se olvide de anular el registro de los eventos al limpiar la clase principal:

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

Vuelva a compilar y volver a implementar. Ahora puede adjuntar, o emparejar un dispositivo de juego y usarlo para volver a colocar el cubo girando.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Instrucciones importantes para el teclado y mouse de entrada

Hay algunas diferencias clave en cómo se puede usar este código en Microsoft HoloLens, que es un dispositivo que se basa principalmente en la entrada de usuario natural – frente a lo que está disponible en un PC con Windows Mixed Reality.
* No puede confiar en el teclado o mouse de entrada estén presentes. Toda la funcionalidad de la aplicación debe trabajar con la mirada, gestos y entrada de voz.
* Cuando se adjunta un teclado Bluetooth, puede ser útil habilitar la entrada de teclado para cualquier texto que podría necesitar la aplicación. Esto puede ser un excelente complemento de dictado, por ejemplo.
* En cuanto al diseño de la aplicación, no se basan en WASD (por ejemplo) y mouse busque los controles de su juego. HoloLens está diseñado para que el usuario a caminar alrededor de la sala. En este caso, el usuario controla la cámara directamente. Una interfaz para impulsar la cámara en torno a la sala con controles de movimiento o buscar no proporciona la misma experiencia.
* Entrada de teclado puede ser una manera excelente de controlar los aspectos de depuración de la aplicación o el motor de juego, sobre todo porque el usuario no tendrá que usar el teclado. Transmitiendo es el mismo que el que está acostumbrado, con la API de eventos de CoreWindow. En este escenario, puede implementar una forma de configurar la aplicación para enrutar los eventos de teclado a un modo de "entrada sólo de debug" durante las sesiones de depuración.
* Los controladores de Bluetooth también funcionan correctamente.

## <a name="see-also"></a>Vea también
* [Accesorios de hardware](hardware-accessories.md)
