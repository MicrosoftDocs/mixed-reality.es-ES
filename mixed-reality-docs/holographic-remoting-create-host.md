---
title: Escritura de una aplicación remota de control remoto de holografías
description: Al crear un contenido remoto de aplicaciones remotas holográficas, que se representa en un equipo remoto, se puede transmitir a HoloLens 2. En este artículo se describe cómo se puede lograr esto.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 53f370dc32b4fe56eb610b6e5687022e0908f7a8
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866865"
---
# <a name="writing-a-holographic-remoting-remote-app"></a><span data-ttu-id="9c098-105">Escritura de una aplicación remota de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="9c098-105">Writing a Holographic Remoting remote app</span></span>

>[!IMPORTANT]
><span data-ttu-id="9c098-106">En este documento se describe la creación de una aplicación remota para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c098-106">This document describes the creation of a remote application for HoloLens 2.</span></span> <span data-ttu-id="9c098-107">Las aplicaciones remotas para **HoloLens (1ª generación)** deben usar el paquete NuGet versión **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="9c098-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="9c098-108">Esto implica que las aplicaciones remotas escritas para HoloLens 2 no son compatibles con HoloLens 1 y viceversa.</span><span class="sxs-lookup"><span data-stu-id="9c098-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="9c098-109">La documentación de HoloLens 1 se puede encontrar [aquí](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="9c098-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="9c098-110">Al crear una aplicación remota Holographic Remoting, el contenido remoto que se representa en un equipo remoto se puede transmitir a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c098-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="9c098-111">En este artículo se describe cómo se puede lograr esto.</span><span class="sxs-lookup"><span data-stu-id="9c098-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="9c098-112">Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="9c098-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="9c098-113">Holographic Remoting permite que una aplicación tenga como destino HoloLens 2 con contenido holográfica representado en un equipo de escritorio o en un dispositivo UWP como la Xbox One, lo que permite el acceso a más recursos del sistema y permite la integración de [vistas envolventes](app-views.md) remotas en el software de equipo de escritorio existente.</span><span class="sxs-lookup"><span data-stu-id="9c098-113">Holographic remoting allows an app to target HoloLens 2 with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="9c098-114">Una aplicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista envolvente virtual y vuelve a transmitir los fotogramas de contenido a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c098-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="9c098-115">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="9c098-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="9c098-116">Holographic Remoting se agrega a una aplicación de escritorio o UWP a través de un paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="9c098-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="9c098-117">Se requiere código adicional que controla la conexión y se representa en una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="9c098-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="9c098-118">Una conexión remota típica tendrá un mínimo de 50 ms de latencia.</span><span class="sxs-lookup"><span data-stu-id="9c098-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="9c098-119">La aplicación de reproducción puede informar de la latencia en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="9c098-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c098-120">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="9c098-120">Prerequisites</span></span>

<span data-ttu-id="9c098-121">Un buen punto de partida es una aplicación de escritorio o UWP basada en DirectX que funciona como destino de la API de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="9c098-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="9c098-122">Para obtener más información, vea [Introducción al desarrollo de DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9c098-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="9c098-123">La [plantilla de proyecto Holographic de C++](creating-a-holographic-directx-project.md) es un buen punto de partida.</span><span class="sxs-lookup"><span data-stu-id="9c098-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9c098-124">Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="9c098-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="9c098-125">Se admite el uso de un apartamento de un [solo subproceso](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) , pero se producirá un rendimiento poco óptimo y posiblemente se produzca una intermitencia durante la reproducción.</span><span class="sxs-lookup"><span data-stu-id="9c098-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="9c098-126">Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartamento multiproceso es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="9c098-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="9c098-127">Obtención del paquete NuGet de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="9c098-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="9c098-128">Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c098-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="9c098-129">Abra el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c098-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="9c098-130">Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="9c098-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="9c098-131">En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="9c098-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="9c098-132">Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="9c098-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="9c098-133">Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="9c098-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="9c098-134">El siguiente cuadro de diálogo que aparece es el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="9c098-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="9c098-135">Haga clic en **acepto para aceptar el contrato de licencia** .</span><span class="sxs-lookup"><span data-stu-id="9c098-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="9c098-136">La versión **1. x.** x del paquete NuGet sigue estando disponible para los desarrolladores que quieran tener como destino HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="9c098-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="9c098-137">Para obtener más información, consulte incorporación de la [comunicación remota holográfica (HoloLens (1º generación))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="9c098-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="9c098-138">Crear el contexto remoto</span><span class="sxs-lookup"><span data-stu-id="9c098-138">Create the remote context</span></span>

<span data-ttu-id="9c098-139">Como primer paso, la aplicación debe crear un contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="9c098-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="9c098-140">Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="9c098-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="9c098-141">Esto se realiza durante la creación del contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="9c098-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="9c098-142">Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto remoto puede producir un comportamiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="9c098-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="9c098-143">El enfoque recomendado es crear el contexto remoto tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9c098-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="9c098-144">Nunca mezcle objetos creados o recuperados a través de cualquier API de realidad mixta de Windows antes de la llamada a CreateRemoteContext con objetos creados o recuperados después.</span><span class="sxs-lookup"><span data-stu-id="9c098-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="9c098-145">A continuación, es necesario crear el espacio holográfica.</span><span class="sxs-lookup"><span data-stu-id="9c098-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="9c098-146">No es necesario especificar CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="9c098-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="9c098-147">Las aplicaciones de escritorio que no tienen un CoreWindow solo pueden pasar un ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="9c098-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="9c098-148">Conexión al dispositivo</span><span class="sxs-lookup"><span data-stu-id="9c098-148">Connect to the device</span></span>

<span data-ttu-id="9c098-149">Una vez que la aplicación remota está lista para la representación de contenido, se puede establecer una conexión con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9c098-149">Once the remote app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="9c098-150">La conexión puede realizarse de una de estas dos maneras.</span><span class="sxs-lookup"><span data-stu-id="9c098-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="9c098-151">La aplicación remota se conecta al reproductor que se ejecuta en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9c098-151">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="9c098-152">El reproductor que se ejecuta en el dispositivo se conecta a la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="9c098-152">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="9c098-153">Para establecer una conexión desde la aplicación remota a HoloLens 2, llame al ```Connect``` método en el contexto remoto y especifique el nombre de host y el puerto.</span><span class="sxs-lookup"><span data-stu-id="9c098-153">To establish a connection from the remote app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="9c098-154">El puerto que usa el reproductor de comunicación remota holográfica es **8265**.</span><span class="sxs-lookup"><span data-stu-id="9c098-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="9c098-155">Como con cualquier API de C++/WinRT, ```Connect``` puede producir una excepción WinRT:: hresult_error que debe controlarse.</span><span class="sxs-lookup"><span data-stu-id="9c098-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="9c098-156">Para evitar el uso de la proyección de lenguaje [/WinRT de C++](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) , se puede incluir el archivo que ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` se encuentra dentro del paquete NuGet de Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="9c098-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="9c098-157">Contiene declaraciones de las interfaces COM subyacentes.</span><span class="sxs-lookup"><span data-stu-id="9c098-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="9c098-158">No obstante, se recomienda el uso de/WinRT de C++.</span><span class="sxs-lookup"><span data-stu-id="9c098-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="9c098-159">La escucha de conexiones entrantes en la aplicación remota se puede realizar mediante una llamada al ```Listen``` método.</span><span class="sxs-lookup"><span data-stu-id="9c098-159">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="9c098-160">El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada.</span><span class="sxs-lookup"><span data-stu-id="9c098-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="9c098-161">El puerto de enlace se usa para el protocolo de enlace inicial.</span><span class="sxs-lookup"><span data-stu-id="9c098-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="9c098-162">A continuación, los datos se envían a través del puerto de transporte.</span><span class="sxs-lookup"><span data-stu-id="9c098-162">The data is then send over the transport port.</span></span> <span data-ttu-id="9c098-163">De forma predeterminada, se usan **8265** y **8266** .</span><span class="sxs-lookup"><span data-stu-id="9c098-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="9c098-164">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```En el paquete NuGet se incluye documentación detallada para la API expuesta por la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="9c098-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="9c098-165">Controlar eventos específicos de la comunicación remota</span><span class="sxs-lookup"><span data-stu-id="9c098-165">Handling Remoting specific events</span></span>

<span data-ttu-id="9c098-166">El contexto remoto expone tres eventos que son importantes para supervisar el estado de una conexión.</span><span class="sxs-lookup"><span data-stu-id="9c098-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="9c098-167">OnConnection: se desencadena cuando se ha establecido correctamente una conexión con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9c098-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="9c098-168">OnDisconnection: se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="9c098-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="9c098-169">MyListener: cuando se inicia la escucha de conexiones entrantes.</span><span class="sxs-lookup"><span data-stu-id="9c098-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="9c098-170">Además, se puede consultar el estado de la conexión utilizando la ```ConnectionState``` propiedad en el contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="9c098-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="9c098-171">Control de eventos de voz</span><span class="sxs-lookup"><span data-stu-id="9c098-171">Handling speech events</span></span>

<span data-ttu-id="9c098-172">El uso de la interfaz de voz remota es posible registrar los desencadenadores de voz con HoloLens 2 y hacerlos remotos en la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="9c098-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="9c098-173">Este miembro adicional es necesario para realizar el seguimiento del estado de la voz remota.</span><span class="sxs-lookup"><span data-stu-id="9c098-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="9c098-174">En primer lugar, es necesario recuperar la interfaz de voz remota.</span><span class="sxs-lookup"><span data-stu-id="9c098-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="9c098-175">Con un método auxiliar asincrónico, puede inicializar la voz remota.</span><span class="sxs-lookup"><span data-stu-id="9c098-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="9c098-176">Esto debe hacerse de forma asincrónica, ya que la inicialización puede tardar un tiempo considerable.</span><span class="sxs-lookup"><span data-stu-id="9c098-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="9c098-177">[Operaciones de simultaneidad y asincrónicas con c++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explica cómo crear funciones asincrónicas con c++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="9c098-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="9c098-178">Hay dos maneras de especificar frases que se reconocerán.</span><span class="sxs-lookup"><span data-stu-id="9c098-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="9c098-179">Especificación dentro de un archivo XML de gramática de voz.</span><span class="sxs-lookup"><span data-stu-id="9c098-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="9c098-180">Vea [Cómo crear una gramática XML básica](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9c098-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="9c098-181">Especifique pasándolos dentro del vector del diccionario a ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="9c098-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="9c098-182">Dentro de la devolución de llamada OnRecognizedSpeech, los eventos de voz se pueden procesar a continuación:</span><span class="sxs-lookup"><span data-stu-id="9c098-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="9c098-183">Vista previa del contenido transmitido localmente</span><span class="sxs-lookup"><span data-stu-id="9c098-183">Preview streamed content locally</span></span>

<span data-ttu-id="9c098-184">Para mostrar el mismo contenido en la aplicación remota que se envía al dispositivo, ```OnSendFrame``` se puede usar el evento del contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="9c098-184">To display the same content in the remote app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="9c098-185">El ```OnSendFrame``` evento se desencadena cada vez que la biblioteca de acceso remoto holográfica envía el marco actual al dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="9c098-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="9c098-186">Este es el momento ideal para tomar el contenido y también dividirlo en la ventana de escritorio o UWP.</span><span class="sxs-lookup"><span data-stu-id="9c098-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="9c098-187">Reproyección de profundidad</span><span class="sxs-lookup"><span data-stu-id="9c098-187">Depth Reprojection</span></span>

<span data-ttu-id="9c098-188">A partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting admite la [reproyección de profundidad](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="9c098-188">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="9c098-189">Esto requiere, además del búfer de color, hacer streaming del búfer de profundidad desde la aplicación remota a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c098-189">This requires, in addition to the color buffer, to also stream the depth buffer from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="9c098-190">De forma predeterminada, el streaming de búfer de profundidad está habilitado y configurado para usar la mitad de la resolución del búfer de color.</span><span class="sxs-lookup"><span data-stu-id="9c098-190">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="9c098-191">Esto puede cambiarse de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="9c098-191">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="9c098-192">Tenga en cuenta que, si no se deben usar los valores predeterminados, ```ConfigureDepthVideoStream``` se debe llamar a antes de establecer una conexión con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c098-192">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="9c098-193">El mejor lugar es justo después de haber creado el contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="9c098-193">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="9c098-194">Los valores posibles para DepthBufferStreamResolution son:</span><span class="sxs-lookup"><span data-stu-id="9c098-194">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="9c098-195">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="9c098-195">Full_Resolution</span></span>
* <span data-ttu-id="9c098-196">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="9c098-196">Half_Resolution</span></span>
* <span data-ttu-id="9c098-197">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="9c098-197">Quarter_Resolution</span></span>
* <span data-ttu-id="9c098-198">Deshabilitado (agregado con la versión [2.1.3](holographic-remoting-version-history.md#v2.1.3) y, si no se usa, no se crea ninguna secuencia de vídeo de profundidad adicional)</span><span class="sxs-lookup"><span data-stu-id="9c098-198">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="9c098-199">Tenga en cuenta que el uso de un búfer de profundidad de resolución completa también afecta a los requisitos de ancho de banda y se debe tener en cuenta en el valor de ancho de banda máximo que se proporciona a ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="9c098-199">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="9c098-200">Junto a la configuración de la resolución, también tiene que confirmar un búfer de profundidad a través de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="9c098-200">Beside configuring the resolution you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="9c098-201">Para comprobar si la reproyección de profundidad es correclty al trabajar en HoloLens 2, puede habilitar un visualizador de profundidad a través del portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9c098-201">To verify if depth reprojection is correclty working on HoloLens 2 you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="9c098-202">Consulte [comprobar profundidad está configurado correctamente](hologram-stability.md#verifying-depth-is-set-correctly) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9c098-202">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="9c098-203">Opcional: canales de datos personalizados</span><span class="sxs-lookup"><span data-stu-id="9c098-203">Optional: Custom data channels</span></span>

<span data-ttu-id="9c098-204">Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida.</span><span class="sxs-lookup"><span data-stu-id="9c098-204">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="9c098-205">Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9c098-205">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c098-206">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9c098-206">See Also</span></span>
* [<span data-ttu-id="9c098-207">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="9c098-207">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="9c098-208">Canales de datos personalizados de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="9c098-208">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="9c098-209">Establecimiento de una conexión segura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="9c098-209">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="9c098-210">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="9c098-210">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="9c098-211">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="9c098-211">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="9c098-212">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9c098-212">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
