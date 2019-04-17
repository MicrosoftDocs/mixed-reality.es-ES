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
# <a name="focus-point-in-unity"></a><span data-ttu-id="9c5a7-104">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="9c5a7-104">Focus point in Unity</span></span>

<span data-ttu-id="9c5a7-105">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="9c5a7-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="9c5a7-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="9c5a7-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="9c5a7-107">El [centrarse punto](hologram-stability.md#stabilization-plane) puede conjunto para proporcionar una sugerencia sobre cómo realizar mejor estabilización en el hologramas actualmente de HoloLens que se va a mostrar.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-107">The [focus point](hologram-stability.md#stabilization-plane) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="9c5a7-108">Si desea establecer el punto de enfoque en Unity, debe establecerse cada fotograma mediante *HolographicSettings.SetFocusPointForFrame()*.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="9c5a7-109">Si no se establece el punto de enfoque para un marco, se usará el plano de estabilización de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="9c5a7-110">De forma predeterminada, los nuevos proyectos de Unity tienen la opción "Habilitar compartida de búfer de profundidad" establecido.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="9c5a7-111">Con esta opción, una aplicación de Unity que se ejecutan en un auricular envolvente de escritorio o un HoloLens que ejecutan Windows 10 de abril de 2018 Update (RS4) o posteriormente enviará el búfer de profundidad para Windows para optimizar la estabilidad holograma automáticamente, sin la aplicación especificar un punto de enfoque:</span><span class="sxs-lookup"><span data-stu-id="9c5a7-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="9c5a7-112">En un escritorio auriculares envolventes, esto le permitirá reprojection de basado en profundidad por píxel.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="9c5a7-113">En un HoloLens que ejecutan el Windows 10 de abril de 2018 Update o posterior, esto analizará el búfer de profundidad para seleccionar automáticamente un plano de estabilización óptimo.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="9c5a7-114">Cualquier enfoque debe proporcionar aún mejor calidad de imagen sin trabajo explícita por la aplicación para seleccionar un punto de enfoque cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="9c5a7-115">Tenga en cuenta que si proporciona manualmente un punto de enfoque, que invalidará el comportamiento automático que se ha descrito anteriormente y normalmente se reducirá la estabilidad holograma.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="9c5a7-116">Por lo general, sólo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en un HoloLens que aún no se ha actualizado a Windows Update 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="9c5a7-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9c5a7-117">Example</span></span>

<span data-ttu-id="9c5a7-118">Hay muchas maneras de establecer el punto de enfoque, tal como se sugiere por las sobrecargas disponibles en el *SetFocusPointForFrame* función estática.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="9c5a7-119">Presentados a continuación es un ejemplo sencillo para establecer el plano de foco en el objeto proporcionado en cada fotograma:</span><span class="sxs-lookup"><span data-stu-id="9c5a7-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

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

<span data-ttu-id="9c5a7-120">Tenga en cuenta que el código simple anterior puede acabar reducir estabilidad holograma si el objeto enfocado termina detrás del usuario.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="9c5a7-121">Esto es por eso normalmente debe establecer la opción "Habilitar compartida de búfer de profundidad" en lugar de especificar manualmente un punto de enfoque.</span><span class="sxs-lookup"><span data-stu-id="9c5a7-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="9c5a7-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="9c5a7-122">See also</span></span>
* [<span data-ttu-id="9c5a7-123">Plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="9c5a7-123">Stabilization plane</span></span>](hologram-stability.md#stabilization-plane)
