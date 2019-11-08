---
title: Manipulación directa con las manos
description: Introducción al modelo de entrada mediante manipulación directa
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens
ms.openlocfilehash: ed3b25fe9a7dd404d07073b578b8da13e1984cab
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435918"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="0a2b7-104">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="0a2b7-104">Direct manipulation with hands</span></span>
<span data-ttu-id="0a2b7-105">La manipulación directa es un modelo de entrada de datos que implica tocar hologramas directamente con las manos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-105">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="0a2b7-106">La idea que impulsa este concepto es que los objetos se comporten exactamente igual que lo hacen en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-106">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="0a2b7-107">Para activar los botones no hay más que presionarlos, para elegir los objetos no hay más que agarrarlos y el contenido 2D se comporta como una pantalla táctil virtual.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-107">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="0a2b7-108">Por eso a los usuarios les resulta muy fácil y divertido aprender la manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-108">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="0a2b7-109">Se considera un modelo de entrada "cercano" porque se usa con preferencia para interactuar con contenido que está al alcance de los brazos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-109">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="0a2b7-110">La manipulación directa utiliza prestaciones, lo que significa que es fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-110">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="0a2b7-111">No hay que enseñar ningún gesto simbólico a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-111">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="0a2b7-112">Todas las interacciones se crean en torno a un elemento visual que se puede tocar o agarrar.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-112">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="0a2b7-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0a2b7-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="0a2b7-114"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="0a2b7-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="0a2b7-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0a2b7-115"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="0a2b7-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0a2b7-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="0a2b7-117"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="0a2b7-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="0a2b7-118">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="0a2b7-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="0a2b7-119">❌ No se admite</span><span class="sxs-lookup"><span data-stu-id="0a2b7-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="0a2b7-120">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="0a2b7-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="0a2b7-121">➕ Una alternativa, se recomienda <a href="point-and-commit.md">apuntar y confirmar con las manos</a>.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-121">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="0a2b7-122">La manipulación directa es un modelo de entrada principal de HoloLens 2, que usa el nuevo sistema articulado de seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-122">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="0a2b7-123">El modelo de entrada también está disponible en los cascos envolventes mediante el uso de controladores de movimiento, pero no se recomienda como medio principal de interacción fuera de la manipulación de objetos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-123">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="0a2b7-124">La manipulación directa no está disponible en HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="0a2b7-124">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="0a2b7-125">Dedo de colisión</span><span class="sxs-lookup"><span data-stu-id="0a2b7-125">Collidable fingertip</span></span>

<span data-ttu-id="0a2b7-126">En HoloLens 2, se reconocen las manos del usuario y se interpretan como modelos óseos de las manos derecha e izquierda.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-126">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="0a2b7-127">Para implementar la idea de tocar los hologramas directamente con las manos, se tendrían que acoplar cinco colisionadores a los cinco dedos del modelo óseo de cada mano.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-127">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="0a2b7-128">Sin embargo, dada la falta de información procedente del tacto, diez dedos de colisión pueden provocar colisiones inesperadas e impredecibles con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-128">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="0a2b7-129">De ahí que se sugiera colocar solo un colisionador en cada dedo índice.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-129">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="0a2b7-130">Los dedos índices de colisión se pueden seguir usando como puntos táctiles activos para diversos gestos táctiles que implican otros dedos como, por ejemplo, presionar con un dedo, pulsar con un dedo, presionar con dos dedos y presionar con cinco dedos, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-130">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-131">![dedo de colisión](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-131">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-132">**Dedo de colisión**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-132">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-133">![Presión de un dedo](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-133">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-134">**Presión de un dedo**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-134">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-135">![Pulsación de un dedo](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-135">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-136">**Pulsación de un dedo**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-136">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-137">![Presión de cinco dedos](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-137">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-138">**Presión de cinco dedos**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-138">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="0a2b7-139">Colisionador esférico</span><span class="sxs-lookup"><span data-stu-id="0a2b7-139">Sphere collider</span></span>

<span data-ttu-id="0a2b7-140">En lugar de usar una forma genérica aleatoria, se recomienda usar un colisionador esférico.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-140">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="0a2b7-141">A continuación, puedes representarlo visualmente para proporcionar mejores indicaciones a objetivos cercanos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-141">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="0a2b7-142">Para aumentar la precisión del toque, el diámetro de la esfera debe coincidir con el grosor del dedo índice.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-142">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="0a2b7-143">Será más fácil recuperar la variable de grosor del dedo con una llamada a la API de mano.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-143">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="0a2b7-144">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="0a2b7-144">Fingertip cursor</span></span>

<span data-ttu-id="0a2b7-145">Además de representar una esfera de colisión en el dedo índice, hemos creado un cursor de dedo avanzado para llegar mejor a objetivos cercanos de forma interactiva.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-145">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="0a2b7-146">Es un cursor en forma de anillo acoplado al dedo índice.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-146">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="0a2b7-147">En función de la proximidad, reacciona dinámicamente a un destino en términos de orientación y tamaño como se detalla a continuación:</span><span class="sxs-lookup"><span data-stu-id="0a2b7-147">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="0a2b7-148">Cuando un dedo índice se mueve hacia un holograma, el cursor está siempre paralelo a la superficie del holograma y su tamaño se reduce gradualmente en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-148">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="0a2b7-149">En cuanto el dedo toca la superficie, el tamaño del cursor se reduce hasta convertirse en un punto y emite un evento de toque.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-149">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="0a2b7-150">Con la información interactiva, los usuarios pueden realizar tareas en objetivos cercanos de forma muy precisa, como desencadenar un hipervínculo o presionar un botón, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-150">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-151">![Cursor de dedo lejano](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-151">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-152">**Cursor de dedo lejano**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-152">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-153">![Cursor de dedo cercano](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-153">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-154">**Cursor de dedo cercano**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-154">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-155">![Cursor de dedo de contacto](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-155">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-156">**Cursor de dedo de contacto**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-156">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="0a2b7-157">Rectángulo de selección con sombreador de proximidad</span><span class="sxs-lookup"><span data-stu-id="0a2b7-157">Bounding box with proximity shader</span></span>

<span data-ttu-id="0a2b7-158">El propio holograma también requiere la capacidad de proporcionar información visual y sonora para compensar la falta de información táctil.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-158">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="0a2b7-159">Con ese fin generamos el concepto de rectángulo de selección con sombreador de proximidad.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-159">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="0a2b7-160">Un rectángulo de selección es un área volumétrica mínima que rodea a un objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-160">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="0a2b7-161">El rectángulo de selección tiene un mecanismo de representación interactivo denominado sombreador de proximidad.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-161">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="0a2b7-162">Así es como se comporta el sombreador de proximidad:</span><span class="sxs-lookup"><span data-stu-id="0a2b7-162">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-163">![Mantener el puntero (lejos) con comentarios visuales](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-163">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-164">**Mantener el puntero (lejos)**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-164">**Hover (far)**</span></span><br>
       <span data-ttu-id="0a2b7-165">Cuando el dedo índice está dentro del alcance, se proyecta un foco con forma de dedo en la superficie del rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-165">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-166">![Mantener el puntero (cerca) con comentarios visuales](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-166">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-167">**Mantener el puntero (cerca)**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-167">**Hover (near)**</span></span><br>
        <span data-ttu-id="0a2b7-168">Cuando el dedo se acerca a la superficie, el foco se reduce en consecuencia.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-168">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-169">![Inicio de contacto](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-169">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-170">**Inicio de contacto**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-170">**Contact begins**</span></span><br>
       <span data-ttu-id="0a2b7-171">En cuanto el dedo toca la superficie, todo el rectángulo de selección cambia de color o genera efectos visuales que reflejan dicho estado.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-171">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-172">![Fin de contacto](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-172">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-173">**Fin de contacto**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-173">**Contact ends**</span></span><br>
       <span data-ttu-id="0a2b7-174">También se puede activar un efecto de sonido que mejore la información visual del toque.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-174">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="0a2b7-175">Botón presionable</span><span class="sxs-lookup"><span data-stu-id="0a2b7-175">Pressable button</span></span>

<span data-ttu-id="0a2b7-176">Con el dedo de colisión, los usuarios ya están listos para interactuar con el componente fundamental de la interfaz de usuario holográfica, como un botón presionable.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-176">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="0a2b7-177">Un botón presionable es un botón holográfico adaptado a una presión directa del dedo.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-177">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="0a2b7-178">Una vez más, debido a la falta de información táctil, el botón presionable cuenta con un par de mecanismos para abordar los problemas relacionados con la información táctil.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-178">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="0a2b7-179">El primer mecanismo es un rectángulo de selección con sombreador de proximidad, del que se ha proporcionado la información pertinente en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-179">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="0a2b7-180">Permite a los usuarios mejorar la sensación de proximidad a la hora de acercarse y entrar en contacto con un botón.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-180">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="0a2b7-181">El segundo mecanismo es la depresión.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-181">The second mechanism is depression.</span></span> <span data-ttu-id="0a2b7-182">La depresión crea una sensación de presión al tocar un botón con un dedo.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-182">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="0a2b7-183">El mecanismo garantiza que el botón se mueve estrechamente junto con el dedo por el eje de profundidad.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-183">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="0a2b7-184">El botón se puede desencadenar cuando se alcanza una profundidad designada (al presionar) o se sale de dicha profundidad (al soltar) después de atravesarlo.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-184">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="0a2b7-185">El efecto de sonido se debe agregar para mejorar la información cuando se desencadena el botón.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-185">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-186">![botón presionable lejano](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-186">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-187">**El dedo está lejos**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-187">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-188">![botón presionable cercano](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-188">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-189">**El dedo se acerca**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-189">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-190">![empieza el contacto con el botón presionable](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-190">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-191">**Inicio de contacto**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-191">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-192">![presión del botón presionable](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-192">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-193">**Presión**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-193">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="0a2b7-194">Interacción con una tableta táctil 2D</span><span class="sxs-lookup"><span data-stu-id="0a2b7-194">2D slate interaction</span></span>

<span data-ttu-id="0a2b7-195">Una tableta táctil 2D es un contenedor holográfico que hospeda contenido de aplicaciones 2D, como un explorador web.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-195">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="0a2b7-196">El concepto de diseño para interactuar con una tableta táctil 2D mediante la manipulación directa es aprovechar el modelo mental de interactuar con una pantalla táctil física.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-196">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="0a2b7-197">Para interactuar con el contacto de la tableta táctil</span><span class="sxs-lookup"><span data-stu-id="0a2b7-197">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-198">![Función táctil](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-198">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-199">**Función táctil**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-199">**Touch**</span></span><br>
       <span data-ttu-id="0a2b7-200">Utiliza el dedo índice para presionar un botón o un hipervínculo.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-200">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-201">![Desplazar](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-201">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-202">**Desplazar**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-202">**Scroll**</span></span><br>
        <span data-ttu-id="0a2b7-203">Utiliza el dedo índice para desplazar el contenido de la tableta táctil hacia arriba y abajo.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-203">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-204">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-204">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-205">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-205">**Zoom**</span></span><br>
       <span data-ttu-id="0a2b7-206">Los dos dedos índices del usuario se utilizan para acercar y alejar el contenido de la tableta táctil, en función del movimiento relativo de los dedos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-206">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="0a2b7-207">Para manipular la propia tableta táctil 2D</span><span class="sxs-lookup"><span data-stu-id="0a2b7-207">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-208">![Mover](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-208">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-209">**Mover**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-209">**Move**</span></span><br>
       <span data-ttu-id="0a2b7-210">Mueve las manos a las esquinas y bordes para mostrar las prestaciones de manipulación más cercanas.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-210">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="0a2b7-211">Agarra la barra holográfica de la parte superior de la tableta táctil 2D para mover toda la tableta táctil.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-211">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-212">![Escalar](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-212">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-213">**Escalar**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-213">**Scale**</span></span><br>
        <span data-ttu-id="0a2b7-214">Agarra las prestaciones de manipulación y realiza un escalado uniforme mediante las prestaciones de esquina.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-214">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-215">![Redistribuir](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-215">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-216">**Redistribuir**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-216">**Reflow**</span></span><br>
       <span data-ttu-id="0a2b7-217">Agarra las prestaciones de manipulación y realiza reflujo a través de las prestaciones de borde.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-217">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="0a2b7-218">Manipulación de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="0a2b7-218">3D object manipulation</span></span>

<span data-ttu-id="0a2b7-219">HoloLens 2 permite a los usuarios habilitar sus manos para dirigir y manipular objetos holográficos 3D mediante la aplicación de un rectángulo de selección a cada objeto 3D.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-219">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="0a2b7-220">El rectángulo de selección proporciona una mejor percepción de la profundidad gracias a su sombreador de proximidad.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-220">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="0a2b7-221">Con el rectángulo de selección, hay dos enfoques de diseño para la manipulación de objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-221">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="0a2b7-222">Manipulación con prestaciones</span><span class="sxs-lookup"><span data-stu-id="0a2b7-222">Affordance-based manipulation</span></span>

<span data-ttu-id="0a2b7-223">La manipulación con prestaciones te permite manipular el objeto 3D a través de un rectángulo de selección por las prestaciones de manipulación que hay a su alrededor.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-223">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-224">![Mover](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-224">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-225">**Mover**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-225">**Move**</span></span><br>
       <span data-ttu-id="0a2b7-226">En cuanto la mano de un usuario esté cerca de un objeto 3D, se mostrarán el rectángulo de selección y la prestación más cercana.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-226">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="0a2b7-227">Los usuarios pueden agarrar el rectángulo de selección para mover todo el objeto.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-227">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-228">![Girar](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-228">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-229">**Girar**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-229">**Rotate**</span></span><br>
        <span data-ttu-id="0a2b7-230">Los usuarios pueden agarrar las prestaciones de borde para girar.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-230">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-231">![Escalar](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-231">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-232">**Escalar**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-232">**Scale**</span></span><br>
       <span data-ttu-id="0a2b7-233">Los usuarios pueden agarrar las prestaciones de esquina para escalar de forma uniforme.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-233">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="0a2b7-234">Manipulación sin prestaciones</span><span class="sxs-lookup"><span data-stu-id="0a2b7-234">Non-affordance based manipulation</span></span>

<span data-ttu-id="0a2b7-235">La manipulación sin prestaciones no acopla ninguna prestación al rectángulo de selección.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-235">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="0a2b7-236">Los usuarios solo pueden mostrar el rectángulo de selección e interactuar directamente con él.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-236">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="0a2b7-237">Si el rectángulo de selección se agarra con una mano, la traslación y rotación del objeto se asocian con el movimiento y la orientación de la mano.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-237">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="0a2b7-238">Cuando el objeto se agarra con dos manos, los usuarios pueden trasladarlo, escalarlo y girarlo en función de los movimientos relativos de las dos manos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-238">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="0a2b7-239">La manipulación específica requiere precisión.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-239">Specific manipulation requires precision.</span></span> <span data-ttu-id="0a2b7-240">Se recomienda usar la **manipulación con prestaciones**, ya que proporciona un alto nivel de granularidad.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-240">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="0a2b7-241">Para la manipulación flexible, se recomienda usar la **manipulación sin prestaciones**, ya que permite experiencias instantáneas y divertidas.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-241">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="0a2b7-242">Gestos instintivos</span><span class="sxs-lookup"><span data-stu-id="0a2b7-242">Instinctual gestures</span></span>

<span data-ttu-id="0a2b7-243">Con HoloLens (1.ª generación), enseñamos a los usuarios un par de gestos predefinidos, como eclosionar y pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-243">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="0a2b7-244">En el caso de HoloLens 2, no pedimos a los usuarios que memoricen gestos simbólicos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-244">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="0a2b7-245">Todos los gestos que los usuarios necesitan (cuando deben interactuar con hologramas y contenido) son instintivos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-245">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="0a2b7-246">Para lograr gestos instintivos ayuda a los usuarios a realizar los gestos mediante el diseño de prestaciones de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-246">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="0a2b7-247">Por ejemplo, si se anima al usuario a arrastrar un objeto o un punto de control acercando dos dedos, el objeto o el punto de control deben ser pequeños.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-247">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="0a2b7-248">Si queremos que el agarre lo realice con cinco dedos, el objeto o el punto de control deberían ser relativamente grandes.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-248">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="0a2b7-249">Al igual que los botones, un botón pequeño limitaría a los usuarios a presionarlo con un solo dedo; un botón grande instaría a los usuarios a presionarlo con las palmas de las manos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-249">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="0a2b7-250">![Mover](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-250">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-251">**Objeto pequeño**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-251">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-252">![Girar](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-252">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="0a2b7-253">**Objeto mediano**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-253">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a2b7-254">![Escalar](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0a2b7-254">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="0a2b7-255">**Objeto grande**</span><span class="sxs-lookup"><span data-stu-id="0a2b7-255">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="0a2b7-256">Diseño simétrico entre las manos y 6 controladores DoF</span><span class="sxs-lookup"><span data-stu-id="0a2b7-256">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="0a2b7-257">Es posible que hayas observado que hay paralelos de interacción que podemos dibujar en AR y controladores de movimiento en VR.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-257">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="0a2b7-258">Las dos entradas pueden usarse para desencadenar manipulaciones directas en sus respectivos entornos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-258">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="0a2b7-259">En HoloLens 2, la realización de las operaciones de agarrar y arrastrar con las manos a corta distancia funciona de forma muy parecida a como lo hace el botón de agarrar en los controladores de movimiento de WMR.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-259">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="0a2b7-260">Esto proporciona a los usuarios familiaridad en la interacción entre las dos plataformas, que puede resultar útil si alguna vez decides portar la aplicación de una plataforma a la otra.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-260">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>


<br>

---


<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="0a2b7-261">Optimización con el seguimiento de los ojos</span><span class="sxs-lookup"><span data-stu-id="0a2b7-261">Optimize with eye tracking</span></span>

<span data-ttu-id="0a2b7-262">La manipulación directa puede parecer mágica si funciona según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-262">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="0a2b7-263">No obstante, también puede resultar frustrante si no se puede mover la mano a ningún lugar sin desencadenar involuntariamente un holograma.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-263">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="0a2b7-264">El seguimiento de los ojos puede ayudar a identificar mejor la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-264">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="0a2b7-265">**Cuándo**: se reduce accidentalmente, lo que desencadena una respuesta de manipulación.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-265">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="0a2b7-266">El seguimiento de los ojos permite saber mejor lo que hace un usuario en cada momento.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-266">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="0a2b7-267">Por ejemplo, imagina que estás leyendo un texto (con instrucciones) de una holografía cuando te dispones a agarrar tu herramienta del mundo real.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-267">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="0a2b7-268">Al hacerlo, mueves la mano accidentalmente por unos botones holográficos interactivos que no te habías percatado de que estaban ahí (por ejemplo, pueden estar fuera del campo de visión del usuario).</span><span class="sxs-lookup"><span data-stu-id="0a2b7-268">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="0a2b7-269">Un resumen: si el usuario lleva un tiempo sin mirar un holograma, pero se ha detectado un evento de tocar o agarrar para él, es probable que el usuario no tuviera realmente intención de interactuar con el holograma.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-269">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="0a2b7-270">**Cuál**:  además de solucionar activaciones positivas falsas, otro ejemplo incluye una mejor identificación de qué hologramas agarrar o usar, ya que es posible que el punto de intersección preciso no esté claro desde tu perspectiva, sobre todo si hay varios hologramas colocados unos cerca de otros.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-270">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="0a2b7-271">Aunque en HoloLens 2 el seguimiento de los ojos tiene limitaciones en función de la precisión con la que puede determinar la mirada con los ojos, puede resultar muy útil para las interacciones cercanas debido a la disparidad de profundidad al interactuar con la entrada a mano.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-271">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="0a2b7-272">Esto significa que a veces es difícil determinar si la mano está detrás o delante de un holograma, por ejemplo, para agarrar con precisión un widget de manipulación.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-272">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="0a2b7-273">**A dónde**: usa información acerca de lo que mira un usuario con gestos que se realizan rápidamente.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-273">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="0a2b7-274">Agarra un holograma y tíralo hacia su destino previsto.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-274">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="0a2b7-275">Aunque es posible que a veces esto funcione, la realización rápida de gestos con la mano puede dar lugar a destinos muy imprecisos.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-275">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="0a2b7-276">Sin embargo, el seguimiento de los ojos podría mejorar la precisión del gesto.</span><span class="sxs-lookup"><span data-stu-id="0a2b7-276">However, eye tracking could improve the accuracy of the gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a2b7-277">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0a2b7-277">See also</span></span>

* [<span data-ttu-id="0a2b7-278">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="0a2b7-278">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0a2b7-279">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="0a2b7-279">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0a2b7-280">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="0a2b7-280">Instinctual interactions</span></span>](interaction-fundamentals.md)
