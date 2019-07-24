---
title: Persistencia en Unity
description: La persistencia permite a los usuarios anclar hologramas individuales o un área de trabajo donde lo deseen y, después, buscarlos más adelante donde esperan muchos usos de la aplicación.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistencia, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524787"
---
# <a name="persistence-in-unity"></a>Persistencia en Unity

**System.IO** *UnityEngine. XR. WSA. Persistence*<br>
**Las** *WorldAnchorStore*

WorldAnchorStore es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real entre instancias de la aplicación. Esto permite a los usuarios anclar hologramas individuales o un área de trabajo dondequiera que deseen y, después, buscarlos más adelante donde esperan muchos usos de la aplicación.

## <a name="how-to-persist-holograms-across-sessions"></a>Cómo conservar los hologramas entre sesiones

El WorldAnchorStore le permitirá conservar la ubicación de los WorldAnchor de las sesiones. Para conservar los hologramas en todas las sesiones, tendrá que realizar un seguimiento por separado de los GameObjects que usan un delimitador mundial determinado. A menudo tiene sentido crear una raíz GameObject con un delimitador mundial y tener los hologramas secundarios anclados por él con un desplazamiento de posición local.

Para cargar hologramas de sesiones anteriores:
1. Obtención de WorldAnchorStore
2. Cargar datos de la aplicación relacionados con el delimitador mundial que le proporciona el identificador del anclaje mundial
3. Carga de un delimitador mundial desde su identificador

Para guardar los hologramas para las sesiones futuras:
1. Obtención de WorldAnchorStore
2. Guardar un delimitador mundial especificando un identificador
3. Guardar datos de la aplicación relacionados con el delimitador mundial junto con un identificador

### <a name="getting-the-worldanchorstore"></a>Obtención de WorldAnchorStore

Vamos a mantener una referencia a WorldAnchorStore en torno a lo que sabemos que estamos preparados para realizar una operación. Dado que se trata de una llamada asincrónica, posiblemente en cuanto se inicia, queremos llamar a

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

En este caso, StoreLoaded es el controlador para cuando se haya completado la carga de WorldAnchorStore:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Ahora tenemos una referencia a WorldAnchorStore que usaremos para guardar y cargar delimitadores del mundo específicos.

### <a name="saving-a-worldanchor"></a>Guardar un WorldAnchor

Para ahorrar, simplemente necesitamos asignar un nombre a lo que estamos guardando y pasarlo en el WorldAnchor que obtuvimos antes cuando queremos ahorrar. Nota: Si intenta guardar dos delimitadores en la misma cadena, se producirá un error (Store. Save devolverá FALSE). Debe eliminar el guardado anterior antes de guardar el nuevo:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Carga de un WorldAnchor

Y para cargar:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

Además, podemos usar Store. Elimine () para quitar un delimitador que se guardó y almacenó anteriormente. Borre () para quitar todos los datos guardados previamente.

### <a name="enumerating-existing-anchors"></a>Enumerar delimitadores existentes

Para detectar los delimitadores almacenados previamente, llame a GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistencia de hologramas para varios dispositivos

Puede usar los <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede ubicar en varios dispositivos de HoloLens, iOS y Android, incluso si esos dispositivos no están presentes al mismo tiempo.  Dado que los delimitadores en la nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.

Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.

## <a name="see-also"></a>Vea también
* [Persistencia del delimitador espacial](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a>
