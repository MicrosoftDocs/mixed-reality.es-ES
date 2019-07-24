---
title: Pérdida de seguimiento en Unity
description: Control de la pérdida de seguimiento en una aplicación de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, imagen de pérdida de seguimiento y pérdida de seguimiento
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548744"
---
# <a name="tracking-loss-in-unity"></a>Pérdida de seguimiento en Unity

Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento". De forma predeterminada, Unity pausará el bucle de actualización y mostrará una imagen de bienvenida al usuario. Cuando se recupera el seguimiento, la imagen de la pantalla de presentación desaparece y el bucle de actualización continúa.

Como alternativa, el usuario puede controlar manualmente esta transición mediante la opción de configuración. Todo el contenido parecerá quedar bloqueado durante la pérdida del seguimiento si no se hace nada para controlarlo.

## <a name="default-handling"></a>Control predeterminado

De forma predeterminada, el bucle de actualización de la aplicación, así como todos los mensajes y eventos se detendrán durante la pérdida de seguimiento. Al mismo tiempo, se mostrará una imagen al usuario. Puede personalizar esta imagen; para ello, vaya a Editar > Configuración-> Player, haga clic en imagen de bienvenida y establezca la imagen de pérdida del seguimiento de holográfica.

## <a name="manual-handling"></a>Control manual

Para controlar manualmente la pérdida de seguimiento, debe ir a **Editar** > **configuración** > de proyecto**reproductor** > **plataforma universal de Windows configuración** > de la pestaña**imagen** debienvenida. >  **Windows Holographic** y desactive la casilla de verificación de la pérdida de seguimiento en pausa y Mostrar imagen. Después, debe controlar los cambios de seguimiento con las API especificadas a continuación.

**Espacio de nombres**: *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldManager*

* El administrador mundial expone un evento para detectar el seguimiento perdido/ganado (*WorldManager. OnPositionalLocatorStateChanged*) y una propiedad para consultar el estado actual (*WorldManager. State*)
* Cuando el estado de seguimiento no está activo, la cámara no parecerá que se traduzca en el mundo virtual, ni siquiera cuando el usuario se traduce. Esto significa que los objetos ya no se correspondan con ninguna ubicación física y todos aparecerán como cuerpo bloqueado.

Al controlar los cambios de seguimiento por su cuenta, debe sondear la propiedad State de cada fotograma o controlar el evento *OnPositionalLocatorStateChanged* .

### <a name="polling"></a>Sondeo

El estado más importante es *PositionalLocatorState. Active* , lo que significa que el seguimiento es totalmente funcional. Cualquier otro estado solo producirá diferencias de rotación en la cámara principal. Por ejemplo:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Controlar el evento OnPositionalLocatorStateChanged

Como alternativa y más conveniente, también puede suscribirse a *OnPositionalLocatorStateChanged* para controlar las transiciones:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>Vea también
* [Control de la pérdida de seguimiento en DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)
