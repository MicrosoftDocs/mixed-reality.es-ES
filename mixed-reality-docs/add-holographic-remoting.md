---
title: Agregar remoting holográfica
description: Explica cómo utilizar Remoting holográfica para representar un HoloLens hologramas a través de la red.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hologramas, remoting holográfica, procesamiento remoto, red de representación, HoloLens, hologramas remotos
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605789"
---
# <a name="add-holographic-remoting"></a>Agregar remoting holográfica

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Agregar remoting holographic a su escritorio o aplicación para UWP

Esta página describe cómo agregar holográfica de comunicación remota a un escritorio o una aplicación para UWP.

Comunicación remota holográfica permite que la aplicación para tener como destino un HoloLens con holográfica contenido hospedado en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, permitiendo el acceso a más recursos del sistema y lo que permite integrar remoto [envolventes vistas](app-views.md) en software de PC de escritorio existente. Una aplicación de host de comunicación remota recibe un flujo de datos de entrada de un HoloLens, representa el contenido en una vista virtual envolvente y transmite el contenido de marcos a HoloLens. La conexión se realiza mediante Wi-Fi estándar. Para usar el acceso remoto, utilizará un paquete NuGet para agregar remoting holographic a su escritorio o aplicación para UWP y escribir código para controlar la conexión y se representan en una vista envolvente. Bibliotecas auxiliares se incluyen en el ejemplo de código que simplifican la tarea de administrar la conexión del dispositivo.

Una conexión de comunicación remota típica tendrá sea tan lenta como 50 ms de latencia. La aplicación de Reproductor puede notificar la latencia en tiempo real.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

### <a name="get-the-remoting-nuget-packages"></a>Obtener la comunicación remota de paquetes de NuGet

Siga estos pasos para obtener el paquete NuGet para la comunicación remota holográfica y agregue una referencia del proyecto:
1. Vaya a su proyecto en Visual Studio.
2. Haga doble clic en el nodo del proyecto y seleccione **administrar paquetes NuGet...**
3. En el panel que aparece, haga clic en **examinar** y, a continuación, busque "Holográfica Remoting".
4. Seleccione **Microsoft.Holographic.Remoting** y haga clic en **instalar**.
5. Si el **Preview** aparece el cuadro de diálogo, haga clic en **Aceptar**.
6. El siguiente cuadro de diálogo que aparece es el contrato de licencia. Haga clic en **acepto** para aceptar el contrato de licencia.

### <a name="create-the-holographicstreamerhelpers"></a>Crear el HolographicStreamerHelpers

En primer lugar, se necesita una instancia de HolographicStreamerHelpers. Agregar esto a la clase que se ocupa de comunicación remota.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

También deberá realizar un seguimiento de estado de conexión. Si desea representar la vista previa, debe tener una textura para copiarlo a. También necesita algunas cosas como un bloqueo de estado de conexión, alguna manera de almacenar la dirección IP de HoloLens y así sucesivamente.

```
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inicializar HolographicStreamerHelpers y conéctese a HoloLens

Para conectarse a un dispositivo HoloLens, cree una instancia de HolographicStreamerHelpers y conéctese a la dirección IP de destino. Deberá establecer el tamaño del fotograma de vídeo para que coincida con el ancho de pantalla de HoloLens y el alto, porque la biblioteca de Remoting holográfica espera que las resoluciones de codificador y descodificador que coincidan exactamente.

```
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

La conexión del dispositivo es asincrónica. Las necesidades de su aplicación para proporcionar los controladores de eventos para conectar, desconectar y marco de envío de eventos.

El evento OnConnected puede actualizar la interfaz de usuario, iniciar representación y así sucesivamente. En nuestro ejemplo de código de escritorio, actualizamos el título de ventana con un mensaje "conectado".

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

Puede controlar el evento OnDisconnected reconexión, las actualizaciones de la interfaz de usuario y así sucesivamente. En este ejemplo, se vuelve a conectar las si se produce un error transitorio.

```
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

Cuando el componente de comunicación remota está listo para enviar un marco, la aplicación se proporciona una oportunidad para realizar una copia del mismo en el SendFrameEvent. En este caso, el marco se copia en una cadena de intercambio para que se pueden mostrar en una ventana de vista previa.

```
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

### <a name="render-holographic-content"></a>Representar el contenido holográfica

Para representar el contenido mediante la comunicación remota, se configura un IFrameworkView virtual dentro de su escritorio o aplicación para UWP y procesar holográficas marcos de comunicación remota. Todas las API de Windows Holographic son usa que la misma manera por esta vista, pero se ha configurado una forma ligeramente diferente.

En lugar de crearlas usted mismo, los componentes de voz y de espacio holográficas proceden de la clase HolographicRemotingHelpers:

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

En lugar de usar un bucle de actualización dentro de un método de ejecución, proporciona actualizaciones de graduación desde el bucle principal de su escritorio o aplicación para UWP. Esto permite que el escritorio o aplicación para UWP para conservar el control del procesamiento de mensajes.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Método de la vista holográfica aplicación Tick() completa una iteración de la actualización, draw, bucle está presente.

```
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

La actualización de la vista holográfica app, representación y bucle presente es exactamente el mismo ya que es cuando se ejecuta en HoloLens - salvo que tienen acceso a una mayor cantidad de recursos del sistema en su PC de escritorio. Puede representar muchos más triángulos, tiene varias pasadas de dibujos, hacer más física y usan x64 procesos para cargar el contenido que requiere más de 2 GB de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Desconectar y finalizar la sesión remota

Para desconectar - por ejemplo, cuando el usuario hace clic en un botón de la interfaz de usuario para desconectar - llame Disconnect() en el HolographicStreamerHelpers y, a continuación, liberar el objeto.

```
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

## <a name="get-the-remoting-player"></a>Obtener el Reproductor de comunicación remota

El Reproductor de comunicación remota de Windows Holographic se ofrece en la tienda de aplicaciones de Windows como para hospedar aplicaciones de comunicación remota para conectarse a un punto de conexión. Para obtener el Reproductor de comunicación remota de Windows Holographic, visite la tienda de aplicaciones de Windows desde su HoloLens, búsqueda para la comunicación remota y descargar la aplicación. El Reproductor de remoting incluye una característica para mostrar las estadísticas en la pantalla, que puede ser útil al depurar aplicaciones de host de comunicación remota.

## <a name="notes-and-resources"></a>Notas y recursos

La vista holográfica aplicación necesitará una manera de proporcionar la aplicación con el dispositivo Direct3D, lo que debe usarse para inicializar el espacio holográfico. La aplicación debe usar este dispositivo Direct3D para copiar y mostrar el fotograma de vista previa.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Ejemplo de código:** Un ejemplo de código completo de Remoting holográfica está disponible, lo que incluye una vista holográfica aplicación que sea compatible con la comunicación remota y los proyectos de host de comunicación remota de escritorio UWP con XAML, DirectX de UWP y Win32. Para obtenerla, vaya aquí:
* [Ejemplo de código holográfico de Windows para la comunicación remota](https://github.com/Microsoft/HoloLensCompanionKit/)

**Tenga en cuenta la depuración:** La biblioteca de Remoting holográfica puede producir excepciones de primera oportunidad. Estas excepciones pueden verse en las sesiones, dependiendo de la configuración de excepciones de Visual Studio que están activa en el momento de depuración. Estas excepciones se detectan internamente por la biblioteca de Remoting holográfica y pueden omitirse.
