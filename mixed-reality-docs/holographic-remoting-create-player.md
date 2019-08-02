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
# <a name="writing-a-custom-holographic-remoting-player-app"></a>Escritura de una aplicación de reproductor remoto holográfica personalizada

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación de reproductor personalizada para HoloLens 2. Los reproductores personalizados escritos para HoloLens 2 no son compatibles con las aplicaciones host escritas para HoloLens 1. Esto implica que ambas aplicaciones deben usar el paquete NuGet versión **2. x. x**.

Mediante la creación de una aplicación de reproductor de acceso remoto holográfica personalizada, puede crear una aplicación personalizada capaz de mostrar [vistas](app-views.md) envolventes desde en una máquina remota de HoloLens 2. En este artículo se describe cómo se puede lograr esto. Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Un reproductor remoto holográfica permite a la aplicación mostrar el contenido holográfica [representado](rendering.md) en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema. Una aplicación de reproductor de comunicación remota holográfica transmite datos de entrada a una aplicación host de Holographic Remoting y recibe una vista envolvente como flujo de audio y vídeo. La conexión se realiza mediante Wi-Fi estándar. Para crear una aplicación de reproductor, usará un paquete NuGet para agregar la comunicación remota holográfica a la aplicación para UWP y escribir código para controlar la conexión y mostrar una vista envolvente. 

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación UWP basada en DirectX que ya tiene como destino la API de Windows Mixed Reality. Para obtener más información, vea [Introducción al desarrollo de DirectX](directx-development-overview.md). Si no tiene una aplicación existente y desea comenzar desde el principio, la [ C++ plantilla de proyecto Holographic](creating-a-holographic-directx-project.md) es un buen punto de partida.

>[!IMPORTANT]
>Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments). El uso de un [Apartamento](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) de un solo subproceso es compatible, pero puede dar lugar a un rendimiento poco óptimo y posiblemente a la reproducción. Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) , un apartamento multiproceso es el valor predeterminado.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obtención del paquete NuGet de Holographic Remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**
3. En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".
4. Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y haga clic en **instalar**.
5. Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.
6. El siguiente cuadro de diálogo que aparece es el contrato de licencia. Haga clic en Acepto para aceptar el contrato de licencia.

>[!IMPORTANT]
><a name="idl"></a>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` En el paquete NuGet se incluye documentación detallada para la API expuesta por la comunicación remota holográfica.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modificar el paquete. appxmanifest de la aplicación

Para que la aplicación tenga en cuenta el Microsoft. Holographic. AppRemoting. dll agregado por el paquete de NuGet, es necesario realizar los siguientes pasos en el proyecto:

1. En el Explorador de soluciones haga clic con el botón derecho en el archivo **Package. appxmanifest** y seleccione **abrir con.** ..
2. Seleccione **Editor XML (texto)** y haga clic en Aceptar.
3. Agregue las líneas siguientes al archivo y guárdela
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
## <a name="create-the-player-context"></a>Crear el contexto del reproductor

Como primer paso, la aplicación debe crear un contexto de reproductor.

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
>Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota. Esto se realiza durante la creación del contexto del reproductor. Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto del reproductor puede producir un comportamiento inesperado. El enfoque recomendado es crear el contexto del reproductor tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta. Nunca mezcle objetos creados o recuperados a través de cualquier API de realidad mixta de ```PlayerContext::Create()``` Windows antes de la llamada a con objetos creados o recuperados después.

A continuación, se puede crear el HolographicSpace llamando a [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>Conexión al host

Una vez que la aplicación de reproducción está lista para representar el contenido, se puede establecer una conexión con el host.

La conexión se puede establecer de una de las maneras siguientes:
1) La aplicación de reproducción que se ejecuta en HoloLens 2 se conecta a la aplicación host.
2) La aplicación host se conecta a la aplicación de reproductor que se ejecuta en HoloLens 2.

Para conectarse desde la aplicación del reproductor al host, llame ```Connect``` al método en el contexto del reproductor y especifique el nombre de host y el puerto. El puerto predeterminado es **8265**.

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
>Como con cualquier C++API ```Connect``` de/WinRT puede producir un WinRT:: hresult_error que debe controlarse.

La escucha de conexiones entrantes en la aplicación del reproductor puede realizarse ```Listen``` mediante una llamada al método. El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada. El puerto de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada, se usan el número de puerto **8265** y **8266** .

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


## <a name="handling-connection-related-events"></a>Controlar eventos relacionados con la conexión

```PlayerContext``` Expone tres eventos para supervisar el estado de la conexión.
1) Conectado: Se desencadena cuando se ha establecido correctamente una conexión con el host.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnection: Se desencadena si se termina una conexión establecida o no se pudo establecer una conexión.
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
>Los ```ConnectionFailureReason``` valores posibles se documentan ```Microsoft.Holographic.AppRemoting.idl``` en el [archivo](#idl).

3) En escucha: Cuando se inicia la escucha de conexiones entrantes.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

Además, se puede consultar el estado de la ```ConnectionState``` conexión utilizando la propiedad en el contexto del reproductor.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Mostrar el marco representado de forma remota

Para mostrar el contenido representado de forma remota, llame ```PlayerContext::BlitRemoteFrame()``` a mientras representa un [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame()```requiere que el búfer de reserva del HolographicFrame actual esté enlazado como destino de representación. El búfer de reserva se puede recibir desde [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) a través de la propiedad [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

Cuando se llama ```BlitRemoteFrame()``` , copia el último fotograma recibido de la aplicación host en el búfer de reserva del HolographicFrame. Además, se establece el conjunto de puntos de enfoque si la aplicación remota ha especificado un punto de enfoque durante la representación del marco remoto.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```potencialmente sobrescribe el punto de enfoque para el marco actual. 
>- Para especificar un punto de enfoque de reserva, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes ```PlayerContext::BlitRemoteFrame()```de. 
>- Para overrwrite el punto de enfoque remoto, llame a [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) después ```PlayerContext::BlitRemoteFrame()```de.

Si se ejecuta ```BlitRemoteFrame()``` correctamente ```BlitResult::Success_Color```, devuelve. En caso contrario, devuelve el motivo del error:
- ```BlitResult::Failed_NoRemoteFrameAvailable```: No se pudo completar porque no hay ningún marco remoto disponible.
- ```BlitResult::Failed_NoCamera```: Error porque no hay ninguna cámara presente.

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Opcional: Obtener estadísticas sobre el último marco remoto

Para diagnosticar problemas de rendimiento o de red, se pueden recuperar estadísticas sobre el último marco remoto ```PlayerContext::LastFrameStatistics``` a través de la propiedad. Las estadísticas se actualizan durante la llamada a [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Para obtener más información, consulte ```PlayerFrameStatistics``` la documentación ```Microsoft.Holographic.AppRemoting.idl``` del [archivo](#idl).

## <a name="optional-custom-data-channels"></a>Opcional: Canales de datos personalizados

Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida. Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.

## <a name="see-also"></a>Vea también
* [Escritura de una aplicación de host de Holographic Remoting](holographic-remoting-create-host.md)
* [Canales de datos personalizados de Holographic Remoting](holographic-remoting-custom-data-channels.md)
* [Establecimiento de una conexión segura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)