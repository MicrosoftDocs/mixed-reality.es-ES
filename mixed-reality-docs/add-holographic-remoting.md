---
title: Incorporación de Holographic Remoting
description: Explica cómo usar la comunicación remota holográfica para representar hologramas en una HoloLens a través de la red.
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, hologramas, comunicación remota holográfica, representación remota, representación en red, HoloLens, hologramas remotos
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277713"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a>Incorporación de la comunicación remota holográfica (HoloLens (1ª generación))

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación host para HoloLens 1. La aplicación host para **HoloLens (1ª generación)** debe usar el paquete NuGet versión **1. x. x**. Esto implica que las aplicaciones host escritas para HoloLens 1 no son compatibles con HoloLens 2 y viceversa.

## <a name="hololens-2"></a>HoloLens 2

Los desarrolladores de HoloLens que usen la comunicación remota de Holographic deberán actualizar sus aplicaciones para que sean compatibles con HoloLens 2. Esto requiere una nueva versión del paquete NuGet de Holographic Remoting. Si una aplicación que usa el paquete NuGet de Holographic Remoting con un número de versión menor que 2.0.0.0 intenta conectarse al reproductor de acceso remoto holográfica en HoloLens 2, se producirá un error en la conexión.

>[!NOTE]
>Las instrucciones específicas de HoloLens 2 se pueden encontrar [aquí](holographic-remoting-create-host.md).


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Adición de Holographic Remoting a su aplicación de escritorio o UWP

En esta página se describe cómo agregar la comunicación remota holográfica a una aplicación de escritorio o UWP.

Holographic Remoting permite que la aplicación tenga como destino una HoloLens con contenido holográfica hospedado en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema y permite integrar [vistas envolventes](app-views.md) remotas en software de equipo de escritorio existente. Una aplicación host de comunicación remota recibe un flujo de datos de entrada de HoloLens, representa el contenido en una vista envolvente virtual y transmite los fotogramas de contenido de nuevo a HoloLens. La conexión se realiza mediante Wi-Fi estándar. Para usar la comunicación remota, usará un paquete NuGet para agregar la comunicación remota holográfica a su aplicación de escritorio o UWP, y escribir código para controlar la conexión y representar en una vista envolvente. Las bibliotecas auxiliares se incluyen en el ejemplo de código que simplifican la tarea de controlar la conexión del dispositivo.

Una conexión remota típica tendrá un mínimo de 50 ms de latencia. La aplicación de reproducción puede informar de la latencia en tiempo real.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.

### <a name="get-the-remoting-nuget-packages"></a>Obtención de los paquetes NuGet de comunicación remota

Siga estos pasos para obtener el paquete NuGet para la comunicación remota de Holographic y agregue una referencia desde el proyecto:
1. Vaya al proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**
3. En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".
4. Seleccione **Microsoft. Holographic. Remoting** y haga clic en **instalar**.
5. Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.
6. El siguiente cuadro de diálogo que aparece es el contrato de licencia. Haga clic en **acepto para aceptar el contrato de licencia** .

### <a name="create-the-holographicstreamerhelpers"></a>Crear HolographicStreamerHelpers

En primer lugar, necesitamos una instancia de HolographicStreamerHelpers. Agregue esto a la clase que controlará la comunicación remota.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

También necesitará realizar un seguimiento del estado de la conexión. Si desea representar la vista previa, debe tener una textura en la que copiarla. También necesita algunas cosas como un bloqueo de estado de conexión, alguna forma de almacenar la dirección IP de HoloLens, etc.

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inicializar HolographicStreamerHelpers y conectarse a HoloLens

Para conectarse a un dispositivo HoloLens, cree una instancia de HolographicStreamerHelpers y conéctese a la dirección IP de destino. Tendrá que establecer el tamaño del fotograma de vídeo para que coincida con el ancho y el alto de la pantalla de HoloLens, ya que la biblioteca remota de Holographic espera que las resoluciones del codificador y el descodificador coincidan exactamente.

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

La conexión del dispositivo es asincrónica. La aplicación debe proporcionar controladores de eventos para los eventos Connect, Disconnect y Send frame.

El evento alconnected puede actualizar la interfaz de usuario, iniciar la representación, etc. En nuestro ejemplo de código de escritorio, actualizamos el título de la ventana con un mensaje "conectado".

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

El evento OnDisconnection puede controlar la reconexión, las actualizaciones de la interfaz de usuario, etc. En este ejemplo, se vuelve a conectar si se produce un error transitorio.

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

Cuando el componente de comunicación remota está listo para enviar un marco, se proporciona a la aplicación la oportunidad de hacer una copia de él en el SendFrameEvent. En este caso, copiamos el fotograma a una cadena de intercambio para que podamos mostrarlo en una ventana de vista previa.

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

### <a name="render-holographic-content"></a>Representación de contenido holográfica

Para representar contenido mediante la comunicación remota, configure un IFrameworkView virtual dentro de la aplicación de escritorio o UWP y procese tramas holográficas de la comunicación remota. Todas las API de Windows Holographic se usan de la misma manera en esta vista, pero se configuran de forma ligeramente diferente.

En lugar de crearlos usted mismo, el espacio holográfica y los componentes de voz provienen de la clase HolographicRemotingHelpers:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

En lugar de usar un bucle de actualización dentro de un método Run, se proporcionan actualizaciones por pasos desde el bucle principal de la aplicación de escritorio o UWP. Esto permite que la aplicación de escritorio o UWP permanezca en el control del procesamiento de mensajes.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

El método tick () de la vista de aplicación holográfica completa una iteración del bucle Update, Draw y Present.

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

El bucle de actualización, representación y presentación de la vista de aplicación holográfica es exactamente el mismo que cuando se ejecuta en HoloLens, salvo que tiene acceso a una cantidad mucho mayor de recursos del sistema en el equipo de escritorio. Puede representar muchos más triángulos, tener más pasos de dibujo, hacer más física y usar procesos x64 para cargar contenido que requiera más de 2 GB de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Desconectar y finalizar la sesión remota

Para desconectarse: por ejemplo, cuando el usuario hace clic en un botón de la interfaz de usuario para desconectar-llamar a Disconnect () en HolographicStreamerHelpers y, a continuación, libera el objeto.

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

## <a name="get-the-remoting-player"></a>Obtener el reproductor remoto

El reproductor de Windows Holographic Remoting se ofrece en la tienda de aplicaciones de Windows como un punto de conexión para que las aplicaciones de host remoto se conecten a. Para obtener el reproductor de Windows Holographic Remoting, visite la tienda de aplicaciones de Windows desde HoloLens, busque la comunicación remota y descargue la aplicación. El reproductor de comunicación remota incluye una característica para mostrar las estadísticas en pantalla, lo que puede resultar útil al depurar aplicaciones de host remoto.

## <a name="notes-and-resources"></a>Notas y recursos

La vista de aplicación holográfica necesitará una manera de proporcionar la aplicación con el dispositivo Direct3D, que debe usarse para inicializar el espacio holográfica. La aplicación debe usar este dispositivo Direct3D para copiar y mostrar el marco de vista previa.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Código de ejemplo:** Hay disponible un ejemplo de código de Holographic Remoting completo, que incluye una vista de aplicación holográfica que es compatible con los proyectos de host remoto y de comunicación remota para escritorio Win32, UWP DirectX y UWP con XAML. Para obtenerlo, vaya aquí:
* [Ejemplo de código Holographic de Windows para la comunicación remota](https://github.com/Microsoft/HoloLensCompanionKit/)

**Nota de depuración:** La biblioteca remota holográfica puede producir excepciones de primera oportunidad. Estas excepciones pueden ser visibles en las sesiones de depuración, en función de la configuración de excepciones de Visual Studio que esté activa en ese momento. Estas excepciones las detecta internamente la biblioteca de comunicación remota holográfica y se pueden omitir.
