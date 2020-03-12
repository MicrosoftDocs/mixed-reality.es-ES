---
title: Canales de datos personalizados de Holographic Remoting
description: Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión de Holographic Remoting ya establecida.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 8bfa19b7af0f3429130aabf70d9d11083bc56a52
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092294"
---
# <a name="custom-holographic-remoting-data-channels"></a>Canales de datos personalizados de Holographic Remoting

>[!NOTE]
>Esta guía es específica de Holographic Remoting en HoloLens 2.

Usar canales de datos personalizados para enviar datos personalizados a través de una conexión de comunicación remota establecida.

>[!IMPORTANT]
>Los canales de datos personalizados requieren una aplicación remota personalizada y una aplicación de reproductor personalizada, ya que permite la comunicación entre las dos aplicaciones personalizadas.

>[!TIP]
>Puede encontrar un ejemplo sencillo de ping-pong en los ejemplos de Remote y Player dentro del [repositorio de github de ejemplos](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)de la comunicación remota de Holographic. Quite los comentarios ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` dentro de los archivos SampleRemoteMain. h/SamplePlayerMain. h para habilitar el código de ejemplo.


## <a name="create-a-custom-data-channel"></a>Creación de un canal de datos personalizado


Para crear un canal de datos personalizado, se necesitan los siguientes campos:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Una vez establecida correctamente una conexión, la creación de nuevos canales de datos se puede iniciar desde el lado remoto o el reproductor. Tanto RemoteContext como PlayerContext proporcionan un método ```CreateDataChannel()``` para hacerlo. El primer parámetro es el identificador de canal que se utiliza para identificar el canal de datos en operaciones posteriores. El segundo parámetro es la prioridad que especifica la prioridad con la que se transfieren los datos de este canal al otro lado. El intervalo válido para los ID. de canal es 0 hasta 63 para el lado remoto y 64 hasta 127 para el jugador. Las prioridades válidas son ```Low```, ```Medium``` o ```High``` (en ambos lados).

Para iniciar la creación de un canal de datos en el lado **remoto** :
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Para iniciar la creación de un canal de datos en el lado del **reproductor** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Para crear un nuevo canal de datos personalizado, solo un lado (ya sea remoto o reproductor) debe llamar al método ```CreateDataChannel```.

## <a name="handling-custom-data-channel-events"></a>Control de eventos de canal de datos personalizados

Para establecer un canal de datos personalizado, es necesario controlar el evento ```OnDataChannelCreated``` (tanto en el reproductor como en el lado remoto). Se desencadena cuando se crea un canal de datos de usuario en cualquier lado y proporciona un ```IDataChannel``` objeto, que se puede usar para enviar y recibir datos a través de este canal.

Para registrar un agente de escucha en el evento ```OnDataChannelCreated```:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Para recibir una notificación cuando se reciban los datos, Regístrese en el evento ```OnDataReceived``` en el objeto ```IDataChannel``` proporcionado por el controlador de ```OnDataChannelCreated```. Regístrese en el evento ```OnClosed``` para recibir una notificación cuando se haya cerrado el canal de datos.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Envío de datos

Para enviar datos a través de un canal de datos personalizado, use el método ```IDataChannel::SendData()```. El primer parámetro es una ```winrt::array_view<const uint8_t>``` a los datos que se deben enviar. El segundo parámetro especifica dónde se deben volver a enviar los datos, hasta que el otro lado confirme la recepción. 

>[!IMPORTANT]
>En caso de condiciones de red erróneas, el mismo paquete de datos podría llegar más de una vez. El código receptor debe ser capaz de controlar esta situación.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Cerrar un canal de datos personalizado

Para cerrar un canal de datos personalizado, use el método ```IDataChannel::Close()```. Los dos lados recibirán una notificación por el evento ```OnClosed``` una vez que se haya cerrado el canal de datos personalizado.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Vea también
* [Escritura de una aplicación remota holográfica Remoting](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor remoto holográfica personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
