---
title: Transferencias de delimitadores locales en Unity
description: Transfiera los anclajes entre varios dispositivos de HoloLens en una aplicación de Unity.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Uso compartido, delimitador, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transferencia, transferencia de delimitador local, exportación de delimitadores, importación de delimitadores
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516138"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="a2cbb-104">Transferencias de delimitadores locales en Unity</span><span class="sxs-lookup"><span data-stu-id="a2cbb-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="a2cbb-105">En situaciones en las que no se pueden usar delimitadores espaciales de <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure</a>, las transferencias de delimitadores locales permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="a2cbb-106">Las transferencias de delimitadores locales proporcionan una recuperación de delimitador menos sólida que los delimitadores espaciales de <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure</a>y los dispositivos iOS y Android no se admiten en este enfoque.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="a2cbb-107">Establecimiento de la funcionalidad SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="a2cbb-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="a2cbb-108">Para que una aplicación transfiera los anclajes espaciales, se debe habilitar la funcionalidad *SpatialPerception* .</span><span class="sxs-lookup"><span data-stu-id="a2cbb-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="a2cbb-109">Cómo habilitar la funcionalidad *SpatialPerception* :</span><span class="sxs-lookup"><span data-stu-id="a2cbb-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="a2cbb-110">En el editor de Unity, abra el panel de **configuración del reproductor** (Editar > configuración del proyecto > Player).</span><span class="sxs-lookup"><span data-stu-id="a2cbb-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="a2cbb-111">Haga clic en la pestaña **"tienda Windows"**</span><span class="sxs-lookup"><span data-stu-id="a2cbb-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="a2cbb-112">Expanda **"configuración de publicación"** y seleccione la funcionalidad **"SpatialPerception"** en la lista **"funcionalidades"** .</span><span class="sxs-lookup"><span data-stu-id="a2cbb-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="a2cbb-113">Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o establecer manualmente [esta funcionalidad en el AppxManifest de Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span><span class="sxs-lookup"><span data-stu-id="a2cbb-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="a2cbb-114">Transferencia de delimitador</span><span class="sxs-lookup"><span data-stu-id="a2cbb-114">Anchor Transfer</span></span>

<span data-ttu-id="a2cbb-115">**System.IO** *UnityEngine. XR. WSA. Sharing*</span><span class="sxs-lookup"><span data-stu-id="a2cbb-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="a2cbb-116">**Tipo**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="a2cbb-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="a2cbb-117">Para transferir un [WorldAnchor](coordinate-systems-in-unity.md), debe establecer el delimitador que se va a transferir.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="a2cbb-118">El usuario de un HoloLens examina su entorno y, de forma manual o mediante programación, elige un punto en el espacio para que sea el delimitador de la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="a2cbb-119">Los datos que representan este punto se pueden serializar y transmitir a los otros dispositivos que compartan la experiencia.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="a2cbb-120">Después, cada dispositivo deserializa los datos de delimitador e intenta buscar ese punto en el espacio.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="a2cbb-121">Para que la transferencia de delimitador funcione, cada dispositivo debe haber explorado en el entorno suficiente, de modo que se pueda identificar el punto representado por el delimitador.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="a2cbb-122">Programa de instalación</span><span class="sxs-lookup"><span data-stu-id="a2cbb-122">Setup</span></span>

<span data-ttu-id="a2cbb-123">El código de ejemplo de esta página tiene algunos campos que se deben inicializar:</span><span class="sxs-lookup"><span data-stu-id="a2cbb-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="a2cbb-124">*GameObject rootGameObject* es un *GameObject* en Unity que tiene un componente *WorldAnchor* en él.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="a2cbb-125">Un usuario de la experiencia compartida colocará esta *GameObject* y exportará los datos a los demás usuarios.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="a2cbb-126">*WorldAnchor gameRootAnchor* es *UnityEngine. XR. WSA. WorldAnchor* que se encuentra en *rootGameObject*.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="a2cbb-127">*Byte [] importedData* es una matriz de bytes para el delimitador serializado que recibe cada cliente a través de la red.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="a2cbb-128">Exportador</span><span class="sxs-lookup"><span data-stu-id="a2cbb-128">Exporting</span></span>

<span data-ttu-id="a2cbb-129">Para exportar, solo necesitamos un *WorldAnchor* y para saber lo que le llamaremos de modo que tenga sentido para la aplicación receptora.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="a2cbb-130">Un cliente de la experiencia compartida realizará estos pasos para exportar el delimitador compartido:</span><span class="sxs-lookup"><span data-stu-id="a2cbb-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="a2cbb-131">Creación de un *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="a2cbb-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="a2cbb-132">Agregar *WorldAnchors* para transferir</span><span class="sxs-lookup"><span data-stu-id="a2cbb-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="a2cbb-133">Inicio de la exportación</span><span class="sxs-lookup"><span data-stu-id="a2cbb-133">Begin the export</span></span>
4. <span data-ttu-id="a2cbb-134">Controlar el evento *OnExportDataAvailable* a medida que los datos estén disponibles</span><span class="sxs-lookup"><span data-stu-id="a2cbb-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="a2cbb-135">Controlar el evento *OnExportComplete*</span><span class="sxs-lookup"><span data-stu-id="a2cbb-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="a2cbb-136">Creamos un *WorldAnchorTransferBatch* para encapsular lo que se va a transferir y exportarlo en bytes:</span><span class="sxs-lookup"><span data-stu-id="a2cbb-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="a2cbb-137">A medida que los datos estén disponibles, envíe los bytes al cliente o búfer a medida que los segmentos de datos estén disponibles y envíe los medios que desee:</span><span class="sxs-lookup"><span data-stu-id="a2cbb-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="a2cbb-138">Una vez completada la exportación, si se ha producido un error en la transferencia de datos y en la serialización, indique al cliente que descarte los datos.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="a2cbb-139">Si la serialización se realizó correctamente, indique al cliente que se han transferido todos los datos y que se puede iniciar la importación:</span><span class="sxs-lookup"><span data-stu-id="a2cbb-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="a2cbb-140">Importa</span><span class="sxs-lookup"><span data-stu-id="a2cbb-140">Importing</span></span>

<span data-ttu-id="a2cbb-141">Después de recibir todos los bytes del remitente, se pueden volver a importar los datos en un *WorldAnchorTransferBatch* y bloquear el objeto de juego raíz en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="a2cbb-142">Nota: la importación a veces producirá un error temporal y se debe volver a intentar:</span><span class="sxs-lookup"><span data-stu-id="a2cbb-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="a2cbb-143">Después de que un *GameObject* se bloquee a través de la llamada de *LockObject* , tendrá un *WorldAnchor* que lo mantendrá en la misma posición física del mundo, pero puede estar en una ubicación diferente en el espacio de coordenadas de Unity que otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="a2cbb-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

