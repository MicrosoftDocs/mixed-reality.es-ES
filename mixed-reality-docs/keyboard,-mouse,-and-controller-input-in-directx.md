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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="09c7f-104">Teclado, mouse y entrada del controlador de DirectX</span><span class="sxs-lookup"><span data-stu-id="09c7f-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="09c7f-105">Teclados, mouse y dispositivos de juego pueden ser útiles formularios de entrada para dispositivos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="09c7f-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="09c7f-106">Mouse y teclados de Bluetooth se admite en HoloLens, para su uso con la depuración de la aplicación o como una forma alternativa de entrada.</span><span class="sxs-lookup"><span data-stu-id="09c7f-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="09c7f-107">Windows Mixed Reality también admite inmersivos conectados a PC - donde los controladores de juego, teclados y ratones históricamente han sido la norma.</span><span class="sxs-lookup"><span data-stu-id="09c7f-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="09c7f-108">Usar entradas mediante teclado en HoloLens, par un teclado Bluetooth al dispositivo o entrada virtual a través de la Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="09c7f-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="09c7f-109">Para usar la entrada de teclado cuando se usan un auricular envolvente de Windows Mixed Reality, asigne foco de entrada a la realidad mixta colocar en el dispositivo o utilizando la tecla Windows + Y combinación de teclado.</span><span class="sxs-lookup"><span data-stu-id="09c7f-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="09c7f-110">Tenga en cuenta que las aplicaciones destinadas a HoloLens deben proporcionar una funcionalidad sin estos dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="09c7f-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="09c7f-111">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="09c7f-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="09c7f-112">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="09c7f-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="09c7f-113">Suscribirse a eventos de entrada de CoreWindow</span><span class="sxs-lookup"><span data-stu-id="09c7f-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="09c7f-114">Entrada de teclado</span><span class="sxs-lookup"><span data-stu-id="09c7f-114">Keyboard input</span></span>

<span data-ttu-id="09c7f-115">En la plantilla de aplicación de Windows Holographic, incluimos un controlador de eventos para la entrada de teclado al igual que cualquier otra aplicación UWP.</span><span class="sxs-lookup"><span data-stu-id="09c7f-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="09c7f-116">La aplicación consume datos de entrada de teclado de la misma manera en Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="09c7f-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="09c7f-117">Desde AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="09c7f-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="09c7f-118">Entradas mediante teclado virtual</span><span class="sxs-lookup"><span data-stu-id="09c7f-118">Virtual keyboard input</span></span>
<span data-ttu-id="09c7f-119">Para el escritorio inmersivos también pueden admitir teclados virtuales representados por Windows a través de la vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="09c7f-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="09c7f-120">Para admitir esto, puede implementar la aplicación **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="09c7f-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="09c7f-121">Esto permite que Windows comprender el estado de sus propios cuadros de texto de la aplicación representó, por lo que el teclado virtual correctamente puede contribuir en el texto no existe.</span><span class="sxs-lookup"><span data-stu-id="09c7f-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="09c7f-122">Para obtener más información sobre la implementación de soporte técnico de CoreTextEditContext, consulte el [CoreTextEditContext ejemplo](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="09c7f-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="09c7f-123">Entrada de mouse</span><span class="sxs-lookup"><span data-stu-id="09c7f-123">Mouse Input</span></span>

<span data-ttu-id="09c7f-124">También puede usar la entrada del mouse, nuevamente a través de los controladores de eventos de entrada de CoreWindow de UWP.</span><span class="sxs-lookup"><span data-stu-id="09c7f-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="09c7f-125">Aquí le explicamos cómo modificar la plantilla de aplicación de Windows Holographic para admitir los clics del mouse en los gestos mismos manera como presionados.</span><span class="sxs-lookup"><span data-stu-id="09c7f-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="09c7f-126">Después de realizar esta modificación, un clic del mouse mientras el exceso de un dispositivo de auriculares envolventes volverá a colocarse el cubo.</span><span class="sxs-lookup"><span data-stu-id="09c7f-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="09c7f-127">Tenga en cuenta que las aplicaciones para UWP también pueden obtener datos XY sin procesar para el mouse mediante el [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span><span class="sxs-lookup"><span data-stu-id="09c7f-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="09c7f-128">Comience por declarar un nuevo controlador OnPointerPressed en AppView.h:</span><span class="sxs-lookup"><span data-stu-id="09c7f-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="09c7f-129">En AppView.cpp, agregue este código al SetWindow:</span><span class="sxs-lookup"><span data-stu-id="09c7f-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="09c7f-130">A continuación, poner esta definición para OnPointerPressed en la parte inferior del archivo:</span><span class="sxs-lookup"><span data-stu-id="09c7f-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="09c7f-131">Acaba de agregar el controlador de eventos es un acceso directo a la clase de plantilla principal.</span><span class="sxs-lookup"><span data-stu-id="09c7f-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="09c7f-132">Vamos a modificar la clase principal para admitir este paso a través.</span><span class="sxs-lookup"><span data-stu-id="09c7f-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="09c7f-133">Agregue esta declaración de método público para el archivo de encabezado:</span><span class="sxs-lookup"><span data-stu-id="09c7f-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="09c7f-134">Necesitará esta variable de miembro privado:</span><span class="sxs-lookup"><span data-stu-id="09c7f-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="09c7f-135">Por último, la clase principal se actualizará con la nueva lógica para admitir los clics del mouse.</span><span class="sxs-lookup"><span data-stu-id="09c7f-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="09c7f-136">Empiece agregando este controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="09c7f-136">Start by adding this event handler.</span></span> <span data-ttu-id="09c7f-137">Asegúrese de actualizar el nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="09c7f-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="09c7f-138">Ahora, en el método de actualización, reemplace la lógica existente para obtener una postura de puntero con esto:</span><span class="sxs-lookup"><span data-stu-id="09c7f-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="09c7f-139">Vuelva a compilar y volver a implementar.</span><span class="sxs-lookup"><span data-stu-id="09c7f-139">Recompile and redeploy.</span></span> <span data-ttu-id="09c7f-140">Tenga en cuenta que el clic del mouse ahora volverá a colocarse el cubo en la envolvente auriculares - o HoloLens con el mouse bluetooth adjuntado.</span><span class="sxs-lookup"><span data-stu-id="09c7f-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="09c7f-141">Compatibilidad del dispositivo de juego</span><span class="sxs-lookup"><span data-stu-id="09c7f-141">Game controller support</span></span>

<span data-ttu-id="09c7f-142">Dispositivos de juego pueden ser una manera práctica y cómoda de permitir que al usuario para controlar una experiencia de Windows Mixed Reality envolvente.</span><span class="sxs-lookup"><span data-stu-id="09c7f-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="09c7f-143">Es el primer paso para agregar compatibilidad con dispositivos de juego en la plantilla de aplicación de Windows Holographic, agregue las siguientes declaraciones de miembro privado a la clase de encabezado para el archivo principal:</span><span class="sxs-lookup"><span data-stu-id="09c7f-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="09c7f-144">Inicializar los eventos de gamepad y cualquier configuración de los controles que está conectados actualmente, en el constructor para la clase principal:</span><span class="sxs-lookup"><span data-stu-id="09c7f-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="09c7f-145">Agregar estos controladores de eventos a la clase principal.</span><span class="sxs-lookup"><span data-stu-id="09c7f-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="09c7f-146">Asegúrese de actualizar el nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="09c7f-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="09c7f-147">Por último, actualice la lógica de entrada para que reconozca los cambios de estado del controlador.</span><span class="sxs-lookup"><span data-stu-id="09c7f-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="09c7f-148">En este caso, usamos la misma variable m_pointerPressed descrita en la sección anterior para agregar los eventos del mouse.</span><span class="sxs-lookup"><span data-stu-id="09c7f-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="09c7f-149">Agregue lo siguiente al método Update, justo antes de que busca el SpatialPointerPose:</span><span class="sxs-lookup"><span data-stu-id="09c7f-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="09c7f-150">No se olvide de anular el registro de los eventos al limpiar la clase principal:</span><span class="sxs-lookup"><span data-stu-id="09c7f-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="09c7f-151">Vuelva a compilar y volver a implementar.</span><span class="sxs-lookup"><span data-stu-id="09c7f-151">Recompile, and redeploy.</span></span> <span data-ttu-id="09c7f-152">Ahora puede adjuntar, o emparejar un dispositivo de juego y usarlo para volver a colocar el cubo girando.</span><span class="sxs-lookup"><span data-stu-id="09c7f-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="09c7f-153">Instrucciones importantes para el teclado y mouse de entrada</span><span class="sxs-lookup"><span data-stu-id="09c7f-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="09c7f-154">Hay algunas diferencias clave en cómo se puede usar este código en Microsoft HoloLens, que es un dispositivo que se basa principalmente en la entrada de usuario natural – frente a lo que está disponible en un PC con Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="09c7f-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="09c7f-155">No puede confiar en el teclado o mouse de entrada estén presentes.</span><span class="sxs-lookup"><span data-stu-id="09c7f-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="09c7f-156">Toda la funcionalidad de la aplicación debe trabajar con la mirada, gestos y entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="09c7f-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="09c7f-157">Cuando se adjunta un teclado Bluetooth, puede ser útil habilitar la entrada de teclado para cualquier texto que podría necesitar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="09c7f-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="09c7f-158">Esto puede ser un excelente complemento de dictado, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="09c7f-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="09c7f-159">En cuanto al diseño de la aplicación, no se basan en WASD (por ejemplo) y mouse busque los controles de su juego.</span><span class="sxs-lookup"><span data-stu-id="09c7f-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="09c7f-160">HoloLens está diseñado para que el usuario a caminar alrededor de la sala.</span><span class="sxs-lookup"><span data-stu-id="09c7f-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="09c7f-161">En este caso, el usuario controla la cámara directamente.</span><span class="sxs-lookup"><span data-stu-id="09c7f-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="09c7f-162">Una interfaz para impulsar la cámara en torno a la sala con controles de movimiento o buscar no proporciona la misma experiencia.</span><span class="sxs-lookup"><span data-stu-id="09c7f-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="09c7f-163">Entrada de teclado puede ser una manera excelente de controlar los aspectos de depuración de la aplicación o el motor de juego, sobre todo porque el usuario no tendrá que usar el teclado.</span><span class="sxs-lookup"><span data-stu-id="09c7f-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="09c7f-164">Transmitiendo es el mismo que el que está acostumbrado, con la API de eventos de CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="09c7f-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="09c7f-165">En este escenario, puede implementar una forma de configurar la aplicación para enrutar los eventos de teclado a un modo de "entrada sólo de debug" durante las sesiones de depuración.</span><span class="sxs-lookup"><span data-stu-id="09c7f-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="09c7f-166">Los controladores de Bluetooth también funcionan correctamente.</span><span class="sxs-lookup"><span data-stu-id="09c7f-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="09c7f-167">Vea también</span><span class="sxs-lookup"><span data-stu-id="09c7f-167">See also</span></span>
* [<span data-ttu-id="09c7f-168">Accesorios de hardware</span><span class="sxs-lookup"><span data-stu-id="09c7f-168">Hardware accessories</span></span>](hardware-accessories.md)
