---
title: Persistencia en Unity
description: Persistencia permite a los usuarios anclar hologramas individuales o un área de trabajo siempre que sea que deseen y, a continuación, busque, donde espera durante varias usa de la aplicación.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistencia, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605779"
---
# <a name="persistence-in-unity"></a>Persistencia en Unity

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Clase:** *WorldAnchorStore*

El WorldAnchorStore es la clave para crear experiencias holográficas donde hologramas permanecen en posiciones específicas reales entre las instancias de la aplicación. Esto le permite a los usuarios anclan hologramas individuales o un área de trabajo donde desee y, a continuación, más adelante le resulte donde esperan a lo largo de muchos usos de la aplicación.

## <a name="how-to-persist-holograms-across-sessions"></a>Cómo conservar hologramas entre sesiones

El WorldAnchorStore le permitirá conservar la ubicación del WorldAnchor entre sesiones. Para conservar realmente hologramas entre sesiones, deberá por separado al realizar un seguimiento de los GameObjects que utilice un delimitador de mundo determinado. A menudo tiene sentido crear una raíz de GameObject con un anclaje del mundo y tener elementos secundarios hologramas delimitadas por él con un desplazamiento de posición local.

Para cargar hologramas de sesiones anteriores:
1. Obtener el WorldAnchorStore
2. Cargar datos relacionados con el delimitador del mundo que proporciona el identificador del delimitador en el mundo de la aplicación
3. Cargar un anclaje del mundo desde su Id.

Para guardar hologramas para sesiones futuras:
1. Obtener el WorldAnchorStore
2. Guardar un anclaje del mundo especificando un identificador
3. Guardar datos relacionados con el delimitador del mundo junto con un identificador de la aplicación

### <a name="getting-the-worldanchorstore"></a>Introducción a la WorldAnchorStore

Queremos mantener una referencia a la WorldAnchorStore en torno a por lo que sabemos que estamos preparados ir cuando desea realizar una operación. Puesto que es una llamada asincrónica, potencialmente tan pronto como inicio, que queremos llamar

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

En este caso, StoreLoaded es nuestro controlador para cuando haya terminado de cargarse el WorldAnchorStore:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Ahora tenemos una referencia a la WorldAnchorStore que usaremos para guardar y cargar los delimitadores de mundo específico.

### <a name="saving-a-worldanchor"></a>Guardar un WorldAnchor

Para guardar, simplemente tenemos lo que se va a guardar y pasarlo en el WorldAnchor obtuvimos antes cuando desea guardar el nombre. Nota: al intentar guardar dos anclajes en la misma cadena se producirá un error (almacén. Guardar se devolverá false). Es preciso eliminar el anterior guardar antes de guardar una nueva:

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

### <a name="loading-a-worldanchor"></a>Cargar un WorldAnchor

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

Además, podemos usar almacén. Delete() para quitar un delimitador que se guardó anteriormente y el almacén. Clear() para quitar todos los datos previamente guardados.

### <a name="enumerating-existing-anchors"></a>Enumerar los anclajes de existentes

Para descubrir los delimitadores almacenados previamente, llame a GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Conservar hologramas para varios dispositivos.

Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para crear un anclaje en la nube duraderas desde un WorldAnchor local, lo que la aplicación, a continuación, puede ubicar a través de varios HoloLens, dispositivos iOS y Android, incluso si esos dispositivos no están presentes en el mismo hora.  Dado que los anclajes en la nube son persistentes, varios dispositivos con el tiempo pueden cada ver contenido representado en relación con ese delimitador en la misma ubicación física.

Para empezar a crear experiencias compartidas en Unity, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guías de inicio rápido de Azure espacial delimitadores Unity</a>.

Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y localizar los anclajes en Unity</a>.

## <a name="see-also"></a>Vea también
* [Persistencia de anclaje espacial](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure delimitadores espaciales</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Delimitadores espaciales Azure SDK para Unity</a>
