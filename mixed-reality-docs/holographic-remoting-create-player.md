---
title: Escritura de un reproductor remoto Holographic Remoting
description: Mediante la creación de una aplicación de reproductor remoto holográfica personalizada, puede crear una aplicación personalizada capaz de mostrar el contenido representado en una máquina remota a HoloLens 2. En este artículo se describe cómo se puede lograr esto.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718099"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="1d63e-105">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="1d63e-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="1d63e-106">En este documento se describe la creación de una aplicación de reproductor personalizada para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d63e-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="1d63e-107">Los reproductores personalizados escritos para HoloLens 2 no son compatibles con las aplicaciones host escritas para HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="1d63e-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="1d63e-108">Esto implica que ambas aplicaciones deben usar el paquete NuGet versión **2. x. x**.</span><span class="sxs-lookup"><span data-stu-id="1d63e-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="1d63e-109">Mediante la creación de una aplicación de reproductor de acceso remoto holográfica personalizada, puede crear una aplicación personalizada capaz de mostrar [vistas](app-views.md) envolventes desde en una máquina remota de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d63e-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="1d63e-110">En este artículo se describe cómo se puede lograr esto.</span><span class="sxs-lookup"><span data-stu-id="1d63e-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="1d63e-111">Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="1d63e-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="1d63e-112">Un reproductor remoto holográfica permite a la aplicación mostrar el contenido holográfica [representado](rendering.md) en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema.</span><span class="sxs-lookup"><span data-stu-id="1d63e-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="1d63e-113">Una aplicación de reproductor de comunicación remota holográfica transmite datos de entrada a una aplicación host de Holographic Remoting y recibe una vista envolvente como flujo de audio y vídeo.</span><span class="sxs-lookup"><span data-stu-id="1d63e-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="1d63e-114">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="1d63e-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="1d63e-115">Para crear una aplicación de reproductor, usará un paquete NuGet para agregar la comunicación remota holográfica a la aplicación para UWP y escribir código para controlar la conexión y mostrar una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="1d63e-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="1d63e-116">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1d63e-116">Prerequisites</span></span>

<span data-ttu-id="1d63e-117">Un buen punto de partida es una aplicación UWP basada en DirectX que ya tiene como destino la API de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1d63e-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="1d63e-118">Para obtener más información, vea [Introducción al desarrollo de DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d63e-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="1d63e-119">Si no tiene una aplicación existente y desea comenzar desde el principio, la [ C++ plantilla de proyecto Holographic](creating-a-holographic-directx-project.md) es un buen punto de partida.</span><span class="sxs-lookup"><span data-stu-id="1d63e-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1d63e-120">Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="1d63e-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="1d63e-121">El uso de un [Apartamento](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) de un solo subproceso es compatible, pero puede dar lugar a un rendimiento poco óptimo y posiblemente a la reproducción.</span><span class="sxs-lookup"><span data-stu-id="1d63e-121">The use of a [single-threaded appartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="1d63e-122">Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) , un apartamento multiproceso es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="1d63e-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="1d63e-123">Obtención del paquete NuGet de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1d63e-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="1d63e-124">Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d63e-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="1d63e-125">Abra el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d63e-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="1d63e-126">Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="1d63e-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="1d63e-127">En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="1d63e-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="1d63e-128">Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="1d63e-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="1d63e-129">Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1d63e-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="1d63e-130">El siguiente cuadro de diálogo que aparece es el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="1d63e-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="1d63e-131">Haga clic en Acepto para aceptar el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="1d63e-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="1d63e-132">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` En el paquete NuGet se incluye documentación detallada para la API expuesta por la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="1d63e-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="1d63e-133">Modificar el paquete. appxmanifest de la aplicación</span><span class="sxs-lookup"><span data-stu-id="1d63e-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="1d63e-134">Para que la aplicación tenga en cuenta el Microsoft. Holographic. AppRemoting. dll agregado por el paquete de NuGet, es necesario realizar los siguientes pasos en el proyecto:</span><span class="sxs-lookup"><span data-stu-id="1d63e-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="1d63e-135">En el Explorador de soluciones haga clic con el botón derecho en el archivo **Package. appxmanifest** y seleccione **abrir con.** ..</span><span class="sxs-lookup"><span data-stu-id="1d63e-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="1d63e-136">Seleccione **Editor XML (texto)** y haga clic en Aceptar.</span><span class="sxs-lookup"><span data-stu-id="1d63e-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="1d63e-137">Agregue las líneas siguientes al archivo y guárdela</span><span class="sxs-lookup"><span data-stu-id="1d63e-137">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="1d63e-138">Crear el contexto del reproductor</span><span class="sxs-lookup"><span data-stu-id="1d63e-138">Create the player context</span></span>

<span data-ttu-id="1d63e-139">Como primer paso, la aplicación debe crear un contexto de reproductor.</span><span class="sxs-lookup"><span data-stu-id="1d63e-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="1d63e-140">Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="1d63e-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="1d63e-141">Esto se realiza durante la creación del contexto del reproductor.</span><span class="sxs-lookup"><span data-stu-id="1d63e-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="1d63e-142">Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto del reproductor puede producir un comportamiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="1d63e-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="1d63e-143">El enfoque recomendado es crear el contexto del reproductor tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1d63e-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="1d63e-144">Nunca mezcle objetos creados o recuperados a través de cualquier API de realidad mixta de ```PlayerContext::Create()``` Windows antes de la llamada a con objetos creados o recuperados después.</span><span class="sxs-lookup"><span data-stu-id="1d63e-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="1d63e-145">A continuación, se puede crear el HolographicSpace llamando a [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="1d63e-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="1d63e-146">Conexión al host</span><span class="sxs-lookup"><span data-stu-id="1d63e-146">Connect to the host</span></span>

<span data-ttu-id="1d63e-147">Una vez que la aplicación de reproducción está lista para representar el contenido, se puede establecer una conexión con el host.</span><span class="sxs-lookup"><span data-stu-id="1d63e-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="1d63e-148">La conexión se puede establecer de una de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="1d63e-148">The connection can be established in one of the follwing ways:</span></span>
1) <span data-ttu-id="1d63e-149">La aplicación de reproducción que se ejecuta en HoloLens 2 se conecta a la aplicación host.</span><span class="sxs-lookup"><span data-stu-id="1d63e-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="1d63e-150">La aplicación host se conecta a la aplicación de reproductor que se ejecuta en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d63e-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="1d63e-151">Para conectarse desde la aplicación del reproductor al host, llame ```Connect``` al método en el contexto del reproductor y especifique el nombre de host y el puerto.</span><span class="sxs-lookup"><span data-stu-id="1d63e-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="1d63e-152">El puerto predeterminado es **8265**.</span><span class="sxs-lookup"><span data-stu-id="1d63e-152">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="1d63e-153">Como con cualquier C++API ```Connect``` de/WinRT puede producir un WinRT:: hresult_error que debe controlarse.</span><span class="sxs-lookup"><span data-stu-id="1d63e-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="1d63e-154">La escucha de conexiones entrantes en la aplicación del reproductor puede realizarse ```Listen``` mediante una llamada al método.</span><span class="sxs-lookup"><span data-stu-id="1d63e-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="1d63e-155">El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada.</span><span class="sxs-lookup"><span data-stu-id="1d63e-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="1d63e-156">El puerto de enlace se usa para el protocolo de enlace inicial.</span><span class="sxs-lookup"><span data-stu-id="1d63e-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="1d63e-157">A continuación, los datos se envían a través del puerto de transporte.</span><span class="sxs-lookup"><span data-stu-id="1d63e-157">The data is then send over the transport port.</span></span> <span data-ttu-id="1d63e-158">De forma predeterminada, se usan el número de puerto **8265** y **8266** .</span><span class="sxs-lookup"><span data-stu-id="1d63e-158">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="1d63e-159">Controlar eventos relacionados con la conexión</span><span class="sxs-lookup"><span data-stu-id="1d63e-159">Handling connection related events</span></span>

<span data-ttu-id="1d63e-160">```PlayerContext``` Expone tres eventos para supervisar el estado de la conexión.</span><span class="sxs-lookup"><span data-stu-id="1d63e-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="1d63e-161">Conectado: Se desencadena cuando se ha establecido correctamente una conexión con el host.</span><span class="sxs-lookup"><span data-stu-id="1d63e-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="1d63e-162">OnDisconnection: Se desencadena si se termina una conexión establecida o no se pudo establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="1d63e-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="1d63e-163">Los ```ConnectionFailureReason``` valores posibles se documentan ```Microsoft.Holographic.AppRemoting.idl``` en el [archivo](#idl).</span><span class="sxs-lookup"><span data-stu-id="1d63e-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="1d63e-164">En escucha: Cuando se inicia la escucha de conexiones entrantes.</span><span class="sxs-lookup"><span data-stu-id="1d63e-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="1d63e-165">Además, se puede consultar el estado de la ```ConnectionState``` conexión utilizando la propiedad en el contexto del reproductor.</span><span class="sxs-lookup"><span data-stu-id="1d63e-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="1d63e-166">Mostrar el marco representado de forma remota</span><span class="sxs-lookup"><span data-stu-id="1d63e-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="1d63e-167">Para mostrar el contenido representado de forma remota, llame ```PlayerContext::BlitRemoteFrame()``` a mientras representa un [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="1d63e-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="1d63e-168">```BlitRemoteFrame()```requiere que el búfer de reserva del HolographicFrame actual esté enlazado como destino de representación.</span><span class="sxs-lookup"><span data-stu-id="1d63e-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="1d63e-169">El búfer de reserva se puede recibir desde [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) a través de la propiedad [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="1d63e-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="1d63e-170">Cuando se llama ```BlitRemoteFrame()``` , copia el último fotograma recibido de la aplicación host en el búfer de reserva del HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="1d63e-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="1d63e-171">Además, se establece el conjunto de puntos de enfoque si la aplicación remota ha especificado un punto de enfoque durante la representación del marco remoto.</span><span class="sxs-lookup"><span data-stu-id="1d63e-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="1d63e-172">```PlayerContext::BlitRemoteFrame()```potencialmente sobrescribe el punto de enfoque para el marco actual.</span><span class="sxs-lookup"><span data-stu-id="1d63e-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="1d63e-173">Para especificar un punto de enfoque de reserva, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes ```PlayerContext::BlitRemoteFrame()```de.</span><span class="sxs-lookup"><span data-stu-id="1d63e-173">To specifiy a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="1d63e-174">Para overrwrite el punto de enfoque remoto, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) después ```PlayerContext::BlitRemoteFrame()```de.</span><span class="sxs-lookup"><span data-stu-id="1d63e-174">To overrwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="1d63e-175">Si se ejecuta ```BlitRemoteFrame()``` correctamente ```BlitResult::Success_Color```, devuelve.</span><span class="sxs-lookup"><span data-stu-id="1d63e-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="1d63e-176">En caso contrario, devuelve el motivo del error:</span><span class="sxs-lookup"><span data-stu-id="1d63e-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="1d63e-177">```BlitResult::Failed_NoRemoteFrameAvailable```: No se pudo completar porque no hay ningún marco remoto disponible.</span><span class="sxs-lookup"><span data-stu-id="1d63e-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="1d63e-178">```BlitResult::Failed_NoCamera```: Error porque no hay ninguna cámara presente.</span><span class="sxs-lookup"><span data-stu-id="1d63e-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="1d63e-179">Opcional: Obtener estadísticas sobre el último marco remoto</span><span class="sxs-lookup"><span data-stu-id="1d63e-179">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="1d63e-180">Para diagnosticar problemas de rendimiento o de red, se pueden recuperar estadísticas sobre el último marco remoto ```PlayerContext::LastFrameStatistics``` a través de la propiedad.</span><span class="sxs-lookup"><span data-stu-id="1d63e-180">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="1d63e-181">Las estadísticas se actualizan durante la llamada a [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="1d63e-181">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="1d63e-182">Para obtener más información, consulte ```PlayerFrameStatistics``` la documentación ```Microsoft.Holographic.AppRemoting.idl``` del [archivo](#idl).</span><span class="sxs-lookup"><span data-stu-id="1d63e-182">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="1d63e-183">Opcional: Canales de datos personalizados</span><span class="sxs-lookup"><span data-stu-id="1d63e-183">Optional: Custom data channels</span></span>

<span data-ttu-id="1d63e-184">Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida.</span><span class="sxs-lookup"><span data-stu-id="1d63e-184">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="1d63e-185">Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="1d63e-185">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d63e-186">Vea también</span><span class="sxs-lookup"><span data-stu-id="1d63e-186">See Also</span></span>
* [<span data-ttu-id="1d63e-187">Escritura de una aplicación de host de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1d63e-187">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="1d63e-188">Canales de datos personalizados de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1d63e-188">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="1d63e-189">Establecimiento de una conexión segura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1d63e-189">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="1d63e-190">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="1d63e-190">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="1d63e-191">Términos de licencia del software de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1d63e-191">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="1d63e-192">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1d63e-192">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)