---
title: Seguimiento de la pérdida en Unity
description: Control de seguimiento de la pérdida de una aplicación de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, pérdida de seguimiento, seguimiento de la imagen de pérdida
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602768"
---
# <a name="tracking-loss-in-unity"></a>Seguimiento de la pérdida en Unity

Cuando el dispositivo no puede encontrar a sí mismo en el mundo, la aplicación experimenta "pérdida de seguimiento". De forma predeterminada, Unity se pausa el bucle de actualización y mostrar una imagen de bienvenida al usuario. Cuando se ha recuperado el seguimiento, la imagen de bienvenida desaparece y el bucle de actualización continúa.

Como alternativa, el usuario puede controlar manualmente esta transición por dejar de participar en la configuración. Todo el contenido le resultarán esté bloqueado durante el seguimiento de si se hace nada para controlar la pérdida de cuerpo.

## <a name="default-handling"></a>El control predeterminado

De forma predeterminada, se detendrá el bucle de actualización de la aplicación, así como todos los mensajes y eventos para la duración de la pérdida de seguimiento. En ese mismo momento, se mostrará una imagen para el usuario. Puede personalizar esta imagen si va a Editar -> Configuración -> Reproductor, al hacer clic en la imagen de la presentación y la configuración de la imagen de la pérdida de seguimiento holográfica.

## <a name="manual-handling"></a>Control manual

Para controlar manualmente la pérdida de seguimiento, debe ir a **editar** > **configuración del proyecto** > **Reproductor**  >   **Pestaña de configuración de plataforma de Windows universal** > **imagen presentación** > **Windows Holographic** y desactive la opción "en seguimiento de pérdida de pausa y mostrar imagen ". Después de eso, tiene que controlar el seguimiento de cambios con las API que se especifican a continuación.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldManager*

* Mundo Manager expone un evento para detectar perdido/adquirida de seguimiento (*WorldManager.OnPositionalLocatorStateChanged*) y una propiedad para consultar el estado actual (*WorldManager.state*)
* Cuando el estado de seguimiento no está activo, la cámara no aparecerá traducir en el mundo virtual incluso cuando el usuario se traduce. Esto significa que los objetos ya no se corresponden a cualquier ubicación física y todos aparecerán cuerpo bloqueado.

Al controlar el seguimiento de cambios en su propio que sondear en busca de la propiedad state cada marco o el identificador de la *OnPositionalLocatorStateChanged* eventos.

### <a name="polling"></a>Sondeo

El estado más importante es *PositionalLocatorState.Active* lo que significa que el seguimiento es totalmente funcional. Solo los deltas rotación produce cualquier otro estado en la cámara principal. Por ejemplo:

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Controle el evento OnPositionalLocatorStateChanged

O bien y de manera más conveniente, también puede suscribirse a *OnPositionalLocatorStateChanged* para controlar las transiciones:

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
* [Controlar el seguimiento de la pérdida de DirectX](coordinate-systems-in-directx.md#handling-tracking-loss)
