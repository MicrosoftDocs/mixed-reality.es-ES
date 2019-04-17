---
title: Transferencias de anclaje local en DirectX
description: Explica cómo sincronizar dos dispositivos HoloLens transfiriéndolo delimitadores espaciales.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, sincronizar, delimitador espacial, la transferencia, participan varios jugadores, ver, escenario, tutorial, código de ejemplo, transferencia, transferencia local de anclaje, exportación de anclaje, importación de anclaje
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605777"
---
# <a name="local-anchor-transfers-in-directx"></a>Transferencias de anclaje local en DirectX

En situaciones donde no se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, las transferencias de anclaje local habilitar un dispositivo HoloLens exportar un delimitador para ser importadas por un segundo dispositivo HoloLens.

>[!NOTE]
>Las transferencias de anclaje locales proporcionan menos sólida retirada de anclaje que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, y dispositivos iOS y Android no son compatibles con este enfoque.

>[!NOTE]
>Los fragmentos de código en este artículo actualmente muestran el uso de C++/CX en lugar de C ++ 17 conforme C++/WinRT como utiliza en el [ C++ plantilla de proyecto holographic](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes a un C++/WinRT del proyecto, aunque deberá traducir el código.

## <a name="transferring-spatial-anchors"></a>Transferir delimitadores espaciales

Puede transferir delimitadores espaciales entre dispositivos de Windows Mixed Reality utilizando el [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Esta API permite agrupar un delimitador con todos los datos de sensor auxiliares necesarios para buscar ese lugar exacto en el mundo y, a continuación, importar ese paquete en otro dispositivo. Una vez que la aplicación en el segundo dispositivo ha importado que fijan, cada aplicación puede representar mediante hologramas que comparte el sistema de coordenadas del anclaje espaciales, que aparecerá en el mismo lugar en el mundo real.

Tenga en cuenta que los anclajes espaciales no están posible transferir entre distintos tipos de dispositivos, por ejemplo un anclaje de HoloLens espacial no puede ser localizable mediante un auricular envolvente.  Delimitadores transferidos no también son compatibles con dispositivos iOS o Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configuración de la aplicación para utilizar la funcionalidad de spatialPerception

La aplicación debe tener permiso para utilizar la funcionalidad de spatialPerception antes de poder usar el [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Esto es necesario porque transferir un anclaje espacial implica compartir imágenes de sensor recopiladas con el tiempo en la proximidad de anclaje, lo que puede incluir información confidencial.

Declare esta capacidad en el archivo package.appxmanifest de la aplicación. Por ejemplo:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funcionalidad proviene de la **uap2** espacio de nombres. Para obtener acceso a este espacio de nombres en el manifiesto, incluirla como un *xlmns* atributo el &lt;paquete > elemento. Por ejemplo:

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**NOTA:** La aplicación debe solicitar la funcionalidad en tiempo de ejecución para que pueda acceder a SpatialAnchor exportación e importación de API. Consulte [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) en los ejemplos siguientes.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serializar los datos de anclaje exportándola el SpatialAnchorTransferManager

Una función auxiliar se incluye en el ejemplo de código para exportar (serializar) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) datos. Esta API exportación serializa todos los delimitadores en una colección de pares clave-valor asociar cadenas delimitadores.

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

En primer lugar, necesitamos configurar el flujo de datos. Esto nos permitirá a 1.) usar TryExportAnchorsAsync para colocar los datos en un búfer que pertenecen a la aplicación y 2). leer datos del flujo del búfer de bytes exportado, que es un flujo de datos de WinRT, en nuestro propio búfer de memoria, que es un std:: vector&lt;bytes >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Es necesario solicitar permiso para tener acceso a los datos espaciales, incluidos los delimitadores que se exportan por el sistema.

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

Si obtenemos permiso y se exportan los delimitadores, podemos leer el flujo de datos. En este caso, también se muestra cómo crear el DataReader y InputStream se usará para leer los datos.

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

Una vez que se leen los bytes en la secuencia, nos podemos guardar en nuestro propio búfer de datos de este modo.

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserializar los datos de anclaje, impórtelo en el sistema mediante la SpatialAnchorTransferManager

Una función auxiliar se incluye en el ejemplo de código para cargar datos exportados previamente. Esta función de deserialización proporciona una colección de pares clave-valor, similares a lo que proporciona el SpatialAnchorStore - salvo que obtuvimos estos datos en otro origen, como un socket de red. Puede procesar y analizar estos datos antes de almacenarlos en memoria de sin conexión, el uso de la aplicación, o (si procede) SpatialAnchorStore de la aplicación.

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

En primer lugar, necesitamos crear objetos de secuencia para obtener acceso a los datos de anclaje. Se va a escribir los datos desde el búfer en un búfer del sistema, por tanto, creamos un DataWriter que escribe en un flujo de datos en memoria con el fin de lograr nuestro objetivo de los delimitadores de un búfer de bytes en el sistema como SpatialAnchors.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Una vez más, necesitamos asegurarnos de que la aplicación tiene permiso para exportar los datos espaciales delimitador, lo que podrían incluir información confidencial sobre el entorno del usuario.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Si se permite el acceso, podemos escribir bytes del búfer en un flujo de datos del sistema.

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

Si tuviéramos correctas en el almacenamiento de bytes en el flujo de datos, podemos intentar importar los datos mediante el SpatialAnchorTransferManager.

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

Si los datos puede importarse, obtenemos una vista del mapa de asociación de cadenas con los delimitadores de pares de clave-valor. Podemos cargar esto en nuestro propio conjunto de datos en memoria y use esa colección para buscar los delimitadores que estamos interesados en usar.

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**NOTA:** Simplemente porque se puede importar un delimitador, no significa necesariamente que se puede usar inmediatamente. El delimitador podría estar en una sala diferente, o en otra ubicación física por completo; el delimitador no será localizable hasta que el dispositivo que se recibió tiene suficiente información visual sobre el entorno que se creó el delimitador, para restaurar la posición del delimitador en relación con el conocido entorno actual. La implementación del cliente debe intentar ubicar el delimitador en relación con su sistema de coordenadas local o un marco de referencia antes de continuar intentar usarlo para el contenido en vivo. Por ejemplo, intentar ubicar el delimitador en relación con un sistema de coordenadas actual periódicamente hasta que el delimitador comienza a ser localizable.

## <a name="special-considerations"></a>Consideraciones especiales

El [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API permite varios [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) que se exportarán en el mismo blob binario opaco. Sin embargo, hay una diferencia sutil en los datos que se va a incluir el blob, según determina si se exporta un SpatialAnchor único o varios SpatialAnchors en una sola llamada.

### <a name="export-of-a-single-spatialanchor"></a>Exportación de una sola SpatialAnchor

El blob contiene una representación del entorno en las proximidades del SpatialAnchor para que pueda reconocer el entorno en el dispositivo que importa el SpatialAnchor. Una vez finalizada la importación, el nuevo SpatialAnchor estarán disponible para el dispositivo. Suponiendo que el usuario ha sido recientemente en la proximidad del anclaje, sea localizable y se pueden representar hologramas conectados a la SpatialAnchor. Estos hologramas aparecerán en la misma ubicación física que lo hacían en el dispositivo original que exporta el SpatialAnchor.

![Exportación de una sola SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Exportación de varias SpatialAnchors

Al igual que la exportación de una sola SpatialAnchor, el blob contiene una representación del entorno en la proximidad de todas las SpatialAnchors especificados. Además, el blob contiene información sobre las conexiones entre el SpatialAnchors incluye, aunque se encuentren en el mismo espacio físico. Esto significa que si se importan dos SpatialAnchors cercanos, a continuación, un holograma asociado a la *segundo* SpatialAnchor sería localizable incluso si el dispositivo reconoce solo el entorno en torno a la *primera* SpatialAnchor, porque los datos suficientes para calcular una transformación entre los dos SpatialAnchors se incluyó en el blob. Si los dos SpatialAnchors se exportaron individualmente (dos diferentes llamadas a TryExportSpatialAnchors), a continuación, puede que no haya suficientes datos incluidos en el blob para hologramas conectados a la segunda SpatialAnchor sea localizable cuando la primera de ellas se encuentra.

![Varios delimitadores exportados mediante una sola llamada TryExportAnchorsAsync](images/multipleanchors.png) ![Varios delimitadores exportados mediante una llamada TryExportAnchorsAsync independiente para cada delimitador](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Por ejemplo: Enviar datos de anclaje mediante un Windows::Networking::StreamSocket

En este caso, se muestra un ejemplo de cómo usar los datos exportados de anclaje enviándolo a través de una red TCP. Se trata de la HolographicSpatialAnchorTransferSample.

La clase WinRT StreamSocket usa la biblioteca PPL. En el caso de errores de red, se devuelve el error a la siguiente tarea de la cadena con una excepción que se vuelve a producir. La excepción contiene un valor HRESULT que indica el estado de error.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Usar un Windows::Networking::StreamSocketListener con TCP para enviar datos exportados de anclaje

Crear una instancia del servidor que realiza escuchas para una conexión.

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

Cuando se recibe una conexión, use la conexión de socket de cliente para enviar datos de anclaje.

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

Ahora, podemos empezar a enviar una transmisión de datos que contiene los datos exportados de anclaje.

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

Antes de que podemos enviarle el propio flujo, en primer lugar, debemos enviar un paquete de encabezado. Este paquete de encabezado debe ser de longitud fija, y también debe indicar la longitud de la matriz de variables de bytes que es el flujo de datos del delimitador; en el caso de este ejemplo tenemos ningún otro dato de encabezado para enviar, por lo que el encabezado tiene una longitud de 4 bytes y contiene un entero de 32 bits sin signo.

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

Una vez que la longitud de la secuencia en bytes, se ha enviado al cliente, podemos continuar para escribir el propio flujo de datos en la secuencia de socket. Esto hará que los bytes de la tienda Premium se envíen al cliente.

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

Como se indicó anteriormente en este tema, debemos ser preparadas para controlar las excepciones que contiene los mensajes de estado de error de red. Errores que no se esperan, podemos escribir la información de la excepción a la consola de depuración de este modo. Esto nos dará una pista acerca de qué ha ocurrido si nuestro ejemplo de código no puede completar la conexión, o si no terminó de enviar los datos de anclaje.

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Utilice un Windows::Networking::StreamSocket con TCP para recibir los datos exportados de anclaje

En primer lugar, tenemos que conectarnos al servidor. Este ejemplo de código muestra cómo crear y configurar un StreamSocket y crear un DataReader, que puede usar para adquirir los datos de la red mediante la conexión de socket.

**NOTA:** Si ejecuta este código de ejemplo, asegúrese de que permite configurar e iniciar el servidor antes de iniciar al cliente.

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

Una vez que tenemos una conexión, nos podemos esperar el servidor enviar datos. Para hacerlo mediante una llamada a LoadAsync en el lector de secuencias de datos.

El primer conjunto de bytes que recibamos siempre debe ser el paquete de encabezado, lo que indica que el delimitador del flujo de longitud de bytes como se describe en la sección anterior.

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

Una vez que hayamos recibido el paquete de encabezado, sabemos que el número de bytes de datos de anclaje debemos esperar que. Podemos continuar para leer los bytes de la secuencia.

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

Este es nuestro código para recibir el flujo de datos de anclaje. De nuevo, se cargará en primer lugar los bytes del flujo; Esta operación puede tardar algún tiempo en completarse mientras espera la StreamSocket para recibir dicha cantidad de bytes de la red.

Una vez completada la operación de carga, podemos leer ese número de bytes. Si se recibe el número de bytes que se esperan para el flujo de datos Premium, podemos seguir adelante e importar los datos del delimitador; Si no es así, debe haber algún tipo de error. Por ejemplo, esto puede ocurrir cuando la instancia del servidor termina antes de que pueda terminar de enviar el flujo de datos o la red deja de funcionar antes de que el flujo de datos completa puede ser recibido por el cliente.

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

De nuevo, debemos ser preparadas para controlar los errores de red desconocido.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Ya está. Ahora, debe tener suficiente información para intentar ubicar los delimitadores que se reciben a través de la red. De nuevo, tenga en cuenta que el cliente debe tener suficientes datos de seguimiento visual para el espacio que se puede encontrar el delimitador. Si no funciona inmediatamente, intente deambulan durante un tiempo. Si sigue sin funcionar, tiene el servidor envía más delimitadores y usa las comunicaciones de red para coincidir con uno que funciona para el cliente. Puede probar esto descargando el HolographicSpatialAnchorTransferSample, configurar el cliente y direcciones IP del servidor y su implementación en los dispositivos HoloLens de cliente y servidor.

## <a name="see-also"></a>Vea también
* [Biblioteca de modelos paralelos (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
