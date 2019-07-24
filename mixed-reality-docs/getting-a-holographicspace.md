---
title: Obtención de un HolographicSpace
description: Explica la API de HolographicSpace, un concepto básico de representación de Holographic y entrada espacial.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrada espacial, representación, cadena de intercambio, marco holográfica, bucle de actualización, bucle de juego, marco de referencia, localización, código de ejemplo, tutorial
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525448"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="faeb5-104">Obtención de un HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="faeb5-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="faeb5-105">La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> es su portal en el mundo holográfica.</span><span class="sxs-lookup"><span data-stu-id="faeb5-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="faeb5-106">Controla la representación envolvente, proporciona datos de la cámara y proporciona acceso a las API de razonamiento espacial.</span><span class="sxs-lookup"><span data-stu-id="faeb5-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="faeb5-107">Creará una para el identificador de usuario de la aplicación de <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">UWP o la</a> aplicación Win32.</span><span class="sxs-lookup"><span data-stu-id="faeb5-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="faeb5-108">Configuración del espacio holográfica</span><span class="sxs-lookup"><span data-stu-id="faeb5-108">Set up the holographic space</span></span>

<span data-ttu-id="faeb5-109">La creación del objeto de espacio holográfica es el primer paso para crear una aplicación de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="faeb5-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="faeb5-110">Las aplicaciones tradicionales de Windows se representan en una cadena de intercambio de Direct3D creada para la ventana principal de la vista de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="faeb5-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="faeb5-111">Esta cadena de intercambio se muestra en una pizarra en la interfaz de usuario holográfica.</span><span class="sxs-lookup"><span data-stu-id="faeb5-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="faeb5-112">Para hacer que la vista de la aplicación sea holográfica en lugar de una pizarra 2D, cree un espacio holográfica para su ventana principal en lugar de una cadena de intercambio.</span><span class="sxs-lookup"><span data-stu-id="faeb5-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="faeb5-113">La presentación de tramas holográficas creadas por este espacio holográfica coloca la aplicación en el modo de representación de pantalla completa.</span><span class="sxs-lookup"><span data-stu-id="faeb5-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="faeb5-114">En el caso de una **aplicación para UWP** a partir [de la *plantilla holográfica DirectX 11 (Windows universal)* ](creating-a-holographic-directx-project.md), busque este código en el método **SetWindow** en AppView. cpp:</span><span class="sxs-lookup"><span data-stu-id="faeb5-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="faeb5-115">En el caso de una **aplicación de Win32** que se [inicie en el ejemplo *BasicHologram* de Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), consulte **App:: CreateWindowAndHolographicSpace** para obtener un ejemplo de cómo crear un HWND y, después, convertirlo en un HWND envolvente mediante la creación de un asociado <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank"> HolographicSpace</a>:</span><span class="sxs-lookup"><span data-stu-id="faeb5-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
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

<span data-ttu-id="faeb5-116">Ahora que ha obtenido un HolographicSpace para su HWND de UWP o HWND de Win32, usará ese HolographicSpace para controlar las cámaras holográficas, crear sistemas de coordenadas y realizar la representación holográfica.</span><span class="sxs-lookup"><span data-stu-id="faeb5-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="faeb5-117">El espacio holográfica actual se usa en varios lugares de la plantilla de DirectX:</span><span class="sxs-lookup"><span data-stu-id="faeb5-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="faeb5-118">La clase **DeviceResources** debe obtener cierta información del objeto HolographicSpace para crear el dispositivo Direct3D.</span><span class="sxs-lookup"><span data-stu-id="faeb5-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="faeb5-119">Este es el identificador del adaptador de DXGI asociado a la pantalla holográfica.</span><span class="sxs-lookup"><span data-stu-id="faeb5-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="faeb5-120">La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa el dispositivo Direct3D 11 de la aplicación para crear y administrar recursos basados en dispositivos como, por ejemplo, los búferes de reserva de cada cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="faeb5-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="faeb5-121">Si le interesa ver lo que hace esta función en el capó, la encontrará en DeviceResources. cpp.</span><span class="sxs-lookup"><span data-stu-id="faeb5-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="faeb5-122">La función **DeviceResources:: InitializeUsingHolographicSpace** muestra cómo obtener el adaptador buscando el LUID y cómo elegir un adaptador predeterminado cuando no se especifica ningún adaptador preferido.</span><span class="sxs-lookup"><span data-stu-id="faeb5-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="faeb5-123">La clase principal de la aplicación usa el espacio holográfica de **AppView:: SetWindow** o **App:: CreateWindowAndHolographicSpace** para las actualizaciones y la representación.</span><span class="sxs-lookup"><span data-stu-id="faeb5-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="faeb5-124">Aunque en las secciones siguientes se mencionan los nombres de función de la plantilla como **AppView:: SetWindow** que suponen que se ha iniciado desde la plantilla de aplicación de UWP de Holographic, los fragmentos de código que se ven se aplicarán igualmente a través de aplicaciones de UWP y Win32.</span><span class="sxs-lookup"><span data-stu-id="faeb5-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="faeb5-125">A continuación, profundizaremos en el proceso de configuración que **SetHolographicSpace** es responsable de en la clase AppMain.</span><span class="sxs-lookup"><span data-stu-id="faeb5-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="faeb5-126">Suscripción a eventos de cámara, creación y eliminación de recursos de la cámara</span><span class="sxs-lookup"><span data-stu-id="faeb5-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="faeb5-127">El contenido holográfica de la aplicación vive en su espacio holográfica y se ve a través de una o varias cámaras holográfica que representan perspectivas diferentes en la escena.</span><span class="sxs-lookup"><span data-stu-id="faeb5-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="faeb5-128">Ahora que tiene el espacio holográfica, puede recibir datos para cámaras holográficas.</span><span class="sxs-lookup"><span data-stu-id="faeb5-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="faeb5-129">La aplicación debe responder a los eventos de **CameraAdded** mediante la creación de los recursos específicos de esa cámara, como la vista de destino de representación del búfer de reserva.</span><span class="sxs-lookup"><span data-stu-id="faeb5-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="faeb5-130">Puede ver este código en la función **DeviceResources:: SetHolographicSpace** , llamada por **AppView:: SetWindow** antes de que la aplicación cree cualquier trama holográfica:</span><span class="sxs-lookup"><span data-stu-id="faeb5-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="faeb5-131">La aplicación también debe responder a los eventos de **CameraRemoved** mediante la liberación de los recursos que se crearon para esa cámara.</span><span class="sxs-lookup"><span data-stu-id="faeb5-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="faeb5-132">De **DeviceResources:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="faeb5-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="faeb5-133">Los controladores de eventos deben completar algún trabajo para que la representación holográfica fluya sin problemas y para que la aplicación se pueda representar en absoluto.</span><span class="sxs-lookup"><span data-stu-id="faeb5-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="faeb5-134">Lea el código y los comentarios de los detalles: puede buscar **OnCameraAdded** y **OnCameraRemoved** en la clase principal para entender cómo controla la asignación **m_cameraResources** mediante **DeviceResources**.</span><span class="sxs-lookup"><span data-stu-id="faeb5-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="faeb5-135">En este momento, nos centramos en AppMain y en la configuración que permite que la aplicación Conozca las cámaras holográficas.</span><span class="sxs-lookup"><span data-stu-id="faeb5-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="faeb5-136">Teniendo esto en cuenta, es importante tener en cuenta los dos requisitos siguientes:</span><span class="sxs-lookup"><span data-stu-id="faeb5-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="faeb5-137">En el caso del controlador de eventos **CameraAdded** , la aplicación puede trabajar de forma asincrónica para finalizar la creación de recursos y la carga de recursos para la nueva cámara holográfica.</span><span class="sxs-lookup"><span data-stu-id="faeb5-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="faeb5-138">Las aplicaciones que tardan más de un fotograma para completar este trabajo deben solicitar un aplazamiento y completar el aplazamiento después de cargarse de forma asincrónica. una [tarea PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) se puede usar para realizar el trabajo asincrónico.</span><span class="sxs-lookup"><span data-stu-id="faeb5-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="faeb5-139">La aplicación debe asegurarse de que esté lista para representarse en esa cámara inmediatamente cuando salga del controlador de eventos o cuando complete el aplazamiento.</span><span class="sxs-lookup"><span data-stu-id="faeb5-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="faeb5-140">Salir del controlador de eventos o completar el aplazamiento indica al sistema que la aplicación ya está lista para recibir tramas holográficas con esa cámara incluida.</span><span class="sxs-lookup"><span data-stu-id="faeb5-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="faeb5-141">Cuando la aplicación recibe un evento **CameraRemoved** , debe liberar todas las referencias al búfer de reserva y salir de la función inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="faeb5-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="faeb5-142">Esto incluye las vistas de destino de representación y cualquier otro recurso que pueda contener una referencia a [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span><span class="sxs-lookup"><span data-stu-id="faeb5-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="faeb5-143">La aplicación también debe asegurarse de que el búfer de reserva no está asociado como destino de representación, como se muestra en **CameraResources:: ReleaseResourcesForBackBuffer**.</span><span class="sxs-lookup"><span data-stu-id="faeb5-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="faeb5-144">Para ayudar a acelerar las cosas, la aplicación puede liberar el búfer de reserva y, a continuación, iniciar una tarea para completar de forma asincrónica cualquier otro trabajo que sea necesario para anular la cámara.</span><span class="sxs-lookup"><span data-stu-id="faeb5-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="faeb5-145">La plantilla de aplicación holográfica incluye una tarea PPL que puede usar con este fin.</span><span class="sxs-lookup"><span data-stu-id="faeb5-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="faeb5-146">Si desea determinar cuándo se muestra una cámara agregada o quitada en el fotograma, use las propiedades **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) y [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .</span><span class="sxs-lookup"><span data-stu-id="faeb5-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="faeb5-147">Creación de un marco de referencia para el contenido holográfica</span><span class="sxs-lookup"><span data-stu-id="faeb5-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="faeb5-148">El contenido de la aplicación debe colocarse en un [sistema de coordenadas espaciales](coordinate-systems-in-directx.md) que se va a representar en el HolographicSpace.</span><span class="sxs-lookup"><span data-stu-id="faeb5-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="faeb5-149">El sistema proporciona dos fotogramas principales de referencia que puede usar para establecer un sistema de coordenadas para los hologramas.</span><span class="sxs-lookup"><span data-stu-id="faeb5-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="faeb5-150">Hay dos tipos de fotogramas de referencia en Windows Holographic: los fotogramas de referencia conectados al dispositivo y hacen referencia a fotogramas que permanecen estacionarios a medida que el dispositivo se mueve por el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="faeb5-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="faeb5-151">De forma predeterminada, la plantilla de aplicación holográfica usa un marco de referencia estacional. Esta es una de las formas más sencillas de representar hologramas de bloque mundial.</span><span class="sxs-lookup"><span data-stu-id="faeb5-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="faeb5-152">Los fotogramas de referencia estacionarios están diseñados para estabilizar las posiciones cerca de la ubicación actual del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="faeb5-153">Esto significa que las coordenadas más allá del dispositivo pueden desplazarse ligeramente con respecto al entorno del usuario, ya que el dispositivo aprende más sobre el espacio que lo rodea.</span><span class="sxs-lookup"><span data-stu-id="faeb5-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="faeb5-154">Hay dos maneras de crear un marco estacionario de referencia: adquirir el sistema de coordenadas de la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)o usar el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="faeb5-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="faeb5-155">Si va a crear una aplicación de Windows Mixed Reality para auriculares envolventes, el punto de partida recomendado es la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que también proporciona información acerca de las capacidades del casco envolvente que gasta el jugador.</span><span class="sxs-lookup"><span data-stu-id="faeb5-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="faeb5-156">Aquí se muestra cómo usar el valor predeterminado de <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span><span class="sxs-lookup"><span data-stu-id="faeb5-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="faeb5-157">El localizador espacial representa el dispositivo de Windows Mixed Reality y realiza un seguimiento del movimiento del dispositivo y proporciona sistemas de coordenadas que se pueden entender en relación con su ubicación.</span><span class="sxs-lookup"><span data-stu-id="faeb5-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="faeb5-158">Desde **AppMain:: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="faeb5-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="faeb5-159">Cree el marco de referencia estacionario una vez cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="faeb5-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="faeb5-160">Esto es análogo a definir un sistema de coordenadas universal, con el origen colocado en la posición del dispositivo cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="faeb5-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="faeb5-161">Este fotograma de referencia no se mueve con el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="faeb5-162">Desde **AppMain:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="faeb5-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="faeb5-163">Todos los marcos de referencia están alineados con la gravedad, lo que significa que el eje y apunta "hacia arriba" con respecto al entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="faeb5-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="faeb5-164">Puesto que Windows usa sistemas de coordenadas "zurdos", la dirección del eje – z coincide con la dirección "hacia delante" a la que se enfrenta el dispositivo cuando se crea el fotograma de referencia.</span><span class="sxs-lookup"><span data-stu-id="faeb5-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="faeb5-165">Cuando la aplicación requiere una ubicación precisa de hologramas individuales, use un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> para anclar el holograma individual en una posición del mundo real.</span><span class="sxs-lookup"><span data-stu-id="faeb5-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="faeb5-166">Por ejemplo, use un delimitador espacial cuando el usuario indique que un punto debe ser de especial interés.</span><span class="sxs-lookup"><span data-stu-id="faeb5-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="faeb5-167">Las posiciones de anclaje no se desplazan, pero se pueden ajustar.</span><span class="sxs-lookup"><span data-stu-id="faeb5-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="faeb5-168">De forma predeterminada, cuando se ajusta un delimitador, facilita su posición en lugar de los próximos fotogramas después de que se haya realizado la corrección.</span><span class="sxs-lookup"><span data-stu-id="faeb5-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="faeb5-169">En función de la aplicación, cuando esto sucede, es posible que desee controlar el ajuste de manera diferente (por ejemplo, si lo aplaza hasta que el holograma esté fuera de la vista).</span><span class="sxs-lookup"><span data-stu-id="faeb5-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="faeb5-170">La propiedad <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> y los eventos <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> habilitan estas personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="faeb5-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="faeb5-171">Responder a los eventos de búsqueda modificada</span><span class="sxs-lookup"><span data-stu-id="faeb5-171">Respond to locatability changed events</span></span>

<span data-ttu-id="faeb5-172">La representación de hologramas con bloqueo mundial requiere que el dispositivo pueda localizarse en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="faeb5-173">Esto puede no ser siempre posible debido a las condiciones del entorno, y si es así, el usuario puede esperar una indicación visual de la interrupción del seguimiento.</span><span class="sxs-lookup"><span data-stu-id="faeb5-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="faeb5-174">Esta indicación visual se debe representar mediante fotogramas de referencia conectados al dispositivo, en lugar de separarse del mundo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="faeb5-175">La aplicación puede solicitar recibir una notificación si se interrumpe el seguimiento por cualquier motivo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="faeb5-176">Regístrese en el evento LocatabilityChanged para detectar cuándo cambia la capacidad del dispositivo de localizarse en el mundo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="faeb5-177">Desde **AppMain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="faeb5-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="faeb5-178">A continuación, use este evento para determinar cuándo no se pueden representar los hologramas estacionales en el mundo.</span><span class="sxs-lookup"><span data-stu-id="faeb5-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="faeb5-179">Vea también</span><span class="sxs-lookup"><span data-stu-id="faeb5-179">See also</span></span>
* [<span data-ttu-id="faeb5-180">Representación en DirectX</span><span class="sxs-lookup"><span data-stu-id="faeb5-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="faeb5-181">Sistemas de coordenadas de DirectX</span><span class="sxs-lookup"><span data-stu-id="faeb5-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
