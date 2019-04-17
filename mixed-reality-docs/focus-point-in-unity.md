---
title: Punto de enfoque en Unity
description: Ajuste manual estabilidad holograma en Unity estableciendo el punto de enfoque
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto de enfoque, el plano de foco, el plano de estabilización, punto estabilización, reprojection, LSR, búfer de profundidad
ms.openlocfilehash: 0f43c37df66ecada86dcb309fcd58d822f0f3481
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605740"
---
# <a name="focus-point-in-unity"></a>Punto de enfoque en Unity

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo**: *HolographicSettings*

El [centrarse punto](hologram-stability.md#stabilization-plane) puede conjunto para proporcionar una sugerencia sobre cómo realizar mejor estabilización en el hologramas actualmente de HoloLens que se va a mostrar.

Si desea establecer el punto de enfoque en Unity, debe establecerse cada fotograma mediante *HolographicSettings.SetFocusPointForFrame()*. Si no se establece el punto de enfoque para un marco, se usará el plano de estabilización de forma predeterminada.

> [!NOTE]
> De forma predeterminada, los nuevos proyectos de Unity tienen la opción "Habilitar compartida de búfer de profundidad" establecido.  Con esta opción, una aplicación de Unity que se ejecutan en un auricular envolvente de escritorio o un HoloLens que ejecutan Windows 10 de abril de 2018 Update (RS4) o posteriormente enviará el búfer de profundidad para Windows para optimizar la estabilidad holograma automáticamente, sin la aplicación especificar un punto de enfoque:
> * En un escritorio auriculares envolventes, esto le permitirá reprojection de basado en profundidad por píxel.
> * En un HoloLens que ejecutan el Windows 10 de abril de 2018 Update o posterior, esto analizará el búfer de profundidad para seleccionar automáticamente un plano de estabilización óptimo.
>
> Cualquier enfoque debe proporcionar aún mejor calidad de imagen sin trabajo explícita por la aplicación para seleccionar un punto de enfoque cada fotograma.  Tenga en cuenta que si proporciona manualmente un punto de enfoque, que invalidará el comportamiento automático que se ha descrito anteriormente y normalmente se reducirá la estabilidad holograma.  Por lo general, sólo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en un HoloLens que aún no se ha actualizado a Windows Update 10 de abril de 2018.

### <a name="example"></a>Ejemplo

Hay muchas maneras de establecer el punto de enfoque, tal como se sugiere por las sobrecargas disponibles en el *SetFocusPointForFrame* función estática. Presentados a continuación es un ejemplo sencillo para establecer el plano de foco en el objeto proporcionado en cada fotograma:

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

Tenga en cuenta que el código simple anterior puede acabar reducir estabilidad holograma si el objeto enfocado termina detrás del usuario.  Esto es por eso normalmente debe establecer la opción "Habilitar compartida de búfer de profundidad" en lugar de especificar manualmente un punto de enfoque.

### <a name="see-also"></a>Vea también
* [Plano de estabilización](hologram-stability.md#stabilization-plane)
