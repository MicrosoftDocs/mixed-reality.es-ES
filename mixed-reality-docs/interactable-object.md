---
title: Objeto interactuable
description: Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, IU, experiencia de usuario
ms.openlocfilehash: 5305af97e9811134212fc6c730727962bb9e8353
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105799"
---
# <a name="interactable-object"></a><span data-ttu-id="47fc7-105">Objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="47fc7-105">Interactable object</span></span>

![Objetos interactivos](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="47fc7-107">Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="47fc7-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="47fc7-108">En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción.</span><span class="sxs-lookup"><span data-stu-id="47fc7-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="47fc7-109">Cualquier elemento puede ser un **objeto interactuable** que desencadene un evento.</span><span class="sxs-lookup"><span data-stu-id="47fc7-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="47fc7-110">Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="47fc7-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="47fc7-111">Todavía hacemos uso de botones tradicionales en ciertas situaciones, como en la interfaz de usuario del cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="47fc7-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="47fc7-112">La representación visual del botón depende del contexto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="47fc7-113">Propiedades importantes del objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="47fc7-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="47fc7-114">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="47fc7-114">Visual cues</span></span>

<span data-ttu-id="47fc7-115">Las indicaciones visuales son indicaciones organolépticas recibidas por el ojo en forma de luz y procesadas por el sistema visual durante la percepción visual.</span><span class="sxs-lookup"><span data-stu-id="47fc7-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="47fc7-116">Dado que el sistema visual es dominante en muchas especies, especialmente en los seres humanos, las indicaciones visuales son una gran fuente de información sobre cómo se percibe el mundo.</span><span class="sxs-lookup"><span data-stu-id="47fc7-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="47fc7-117">Dado que los objetos holográficas se mezclan con el entorno real en realidad mixta, podría ser difícil comprender con qué objetos puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="47fc7-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="47fc7-118">En el caso de cualquier objeto interactuable de su experiencia, es importante proporcionar indicaciones visuales diferenciadas para cada estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="47fc7-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="47fc7-119">Esto ayuda al usuario a comprender qué parte de su experiencia es interactivable y hace que el usuario esté seguro mediante el uso de un método de interacción coherente.</span><span class="sxs-lookup"><span data-stu-id="47fc7-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="47fc7-120">Interacciones lejanas</span><span class="sxs-lookup"><span data-stu-id="47fc7-120">Far interactions</span></span>

<span data-ttu-id="47fc7-121">En el caso de los objetos que el usuario pueda interactuar con la mirada, el rayo y el rayo del controlador de movimiento, se recomienda tener una indicación visual diferente para estos tres Estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="47fc7-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="47fc7-122">![interactibleobject-States-](images/interactibleobject-states-default.jpg) predeterminada</span><span class="sxs-lookup"><span data-stu-id="47fc7-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="47fc7-123">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="47fc7-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="47fc7-124">Estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-124">Default idle state of the object.</span></span>
    <span data-ttu-id="47fc7-125">El cursor no está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-125">The cursor is not on the object.</span></span> <span data-ttu-id="47fc7-126">No se detecta la mano.</span><span class="sxs-lookup"><span data-stu-id="47fc7-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47fc7-127">![interactibleobject-States-](images/interactibleobject-states-targeted.jpg) de destino</span><span class="sxs-lookup"><span data-stu-id="47fc7-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="47fc7-128">**Estado de destino (mantener el mouse)**</span><span class="sxs-lookup"><span data-stu-id="47fc7-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="47fc7-129">Cuando el objeto se destine con el cursor de miración, la proximidad del dedo o el puntero del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="47fc7-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="47fc7-130">El cursor está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-130">The cursor is on the object.</span></span> <span data-ttu-id="47fc7-131">La mano se detecta y está lista.</span><span class="sxs-lookup"><span data-stu-id="47fc7-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47fc7-132">![interactibleobject-States-pressed](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="47fc7-133">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="47fc7-133">**Pressed state**</span></span><br>
        <span data-ttu-id="47fc7-134">Cuando el objeto se presiona con un gesto de pulsación de aire, presionar el dedo o el botón seleccionar del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="47fc7-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="47fc7-135">El cursor está en el objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-135">The cursor is on the object.</span></span> <span data-ttu-id="47fc7-136">Se detecta una mano, se puntea en el aire.</span><span class="sxs-lookup"><span data-stu-id="47fc7-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="47fc7-137">Puede usar técnicas como resaltado o escalado para proporcionar indicaciones visuales para el estado de entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="47fc7-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="47fc7-138">En la realidad mixta, puede encontrar los ejemplos de visualización de distintos Estados de entrada en el menú Inicio y con los botones de la barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="47fc7-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="47fc7-139">Este es el aspecto de estos Estados en un **botón holográfica**:</span><span class="sxs-lookup"><span data-stu-id="47fc7-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="47fc7-140">![interactibleobject-States-](images/MRTK_InteractableState-default.jpg) predeterminada</span><span class="sxs-lookup"><span data-stu-id="47fc7-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="47fc7-141">**Estado predeterminado (observación)**</span><span class="sxs-lookup"><span data-stu-id="47fc7-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47fc7-142">![interactibleobject-States-](images/MRTK_InteractableState-targeted.jpg) de destino</span><span class="sxs-lookup"><span data-stu-id="47fc7-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="47fc7-143">**Estado de destino (mantener el mouse)**</span><span class="sxs-lookup"><span data-stu-id="47fc7-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="47fc7-144">![interactibleobject-States-pressed](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="47fc7-145">**Estado presionado**</span><span class="sxs-lookup"><span data-stu-id="47fc7-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="47fc7-146">Interacciones cercanas (directas)</span><span class="sxs-lookup"><span data-stu-id="47fc7-146">Near interactions (direct)</span></span> 

<span data-ttu-id="47fc7-147">HoloLens 2 admite la entrada de seguimiento de mano articulada que permite interactuar con objetos.</span><span class="sxs-lookup"><span data-stu-id="47fc7-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="47fc7-148">Sin comentarios hápticos e percepción de profundidad perfecta, a veces puede ser difícil saber hasta dónde se encuentra su mano de un objeto o si lo toca.</span><span class="sxs-lookup"><span data-stu-id="47fc7-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="47fc7-149">Es importante proporcionar suficientes indicaciones visuales para comunicar el estado del objeto y, en particular, el estado de las manos con respecto a ese objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="47fc7-150">Use los comentarios visuales para comunicar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="47fc7-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="47fc7-151">**Predeterminado (observación)** : estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="47fc7-152">**Mantener el mouse**: cuando una mano está cerca de un holograma, cambie los objetos visuales para comunicar que esa mano está dirigida al holograma.</span><span class="sxs-lookup"><span data-stu-id="47fc7-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="47fc7-153">**Distancia y punto de interacción**: a medida que la mano se aproxima a un holograma, el diseño de comentarios para comunicar el punto de interacción proyectado, así como la distancia desde el objeto que es el dedo</span><span class="sxs-lookup"><span data-stu-id="47fc7-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="47fc7-154">**Inicio de contacto**: cambie los objetos visuales (Light, color) para comunicar que se ha producido una entrada táctil</span><span class="sxs-lookup"><span data-stu-id="47fc7-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="47fc7-155">**Agarre**: cambiar objetos visuales (claros, de color) cuando se agarre el objeto</span><span class="sxs-lookup"><span data-stu-id="47fc7-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="47fc7-156">**Extremos de contacto**: cambios visuales (claros, de color) cuando la entrada táctil ha finalizado</span><span class="sxs-lookup"><span data-stu-id="47fc7-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="47fc7-157">![al mantener el mouse (lejano)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="47fc7-158">**Mantener el mouse (lejano)**</span><span class="sxs-lookup"><span data-stu-id="47fc7-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="47fc7-159">Resaltado en función de la proximidad de la mano.</span><span class="sxs-lookup"><span data-stu-id="47fc7-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="47fc7-160">![mantener el mouse (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="47fc7-161">**Mantener el mouse (Near)**</span><span class="sxs-lookup"><span data-stu-id="47fc7-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="47fc7-162">Resaltar cambios de tamaño en función de la distancia a la mano.</span><span class="sxs-lookup"><span data-stu-id="47fc7-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="47fc7-163">![tocar y presionar](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="47fc7-164">**Tocar y presionar**</span><span class="sxs-lookup"><span data-stu-id="47fc7-164">**Touch / press**</span></span><br>
        <span data-ttu-id="47fc7-165">Comentarios de Visual Plus audio.</span><span class="sxs-lookup"><span data-stu-id="47fc7-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="47fc7-166">![agarre](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="47fc7-167">**Visión**</span><span class="sxs-lookup"><span data-stu-id="47fc7-167">**Grasp**</span></span><br>
        <span data-ttu-id="47fc7-168">Comentarios de Visual Plus audio.</span><span class="sxs-lookup"><span data-stu-id="47fc7-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="47fc7-169">Un [botón de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) es un ejemplo de cómo se visualizan los distintos Estados de interacción de entrada:</span><span class="sxs-lookup"><span data-stu-id="47fc7-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="47fc7-170">![](images/640px-interactibleobject-pressablebutton-default.jpg) predeterminada</span><span class="sxs-lookup"><span data-stu-id="47fc7-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="47fc7-171">**Predeterminada**</span><span class="sxs-lookup"><span data-stu-id="47fc7-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="47fc7-172">![mantener el puntero](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="47fc7-173">**Activada**</span><span class="sxs-lookup"><span data-stu-id="47fc7-173">**Hover**</span></span><br>
        <span data-ttu-id="47fc7-174">Revela un efecto de iluminación basado en proximidad.</span><span class="sxs-lookup"><span data-stu-id="47fc7-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="47fc7-175">![Función táctil](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="47fc7-176">**Función táctil**</span><span class="sxs-lookup"><span data-stu-id="47fc7-176">**Touch**</span></span><br>
        <span data-ttu-id="47fc7-177">Mostrar efecto de rizo.</span><span class="sxs-lookup"><span data-stu-id="47fc7-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="47fc7-178">![Presione](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="47fc7-179">**Pulse**</span><span class="sxs-lookup"><span data-stu-id="47fc7-179">**Press**</span></span><br>
        <span data-ttu-id="47fc7-180">Mueva la placa frontal.</span><span class="sxs-lookup"><span data-stu-id="47fc7-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="47fc7-181">La indicación visual "Ring" en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="47fc7-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="47fc7-182">En HoloLens 2, hay una indicación visual adicional que puede ayudar a la percepción del usuario de la profundidad.</span><span class="sxs-lookup"><span data-stu-id="47fc7-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="47fc7-183">Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="47fc7-184">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="47fc7-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="47fc7-185">Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="47fc7-186">*Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="47fc7-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="47fc7-187">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="47fc7-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="47fc7-188">![comentarios visuales sobre la proximidad](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="47fc7-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="47fc7-189">Señales de audio</span><span class="sxs-lookup"><span data-stu-id="47fc7-189">Audio cues</span></span>

<span data-ttu-id="47fc7-190">En el caso de las interacciones directas, los comentarios de audio adecuados pueden mejorar drásticamente la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="47fc7-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="47fc7-191">Use los comentarios de audio para comunicar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="47fc7-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="47fc7-192">**Inicio de contacto**: reproducir un sonido cuando se inicie Touch</span><span class="sxs-lookup"><span data-stu-id="47fc7-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="47fc7-193">**Contactos**finales: reproducir sonido en el extremo táctil</span><span class="sxs-lookup"><span data-stu-id="47fc7-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="47fc7-194">**Inicio**de la toma: reproducir sonido cuando se inicie la captura</span><span class="sxs-lookup"><span data-stu-id="47fc7-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="47fc7-195">Acabado de **agarre**: reproducir un sonido al finalizar la toma</span><span class="sxs-lookup"><span data-stu-id="47fc7-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="47fc7-196">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="47fc7-196">Voice commanding</span></span><br>
        <span data-ttu-id="47fc7-197">Para cualquier objeto interactuable, es importante admitir opciones de interacción alternativas.</span><span class="sxs-lookup"><span data-stu-id="47fc7-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="47fc7-198">De forma predeterminada, se recomienda que se admitan los [comandos de voz](voice-design.md) para cualquier objeto que sea interactuable.</span><span class="sxs-lookup"><span data-stu-id="47fc7-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="47fc7-199">Para mejorar la capacidad de detección, también puede proporcionar una información sobre herramientas durante el estado de mantener el mouse.</span><span class="sxs-lookup"><span data-stu-id="47fc7-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="47fc7-200">*Image: información sobre herramientas para el comando Voice*</span><span class="sxs-lookup"><span data-stu-id="47fc7-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comandos de voz](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="47fc7-202">Recomendaciones de ajuste de tamaño</span><span class="sxs-lookup"><span data-stu-id="47fc7-202">Sizing recommendations</span></span> 

<span data-ttu-id="47fc7-203">Para asegurarse de que los usuarios puedan tocar fácilmente todos los objetos interactivos, se recomienda asegurarse de que el interactuable cumple un tamaño mínimo (el ángulo visual se mide a menudo en grados de arco visual) en función de la distancia que se coloca del usuario.</span><span class="sxs-lookup"><span data-stu-id="47fc7-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="47fc7-204">El ángulo visual se basa en la distancia entre los ojos del usuario y el objeto y permanece constante, mientras que el tamaño físico del destino puede cambiar a medida que cambia la distancia del usuario.</span><span class="sxs-lookup"><span data-stu-id="47fc7-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="47fc7-205">Para determinar el tamaño físico necesario de un objeto en función de la distancia del usuario, pruebe a usar una calculadora de ángulo visual como [esta](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="47fc7-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="47fc7-206">A continuación se muestran las recomendaciones para tamaños mínimos de contenido interactuable.</span><span class="sxs-lookup"><span data-stu-id="47fc7-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="47fc7-207">Tamaño de destino para la interacción directa</span><span class="sxs-lookup"><span data-stu-id="47fc7-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="47fc7-208">Posición</span><span class="sxs-lookup"><span data-stu-id="47fc7-208">Distance</span></span> | <span data-ttu-id="47fc7-209">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="47fc7-209">Viewing angle</span></span> | <span data-ttu-id="47fc7-210">Size</span><span class="sxs-lookup"><span data-stu-id="47fc7-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="47fc7-211">45cm</span><span class="sxs-lookup"><span data-stu-id="47fc7-211">45cm</span></span>  | <span data-ttu-id="47fc7-212">no menor que 2 °</span><span class="sxs-lookup"><span data-stu-id="47fc7-212">no smaller than 2°</span></span> | <span data-ttu-id="47fc7-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="47fc7-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="47fc7-214">![tamaño de destino para la interacción directa](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="47fc7-215">*Tamaño de destino para la interacción directa*</span><span class="sxs-lookup"><span data-stu-id="47fc7-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="47fc7-216">Tamaño de destino de los botones</span><span class="sxs-lookup"><span data-stu-id="47fc7-216">Target size for buttons</span></span>

<span data-ttu-id="47fc7-217">Al crear botones para la interacción directa, se recomienda un tamaño mínimo mayor de 3,2 x 3,2 cm para asegurarse de que hay espacio suficiente para contener un icono y un posible texto.</span><span class="sxs-lookup"><span data-stu-id="47fc7-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="47fc7-218">Posición</span><span class="sxs-lookup"><span data-stu-id="47fc7-218">Distance</span></span> | <span data-ttu-id="47fc7-219">Tamaño mínimo</span><span class="sxs-lookup"><span data-stu-id="47fc7-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="47fc7-220">45cm</span><span class="sxs-lookup"><span data-stu-id="47fc7-220">45cm</span></span>  | <span data-ttu-id="47fc7-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="47fc7-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="47fc7-222">![tamaño de destino de los botones](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="47fc7-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="47fc7-223">*Tamaño de destino de los botones*</span><span class="sxs-lookup"><span data-stu-id="47fc7-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="47fc7-224">Tamaño de destino para la interacción de mano o de rayo</span><span class="sxs-lookup"><span data-stu-id="47fc7-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="47fc7-225">Posición</span><span class="sxs-lookup"><span data-stu-id="47fc7-225">Distance</span></span> | <span data-ttu-id="47fc7-226">Ángulo de visualización</span><span class="sxs-lookup"><span data-stu-id="47fc7-226">Viewing angle</span></span> | <span data-ttu-id="47fc7-227">Size</span><span class="sxs-lookup"><span data-stu-id="47fc7-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="47fc7-228">2m</span><span class="sxs-lookup"><span data-stu-id="47fc7-228">2m</span></span>  | <span data-ttu-id="47fc7-229">no menor que 1 °</span><span class="sxs-lookup"><span data-stu-id="47fc7-229">no smaller than 1°</span></span> | <span data-ttu-id="47fc7-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="47fc7-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="47fc7-231">![tamaño de destino de la interacción de rayo o de una mirada a mano](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="47fc7-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="47fc7-232">*Tamaño de destino para la interacción de mano o de rayo*</span><span class="sxs-lookup"><span data-stu-id="47fc7-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a><span data-ttu-id="47fc7-233">Objeto interactuable en MRTK (kit de herramientas de realidad mixta) para unidad</span><span class="sxs-lookup"><span data-stu-id="47fc7-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span></span>

<span data-ttu-id="47fc7-234">En **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , puede usar el script [**interactúable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) para que los objetos respondan a diversos tipos de Estados de interacción de entrada.</span><span class="sxs-lookup"><span data-stu-id="47fc7-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="47fc7-235">Admite varios tipos de temas que permiten definir Estados visuales mediante el control de las propiedades del objeto como el color, el tamaño, el material y el sombreador.</span><span class="sxs-lookup"><span data-stu-id="47fc7-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="47fc7-236">Interactuable</span><span class="sxs-lookup"><span data-stu-id="47fc7-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="47fc7-237">Button</span><span class="sxs-lookup"><span data-stu-id="47fc7-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="47fc7-238">Escena de ejemplos de interacción de mano</span><span class="sxs-lookup"><span data-stu-id="47fc7-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="47fc7-239">El sombreador estándar de MixedRealityToolkit proporciona varias opciones, como la **luz de proximidad** , que le ayuda a crear indicaciones visuales y de audio.</span><span class="sxs-lookup"><span data-stu-id="47fc7-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="47fc7-240">Sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="47fc7-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="47fc7-241">Consulta también</span><span class="sxs-lookup"><span data-stu-id="47fc7-241">See also</span></span>

* [<span data-ttu-id="47fc7-242">Cursores</span><span class="sxs-lookup"><span data-stu-id="47fc7-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="47fc7-243">Rayo de mano</span><span class="sxs-lookup"><span data-stu-id="47fc7-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="47fc7-244">Button</span><span class="sxs-lookup"><span data-stu-id="47fc7-244">Button</span></span>](button.md)
* [<span data-ttu-id="47fc7-245">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="47fc7-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="47fc7-246">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="47fc7-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="47fc7-247">Manipula</span><span class="sxs-lookup"><span data-stu-id="47fc7-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="47fc7-248">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="47fc7-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="47fc7-249">Menú Near</span><span class="sxs-lookup"><span data-stu-id="47fc7-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="47fc7-250">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="47fc7-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="47fc7-251">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="47fc7-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="47fc7-252">Teclado</span><span class="sxs-lookup"><span data-stu-id="47fc7-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="47fc7-253">Herramienta</span><span class="sxs-lookup"><span data-stu-id="47fc7-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="47fc7-254">Tabletas</span><span class="sxs-lookup"><span data-stu-id="47fc7-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="47fc7-255">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="47fc7-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="47fc7-256">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="47fc7-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="47fc7-257">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="47fc7-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="47fc7-258">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="47fc7-258">Surface magnetism</span></span>](surface-magnetism.md)