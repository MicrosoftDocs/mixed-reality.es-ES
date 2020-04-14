---
title: Obtención de un HolographicSpace
description: Explica la API de HolographicSpace, un concepto básico de representación de Holographic y entrada espacial.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, entrada espacial, representación, cadena de intercambio, marco holográfica, bucle de actualización, bucle de juego, marco de referencia, localización, código de ejemplo, tutorial
ms.openlocfilehash: 76211c8a5394e2e296748253df4eac063841746c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277833"
---
# <a name="getting-a-holographicspace"></a>Obtención de un HolographicSpace

La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> es su portal en el mundo holográfica. Controla la representación envolvente, proporciona datos de la cámara y proporciona acceso a las API de razonamiento espacial. Creará una para el identificador de usuario de la <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">aplicación de UWP o la</a> aplicación Win32.

## <a name="set-up-the-holographic-space"></a>Configuración del espacio holográfica

La creación del objeto de espacio holográfica es el primer paso para crear una aplicación de Windows Mixed Reality. Las aplicaciones tradicionales de Windows se representan en una cadena de intercambio de Direct3D creada para la ventana principal de la vista de la aplicación. Esta cadena de intercambio se muestra en una pizarra en la interfaz de usuario holográfica. Para hacer que la vista de la aplicación sea holográfica en lugar de una pizarra 2D, cree un espacio holográfica para su ventana principal en lugar de una cadena de intercambio. La presentación de tramas holográficas creadas por este espacio holográfica coloca la aplicación en el modo de representación de pantalla completa.

En el caso de una **aplicación para UWP** a partir [de la *plantilla holográfica DirectX 11 (Windows universal)* ](creating-a-holographic-directx-project.md), busque este código en el método **SetWindow** en AppView. cpp:

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

En el caso de una **aplicación de Win32** que se [inicie en el ejemplo de Win32 *BasicHologram* ](creating-a-holographic-directx-project.md#creating-a-win32-project), consulte **App:: CreateWindowAndHolographicSpace** para obtener un ejemplo de cómo crear un HWND y luego convertirlo en un HWND envolvente mediante la creación de un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>asociado:
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

Ahora que ha obtenido un HolographicSpace para su HWND de UWP o HWND de Win32, usará ese HolographicSpace para controlar las cámaras holográficas, crear sistemas de coordenadas y realizar la representación holográfica. El espacio holográfica actual se usa en varios lugares de la plantilla de DirectX:
* La clase **DeviceResources** debe obtener cierta información del objeto HolographicSpace para crear el dispositivo Direct3D. Este es el identificador del adaptador de DXGI asociado a la pantalla holográfica. La clase <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> usa el dispositivo Direct3D 11 de la aplicación para crear y administrar recursos basados en dispositivos como, por ejemplo, los búferes de reserva de cada cámara holográfica. Si le interesa ver lo que hace esta función en el capó, la encontrará en DeviceResources. cpp.
* La función **DeviceResources:: InitializeUsingHolographicSpace** muestra cómo obtener el adaptador buscando el LUID y cómo elegir un adaptador predeterminado cuando no se especifica ningún adaptador preferido.
* La clase principal de la aplicación usa el espacio holográfica de **AppView:: SetWindow** o **App:: CreateWindowAndHolographicSpace** para las actualizaciones y la representación.

>[!NOTE]
>Aunque en las secciones siguientes se mencionan los nombres de función de la plantilla como **AppView:: SetWindow** que suponen que se ha iniciado desde la plantilla de aplicación de UWP de Holographic, los fragmentos de código que se ven se aplicarán igualmente a través de aplicaciones de UWP y Win32.

A continuación, profundizaremos en el proceso de configuración que **SetHolographicSpace** es responsable de en la clase AppMain.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>Suscripción a eventos de cámara, creación y eliminación de recursos de la cámara

El contenido holográfica de la aplicación vive en su espacio holográfica y se ve a través de una o varias cámaras holográfica que representan perspectivas diferentes en la escena. Ahora que tiene el espacio holográfica, puede recibir datos para cámaras holográficas.

La aplicación debe responder a los eventos de **CameraAdded** mediante la creación de los recursos específicos de esa cámara, como la vista de destino de representación del búfer de reserva. Puede ver este código en la función **DeviceResources:: SetHolographicSpace** , llamada por **AppView:: SetWindow** antes de que la aplicación cree cualquier trama holográfica:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

La aplicación también debe responder a los eventos de **CameraRemoved** mediante la liberación de los recursos que se crearon para esa cámara.

De **DeviceResources:: SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

Los controladores de eventos deben completar algún trabajo para que la representación holográfica fluya sin problemas y para que la aplicación se pueda representar en absoluto. Lea el código y los comentarios de los detalles: puede buscar **OnCameraAdded** y **OnCameraRemoved** en la clase principal para entender cómo controla la asignación de **m_cameraResources** mediante **DeviceResources**.

En este momento, nos centramos en AppMain y en la configuración que permite que la aplicación Conozca las cámaras holográficas. Teniendo esto en cuenta, es importante tener en cuenta los dos requisitos siguientes:

1. En el caso del controlador de eventos **CameraAdded** , la aplicación puede trabajar de forma asincrónica para finalizar la creación de recursos y la carga de recursos para la nueva cámara holográfica. Las aplicaciones que tardan más de un fotograma para completar este trabajo deben solicitar un aplazamiento y completar el aplazamiento después de cargarse de forma asincrónica. una [tarea PPL](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) se puede usar para realizar el trabajo asincrónico. La aplicación debe asegurarse de que esté lista para representarse en esa cámara inmediatamente cuando salga del controlador de eventos o cuando complete el aplazamiento. Salir del controlador de eventos o completar el aplazamiento indica al sistema que la aplicación ya está lista para recibir tramas holográficas con esa cámara incluida.

2. Cuando la aplicación recibe un evento **CameraRemoved** , debe liberar todas las referencias al búfer de reserva y salir de la función inmediatamente. Esto incluye las vistas de destino de representación y cualquier otro recurso que pueda contener una referencia a [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource). La aplicación también debe asegurarse de que el búfer de reserva no está asociado como destino de representación, como se muestra en **CameraResources:: ReleaseResourcesForBackBuffer**. Para ayudar a acelerar las cosas, la aplicación puede liberar el búfer de reserva y, a continuación, iniciar una tarea para completar de forma asincrónica cualquier otro trabajo que sea necesario para anular la cámara. La plantilla de aplicación holográfica incluye una tarea PPL que puede usar con este fin.

>[!NOTE]
>Si desea determinar cuándo se muestra una cámara agregada o quitada en el fotograma, use las propiedades **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) y [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) .

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Creación de un marco de referencia para el contenido holográfica

El contenido de la aplicación debe colocarse en un [sistema de coordenadas espaciales](coordinate-systems-in-directx.md) que se va a representar en el HolographicSpace. El sistema proporciona dos fotogramas principales de referencia que puede usar para establecer un sistema de coordenadas para los hologramas.

Hay dos tipos de fotogramas de referencia en Windows Holographic: los fotogramas de referencia conectados al dispositivo y hacen referencia a fotogramas que permanecen estacionarios a medida que el dispositivo se mueve por el entorno del usuario. De forma predeterminada, la plantilla de aplicación holográfica usa un marco de referencia estacional. Esta es una de las formas más sencillas de representar hologramas de bloque mundial.

Los fotogramas de referencia estacionarios están diseñados para estabilizar las posiciones cerca de la ubicación actual del dispositivo. Esto significa que las coordenadas más allá del dispositivo pueden desplazarse ligeramente con respecto al entorno del usuario, ya que el dispositivo aprende más sobre el espacio que lo rodea. Hay dos maneras de crear un marco estacionario de referencia: adquirir el sistema de coordenadas de la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)o usar el valor predeterminado <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>. Si va a crear una aplicación de Windows Mixed Reality para auriculares envolventes, el punto de partida recomendado es la [fase espacial](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), que también proporciona información acerca de las capacidades del casco envolvente que gasta el jugador. Aquí se muestra cómo usar el valor predeterminado de <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.

El localizador espacial representa el dispositivo de Windows Mixed Reality y realiza un seguimiento del movimiento del dispositivo y proporciona sistemas de coordenadas que se pueden entender en relación con su ubicación.

Desde **AppMain:: OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

Cree el marco de referencia estacionario una vez cuando se inicie la aplicación. Esto es análogo a definir un sistema de coordenadas universal, con el origen colocado en la posición del dispositivo cuando se inicia la aplicación. Este fotograma de referencia no se mueve con el dispositivo.

Desde **AppMain:: SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

Todos los marcos de referencia están alineados con la gravedad, lo que significa que el eje y apunta "hacia arriba" con respecto al entorno del usuario. Puesto que Windows usa sistemas de coordenadas "zurdos", la dirección del eje – z coincide con la dirección "hacia delante" a la que se enfrenta el dispositivo cuando se crea el fotograma de referencia.

>[!NOTE]
>Cuando la aplicación requiere una ubicación precisa de hologramas individuales, use un <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> para anclar el holograma individual en una posición del mundo real. Por ejemplo, use un delimitador espacial cuando el usuario indique que un punto debe ser de especial interés. Las posiciones de anclaje no se desplazan, pero se pueden ajustar. De forma predeterminada, cuando se ajusta un delimitador, facilita su posición en lugar de los próximos fotogramas después de que se haya realizado la corrección. En función de la aplicación, cuando esto sucede, es posible que desee controlar el ajuste de manera diferente (por ejemplo, si lo aplaza hasta que el holograma esté fuera de la vista). La propiedad <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> y los eventos <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> habilitan estas personalizaciones.

## <a name="respond-to-locatability-changed-events"></a>Responder a los eventos de búsqueda modificada

La representación de hologramas con bloqueo mundial requiere que el dispositivo pueda localizarse en todo el mundo. Esto puede no ser siempre posible debido a las condiciones del entorno, y si es así, el usuario puede esperar una indicación visual de la interrupción del seguimiento. Esta indicación visual se debe representar mediante fotogramas de referencia conectados al dispositivo, en lugar de separarse del mundo.

La aplicación puede solicitar recibir una notificación si se interrumpe el seguimiento por cualquier motivo. Regístrese en el evento LocatabilityChanged para detectar cuándo cambia la capacidad del dispositivo de localizarse en el mundo. Desde **AppMain:: SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

A continuación, use este evento para determinar cuándo no se pueden representar los hologramas estacionales en el mundo.

## <a name="see-also"></a>Vea también
* [Representación en DirectX](rendering-in-directx.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
