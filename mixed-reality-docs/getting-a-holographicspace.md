---
title: Obtener un HolographicSpace
description: Explica la API HolographicSpace, un concepto básico para la representación holográfica y entrada espacial.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, espacial, de entrada de representación, intercambiar la cadena, marco holográfica, bucle de actualización, bucle de juego, marco de referencia, locatability, código de ejemplo, tutorial
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605780"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="52178-104">Obtener un HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="52178-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="52178-105">El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> clase es su portal hacia el mundo holográfico.</span><span class="sxs-lookup"><span data-stu-id="52178-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="52178-106">Controla la representación envolvente, proporciona datos de la cámara y proporciona acceso a espacial razonamiento de las API.</span><span class="sxs-lookup"><span data-stu-id="52178-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="52178-107">Creará una para la aplicación UWP <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> o HWND de la aplicación Win32.</span><span class="sxs-lookup"><span data-stu-id="52178-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="52178-108">Configura el espacio holográfico</span><span class="sxs-lookup"><span data-stu-id="52178-108">Set up the holographic space</span></span>

<span data-ttu-id="52178-109">Crear el objeto de espacio holográfica es el primer paso para hacer que su aplicación de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="52178-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="52178-110">Las aplicaciones tradicionales de Windows se representan en una cadena de intercambio de Direct3D creada para la ventana principal de su vista de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="52178-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="52178-111">Esta cadena de intercambio se muestra en una pizarra en la interfaz de usuario holográfica.</span><span class="sxs-lookup"><span data-stu-id="52178-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="52178-112">Para hacer que la vista de la aplicación holographic en lugar de una pizarra 2D, cree un espacio holográfico para su ventana principal en lugar de una cadena de intercambio.</span><span class="sxs-lookup"><span data-stu-id="52178-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="52178-113">Presentar holográficas marcos creados por este espacio holográfica, la aplicación pone en modo de representación de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="52178-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="52178-114">Para un **aplicación para UWP** [a partir de la *plantilla de aplicación de 11 holográfica DirectX (Windows Universal)*](creating-a-holographic-directx-project.md), busque este código en el **SetWindow** método AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="52178-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="52178-115">Para un **aplicación Win32** [a partir de la *BasicHologram* ejemplo Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), examine **App::CreateWindowAndHolographicSpace** para un ejemplo de cómo crear un HWND y, a continuación, convertirlo en un HWND envolvente mediante la creación de un asociado <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="52178-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="52178-116">Ahora que ha obtenido un HolographicSpace para la CoreWindow de UWP o HWND Win32, usará ese HolographicSpace controlar cámaras holográficas, crear sistemas de coordenadas y no la representación holográfica.</span><span class="sxs-lookup"><span data-stu-id="52178-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="52178-117">El espacio holográfico actual se usa en varios lugares de la plantilla de DirectX:</span><span class="sxs-lookup"><span data-stu-id="52178-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="52178-118">El **DeviceResources** clase debe obtener cierta información del objeto HolographicSpace con el fin de crear el dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="52178-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="52178-119">Este es el identificador de adaptador DXGI asociado a la pantalla holográfica.</span><span class="sxs-lookup"><span data-stu-id="52178-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="52178-120">El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> clase usa el dispositivo de la aplicación Direct3D 11 para crear y administrar los recursos basados en el dispositivo, como los búferes de reserva para cada cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="52178-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="52178-121">Si está interesado en ver lo que hace esta función en segundo plano, se encontrará en DeviceResources.cpp.</span><span class="sxs-lookup"><span data-stu-id="52178-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="52178-122">La función **DeviceResources::InitializeUsingHolographicSpace** muestra cómo obtener el adaptador buscando el LUID – y cómo elegir un adaptador de forma predeterminada cuando no se especifica ningún adaptador preferido.</span><span class="sxs-lookup"><span data-stu-id="52178-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="52178-123">Clase principal de la aplicación usa el espacio holográfico desde **AppView::SetWindow** o **App::CreateWindowAndHolographicSpace** para las actualizaciones y la representación.</span><span class="sxs-lookup"><span data-stu-id="52178-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="52178-124">Aunque las secciones siguientes mencionan los nombres de función de la plantilla como **AppView::SetWindow** que se supone que ha iniciado desde la plantilla de aplicación para UWP holográfica, verá los fragmentos de código también se aplicarán en las aplicaciones UWP y Win32.</span><span class="sxs-lookup"><span data-stu-id="52178-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="52178-125">A continuación, analizaremos en profundidad la configuración del proceso que **SetHolographicSpace** es responsable de la clase AppMain.</span><span class="sxs-lookup"><span data-stu-id="52178-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="52178-126">Suscribirse a eventos de cámara, crear y quitar recursos de la cámara</span><span class="sxs-lookup"><span data-stu-id="52178-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="52178-127">Contenido de la aplicación holographic reside en su espacio holográfica y se visualiza a través de una o más cámaras holográficas que representan distintas perspectivas en la escena.</span><span class="sxs-lookup"><span data-stu-id="52178-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="52178-128">Ahora que tiene el espacio holográfico, puede recibir datos para las cámaras holográficas.</span><span class="sxs-lookup"><span data-stu-id="52178-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="52178-129">La aplicación debe responder a **CameraAdded** eventos mediante la creación de todos los recursos que son específicos a tu cámara, tales como el búfer de reserva de procesar la vista de destino.</span><span class="sxs-lookup"><span data-stu-id="52178-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="52178-130">Puede ver este código en el **DeviceResources::SetHolographicSpace** función que llama **AppView::SetWindow** antes de la aplicación crea los fotogramas holográficas:</span><span class="sxs-lookup"><span data-stu-id="52178-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="52178-131">La aplicación también debe responder a **CameraRemoved** eventos mediante la liberación de recursos que se crearon para que la cámara.</span><span class="sxs-lookup"><span data-stu-id="52178-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="52178-132">Desde **DeviceResources::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="52178-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="52178-133">Los controladores de eventos deben completar un trabajo con el fin de mantener la representación holográfica fluir sin problemas, de modo que la aplicación es capaz de representar en absoluto.</span><span class="sxs-lookup"><span data-stu-id="52178-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="52178-134">Leer el código y comentarios para obtener los detalles: puede buscar **OnCameraAdded** y **OnCameraRemoved** en la clase principal para comprender cómo la **m_cameraResources** mapa es controlando **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="52178-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="52178-135">En este momento, nos hemos centrado en AppMain y el programa de instalación que lo hace para habilitar la aplicación saber acerca de las cámaras holográficas.</span><span class="sxs-lookup"><span data-stu-id="52178-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="52178-136">Teniendo esto en mente, es importante tomar nota de los dos requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="52178-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="52178-137">Para el **CameraAdded** controlador de eventos, la aplicación puede trabajar de forma asincrónica para finalizar la creación de recursos y carga de activos para la nueva cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="52178-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="52178-138">Las aplicaciones que tarden más de un marco para completar este trabajo deben solicitar un aplazamiento y completar el aplazamiento después de cargar de forma asincrónica; un [tareas PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) puede utilizarse para realizar trabajo asincrónico.</span><span class="sxs-lookup"><span data-stu-id="52178-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="52178-139">La aplicación debe asegurarse de que está listo para representar a tu cámara inmediatamente cuando sale del controlador de eventos o cuando se completa el aplazamiento.</span><span class="sxs-lookup"><span data-stu-id="52178-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="52178-140">Sale del controlador de eventos o completar el aplazamiento indica al sistema que la aplicación ahora está lista para recibir holográficas marcos con tu cámara incluida.</span><span class="sxs-lookup"><span data-stu-id="52178-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="52178-141">Cuando la aplicación recibe un **CameraRemoved** evento, debe liberar todas las referencias para el búfer de reserva y salir inmediatamente a la función.</span><span class="sxs-lookup"><span data-stu-id="52178-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="52178-142">Esto incluye vistas de destino de representación y cualquier otro recurso que podría contener una referencia a la [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="52178-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="52178-143">La aplicación también debe asegurarse de que el búfer de reserva no se adjunta como un destino de representación, como se muestra en **CameraResources::ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="52178-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="52178-144">Para ayudar a acelerar el proceso a lo largo de, la aplicación puede liberar el búfer de reserva y, a continuación, iniciar una tarea para completar cualquier otro trabajo que es necesario anular tu cámara de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="52178-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="52178-145">La plantilla de aplicación holográfica incluye una tarea PPL que puede usar para este propósito.</span><span class="sxs-lookup"><span data-stu-id="52178-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="52178-146">Si desea determinar cuándo se muestra una cámara agregada o quita en el fotograma, utilice el **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) y [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) propiedades.</span><span class="sxs-lookup"><span data-stu-id="52178-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="52178-147">Crear un marco de referencia para su contenido holográfico</span><span class="sxs-lookup"><span data-stu-id="52178-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="52178-148">Contenido de la aplicación debe estar posicionado en un [del sistema de coordenadas espacial](coordinate-systems-in-directx.md) se represente en el HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="52178-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="52178-149">El sistema proporciona dos principales marcos de referencia que puede usar para establecer un sistema de coordenadas para las hologramas.</span><span class="sxs-lookup"><span data-stu-id="52178-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="52178-150">Hay dos tipos de fotogramas de referencia de Windows Holographic: hacer referencia a marcos asociados al dispositivo y referencia que se mantenga estacionario cuando el dispositivo se mueve a través del entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="52178-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="52178-151">La plantilla de aplicación holográfica usa un marco estático de referencia de forma predeterminada; Esta es una de las maneras más sencillas de representar hologramas bloqueado por el mundo.</span><span class="sxs-lookup"><span data-stu-id="52178-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="52178-152">Marcos de referencia fijos están diseñados para estabilizar posiciones cerca de la ubicación del dispositivo actual.</span><span class="sxs-lookup"><span data-stu-id="52178-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="52178-153">Esto significa que se permiten las coordenadas más lejos el dispositivo a desviarse ligeramente con respecto a la del entorno del usuario, como el dispositivo aprende más sobre el espacio alrededor de ella.</span><span class="sxs-lookup"><span data-stu-id="52178-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="52178-154">Hay dos maneras de crear un marco estático de referencia: adquirir el sistema de coordenadas de la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), o use el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="52178-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="52178-155">Si va a crear una aplicación de Windows Mixed Reality para inmersivos, el punto de partida recomendado es el [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que también proporciona información acerca de las capacidades de los auriculares envolventes adosadas al Reproductor.</span><span class="sxs-lookup"><span data-stu-id="52178-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="52178-156">Aquí, se muestra cómo usar el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="52178-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="52178-157">El localizador espacial representa el dispositivo Windows Mixed Reality y realiza un seguimiento del movimiento del dispositivo y proporciona los sistemas de coordenadas que pueda entender con respecto a su ubicación.</span><span class="sxs-lookup"><span data-stu-id="52178-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="52178-158">Desde **AppMain::OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="52178-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="52178-159">Cree una vez el marco de referencia estacionario cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="52178-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="52178-160">Esto es análogo a la definición de un sistema de coordenadas del mundo, con el origen que se coloca en la posición del dispositivo cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="52178-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="52178-161">Este marco de referencia no se mueve con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="52178-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="52178-162">Desde **AppMain::SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="52178-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="52178-163">Todos los marcos de referencia son gravedad alineada, lo que significa que el eje y puntos de "up" en relación con el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="52178-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="52178-164">Puesto que Windows usa "diestros" sistemas de coordenadas, la dirección del eje z: coincide con la dirección "forward" el dispositivo está orientado a cuando se crea el marco de referencia.</span><span class="sxs-lookup"><span data-stu-id="52178-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="52178-165">Si la aplicación requiere la posición precisa de hologramas individuales, utilice un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> a delimitar el holograma individual a una posición en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="52178-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="52178-166">Por ejemplo, utilice un delimitador espacial cuando el usuario indica que un punto de ser de especial interés.</span><span class="sxs-lookup"><span data-stu-id="52178-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="52178-167">No desvíen posiciones de delimitador, pero puede ajustarse.</span><span class="sxs-lookup"><span data-stu-id="52178-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="52178-168">De forma predeterminada, cuando se ajusta un delimitador, facilita su posición en su lugar a través de las tramas siguientes después de la corrección se ha producido.</span><span class="sxs-lookup"><span data-stu-id="52178-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="52178-169">Dependiendo de la aplicación, cuando esto sucede puede controlar el ajuste de forma diferente (por ejemplo, aplazarla hasta que el holograma está fuera de la vista).</span><span class="sxs-lookup"><span data-stu-id="52178-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="52178-170">El <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> propiedad y <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> los eventos habilitan estas personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="52178-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="52178-171">Responder a eventos locatability cambiado</span><span class="sxs-lookup"><span data-stu-id="52178-171">Respond to locatability changed events</span></span>

<span data-ttu-id="52178-172">Representación hologramas bloqueado por el mundo requiere que el dispositivo se puede localizar a sí mismo en el mundo.</span><span class="sxs-lookup"><span data-stu-id="52178-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="52178-173">Esto no siempre sea posible debido a condiciones ambientales y, si es así, el usuario puede esperar una indicación visual de la interrupción de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="52178-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="52178-174">Esta indicación visual se debe representar mediante marcos de referencia asociados al dispositivo, en lugar de diseño de fondo a todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="52178-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="52178-175">Aplicación puede solicitar que se le notifique si el seguimiento se interrumpe por algún motivo.</span><span class="sxs-lookup"><span data-stu-id="52178-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="52178-176">Registrarse para que el evento LocatabilityChanged detectar cuándo la capacidad del dispositivo a sí mismo buscar en los cambios del mundo.</span><span class="sxs-lookup"><span data-stu-id="52178-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="52178-177">Desde **AppMain::SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="52178-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="52178-178">A continuación, use este evento para determinar cuándo no se puede representar hologramas estacionarios a todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="52178-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="52178-179">Vea también</span><span class="sxs-lookup"><span data-stu-id="52178-179">See also</span></span>
* [<span data-ttu-id="52178-180">Representación de DirectX</span><span class="sxs-lookup"><span data-stu-id="52178-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="52178-181">Sistemas de coordenadas en DirectX</span><span class="sxs-lookup"><span data-stu-id="52178-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
