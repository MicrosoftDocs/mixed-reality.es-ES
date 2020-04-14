---
title: Escritura de un reproductor remoto Holographic Remoting
description: Mediante la creación de una aplicación de reproductor remoto holográfica personalizada, puede crear una aplicación personalizada capaz de mostrar el contenido representado en una máquina remota a HoloLens 2. En este artículo se describe cómo se puede lograr esto.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: b276558e43fc545be9e5c0be6feded229904ee97
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278223"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="33890-105">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="33890-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="33890-106">En este documento se describe la creación de una aplicación de reproductor personalizada para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="33890-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="33890-107">Los reproductores personalizados escritos para HoloLens 2 no son compatibles con las aplicaciones remotas escritas para HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="33890-107">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="33890-108">Esto implica que ambas aplicaciones deben usar el paquete NuGet versión **2. x. x**.</span><span class="sxs-lookup"><span data-stu-id="33890-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="33890-109">Mediante la creación de una aplicación de reproductor de acceso remoto holográfica personalizada, puede crear una aplicación personalizada capaz de mostrar [vistas envolventes](app-views.md) desde en una máquina remota de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="33890-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="33890-110">En este artículo se describe cómo se puede lograr esto.</span><span class="sxs-lookup"><span data-stu-id="33890-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="33890-111">Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="33890-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="33890-112">Un reproductor remoto holográfica permite a la aplicación mostrar el contenido holográfica [representado](rendering.md) en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema.</span><span class="sxs-lookup"><span data-stu-id="33890-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="33890-113">Una aplicación de reproductor de comunicación remota holográfica transmite datos de entrada a una aplicación remota de Holographic Remoting y recibe una vista envolvente como flujo de audio y vídeo.</span><span class="sxs-lookup"><span data-stu-id="33890-113">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="33890-114">La conexión se realiza mediante Wi-Fi estándar.</span><span class="sxs-lookup"><span data-stu-id="33890-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="33890-115">Para crear una aplicación de reproductor, usará un paquete NuGet para agregar la comunicación remota holográfica a la aplicación para UWP y escribir código para controlar la conexión y mostrar una vista envolvente.</span><span class="sxs-lookup"><span data-stu-id="33890-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="33890-116">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="33890-116">Prerequisites</span></span>

<span data-ttu-id="33890-117">Un buen punto de partida es una aplicación UWP basada en DirectX que ya tiene como destino la API de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="33890-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="33890-118">Para obtener más información, vea [Introducción al desarrollo de DirectX](directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="33890-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="33890-119">Si no tiene una aplicación existente y desea comenzar desde el principio, la [ C++ plantilla de proyecto Holographic](creating-a-holographic-directx-project.md) es un buen punto de partida.</span><span class="sxs-lookup"><span data-stu-id="33890-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="33890-120">Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span><span class="sxs-lookup"><span data-stu-id="33890-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="33890-121">El uso de un [Apartamento de un solo subproceso](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) es compatible, pero puede dar lugar a un rendimiento poco óptimo y posiblemente a la reproducción.</span><span class="sxs-lookup"><span data-stu-id="33890-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="33890-122">Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un apartamento multiproceso es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="33890-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="33890-123">Obtención del paquete NuGet de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="33890-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="33890-124">Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="33890-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="33890-125">Abra el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="33890-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="33890-126">Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="33890-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="33890-127">En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="33890-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="33890-128">Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="33890-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="33890-129">Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="33890-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="33890-130">El siguiente cuadro de diálogo que aparece es el contrato de licencia.</span><span class="sxs-lookup"><span data-stu-id="33890-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="33890-131">Haga clic en **acepto para aceptar el contrato de licencia** .</span><span class="sxs-lookup"><span data-stu-id="33890-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="33890-132">La ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro del paquete NuGet contiene documentación detallada para la API expuesta por la comunicación remota holográfica.</span><span class="sxs-lookup"><span data-stu-id="33890-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="33890-133">Modificar el paquete. appxmanifest de la aplicación</span><span class="sxs-lookup"><span data-stu-id="33890-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="33890-134">Para que la aplicación tenga en cuenta el Microsoft. Holographic. AppRemoting. dll agregado por el paquete de NuGet, es necesario realizar los siguientes pasos en el proyecto:</span><span class="sxs-lookup"><span data-stu-id="33890-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="33890-135">En el Explorador de soluciones haga clic con el botón derecho en el archivo **Package. appxmanifest** y seleccione **abrir con.** ..</span><span class="sxs-lookup"><span data-stu-id="33890-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="33890-136">Seleccione **Editor XML (texto)** y haga clic en Aceptar.</span><span class="sxs-lookup"><span data-stu-id="33890-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="33890-137">Agregue las líneas siguientes al archivo y guárdela</span><span class="sxs-lookup"><span data-stu-id="33890-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="33890-138">Crear el contexto del reproductor</span><span class="sxs-lookup"><span data-stu-id="33890-138">Create the player context</span></span>

<span data-ttu-id="33890-139">Como primer paso, la aplicación debe crear un contexto de reproductor.</span><span class="sxs-lookup"><span data-stu-id="33890-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="33890-140">Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="33890-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="33890-141">Esto se realiza durante la creación del contexto del reproductor.</span><span class="sxs-lookup"><span data-stu-id="33890-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="33890-142">Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto del reproductor puede producir un comportamiento inesperado.</span><span class="sxs-lookup"><span data-stu-id="33890-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="33890-143">El enfoque recomendado es crear el contexto del reproductor tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="33890-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="33890-144">Nunca mezcle objetos creados o recuperados a través de una API de realidad mixta de Windows antes de la llamada a ```PlayerContext::Create``` con objetos creados o recuperados después.</span><span class="sxs-lookup"><span data-stu-id="33890-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="33890-145">A continuación, se puede crear el HolographicSpace llamando a [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="33890-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="33890-146">Conexión a la aplicación remota</span><span class="sxs-lookup"><span data-stu-id="33890-146">Connect to the remote app</span></span>

<span data-ttu-id="33890-147">Una vez que la aplicación de reproducción está lista para la representación de contenido, se puede establecer una conexión con la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="33890-147">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="33890-148">La conexión se puede establecer de una de las siguientes maneras:</span><span class="sxs-lookup"><span data-stu-id="33890-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="33890-149">La aplicación de reproducción que se ejecuta en HoloLens 2 se conecta a la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="33890-149">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="33890-150">La aplicación remota se conecta a la aplicación de reproductor que se ejecuta en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="33890-150">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="33890-151">Para conectarse desde la aplicación de reproducción a la aplicación remota, llame al método ```Connect``` en el contexto del reproductor y especifique el nombre de host y el puerto.</span><span class="sxs-lookup"><span data-stu-id="33890-151">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="33890-152">El puerto predeterminado es **8265**.</span><span class="sxs-lookup"><span data-stu-id="33890-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="33890-153">Al igual que C++con cualquier API de/WinRT ```Connect``` podría producir un WinRT:: hresult_error que debe controlarse.</span><span class="sxs-lookup"><span data-stu-id="33890-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="33890-154">La escucha de las conexiones entrantes en la aplicación del reproductor puede realizarse llamando al método ```Listen```.</span><span class="sxs-lookup"><span data-stu-id="33890-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="33890-155">El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada.</span><span class="sxs-lookup"><span data-stu-id="33890-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="33890-156">El puerto de enlace se usa para el protocolo de enlace inicial.</span><span class="sxs-lookup"><span data-stu-id="33890-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="33890-157">A continuación, los datos se envían a través del puerto de transporte.</span><span class="sxs-lookup"><span data-stu-id="33890-157">The data is then send over the transport port.</span></span> <span data-ttu-id="33890-158">De forma predeterminada, se usan el número de puerto **8265** y **8266** .</span><span class="sxs-lookup"><span data-stu-id="33890-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="33890-159">Controlar eventos relacionados con la conexión</span><span class="sxs-lookup"><span data-stu-id="33890-159">Handling connection related events</span></span>

<span data-ttu-id="33890-160">El ```PlayerContext``` expone tres eventos para supervisar el estado de la conexión.</span><span class="sxs-lookup"><span data-stu-id="33890-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="33890-161">OnConnection: se desencadena cuando se ha establecido correctamente una conexión con la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="33890-161">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="33890-162">OnDisconnection: se desencadena si se termina una conexión establecida o no se pudo establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="33890-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="33890-163">Los valores de ```ConnectionFailureReason``` posibles se documentan en el [archivo](#idl)de ```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="33890-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="33890-164">MyListener: cuando se inicia la escucha de conexiones entrantes.</span><span class="sxs-lookup"><span data-stu-id="33890-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="33890-165">Además, se puede consultar el estado de la conexión utilizando la propiedad ```ConnectionState``` en el contexto del reproductor.</span><span class="sxs-lookup"><span data-stu-id="33890-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="33890-166">Mostrar el marco representado de forma remota</span><span class="sxs-lookup"><span data-stu-id="33890-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="33890-167">Para mostrar el contenido representado de forma remota, llame a ```PlayerContext::BlitRemoteFrame``` mientras representa un [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="33890-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="33890-168">```BlitRemoteFrame``` requiere que el búfer de reserva del HolographicFrame actual esté enlazado como destino de representación.</span><span class="sxs-lookup"><span data-stu-id="33890-168">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="33890-169">El búfer de reserva se puede recibir desde [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) a través de la propiedad [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="33890-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="33890-170">Cuando se llama, ```BlitRemoteFrame``` copia el último fotograma recibido de la aplicación remota en el búfer de reserva del HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="33890-170">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="33890-171">Además, se establece el conjunto de puntos de enfoque si la aplicación remota ha especificado un punto de enfoque durante la representación del marco remoto.</span><span class="sxs-lookup"><span data-stu-id="33890-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="33890-172">```PlayerContext::BlitRemoteFrame``` potencialmente sobrescribe el punto de enfoque para el marco actual.</span><span class="sxs-lookup"><span data-stu-id="33890-172">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="33890-173">Para especificar un punto de enfoque de reserva, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes de ```PlayerContext::BlitRemoteFrame```.</span><span class="sxs-lookup"><span data-stu-id="33890-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="33890-174">Para sobrescribir el punto de enfoque remoto, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) después de ```PlayerContext::BlitRemoteFrame```.</span><span class="sxs-lookup"><span data-stu-id="33890-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="33890-175">Si se ejecuta correctamente, ```BlitRemoteFrame``` devuelve ```BlitResult::Success_Color```.</span><span class="sxs-lookup"><span data-stu-id="33890-175">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="33890-176">En caso contrario, devuelve el motivo del error:</span><span class="sxs-lookup"><span data-stu-id="33890-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="33890-177">```BlitResult::Failed_NoRemoteFrameAvailable```: error porque no hay ningún marco remoto disponible.</span><span class="sxs-lookup"><span data-stu-id="33890-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="33890-178">```BlitResult::Failed_NoCamera```: error porque no hay ninguna cámara presente.</span><span class="sxs-lookup"><span data-stu-id="33890-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="33890-179">```BlitResult::Failed_RemoteFrameTooOld```: error porque el marco remoto es demasiado antiguo (consulte la propiedad PlayerContext:: BlitRemoteFrameTimeout).</span><span class="sxs-lookup"><span data-stu-id="33890-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="33890-180">A partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0) , es posible que un reproductor personalizado use la reproyección de profundidad mediante la comunicación remota de Holographic.</span><span class="sxs-lookup"><span data-stu-id="33890-180">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="33890-181">```BlitResult``` también puede devolver ```BlitResult::Success_Color_Depth``` en las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="33890-181">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="33890-182">La aplicación remota ha confirmado un búfer de profundidad a través de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="33890-182">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="33890-183">La aplicación de reproductor personalizada ha enlazado un búfer de profundidad válido antes de llamar a ```BlitRemoteFrame```.</span><span class="sxs-lookup"><span data-stu-id="33890-183">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="33890-184">Si se cumplen estas condiciones ```BlitRemoteFrame``` convertirá la profundidad remota en el búfer de profundidad local enlazado actualmente.</span><span class="sxs-lookup"><span data-stu-id="33890-184">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="33890-185">Después, puede representar contenido local adicional que tendrá una intersección de profundidad con el contenido representado remoto.</span><span class="sxs-lookup"><span data-stu-id="33890-185">You can then render additional local content which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="33890-186">Además, puede confirmar el búfer de profundidad local a través de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) en el reproductor personalizado para tener una reproyección de profundidad para el contenido representado de forma local y remota.</span><span class="sxs-lookup"><span data-stu-id="33890-186">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="33890-187">Consulte [reproyección de profundidad](hologram-stability.md#reprojection) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="33890-187">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="33890-188">Modo de transformación de proyección</span><span class="sxs-lookup"><span data-stu-id="33890-188">Projection Transform Mode</span></span>

<span data-ttu-id="33890-189">Un problema que se produce al usar la reproyección de profundidad a través de la comunicación remota de Holographic es que el contenido remoto se puede representar con una transformación de proyección diferente que el contenido local que representa directamente la aplicación de reproductor personalizada.</span><span class="sxs-lookup"><span data-stu-id="33890-189">One problem which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="33890-190">Un caso de uso común es especificar valores diferentes para el plano Near y Far (a través de [HolographicCamera:: SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) y [HolographicCamera:: SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) en el lado del reproductor y en el lado remoto.</span><span class="sxs-lookup"><span data-stu-id="33890-190">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="33890-191">En este caso, no está claro si la transformación de proyección en el lado del reproductor debe reflejar las distancias de plano Near/Far remoto o las locales.</span><span class="sxs-lookup"><span data-stu-id="33890-191">In this case it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="33890-192">A partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0) , puede controlar el modo de transformación de proyección a través de ```PlayerContext::ProjectionTransformConfig```.</span><span class="sxs-lookup"><span data-stu-id="33890-192">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="33890-193">Los valores admitidos son:</span><span class="sxs-lookup"><span data-stu-id="33890-193">Supported values are:</span></span>

- <span data-ttu-id="33890-194">```Local``` - [HolographicCameraPose::P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) devuelve una transformación de proyección que refleja las distancias de plano Near/Far establecidas por la aplicación de reproductor personalizada en el HolographicCamera.</span><span class="sxs-lookup"><span data-stu-id="33890-194">```Local``` - [HolographicCameraPose::ProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="33890-195">la transformación de proyección de ```Remote``` refleja las distancias de plano Near y Far especificadas por la aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="33890-195">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="33890-196">```Merged``` las distancias de plano Near y Far desde la aplicación remota y la aplicación de reproductor personalizada se combinan.</span><span class="sxs-lookup"><span data-stu-id="33890-196">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="33890-197">De forma predeterminada, esto se realiza tomando el mínimo de las distancias de plano cercanos y el máximo de las distancias de plano lejano.</span><span class="sxs-lookup"><span data-stu-id="33890-197">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="33890-198">En caso de que se invierta el lado remoto o el local, por ejemplo, < Near, se voltean las distancias de plano Near/Far remoto.</span><span class="sxs-lookup"><span data-stu-id="33890-198">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <a name="optional-set-blitremoteframetimeout"></a><span data-ttu-id="33890-199">Opcional: establecer BlitRemoteFrameTimeout<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="33890-199">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="33890-200">```PlayerContext::BlitRemoteFrameTimeout``` se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="33890-200">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="33890-201">La propiedad ```PlayerContext::BlitRemoteFrameTimeout``` especifica la cantidad de tiempo que se reutiliza un marco remoto si no se recibe un nuevo marco remoto.</span><span class="sxs-lookup"><span data-stu-id="33890-201">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="33890-202">Un caso de uso común es habilitar el tiempo de espera de BlitRemoteFrame para mostrar una pantalla en blanco si no se recibe ningún fotograma nuevo durante un período de tiempo determinado.</span><span class="sxs-lookup"><span data-stu-id="33890-202">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="33890-203">Cuando está habilitado, el tipo de valor devuelto del método ```BlitRemoteFrame``` también puede usarse para cambiar a un contenido de reserva representado localmente.</span><span class="sxs-lookup"><span data-stu-id="33890-203">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="33890-204">Para habilitar el tiempo de espera, establezca el valor de la propiedad en una duración igual o superior a 100 ms.</span><span class="sxs-lookup"><span data-stu-id="33890-204">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="33890-205">Para deshabilitar el tiempo de espera, establezca la propiedad en cero Duration.</span><span class="sxs-lookup"><span data-stu-id="33890-205">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="33890-206">Si el tiempo de espera está habilitado y no se recibe ningún marco remoto durante el tiempo establecido, BlitRemoteFrame producirá un error y devolverá ```Failed_RemoteFrameTooOld``` hasta que se reciba un nuevo marco remoto.</span><span class="sxs-lookup"><span data-stu-id="33890-206">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="33890-207">Opcional: obtener estadísticas sobre el último marco remoto</span><span class="sxs-lookup"><span data-stu-id="33890-207">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="33890-208">Para diagnosticar problemas de rendimiento o de red, se pueden recuperar estadísticas sobre el último marco remoto a través de la propiedad ```PlayerContext::LastFrameStatistics```.</span><span class="sxs-lookup"><span data-stu-id="33890-208">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="33890-209">Las estadísticas se actualizan durante la llamada a [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="33890-209">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="33890-210">Para obtener más información, consulte la documentación de ```PlayerFrameStatistics``` en el [archivo](#idl)de ```Microsoft.Holographic.AppRemoting.idl```.</span><span class="sxs-lookup"><span data-stu-id="33890-210">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="33890-211">Opcional: canales de datos personalizados</span><span class="sxs-lookup"><span data-stu-id="33890-211">Optional: Custom data channels</span></span>

<span data-ttu-id="33890-212">Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida.</span><span class="sxs-lookup"><span data-stu-id="33890-212">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="33890-213">Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="33890-213">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="33890-214">Consulta también</span><span class="sxs-lookup"><span data-stu-id="33890-214">See Also</span></span>
* [<span data-ttu-id="33890-215">Escritura de una aplicación remota holográfica Remoting</span><span class="sxs-lookup"><span data-stu-id="33890-215">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="33890-216">Canales de datos personalizados de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="33890-216">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="33890-217">Establecimiento de una conexión segura con Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="33890-217">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="33890-218">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="33890-218">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="33890-219">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="33890-219">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="33890-220">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="33890-220">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
