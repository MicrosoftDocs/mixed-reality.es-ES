---
title: Incorporación de Holographic Remoting
description: Explica cómo usar la comunicación remota holográfica para representar hologramas en una HoloLens a través de la red.
author: MikeRiches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, hologramas, comunicación remota holográfica, representación remota, representación en red, HoloLens, hologramas remotos
ms.openlocfilehash: 523486c26c03bd4b3d5ed8e8cafd994f12678e3b
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122050"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="2f32d-104">Incorporación de la comunicación remota holográfica (HoloLens (1ª generación))</span><span class="sxs-lookup"><span data-stu-id="2f32d-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="2f32d-105">En este documento se describe la creación de una aplicación host para HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="2f32d-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="2f32d-106">La aplicación host para **HoloLens (1ª generación)** debe usar el paquete NuGet versión **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="2f32d-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="2f32d-107">Esto implica que las aplicaciones host escritas para HoloLens 1 no son compatibles con HoloLens 2 y viceversa.</span><span class="sxs-lookup"><span data-stu-id="2f32d-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="2f32d-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2f32d-108">HoloLens 2</span></span>

<span data-ttu-id="2f32d-109">Los desarrolladores de HoloLens que usen la comunicación remota de Holographic deberán actualizar sus aplicaciones para que sean compatibles con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2f32d-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="2f32d-110">Esto requiere una nueva versión del paquete NuGet de Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="2f32d-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="2f32d-111">Si una aplicación que usa el paquete NuGet de Holographic Remoting con un número de versión menor que 2.0.0.0 intenta conectarse al reproductor de acceso remoto holográfica en HoloLens 2, se producirá un error en la conexión.</span><span class="sxs-lookup"><span data-stu-id="2f32d-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="2f32d-112">Las instrucciones específicas de HoloLens 2 se pueden encontrar [aquí](holographic-remoting-create-host.md).</span><span class="sxs-lookup"><span data-stu-id="2f32d-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="2f32d-113">Adición de Holographic Remoting a su aplicación de escritorio o UWP</span><span class="sxs-lookup"><span data-stu-id="2f32d-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="2f32d-114">En esta página se describe cómo agregar la comunicación remota holográfica a una aplicación de escritorio o UWP.</span><span class="sxs-lookup"><span data-stu-id="2f32d-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="2f32d-115">Holographic Remoting permite que la aplicación tenga como destino HoloLens con contenido holográfica hospedado en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema y permite integrar [vistas](app-views.md) envolventes remotas en software de equipo de escritorio existente.</span><span class="sxs-lookup"><span data-stu-id="2f32d-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="2f32d-116">Una aplicación host de comunicación remota recibe un flujo de datos de entrada de HoloLens, representa el contenido en una vista envolvente virtual y transmite los fotogramas de contenido de nuevo a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2f32d-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="2f32d-117">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="2f32d-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="2f32d-118">Para usar la comunicación remota, usará un paquete NuGet para agregar la comunicación remota holográfica a su aplicación de escritorio o UWP, y escribir código para controlar la conexión y representar en una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="2f32d-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="2f32d-119">Las bibliotecas auxiliares se incluyen en el ejemplo de código que simplifican la tarea de controlar la conexión del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2f32d-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="2f32d-120">Una conexión remota típica tendrá un mínimo de 50 ms de latencia.</span><span class="sxs-lookup"><span data-stu-id="2f32d-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="2f32d-121">La aplicación de reproducción puede informar de la latencia en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="2f32d-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="2f32d-122">Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="2f32d-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="2f32d-123">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="2f32d-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="2f32d-124">Obtención de los paquetes NuGet de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="2f32d-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="2f32d-125">Siga estos pasos para obtener el paquete NuGet para la comunicación remota de Holographic y agregue una referencia desde el proyecto:</span><span class="sxs-lookup"><span data-stu-id="2f32d-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="2f32d-126">Vaya al proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f32d-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="2f32d-127">Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="2f32d-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="2f32d-128">En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="2f32d-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="2f32d-129">Seleccione **Microsoft. Holographic. Remoting** y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="2f32d-129">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="2f32d-130">Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="2f32d-130">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="2f32d-131">El siguiente cuadro de diálogo que aparece es el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="2f32d-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="2f32d-132">Haga clic en Acepto para aceptar el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="2f32d-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="2f32d-133">Crear HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="2f32d-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="2f32d-134">En primer lugar, necesitamos una instancia de HolographicStreamerHelpers.</span><span class="sxs-lookup"><span data-stu-id="2f32d-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="2f32d-135">Agregue esto a la clase que controlará la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="2f32d-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="2f32d-136">También necesitará realizar un seguimiento del estado de la conexión.</span><span class="sxs-lookup"><span data-stu-id="2f32d-136">You'll also need to track connection state.</span></span> <span data-ttu-id="2f32d-137">Si desea representar la vista previa, debe tener una textura en la que copiarla.</span><span class="sxs-lookup"><span data-stu-id="2f32d-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="2f32d-138">También necesita algunas cosas como un bloqueo de estado de conexión, alguna forma de almacenar la dirección IP de HoloLens, etc.</span><span class="sxs-lookup"><span data-stu-id="2f32d-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="2f32d-139">Inicializar HolographicStreamerHelpers y conectarse a HoloLens</span><span class="sxs-lookup"><span data-stu-id="2f32d-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="2f32d-140">Para conectarse a un dispositivo HoloLens, cree una instancia de HolographicStreamerHelpers y conéctese a la dirección IP de destino.</span><span class="sxs-lookup"><span data-stu-id="2f32d-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="2f32d-141">Tendrá que establecer el tamaño del fotograma de vídeo para que coincida con el ancho y el alto de la pantalla de HoloLens, ya que la biblioteca remota de Holographic espera que las resoluciones del codificador y el descodificador coincidan exactamente.</span><span class="sxs-lookup"><span data-stu-id="2f32d-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
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

<span data-ttu-id="2f32d-142">La conexión del dispositivo es asincrónica.</span><span class="sxs-lookup"><span data-stu-id="2f32d-142">The device connection is asynchronous.</span></span> <span data-ttu-id="2f32d-143">La aplicación debe proporcionar controladores de eventos para los eventos Connect, Disconnect y Send frame.</span><span class="sxs-lookup"><span data-stu-id="2f32d-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="2f32d-144">El evento alconnected puede actualizar la interfaz de usuario, iniciar la representación, etc.</span><span class="sxs-lookup"><span data-stu-id="2f32d-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="2f32d-145">En nuestro ejemplo de código de escritorio, actualizamos el título de la ventana con un mensaje "conectado".</span><span class="sxs-lookup"><span data-stu-id="2f32d-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="2f32d-146">El evento OnDisconnection puede controlar la reconexión, las actualizaciones de la interfaz de usuario, etc.</span><span class="sxs-lookup"><span data-stu-id="2f32d-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="2f32d-147">En este ejemplo, se vuelve a conectar si se produce un error transitorio.</span><span class="sxs-lookup"><span data-stu-id="2f32d-147">In this example, we reconnect if there is a transient failure.</span></span>

```cpp
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

<span data-ttu-id="2f32d-148">Cuando el componente de comunicación remota está listo para enviar un marco, se proporciona a la aplicación la oportunidad de hacer una copia de él en el SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="2f32d-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="2f32d-149">En este caso, copiamos el fotograma a una cadena de intercambio para que podamos mostrarlo en una ventana de vista previa.</span><span class="sxs-lookup"><span data-stu-id="2f32d-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
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

### <a name="render-holographic-content"></a><span data-ttu-id="2f32d-150">Representación de contenido holográfica</span><span class="sxs-lookup"><span data-stu-id="2f32d-150">Render holographic content</span></span>

<span data-ttu-id="2f32d-151">Para representar contenido mediante la comunicación remota, configure un IFrameworkView virtual dentro de la aplicación de escritorio o UWP y procese tramas holográficas de la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="2f32d-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="2f32d-152">Todas las API de Windows Holographic se usan de la misma manera en esta vista, pero se configuran de forma ligeramente diferente.</span><span class="sxs-lookup"><span data-stu-id="2f32d-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="2f32d-153">En lugar de crearlos usted mismo, el espacio holográfica y los componentes de voz provienen de la clase HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="2f32d-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="2f32d-154">En lugar de usar un bucle de actualización dentro de un método Run, se proporcionan actualizaciones por pasos desde el bucle principal de la aplicación de escritorio o UWP.</span><span class="sxs-lookup"><span data-stu-id="2f32d-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="2f32d-155">Esto permite que la aplicación de escritorio o UWP permanezca en el control del procesamiento de mensajes.</span><span class="sxs-lookup"><span data-stu-id="2f32d-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="2f32d-156">El método tick () de la vista de aplicación holográfica completa una iteración del bucle Update, Draw y Present.</span><span class="sxs-lookup"><span data-stu-id="2f32d-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
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

<span data-ttu-id="2f32d-157">El bucle de actualización, representación y presentación de la vista de aplicación holográfica es exactamente el mismo que cuando se ejecuta en HoloLens, salvo que tiene acceso a una cantidad mucho mayor de recursos del sistema en el equipo de escritorio.</span><span class="sxs-lookup"><span data-stu-id="2f32d-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="2f32d-158">Puede representar muchos más triángulos, tener más pasos de dibujo, hacer más física y usar procesos x64 para cargar contenido que requiera más de 2 GB de RAM.</span><span class="sxs-lookup"><span data-stu-id="2f32d-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="2f32d-159">Desconectar y finalizar la sesión remota</span><span class="sxs-lookup"><span data-stu-id="2f32d-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="2f32d-160">Para desconectarse: por ejemplo, cuando el usuario hace clic en un botón de la interfaz de usuario para desconectar-llamar a Disconnect () en HolographicStreamerHelpers y, a continuación, libera el objeto.</span><span class="sxs-lookup"><span data-stu-id="2f32d-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
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

## <a name="get-the-remoting-player"></a><span data-ttu-id="2f32d-161">Obtener el reproductor remoto</span><span class="sxs-lookup"><span data-stu-id="2f32d-161">Get the remoting player</span></span>

<span data-ttu-id="2f32d-162">El reproductor de Windows Holographic Remoting se ofrece en la tienda de aplicaciones de Windows como un punto de conexión para que las aplicaciones de host remoto se conecten a.</span><span class="sxs-lookup"><span data-stu-id="2f32d-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="2f32d-163">Para obtener el reproductor de Windows Holographic Remoting, visite la tienda de aplicaciones de Windows desde HoloLens, busque la comunicación remota y descargue la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2f32d-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="2f32d-164">El reproductor de comunicación remota incluye una característica para mostrar las estadísticas en pantalla, lo que puede resultar útil al depurar aplicaciones de host remoto.</span><span class="sxs-lookup"><span data-stu-id="2f32d-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="2f32d-165">Notas y recursos</span><span class="sxs-lookup"><span data-stu-id="2f32d-165">Notes and resources</span></span>

<span data-ttu-id="2f32d-166">La vista de aplicación holográfica necesitará una manera de proporcionar la aplicación con el dispositivo Direct3D, que debe usarse para inicializar el espacio holográfica.</span><span class="sxs-lookup"><span data-stu-id="2f32d-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="2f32d-167">La aplicación debe usar este dispositivo Direct3D para copiar y mostrar el marco de vista previa.</span><span class="sxs-lookup"><span data-stu-id="2f32d-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="2f32d-168">**Código de ejemplo:** Hay disponible un ejemplo de código de Holographic Remoting completo, que incluye una vista de aplicación holográfica que es compatible con los proyectos de host remoto y de comunicación remota para escritorio Win32, UWP DirectX y UWP con XAML.</span><span class="sxs-lookup"><span data-stu-id="2f32d-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="2f32d-169">Para obtenerlo, vaya aquí:</span><span class="sxs-lookup"><span data-stu-id="2f32d-169">To get it, go here:</span></span>
* [<span data-ttu-id="2f32d-170">Ejemplo de código Holographic de Windows para la comunicación remota</span><span class="sxs-lookup"><span data-stu-id="2f32d-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="2f32d-171">**Nota de depuración:** La biblioteca remota holográfica puede producir excepciones de primera oportunidad.</span><span class="sxs-lookup"><span data-stu-id="2f32d-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="2f32d-172">Estas excepciones pueden ser visibles en las sesiones de depuración, en función de la configuración de excepciones de Visual Studio que esté activa en ese momento.</span><span class="sxs-lookup"><span data-stu-id="2f32d-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="2f32d-173">Estas excepciones las detecta internamente la biblioteca de comunicación remota holográfica y se pueden omitir.</span><span class="sxs-lookup"><span data-stu-id="2f32d-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
