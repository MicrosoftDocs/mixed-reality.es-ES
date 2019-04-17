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
# <a name="getting-a-holographicspace"></a>Obtener un HolographicSpace

El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> clase es su portal hacia el mundo holográfico. Controla la representación envolvente, proporciona datos de la cámara y proporciona acceso a espacial razonamiento de las API. Creará una para la aplicación UWP <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> o HWND de la aplicación Win32.

## <a name="set-up-the-holographic-space"></a>Configura el espacio holográfico

Crear el objeto de espacio holográfica es el primer paso para hacer que su aplicación de Windows Mixed Reality. Las aplicaciones tradicionales de Windows se representan en una cadena de intercambio de Direct3D creada para la ventana principal de su vista de la aplicación. Esta cadena de intercambio se muestra en una pizarra en la interfaz de usuario holográfica. Para hacer que la vista de la aplicación holographic en lugar de una pizarra 2D, cree un espacio holográfico para su ventana principal en lugar de una cadena de intercambio. Presentar holográficas marcos creados por este espacio holográfica, la aplicación pone en modo de representación de pantalla completa.

Para un **aplicación para UWP** [a partir de la *plantilla de aplicación de 11 holográfica DirectX (Windows Universal)*](creating-a-holographic-directx-project.md), busque este código en el **SetWindow** método AppView.cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

Para un **aplicación Win32** [a partir de la *BasicHologram* ejemplo Win32](creating-a-holographic-directx-project.md#creating-a-win32-project), examine **App::CreateWindowAndHolographicSpace** para un ejemplo de cómo crear un HWND y, a continuación, convertirlo en un HWND envolvente mediante la creación de un asociado <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
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

Ahora que ha obtenido un HolographicSpace para la CoreWindow de UWP o HWND Win32, usará ese HolographicSpace controlar cámaras holográficas, crear sistemas de coordenadas y no la representación holográfica. El espacio holográfico actual se usa en varios lugares de la plantilla de DirectX:
* El **DeviceResources** clase debe obtener cierta información del objeto HolographicSpace con el fin de crear el dispositivo Direct3D. Este es el identificador de adaptador DXGI asociado a la pantalla holográfica. El <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> clase usa el dispositivo de la aplicación Direct3D 11 para crear y administrar los recursos basados en el dispositivo, como los búferes de reserva para cada cámara holográfica. Si está interesado en ver lo que hace esta función en segundo plano, se encontrará en DeviceResources.cpp.
* La función **DeviceResources::InitializeUsingHolographicSpace** muestra cómo obtener el adaptador buscando el LUID – y cómo elegir un adaptador de forma predeterminada cuando no se especifica ningún adaptador preferido.
* Clase principal de la aplicación usa el espacio holográfico desde **AppView::SetWindow** o **App::CreateWindowAndHolographicSpace** para las actualizaciones y la representación.

>[!NOTE]
>Aunque las secciones siguientes mencionan los nombres de función de la plantilla como **AppView::SetWindow** que se supone que ha iniciado desde la plantilla de aplicación para UWP holográfica, verá los fragmentos de código también se aplicarán en las aplicaciones UWP y Win32.

A continuación, analizaremos en profundidad la configuración del proceso que **SetHolographicSpace** es responsable de la clase AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Suscribirse a eventos de cámara, crear y quitar recursos de la cámara

Contenido de la aplicación holographic reside en su espacio holográfica y se visualiza a través de una o más cámaras holográficas que representan distintas perspectivas en la escena. Ahora que tiene el espacio holográfico, puede recibir datos para las cámaras holográficas.

La aplicación debe responder a **CameraAdded** eventos mediante la creación de todos los recursos que son específicos a tu cámara, tales como el búfer de reserva de procesar la vista de destino. Puede ver este código en el **DeviceResources::SetHolographicSpace** función que llama **AppView::SetWindow** antes de la aplicación crea los fotogramas holográficas:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

La aplicación también debe responder a **CameraRemoved** eventos mediante la liberación de recursos que se crearon para que la cámara.

Desde **DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Los controladores de eventos deben completar un trabajo con el fin de mantener la representación holográfica fluir sin problemas, de modo que la aplicación es capaz de representar en absoluto. Leer el código y comentarios para obtener los detalles: puede buscar **OnCameraAdded** y **OnCameraRemoved** en la clase principal para comprender cómo la **m_cameraResources** mapa es controlando **DeviceResources**.

En este momento, nos hemos centrado en AppMain y el programa de instalación que lo hace para habilitar la aplicación saber acerca de las cámaras holográficas. Teniendo esto en mente, es importante tomar nota de los dos requisitos siguientes:

1. Para el **CameraAdded** controlador de eventos, la aplicación puede trabajar de forma asincrónica para finalizar la creación de recursos y carga de activos para la nueva cámara holográfica. Las aplicaciones que tarden más de un marco para completar este trabajo deben solicitar un aplazamiento y completar el aplazamiento después de cargar de forma asincrónica; un [tareas PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) puede utilizarse para realizar trabajo asincrónico. La aplicación debe asegurarse de que está listo para representar a tu cámara inmediatamente cuando sale del controlador de eventos o cuando se completa el aplazamiento. Sale del controlador de eventos o completar el aplazamiento indica al sistema que la aplicación ahora está lista para recibir holográficas marcos con tu cámara incluida.

2. Cuando la aplicación recibe un **CameraRemoved** evento, debe liberar todas las referencias para el búfer de reserva y salir inmediatamente a la función. Esto incluye vistas de destino de representación y cualquier otro recurso que podría contener una referencia a la [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). La aplicación también debe asegurarse de que el búfer de reserva no se adjunta como un destino de representación, como se muestra en **CameraResources::ReleaseResourcesForBackBuffer**. Para ayudar a acelerar el proceso a lo largo de, la aplicación puede liberar el búfer de reserva y, a continuación, iniciar una tarea para completar cualquier otro trabajo que es necesario anular tu cámara de forma asincrónica. La plantilla de aplicación holográfica incluye una tarea PPL que puede usar para este propósito.

>[!NOTE]
>Si desea determinar cuándo se muestra una cámara agregada o quita en el fotograma, utilice el **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) y [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) propiedades.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Crear un marco de referencia para su contenido holográfico

Contenido de la aplicación debe estar posicionado en un [del sistema de coordenadas espacial](coordinate-systems-in-directx.md) se represente en el HolographicSpace. El sistema proporciona dos principales marcos de referencia que puede usar para establecer un sistema de coordenadas para las hologramas.

Hay dos tipos de fotogramas de referencia de Windows Holographic: hacer referencia a marcos asociados al dispositivo y referencia que se mantenga estacionario cuando el dispositivo se mueve a través del entorno del usuario. La plantilla de aplicación holográfica usa un marco estático de referencia de forma predeterminada; Esta es una de las maneras más sencillas de representar hologramas bloqueado por el mundo.

Marcos de referencia fijos están diseñados para estabilizar posiciones cerca de la ubicación del dispositivo actual. Esto significa que se permiten las coordenadas más lejos el dispositivo a desviarse ligeramente con respecto a la del entorno del usuario, como el dispositivo aprende más sobre el espacio alrededor de ella. Hay dos maneras de crear un marco estático de referencia: adquirir el sistema de coordenadas de la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), o use el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Si va a crear una aplicación de Windows Mixed Reality para inmersivos, el punto de partida recomendado es el [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que también proporciona información acerca de las capacidades de los auriculares envolventes adosadas al Reproductor. Aquí, se muestra cómo usar el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

El localizador espacial representa el dispositivo Windows Mixed Reality y realiza un seguimiento del movimiento del dispositivo y proporciona los sistemas de coordenadas que pueda entender con respecto a su ubicación.

Desde **AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Cree una vez el marco de referencia estacionario cuando se inicia la aplicación. Esto es análogo a la definición de un sistema de coordenadas del mundo, con el origen que se coloca en la posición del dispositivo cuando se inicia la aplicación. Este marco de referencia no se mueve con el dispositivo.

Desde **AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Todos los marcos de referencia son gravedad alineada, lo que significa que el eje y puntos de "up" en relación con el entorno del usuario. Puesto que Windows usa "diestros" sistemas de coordenadas, la dirección del eje z: coincide con la dirección "forward" el dispositivo está orientado a cuando se crea el marco de referencia.

>[!NOTE]
>Si la aplicación requiere la posición precisa de hologramas individuales, utilice un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> a delimitar el holograma individual a una posición en el mundo real. Por ejemplo, utilice un delimitador espacial cuando el usuario indica que un punto de ser de especial interés. No desvíen posiciones de delimitador, pero puede ajustarse. De forma predeterminada, cuando se ajusta un delimitador, facilita su posición en su lugar a través de las tramas siguientes después de la corrección se ha producido. Dependiendo de la aplicación, cuando esto sucede puede controlar el ajuste de forma diferente (por ejemplo, aplazarla hasta que el holograma está fuera de la vista). El <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> propiedad y <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> los eventos habilitan estas personalizaciones.

## <a name="respond-to-locatability-changed-events"></a>Responder a eventos locatability cambiado

Representación hologramas bloqueado por el mundo requiere que el dispositivo se puede localizar a sí mismo en el mundo. Esto no siempre sea posible debido a condiciones ambientales y, si es así, el usuario puede esperar una indicación visual de la interrupción de seguimiento. Esta indicación visual se debe representar mediante marcos de referencia asociados al dispositivo, en lugar de diseño de fondo a todo el mundo.

Aplicación puede solicitar que se le notifique si el seguimiento se interrumpe por algún motivo. Registrarse para que el evento LocatabilityChanged detectar cuándo la capacidad del dispositivo a sí mismo buscar en los cambios del mundo. Desde **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

A continuación, use este evento para determinar cuándo no se puede representar hologramas estacionarios a todo el mundo.

## <a name="see-also"></a>Vea también
* [Representación de DirectX](rendering-in-directx.md)
* [Sistemas de coordenadas en DirectX](coordinate-systems-in-directx.md)
