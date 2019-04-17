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
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="19b21-104">Seguimiento de la pérdida en Unity</span><span class="sxs-lookup"><span data-stu-id="19b21-104">Tracking loss in Unity</span></span>

<span data-ttu-id="19b21-105">Cuando el dispositivo no puede encontrar a sí mismo en el mundo, la aplicación experimenta "pérdida de seguimiento".</span><span class="sxs-lookup"><span data-stu-id="19b21-105">When the device cannot locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="19b21-106">De forma predeterminada, Unity se pausa el bucle de actualización y mostrar una imagen de bienvenida al usuario.</span><span class="sxs-lookup"><span data-stu-id="19b21-106">By default, Unity will pause the update loop and display a splash image to the user.</span></span> <span data-ttu-id="19b21-107">Cuando se ha recuperado el seguimiento, la imagen de bienvenida desaparece y el bucle de actualización continúa.</span><span class="sxs-lookup"><span data-stu-id="19b21-107">When tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="19b21-108">Como alternativa, el usuario puede controlar manualmente esta transición por dejar de participar en la configuración.</span><span class="sxs-lookup"><span data-stu-id="19b21-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="19b21-109">Todo el contenido le resultarán esté bloqueado durante el seguimiento de si se hace nada para controlar la pérdida de cuerpo.</span><span class="sxs-lookup"><span data-stu-id="19b21-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="19b21-110">El control predeterminado</span><span class="sxs-lookup"><span data-stu-id="19b21-110">Default Handling</span></span>

<span data-ttu-id="19b21-111">De forma predeterminada, se detendrá el bucle de actualización de la aplicación, así como todos los mensajes y eventos para la duración de la pérdida de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="19b21-111">By default, the update loop of the app as well as all messages and events will stop for the duration of tracking loss.</span></span> <span data-ttu-id="19b21-112">En ese mismo momento, se mostrará una imagen para el usuario.</span><span class="sxs-lookup"><span data-stu-id="19b21-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="19b21-113">Puede personalizar esta imagen si va a Editar -> Configuración -> Reproductor, al hacer clic en la imagen de la presentación y la configuración de la imagen de la pérdida de seguimiento holográfica.</span><span class="sxs-lookup"><span data-stu-id="19b21-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="19b21-114">Control manual</span><span class="sxs-lookup"><span data-stu-id="19b21-114">Manual Handling</span></span>

<span data-ttu-id="19b21-115">Para controlar manualmente la pérdida de seguimiento, debe ir a **editar** > **configuración del proyecto** > **Reproductor**  >   **Pestaña de configuración de plataforma de Windows universal** > **imagen presentación** > **Windows Holographic** y desactive la opción "en seguimiento de pérdida de pausa y mostrar imagen ".</span><span class="sxs-lookup"><span data-stu-id="19b21-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="19b21-116">Después de eso, tiene que controlar el seguimiento de cambios con las API que se especifican a continuación.</span><span class="sxs-lookup"><span data-stu-id="19b21-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="19b21-117">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="19b21-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="19b21-118">**Tipo:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="19b21-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="19b21-119">Mundo Manager expone un evento para detectar perdido/adquirida de seguimiento (*WorldManager.OnPositionalLocatorStateChanged*) y una propiedad para consultar el estado actual (*WorldManager.state*)</span><span class="sxs-lookup"><span data-stu-id="19b21-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="19b21-120">Cuando el estado de seguimiento no está activo, la cámara no aparecerá traducir en el mundo virtual incluso cuando el usuario se traduce.</span><span class="sxs-lookup"><span data-stu-id="19b21-120">When the tracking state is not active, the camera will not appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="19b21-121">Esto significa que los objetos ya no se corresponden a cualquier ubicación física y todos aparecerán cuerpo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="19b21-121">This means objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="19b21-122">Al controlar el seguimiento de cambios en su propio que sondear en busca de la propiedad state cada marco o el identificador de la *OnPositionalLocatorStateChanged* eventos.</span><span class="sxs-lookup"><span data-stu-id="19b21-122">When handling tracking changes on your own you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="19b21-123">Sondeo</span><span class="sxs-lookup"><span data-stu-id="19b21-123">Polling</span></span>

<span data-ttu-id="19b21-124">El estado más importante es *PositionalLocatorState.Active* lo que significa que el seguimiento es totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="19b21-124">The most important state is *PositionalLocatorState.Active* which means tracking is fully functional.</span></span> <span data-ttu-id="19b21-125">Solo los deltas rotación produce cualquier otro estado en la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="19b21-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="19b21-126">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="19b21-126">For example:</span></span>

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

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="19b21-127">Controle el evento OnPositionalLocatorStateChanged</span><span class="sxs-lookup"><span data-stu-id="19b21-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="19b21-128">O bien y de manera más conveniente, también puede suscribirse a *OnPositionalLocatorStateChanged* para controlar las transiciones:</span><span class="sxs-lookup"><span data-stu-id="19b21-128">Alternatively and more conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="19b21-129">Vea también</span><span class="sxs-lookup"><span data-stu-id="19b21-129">See also</span></span>
* [<span data-ttu-id="19b21-130">Controlar el seguimiento de la pérdida de DirectX</span><span class="sxs-lookup"><span data-stu-id="19b21-130">Handling tracking loss in DirectX</span></span>](coordinate-systems-in-directx.md#handling-tracking-loss)
