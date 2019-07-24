---
title: Manos libres
description: Optimización de la aplicación para manos libres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidad mixta, manos libres, miradas por mirados, interacción, diseño
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414394"
---
# <a name="hands-free"></a><span data-ttu-id="60d35-104">Manos libres</span><span class="sxs-lookup"><span data-stu-id="60d35-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="60d35-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="60d35-105">Scenarios</span></span>

<span data-ttu-id="60d35-106">Como se describe en [información general sobre el modelo de interacción](interaction-fundamentals.md), una vez que haya identificado los usuarios y sus objetivos, pregúntese qué desafíos ambientales o de situaciones pueden enfrentarse a medida que trabajan para llevar a cabo sus tareas.</span><span class="sxs-lookup"><span data-stu-id="60d35-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="60d35-107">Por ejemplo, muchos usuarios necesitan usar sus manos para lograr sus objetivos del mundo real y tendrán dificultades para interactuar con una interfaz basada en manos y controladores.</span><span class="sxs-lookup"><span data-stu-id="60d35-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="60d35-108">Algunos escenarios específicos pueden ser:</span><span class="sxs-lookup"><span data-stu-id="60d35-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="60d35-109">Se le guiará a través de una tarea, mientras que las manos están ocupadas.</span><span class="sxs-lookup"><span data-stu-id="60d35-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="60d35-110">Referencia a materiales mientras sus manos están ocupados</span><span class="sxs-lookup"><span data-stu-id="60d35-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="60d35-111">Fatiga manual</span><span class="sxs-lookup"><span data-stu-id="60d35-111">Hand fatigue</span></span>
* <span data-ttu-id="60d35-112">Guantes en los que no se puede realizar un seguimiento</span><span class="sxs-lookup"><span data-stu-id="60d35-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="60d35-113">Llevar algo</span><span class="sxs-lookup"><span data-stu-id="60d35-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="60d35-114">Modalidades de manos libres</span><span class="sxs-lookup"><span data-stu-id="60d35-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="60d35-115">Comandos de voz</span><span class="sxs-lookup"><span data-stu-id="60d35-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="60d35-116">El uso de la voz para el comando y el control de una interfaz no solo permite al usuario operar Handsfree, sino que también puede omitir varios pasos.</span><span class="sxs-lookup"><span data-stu-id="60d35-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="60d35-117">El uso de esta modalidad puede abarcar desde permitir al usuario simplemente leer el nombre de cualquier botón en voz alta para activarlo, como en el caso de "ver-ti", para conversar con un agente que puede realizar tareas por usted.</span><span class="sxs-lookup"><span data-stu-id="60d35-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="60d35-118">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="60d35-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="60d35-119">En algunas situaciones sin experiencia, el uso de la voz no es lo ideal o incluso posible.</span><span class="sxs-lookup"><span data-stu-id="60d35-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="60d35-120">Los entornos de fábrica, la privacidad o las normas sociales de alta carga pueden ser restricciones.</span><span class="sxs-lookup"><span data-stu-id="60d35-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="60d35-121">El modelo de miras y de la vivienda permite al usuario navegar por la aplicación mediante el vector de encabezado para apuntar, mientras que la permanencia o la vivienda en un botón, se activará después de un período de tiempo determinado, normalmente aproximadamente en un segundo.</span><span class="sxs-lookup"><span data-stu-id="60d35-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="60d35-122">Transición dentro y fuera de manos libres</span><span class="sxs-lookup"><span data-stu-id="60d35-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="60d35-123">En estos casos, la liberación de las manos de la interacción con los hologramas para la navegación y los comandos puede abarcar de ser un requisito absoluto para el funcionamiento de la aplicación, de un extremo a otro, a una mayor comodidad en la que el usuario puede realizar la transición en cualquier tiempo.</span><span class="sxs-lookup"><span data-stu-id="60d35-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="60d35-124">Si el requisito de la aplicación es que siempre se usará de forma gratuita, ya sea mediante la permanencia, comandos de voz o el único comando de voz, "seleccionar", asegúrese de hacer las adaptaciones adecuadas en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="60d35-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="60d35-125">Si el usuario de destino debe ser capaz de cambiar de manos libres a su discreción, es importante tener en cuenta los siguientes principios.</span><span class="sxs-lookup"><span data-stu-id="60d35-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="60d35-126">Supongamos que el usuario ya está en el modo al que desea cambiar</span><span class="sxs-lookup"><span data-stu-id="60d35-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="60d35-127">Por ejemplo, si el usuario está en la fábrica, viendo una referencia de vídeo en su Hololens y decide tomar una llave para empezar a trabajar, lo más probable es que empiece a trabajar en Handsfree sin tener que dejar la llave inglesa para presionar un botón.</span><span class="sxs-lookup"><span data-stu-id="60d35-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="60d35-128">Debe ser capaz de invocar una sesión de voz con un comando de voz, hospedar en una interfaz de usuario ya visible para comenzar la permanencia o decir la palabra "seleccionar".</span><span class="sxs-lookup"><span data-stu-id="60d35-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="60d35-129">El usuario debe tener la capacidad de:</span><span class="sxs-lookup"><span data-stu-id="60d35-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="60d35-130">Cambiar a manos libres sin manos libres</span><span class="sxs-lookup"><span data-stu-id="60d35-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="60d35-131">Cambiar a manos con las manos</span><span class="sxs-lookup"><span data-stu-id="60d35-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="60d35-132">Cambiar al controlador mediante un controlador</span><span class="sxs-lookup"><span data-stu-id="60d35-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="60d35-133">Crear formas redundantes de cambiar de modo</span><span class="sxs-lookup"><span data-stu-id="60d35-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="60d35-134">Aunque el primer principio es acerca del acceso, el segundo es acerca de la disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="60d35-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="60d35-135">No debe haber una única manera de pasar de un modo a otro.</span><span class="sxs-lookup"><span data-stu-id="60d35-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="60d35-136">Algunos ejemplos serían:</span><span class="sxs-lookup"><span data-stu-id="60d35-136">Some examples would be:</span></span> 
* <span data-ttu-id="60d35-137">Un botón para iniciar las interacciones de voz</span><span class="sxs-lookup"><span data-stu-id="60d35-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="60d35-138">Un comando de voz para realizar la transición al uso de fijamente + viviendas</span><span class="sxs-lookup"><span data-stu-id="60d35-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="60d35-139">Agregar un guion de series</span><span class="sxs-lookup"><span data-stu-id="60d35-139">Add a dash of drama</span></span>
<span data-ttu-id="60d35-140">Un modificador de modo es un gran negocio, es importante que cuando estas transiciones sucedan que son un conmutador explícito, incluso drástico, para que el usuario sepa lo que ha sucedido.</span><span class="sxs-lookup"><span data-stu-id="60d35-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="60d35-141">Lista de comprobación de usabilidad</span><span class="sxs-lookup"><span data-stu-id="60d35-141">Usability checklist</span></span>

<span data-ttu-id="60d35-142">**¿Puede el usuario hacer todo lo posible y todo lo que sea gratuito?**</span><span class="sxs-lookup"><span data-stu-id="60d35-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="60d35-143">Cada interactúable debe ser accesible sin complicaciones</span><span class="sxs-lookup"><span data-stu-id="60d35-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="60d35-144">Asegúrese de que hay un reemplazo para todos los gestos personalizados, como el cambio de tamaño, la colocación, los deslizamientos, los grifos, etc.</span><span class="sxs-lookup"><span data-stu-id="60d35-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="60d35-145">Asegúrese de que el usuario tiene el control seguro de la presencia de la interfaz de usuario, la ubicación y el nivel de detalle en todo momento.</span><span class="sxs-lookup"><span data-stu-id="60d35-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="60d35-146">Sacar la interfaz de usuario del camino</span><span class="sxs-lookup"><span data-stu-id="60d35-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="60d35-147">Interfaz de usuario de direccionamiento fuera del campo de vista (campo de campo)</span><span class="sxs-lookup"><span data-stu-id="60d35-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="60d35-148">¿Cuánto veo, dónde?</span><span class="sxs-lookup"><span data-stu-id="60d35-148">How much I see, where, when</span></span>

<span data-ttu-id="60d35-149">**¿La mecánica de la interacción se enseña y se refuerza con las prestaciones adecuadas?**</span><span class="sxs-lookup"><span data-stu-id="60d35-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="60d35-150">¿Entiende el usuario...</span><span class="sxs-lookup"><span data-stu-id="60d35-150">Does the user understand ...</span></span>
* <span data-ttu-id="60d35-151">... ¿En qué modo se encuentran?</span><span class="sxs-lookup"><span data-stu-id="60d35-151">... What mode they are in?</span></span>
* <span data-ttu-id="60d35-152">... ¿Qué pueden hacer en este modo?</span><span class="sxs-lookup"><span data-stu-id="60d35-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="60d35-153">... ¿Cuál es el estado actual?</span><span class="sxs-lookup"><span data-stu-id="60d35-153">... What is the current state?</span></span>
* <span data-ttu-id="60d35-154">... ¿Cómo pueden realizar la transición?</span><span class="sxs-lookup"><span data-stu-id="60d35-154">... How they can transition out?</span></span>
    
<span data-ttu-id="60d35-155">**¿La interfaz de usuario está optimizada para manos libres?**</span><span class="sxs-lookup"><span data-stu-id="60d35-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="60d35-156">Ejemplo: Las prestaciones de permanencia no están integradas en los patrones 2D típicos</span><span class="sxs-lookup"><span data-stu-id="60d35-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="60d35-157">Ejemplo: El destino de la voz es mejor con el resaltado de objetos</span><span class="sxs-lookup"><span data-stu-id="60d35-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="60d35-158">Ejemplo: Las interacciones de voz son mejores con títulos que se deben activar</span><span class="sxs-lookup"><span data-stu-id="60d35-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="60d35-159">Vea también</span><span class="sxs-lookup"><span data-stu-id="60d35-159">See also</span></span>
* [<span data-ttu-id="60d35-160">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="60d35-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="60d35-161">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="60d35-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="60d35-162">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="60d35-162">Point and commit with hands</span></span>](point-and-commit.md)
