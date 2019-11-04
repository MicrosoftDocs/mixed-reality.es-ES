---
title: Mirada con la cabeza y confirmación
description: Introducción al modelo de entrada de mirada con la cabeza y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, gaze, gaze targeting, interaction, design
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441091"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="bc2f9-104">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="bc2f9-104">Head-gaze and commit</span></span>
<span data-ttu-id="bc2f9-105">_Encabezado y confirmación_ es un caso especial del modelo de entrada de [mira y de confirmación](gaze-and-commit.md) que implica el destino de un objeto con la dirección del encabezado hacia delante (dirección del encabezado) y, a continuación, la actuación con una entrada secundaria, como el movimiento de la mano. Pulse o el comando de voz "seleccionar".</span><span class="sxs-lookup"><span data-stu-id="bc2f9-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="bc2f9-106">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="bc2f9-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bc2f9-107"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="bc2f9-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="bc2f9-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="bc2f9-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="bc2f9-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="bc2f9-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="bc2f9-110"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="bc2f9-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bc2f9-111">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="bc2f9-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="bc2f9-112">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="bc2f9-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="bc2f9-113">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="bc2f9-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="bc2f9-114">➕ Opción alternativa</span><span class="sxs-lookup"><span data-stu-id="bc2f9-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="bc2f9-115">Ajuste de tamaño del destino y comentarios</span><span class="sxs-lookup"><span data-stu-id="bc2f9-115">Target sizing and feedback</span></span>
<span data-ttu-id="bc2f9-116">El vector de miras hacia abajo se ha mostrado varias veces para que se pueda usar para lograr objetivos más precisos, pero a menudo funciona mejor para la segmentación bruta: adquisición de destinos algo más grandes.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="bc2f9-117">Los tamaños mínimos de destino de 1 a 1,5 grados permiten acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados a menudo permiten una mayor velocidad.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="bc2f9-118">Tenga en cuenta que el tamaño que el usuario establece como destino es realmente un área 2D incluso para los elementos 3D (cualquier proyección de ellos debe ser un área potencial de destino).</span><span class="sxs-lookup"><span data-stu-id="bc2f9-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="bc2f9-119">Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es muy útil.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="bc2f9-120">Esto puede incluir tratamientos como efectos visibles de "mantener el mouse", resaltados de audio o clics o alineación clara de un cursor con un elemento.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="bc2f9-121">![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc2f9-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="bc2f9-122">*Tamaño de objetivo óptimo a una distancia de 2 metros*</span><span class="sxs-lookup"><span data-stu-id="bc2f9-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="bc2f9-123">![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc2f9-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="bc2f9-124">*Ejemplo de resaltado de un objeto establecido como destino de la mirada*</span><span class="sxs-lookup"><span data-stu-id="bc2f9-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="bc2f9-125">Situación del destino</span><span class="sxs-lookup"><span data-stu-id="bc2f9-125">Target placement</span></span>
<span data-ttu-id="bc2f9-126">A menudo, los usuarios no pueden encontrar los elementos de la interfaz de usuario que están colocados muy altos o muy bajos en su campo de vista, centrándose en la mayor parte de su atención en áreas en torno a su enfoque principal, que es aproximadamente en el nivel de ojo.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="bc2f9-127">Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="bc2f9-128">Dada la tendencia de los usuarios de centrarse en un área visual relativamente pequeña en todo momento (el cono de atención de la visión es de 10 grados aproximadamente), agrupar los elementos de la interfaz de usuario según su relación conceptual puede producir comportamientos de llamada de atención de un elemento a otro, ya que un usuario mueve su mirada dentro de un área.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="bc2f9-129">Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="bc2f9-130">![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="bc2f9-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="bc2f9-131">*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="bc2f9-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="bc2f9-132">Mejora de los comportamientos de establecimiento de destino</span><span class="sxs-lookup"><span data-stu-id="bc2f9-132">Improving targeting behaviors</span></span>
<span data-ttu-id="bc2f9-133">Si la intención del usuario de destinar algo puede determinarse (o aproximarse de cerca), puede resultar muy útil aceptar los intentos de pérdida en la interacción como si estuviesen dirigidos correctamente.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="bc2f9-134">Estos son algunos de los métodos correctos que se pueden incorporar en experiencias de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="bc2f9-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="bc2f9-135">Estabilización de la mirada con la cabeza ("pozos de gravedad")</span><span class="sxs-lookup"><span data-stu-id="bc2f9-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="bc2f9-136">Esto se debe activar la mayoría o la totalidad del tiempo.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="bc2f9-137">Esta técnica elimina las vibraciones de cabeza natural y cuello que los usuarios podrían tener como movimiento debido a comportamientos de mirar y hablar.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="bc2f9-138">Algoritmos de vínculo más cercano</span><span class="sxs-lookup"><span data-stu-id="bc2f9-138">Closest link algorithms</span></span>
<span data-ttu-id="bc2f9-139">Funcionan mejor en áreas con un contenido interactivo disperso.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="bc2f9-140">Si hay una probabilidad alta de que pueda determinar con qué un usuario estaba intentando interactuar, puede complementar sus capacidades de destino suponiendo cierto nivel de intento.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="bc2f9-141">Acciones de la</span><span class="sxs-lookup"><span data-stu-id="bc2f9-141">Backdating and postdating actions</span></span>
<span data-ttu-id="bc2f9-142">Este mecanismo es útil en las tareas que requieren velocidad.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="bc2f9-143">Cuando un usuario pasa por una serie de maniobras de destino y activación a velocidad, resulta útil asumir algún intento y permitir que los pasos perdidos actúen en los destinos en los que el usuario tenía el foco ligeramente antes o ligeramente después de la pulsación (50 ms antes/después era efectiva en EA pruebas de RLY).</span><span class="sxs-lookup"><span data-stu-id="bc2f9-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="bc2f9-144">Suavizado</span><span class="sxs-lookup"><span data-stu-id="bc2f9-144">Smoothing</span></span>
<span data-ttu-id="bc2f9-145">Este mecanismo es útil para los movimientos de las acciones, lo que reduce la ligera vibración y Wobble debido a las características de movimiento de cabeza natural.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="bc2f9-146">Al suavizar los movimientos de las acciones, smoothándose por el tamaño y la distancia de los movimientos en lugar de a lo largo del tiempo.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="bc2f9-147">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="bc2f9-147">Magnetism</span></span>
<span data-ttu-id="bc2f9-148">Este mecanismo puede considerarse como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar hitboxes, ya sea visible o no, a medida que los usuarios se aproximan a los objetivos probables mediante el uso de algún conocimiento del diseño interactivo para mejorar enfoque del intento del usuario.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="bc2f9-149">Esto puede resultar especialmente eficaz para destinos pequeños.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="bc2f9-150">Permanencia del foco</span><span class="sxs-lookup"><span data-stu-id="bc2f9-150">Focus stickiness</span></span>
<span data-ttu-id="bc2f9-151">Al determinar los elementos interactivos cercanos en los que se va a dar el foco, el ajuste de enfoque proporciona una inclinación al elemento que está enfocado actualmente.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="bc2f9-152">Esto ayuda a reducir los comportamientos de cambio de foco errático al flotar en un punto medio entre dos elementos con ruido natural.</span><span class="sxs-lookup"><span data-stu-id="bc2f9-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="bc2f9-153">Consulta también</span><span class="sxs-lookup"><span data-stu-id="bc2f9-153">See also</span></span>
* [<span data-ttu-id="bc2f9-154">Interacción basada en ojos</span><span class="sxs-lookup"><span data-stu-id="bc2f9-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="bc2f9-155">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="bc2f9-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="bc2f9-156">Manipulación práctica directa</span><span class="sxs-lookup"><span data-stu-id="bc2f9-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="bc2f9-157">Gestos prácticos</span><span class="sxs-lookup"><span data-stu-id="bc2f9-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="bc2f9-158">Manos y confirmación</span><span class="sxs-lookup"><span data-stu-id="bc2f9-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="bc2f9-159">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="bc2f9-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="bc2f9-160">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="bc2f9-160">Voice input</span></span>](voice-input.md)



