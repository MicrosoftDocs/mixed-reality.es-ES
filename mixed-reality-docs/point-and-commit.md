---
title: Apuntar y confirmar con las manos
description: Introducción al modelo de entrada de apuntar y confirmar
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, interacción, diseño, HoloLens, manos, lejos, apuntar y confirmar
ms.openlocfilehash: e454b7f26b402d5c168323762865d10f7feb8a17
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437647"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="5873b-104">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="5873b-104">Point and commit with hands</span></span>

<span data-ttu-id="5873b-105">Apuntar y confirmar con las manos es un modelo de entrada que permite a los usuarios seleccionar como destino, seleccionar y manipular contenidos 2D y objetos 3D que están fuera de su alcance.</span><span class="sxs-lookup"><span data-stu-id="5873b-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects that are out of reach.</span></span> <span data-ttu-id="5873b-106">Esta técnica de interacción "lejana" es única de la realidad mixta y no es la forma en que los seres humanos interactúan de forma natural con el mundo real.</span><span class="sxs-lookup"><span data-stu-id="5873b-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally interact with the real world.</span></span> <span data-ttu-id="5873b-107">Por ejemplo, en la película de superhéroes *X-Men*, el personaje [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) es capaz de llegar a objetos lejanos y manipularlos a distancia con las manos.</span><span class="sxs-lookup"><span data-stu-id="5873b-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="5873b-108">Esto no es algo que los seres humanos pueden hacer en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="5873b-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="5873b-109">Tanto en HoloLens (AR) como en Mixed Reality (MR), dotamos a los usuarios con poderes mágicos y eliminamos la limitación física del mundo real, no solo para tener una magnífica experiencia con contenido holográfico, sino también para aumentar la eficacia y eficiencia de las interacciones.</span><span class="sxs-lookup"><span data-stu-id="5873b-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic content but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="5873b-110">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="5873b-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="5873b-111"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="5873b-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="5873b-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="5873b-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="5873b-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="5873b-113"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="5873b-114"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="5873b-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="5873b-115">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="5873b-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="5873b-116">❌ No se admite</span><span class="sxs-lookup"><span data-stu-id="5873b-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="5873b-117">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="5873b-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="5873b-118">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="5873b-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="5873b-119">_"Apuntar y confirmar con las manos"_ es una de las nuevas características que utiliza el nuevo sistema articulado de seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="5873b-119">_"Point and commit with hands"_ is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="5873b-120">Este modelo de entrada también es el principal en los cascos envolventes mediante el uso de controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="5873b-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="5873b-121">Rayos de las manos</span><span class="sxs-lookup"><span data-stu-id="5873b-121">Hand rays</span></span>

<span data-ttu-id="5873b-122">En HoloLens 2, hemos creado un haz que sale desde el centro de la palma de la mano.</span><span class="sxs-lookup"><span data-stu-id="5873b-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="5873b-123">Dicho rayo se trata como una extensión de la mano.</span><span class="sxs-lookup"><span data-stu-id="5873b-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="5873b-124">Un cursor con forma de anillo se acopla al final del rayo para indicar la ubicación en que el rayo se cruza con un objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="5873b-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="5873b-125">El objeto en que se posa el cursor puede recibir comandos gestuales de la mano.</span><span class="sxs-lookup"><span data-stu-id="5873b-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="5873b-126">Este comando gestual básico se desencadena al usar los dedos pulgar e índice para realizar la acción de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="5873b-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="5873b-127">Si se usa el haz de mano para apuntar y la acción de pulsar en el aire para confirmar, los usuarios pueden activar un botón o un hipervínculo.</span><span class="sxs-lookup"><span data-stu-id="5873b-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="5873b-128">Con más gestos compuestos, los usuarios son capaces de navegar por el contenido web y manipular objetos 3D a distancia.</span><span class="sxs-lookup"><span data-stu-id="5873b-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="5873b-129">El diseño visual del rayo de la mano también debe reaccionar a estos estados de apuntar y confirmar, como se describe y se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="5873b-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="5873b-130">![haces de mano que apuntan](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-130">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="5873b-131">**Estado de apuntar**</span><span class="sxs-lookup"><span data-stu-id="5873b-131">**Pointing state**</span></span><br>
        <span data-ttu-id="5873b-132">En el estado *señalar*, el rayo es una línea discontinua y el cursor tiene forma de anillo.</span><span class="sxs-lookup"><span data-stu-id="5873b-132">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5873b-133">![haces de mano que confirman](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-133">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="5873b-134">**Estado de confirmación**</span><span class="sxs-lookup"><span data-stu-id="5873b-134">**Commit state**</span></span><br>
        <span data-ttu-id="5873b-135">En el estado *confirmar*, el rayo se convierte en una línea sólida y el cursor se reduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="5873b-135">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="transition-between-near-and-far"></a><span data-ttu-id="5873b-136">Transición entre cerca y lejos</span><span class="sxs-lookup"><span data-stu-id="5873b-136">Transition between near and far</span></span>

<span data-ttu-id="5873b-137">En lugar de usar un gesto concreto, como "apuntar con el dedo índice" para dirigir el haz, hemos diseñado el haz para que parta del centro de la palma de la mano, con el fin de liberar y reservar los cinco dedos para los gestos más manipulativos, como acercar los dedos y agarrar.</span><span class="sxs-lookup"><span data-stu-id="5873b-137">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="5873b-138">Con este diseño, creamos solo un modelo mental, se usa el mismo conjunto de gestos de las manos para la interacción cercana y la lejana.</span><span class="sxs-lookup"><span data-stu-id="5873b-138">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="5873b-139">Puedes usar el mismo gesto de arrastrar para manipular objetos que se encuentren a distinta distancia.</span><span class="sxs-lookup"><span data-stu-id="5873b-139">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="5873b-140">La invocación de los haces es automática y se basa en la proximidad:</span><span class="sxs-lookup"><span data-stu-id="5873b-140">The invocation of the rays is automatic and proximity based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5873b-141">![Manipulación cercana](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-141">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="5873b-142">**Manipulación cercana**</span><span class="sxs-lookup"><span data-stu-id="5873b-142">**Near manipulation**</span></span><br>
        <span data-ttu-id="5873b-143">Cuando a un objeto se llega estirando el brazo (aproximadamente 50 cm), los haces se desactivan automáticamente, lo que fomenta la interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="5873b-143">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5873b-144">![Manipulación lejana](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-144">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="5873b-145">**Manipulación lejana**</span><span class="sxs-lookup"><span data-stu-id="5873b-145">**Far manipulation**</span></span><br>
        <span data-ttu-id="5873b-146">Cuando el objeto está a más de 50 cm, los rayos se activan.</span><span class="sxs-lookup"><span data-stu-id="5873b-146">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="5873b-147">La transición suave y sin problemas.</span><span class="sxs-lookup"><span data-stu-id="5873b-147">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="5873b-148">Interacción con una tableta táctil 2D</span><span class="sxs-lookup"><span data-stu-id="5873b-148">2D slate interaction</span></span>

<span data-ttu-id="5873b-149">Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web.</span><span class="sxs-lookup"><span data-stu-id="5873b-149">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="5873b-150">El concepto de diseño para la interacción lejana con una tableta táctil 2D es usar los rayos de las manos para buscar el objetivo y pulsar en el aire para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="5873b-150">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="5873b-151">Después de buscar el destino con un rayo de la mano, los usuarios pueden pulsar en el aire para desencadenar un hipervínculo o un botón.</span><span class="sxs-lookup"><span data-stu-id="5873b-151">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="5873b-152">Pueden usar una mano para "pulsar en el aire y arrastrar" a fin de desplazar el contenido de la tableta táctil hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="5873b-152">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="5873b-153">El movimiento relativo de usar las dos manos para pulsar en el aire y arrastrar puede acercar y alejar el contenido de la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="5873b-153">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="5873b-154">Si se seleccionan como destino del rayo las esquinas y los bordes aparece la prestación de manipulación más cercana.</span><span class="sxs-lookup"><span data-stu-id="5873b-154">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="5873b-155">Al "agarrar y arrastrar" las prestaciones de manipulación, los usuarios pueden realizar un escalado uniforme mediante las prestaciones de la esquina y redistribuir la tableta táctil mediante las prestaciones del borde.</span><span class="sxs-lookup"><span data-stu-id="5873b-155">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="5873b-156">El procedimiento de agarrar y arrastrar la barra holográfica de la parte superior de la tableta táctil 2D permite a los usuarios mover toda la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="5873b-156">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5873b-157">![Hacer clic en la interacción con una tableta táctil 2D](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-157">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="5873b-158">**Hacer clic**</span><span class="sxs-lookup"><span data-stu-id="5873b-158">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5873b-159">![Desplazar en la interacción con una tableta táctil 2D](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-159">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="5873b-160">**Desplazar**</span><span class="sxs-lookup"><span data-stu-id="5873b-160">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5873b-161">![Zoom en la interacción con una tableta táctil 2D](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-161">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="5873b-162">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="5873b-162">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="5873b-163">**Para manipular la tableta táctil 2D**</span><span class="sxs-lookup"><span data-stu-id="5873b-163">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="5873b-164">los usuarios apuntan el rayo de la mano a las esquinas y bordes y aparece la prestación de manipulación más cercana.</span><span class="sxs-lookup"><span data-stu-id="5873b-164">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="5873b-165">Al aplicar un gesto de manipulación en la prestación, los usuarios pueden realizar un escalado uniforme mediante la prestación de la esquina y redistribuir la tableta táctil mediante la prestación del borde.</span><span class="sxs-lookup"><span data-stu-id="5873b-165">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="5873b-166">Al aplicar un gesto de manipulación a la barra holográfica de la parte superior de la tableta táctil 2D, los usuarios pueden mover toda la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="5873b-166">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>


<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="5873b-167">Manipulación de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="5873b-167">3D object manipulation</span></span>

<span data-ttu-id="5873b-168">En la manipulación directa, hay dos formas de que los usuarios manipulen objetos 3D, la manipulación con prestaciones y la manipulación sin prestaciones.</span><span class="sxs-lookup"><span data-stu-id="5873b-168">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="5873b-169">En el modelo de señalar y confirmar, los usuarios son capaces de conseguir exactamente las mismas tareas a través de los rayos de las manos.</span><span class="sxs-lookup"><span data-stu-id="5873b-169">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="5873b-170">No se necesita ningún aprendizaje adicional.</span><span class="sxs-lookup"><span data-stu-id="5873b-170">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="5873b-171">Manipulación con prestaciones</span><span class="sxs-lookup"><span data-stu-id="5873b-171">Affordance-based manipulation</span></span>
<span data-ttu-id="5873b-172">Los usuarios usan los rayos de las manos para apuntar y mostrar el rectángulo de selección y las prestaciones de manipulación.</span><span class="sxs-lookup"><span data-stu-id="5873b-172">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="5873b-173">Los usuarios pueden aplicar el gesto de manipulación al rectángulo de selección para mover todo el objeto, a las prestaciones del borde para girarlo y a las prestaciones de la esquina para escalarlo de forma uniforme.</span><span class="sxs-lookup"><span data-stu-id="5873b-173">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="5873b-174">![Movimiento lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-174">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="5873b-175">**Mover**</span><span class="sxs-lookup"><span data-stu-id="5873b-175">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5873b-176">![Giro lejano en la manipulación de objetos 3D](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-176">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="5873b-177">**Girar**</span><span class="sxs-lookup"><span data-stu-id="5873b-177">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5873b-178">![Escala lejana en la manipulación de objetos 3D](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-178">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="5873b-179">**Escalar**</span><span class="sxs-lookup"><span data-stu-id="5873b-179">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="5873b-180">Manipulación sin prestaciones</span><span class="sxs-lookup"><span data-stu-id="5873b-180">Non-affordance based manipulation</span></span>
<span data-ttu-id="5873b-181">Los usuarios señalan con los rayos de las manos para mostrar el rectángulo de selección y, después, le aplican directamente los gestos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="5873b-181">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="5873b-182">Con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano.</span><span class="sxs-lookup"><span data-stu-id="5873b-182">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="5873b-183">Con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.</span><span class="sxs-lookup"><span data-stu-id="5873b-183">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="5873b-184">Gestos instintivos</span><span class="sxs-lookup"><span data-stu-id="5873b-184">Instinctual gestures</span></span>
<span data-ttu-id="5873b-185">El concepto de gestos instintivos para señalar y confirmar es similar a la de la [manipulación directa con las manos](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="5873b-185">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="5873b-186">Los gestos que los usuarios realizan en un objeto 3D los guía el diseño de las prestaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="5873b-186">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="5873b-187">Por ejemplo, un punto de control pequeño podría motivar a los usuarios a acercar los dedos pulgar e índice, mientras que si un usuario quiere agarrar un objeto mayor, debe usar los cinco dedos.</span><span class="sxs-lookup"><span data-stu-id="5873b-187">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5873b-188">![gestos instintivos para objetos lejanos pequeños](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-188">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="5873b-189">**Objeto pequeño**</span><span class="sxs-lookup"><span data-stu-id="5873b-189">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5873b-190">![gestos instintivos para objetos lejanos medianos](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-190">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="5873b-191">**Objeto mediano**</span><span class="sxs-lookup"><span data-stu-id="5873b-191">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5873b-192">![gestos instintivos para objetos lejanos grandes](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-192">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="5873b-193">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="5873b-193">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="5873b-194">Diseño simétrico entre las manos y 6 controladores DoF</span><span class="sxs-lookup"><span data-stu-id="5873b-194">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="5873b-195">El concepto de apuntar y confirmar para la interacción lejana se creó y definió inicialmente para el Portal de realidad mixta (MRP), donde un usuario lleva puesto un casco envolvente e interactúa con objetos 3D a través de los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="5873b-195">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="5873b-196">Los controladores de movimiento lanzar rayos para señalar y manipular objetos lejanos.</span><span class="sxs-lookup"><span data-stu-id="5873b-196">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="5873b-197">Hay botones en los controladores para confirmar más acciones diferentes.</span><span class="sxs-lookup"><span data-stu-id="5873b-197">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="5873b-198">Aprovechamos el modelo de interacción de rayos y los acoplamos a ambas manos.</span><span class="sxs-lookup"><span data-stu-id="5873b-198">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="5873b-199">Con este diseño simétrico, los usuarios que están familiarizados con MRP no necesitan aprender otro modelo de interacción para señalar y manipular a distancia cuando usan HoloLens 2, y viceversa.</span><span class="sxs-lookup"><span data-stu-id="5873b-199">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="5873b-200">![diseño simétrico para haces con controladores](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-200">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="5873b-201">**Haces de controlador**</span><span class="sxs-lookup"><span data-stu-id="5873b-201">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5873b-202">![diseño simétrico para haces con manos](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="5873b-202">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="5873b-203">**Haces de mano**</span><span class="sxs-lookup"><span data-stu-id="5873b-203">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="5873b-204">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5873b-204">See also</span></span>
* [<span data-ttu-id="5873b-205">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="5873b-205">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5873b-206">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="5873b-206">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5873b-207">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="5873b-207">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5873b-208">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="5873b-208">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="5873b-209">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="5873b-209">Instinctual interactions</span></span>](interaction-fundamentals.md)