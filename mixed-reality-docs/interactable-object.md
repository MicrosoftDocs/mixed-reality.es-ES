---
title: Interactable object
description: A button has long been a metaphor used for triggering an event in the 2D abstract world. In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Mixed Reality, Controls, interaction, ui, ux
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143257"
---
# <a name="interactable-object"></a><span data-ttu-id="9686a-105">Interactable object</span><span class="sxs-lookup"><span data-stu-id="9686a-105">Interactable object</span></span>

![Interactible objects](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="9686a-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span><span class="sxs-lookup"><span data-stu-id="9686a-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="9686a-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span><span class="sxs-lookup"><span data-stu-id="9686a-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="9686a-109">Anything can be an **interactable object** that triggers an event.</span><span class="sxs-lookup"><span data-stu-id="9686a-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="9686a-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span><span class="sxs-lookup"><span data-stu-id="9686a-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="9686a-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span><span class="sxs-lookup"><span data-stu-id="9686a-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="9686a-112">The visual representation of the button depends on the context.</span><span class="sxs-lookup"><span data-stu-id="9686a-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="9686a-113">Important properties of the interactable object</span><span class="sxs-lookup"><span data-stu-id="9686a-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="9686a-114">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="9686a-114">Visual cues</span></span>

<span data-ttu-id="9686a-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span><span class="sxs-lookup"><span data-stu-id="9686a-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="9686a-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span><span class="sxs-lookup"><span data-stu-id="9686a-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="9686a-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span><span class="sxs-lookup"><span data-stu-id="9686a-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="9686a-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span><span class="sxs-lookup"><span data-stu-id="9686a-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="9686a-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span><span class="sxs-lookup"><span data-stu-id="9686a-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="9686a-120">Far interactions</span><span class="sxs-lookup"><span data-stu-id="9686a-120">Far interactions</span></span>

<span data-ttu-id="9686a-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span><span class="sxs-lookup"><span data-stu-id="9686a-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="9686a-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="9686a-123">**Default (Observation) state**</span><span class="sxs-lookup"><span data-stu-id="9686a-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="9686a-124">Default idle state of the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-124">Default idle state of the object.</span></span>
    <span data-ttu-id="9686a-125">The cursor is not on the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-125">The cursor is not on the object.</span></span> <span data-ttu-id="9686a-126">Hand is not detected.</span><span class="sxs-lookup"><span data-stu-id="9686a-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9686a-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="9686a-128">**Targeted (Hover) state**</span><span class="sxs-lookup"><span data-stu-id="9686a-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="9686a-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span><span class="sxs-lookup"><span data-stu-id="9686a-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="9686a-130">The cursor is on the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-130">The cursor is on the object.</span></span> <span data-ttu-id="9686a-131">Hand is detected, ready.</span><span class="sxs-lookup"><span data-stu-id="9686a-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9686a-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="9686a-133">**Pressed state**</span><span class="sxs-lookup"><span data-stu-id="9686a-133">**Pressed state**</span></span><br>
        <span data-ttu-id="9686a-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span><span class="sxs-lookup"><span data-stu-id="9686a-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="9686a-135">The cursor is on the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-135">The cursor is on the object.</span></span> <span data-ttu-id="9686a-136">Hand is detected, air tapped.</span><span class="sxs-lookup"><span data-stu-id="9686a-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="9686a-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span><span class="sxs-lookup"><span data-stu-id="9686a-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="9686a-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span><span class="sxs-lookup"><span data-stu-id="9686a-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="9686a-139">Here is what these states look like on a **holographic button**:</span><span class="sxs-lookup"><span data-stu-id="9686a-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="9686a-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="9686a-141">**Default (Observation) state**</span><span class="sxs-lookup"><span data-stu-id="9686a-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9686a-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="9686a-143">**Targeted (Hover) state**</span><span class="sxs-lookup"><span data-stu-id="9686a-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="9686a-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="9686a-145">**Pressed state**</span><span class="sxs-lookup"><span data-stu-id="9686a-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="9686a-146">Near interactions (direct)</span><span class="sxs-lookup"><span data-stu-id="9686a-146">Near interactions (direct)</span></span> 

<span data-ttu-id="9686a-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span><span class="sxs-lookup"><span data-stu-id="9686a-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="9686a-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span><span class="sxs-lookup"><span data-stu-id="9686a-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="9686a-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span><span class="sxs-lookup"><span data-stu-id="9686a-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="9686a-150">Use visual feedback to communicate the following:</span><span class="sxs-lookup"><span data-stu-id="9686a-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="9686a-151">**Default (Observation)** : Default idle state of the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="9686a-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span><span class="sxs-lookup"><span data-stu-id="9686a-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="9686a-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span><span class="sxs-lookup"><span data-stu-id="9686a-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="9686a-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span><span class="sxs-lookup"><span data-stu-id="9686a-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="9686a-155">**Grasped**: Change visuals (light, color) when the object is grasped</span><span class="sxs-lookup"><span data-stu-id="9686a-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="9686a-156">**Contact ends**: Change visuals (light, color) when touch has ended</span><span class="sxs-lookup"><span data-stu-id="9686a-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="9686a-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="9686a-158">**Hover (Far)**</span><span class="sxs-lookup"><span data-stu-id="9686a-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="9686a-159">Highlighting based on the proximity of the hand.</span><span class="sxs-lookup"><span data-stu-id="9686a-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9686a-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="9686a-161">**Hover (Near)**</span><span class="sxs-lookup"><span data-stu-id="9686a-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="9686a-162">Highlight size changes based on the distance to the hand.</span><span class="sxs-lookup"><span data-stu-id="9686a-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="9686a-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="9686a-164">**Touch / press**</span><span class="sxs-lookup"><span data-stu-id="9686a-164">**Touch / press**</span></span><br>
        <span data-ttu-id="9686a-165">Visual plus audio feedback.</span><span class="sxs-lookup"><span data-stu-id="9686a-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9686a-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="9686a-167">**Grasp**</span><span class="sxs-lookup"><span data-stu-id="9686a-167">**Grasp**</span></span><br>
        <span data-ttu-id="9686a-168">Visual plus audio feedback.</span><span class="sxs-lookup"><span data-stu-id="9686a-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="9686a-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span><span class="sxs-lookup"><span data-stu-id="9686a-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="9686a-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="9686a-171">**Default**</span><span class="sxs-lookup"><span data-stu-id="9686a-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9686a-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="9686a-173">**Hover**</span><span class="sxs-lookup"><span data-stu-id="9686a-173">**Hover**</span></span><br>
        <span data-ttu-id="9686a-174">Reveal a proximity-based lighting effect.</span><span class="sxs-lookup"><span data-stu-id="9686a-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="9686a-175">![Función táctil](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="9686a-176">**Función táctil**</span><span class="sxs-lookup"><span data-stu-id="9686a-176">**Touch**</span></span><br>
        <span data-ttu-id="9686a-177">Show ripple effect.</span><span class="sxs-lookup"><span data-stu-id="9686a-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9686a-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="9686a-179">**Press**</span><span class="sxs-lookup"><span data-stu-id="9686a-179">**Press**</span></span><br>
        <span data-ttu-id="9686a-180">Move the front plate.</span><span class="sxs-lookup"><span data-stu-id="9686a-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="9686a-181">The "ring" visual cue on HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9686a-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="9686a-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span><span class="sxs-lookup"><span data-stu-id="9686a-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="9686a-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="9686a-184">The ring eventually converges into a dot when the pressed state is reached.</span><span class="sxs-lookup"><span data-stu-id="9686a-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="9686a-185">This visual affordance helps the user understand how far they are from the object.</span><span class="sxs-lookup"><span data-stu-id="9686a-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="9686a-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span><span class="sxs-lookup"><span data-stu-id="9686a-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9686a-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9686a-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9686a-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="9686a-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="9686a-189">Audio cues</span><span class="sxs-lookup"><span data-stu-id="9686a-189">Audio cues</span></span>

<span data-ttu-id="9686a-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span><span class="sxs-lookup"><span data-stu-id="9686a-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="9686a-191">Use audio feedback to communicate the following:</span><span class="sxs-lookup"><span data-stu-id="9686a-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="9686a-192">**Contact begins**: Play sound when touch begins</span><span class="sxs-lookup"><span data-stu-id="9686a-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="9686a-193">**Contact ends**: Play sound on touch end</span><span class="sxs-lookup"><span data-stu-id="9686a-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="9686a-194">**Grab begins**: Play sound when grab starts</span><span class="sxs-lookup"><span data-stu-id="9686a-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="9686a-195">**Grab ends**: Play sound when grab ends</span><span class="sxs-lookup"><span data-stu-id="9686a-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="9686a-196">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="9686a-196">Voice commanding</span></span><br>
        <span data-ttu-id="9686a-197">For any interactable objects, it is important to support alternative interaction options.</span><span class="sxs-lookup"><span data-stu-id="9686a-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="9686a-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span><span class="sxs-lookup"><span data-stu-id="9686a-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="9686a-199">To improve discoverability, you can also provide a tooltip during the hover state.</span><span class="sxs-lookup"><span data-stu-id="9686a-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="9686a-200">*Image: Tooltip for the voice command*</span><span class="sxs-lookup"><span data-stu-id="9686a-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![voice commanding](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="9686a-202">Sizing recommendations</span><span class="sxs-lookup"><span data-stu-id="9686a-202">Sizing recommendations</span></span> 

<span data-ttu-id="9686a-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span><span class="sxs-lookup"><span data-stu-id="9686a-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="9686a-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span><span class="sxs-lookup"><span data-stu-id="9686a-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="9686a-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="9686a-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="9686a-206">Below are the recommendations for minimum sizes of interactable content.</span><span class="sxs-lookup"><span data-stu-id="9686a-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="9686a-207">Target size for direct hand interaction</span><span class="sxs-lookup"><span data-stu-id="9686a-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="9686a-208">Distance</span><span class="sxs-lookup"><span data-stu-id="9686a-208">Distance</span></span> | <span data-ttu-id="9686a-209">Viewing angle</span><span class="sxs-lookup"><span data-stu-id="9686a-209">Viewing angle</span></span> | <span data-ttu-id="9686a-210">Size</span><span class="sxs-lookup"><span data-stu-id="9686a-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="9686a-211">45cm</span><span class="sxs-lookup"><span data-stu-id="9686a-211">45cm</span></span>  | <span data-ttu-id="9686a-212">no smaller than 2°</span><span class="sxs-lookup"><span data-stu-id="9686a-212">no smaller than 2°</span></span> | <span data-ttu-id="9686a-213">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="9686a-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="9686a-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="9686a-215">*Target size for direct hand interaction*</span><span class="sxs-lookup"><span data-stu-id="9686a-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="9686a-216">Target size for buttons</span><span class="sxs-lookup"><span data-stu-id="9686a-216">Target size for buttons</span></span>

<span data-ttu-id="9686a-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span><span class="sxs-lookup"><span data-stu-id="9686a-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="9686a-218">Distance</span><span class="sxs-lookup"><span data-stu-id="9686a-218">Distance</span></span> | <span data-ttu-id="9686a-219">Tamaño mínimo</span><span class="sxs-lookup"><span data-stu-id="9686a-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="9686a-220">45cm</span><span class="sxs-lookup"><span data-stu-id="9686a-220">45cm</span></span>  | <span data-ttu-id="9686a-221">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="9686a-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="9686a-222">![Target size for the buttons](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="9686a-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="9686a-223">*Target size for the buttons*</span><span class="sxs-lookup"><span data-stu-id="9686a-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="9686a-224">Target size for hand ray or gaze interaction</span><span class="sxs-lookup"><span data-stu-id="9686a-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="9686a-225">Distance</span><span class="sxs-lookup"><span data-stu-id="9686a-225">Distance</span></span> | <span data-ttu-id="9686a-226">Viewing angle</span><span class="sxs-lookup"><span data-stu-id="9686a-226">Viewing angle</span></span> | <span data-ttu-id="9686a-227">Size</span><span class="sxs-lookup"><span data-stu-id="9686a-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="9686a-228">2m</span><span class="sxs-lookup"><span data-stu-id="9686a-228">2m</span></span>  | <span data-ttu-id="9686a-229">no smaller than 1°</span><span class="sxs-lookup"><span data-stu-id="9686a-229">no smaller than 1°</span></span> | <span data-ttu-id="9686a-230">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="9686a-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="9686a-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="9686a-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="9686a-232">*Target size for hand ray or gaze interaction*</span><span class="sxs-lookup"><span data-stu-id="9686a-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a><span data-ttu-id="9686a-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span><span class="sxs-lookup"><span data-stu-id="9686a-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span></span>

<span data-ttu-id="9686a-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span><span class="sxs-lookup"><span data-stu-id="9686a-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="9686a-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span><span class="sxs-lookup"><span data-stu-id="9686a-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="9686a-236">Interactable</span><span class="sxs-lookup"><span data-stu-id="9686a-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="9686a-237">Button</span><span class="sxs-lookup"><span data-stu-id="9686a-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="9686a-238">Hand interaction examples scene</span><span class="sxs-lookup"><span data-stu-id="9686a-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="9686a-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span><span class="sxs-lookup"><span data-stu-id="9686a-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="9686a-240">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="9686a-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="9686a-241">Consulta también</span><span class="sxs-lookup"><span data-stu-id="9686a-241">See also</span></span>

* [<span data-ttu-id="9686a-242">Cursores</span><span class="sxs-lookup"><span data-stu-id="9686a-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9686a-243">Hand ray</span><span class="sxs-lookup"><span data-stu-id="9686a-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9686a-244">Button</span><span class="sxs-lookup"><span data-stu-id="9686a-244">Button</span></span>](button.md)
* [<span data-ttu-id="9686a-245">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="9686a-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9686a-246">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9686a-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9686a-247">Manipulation</span><span class="sxs-lookup"><span data-stu-id="9686a-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9686a-248">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="9686a-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9686a-249">Near menu</span><span class="sxs-lookup"><span data-stu-id="9686a-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9686a-250">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="9686a-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9686a-251">Voice command</span><span class="sxs-lookup"><span data-stu-id="9686a-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9686a-252">Teclado</span><span class="sxs-lookup"><span data-stu-id="9686a-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9686a-253">Tooltip</span><span class="sxs-lookup"><span data-stu-id="9686a-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9686a-254">Slate</span><span class="sxs-lookup"><span data-stu-id="9686a-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="9686a-255">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="9686a-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="9686a-256">Shader</span><span class="sxs-lookup"><span data-stu-id="9686a-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="9686a-257">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="9686a-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9686a-258">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="9686a-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9686a-259">Surface magnetism</span><span class="sxs-lookup"><span data-stu-id="9686a-259">Surface magnetism</span></span>](surface-magnetism.md)
