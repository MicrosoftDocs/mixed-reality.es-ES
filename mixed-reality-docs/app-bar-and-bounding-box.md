---
title: Cuadro de límite y barra de la aplicación
description: The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite
ms.openlocfilehash: e4f519cba459efac25f6c1370b07fcda4def30a1
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143174"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="3f19a-104">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="3f19a-104">Bounding box and App bar</span></span>
<span data-ttu-id="3f19a-105">![límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/UX/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f19a-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="3f19a-106">¿Cuál es el cuadro de límite?</span><span class="sxs-lookup"><span data-stu-id="3f19a-106">What is the Bounding box?</span></span>

<span data-ttu-id="3f19a-107">El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="3f19a-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="3f19a-108">Proporciona al usuario una asequibilidad de que el objeto es ajustable actualmente.</span><span class="sxs-lookup"><span data-stu-id="3f19a-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="3f19a-109">En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario.</span><span class="sxs-lookup"><span data-stu-id="3f19a-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="3f19a-110">It shows visual feedback to help the user perceive the distance from the object.</span><span class="sxs-lookup"><span data-stu-id="3f19a-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="3f19a-111">Scaling an object</span><span class="sxs-lookup"><span data-stu-id="3f19a-111">Scaling an object</span></span><br>
        <span data-ttu-id="3f19a-112">The corners of the bounding box tell the user that the object can scale.</span><span class="sxs-lookup"><span data-stu-id="3f19a-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="3f19a-113">The handles follow a widely understood pattern for adjusting scale.</span><span class="sxs-lookup"><span data-stu-id="3f19a-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="3f19a-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span><span class="sxs-lookup"><span data-stu-id="3f19a-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="3f19a-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span><span class="sxs-lookup"><span data-stu-id="3f19a-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="3f19a-116">*Video loop: Scaling an object via bounding box*</span><span class="sxs-lookup"><span data-stu-id="3f19a-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3f19a-117">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3f19a-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3f19a-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="3f19a-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="3f19a-119">Rotating an object</span><span class="sxs-lookup"><span data-stu-id="3f19a-119">Rotating an object</span></span><br>
        <span data-ttu-id="3f19a-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span><span class="sxs-lookup"><span data-stu-id="3f19a-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="3f19a-121">This gives the user more fine adjustment over their placed holograms.</span><span class="sxs-lookup"><span data-stu-id="3f19a-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="3f19a-122">Not only can they adjust and scale, but now rotate as well.</span><span class="sxs-lookup"><span data-stu-id="3f19a-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="3f19a-123">*Video loop: Rotating an object via bounding box*</span><span class="sxs-lookup"><span data-stu-id="3f19a-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3f19a-124">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3f19a-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3f19a-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="3f19a-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="3f19a-126">Visual feedback on hand proximity on HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f19a-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="3f19a-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span><span class="sxs-lookup"><span data-stu-id="3f19a-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="3f19a-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span><span class="sxs-lookup"><span data-stu-id="3f19a-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="3f19a-129">The ring eventually converges into a dot when the pressed state is reached.</span><span class="sxs-lookup"><span data-stu-id="3f19a-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="3f19a-130">This visual affordance helps the user understand how far they are from the object.</span><span class="sxs-lookup"><span data-stu-id="3f19a-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="3f19a-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span><span class="sxs-lookup"><span data-stu-id="3f19a-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3f19a-132">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3f19a-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3f19a-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="3f19a-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="3f19a-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="3f19a-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="3f19a-135">What is the App bar?</span><span class="sxs-lookup"><span data-stu-id="3f19a-135">What is the App bar?</span></span>

<span data-ttu-id="3f19a-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span><span class="sxs-lookup"><span data-stu-id="3f19a-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="3f19a-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span><span class="sxs-lookup"><span data-stu-id="3f19a-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="3f19a-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span><span class="sxs-lookup"><span data-stu-id="3f19a-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="3f19a-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span><span class="sxs-lookup"><span data-stu-id="3f19a-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="3f19a-140">The App bar follows the user</span><span class="sxs-lookup"><span data-stu-id="3f19a-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="3f19a-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span><span class="sxs-lookup"><span data-stu-id="3f19a-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="3f19a-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span><span class="sxs-lookup"><span data-stu-id="3f19a-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="3f19a-143">*Video loop: Walking around a hologram, the App bar follows*</span><span class="sxs-lookup"><span data-stu-id="3f19a-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3f19a-144">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3f19a-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3f19a-145">![Walking around a hologram.</span><span class="sxs-lookup"><span data-stu-id="3f19a-145">![Walking around a hologram.</span></span> <span data-ttu-id="3f19a-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="3f19a-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="3f19a-147">Bounding box in MRTK(Mixed Reality Toolkit) for Unity</span><span class="sxs-lookup"><span data-stu-id="3f19a-147">Bounding box in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="3f19a-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span><span class="sxs-lookup"><span data-stu-id="3f19a-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="3f19a-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span><span class="sxs-lookup"><span data-stu-id="3f19a-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="3f19a-150">MRTK - Bounding Box</span><span class="sxs-lookup"><span data-stu-id="3f19a-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="3f19a-151">Consulta también</span><span class="sxs-lookup"><span data-stu-id="3f19a-151">See also</span></span>

* [<span data-ttu-id="3f19a-152">Cursores</span><span class="sxs-lookup"><span data-stu-id="3f19a-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3f19a-153">Rayo de mano</span><span class="sxs-lookup"><span data-stu-id="3f19a-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3f19a-154">Button</span><span class="sxs-lookup"><span data-stu-id="3f19a-154">Button</span></span>](button.md)
* [<span data-ttu-id="3f19a-155">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="3f19a-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3f19a-156">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="3f19a-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3f19a-157">Manipula</span><span class="sxs-lookup"><span data-stu-id="3f19a-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3f19a-158">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="3f19a-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3f19a-159">Menú Near</span><span class="sxs-lookup"><span data-stu-id="3f19a-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3f19a-160">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="3f19a-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3f19a-161">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="3f19a-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3f19a-162">Teclado</span><span class="sxs-lookup"><span data-stu-id="3f19a-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3f19a-163">Herramienta</span><span class="sxs-lookup"><span data-stu-id="3f19a-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3f19a-164">Tabletas</span><span class="sxs-lookup"><span data-stu-id="3f19a-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="3f19a-165">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="3f19a-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="3f19a-166">Sombreador</span><span class="sxs-lookup"><span data-stu-id="3f19a-166">Shader</span></span>](shader.md)
* [<span data-ttu-id="3f19a-167">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="3f19a-167">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3f19a-168">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="3f19a-168">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3f19a-169">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="3f19a-169">Surface magnetism</span></span>](surface-magnetism.md)
