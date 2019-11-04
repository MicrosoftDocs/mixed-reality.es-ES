---
title: Canales de datos personalizados de Holographic Remoting
description: Los canales de datos personalizados se pueden usar para enviar datos de usuario a través de la conexión de Holographic Remoting ya establecida.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: a862fa52695c7bfb94b58c6c0b85606a112835da
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434275"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="12b61-104">Canales de datos personalizados de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="12b61-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="12b61-105">Esta guía es específica de Holographic Remoting en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="12b61-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="12b61-106">Usar canales de datos personalizados para enviar datos personalizados a través de una conexión de comunicación remota establecida.</span><span class="sxs-lookup"><span data-stu-id="12b61-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="12b61-107">Los canales de datos personalizados requieren una aplicación host personalizada y una aplicación de reproductor personalizada, ya que permite la comunicación entre las dos aplicaciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="12b61-107">Custom data channels require a custom host app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="12b61-108">Puede encontrar un ejemplo sencillo de ping-pong en los ejemplos de host y reproductor dentro del repositorio de github de ejemplos de la [comunicación remota de Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="12b61-108">A simple ping-pong example can be found in the host and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="12b61-109">Quite los comentarios ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` dentro de los archivos SampleHostMain. h/SamplePlayerMain. h para habilitar el código de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="12b61-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleHostMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="12b61-110">Creación de un canal de datos personalizado</span><span class="sxs-lookup"><span data-stu-id="12b61-110">Create a custom data channel</span></span>


<span data-ttu-id="12b61-111">Para crear un canal de datos personalizado, se necesitan los siguientes campos:</span><span class="sxs-lookup"><span data-stu-id="12b61-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="12b61-112">Una vez establecida correctamente una conexión, la creación de nuevos canales de datos se puede iniciar desde el lado del host y/o el jugador.</span><span class="sxs-lookup"><span data-stu-id="12b61-112">After a connection was successfully established, the creation of new data channels can be initiated from either the host side and/or the player side.</span></span> <span data-ttu-id="12b61-113">Tanto RemoteContext como PlayerContext proporcionan un método ```CreateDataChannel()``` para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="12b61-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="12b61-114">El primer parámetro es el identificador de canal que se usa para identificar el canal de datos en las operaciones de susequent.</span><span class="sxs-lookup"><span data-stu-id="12b61-114">The first parameter is the channel ID which is used to identify the data channel in susequent operations.</span></span> <span data-ttu-id="12b61-115">El segundo parámetro es la prioridad que especifica la prioridad con la que se transfieren los datos de este canal al otro lado.</span><span class="sxs-lookup"><span data-stu-id="12b61-115">The second paramter is the priority which specifies the priority with which data of this channel is transfered to the other side.</span></span> <span data-ttu-id="12b61-116">El intervalo válido para los ID. de canal es 0 hasta 63 para el lado del host y 64 hasta la 127 para el jugador incluido.</span><span class="sxs-lookup"><span data-stu-id="12b61-116">The valid range for channel IDs is 0 up to and including 63 for the host side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="12b61-117">Las prioridades válidas son ```Low```, ```Medium``` o ```High``` (en ambos lados).</span><span class="sxs-lookup"><span data-stu-id="12b61-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="12b61-118">Para iniciar la creación de un canal de datos en el lado **host** :</span><span class="sxs-lookup"><span data-stu-id="12b61-118">To initiate the creation of a data channel on the **host** side:</span></span>
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="12b61-119">Para iniciar la creación de un canal de datos en el lado del **reproductor** :</span><span class="sxs-lookup"><span data-stu-id="12b61-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="12b61-120">Para crear un nuevo canal de datos personalizado, solo un lado (host o reproductor) debe llamar al método ```CreateDataChannel```.</span><span class="sxs-lookup"><span data-stu-id="12b61-120">To create a new custom data channel, only one side (either host or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="12b61-121">Control de eventos de canal de datos personalizados</span><span class="sxs-lookup"><span data-stu-id="12b61-121">Handling custom data channel events</span></span>

<span data-ttu-id="12b61-122">Para establecer un canal de datos personalizado, es necesario controlar el evento de ```OnDataChannelCreated``` (tanto en el reproductor como en el lado del host).</span><span class="sxs-lookup"><span data-stu-id="12b61-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the host side).</span></span> <span data-ttu-id="12b61-123">Se desencadena cuando se crea un canal de datos de usuario en cualquier lado y proporciona un ```IDataChannel``` objeto, que se puede usar para enviar y recibir datos a través de este canal.</span><span class="sxs-lookup"><span data-stu-id="12b61-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="12b61-124">Para registrar un agente de escucha en el evento ```OnDataChannelCreated```:</span><span class="sxs-lookup"><span data-stu-id="12b61-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="12b61-125">Para recibir una notificación cuando se reciban los datos, Regístrese en el evento ```OnDataReceived``` en el objeto ```IDataChannel``` proporcionado por el controlador de ```OnDataChannelCreated```.</span><span class="sxs-lookup"><span data-stu-id="12b61-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="12b61-126">Regístrese en el evento ```OnClosed``` para recibir una notificación cuando se haya cerrado el canal de datos.</span><span class="sxs-lookup"><span data-stu-id="12b61-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="12b61-127">Envío de datos</span><span class="sxs-lookup"><span data-stu-id="12b61-127">Sending data</span></span>

<span data-ttu-id="12b61-128">Para enviar datos a través de un canal de datos personalizado, use el método ```IDataChannel::SendData()```.</span><span class="sxs-lookup"><span data-stu-id="12b61-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="12b61-129">El primer parámetro es una ```winrt::array_view<const uint8_t>``` a los datos que se deben enviar.</span><span class="sxs-lookup"><span data-stu-id="12b61-129">The first paramter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="12b61-130">El segundo parámetro especifica si se deben volver a enviar los datos, hasta que el otro lado confirme la recepción.</span><span class="sxs-lookup"><span data-stu-id="12b61-130">The second parameter specifies wheter the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="12b61-131">En caso de condiciones de red erróneas, el mismo paquete de datos podría llegar más de una vez.</span><span class="sxs-lookup"><span data-stu-id="12b61-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="12b61-132">El código receptor debe ser capaz de controlar esta situación.</span><span class="sxs-lookup"><span data-stu-id="12b61-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="12b61-133">Cerrar un canal de datos personalizado</span><span class="sxs-lookup"><span data-stu-id="12b61-133">Closing a custom data channel</span></span>

<span data-ttu-id="12b61-134">Para cerrar un canal de datos personalizado, use el método ```IDataChannel::Close()```.</span><span class="sxs-lookup"><span data-stu-id="12b61-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="12b61-135">Los dos lados recibirán una notificación por el evento ```OnClosed``` una vez que se haya cerrado el canal de datos personalizado.</span><span class="sxs-lookup"><span data-stu-id="12b61-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="12b61-136">Consulta también</span><span class="sxs-lookup"><span data-stu-id="12b61-136">See Also</span></span>
* [<span data-ttu-id="12b61-137">Escritura de una aplicación de host de Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="12b61-137">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="12b61-138">Escritura de una aplicación de reproductor remoto holográfica personalizada</span><span class="sxs-lookup"><span data-stu-id="12b61-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="12b61-139">Solución de problemas y limitaciones de la comunicación remota holográfica</span><span class="sxs-lookup"><span data-stu-id="12b61-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="12b61-140">Términos de licencia del software de control remoto de holografías</span><span class="sxs-lookup"><span data-stu-id="12b61-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="12b61-141">Declaración de privacidad de Microsoft</span><span class="sxs-lookup"><span data-stu-id="12b61-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
