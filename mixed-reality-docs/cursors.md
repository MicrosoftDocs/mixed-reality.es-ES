---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª generación), HoloLens 2, realidad mixta, cursores, destinatarios, mirados, gestos
ms.openlocfilehash: 969906cb09e100dbdd289d78baba722a4bd32537
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723244"
---
# <a name="cursors"></a><span data-ttu-id="6210e-104">Cursores</span><span class="sxs-lookup"><span data-stu-id="6210e-104">Cursors</span></span>

![Cursores](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="6210e-106">Un cursor, o indicador del vector de destinatarios actual, proporciona comentarios continuos para que el usuario comprenda Dónde está el foco actual en ese momento.</span><span class="sxs-lookup"><span data-stu-id="6210e-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="6210e-107">El cursor permite al usuario comprender su punto de destino actual y actúa como comentario para indicar qué área, holograma o punto responderá a la entrada.</span><span class="sxs-lookup"><span data-stu-id="6210e-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="6210e-108">Es la representación digital de dónde el dispositivo entiende la atención del usuario (aunque es posible que no sea el mismo que determinar nada sobre sus intenciones).</span><span class="sxs-lookup"><span data-stu-id="6210e-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="6210e-109">Los comentarios proporcionados por el cursor ofrecen a los usuarios la posibilidad de anticiparse a cómo responderá el sistema, usar esa señal como comentario para comunicar mejor su intención al dispositivo y, en última instancia, tener más confianza sobre sus interacciones.</span><span class="sxs-lookup"><span data-stu-id="6210e-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="6210e-110">Hay 3 tipos de cursores: **Finger, Ray**y **Head-mirate**.</span><span class="sxs-lookup"><span data-stu-id="6210e-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="6210e-111">Estos cursores de señalización funcionan con diferentes modalidades de entrada en HoloLens, HoloLens 2 y auriculares envolvente.</span><span class="sxs-lookup"><span data-stu-id="6210e-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="6210e-112">A continuación se ofrecen instrucciones sobre qué tipo de cursor se debe utilizar para cada tipo de auriculares y modelo de interacción.</span><span class="sxs-lookup"><span data-stu-id="6210e-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="6210e-113">En el kit de herramientas de realidad mixta (MRTK), hemos creado módulos de cursores de arrastrar y colocar para ayudarle a crear la experiencia adecuada.</span><span class="sxs-lookup"><span data-stu-id="6210e-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="6210e-114">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="6210e-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="6210e-115"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="6210e-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="6210e-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="6210e-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="6210e-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="6210e-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="6210e-118"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="6210e-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="6210e-119">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="6210e-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6210e-120">✔️</span><span class="sxs-lookup"><span data-stu-id="6210e-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="6210e-121">Cursor de rayo</span><span class="sxs-lookup"><span data-stu-id="6210e-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="6210e-122">✔️</span><span class="sxs-lookup"><span data-stu-id="6210e-122">✔️</span></span></td>
        <td><span data-ttu-id="6210e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="6210e-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="6210e-124">Cursor de miras hacia abajo</span><span class="sxs-lookup"><span data-stu-id="6210e-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="6210e-125">✔️</span><span class="sxs-lookup"><span data-stu-id="6210e-125">✔️</span></span></td>
        <td><span data-ttu-id="6210e-126">✔️</span><span class="sxs-lookup"><span data-stu-id="6210e-126">✔️</span></span></td>
        <td><span data-ttu-id="6210e-127">✔️</span><span class="sxs-lookup"><span data-stu-id="6210e-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="6210e-128">Cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="6210e-128">Finger cursor</span></span>
<span data-ttu-id="6210e-129">El cursor de dedo solo está disponible en HoloLens 2 para mejorar el modo de interacción "[manipulación directa con manos](direct-manipulation.md)".</span><span class="sxs-lookup"><span data-stu-id="6210e-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="6210e-130">Para comprender mejor dónde apunta el dedo, hemos adjuntado anillos a las propinas de ambos dedos del índice.</span><span class="sxs-lookup"><span data-stu-id="6210e-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="6210e-131">El tamaño del anillo se basa en la proximidad del dedo a la superficie de la interfaz de usuario (cuanto más cerca del dedo, menor es el anillo) y se reducirá a una forma de punto cuando el dedo se ponga en contacto con la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6210e-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="6210e-132">![](images/finger-cursor.png) de cursor de dedo</span><span class="sxs-lookup"><span data-stu-id="6210e-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="6210e-133">**Estados de comentarios visuales del cursor de dedo** 1: el anillo se reduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="6210e-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="6210e-134">2: el anillo se alinea con la superficie.</span><span class="sxs-lookup"><span data-stu-id="6210e-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="6210e-135">3: el anillo es perpendicular al vector de dedo.</span><span class="sxs-lookup"><span data-stu-id="6210e-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="6210e-136">4: sin anillo.</span><span class="sxs-lookup"><span data-stu-id="6210e-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="6210e-137">Cursor de rayo</span><span class="sxs-lookup"><span data-stu-id="6210e-137">Ray cursor</span></span>
<span data-ttu-id="6210e-138">Los cursores de rayo se adjuntan al final de los rayos que apuntan mucho para permitir la manipulación de objetos que no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="6210e-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="6210e-139">En los auriculares envolventes, los rayos salen de los controladores de movimiento y finalizan los cursores de punto.</span><span class="sxs-lookup"><span data-stu-id="6210e-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="6210e-140">En HoloLens 2, aprovechamos el modelo mental de estos rayos de controlador de movimiento y los rayos de mano diseñados que se originan a partir de las palmeras y acaban en cursores en forma de anillo que son coherentes con los cursores de dedo utilizados en la manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="6210e-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="6210e-141">![controlador de cursor de rayo](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="6210e-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="6210e-142">**Cursores de rayo de controladores de movimiento**</span><span class="sxs-lookup"><span data-stu-id="6210e-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6210e-143">![mano de cursor de rayo](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="6210e-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="6210e-144">**Cursores de rayo de manos**</span><span class="sxs-lookup"><span data-stu-id="6210e-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="6210e-145">Cursor de miras hacia abajo</span><span class="sxs-lookup"><span data-stu-id="6210e-145">Head-gaze cursor</span></span>
<span data-ttu-id="6210e-146">El cursor de mira hacia abajo es un punto que se adjunta al final de un vector de miras hacia arriba invisible que usa la posición y la rotación del encabezado al punto.</span><span class="sxs-lookup"><span data-stu-id="6210e-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="6210e-147">Para ejecutar acciones, este cursor señalador se empareja con varias entradas de confirmación, como la pulsación de aire, los comandos de voz, la permanencia y la pulsación de botones.</span><span class="sxs-lookup"><span data-stu-id="6210e-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="6210e-148">En HoloLens 2, el encabezado de la mirada es mejor con cualquier entrada de confirmación que no se pulse en el aire, ya que habrá un conflicto de interacción entre la derivación del aire y los rayos de mano.</span><span class="sxs-lookup"><span data-stu-id="6210e-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="6210e-149">![mano del cursor de mira hacia abajo](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="6210e-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="6210e-150">**Cursor de mira hacia abajo con el gesto de mano**</span><span class="sxs-lookup"><span data-stu-id="6210e-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="6210e-151">![](images/head-gaze-cursor-voice.png) de voz de cursor de mira</span><span class="sxs-lookup"><span data-stu-id="6210e-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="6210e-152">**Cursor de mira hacia abajo con el comando de voz**</span><span class="sxs-lookup"><span data-stu-id="6210e-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="6210e-153">Recomendaciones de personalización de cursores</span><span class="sxs-lookup"><span data-stu-id="6210e-153">Cursor customization recommendations</span></span>
<span data-ttu-id="6210e-154">Si desea personalizar los comportamientos y los aspectos de los comentarios del cursor, estas son algunas recomendaciones de diseño:</span><span class="sxs-lookup"><span data-stu-id="6210e-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="6210e-155">Escala del cursor</span><span class="sxs-lookup"><span data-stu-id="6210e-155">Cursor scale</span></span>
* <span data-ttu-id="6210e-156">El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.</span><span class="sxs-lookup"><span data-stu-id="6210e-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="6210e-157">Dependiendo de la experiencia que cree, el escalado del cursor a medida que el usuario busca también es una consideración importante.</span><span class="sxs-lookup"><span data-stu-id="6210e-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="6210e-158">Por ejemplo, a medida que el usuario mira más en su experiencia, el cursor no debe ser demasiado pequeño, por lo que se pierde.</span><span class="sxs-lookup"><span data-stu-id="6210e-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="6210e-159">Al escalar el cursor, considere la posibilidad de aplicarle una animación de software a medida que se escale para darle una sensación orgánica.</span><span class="sxs-lookup"><span data-stu-id="6210e-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="6210e-160">Evite obstruir el contenido.</span><span class="sxs-lookup"><span data-stu-id="6210e-160">Avoid obstructing content.</span></span> <span data-ttu-id="6210e-161">Los hologramas son lo que hacen que la experiencia sea memorable y el cursor no debe apartarse de ellas.</span><span class="sxs-lookup"><span data-stu-id="6210e-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="6210e-162">Forma cursor no direccional</span><span class="sxs-lookup"><span data-stu-id="6210e-162">Directionless cursor shape</span></span>
* <span data-ttu-id="6210e-163">Aunque no hay ninguna forma de cursor derecha, se recomienda usar una forma sin dirección como un toro.</span><span class="sxs-lookup"><span data-stu-id="6210e-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="6210e-164">Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) puede confundir al usuario para que siempre mire ese modo.</span><span class="sxs-lookup"><span data-stu-id="6210e-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="6210e-165">Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario.</span><span class="sxs-lookup"><span data-stu-id="6210e-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="6210e-166">Por ejemplo, al escalar los hologramas en el sistema operativo de realidad mixta, el cursor incluye de forma temporal flechas que indican al usuario Cómo trasladar la mano para escalar el holograma.</span><span class="sxs-lookup"><span data-stu-id="6210e-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="6210e-167">Apariencia y funcionamiento</span><span class="sxs-lookup"><span data-stu-id="6210e-167">Look and feel</span></span>
* <span data-ttu-id="6210e-168">Un anillo o cursor con forma de aro funciona con muchas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="6210e-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="6210e-169">Elija un color y una forma que mejor represente la experiencia que va a crear.</span><span class="sxs-lookup"><span data-stu-id="6210e-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="6210e-170">Los cursores son especialmente propensos a la [separación de colores](hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="6210e-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="6210e-171">Un cursor pequeño con opacidad equilibrada mantiene informativa sin dominar la jerarquía visual.</span><span class="sxs-lookup"><span data-stu-id="6210e-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="6210e-172">Tenga en Cognizant el uso de sombras o resaltados detrás del cursor, ya que podrían obstruir el contenido y distraerse de la tarea a mano.</span><span class="sxs-lookup"><span data-stu-id="6210e-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="6210e-173">Los cursores deben alinearse con las superficies de la aplicación y Hug, lo que le dará la sensación de que el sistema puede ver dónde están buscando, pero también que el sistema es consciente de su entorno.</span><span class="sxs-lookup"><span data-stu-id="6210e-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="6210e-174">Por ejemplo, en el sistema operativo de realidad mixta, el cursor se alinea con las superficies del mundo del usuario, lo que crea un sentimiento de sensibilización del mundo incluso cuando el usuario no está mirando directamente a un holograma.</span><span class="sxs-lookup"><span data-stu-id="6210e-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="6210e-175">El bloqueo magnético del cursor en un elemento interactivo cuando está dentro de proximidad puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando realice una acción de selección.</span><span class="sxs-lookup"><span data-stu-id="6210e-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="6210e-176">Indicaciones visuales</span><span class="sxs-lookup"><span data-stu-id="6210e-176">Visual cues</span></span>
* <span data-ttu-id="6210e-177">Si su experiencia se centra en un solo holograma, el cursor debe alinearse y Hug solo ese holograma y cambiar de forma cuando mira el holograma.</span><span class="sxs-lookup"><span data-stu-id="6210e-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="6210e-178">Esto puede transmitir al usuario que el holograma es accionable y puede interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="6210e-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="6210e-179">Si la aplicación usa la asignación espacial, el cursor podría alinear y Hug cada superficie que ve.</span><span class="sxs-lookup"><span data-stu-id="6210e-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="6210e-180">Esto proporciona comentarios a los usuarios de que HoloLens y su aplicación pueden ver su espacio.</span><span class="sxs-lookup"><span data-stu-id="6210e-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="6210e-181">Esto refuerza el hecho de que los hologramas son reales y en nuestro mundo y ayudan a salvar la brecha entre real y virtual.</span><span class="sxs-lookup"><span data-stu-id="6210e-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="6210e-182">Tenga una idea de lo que debe hacer el cursor cuando no haya ningún holograma o superficie en la vista.</span><span class="sxs-lookup"><span data-stu-id="6210e-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="6210e-183">Colocarlo a una distancia predeterminada delante del usuario es una opción.</span><span class="sxs-lookup"><span data-stu-id="6210e-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="6210e-184">Acciones posibles</span><span class="sxs-lookup"><span data-stu-id="6210e-184">Possible actions</span></span>
* <span data-ttu-id="6210e-185">El cursor se puede representar mediante iconos diferentes para transmitir posibles acciones que puede realizar un holograma, como el escalado o la rotación.</span><span class="sxs-lookup"><span data-stu-id="6210e-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="6210e-186">Agregue solo información adicional sobre el cursor si significa algo al usuario.</span><span class="sxs-lookup"><span data-stu-id="6210e-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="6210e-187">De lo contrario, es posible que los usuarios no perciban los cambios de estado u obtengan una confusión con el cursor.</span><span class="sxs-lookup"><span data-stu-id="6210e-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="6210e-188">Estado de entrada</span><span class="sxs-lookup"><span data-stu-id="6210e-188">Input state</span></span>
* <span data-ttu-id="6210e-189">Podríamos usar el cursor para mostrar el estado de entrada o la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="6210e-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="6210e-190">Por ejemplo, podríamos mostrar un icono que indica al usuario que el sistema ve su estado de mano y que la aplicación sabe que está listo para tomar medidas.</span><span class="sxs-lookup"><span data-stu-id="6210e-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="6210e-191">También podríamos usar el cursor para mostrar a los usuarios que el sistema ha escuchado comandos de voz a través de un Change de color momentáneo</span><span class="sxs-lookup"><span data-stu-id="6210e-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="6210e-192">Los siguientes Estados de cursor se pueden implementar de maneras diferentes.</span><span class="sxs-lookup"><span data-stu-id="6210e-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="6210e-193">Puede implementar estos Estados diferentes modelando el cursor como una máquina de Estados.</span><span class="sxs-lookup"><span data-stu-id="6210e-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="6210e-194">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="6210e-194">For example:</span></span>
    * <span data-ttu-id="6210e-195">Estado de inactividad es donde se muestra el cursor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="6210e-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="6210e-196">El estado listo es cuando se ha detectado la mano del usuario en la posición listo.</span><span class="sxs-lookup"><span data-stu-id="6210e-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="6210e-197">El estado de interacción es cuando el usuario realiza una interacción determinada.</span><span class="sxs-lookup"><span data-stu-id="6210e-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="6210e-198">El estado de las acciones posibles o el estado de desplazamiento es cuando se transmiten las posibles acciones que se pueden realizar en un holograma.</span><span class="sxs-lookup"><span data-stu-id="6210e-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="6210e-199">También puede implementar estos Estados de forma que pueda mostrar distintos recursos artísticos cuando se detecten distintos Estados.</span><span class="sxs-lookup"><span data-stu-id="6210e-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="6210e-200">"Sin cursor"</span><span class="sxs-lookup"><span data-stu-id="6210e-200">Going "cursor-free"</span></span>
<span data-ttu-id="6210e-201">Se recomienda diseñar sin un cursor cuando el sentido de la inmersión es un componente clave de una experiencia y cuando las interacciones que señalan (a través de la mirada y el gesto) no requieren una gran precisión.</span><span class="sxs-lookup"><span data-stu-id="6210e-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="6210e-202">El sistema debe seguir cumpliendo las necesidades que normalmente cumple un cursor al proporcionar a los usuarios comentarios continuos sobre el conocimiento del sistema y ayudarles a comunicar sus intenciones al sistema de forma segura.</span><span class="sxs-lookup"><span data-stu-id="6210e-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="6210e-203">Esto puede ser factible a través de otros cambios de estado perceptibles.</span><span class="sxs-lookup"><span data-stu-id="6210e-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6210e-204">Cursor en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="6210e-204">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="6210e-205">De forma predeterminada, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona un cursor recurso prefabricado ([DefaultCursor. recurso prefabricado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tiene el mismo estado visual que el cursor del sistema del shell.</span><span class="sxs-lookup"><span data-stu-id="6210e-205">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="6210e-206">Se asigna en el perfil de entrada de MRTK, en Punteros.</span><span class="sxs-lookup"><span data-stu-id="6210e-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="6210e-207">Puede reemplazar o personalizar este cursor para su experiencia.</span><span class="sxs-lookup"><span data-stu-id="6210e-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="6210e-208">Para la experiencia con la entrada de seguimiento ocular, MRTK también proporciona EyeGazeCursor que tiene un efecto visual sutil para minimizar la distracción.</span><span class="sxs-lookup"><span data-stu-id="6210e-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="6210e-209">MRTK: perfil de puntero</span><span class="sxs-lookup"><span data-stu-id="6210e-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="6210e-210">MRTK: sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="6210e-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="6210e-211">MRTK: punteros</span><span class="sxs-lookup"><span data-stu-id="6210e-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="6210e-212">Consulta también</span><span class="sxs-lookup"><span data-stu-id="6210e-212">See also</span></span>
* [<span data-ttu-id="6210e-213">Gestos</span><span class="sxs-lookup"><span data-stu-id="6210e-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="6210e-214">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="6210e-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
