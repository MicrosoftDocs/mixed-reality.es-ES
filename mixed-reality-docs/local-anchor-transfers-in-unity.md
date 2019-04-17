---
title: Transferencias de anclaje local en Unity
description: Transferir los delimitadores entre varios dispositivos de HoloLens en una aplicación de Unity.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Recursos compartidos, delimitador, WorldAnchor, MR compartir 250, WorldAnchorTransferBatch, SpatialPerception, transferencia, transferencia local de anclaje, exportación de anclaje, importación de anclaje
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605775"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="7282a-104">Transferencias de anclaje local en Unity</span><span class="sxs-lookup"><span data-stu-id="7282a-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="7282a-105">En situaciones donde no se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, las transferencias de anclaje local habilitar un dispositivo HoloLens exportar un delimitador para ser importadas por un segundo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7282a-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="7282a-106">Las transferencias de anclaje locales proporcionan menos sólida retirada de anclaje que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, y dispositivos iOS y Android no son compatibles con este enfoque.</span><span class="sxs-lookup"><span data-stu-id="7282a-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="7282a-107">Establecer la capacidad de SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="7282a-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="7282a-108">En orden para una aplicación transferir los anclajes de espaciales, el *SpatialPerception* posibilidad debe habilitarse.</span><span class="sxs-lookup"><span data-stu-id="7282a-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="7282a-109">Cómo habilitar el *SpatialPerception* capacidad:</span><span class="sxs-lookup"><span data-stu-id="7282a-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="7282a-110">En el Editor de Unity, abra el **"Configuración del Reproductor"** panel (Editar > configuración del proyecto > Reproductor)</span><span class="sxs-lookup"><span data-stu-id="7282a-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="7282a-111">Haga clic en el **"Windows Store"** ficha</span><span class="sxs-lookup"><span data-stu-id="7282a-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="7282a-112">Expanda **"Configuración de publicación"** y compruebe el **"SpatialPerception"** capacidad en el **"Capacidades"** lista</span><span class="sxs-lookup"><span data-stu-id="7282a-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="7282a-113">Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o manualmente [establecer esta funcionalidad en el AppxManifest en Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="7282a-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="7282a-114">Transferencia de anclaje</span><span class="sxs-lookup"><span data-stu-id="7282a-114">Anchor Transfer</span></span>

<span data-ttu-id="7282a-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="7282a-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="7282a-116">**Tipo**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="7282a-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="7282a-117">Para transferir un [WorldAnchor](coordinate-systems-in-unity.md), uno debe establecer el delimitador que se transferirá.</span><span class="sxs-lookup"><span data-stu-id="7282a-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="7282a-118">El usuario de uno HoloLens examina su entorno y manualmente o mediante programación, elige un punto en el espacio que el delimitador de la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="7282a-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="7282a-119">A continuación, se pueden serializar y transmitir a los otros dispositivos que están compartiendo en la experiencia de los datos que representa este punto.</span><span class="sxs-lookup"><span data-stu-id="7282a-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="7282a-120">Cada dispositivo, a continuación, deserializa los datos de anclaje e intenta localizar ese punto en el espacio.</span><span class="sxs-lookup"><span data-stu-id="7282a-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="7282a-121">En orden para transferir ancla para que funcione, cada dispositivo debe escaneen suficiente del entorno de modo que se puede identificar el punto representado por el delimitador.</span><span class="sxs-lookup"><span data-stu-id="7282a-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="7282a-122">Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="7282a-122">Setup</span></span>

<span data-ttu-id="7282a-123">El código de ejemplo en esta página tiene unos cuantos campos que deben inicializarse:</span><span class="sxs-lookup"><span data-stu-id="7282a-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="7282a-124">*GameObject rootGameObject* es un *GameObject* en Unity que tiene un *WorldAnchor* componente en él.</span><span class="sxs-lookup"><span data-stu-id="7282a-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="7282a-125">Un usuario en la experiencia compartida Esto colocará *GameObject* y exportar los datos a los demás usuarios.</span><span class="sxs-lookup"><span data-stu-id="7282a-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="7282a-126">*WorldAnchor gameRootAnchor* es el *UnityEngine.XR.WSA.WorldAnchor* que se encuentra en *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="7282a-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="7282a-127">*Byte [] importedData* es una matriz de bytes para el delimitador serializada recibe cada cliente a través de la red.</span><span class="sxs-lookup"><span data-stu-id="7282a-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="7282a-128">Exportar</span><span class="sxs-lookup"><span data-stu-id="7282a-128">Exporting</span></span>

<span data-ttu-id="7282a-129">Para exportar, sólo necesitamos un *WorldAnchor* y saber lo que llamaremos a lo que resulta conveniente para la aplicación receptora.</span><span class="sxs-lookup"><span data-stu-id="7282a-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="7282a-130">Un cliente en la experiencia compartida llevará a cabo estos pasos para exportar el delimitador compartido:</span><span class="sxs-lookup"><span data-stu-id="7282a-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="7282a-131">Crear un *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="7282a-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="7282a-132">Agregar el *WorldAnchors* para transferir</span><span class="sxs-lookup"><span data-stu-id="7282a-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="7282a-133">Iniciar la exportación</span><span class="sxs-lookup"><span data-stu-id="7282a-133">Begin the export</span></span>
4. <span data-ttu-id="7282a-134">Controlar la *OnExportDataAvailable* eventos como los datos se convierte en disponible</span><span class="sxs-lookup"><span data-stu-id="7282a-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="7282a-135">Controlar la *OnExportComplete* eventos</span><span class="sxs-lookup"><span data-stu-id="7282a-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="7282a-136">Creamos un *WorldAnchorTransferBatch* para encapsular lo que se pueden transferir y exportarlas a continuación, en bytes:</span><span class="sxs-lookup"><span data-stu-id="7282a-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="7282a-137">Cuando hay datos disponibles, enviar los bytes en el cliente o el búfer como segmentos de datos está disponible y enviar a través de cualquier medio deseado:</span><span class="sxs-lookup"><span data-stu-id="7282a-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="7282a-138">Una vez completada la exportación, si nos hemos transferir datos y la serialización no se pudo, indicar al cliente para descartar los datos.</span><span class="sxs-lookup"><span data-stu-id="7282a-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="7282a-139">Si la serialización se realizó correctamente, indicar al cliente que se ha transferido todos los datos y puede empezar a importar:</span><span class="sxs-lookup"><span data-stu-id="7282a-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="7282a-140">Importar</span><span class="sxs-lookup"><span data-stu-id="7282a-140">Importing</span></span>

<span data-ttu-id="7282a-141">Después de recibir todos los bytes del remitente, podemos importar los datos en un *WorldAnchorTransferBatch* y bloquear el objeto de juego de raíz en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="7282a-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="7282a-142">Nota: importación transiently a veces, se producirá un error y necesita volver a intentarlo:</span><span class="sxs-lookup"><span data-stu-id="7282a-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="7282a-143">Después de un *GameObject* está bloqueada mediante el *LockObject* llamada, tendrá un *WorldAnchor* que mantendrá en la misma posición física en el mundo, pero puede estar en un espacio que otros usuarios de coordenadas de ubicación diferente en el Unity.</span><span class="sxs-lookup"><span data-stu-id="7282a-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

