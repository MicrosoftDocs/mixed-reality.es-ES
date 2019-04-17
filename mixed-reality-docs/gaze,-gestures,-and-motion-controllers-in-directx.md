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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="7a5c2-104">Mirada, gestos y controladores de movimiento de DirectX</span><span class="sxs-lookup"><span data-stu-id="7a5c2-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="7a5c2-105">Si va a compilar directamente en la parte superior de la plataforma, tendrá que controlar la entrada procedente del usuario - como donde el usuario examina a través de [mirada principal](gaze.md) y el usuario que ha seleccionado con [gestos](gestures.md) o [motion controladores](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="7a5c2-106">Combinación de estas formas de entrada, puede que los usuarios puedan colocar un [holograma](hologram.md) en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="7a5c2-107">El [plantilla de aplicación holográfica](creating-a-holographic-directx-project.md) tiene un ejemplo sencillo de usar.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="7a5c2-108">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7a5c2-109">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="7a5c2-110">Entrada de mirada</span><span class="sxs-lookup"><span data-stu-id="7a5c2-110">Gaze input</span></span>

<span data-ttu-id="7a5c2-111">Para obtener acceso a los usuarios [mirada principal](gaze.md), usa el [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) tipo.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="7a5c2-112">La plantilla de aplicación holográfica incluye código básico para mirada de descripción.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="7a5c2-113">Este código proporciona un vector que señala hacia delante entre la vista del usuario, teniendo en cuenta posición del dispositivo y la orientación en un determinado [del sistema de coordenadas](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




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

<span data-ttu-id="7a5c2-114">Puede encontrar pregunta: "Pero donde el sistema de coordenadas proviene?"</span><span class="sxs-lookup"><span data-stu-id="7a5c2-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="7a5c2-115">Vamos a responder esa pregunta.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-115">Let's answer that question.</span></span> <span data-ttu-id="7a5c2-116">En nuestro AppMain **actualización** función, se procesa un evento de entrada espacial mediante la adquisición en relación con el sistema de coordenadas para nuestro StationaryFrameOfReference.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="7a5c2-117">Recuerde que se creó el StationaryFrameOfReference cuando se configura el [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), y se ha adquirido el sistema de coordenadas del principio de [actualización](rendering-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




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

<span data-ttu-id="7a5c2-118">Tenga en cuenta que los datos está asociados a un estado de puntero de algún tipo.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="7a5c2-119">Esto se obtiene de un evento de entrada espacial.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-119">We get this from a spatial input event.</span></span> <span data-ttu-id="7a5c2-120">El objeto de datos del evento incluye un sistema de coordenadas, por lo que siempre se puede relacionar la dirección mirada en el momento del evento con cualquier sistema de coordenadas espacial necesita.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="7a5c2-121">De hecho, debe hacerlo con el fin de obtener la postura de puntero.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="7a5c2-122">Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="7a5c2-123">Controlador de gestos y movimiento de entrada</span><span class="sxs-lookup"><span data-stu-id="7a5c2-123">Gesture and motion controller input</span></span>

<span data-ttu-id="7a5c2-124">En Windows Mixed Reality, tanto entregar [gestos](gestures.md) y [controladores de movimiento](motion-controllers.md) se controlan a través de la misma espacial entrada API, se encuentra en la [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) espacio de nombres.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="7a5c2-125">Esto le permite controlar fácilmente acciones comunes como **seleccione** presiona la misma manera a través de las manos y los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="7a5c2-126">Hay dos niveles de API que puede tener como destino al administrar los controladores de movimiento o de gestos en realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="7a5c2-127">[Interacciones](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) y [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), que se accede mediante un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="7a5c2-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="7a5c2-128">[Los gestos compuestos](gestures.md#composite-gestures) ([pulsado](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), mantenga, manipulación, navegación), que se accede mediante un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="7a5c2-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="7a5c2-129">Interacciones de SELECT/menú/comprensión o panel táctil o tecla de navegación: SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="7a5c2-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="7a5c2-130">Para detectar las presiones de bajo nivel, versiones y actualizaciones a través de las manos y los dispositivos de entrada en Windows Mixed Reality, se inicia desde un [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="7a5c2-131">El SpatialInteractionManager tiene un evento que informa a la aplicación cuando una mano o el controlador de movimiento ha detectado la entrada.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="7a5c2-132">Hay tres tipos de clave de SpatialInteractionSource, cada uno representado por un valor diferente de SpatialInteractionSourceKind:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="7a5c2-133">**Mano** representa mano detectadas de un usuario.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="7a5c2-134">Orígenes de mano sólo están disponibles en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="7a5c2-135">**Controlador** representa un controlador de movimiento emparejado.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="7a5c2-136">Los controladores de movimiento pueden ofrecer una variedad de capacidades, por ejemplo: Seleccione los desencadenadores, los botones de menú, botones de comprensión, touchpads y sticks analógicos.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="7a5c2-137">**Voz** representa la voz del usuario hablando palabras clave del sistema detectado.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="7a5c2-138">Esto inyectar un presione Select y de versión cada vez que el usuario dice "Select".</span><span class="sxs-lookup"><span data-stu-id="7a5c2-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="7a5c2-139">Para detectar pulsaciones a través de cualquiera de estos orígenes de interacción, puede controlar el evento SourcePressed en SpatialInteractionManager en SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="7a5c2-140">Este evento presionado se envía a la aplicación de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="7a5c2-141">La aplicación o el motor de juego que desee realizar el procesamiento inmediatamente o puede que desee poner en cola los datos del evento en su rutina de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="7a5c2-142">La plantilla incluye una clase auxiliar para ayudarle a comenzar.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="7a5c2-143">Esta plantilla forgoes cualquier procesamiento por motivos de simplicidad del diseño.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="7a5c2-144">Realiza un seguimiento de la clase auxiliar si uno o más **Pressed** eventos se han producido desde la última **actualización** llamar.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="7a5c2-145">Desde SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-145">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="7a5c2-146">Si es así, devuelve el [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) para el evento de entrada más reciente durante la actualización siguiente.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="7a5c2-147">Desde SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-147">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="7a5c2-148">Tenga en cuenta que el código anterior tratará todos presiona del mismo modo, si el usuario está realizando un elemento principal **seleccione** presione o una base de datos secundaria **menú** o **sujete** presione.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="7a5c2-149">El **seleccione** press es una forma principal de interacción compatible entre manos, movimiento de los controladores y voz, activen mediante una mano realizar una derivación de aire, un controlador de movimiento con su desencadenador/botón primario presionado o el usuario voz diciendo "Select".</span><span class="sxs-lookup"><span data-stu-id="7a5c2-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="7a5c2-150">Seleccionadas pulsaciones representan la intención del usuario para activar el holograma que como destino.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="7a5c2-151">Para analizar qué tipo de prensa se está produciendo, modificaremos el controlador de eventos SpatialInteractionManager::SourceUpdated.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="7a5c2-152">Nuestro código detectará presiones de comprensión (si está disponible) y usarlos para volver a colocar el cubo.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="7a5c2-153">Si no está disponible la comprensión, usaremos pulsaciones seleccionadas en su lugar.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="7a5c2-154">Agregue las siguientes declaraciones de miembro privado para SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="7a5c2-155">Abra SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="7a5c2-156">Agregar el registro de eventos siguiente al constructor:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="7a5c2-157">Este es el código de controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-157">This is the event handler code.</span></span> <span data-ttu-id="7a5c2-158">Si el origen de entrada está experimentando una idea, se almacenará la postura de puntero para el bucle de actualización siguiente.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="7a5c2-159">En caso contrario, comprobará pulsación de una selección en su lugar.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="7a5c2-160">Desde SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-160">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="7a5c2-161">Asegúrese de que se va a anular el controlador de eventos en el destructor.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="7a5c2-162">Desde SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="7a5c2-163">Volver a compilar y, a continuación, volver a implementar.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="7a5c2-164">El proyecto de plantilla debería poder reconocer las interacciones de comprensión para volver a colocar el cubo girando.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="7a5c2-165">La API SpatialInteractionSource es compatible con controladores con una amplia gama de capacidades.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="7a5c2-166">En el ejemplo mostrado anteriormente, comprobamos si se admite la comprensión antes de intentar utilizarlo.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="7a5c2-167">El SpatialInteractionSource admite las siguientes características opcionales más allá de los comunes **seleccione** presione:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="7a5c2-168">**Botón de menú:** Comprobar compatibilidad inspeccionando la propiedad IsMenuSupported.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="7a5c2-169">Cuando se admita, compruebe el [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propiedad para averiguar si el botón está presionada.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="7a5c2-170">**Sujete el botón:** Comprobar compatibilidad inspeccionando la propiedad IsGraspSupported.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="7a5c2-171">Cuando se admita, compruebe el [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) propiedad para averiguar si se activa la comprensión.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="7a5c2-172">Para los controladores, el SpatialInteractionSource tiene una propiedad de controlador con capacidades adicionales.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="7a5c2-173">**HasThumbstick:** Si es true, el controlador tiene una tecla de navegación.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="7a5c2-174">Inspeccionar el [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) propiedad de la SpatialInteractionSourceState para adquirir la tecla de navegación x y los valores y (ThumbstickX y ThumbstickY), así como su estado presionado (IsThumbstickPressed).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="7a5c2-175">**HasTouchpad:** Si es true, el controlador tiene un panel táctil.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="7a5c2-176">Inspeccionar la propiedad ControllerProperties de la SpatialInteractionSourceState para adquirir el panel táctil x e y valores (TouchpadX y TouchpadY) y para saber si el usuario toca la almohadilla (IsTouchpadTouched) y si presiona el panel táctil hacia abajo () IsTouchpadPressed).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="7a5c2-177">**SimpleHapticsController:** Para el controlador de la API de SimpleHapticsController le permite inspeccionar las capacidades de haptics del controlador, y también permite controlar comentarios hápticos.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="7a5c2-178">Tenga en cuenta que el intervalo de pantalla táctil y la tecla de navegación de -1 a 1 para ambos ejes (de abajo a arriba y de izquierda a derecha).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="7a5c2-179">El intervalo para el desencadenador analógico, que se obtiene acceso mediante la propiedad SpatialInteractionSourceState::SelectPressedValue, tiene un intervalo de 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="7a5c2-180">Un valor de 1 se correlaciona con IsSelectPressed igual a true. cualquier otro valor se correlaciona con IsSelectPressed igual a false.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="7a5c2-181">Tenga en cuenta que para una mano y un controlador, utilizando SpatialInteractionSourceState::Properties::TryGetLocation proporcionará la posición del usuario disponible, esto es distinto de la postura de puntero que representa a ray señalador del controlador.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="7a5c2-182">Si desea que se va a dibujar algo en la ubicación de la mano, utilice TryGetLocation.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="7a5c2-183">Si desea raycast desde la punta del controlador, obtenga señalador rayo de TryGetInteractionSourcePose en el SpatialPointerPose.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="7a5c2-184">También puede usar los otros eventos en SpatialInteractionManager como SourceDetected y SourceLost, reaccionar cuando manos ENTRAR o salir de la vista del dispositivo o cuando mueve de dentro o fuera de la posición lista (dedo de índice se genera con palm hacia delante) o al movimiento controladores para activar o desactivar o están emparejados/no emparejados.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="7a5c2-185">Postura de control frente a la postura señalador</span><span class="sxs-lookup"><span data-stu-id="7a5c2-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="7a5c2-186">Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma, con el diseño de cada controlador que se diferencia en su relación entre la posición del usuario mano y natural "Reenviar" dirección de que las aplicaciones debe utilizar para que apunte al representar el controlador.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="7a5c2-187">Para representar mejor estos controladores, hay dos tipos de plantea que puede investigar para cada origen de interacción:</span><span class="sxs-lookup"><span data-stu-id="7a5c2-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="7a5c2-188">El **control postura**, que representa la ubicación de la palma de una mano detectada por un HoloLens, o bien la palma que contiene un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="7a5c2-189">En inmersivos, esta postura mejor se usa para representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="7a5c2-190">El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="7a5c2-191">El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)</span><span class="sxs-lookup"><span data-stu-id="7a5c2-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="7a5c2-192">El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="7a5c2-193">El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="7a5c2-194">Puede tener acceso a la postura de control a través de [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="7a5c2-195">El **puntero postura**, que representa la punta del controlador que señala hacia delante.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="7a5c2-196">Esta postura está concebida para raycast cuando **apuntando a la interfaz de usuario** cuando está representando el propio modelo de controlador.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="7a5c2-197">Puede tener acceso a la postura de puntero a través de [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="7a5c2-198">Gestos compuestos: SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="7a5c2-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="7a5c2-199">Un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpreta las interacciones del usuario de las manos, controladores de movimiento y el comando de voz "Select" a los eventos de gestos espacial expuesta, qué destino de los usuarios mediante su mirada principal.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="7a5c2-200">Gestos espaciales constituyen una clave de entrada para las aplicaciones de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="7a5c2-201">Mediante el enrutamientos interacciones desde el SpatialInteractionManager a SpatialGestureRecognizer de un holograma, las aplicaciones pueden detectar eventos Tap, suspensión, manipulación y navegación uniformemente entre manos, voz y dispositivos de entrada espaciales, sin tener que controlar las pulsaciones y libera manualmente.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="7a5c2-202">SpatialGestureRecognizer realiza solo la anulación de ambigüedades mínimo entre el conjunto de gestos que solicitan.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="7a5c2-203">Por ejemplo, si se solicita solo Tap, el usuario puede presionada su dedo como deseen y todavía se producirá una derivación.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="7a5c2-204">Si se solicita tanto pulsado, después de aproximadamente un segundo de mantener presionado su dedo, el gesto se promoverá a una suspensión y ya no se producirá un punteo.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="7a5c2-205">Para usar SpatialGestureRecognizer, controlar el SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) agarre el SpatialPointerPose expuesto allí y eventos.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="7a5c2-206">Usar ray de mirada principal del usuario desde esta postura para formar una intersección con el hologramas y superficie mallas en el entorno del usuario, con el fin de determinar lo que va a interactuar con el usuario.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="7a5c2-207">A continuación, enrutar la SpatialInteraction en los argumentos de evento SpatialGestureRecognizer del holograma de destino, mediante su [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) método.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="7a5c2-208">Esto inicia la interpretación de esa interacción según la [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) establecer en ese módulo de reconocimiento, o en tiempo de creación - [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span><span class="sxs-lookup"><span data-stu-id="7a5c2-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="7a5c2-209">En HoloLens, las interacciones y gestos generalmente deben derivar sus destinatarios de mirada principal del usuario, en lugar de intentar para representar o interactuar directamente en la ubicación de la mano.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="7a5c2-210">Una vez que se ha iniciado una interacción, los movimientos relativos de la mano pueden utilizarse para controlar el movimiento, al igual que con el gesto de manipulación o exploración.</span><span class="sxs-lookup"><span data-stu-id="7a5c2-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a5c2-211">Vea también</span><span class="sxs-lookup"><span data-stu-id="7a5c2-211">See also</span></span>
* [<span data-ttu-id="7a5c2-212">Gaze</span><span class="sxs-lookup"><span data-stu-id="7a5c2-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="7a5c2-213">Gestos</span><span class="sxs-lookup"><span data-stu-id="7a5c2-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="7a5c2-214">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="7a5c2-214">Motion controllers</span></span>](motion-controllers.md)
