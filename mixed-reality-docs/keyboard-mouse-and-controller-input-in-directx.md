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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="96c8e-104">Teclado, mouse y entrada del controlador en DirectX</span><span class="sxs-lookup"><span data-stu-id="96c8e-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="96c8e-105">Los teclados, los mouse y los controladores de juego pueden ser formas útiles de entrada para dispositivos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="96c8e-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="96c8e-106">Los teclados y ratones Bluetooth se admiten en HoloLens, para su uso con la depuración de la aplicación o como una forma alternativa de entrada.</span><span class="sxs-lookup"><span data-stu-id="96c8e-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="96c8e-107">Windows Mixed Reality también admite auriculares envolventes conectados a equipos, donde los ratones, los teclados y los controladores de juegos han sido históricamente la norma.</span><span class="sxs-lookup"><span data-stu-id="96c8e-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="96c8e-108">Para usar la entrada del teclado en HoloLens, empareje un teclado Bluetooth a su dispositivo o use la entrada virtual a través del portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="96c8e-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="96c8e-109">Para usar la entrada del teclado al mismo tiempo que usa un auricular envolvente de realidad mixta de Windows, asigne el foco de entrada a la realidad mixta colocando en el dispositivo o mediante la combinación de teclas de Windows + Y.</span><span class="sxs-lookup"><span data-stu-id="96c8e-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="96c8e-110">Tenga en cuenta que las aplicaciones destinadas a HoloLens deben proporcionar funcionalidad sin estos dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="96c8e-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="96c8e-111">Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="96c8e-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="96c8e-112">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="96c8e-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="96c8e-113">Suscribirse a eventos de entrada de CoreWindow</span><span class="sxs-lookup"><span data-stu-id="96c8e-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="96c8e-114">Entrada de teclado</span><span class="sxs-lookup"><span data-stu-id="96c8e-114">Keyboard input</span></span>

<span data-ttu-id="96c8e-115">En la plantilla de aplicación de Windows Holographic, se incluye un controlador de eventos para la entrada de teclado como cualquier otra aplicación de UWP.</span><span class="sxs-lookup"><span data-stu-id="96c8e-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="96c8e-116">La aplicación consume los datos de entrada del teclado de la misma forma en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="96c8e-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="96c8e-117">Desde AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="96c8e-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="96c8e-118">Entrada de teclado virtual</span><span class="sxs-lookup"><span data-stu-id="96c8e-118">Virtual keyboard input</span></span>
<span data-ttu-id="96c8e-119">En el caso de los auriculares de escritorio envolventes, también puede admitir Teclados virtuales representados por Windows sobre la vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="96c8e-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="96c8e-120">Para admitir esto, la aplicación puede implementar **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="96c8e-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="96c8e-121">Esto permite a Windows comprender el estado de sus propios cuadros de texto presentados por la aplicación, por lo que el teclado virtual puede contribuir correctamente al texto.</span><span class="sxs-lookup"><span data-stu-id="96c8e-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="96c8e-122">Para obtener más información sobre cómo implementar la compatibilidad con CoreTextEditContext, vea el [ejemplo CoreTextEditContext](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="96c8e-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="96c8e-123">Entrada del mouse</span><span class="sxs-lookup"><span data-stu-id="96c8e-123">Mouse Input</span></span>

<span data-ttu-id="96c8e-124">También puede usar la entrada del mouse de nuevo a través de los controladores de eventos de entrada de CoreWindow de UWP.</span><span class="sxs-lookup"><span data-stu-id="96c8e-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="96c8e-125">Aquí se muestra cómo modificar la plantilla de la aplicación holográfica de Windows para admitir los clics del mouse de la misma manera que los gestos presionados.</span><span class="sxs-lookup"><span data-stu-id="96c8e-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="96c8e-126">Después de realizar esta modificación, al hacer clic con el mouse mientras se contenía un dispositivo con auriculares envolvente, cambiará la posición del cubo.</span><span class="sxs-lookup"><span data-stu-id="96c8e-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="96c8e-127">Tenga en cuenta que las aplicaciones UWP también pueden obtener datos XY sin formato para el mouse mediante la API de [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) .</span><span class="sxs-lookup"><span data-stu-id="96c8e-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="96c8e-128">Empiece por declarar un nuevo controlador OnPointerPressed en AppView. h:</span><span class="sxs-lookup"><span data-stu-id="96c8e-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="96c8e-129">En AppView. cpp, agregue este código a SetWindow:</span><span class="sxs-lookup"><span data-stu-id="96c8e-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="96c8e-130">Después, coloque esta definición para OnPointerPressed en la parte inferior del archivo:</span><span class="sxs-lookup"><span data-stu-id="96c8e-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="96c8e-131">El controlador de eventos que acabamos de agregar es un paso a través de la clase principal de la plantilla.</span><span class="sxs-lookup"><span data-stu-id="96c8e-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="96c8e-132">Vamos a modificar la clase principal para que admita este paso.</span><span class="sxs-lookup"><span data-stu-id="96c8e-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="96c8e-133">Agregue esta declaración de método público al archivo de encabezado:</span><span class="sxs-lookup"><span data-stu-id="96c8e-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="96c8e-134">Necesitará esta variable miembro privada también:</span><span class="sxs-lookup"><span data-stu-id="96c8e-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="96c8e-135">Por último, actualizaremos la clase principal con una nueva lógica para admitir los clics del mouse.</span><span class="sxs-lookup"><span data-stu-id="96c8e-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="96c8e-136">Empiece por agregar este controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="96c8e-136">Start by adding this event handler.</span></span> <span data-ttu-id="96c8e-137">Asegúrese de actualizar el nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="96c8e-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="96c8e-138">Ahora, en el método de actualización, reemplace la lógica existente para obtener una repose de puntero con este:</span><span class="sxs-lookup"><span data-stu-id="96c8e-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="96c8e-139">Vuelva a compilar e implementar.</span><span class="sxs-lookup"><span data-stu-id="96c8e-139">Recompile and redeploy.</span></span> <span data-ttu-id="96c8e-140">Tenga en cuenta que, al hacer clic con el mouse, se volverá a colocar el cubo en el casco envolvente, o HoloLens, con el mouse Bluetooth conectado.</span><span class="sxs-lookup"><span data-stu-id="96c8e-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="96c8e-141">Compatibilidad con el dispositivo de juego</span><span class="sxs-lookup"><span data-stu-id="96c8e-141">Game controller support</span></span>

<span data-ttu-id="96c8e-142">Los dispositivos de juego pueden ser una forma divertida y cómoda de permitir al usuario controlar una experiencia de Windows Mixed Reality más envolvente.</span><span class="sxs-lookup"><span data-stu-id="96c8e-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="96c8e-143">El primer paso para agregar compatibilidad con dispositivos de juego a la plantilla de aplicación de Windows Holographic es agregar las siguientes declaraciones de miembro privado a la clase de encabezado para el archivo principal:</span><span class="sxs-lookup"><span data-stu-id="96c8e-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="96c8e-144">Inicialice los eventos del controlador de juegos y los controladores de juegos que estén conectados actualmente en el constructor de la clase principal:</span><span class="sxs-lookup"><span data-stu-id="96c8e-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="96c8e-145">Agregue estos controladores de eventos a la clase principal.</span><span class="sxs-lookup"><span data-stu-id="96c8e-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="96c8e-146">Asegúrese de actualizar el nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="96c8e-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="96c8e-147">Por último, actualice la lógica de entrada para que reconozca los cambios en el estado del controlador.</span><span class="sxs-lookup"><span data-stu-id="96c8e-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="96c8e-148">Aquí, usamos la misma variable m_pointerPressed descrita en la sección anterior para agregar eventos del mouse.</span><span class="sxs-lookup"><span data-stu-id="96c8e-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="96c8e-149">Agregue esto al método Update, justo antes de donde comprueba el SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="96c8e-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="96c8e-150">No olvide anular el registro de los eventos al limpiar la clase principal:</span><span class="sxs-lookup"><span data-stu-id="96c8e-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="96c8e-151">Vuelva a compilar e implementar.</span><span class="sxs-lookup"><span data-stu-id="96c8e-151">Recompile, and redeploy.</span></span> <span data-ttu-id="96c8e-152">Ahora puede adjuntar, o emparejar, un dispositivo de juego y usarlo para cambiar la posición del cubo giratorio.</span><span class="sxs-lookup"><span data-stu-id="96c8e-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="96c8e-153">Directrices importantes para la entrada de teclado y del mouse</span><span class="sxs-lookup"><span data-stu-id="96c8e-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="96c8e-154">Hay algunas diferencias importantes en el modo en que este código se puede usar en Microsoft HoloLens, que es un dispositivo que se basa principalmente en la entrada natural del usuario, frente a lo que está disponible en un equipo con Windows Mixed Reality habilitado.</span><span class="sxs-lookup"><span data-stu-id="96c8e-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="96c8e-155">No se puede confiar en que la entrada del mouse o del teclado esté presente.</span><span class="sxs-lookup"><span data-stu-id="96c8e-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="96c8e-156">Toda la funcionalidad de la aplicación debe funcionar con la mirada, el gesto y la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="96c8e-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="96c8e-157">Cuando se adjunta un teclado Bluetooth, puede resultar útil habilitar la entrada del teclado para cualquier texto que la aplicación pueda solicitar.</span><span class="sxs-lookup"><span data-stu-id="96c8e-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="96c8e-158">Este puede ser un complemento excelente para el dictado, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="96c8e-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="96c8e-159">En lo que respecta al diseño de la aplicación, no confíe en los controles WASD y de apariencia del mouse para el juego.</span><span class="sxs-lookup"><span data-stu-id="96c8e-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="96c8e-160">HoloLens está diseñado para que el usuario pueda desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="96c8e-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="96c8e-161">En este caso, el usuario controla la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="96c8e-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="96c8e-162">Una interfaz para impulsar la cámara en torno a la habitación con controles de movimiento y apariencia no proporciona la misma experiencia.</span><span class="sxs-lookup"><span data-stu-id="96c8e-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="96c8e-163">La entrada mediante teclado puede ser una manera excelente de controlar los aspectos de depuración de la aplicación o el motor de juegos, sobre todo porque el usuario no tendrá que usar el teclado.</span><span class="sxs-lookup"><span data-stu-id="96c8e-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="96c8e-164">El cableado es el mismo que se usa con las API de eventos de CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="96c8e-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="96c8e-165">En este escenario, puede optar por implementar una manera de configurar la aplicación para que enrute los eventos de teclado a un modo de "depuración de solo entrada" durante las sesiones de depuración.</span><span class="sxs-lookup"><span data-stu-id="96c8e-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="96c8e-166">Los controladores Bluetooth también funcionan.</span><span class="sxs-lookup"><span data-stu-id="96c8e-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="96c8e-167">Vea también</span><span class="sxs-lookup"><span data-stu-id="96c8e-167">See also</span></span>
* [<span data-ttu-id="96c8e-168">Accesorios de hardware</span><span class="sxs-lookup"><span data-stu-id="96c8e-168">Hardware accessories</span></span>](hardware-accessories.md)
