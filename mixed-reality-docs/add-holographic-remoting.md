---
title: Agregar remoting holográfica
description: Explica cómo utilizar Remoting holográfica para representar un HoloLens hologramas a través de la red.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, remoting holográfica, procesamiento remoto, red de representación, HoloLens, hologramas remotos
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605789"
---
# <a name="add-holographic-remoting"></a><span data-ttu-id="79cc8-104">Agregar remoting holográfica</span><span class="sxs-lookup"><span data-stu-id="79cc8-104">Add holographic remoting</span></span>

> [!NOTE]
> <span data-ttu-id="79cc8-105">Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="79cc8-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="79cc8-106">Agregar remoting holographic a su escritorio o aplicación para UWP</span><span class="sxs-lookup"><span data-stu-id="79cc8-106">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="79cc8-107">Esta página describe cómo agregar holográfica de comunicación remota a un escritorio o una aplicación para UWP.</span><span class="sxs-lookup"><span data-stu-id="79cc8-107">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="79cc8-108">Comunicación remota holográfica permite que la aplicación para tener como destino un HoloLens con holográfica contenido hospedado en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, permitiendo el acceso a más recursos del sistema y lo que permite integrar remoto [envolventes vistas](app-views.md) en software de PC de escritorio existente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-108">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="79cc8-109">Una aplicación de host de comunicación remota recibe un flujo de datos de entrada de un HoloLens, representa el contenido en una vista virtual envolvente y transmite el contenido de marcos a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="79cc8-109">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="79cc8-110">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="79cc8-110">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="79cc8-111">Para usar el acceso remoto, utilizará un paquete NuGet para agregar remoting holographic a su escritorio o aplicación para UWP y escribir código para controlar la conexión y se representan en una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-111">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="79cc8-112">Bibliotecas auxiliares se incluyen en el ejemplo de código que simplifican la tarea de administrar la conexión del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="79cc8-112">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="79cc8-113">Una conexión de comunicación remota típica tendrá sea tan lenta como 50 ms de latencia.</span><span class="sxs-lookup"><span data-stu-id="79cc8-113">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="79cc8-114">La aplicación de Reproductor puede notificar la latencia en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="79cc8-114">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="79cc8-115">Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="79cc8-115">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="79cc8-116">Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.</span><span class="sxs-lookup"><span data-stu-id="79cc8-116">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="79cc8-117">Obtener la comunicación remota de paquetes de NuGet</span><span class="sxs-lookup"><span data-stu-id="79cc8-117">Get the remoting NuGet packages</span></span>

<span data-ttu-id="79cc8-118">Siga estos pasos para obtener el paquete NuGet para la comunicación remota holográfica y agregue una referencia del proyecto:</span><span class="sxs-lookup"><span data-stu-id="79cc8-118">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="79cc8-119">Vaya a su proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79cc8-119">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="79cc8-120">Haga doble clic en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="79cc8-120">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="79cc8-121">En el panel que aparece, haga clic en **examinar** y, a continuación, busque "Holográfica Remoting".</span><span class="sxs-lookup"><span data-stu-id="79cc8-121">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="79cc8-122">Seleccione **Microsoft.Holographic.Remoting** y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="79cc8-122">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="79cc8-123">Si el **Preview** aparece el cuadro de diálogo, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="79cc8-123">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="79cc8-124">El siguiente cuadro de diálogo que aparece es el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="79cc8-124">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="79cc8-125">Haga clic en **acepto** para aceptar el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="79cc8-125">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="79cc8-126">Crear el HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="79cc8-126">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="79cc8-127">En primer lugar, se necesita una instancia de HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="79cc8-127">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="79cc8-128">Agregar esto a la clase que se ocupa de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="79cc8-128">Add this to the class that will be handling remoting.</span></span>

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="79cc8-129">También deberá realizar un seguimiento de estado de conexión.</span><span class="sxs-lookup"><span data-stu-id="79cc8-129">You'll also need to track connection state.</span></span> <span data-ttu-id="79cc8-130">Si desea representar la vista previa, debe tener una textura para copiarlo a.</span><span class="sxs-lookup"><span data-stu-id="79cc8-130">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="79cc8-131">También necesita algunas cosas como un bloqueo de estado de conexión, alguna manera de almacenar la dirección IP de HoloLens y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-131">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="79cc8-132">Inicializar HolographicStreamerHelpers y conéctese a HoloLens</span><span class="sxs-lookup"><span data-stu-id="79cc8-132">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="79cc8-133">Para conectarse a un dispositivo HoloLens, cree una instancia de HolographicStreamerHelpers y conéctese a la dirección IP de destino.</span><span class="sxs-lookup"><span data-stu-id="79cc8-133">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="79cc8-134">Deberá establecer el tamaño del fotograma de vídeo para que coincida con el ancho de pantalla de HoloLens y el alto, porque la biblioteca de Remoting holográfica espera que las resoluciones de codificador y descodificador que coincidan exactamente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-134">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="79cc8-135">La conexión del dispositivo es asincrónica.</span><span class="sxs-lookup"><span data-stu-id="79cc8-135">The device connection is asynchronous.</span></span> <span data-ttu-id="79cc8-136">Las necesidades de su aplicación para proporcionar los controladores de eventos para conectar, desconectar y marco de envío de eventos.</span><span class="sxs-lookup"><span data-stu-id="79cc8-136">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="79cc8-137">El evento OnConnected puede actualizar la interfaz de usuario, iniciar representación y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-137">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="79cc8-138">En nuestro ejemplo de código de escritorio, actualizamos el título de ventana con un mensaje "conectado".</span><span class="sxs-lookup"><span data-stu-id="79cc8-138">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="79cc8-139">Puede controlar el evento OnDisconnected reconexión, las actualizaciones de la interfaz de usuario y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-139">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="79cc8-140">En este ejemplo, se vuelve a conectar las si se produce un error transitorio.</span><span class="sxs-lookup"><span data-stu-id="79cc8-140">In this example, we reconnect if there is a transient failure.</span></span>

```
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="79cc8-141">Cuando el componente de comunicación remota está listo para enviar un marco, la aplicación se proporciona una oportunidad para realizar una copia del mismo en el SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="79cc8-141">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="79cc8-142">En este caso, el marco se copia en una cadena de intercambio para que se pueden mostrar en una ventana de vista previa.</span><span class="sxs-lookup"><span data-stu-id="79cc8-142">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="79cc8-143">Representar el contenido holográfica</span><span class="sxs-lookup"><span data-stu-id="79cc8-143">Render holographic content</span></span>

<span data-ttu-id="79cc8-144">Para representar el contenido mediante la comunicación remota, se configura un IFrameworkView virtual dentro de su escritorio o aplicación para UWP y procesar holográficas marcos de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="79cc8-144">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="79cc8-145">Todas las API de Windows Holographic son usa que la misma manera por esta vista, pero se ha configurado una forma ligeramente diferente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-145">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="79cc8-146">En lugar de crearlas usted mismo, los componentes de voz y de espacio holográficas proceden de la clase HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="79cc8-146">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="79cc8-147">En lugar de usar un bucle de actualización dentro de un método de ejecución, proporciona actualizaciones de graduación desde el bucle principal de su escritorio o aplicación para UWP.</span><span class="sxs-lookup"><span data-stu-id="79cc8-147">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="79cc8-148">Esto permite que el escritorio o aplicación para UWP para conservar el control del procesamiento de mensajes.</span><span class="sxs-lookup"><span data-stu-id="79cc8-148">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="79cc8-149">Método de la vista holográfica aplicación Tick() completa una iteración de la actualización, draw, bucle está presente.</span><span class="sxs-lookup"><span data-stu-id="79cc8-149">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="79cc8-150">La actualización de la vista holográfica app, representación y bucle presente es exactamente el mismo ya que es cuando se ejecuta en HoloLens - salvo que tienen acceso a una mayor cantidad de recursos del sistema en su PC de escritorio.</span><span class="sxs-lookup"><span data-stu-id="79cc8-150">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="79cc8-151">Puede representar muchos más triángulos, tiene varias pasadas de dibujos, hacer más física y usan x64 procesos para cargar el contenido que requiere más de 2 GB de RAM.</span><span class="sxs-lookup"><span data-stu-id="79cc8-151">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="79cc8-152">Desconectar y finalizar la sesión remota</span><span class="sxs-lookup"><span data-stu-id="79cc8-152">Disconnect and end the remote session</span></span>

<span data-ttu-id="79cc8-153">Para desconectar - por ejemplo, cuando el usuario hace clic en un botón de la interfaz de usuario para desconectar - llame Disconnect() en el HolographicStreamerHelpers y, a continuación, liberar el objeto.</span><span class="sxs-lookup"><span data-stu-id="79cc8-153">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="79cc8-154">Obtener el Reproductor de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="79cc8-154">Get the remoting player</span></span>

<span data-ttu-id="79cc8-155">El Reproductor de comunicación remota de Windows Holographic se ofrece en la tienda de aplicaciones de Windows como para hospedar aplicaciones de comunicación remota para conectarse a un punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="79cc8-155">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="79cc8-156">Para obtener el Reproductor de comunicación remota de Windows Holographic, visite la tienda de aplicaciones de Windows desde su HoloLens, búsqueda para la comunicación remota y descargar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="79cc8-156">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="79cc8-157">El Reproductor de remoting incluye una característica para mostrar las estadísticas en la pantalla, que puede ser útil al depurar aplicaciones de host de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="79cc8-157">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="79cc8-158">Notas y recursos</span><span class="sxs-lookup"><span data-stu-id="79cc8-158">Notes and resources</span></span>

<span data-ttu-id="79cc8-159">La vista holográfica aplicación necesitará una manera de proporcionar la aplicación con el dispositivo Direct3D, lo que debe usarse para inicializar el espacio holográfico.</span><span class="sxs-lookup"><span data-stu-id="79cc8-159">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="79cc8-160">La aplicación debe usar este dispositivo Direct3D para copiar y mostrar el fotograma de vista previa.</span><span class="sxs-lookup"><span data-stu-id="79cc8-160">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="79cc8-161">**Ejemplo de código:** Un ejemplo de código completo de Remoting holográfica está disponible, lo que incluye una vista holográfica aplicación que sea compatible con la comunicación remota y los proyectos de host de comunicación remota de escritorio UWP con XAML, DirectX de UWP y Win32.</span><span class="sxs-lookup"><span data-stu-id="79cc8-161">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="79cc8-162">Para obtenerla, vaya aquí:</span><span class="sxs-lookup"><span data-stu-id="79cc8-162">To get it, go here:</span></span>
* [<span data-ttu-id="79cc8-163">Ejemplo de código holográfico de Windows para la comunicación remota</span><span class="sxs-lookup"><span data-stu-id="79cc8-163">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="79cc8-164">**Tenga en cuenta la depuración:** La biblioteca de Remoting holográfica puede producir excepciones de primera oportunidad.</span><span class="sxs-lookup"><span data-stu-id="79cc8-164">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="79cc8-165">Estas excepciones pueden verse en las sesiones, dependiendo de la configuración de excepciones de Visual Studio que están activa en el momento de depuración.</span><span class="sxs-lookup"><span data-stu-id="79cc8-165">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="79cc8-166">Estas excepciones se detectan internamente por la biblioteca de Remoting holográfica y pueden omitirse.</span><span class="sxs-lookup"><span data-stu-id="79cc8-166">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
