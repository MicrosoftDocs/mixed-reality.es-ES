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
# <a name="local-anchor-transfers-in-unity"></a>Transferencias de anclaje local en Unity

En situaciones donde no se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, las transferencias de anclaje local habilitar un dispositivo HoloLens exportar un delimitador para ser importadas por un segundo dispositivo HoloLens.

>[!NOTE]
>Las transferencias de anclaje locales proporcionan menos sólida retirada de anclaje que <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>, y dispositivos iOS y Android no son compatibles con este enfoque.

### <a name="setting-the-spatialperception-capability"></a>Establecer la capacidad de SpatialPerception

En orden para una aplicación transferir los anclajes de espaciales, el *SpatialPerception* posibilidad debe habilitarse.

Cómo habilitar el *SpatialPerception* capacidad:
1. En el Editor de Unity, abra el **"Configuración del Reproductor"** panel (Editar > configuración del proyecto > Reproductor)
2. Haga clic en el **"Windows Store"** ficha
3. Expanda **"Configuración de publicación"** y compruebe el **"SpatialPerception"** capacidad en el **"Capacidades"** lista

>[!NOTE]
>Si ya ha exportado el proyecto de Unity a una solución de Visual Studio, deberá exportar a una nueva carpeta o manualmente [establecer esta funcionalidad en el AppxManifest en Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Transferencia de anclaje

**Namespace:** *UnityEngine.XR.WSA.Sharing*<br>
**Tipo**: *WorldAnchorTransferBatch*

Para transferir un [WorldAnchor](coordinate-systems-in-unity.md), uno debe establecer el delimitador que se transferirá. El usuario de uno HoloLens examina su entorno y manualmente o mediante programación, elige un punto en el espacio que el delimitador de la experiencia compartida. A continuación, se pueden serializar y transmitir a los otros dispositivos que están compartiendo en la experiencia de los datos que representa este punto. Cada dispositivo, a continuación, deserializa los datos de anclaje e intenta localizar ese punto en el espacio. En orden para transferir ancla para que funcione, cada dispositivo debe escaneen suficiente del entorno de modo que se puede identificar el punto representado por el delimitador.

### <a name="setup"></a>Programa de instalación

El código de ejemplo en esta página tiene unos cuantos campos que deben inicializarse:
1. *GameObject rootGameObject* es un *GameObject* en Unity que tiene un *WorldAnchor* componente en él. Un usuario en la experiencia compartida Esto colocará *GameObject* y exportar los datos a los demás usuarios.
2. *WorldAnchor gameRootAnchor* es el *UnityEngine.XR.WSA.WorldAnchor* que se encuentra en *rootGameObject*.
3. *Byte [] importedData* es una matriz de bytes para el delimitador serializada recibe cada cliente a través de la red.

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

### <a name="exporting"></a>Exportar

Para exportar, sólo necesitamos un *WorldAnchor* y saber lo que llamaremos a lo que resulta conveniente para la aplicación receptora. Un cliente en la experiencia compartida llevará a cabo estos pasos para exportar el delimitador compartido:
1. Crear un *WorldAnchorTransferBatch*
2. Agregar el *WorldAnchors* para transferir
3. Iniciar la exportación
4. Controlar la *OnExportDataAvailable* eventos como los datos se convierte en disponible
5. Controlar la *OnExportComplete* eventos

Creamos un *WorldAnchorTransferBatch* para encapsular lo que se pueden transferir y exportarlas a continuación, en bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Cuando hay datos disponibles, enviar los bytes en el cliente o el búfer como segmentos de datos está disponible y enviar a través de cualquier medio deseado:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Una vez completada la exportación, si nos hemos transferir datos y la serialización no se pudo, indicar al cliente para descartar los datos. Si la serialización se realizó correctamente, indicar al cliente que se ha transferido todos los datos y puede empezar a importar:

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

Después de recibir todos los bytes del remitente, podemos importar los datos en un *WorldAnchorTransferBatch* y bloquear el objeto de juego de raíz en la misma ubicación física. Nota: importación transiently a veces, se producirá un error y necesita volver a intentarlo:

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

Después de un *GameObject* está bloqueada mediante el *LockObject* llamada, tendrá un *WorldAnchor* que mantendrá en la misma posición física en el mundo, pero puede estar en un espacio que otros usuarios de coordenadas de ubicación diferente en el Unity.

