---
title: Escritura de una aplicación de host de Holographic Remoting
description: Mediante la creación de un contenido remoto de aplicación de host de Holographic Remoting, que se representa en un equipo remoto, se puede transmitir a HoloLens 2. En este artículo se describe cómo se puede lograr esto.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 6b0f92fce1099ec98d87100e015de9442bff6bd2
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122029"
---
# <a name="writing-a-holographic-remoting-host-app"></a>Escritura de una aplicación de host de Holographic Remoting

>[!IMPORTANT]
>En este documento se describe la creación de una aplicación host para HoloLens 2. La aplicación host para **HoloLens (1ª generación)** debe usar el paquete NuGet versión **1. x. x**. Esto implica que las aplicaciones host escritas para HoloLens 2 no son compatibles con HoloLens 1 y viceversa. La documentación de HoloLens 1 se puede encontrar [aquí](add-holographic-remoting.md).

Al crear un contenido remoto de aplicación de host de Holographic Remoting que se representa en un equipo remoto, se puede transmitir a HoloLens 2. En este artículo se describe cómo se puede lograr esto. Todo el código de esta página y los proyectos de trabajo se pueden encontrar en el repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

Holographic Remoting permite que una aplicación tenga como destino HoloLens 2 con contenido holográfica hospedado en un equipo de escritorio o en un dispositivo UWP, como la Xbox One, lo que permite el acceso a más recursos del sistema y permite integrar [vistas](app-views.md) envolventes remotas en el existente. software de equipo de escritorio. Una aplicación host de comunicación remota recibe un flujo de datos de entrada de HoloLens 2, representa el contenido en una vista envolvente virtual y vuelve a transmitir los fotogramas de contenido a HoloLens 2. La conexión se realiza mediante Wi-Fi estándar. Holographic Remoting se agrega a una aplicación de escritorio o UWP a través de un paquete NuGet. Se requiere código adicional que controla la conexión y se representa en una vista envolvente.

Una conexión remota típica tendrá un mínimo de 50 ms de latencia. La aplicación de reproducción puede informar de la latencia en tiempo real.

## <a name="prerequisites"></a>Requisitos previos

Un buen punto de partida es una aplicación de escritorio o UWP basada en DirectX que funciona como destino de la API de Windows Mixed Reality. Para obtener más información, vea [Introducción al desarrollo de DirectX](directx-development-overview.md). La [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md) es un buen punto de partida.

>[!IMPORTANT]
>Cualquier aplicación que use la comunicación remota de Holographic debe crearse para usar un [Apartamento multiproceso](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments). Se admite el uso de un apartamento de un [solo subproceso](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) , pero se producirá un rendimiento poco óptimo y posiblemente se produzca una intermitencia durante la reproducción. Al usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) , un apartamento multiproceso es el valor predeterminado.



## <a name="get-the-holographic-remoting-nuget-package"></a>Obtención del paquete NuGet de Holographic Remoting

Los pasos siguientes son necesarios para agregar el paquete NuGet a un proyecto en Visual Studio.
1. Abra el proyecto en Visual Studio.
2. Haga clic con el botón derecho en el nodo del proyecto y seleccione **administrar paquetes NuGet...**
3. En el panel que aparece, haga clic en **examinar** y busque "Holographic Remoting".
4. Seleccione **Microsoft. Holographic. Remoting**, asegúrese de elegir la versión **2. x. x** más reciente y haga clic en **instalar**.
5. Si aparece el cuadro de diálogo **vista previa** , haga clic en **Aceptar**.
6. El siguiente cuadro de diálogo que aparece es el contrato de licencia. Haga clic en Acepto para aceptar el contrato de licencia.

>[!NOTE]
>La versión **1. x.** x del paquete NuGet sigue estando disponible para los desarrolladores que quieran tener como destino HoloLens 1. Para obtener más información, consulte incorporación de la [comunicación remota holográfica (HoloLens (1º generación))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Crear el contexto remoto

Como primer paso, la aplicación debe crear un contexto remoto.

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
>Holographic Remoting funciona reemplazando el tiempo de ejecución de Windows Mixed Reality, que forma parte de Windows con un tiempo de ejecución específico de comunicación remota. Esto se realiza durante la creación del contexto remoto. Por ese motivo, cualquier llamada en cualquier API de Windows Mixed Reality antes de crear el contexto remoto puede producir un comportamiento inesperado. El enfoque recomendado es crear el contexto remoto tan pronto como sea posible antes de la interacción con cualquier API de realidad mixta. Nunca mezcle objetos creados o recuperados a través de cualquier API de realidad mixta de Windows antes de la llamada a CreateRemoteContext con objetos creados o recuperados después.

A continuación, es necesario crear el espacio holográfica. No es necesario especificar CoreWindow. Las aplicaciones de escritorio que no tienen un CoreWindow solo pueden pasar ```nullptr```un.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Conexión al dispositivo

Una vez que la aplicación host esté lista para la representación de contenido, se puede establecer una conexión con el dispositivo.

La conexión puede realizarse de una de estas dos maneras.
1) La aplicación host se conecta al reproductor que se ejecuta en el dispositivo.
2) El reproductor que se ejecuta en el dispositivo se conecta a la aplicación host.

Para establecer una conexión desde la aplicación host a HoloLens 2, llame ```Connect``` al método en el contexto remoto y especifique el nombre de host y el puerto. El puerto que usa el reproductor de comunicación remota holográfica es **8265**.

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
>Como con cualquier C++API ```Connect``` de/WinRT puede producir un WinRT:: hresult_error que debe controlarse.

>[!TIP]
>Para evitar el [ C++](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) uso de la proyección de ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` lenguaje/WinRT se puede incluir el archivo que se encuentra dentro del paquete NuGet de Holographic Remoting. Contiene declaraciones de las interfaces COM subyacentes. No obstante, C++se recomienda el uso de/WinRT.

Para realizar escuchas de conexiones entrantes en la aplicación host, puede ```Listen``` llamar al método. El puerto de enlace y el puerto de transporte se pueden especificar durante esta llamada. El puerto de enlace se usa para el protocolo de enlace inicial. A continuación, los datos se envían a través del puerto de transporte. De forma predeterminada, se usan **8265** y **8266** .

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
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` En el paquete NuGet se incluye documentación detallada para la API expuesta por la comunicación remota holográfica.

## <a name="handling-remoting-specific-events"></a>Controlar eventos específicos de la comunicación remota

El contexto remoto expone tres eventos que son importantes para supervisar el estado de una conexión.
1) Conectado: Se desencadena cuando se ha establecido correctamente una conexión con el dispositivo.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnection: Se desencadena si se cierra una conexión establecida o no se pudo establecer una conexión.
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
3) En escucha: Cuando se inicia la escucha de conexiones entrantes.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Además, se puede consultar el estado de la ```ConnectionState``` conexión utilizando la propiedad en el contexto remoto.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Control de eventos de voz

El uso de la interfaz de voz remota es posible registrar los desencadenadores de voz con HoloLens 2 y hacerlos remotos en la aplicación host.

Este miembro adicional es necesario para realizar el seguimiento del estado de la voz remota.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

En primer lugar, es necesario recuperar la interfaz de voz remota.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Con un método auxiliar asincrónico, puede inicializar la voz remota. Esto debe hacerse de forma asincrónica, ya que la inicialización puede tardar un tiempo considerable. [Simultaneidad y operaciones asincrónicas C++con/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) explica cómo crear funciones asincrónicas con/WinRT. C++

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
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"en-US", grammarFile, dictionary);
}
```

Hay dos maneras de especificar frases que se reconocerán.
1) Especificación dentro de un archivo XML de gramática de voz. Vea [Cómo crear una gramática XML básica](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) para obtener más información.
2) Especifique pasándolos dentro del vector del diccionario a ```ApplyParameters```.

Dentro de la devolución de llamada OnRecognizedSpeech, los eventos de voz se pueden procesar a continuación:

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
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

## <a name="preview-streamed-content-locally"></a>Vista previa del contenido transmitido localmente

Para mostrar el mismo contenido en la aplicación host que se envía al dispositivo, se ```OnSendFrame``` puede usar el evento del contexto remoto. El ```OnSendFrame``` evento se desencadena cada vez que la biblioteca de acceso remoto holográfica envía el marco actual al dispositivo remoto. Este es el momento ideal para tomar el contenido y también dividirlo en la ventana de escritorio o UWP.

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

## <a name="optional-custom-data-channels"></a>Opcional: Canales de datos personalizados

Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión remota ya establecida. Vea [canales de datos personalizados](holographic-remoting-custom-data-channels.md) para obtener más información.

## <a name="see-also"></a>Vea también
* [Escritura de una aplicación de reproductor remoto holográfica personalizada](holographic-remoting-create-player.md)
* [Canales de datos personalizados de control remoto de holografías](holographic-remoting-custom-data-channels.md)
* [Establecimiento de una conexión segura con Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
