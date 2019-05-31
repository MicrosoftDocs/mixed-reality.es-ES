---
title: Manos libres
description: Optimizar la aplicación para la configuración manos libres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: La realidad mixta, manos libres, que mirar, mirar como destino, interacción, diseño
ms.openlocfilehash: 23b1def15c4ad900265fab2a2c8757cf96706fbc
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402340"
---
# <a name="hands-free"></a><span data-ttu-id="32eed-104">Manos libres</span><span class="sxs-lookup"><span data-stu-id="32eed-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="32eed-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="32eed-105">Scenarios</span></span>

<span data-ttu-id="32eed-106">Como se describe en el [información general del modelo de interacción](interaction-fundamentals.md), una vez identificados los usuarios y sus objetivos, pregúntese qué desafíos del entorno o conocimiento produzcan mientras trabajan para realizar sus tareas.</span><span class="sxs-lookup"><span data-stu-id="32eed-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="32eed-107">Por ejemplo, muchos usuarios necesitan usar las manos y lograr sus objetivos reales tienen dificultades para interactuar con una interfaz basada en las manos y controladores.</span><span class="sxs-lookup"><span data-stu-id="32eed-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="32eed-108">Podrían ser algunos escenarios concretos:</span><span class="sxs-lookup"><span data-stu-id="32eed-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="32eed-109">Se le guiará a través de una tarea, mientras que las manos están ocupadas</span><span class="sxs-lookup"><span data-stu-id="32eed-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="32eed-110">Hacer referencia a materiales mientras están ocupadas sus manos</span><span class="sxs-lookup"><span data-stu-id="32eed-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="32eed-111">Fatiga de la mano</span><span class="sxs-lookup"><span data-stu-id="32eed-111">Hand fatigue</span></span>
* <span data-ttu-id="32eed-112">Guantes que no se puede realizar el seguimiento</span><span class="sxs-lookup"><span data-stu-id="32eed-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="32eed-113">Llevar a algo</span><span class="sxs-lookup"><span data-stu-id="32eed-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="32eed-114">Modalidades de manos libres</span><span class="sxs-lookup"><span data-stu-id="32eed-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="32eed-115">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="32eed-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="32eed-116">Uso de la voz para comando y control de que una interfaz puede no sólo permite al usuario manos libres de funcionar, pero también omitir varios pasos.</span><span class="sxs-lookup"><span data-stu-id="32eed-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="32eed-117">El uso de esta modalidad puede oscilar entre que permite al usuario simplemente leyendo el nombre de cualquier botón en voz alta activarlo, como se muestra en vea-it-say-it, para conversar con un agente que puede realizar las tareas por usted.</span><span class="sxs-lookup"><span data-stu-id="32eed-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="32eed-118">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="32eed-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="32eed-119">En algunas situaciones en las manos libres, uso de la voz no es ideal o posible.</span><span class="sxs-lookup"><span data-stu-id="32eed-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="32eed-120">Entornos de fábrica fuerte, privacidad o normas sociales pueden ser restricciones.</span><span class="sxs-lookup"><span data-stu-id="32eed-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="32eed-121">El encabezado que mirar + profundizaré modelo permite al usuario navegar por la aplicación mediante el uso de su vector principal para que apunte al persistentes, o reposo en un botón se activarán después de una cierta cantidad de tiempo (normalmente aproximadamente 1 segundo o menos).</span><span class="sxs-lookup"><span data-stu-id="32eed-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="32eed-122">Transición dentro y fuera de manos libres</span><span class="sxs-lookup"><span data-stu-id="32eed-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="32eed-123">Para estos escenarios, la liberación de las manos de interactuar con hologramas para navegación y comandos puede ser desde un requisito imprescindible para el funcionamiento de la aplicación,-to-end, para una mayor comodidad en la que el usuario puede realizar dentro y fuera de la transición en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="32eed-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="32eed-124">Si el requisito de la aplicación es que siempre se usará con manos libres, ya sea a través de permanencia, comandos de voz o el comando de voz única, "select", asegúrese de realizar el alojamiento adecuado en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="32eed-124">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="32eed-125">Si el usuario de destino debe ser capaz de cambiar de manos a manos libres a su discreción, es importante tener estos principios en cuenta:</span><span class="sxs-lookup"><span data-stu-id="32eed-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="32eed-126">Suponga que el usuario ya está en el modo en que desea cambiar a</span><span class="sxs-lookup"><span data-stu-id="32eed-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="32eed-127">Por ejemplo, si el usuario está en la fábrica, siguiendo una referencia de vídeo en su Hololens y decide recoger una llave inglesa para empezar a trabajar, más probable es que le gustaría empezar a trabajar en manos libres sin necesidad de dejar la llave inglesa que presionar un botón.</span><span class="sxs-lookup"><span data-stu-id="32eed-127">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="32eed-128">Debería poder llamar a una sesión de voz con un comando de voz, profundizaré en la interfaz de usuario ya visible para comenzar la permanencia o, por ejemplo la palabra "select".</span><span class="sxs-lookup"><span data-stu-id="32eed-128">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="32eed-129">El usuario debe tener la capacidad de:</span><span class="sxs-lookup"><span data-stu-id="32eed-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="32eed-130">Cambiar a manos libres al manos libres</span><span class="sxs-lookup"><span data-stu-id="32eed-130">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="32eed-131">Cambiar a manos con sus manos</span><span class="sxs-lookup"><span data-stu-id="32eed-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="32eed-132">Cambiar al controlador mediante un controlador</span><span class="sxs-lookup"><span data-stu-id="32eed-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="32eed-133">Crear redundancia de maneras de cambiar los modos de</span><span class="sxs-lookup"><span data-stu-id="32eed-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="32eed-134">Aunque el primer principio es acerca del acceso, la segunda es sobre la disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="32eed-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="32eed-135">Simplemente no debe haber una manera de transición dentro y fuera de un modo única.</span><span class="sxs-lookup"><span data-stu-id="32eed-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="32eed-136">Algunos ejemplos serían:</span><span class="sxs-lookup"><span data-stu-id="32eed-136">Some examples would be:</span></span> 
* <span data-ttu-id="32eed-137">Un botón para iniciar interacciones de voz</span><span class="sxs-lookup"><span data-stu-id="32eed-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="32eed-138">Un comando de voz para realizar la transición al uso de mirada + permanencia</span><span class="sxs-lookup"><span data-stu-id="32eed-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="32eed-139">Agregar un guión de drama</span><span class="sxs-lookup"><span data-stu-id="32eed-139">Add a dash of drama</span></span>
<span data-ttu-id="32eed-140">Un modificador de modo es un componente indispensable, es importante que cuando se producen estas transiciones, que sean un modificador explícito, incluso espectacular, para permitir al usuario saber qué ha ocurrido.</span><span class="sxs-lookup"><span data-stu-id="32eed-140">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="32eed-141">Lista de comprobación de facilidad de uso</span><span class="sxs-lookup"><span data-stu-id="32eed-141">Usability checklist</span></span>

<span data-ttu-id="32eed-142">**¿Puede hacer el usuario todo y cualquier otra cosa manos libres, to-end?**</span><span class="sxs-lookup"><span data-stu-id="32eed-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="32eed-143">Cada interactible debe ser accesible con manos libres</span><span class="sxs-lookup"><span data-stu-id="32eed-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="32eed-144">Asegúrese de que hay un reemplazo para todos los gestos personalizados, como el tamaño, colocación, deslizamientos, derivaciones, etcetera.</span><span class="sxs-lookup"><span data-stu-id="32eed-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="32eed-145">Asegúrese de que el usuario tiene control seguro de la presencia de la interfaz de usuario, ubicación, nivel de detalle en todo momento</span><span class="sxs-lookup"><span data-stu-id="32eed-145">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="32eed-146">Introducción de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="32eed-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="32eed-147">Direccionamiento de la interfaz de usuario que está fuera del campo de visión (FOV)</span><span class="sxs-lookup"><span data-stu-id="32eed-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="32eed-148">¿Cuánto tiempo puedo ver, donde cuando</span><span class="sxs-lookup"><span data-stu-id="32eed-148">How much I see, where, when</span></span>

<span data-ttu-id="32eed-149">**¿Son la mecánica de la interacción que se va a impartidos y reforzó de manera regular con la factibilidad derecha?**</span><span class="sxs-lookup"><span data-stu-id="32eed-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="32eed-150">¿¿Entiende el usuario...</span><span class="sxs-lookup"><span data-stu-id="32eed-150">Does the user understand ...</span></span>
* <span data-ttu-id="32eed-151">... ¿Qué modo se encuentran en?</span><span class="sxs-lookup"><span data-stu-id="32eed-151">... What mode they are in?</span></span>
* <span data-ttu-id="32eed-152">... ¿Qué puede hacer en este modo?</span><span class="sxs-lookup"><span data-stu-id="32eed-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="32eed-153">... ¿Qué es el estado actual?</span><span class="sxs-lookup"><span data-stu-id="32eed-153">... What is the current state?</span></span>
* <span data-ttu-id="32eed-154">... ¿Cómo puede realizar la transición fuera?</span><span class="sxs-lookup"><span data-stu-id="32eed-154">... How they can transition out?</span></span>
    
<span data-ttu-id="32eed-155">**¿La interfaz de usuario optimizada para manos libres?**</span><span class="sxs-lookup"><span data-stu-id="32eed-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="32eed-156">P. ej.</span><span class="sxs-lookup"><span data-stu-id="32eed-156">Ex.</span></span> <span data-ttu-id="32eed-157">Prestaciones de permanencia no están integradas en los patrones típicos de 2D</span><span class="sxs-lookup"><span data-stu-id="32eed-157">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="32eed-158">P. ej.</span><span class="sxs-lookup"><span data-stu-id="32eed-158">Ex.</span></span> <span data-ttu-id="32eed-159">Destinatarios de voz están mejor con el objeto resaltado</span><span class="sxs-lookup"><span data-stu-id="32eed-159">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="32eed-160">P. ej.</span><span class="sxs-lookup"><span data-stu-id="32eed-160">Ex.</span></span> <span data-ttu-id="32eed-161">Interacciones de voz son mejores con subtítulos que tienen que estar activado</span><span class="sxs-lookup"><span data-stu-id="32eed-161">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="32eed-162">Vea también</span><span class="sxs-lookup"><span data-stu-id="32eed-162">See also</span></span>
* [<span data-ttu-id="32eed-163">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="32eed-163">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="32eed-164">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="32eed-164">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="32eed-165">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="32eed-165">Point and commit with hands</span></span>](point-and-commit.md)
