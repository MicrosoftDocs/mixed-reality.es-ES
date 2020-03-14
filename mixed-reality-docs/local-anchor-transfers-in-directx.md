---
title: Transferencias de delimitadores locales en DirectX
description: Explica cómo sincronizar dos dispositivos HoloLens transfiriendo anclajes espaciales.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, sincronizar, delimitador espacial, transferencia, multijugador, vista, escenario, tutorial, código de ejemplo, transferencia, transferencia de delimitador local, exportación de delimitadores, importación de delimitadores
ms.openlocfilehash: f961862c3c49872484683e264fb9c62b5d0b60ee
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376032"
---
# <a name="local-anchor-transfers-in-directx"></a>Transferencias de delimitadores locales en DirectX

En situaciones en las que no se pueden usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">delimitadores espaciales de Azure</a>, las transferencias de delimitadores locales permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.

>[!NOTE]
>Las transferencias de delimitadores locales proporcionan una recuperación de delimitador menos sólida que los delimitadores <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">espaciales de Azure</a>y los dispositivos iOS y Android no se admiten en este enfoque.

>[!NOTE]
>Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).  Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.

## <a name="transferring-spatial-anchors"></a>Transferir delimitadores espaciales

Puede transferir delimitadores espaciales entre dispositivos de Windows Mixed Reality mediante [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Esta API le permite agrupar un delimitador con todos los datos de sensor necesarios para encontrar ese lugar exacto en el mundo y, a continuación, importar ese lote en otro dispositivo. Una vez que la aplicación en el segundo dispositivo ha importado ese delimitador, cada aplicación puede representar hologramas usando el sistema de coordenadas del delimitador espacial compartido, que aparecerá en el mismo lugar del mundo real.

Tenga en cuenta que los anclajes espaciales no pueden transferirse entre diferentes tipos de dispositivos, por ejemplo, es posible que no se pueda localizar un anclaje espacial de HoloLens mediante un casco envolvente.  Los delimitadores transferidos tampoco son compatibles con dispositivos iOS o Android.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Configuración de la aplicación para usar la funcionalidad spatialPerception

Se debe conceder permiso a la aplicación para usar la funcionalidad spatialPerception antes de poder usar [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx). Esto es necesario porque la transferencia de un delimitador espacial implica compartir imágenes de sensor recopiladas a lo largo del tiempo en proximidad de ese delimitador, lo que puede incluir información confidencial.

Declare esta funcionalidad en el archivo package. appxmanifest de la aplicación. A continuación te mostramos un ejemplo:

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

La funcionalidad proviene del espacio de nombres **uap2** . Para obtener acceso a este espacio de nombres en el manifiesto, inclúyalo como un atributo *xlmns* en el elemento &lt;paquete >. A continuación te mostramos un ejemplo:

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**Nota:** La aplicación tendrá que solicitar la funcionalidad en tiempo de ejecución para poder acceder a las API de exportación e importación de SpatialAnchor. Vea [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) en los ejemplos siguientes.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>Serializar los datos del delimitador exportándolos con el SpatialAnchorTransferManager

En el ejemplo de código se incluye una función auxiliar para exportar (serializar) los datos [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) . Esta API de exportación serializa todos los delimitadores de una colección de pares clave-valor que asocian cadenas con delimitadores.

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

En primer lugar, es necesario configurar el flujo de datos. Esto nos permitirá 1). Use TryExportAnchorsAsync para colocar los datos en un búfer que pertenezca a la aplicación y 2). leer datos del flujo de búfer de bytes exportado, que es un flujo de datos de WinRT, en nuestro propio búfer de memoria, que es un objeto STD:: Vector&lt;Byte >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

Necesitamos solicitar permiso para tener acceso a los datos espaciales, incluidos los delimitadores que exporta el sistema.

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

Si obtenemos el permiso y se exportan los delimitadores, podemos leer el flujo de datos. En este caso, también se muestra cómo crear DataReader y InputStream usaremos para leer los datos.

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

Después de leer los bytes de la secuencia, podemos guardarlos en nuestro propio búfer de datos, como sucede.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>Deserialización de datos de anclaje importándolos en el sistema mediante SpatialAnchorTransferManager

En el ejemplo de código se incluye una función auxiliar para cargar los datos exportados previamente. Esta función de deserialización proporciona una colección de pares clave-valor, similar a lo que proporciona el SpatialAnchorStore, excepto que se obtuvieron estos datos de otro origen, como un socket de red. Puede procesar y motivar estos datos antes de almacenarlos sin conexión, mediante la memoria de la aplicación o, si procede, el SpatialAnchorStore de la aplicación.

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

En primer lugar, es necesario crear objetos Stream para tener acceso a los datos de delimitador. Vamos a escribir los datos de nuestro búfer en un búfer del sistema, por lo que crearemos un objeto de escritura que escriba en un flujo de datos en memoria para lograr el objetivo de obtener los delimitadores de un búfer de bytes en el sistema como SpatialAnchors.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

Una vez más, es necesario asegurarse de que la aplicación tiene permiso para exportar datos de anclaje espacial, lo que podría incluir información privada sobre el entorno del usuario.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

Si se permite el acceso, se pueden escribir bytes del búfer en un flujo de datos del sistema.

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

Si se almacenaran correctamente bytes en el flujo de datos, podemos intentar importar esos datos mediante SpatialAnchorTransferManager.

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

Si se pueden importar los datos, obtenemos una vista de mapa de pares clave-valor que asocian cadenas con delimitadores. Podemos cargarlo en nuestra propia recopilación de datos en memoria y usar esa colección para buscar los delimitadores que estamos interesados en usar.

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

**Nota:** Solo porque puede importar un delimitador, no significa necesariamente que se pueda usar de inmediato. El delimitador puede estar en un salón diferente u otra ubicación física completamente; no se puede localizar el delimitador hasta que el dispositivo que lo recibe tenga suficiente información visual sobre el entorno en el que se creó el delimitador, para restaurar la posición del delimitador en relación con el entorno actual conocido. La implementación del cliente debe intentar localizar el delimitador en relación con el sistema de coordenadas local o el marco de referencia antes de continuar para intentar usarlo para el contenido en directo. Por ejemplo, intente buscar el delimitador en relación con un sistema de coordenadas actual periódicamente hasta que el delimitador empiece a ser localizable.

## <a name="special-considerations"></a>Consideraciones especiales

La API de [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) permite exportar varios [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) en el mismo BLOB binario opaco. Sin embargo, hay una diferencia sutil en cuanto a los datos que incluirá el BLOB, en función de si se exportan un único SpatialAnchor o varios SpatialAnchors en una sola llamada.

### <a name="export-of-a-single-spatialanchor"></a>Exportación de un único SpatialAnchor

El BLOB contiene una representación del entorno en las proximidades de SpatialAnchor para que el entorno pueda reconocerse en el dispositivo que importa el SpatialAnchor. Una vez finalizada la importación, el nuevo SpatialAnchor estará disponible para el dispositivo. Suponiendo que el usuario ha estado cerca del delimitador, se puede localizar y los hologramas adjuntos al SpatialAnchor se pueden representar. Estos hologramas se mostrarán en la misma ubicación física que tenían en el dispositivo original que exportó el SpatialAnchor.

![Exportación de un único SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>Exportación de varios SpatialAnchors

Al igual que la exportación de un único SpatialAnchor, el BLOB contiene una representación del entorno en las proximidades de todo el SpatialAnchors especificado. Además, el BLOB contiene información sobre las conexiones entre el SpatialAnchors incluido, si se encuentran en el mismo espacio físico. Esto significa que, si se importan dos SpatialAnchors cercanos, se puede localizar un holograma asociado al *segundo* SpatialAnchor aunque el dispositivo solo reconozca el entorno en torno a la *primera* SpatialAnchor, ya que los datos necesarios para calcular la transformación entre los dos SpatialAnchors se incluyeron en el BLOB. Si los dos SpatialAnchors se exportaron individualmente (dos llamadas independientes a TryExportSpatialAnchors), es posible que no haya suficientes datos incluidos en el BLOB para los hologramas adjuntos al segundo SpatialAnchor que se puedan localizar cuando se encuentre el primero.

![Varios delimitadores exportados mediante una única llamada a TryExportAnchorsAsync](images/multipleanchors.png) ![Varios delimitadores exportados mediante una llamada TryExportAnchorsAsync independiente para cada delimitador](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>Ejemplo: enviar datos de delimitador mediante Windows:: Networking:: StreamSocket

Aquí se proporciona un ejemplo de cómo usar los datos de delimitador exportados enviándolos a través de una red TCP. Este es el HolographicSpatialAnchorTransferSample.

La clase WinRT StreamSocket usa la biblioteca de tareas de PPL. En el caso de los errores de red, el error se devuelve a la siguiente tarea de la cadena mediante una excepción que se vuelve a iniciar. La excepción contiene un valor HRESULT que indica el estado de error.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Usar un Windows:: Networking:: StreamSocketListener con TCP para enviar datos de delimitador exportados

Cree una instancia de servidor que escucha una conexión.

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

Cuando se recibe una conexión, use la conexión de socket de cliente para enviar datos de delimitador.

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

Ahora, podemos empezar a enviar un flujo de datos que contiene los datos del delimitador exportados.

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

Antes de poder enviar el flujo, primero debemos enviar un paquete de encabezado. Este paquete de encabezado debe ser de longitud fija, y también debe indicar la longitud de la matriz variable de bytes que es el flujo de datos de delimitador; en el caso de este ejemplo, no hay ningún otro dato de encabezado para enviar, por lo que nuestro encabezado tiene una longitud de 4 bytes y contiene un entero de 32 bits sin signo.

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

Una vez que se ha enviado la longitud del flujo, en bytes, al cliente, podemos continuar escribiendo el flujo de datos en el flujo de socket. Esto hará que los bytes de almacenamiento delimitados se envíen al cliente.

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

Como se indicó anteriormente en este tema, debemos estar preparados para controlar las excepciones que contienen mensajes de estado de error de red. En el caso de los errores que no se esperan, podemos escribir la información de la excepción en la consola de depuración como tal. Esto nos dará una pista sobre lo que ha sucedido si nuestro ejemplo de código no puede completar la conexión, o si no puede terminar de enviar los datos del delimitador.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Usar un Windows:: Networking:: StreamSocket con TCP para recibir datos de delimitador exportados

En primer lugar, tenemos que conectarnos al servidor. En este ejemplo de código se muestra cómo crear y configurar un StreamSocket, y cómo crear un DataReader que puede usar para adquirir datos de red mediante la conexión de socket.

**Nota:** Si ejecuta este código de ejemplo, asegúrese de configurar e iniciar el servidor antes de iniciar el cliente.

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

Una vez que tenemos una conexión, podemos esperar a que el servidor envíe datos. Para ello, se llama a LoadAsync en el lector de datos de la secuencia.

El primer conjunto de bytes que recibirá siempre debe ser el paquete de encabezado, que indica la longitud de bytes del flujo de datos de delimitador tal y como se describe en la sección anterior.

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

Después de haber recibido el paquete de encabezado, sabemos cuántos bytes de datos de delimitador deberíamos esperar. Podemos continuar leyendo los bytes de la secuencia.

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

Este es el código para recibir el flujo de datos de delimitador. De nuevo, cargaremos primero los bytes de la secuencia. Esta operación puede tardar algún tiempo en completarse, ya que el StreamSocket espera a recibir esa cantidad de bytes de la red.

Una vez completada la operación de carga, podemos leer ese número de bytes. Si se ha recibido el número de bytes que se esperan para el flujo de datos de delimitador, se pueden importar los datos de delimitador. en caso contrario, debe haber habido algún tipo de error. Por ejemplo, esto puede ocurrir cuando la instancia de servidor termina antes de que pueda finalizar el envío del flujo de datos o la red deja de funcionar antes de que el cliente pueda recibir el flujo de datos completo.

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

De nuevo, debemos estar preparados para controlar los errores de red desconocidos.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

Ya está. Ahora, debe tener suficiente información para intentar localizar los delimitadores recibidos a través de la red. De nuevo, tenga en cuenta que el cliente debe tener suficientes datos de seguimiento visual para que el espacio Localice correctamente el delimitador. Si no funciona de inmediato, intente recorrer un rato. Si sigue sin funcionar, haga que el servidor envíe más delimitadores y use las comunicaciones de red para aceptar una que funcione para el cliente. Para probar esto, descargue HolographicSpatialAnchorTransferSample, configure las direcciones IP del cliente y del servidor y impleméntela en los dispositivos cliente y servidor HoloLens.

## <a name="see-also"></a>Vea también
* [Biblioteca de patrones de procesamiento paralelo (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows. networking. StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows. networking. StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
