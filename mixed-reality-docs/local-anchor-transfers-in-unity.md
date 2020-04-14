---
title: Transferencias de delimitadores locales en Unity
description: Transfiera los anclajes entre varios dispositivos de HoloLens en una aplicación de Unity.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Uso compartido, delimitador, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, transferencia, transferencia de delimitador local, exportación de delimitadores, importación de delimitadores
ms.openlocfilehash: fd071f736add094fd65ae4d889f8008eefd8515d
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278063"
---
# <a name="local-anchor-transfers-in-unity"></a>Transferencias de delimitadores locales en Unity

En situaciones en las que no se pueden usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">delimitadores espaciales de Azure</a>, las transferencias de delimitadores locales permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.

>[!NOTE]
>Las transferencias de delimitadores locales proporcionan una recuperación de delimitador menos sólida que los delimitadores <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">espaciales de Azure</a>y los dispositivos iOS y Android no se admiten en este enfoque.

### <a name="setting-the-spatialperception-capability"></a>Establecimiento de la funcionalidad SpatialPerception

Para que una aplicación transfiera los anclajes espaciales, se debe habilitar la funcionalidad *SpatialPerception* .

Cómo habilitar la funcionalidad *SpatialPerception* :
1. En el editor de Unity, abra el panel de **configuración del reproductor** (Editar > configuración del proyecto > Player).
2. Haga clic en la pestaña **"tienda Windows"**
3. Expanda **"configuración de publicación"** y seleccione la funcionalidad **"SpatialPerception"** en la lista **"funcionalidades"** .

>[!NOTE]
>Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o establecer manualmente [esta funcionalidad en el AppxManifest de Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Transferencia de delimitador

**Espacio de nombres:** *UnityEngine. XR. WSA. Sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Para transferir un [WorldAnchor](coordinate-systems-in-unity.md), debe establecer el delimitador que se va a transferir. El usuario de un HoloLens examina su entorno y, de forma manual o mediante programación, elige un punto en el espacio para que sea el delimitador de la experiencia compartida. Los datos que representan este punto se pueden serializar y transmitir a los otros dispositivos que compartan la experiencia. Después, cada dispositivo deserializa los datos de delimitador e intenta buscar ese punto en el espacio. Para que la transferencia de delimitador funcione, cada dispositivo debe haber explorado en el entorno suficiente, de modo que se pueda identificar el punto representado por el delimitador.

### <a name="setup"></a>Instalación

El código de ejemplo de esta página tiene algunos campos que se deben inicializar:
1. *GameObject rootGameObject* es un *GameObject* en Unity que tiene un componente *WorldAnchor* en él. Un usuario de la experiencia compartida colocará esta *GameObject* y exportará los datos a los demás usuarios.
2. *WorldAnchor gameRootAnchor* es *UnityEngine. XR. WSA. WorldAnchor* que se encuentra en *rootGameObject*.
3. *Byte [] importedData* es una matriz de bytes para el delimitador serializado que recibe cada cliente a través de la red.

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

### <a name="exporting"></a>Exportador

Para exportar, solo necesitamos un *WorldAnchor* y para saber lo que le llamaremos de modo que tenga sentido para la aplicación receptora. Un cliente de la experiencia compartida realizará estos pasos para exportar el delimitador compartido:
1. Creación de un *WorldAnchorTransferBatch*
2. Agregar *WorldAnchors* para transferir
3. Inicio de la exportación
4. Controlar el evento *OnExportDataAvailable* a medida que los datos estén disponibles
5. Controlar el evento *OnExportComplete*

Creamos un *WorldAnchorTransferBatch* para encapsular lo que se va a transferir y exportarlo en bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

A medida que los datos estén disponibles, envíe los bytes al cliente o búfer a medida que los segmentos de datos estén disponibles y envíe los medios que desee:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Una vez completada la exportación, si se ha producido un error en la transferencia de datos y en la serialización, indique al cliente que descarte los datos. Si la serialización se realizó correctamente, indique al cliente que se han transferido todos los datos y que se puede iniciar la importación:

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

### <a name="importing"></a>Importar

Después de recibir todos los bytes del remitente, se pueden volver a importar los datos en un *WorldAnchorTransferBatch* y bloquear el objeto de juego raíz en la misma ubicación física. Nota: la importación a veces producirá un error temporal y se debe volver a intentar:

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

Después de que un *GameObject* se bloquee a través de la llamada de *LockObject* , tendrá un *WorldAnchor* que lo mantendrá en la misma posición física del mundo, pero puede estar en una ubicación diferente en el espacio de coordenadas de Unity que otros usuarios.

