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
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="4b77d-104">Transferencias de delimitadores locales en DirectX</span><span class="sxs-lookup"><span data-stu-id="4b77d-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="4b77d-105">En situaciones en las que no se pueden usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">delimitadores espaciales de Azure</a>, las transferencias de delimitadores locales permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.</span><span class="sxs-lookup"><span data-stu-id="4b77d-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="4b77d-106">Las transferencias de delimitadores locales proporcionan una recuperación de delimitador menos sólida que los delimitadores <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">espaciales de Azure</a>y los dispositivos iOS y Android no se admiten en este enfoque.</span><span class="sxs-lookup"><span data-stu-id="4b77d-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="4b77d-107">Los fragmentos de código de este artículo muestran actualmente el uso C++de/CX en lugar de/WinRT compatible C++con C + +17, tal y como se usa en la [ C++ plantilla de proyecto holográfica](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="4b77d-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4b77d-108">Los conceptos son equivalentes para C++un proyecto de/WinRT, aunque tendrá que traducir el código.</span><span class="sxs-lookup"><span data-stu-id="4b77d-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="4b77d-109">Transferir delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="4b77d-109">Transferring spatial anchors</span></span>

<span data-ttu-id="4b77d-110">Puede transferir delimitadores espaciales entre dispositivos de Windows Mixed Reality mediante [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="4b77d-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="4b77d-111">Esta API le permite agrupar un delimitador con todos los datos de sensor necesarios para encontrar ese lugar exacto en el mundo y, a continuación, importar ese lote en otro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4b77d-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="4b77d-112">Una vez que la aplicación en el segundo dispositivo ha importado ese delimitador, cada aplicación puede representar hologramas usando el sistema de coordenadas del delimitador espacial compartido, que aparecerá en el mismo lugar del mundo real.</span><span class="sxs-lookup"><span data-stu-id="4b77d-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="4b77d-113">Tenga en cuenta que los anclajes espaciales no pueden transferirse entre diferentes tipos de dispositivos, por ejemplo, es posible que no se pueda localizar un anclaje espacial de HoloLens mediante un casco envolvente.</span><span class="sxs-lookup"><span data-stu-id="4b77d-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="4b77d-114">Los delimitadores transferidos tampoco son compatibles con dispositivos iOS o Android.</span><span class="sxs-lookup"><span data-stu-id="4b77d-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="4b77d-115">Configuración de la aplicación para usar la funcionalidad spatialPerception</span><span class="sxs-lookup"><span data-stu-id="4b77d-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="4b77d-116">Se debe conceder permiso a la aplicación para usar la funcionalidad spatialPerception antes de poder usar [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="4b77d-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="4b77d-117">Esto es necesario porque la transferencia de un delimitador espacial implica compartir imágenes de sensor recopiladas a lo largo del tiempo en proximidad de ese delimitador, lo que puede incluir información confidencial.</span><span class="sxs-lookup"><span data-stu-id="4b77d-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="4b77d-118">Declare esta funcionalidad en el archivo package. appxmanifest de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4b77d-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="4b77d-119">A continuación te mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4b77d-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="4b77d-120">La funcionalidad proviene del espacio de nombres **uap2** .</span><span class="sxs-lookup"><span data-stu-id="4b77d-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="4b77d-121">Para obtener acceso a este espacio de nombres en el manifiesto, inclúyalo como un atributo *xlmns* en el elemento &lt;paquete >.</span><span class="sxs-lookup"><span data-stu-id="4b77d-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="4b77d-122">A continuación te mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4b77d-122">Here's an example:</span></span>

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="4b77d-123">**Nota:** La aplicación tendrá que solicitar la funcionalidad en tiempo de ejecución para poder acceder a las API de exportación e importación de SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="4b77d-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="4b77d-124">Vea [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) en los ejemplos siguientes.</span><span class="sxs-lookup"><span data-stu-id="4b77d-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="4b77d-125">Serializar los datos del delimitador exportándolos con el SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="4b77d-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="4b77d-126">En el ejemplo de código se incluye una función auxiliar para exportar (serializar) los datos [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) .</span><span class="sxs-lookup"><span data-stu-id="4b77d-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="4b77d-127">Esta API de exportación serializa todos los delimitadores de una colección de pares clave-valor que asocian cadenas con delimitadores.</span><span class="sxs-lookup"><span data-stu-id="4b77d-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="4b77d-128">En primer lugar, es necesario configurar el flujo de datos.</span><span class="sxs-lookup"><span data-stu-id="4b77d-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="4b77d-129">Esto nos permitirá 1). Use TryExportAnchorsAsync para colocar los datos en un búfer que pertenezca a la aplicación y 2). leer datos del flujo de búfer de bytes exportado, que es un flujo de datos de WinRT, en nuestro propio búfer de memoria, que es un objeto STD:: Vector&lt;Byte >.</span><span class="sxs-lookup"><span data-stu-id="4b77d-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="4b77d-130">Necesitamos solicitar permiso para tener acceso a los datos espaciales, incluidos los delimitadores que exporta el sistema.</span><span class="sxs-lookup"><span data-stu-id="4b77d-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="4b77d-131">Si obtenemos el permiso y se exportan los delimitadores, podemos leer el flujo de datos.</span><span class="sxs-lookup"><span data-stu-id="4b77d-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="4b77d-132">En este caso, también se muestra cómo crear DataReader y InputStream usaremos para leer los datos.</span><span class="sxs-lookup"><span data-stu-id="4b77d-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="4b77d-133">Después de leer los bytes de la secuencia, podemos guardarlos en nuestro propio búfer de datos, como sucede.</span><span class="sxs-lookup"><span data-stu-id="4b77d-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="4b77d-134">Deserialización de datos de anclaje importándolos en el sistema mediante SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="4b77d-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="4b77d-135">En el ejemplo de código se incluye una función auxiliar para cargar los datos exportados previamente.</span><span class="sxs-lookup"><span data-stu-id="4b77d-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="4b77d-136">Esta función de deserialización proporciona una colección de pares clave-valor, similar a lo que proporciona el SpatialAnchorStore, excepto que se obtuvieron estos datos de otro origen, como un socket de red.</span><span class="sxs-lookup"><span data-stu-id="4b77d-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="4b77d-137">Puede procesar y motivar estos datos antes de almacenarlos sin conexión, mediante la memoria de la aplicación o, si procede, el SpatialAnchorStore de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4b77d-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="4b77d-138">En primer lugar, es necesario crear objetos Stream para tener acceso a los datos de delimitador.</span><span class="sxs-lookup"><span data-stu-id="4b77d-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="4b77d-139">Vamos a escribir los datos de nuestro búfer en un búfer del sistema, por lo que crearemos un objeto de escritura que escriba en un flujo de datos en memoria para lograr el objetivo de obtener los delimitadores de un búfer de bytes en el sistema como SpatialAnchors.</span><span class="sxs-lookup"><span data-stu-id="4b77d-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="4b77d-140">Una vez más, es necesario asegurarse de que la aplicación tiene permiso para exportar datos de anclaje espacial, lo que podría incluir información privada sobre el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="4b77d-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="4b77d-141">Si se permite el acceso, se pueden escribir bytes del búfer en un flujo de datos del sistema.</span><span class="sxs-lookup"><span data-stu-id="4b77d-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="4b77d-142">Si se almacenaran correctamente bytes en el flujo de datos, podemos intentar importar esos datos mediante SpatialAnchorTransferManager.</span><span class="sxs-lookup"><span data-stu-id="4b77d-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="4b77d-143">Si se pueden importar los datos, obtenemos una vista de mapa de pares clave-valor que asocian cadenas con delimitadores.</span><span class="sxs-lookup"><span data-stu-id="4b77d-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="4b77d-144">Podemos cargarlo en nuestra propia recopilación de datos en memoria y usar esa colección para buscar los delimitadores que estamos interesados en usar.</span><span class="sxs-lookup"><span data-stu-id="4b77d-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="4b77d-145">**Nota:** Solo porque puede importar un delimitador, no significa necesariamente que se pueda usar de inmediato.</span><span class="sxs-lookup"><span data-stu-id="4b77d-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="4b77d-146">El delimitador puede estar en un salón diferente u otra ubicación física completamente; no se puede localizar el delimitador hasta que el dispositivo que lo recibe tenga suficiente información visual sobre el entorno en el que se creó el delimitador, para restaurar la posición del delimitador en relación con el entorno actual conocido.</span><span class="sxs-lookup"><span data-stu-id="4b77d-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="4b77d-147">La implementación del cliente debe intentar localizar el delimitador en relación con el sistema de coordenadas local o el marco de referencia antes de continuar para intentar usarlo para el contenido en directo.</span><span class="sxs-lookup"><span data-stu-id="4b77d-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="4b77d-148">Por ejemplo, intente buscar el delimitador en relación con un sistema de coordenadas actual periódicamente hasta que el delimitador empiece a ser localizable.</span><span class="sxs-lookup"><span data-stu-id="4b77d-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="4b77d-149">Consideraciones especiales</span><span class="sxs-lookup"><span data-stu-id="4b77d-149">Special Considerations</span></span>

<span data-ttu-id="4b77d-150">La API de [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) permite exportar varios [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) en el mismo BLOB binario opaco.</span><span class="sxs-lookup"><span data-stu-id="4b77d-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="4b77d-151">Sin embargo, hay una diferencia sutil en cuanto a los datos que incluirá el BLOB, en función de si se exportan un único SpatialAnchor o varios SpatialAnchors en una sola llamada.</span><span class="sxs-lookup"><span data-stu-id="4b77d-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="4b77d-152">Exportación de un único SpatialAnchor</span><span class="sxs-lookup"><span data-stu-id="4b77d-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="4b77d-153">El BLOB contiene una representación del entorno en las proximidades de SpatialAnchor para que el entorno pueda reconocerse en el dispositivo que importa el SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="4b77d-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="4b77d-154">Una vez finalizada la importación, el nuevo SpatialAnchor estará disponible para el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4b77d-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="4b77d-155">Suponiendo que el usuario ha estado cerca del delimitador, se puede localizar y los hologramas adjuntos al SpatialAnchor se pueden representar.</span><span class="sxs-lookup"><span data-stu-id="4b77d-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="4b77d-156">Estos hologramas se mostrarán en la misma ubicación física que tenían en el dispositivo original que exportó el SpatialAnchor.</span><span class="sxs-lookup"><span data-stu-id="4b77d-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![Exportación de un único SpatialAnchor](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="4b77d-158">Exportación de varios SpatialAnchors</span><span class="sxs-lookup"><span data-stu-id="4b77d-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="4b77d-159">Al igual que la exportación de un único SpatialAnchor, el BLOB contiene una representación del entorno en las proximidades de todo el SpatialAnchors especificado.</span><span class="sxs-lookup"><span data-stu-id="4b77d-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="4b77d-160">Además, el BLOB contiene información sobre las conexiones entre el SpatialAnchors incluido, si se encuentran en el mismo espacio físico.</span><span class="sxs-lookup"><span data-stu-id="4b77d-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="4b77d-161">Esto significa que, si se importan dos SpatialAnchors cercanos, se puede localizar un holograma asociado al *segundo* SpatialAnchor aunque el dispositivo solo reconozca el entorno en torno a la *primera* SpatialAnchor, ya que los datos necesarios para calcular la transformación entre los dos SpatialAnchors se incluyeron en el BLOB.</span><span class="sxs-lookup"><span data-stu-id="4b77d-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="4b77d-162">Si los dos SpatialAnchors se exportaron individualmente (dos llamadas independientes a TryExportSpatialAnchors), es posible que no haya suficientes datos incluidos en el BLOB para los hologramas adjuntos al segundo SpatialAnchor que se puedan localizar cuando se encuentre el primero.</span><span class="sxs-lookup"><span data-stu-id="4b77d-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![Varios delimitadores exportados mediante una única llamada a TryExportAnchorsAsync](images/multipleanchors.png) ![Varios delimitadores exportados mediante una llamada TryExportAnchorsAsync independiente para cada delimitador](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="4b77d-165">Ejemplo: enviar datos de delimitador mediante Windows:: Networking:: StreamSocket</span><span class="sxs-lookup"><span data-stu-id="4b77d-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="4b77d-166">Aquí se proporciona un ejemplo de cómo usar los datos de delimitador exportados enviándolos a través de una red TCP.</span><span class="sxs-lookup"><span data-stu-id="4b77d-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="4b77d-167">Este es el HolographicSpatialAnchorTransferSample.</span><span class="sxs-lookup"><span data-stu-id="4b77d-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="4b77d-168">La clase WinRT StreamSocket usa la biblioteca de tareas de PPL.</span><span class="sxs-lookup"><span data-stu-id="4b77d-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="4b77d-169">En el caso de los errores de red, el error se devuelve a la siguiente tarea de la cadena mediante una excepción que se vuelve a iniciar.</span><span class="sxs-lookup"><span data-stu-id="4b77d-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="4b77d-170">La excepción contiene un valor HRESULT que indica el estado de error.</span><span class="sxs-lookup"><span data-stu-id="4b77d-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="4b77d-171">Usar un Windows:: Networking:: StreamSocketListener con TCP para enviar datos de delimitador exportados</span><span class="sxs-lookup"><span data-stu-id="4b77d-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="4b77d-172">Cree una instancia de servidor que escucha una conexión.</span><span class="sxs-lookup"><span data-stu-id="4b77d-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="4b77d-173">Cuando se recibe una conexión, use la conexión de socket de cliente para enviar datos de delimitador.</span><span class="sxs-lookup"><span data-stu-id="4b77d-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="4b77d-174">Ahora, podemos empezar a enviar un flujo de datos que contiene los datos del delimitador exportados.</span><span class="sxs-lookup"><span data-stu-id="4b77d-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="4b77d-175">Antes de poder enviar el flujo, primero debemos enviar un paquete de encabezado.</span><span class="sxs-lookup"><span data-stu-id="4b77d-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="4b77d-176">Este paquete de encabezado debe ser de longitud fija, y también debe indicar la longitud de la matriz variable de bytes que es el flujo de datos de delimitador; en el caso de este ejemplo, no hay ningún otro dato de encabezado para enviar, por lo que nuestro encabezado tiene una longitud de 4 bytes y contiene un entero de 32 bits sin signo.</span><span class="sxs-lookup"><span data-stu-id="4b77d-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="4b77d-177">Una vez que se ha enviado la longitud del flujo, en bytes, al cliente, podemos continuar escribiendo el flujo de datos en el flujo de socket.</span><span class="sxs-lookup"><span data-stu-id="4b77d-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="4b77d-178">Esto hará que los bytes de almacenamiento delimitados se envíen al cliente.</span><span class="sxs-lookup"><span data-stu-id="4b77d-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="4b77d-179">Como se indicó anteriormente en este tema, debemos estar preparados para controlar las excepciones que contienen mensajes de estado de error de red.</span><span class="sxs-lookup"><span data-stu-id="4b77d-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="4b77d-180">En el caso de los errores que no se esperan, podemos escribir la información de la excepción en la consola de depuración como tal.</span><span class="sxs-lookup"><span data-stu-id="4b77d-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="4b77d-181">Esto nos dará una pista sobre lo que ha sucedido si nuestro ejemplo de código no puede completar la conexión, o si no puede terminar de enviar los datos del delimitador.</span><span class="sxs-lookup"><span data-stu-id="4b77d-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="4b77d-182">Usar un Windows:: Networking:: StreamSocket con TCP para recibir datos de delimitador exportados</span><span class="sxs-lookup"><span data-stu-id="4b77d-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="4b77d-183">En primer lugar, tenemos que conectarnos al servidor.</span><span class="sxs-lookup"><span data-stu-id="4b77d-183">First, we have to connect to the server.</span></span> <span data-ttu-id="4b77d-184">En este ejemplo de código se muestra cómo crear y configurar un StreamSocket, y cómo crear un DataReader que puede usar para adquirir datos de red mediante la conexión de socket.</span><span class="sxs-lookup"><span data-stu-id="4b77d-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="4b77d-185">**Nota:** Si ejecuta este código de ejemplo, asegúrese de configurar e iniciar el servidor antes de iniciar el cliente.</span><span class="sxs-lookup"><span data-stu-id="4b77d-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="4b77d-186">Una vez que tenemos una conexión, podemos esperar a que el servidor envíe datos.</span><span class="sxs-lookup"><span data-stu-id="4b77d-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="4b77d-187">Para ello, se llama a LoadAsync en el lector de datos de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="4b77d-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="4b77d-188">El primer conjunto de bytes que recibirá siempre debe ser el paquete de encabezado, que indica la longitud de bytes del flujo de datos de delimitador tal y como se describe en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="4b77d-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="4b77d-189">...</span><span class="sxs-lookup"><span data-stu-id="4b77d-189">...</span></span>

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

<span data-ttu-id="4b77d-190">Después de haber recibido el paquete de encabezado, sabemos cuántos bytes de datos de delimitador deberíamos esperar.</span><span class="sxs-lookup"><span data-stu-id="4b77d-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="4b77d-191">Podemos continuar leyendo los bytes de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="4b77d-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="4b77d-192">Este es el código para recibir el flujo de datos de delimitador.</span><span class="sxs-lookup"><span data-stu-id="4b77d-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="4b77d-193">De nuevo, cargaremos primero los bytes de la secuencia. Esta operación puede tardar algún tiempo en completarse, ya que el StreamSocket espera a recibir esa cantidad de bytes de la red.</span><span class="sxs-lookup"><span data-stu-id="4b77d-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="4b77d-194">Una vez completada la operación de carga, podemos leer ese número de bytes.</span><span class="sxs-lookup"><span data-stu-id="4b77d-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="4b77d-195">Si se ha recibido el número de bytes que se esperan para el flujo de datos de delimitador, se pueden importar los datos de delimitador. en caso contrario, debe haber habido algún tipo de error.</span><span class="sxs-lookup"><span data-stu-id="4b77d-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="4b77d-196">Por ejemplo, esto puede ocurrir cuando la instancia de servidor termina antes de que pueda finalizar el envío del flujo de datos o la red deja de funcionar antes de que el cliente pueda recibir el flujo de datos completo.</span><span class="sxs-lookup"><span data-stu-id="4b77d-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="4b77d-197">De nuevo, debemos estar preparados para controlar los errores de red desconocidos.</span><span class="sxs-lookup"><span data-stu-id="4b77d-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="4b77d-198">Ya está.</span><span class="sxs-lookup"><span data-stu-id="4b77d-198">That's it!</span></span> <span data-ttu-id="4b77d-199">Ahora, debe tener suficiente información para intentar localizar los delimitadores recibidos a través de la red.</span><span class="sxs-lookup"><span data-stu-id="4b77d-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="4b77d-200">De nuevo, tenga en cuenta que el cliente debe tener suficientes datos de seguimiento visual para que el espacio Localice correctamente el delimitador. Si no funciona de inmediato, intente recorrer un rato.</span><span class="sxs-lookup"><span data-stu-id="4b77d-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="4b77d-201">Si sigue sin funcionar, haga que el servidor envíe más delimitadores y use las comunicaciones de red para aceptar una que funcione para el cliente.</span><span class="sxs-lookup"><span data-stu-id="4b77d-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="4b77d-202">Para probar esto, descargue HolographicSpatialAnchorTransferSample, configure las direcciones IP del cliente y del servidor y impleméntela en los dispositivos cliente y servidor HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4b77d-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b77d-203">Vea también</span><span class="sxs-lookup"><span data-stu-id="4b77d-203">See also</span></span>
* [<span data-ttu-id="4b77d-204">Biblioteca de patrones de procesamiento paralelo (PPL)</span><span class="sxs-lookup"><span data-stu-id="4b77d-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="4b77d-205">Windows. networking. StreamSocket</span><span class="sxs-lookup"><span data-stu-id="4b77d-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="4b77d-206">Windows. networking. StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="4b77d-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
