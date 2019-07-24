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
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="c75d1-104">Pérdida de seguimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="c75d1-104">Tracking loss in Unity</span></span>

<span data-ttu-id="c75d1-105">Cuando el dispositivo no se encuentra en el mundo, la aplicación experimenta "pérdida de seguimiento".</span><span class="sxs-lookup"><span data-stu-id="c75d1-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="c75d1-106">De forma predeterminada, Unity pausará el bucle de actualización y mostrará una imagen de bienvenida al usuario.</span><span class="sxs-lookup"><span data-stu-id="c75d1-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="c75d1-107">Cuando se recupera el seguimiento, la imagen de la pantalla de presentación desaparece y el bucle de actualización continúa.</span><span class="sxs-lookup"><span data-stu-id="c75d1-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="c75d1-108">Como alternativa, el usuario puede controlar manualmente esta transición mediante la opción de configuración.</span><span class="sxs-lookup"><span data-stu-id="c75d1-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="c75d1-109">Todo el contenido parecerá quedar bloqueado durante la pérdida del seguimiento si no se hace nada para controlarlo.</span><span class="sxs-lookup"><span data-stu-id="c75d1-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="c75d1-110">Control predeterminado</span><span class="sxs-lookup"><span data-stu-id="c75d1-110">Default Handling</span></span>

<span data-ttu-id="c75d1-111">De forma predeterminada, el bucle de actualización de la aplicación, así como todos los mensajes y eventos se detendrán durante la pérdida de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="c75d1-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="c75d1-112">Al mismo tiempo, se mostrará una imagen al usuario.</span><span class="sxs-lookup"><span data-stu-id="c75d1-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="c75d1-113">Puede personalizar esta imagen; para ello, vaya a Editar > Configuración-> Player, haga clic en imagen de bienvenida y establezca la imagen de pérdida del seguimiento de holográfica.</span><span class="sxs-lookup"><span data-stu-id="c75d1-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="c75d1-114">Control manual</span><span class="sxs-lookup"><span data-stu-id="c75d1-114">Manual Handling</span></span>

<span data-ttu-id="c75d1-115">Para controlar manualmente la pérdida de seguimiento, debe ir a **Editar** > **configuración** > de proyecto**reproductor** > **plataforma universal de Windows configuración** > de la pestaña**imagen** debienvenida. >  **Windows Holographic** y desactive la casilla de verificación de la pérdida de seguimiento en pausa y Mostrar imagen.</span><span class="sxs-lookup"><span data-stu-id="c75d1-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="c75d1-116">Después, debe controlar los cambios de seguimiento con las API especificadas a continuación.</span><span class="sxs-lookup"><span data-stu-id="c75d1-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="c75d1-117">**Espacio de nombres**: *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="c75d1-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="c75d1-118">**Tipo:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="c75d1-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="c75d1-119">El administrador mundial expone un evento para detectar el seguimiento perdido/ganado (*WorldManager. OnPositionalLocatorStateChanged*) y una propiedad para consultar el estado actual (*WorldManager. State*)</span><span class="sxs-lookup"><span data-stu-id="c75d1-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="c75d1-120">Cuando el estado de seguimiento no está activo, la cámara no parecerá que se traduzca en el mundo virtual, ni siquiera cuando el usuario se traduce.</span><span class="sxs-lookup"><span data-stu-id="c75d1-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="c75d1-121">Esto significa que los objetos ya no se correspondan con ninguna ubicación física y todos aparecerán como cuerpo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="c75d1-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="c75d1-122">Al controlar los cambios de seguimiento por su cuenta, debe sondear la propiedad State de cada fotograma o controlar el evento *OnPositionalLocatorStateChanged* .</span><span class="sxs-lookup"><span data-stu-id="c75d1-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="c75d1-123">Sondeo</span><span class="sxs-lookup"><span data-stu-id="c75d1-123">Polling</span></span>

<span data-ttu-id="c75d1-124">El estado más importante es *PositionalLocatorState. Active* , lo que significa que el seguimiento es totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="c75d1-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="c75d1-125">Cualquier otro estado solo producirá diferencias de rotación en la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="c75d1-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="c75d1-126">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c75d1-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="c75d1-127">Controlar el evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="c75d1-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="c75d1-128">Como alternativa y más conveniente, también puede suscribirse a *OnPositionalLocatorStateChanged* para controlar las transiciones:</span><span class="sxs-lookup"><span data-stu-id="c75d1-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c75d1-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="c75d1-129">See also</span></span>
* [<span data-ttu-id="c75d1-130">Control de la pérdida de seguimiento en DirectX</span><span class="sxs-lookup"><span data-stu-id="c75d1-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
