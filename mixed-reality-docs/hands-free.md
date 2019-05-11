---
title: Optimizar la aplicación para la configuración manos libres
description: Optimizar la aplicación para la configuración manos libres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: La realidad mixta, manos libres, que mirar, mirar como destino, interacción, diseño
ms.openlocfilehash: f39a9524831161997b59be6cf89b124fa5b29c78
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524329"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="510a7-104">Optimizar la aplicación para la configuración manos libres</span><span class="sxs-lookup"><span data-stu-id="510a7-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="510a7-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="510a7-105">Scenarios</span></span>

<span data-ttu-id="510a7-106">Como se describe en el [información general del modelo de interacción](interaction-fundamentals.md), una vez identificados los usuarios y sus objetivos, pregúntese qué desafíos del entorno o conocimiento produzcan mientras trabajan para realizar sus tareas.</span><span class="sxs-lookup"><span data-stu-id="510a7-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="510a7-107">Por ejemplo, muchos usuarios necesitan usar las manos y lograr sus objetivos reales tienen dificultades para interactuar con una interfaz basada en las manos y controladores.</span><span class="sxs-lookup"><span data-stu-id="510a7-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="510a7-108">Podrían ser algunos escenarios concretos:</span><span class="sxs-lookup"><span data-stu-id="510a7-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="510a7-109">Se le guiará a través de una tarea, mientras que las manos están ocupadas</span><span class="sxs-lookup"><span data-stu-id="510a7-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="510a7-110">Hacer referencia a materiales mientras están ocupadas sus manos</span><span class="sxs-lookup"><span data-stu-id="510a7-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="510a7-111">Fatiga de la mano</span><span class="sxs-lookup"><span data-stu-id="510a7-111">Hand fatigue</span></span>
* <span data-ttu-id="510a7-112">Guantes que no se puede realizar el seguimiento</span><span class="sxs-lookup"><span data-stu-id="510a7-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="510a7-113">Llevar a algo</span><span class="sxs-lookup"><span data-stu-id="510a7-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="510a7-114">Modalidades de manos libres</span><span class="sxs-lookup"><span data-stu-id="510a7-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="510a7-115">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="510a7-115">Voice commanding</span></span>

<span data-ttu-id="510a7-116">Uso de la voz para comando y control de que una interfaz puede no sólo permite al usuario manos libres de funcionar, pero también omitir varios pasos.</span><span class="sxs-lookup"><span data-stu-id="510a7-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="510a7-117">El uso de esta modalidad puede oscilar entre que permite al usuario simplemente leyendo el nombre de cualquier botón en voz alta activarlo, como se muestra en vea-it-say-it, para conversar con un agente que puede realizar las tareas por usted.</span><span class="sxs-lookup"><span data-stu-id="510a7-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="510a7-118">Diseño de la voz</span><span class="sxs-lookup"><span data-stu-id="510a7-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="510a7-119">Mirada HEAD y permanencia</span><span class="sxs-lookup"><span data-stu-id="510a7-119">Head gaze and dwell</span></span>

<span data-ttu-id="510a7-120">En algunas situaciones en las manos libres, uso de la voz no es ideal o posible.</span><span class="sxs-lookup"><span data-stu-id="510a7-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="510a7-121">Entornos de fábrica fuerte, privacidad o normas sociales pueden ser restricciones.</span><span class="sxs-lookup"><span data-stu-id="510a7-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="510a7-122">El encabezado que mirar + profundizaré modelo permite al usuario navegar por la aplicación mediante el uso de su vector principal para que apunte al persistentes, o reposo en un botón se activarán después de una cierta cantidad de tiempo (normalmente aproximadamente 1 segundo o menos).</span><span class="sxs-lookup"><span data-stu-id="510a7-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="510a7-123">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="510a7-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="510a7-124">Transición dentro y fuera de manos libres</span><span class="sxs-lookup"><span data-stu-id="510a7-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="510a7-125">Para estos escenarios, la liberación de las manos de interactuar con hologramas para navegación y comandos puede ser desde un requisito imprescindible para el funcionamiento de la aplicación,-to-end, para una mayor comodidad en la que el usuario puede realizar dentro y fuera de la transición en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="510a7-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="510a7-126">Si el requisito de la aplicación es que siempre se usará con manos libres, ya sea a través de permanencia, comandos de voz o el comando de voz única, "select", asegúrese de realizar el alojamiento adecuado en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="510a7-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="510a7-127">Si el usuario de destino debe ser capaz de cambiar de manos a manos libres a su discreción, es importante tener estos principios en cuenta:</span><span class="sxs-lookup"><span data-stu-id="510a7-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="510a7-128">Suponga que el usuario ya está en el modo en que desea cambiar a</span><span class="sxs-lookup"><span data-stu-id="510a7-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="510a7-129">Por ejemplo, si el usuario está en la fábrica, siguiendo una referencia de vídeo en su Hololens y decide recoger una llave inglesa para empezar a trabajar, más probable es que le gustaría empezar a trabajar en manos libres sin necesidad de dejar la llave inglesa que presionar un botón.</span><span class="sxs-lookup"><span data-stu-id="510a7-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="510a7-130">Debería poder llamar a una sesión de voz con un comando de voz, profundizaré en la interfaz de usuario ya visible para comenzar la permanencia o, por ejemplo la palabra "select".</span><span class="sxs-lookup"><span data-stu-id="510a7-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="510a7-131">El usuario debe tener la capacidad de:</span><span class="sxs-lookup"><span data-stu-id="510a7-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="510a7-132">Cambiar a manos libres al manos libres</span><span class="sxs-lookup"><span data-stu-id="510a7-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="510a7-133">Cambiar a manos con sus manos</span><span class="sxs-lookup"><span data-stu-id="510a7-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="510a7-134">Cambiar al controlador mediante un controlador</span><span class="sxs-lookup"><span data-stu-id="510a7-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="510a7-135">Crear redundancia de maneras de cambiar los modos de</span><span class="sxs-lookup"><span data-stu-id="510a7-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="510a7-136">Aunque el primer principio es acerca del acceso, la segunda es sobre la disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="510a7-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="510a7-137">Simplemente no debe haber una manera de transición dentro y fuera de un modo única.</span><span class="sxs-lookup"><span data-stu-id="510a7-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="510a7-138">Algunos ejemplos serían:</span><span class="sxs-lookup"><span data-stu-id="510a7-138">Some examples would be:</span></span> 
* <span data-ttu-id="510a7-139">Un botón para iniciar interacciones de voz</span><span class="sxs-lookup"><span data-stu-id="510a7-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="510a7-140">Un comando de voz para realizar la transición al uso de mirada + permanencia</span><span class="sxs-lookup"><span data-stu-id="510a7-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="510a7-141">Agregar un guión de drama</span><span class="sxs-lookup"><span data-stu-id="510a7-141">Add a dash of drama</span></span>
<span data-ttu-id="510a7-142">Un modificador de modo es un componente indispensable, es importante que cuando se producen estas transiciones, que sean un modificador explícito, incluso espectacular, para permitir al usuario saber qué ha ocurrido.</span><span class="sxs-lookup"><span data-stu-id="510a7-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="510a7-143">Lista de comprobación de facilidad de uso</span><span class="sxs-lookup"><span data-stu-id="510a7-143">Usability checklist</span></span>

<span data-ttu-id="510a7-144">**¿Puede hacer el usuario todo y cualquier otra cosa manos libres, to-end?**</span><span class="sxs-lookup"><span data-stu-id="510a7-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="510a7-145">Cada interactible debe ser accesible con manos libres</span><span class="sxs-lookup"><span data-stu-id="510a7-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="510a7-146">Asegúrese de que hay un reemplazo para todos los gestos personalizados, como el tamaño, colocación, deslizamientos, derivaciones, etcetera.</span><span class="sxs-lookup"><span data-stu-id="510a7-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="510a7-147">Asegúrese de que el usuario tiene control seguro de la presencia de la interfaz de usuario, ubicación, nivel de detalle en todo momento</span><span class="sxs-lookup"><span data-stu-id="510a7-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="510a7-148">Introducción de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="510a7-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="510a7-149">Direccionamiento de la interfaz de usuario que está fuera del campo de visión (FOV)</span><span class="sxs-lookup"><span data-stu-id="510a7-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="510a7-150">¿Cuánto tiempo puedo ver, donde cuando</span><span class="sxs-lookup"><span data-stu-id="510a7-150">How much I see, where, when</span></span>

<span data-ttu-id="510a7-151">**¿Son la mecánica de la interacción que se va a impartidos y reforzó de manera regular con la factibilidad derecha?**</span><span class="sxs-lookup"><span data-stu-id="510a7-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="510a7-152">¿¿Entiende el usuario...</span><span class="sxs-lookup"><span data-stu-id="510a7-152">Does the user understand ...</span></span>
* <span data-ttu-id="510a7-153">... ¿Qué modo se encuentran en?</span><span class="sxs-lookup"><span data-stu-id="510a7-153">... What mode they are in?</span></span>
* <span data-ttu-id="510a7-154">... ¿Qué puede hacer en este modo?</span><span class="sxs-lookup"><span data-stu-id="510a7-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="510a7-155">... ¿Qué es el estado actual?</span><span class="sxs-lookup"><span data-stu-id="510a7-155">... What is the current state?</span></span>
* <span data-ttu-id="510a7-156">... ¿Cómo puede realizar la transición fuera?</span><span class="sxs-lookup"><span data-stu-id="510a7-156">... How they can transition out?</span></span>
    
<span data-ttu-id="510a7-157">**¿La interfaz de usuario optimizada para manos libres?**</span><span class="sxs-lookup"><span data-stu-id="510a7-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="510a7-158">P. ej.</span><span class="sxs-lookup"><span data-stu-id="510a7-158">Ex.</span></span> <span data-ttu-id="510a7-159">Prestaciones de permanencia no están integradas en los patrones típicos de 2D</span><span class="sxs-lookup"><span data-stu-id="510a7-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="510a7-160">P. ej.</span><span class="sxs-lookup"><span data-stu-id="510a7-160">Ex.</span></span> <span data-ttu-id="510a7-161">Destinatarios de voz están mejor con el objeto resaltado</span><span class="sxs-lookup"><span data-stu-id="510a7-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="510a7-162">P. ej.</span><span class="sxs-lookup"><span data-stu-id="510a7-162">Ex.</span></span> <span data-ttu-id="510a7-163">Interacciones de voz son mejores con subtítulos que tienen que estar activado</span><span class="sxs-lookup"><span data-stu-id="510a7-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="510a7-164">Vea también</span><span class="sxs-lookup"><span data-stu-id="510a7-164">See also</span></span>
* [<span data-ttu-id="510a7-165">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="510a7-165">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="510a7-166">Manipulación directa</span><span class="sxs-lookup"><span data-stu-id="510a7-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="510a7-167">Señalar y confirmar</span><span class="sxs-lookup"><span data-stu-id="510a7-167">Point and commit</span></span>](point-and-commit.md)
