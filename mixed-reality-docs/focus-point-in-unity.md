---
title: Punto de enfoque en Unity
description: Ajuste manual de la estabilidad de holograma en Unity estableciendo el punto de enfoque
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto de enfoque, plano de enfoque, plano de estabilización, punto de estabilización, Reproyección, LSR, búfer de profundidad
ms.openlocfilehash: d48f6f1878a68a17be263f10b809229dc2705c58
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435414"
---
# <a name="focus-point-in-unity"></a>Punto de enfoque en Unity

**Espacio de nombres:** *UnityEngine. XR. WSA*<br>
**Tipo**: *HolographicSettings*

Se puede establecer el [punto de enfoque](hologram-stability.md#reprojection) para proporcionar a HoloLens una sugerencia sobre cómo realizar mejor la estabilización en los hologramas que se muestran actualmente.

Si desea establecer el punto de enfoque en Unity, debe establecer cada fotograma mediante *HolographicSettings. SetFocusPointForFrame ()* . Si no se establece el punto de enfoque para un marco, se usará el plano de estabilización predeterminado.

> [!NOTE]
> De forma predeterminada, los nuevos proyectos de Unity tienen establecida la opción "habilitar el uso compartido del búfer de profundidad".  Con esta opción, una aplicación de Unity que se ejecute en un casco de escritorio envolvente o en una HoloLens que ejecute la actualización 2018 de abril de Windows 10 (RS4) o posterior enviará el búfer de profundidad a Windows para optimizar la estabilidad del holograma automáticamente, sin que la aplicación especifique un punto de enfoque:
> * En un casco de escritorio envolvente, esto habilitará la Reproyección basada en profundidad por píxel.
> * En una HoloLens que ejecute la actualización de abril de 2018 de Windows 10 o posterior, se analizará el búfer de profundidad para elegir un plano de estabilización óptimo automáticamente.
>
> Cualquier enfoque debe proporcionar una calidad de imagen incluso mejor sin que la aplicación Seleccione un punto de enfoque cada fotograma.  Tenga en cuenta que si proporciona un punto de enfoque manualmente, se invalidará el comportamiento automático descrito anteriormente y se reducirá la estabilidad del holograma.  Por lo general, solo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en una HoloLens que todavía no se ha actualizado a la actualización 2018 de abril de Windows 10.

### <a name="example"></a>Ejemplo

Hay muchas maneras de establecer el punto de enfoque, como se sugiere por las sobrecargas disponibles en la función estática *SetFocusPointForFrame* . A continuación se muestra un ejemplo sencillo para establecer el plano de enfoque en el objeto proporcionado en cada fotograma:

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

Tenga en cuenta que el código anterior puede acabar reduciendo la estabilidad del holograma si el objeto que tiene el foco termina detrás del usuario.  Este es el motivo por el que normalmente debería establecer "habilitar el uso compartido del búfer de profundidad" en lugar de especificar manualmente un punto de enfoque.

### <a name="see-also"></a>Consulta también
* [Plano de estabilización](hologram-stability.md#reprojection)
