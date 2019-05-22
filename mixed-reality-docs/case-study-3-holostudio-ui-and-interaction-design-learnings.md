---
title: 'Caso práctico: HoloStudio 3 interfaz de usuario y la interacción de diseño aprendizajes'
description: HoloStudio UI y conocimientos de diseño de interacción
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Windows HoloLens, HoloStudio, la realidad mixta
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974829"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="8ec06-104">Caso práctico: HoloStudio 3 interfaz de usuario y la interacción de diseño aprendizajes</span><span class="sxs-lookup"><span data-stu-id="8ec06-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="8ec06-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) era una de las primeras aplicaciones de Microsoft para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ec06-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="8ec06-106">Por este motivo, tuvimos que crear nuevas y mejores prácticas para 3D de la interfaz de usuario y el diseño de interacción.</span><span class="sxs-lookup"><span data-stu-id="8ec06-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="8ec06-107">Esto es lo hicimos a través de una gran cantidad de pruebas de usuario, creación de prototipos y pruebas y errores.</span><span class="sxs-lookup"><span data-stu-id="8ec06-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="8ec06-108">Sabemos que no todo el mundo tiene los recursos a su disposición para realizar este tipo de investigación, por lo que teníamos nuestra diseñador holográfica senior, Marcus Ghaly, compartir tres cosas aprendimos durante el desarrollo de HoloStudio sobre el diseño de interfaz de usuario y la interacción para aplicaciones de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8ec06-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="8ec06-109">Vea el vídeo</span><span class="sxs-lookup"><span data-stu-id="8ec06-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="8ec06-110">Problema #1: Las personas no deseaba mover sus creaciones</span><span class="sxs-lookup"><span data-stu-id="8ec06-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="8ec06-111">Se diseñó originalmente en HoloStudio workbench como un rectángulo, mucho que encontrará en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="8ec06-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="8ec06-112">El problema es que las personas tienen una duración de la experiencia que les indica que permanezca aún cuando están sentados en una mesa o trabajar frente a un equipo, por lo que no estaban moverse por el área de trabajo y explorar su creación en 3D desde todos los lados.</span><span class="sxs-lookup"><span data-stu-id="8ec06-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![El diseño rectangular de workbench en HoloStudio dissuaded a los usuarios mover y ver sus creaciones de todos los lados.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="8ec06-114">Teníamos los conocimientos para hacer que workbench redondear, por lo que se ha producido ninguna "delante" o borrar el lugar al que se suponía que debía independiente.</span><span class="sxs-lookup"><span data-stu-id="8ec06-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="8ec06-115">Cuando lo probamos, repentinamente personas a mover y explorar sus creaciones en sus propios.</span><span class="sxs-lookup"><span data-stu-id="8ec06-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![El diseño de workbench circular aconseja a los usuarios recorrer todo sentido sus creaciones.](images/circular-workbench-500px.jpg)

<span data-ttu-id="8ec06-117">**¿Qué hemos aprendido**</span><span class="sxs-lookup"><span data-stu-id="8ec06-117">**What we learned**</span></span>

<span data-ttu-id="8ec06-118">Siempre se puede pensar en lo que es cómodo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="8ec06-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="8ec06-119">Sacar provecho de su espacio físico es una interesante característica de HoloLens y algo que no se puede hacer con otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8ec06-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="8ec06-120">Problema #2: Los cuadros de diálogo modales a veces están fuera del marco holográfico</span><span class="sxs-lookup"><span data-stu-id="8ec06-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="8ec06-121">A veces, el usuario puede buscar en una dirección diferente de lo que necesita su atención en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8ec06-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="8ec06-122">En un equipo, que puede simplemente la ventana emergente de seguridad de un cuadro de diálogo, pero si lo hace en la cara de una persona en un entorno 3D, puede sentir como si el cuadro de diálogo se está metiendo su manera.</span><span class="sxs-lookup"><span data-stu-id="8ec06-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="8ec06-123">Debe leer el mensaje, pero su instinto es intentar obtener fuera de él.</span><span class="sxs-lookup"><span data-stu-id="8ec06-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="8ec06-124">Esta reacción es fantástica si juega un juego, pero en una herramienta diseñada para el trabajo, es ideal.</span><span class="sxs-lookup"><span data-stu-id="8ec06-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="8ec06-125">Después de probar algunas cosas diferentes, finalmente se liquidan sobre el uso de un sistema de "pensé burbuja" para nuestro cuadros de diálogo y agregan tendrils que los usuarios pueden seguir para que sea necesaria su atención en nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="8ec06-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="8ec06-126">También hemos realizado el pulso tendrils, lo que suponía una sensación de direccionalidad para que los usuarios supieran dónde debe ir.</span><span class="sxs-lookup"><span data-stu-id="8ec06-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![El sistema "Pensé burbuja" incluye parpadeante tendrils que proporciona una idea de dirección, dando lugar a los usuarios a que se necesita su atención en la aplicación.](images/thought-bubble-500px.jpg)

<span data-ttu-id="8ec06-128">**¿Qué hemos aprendido**</span><span class="sxs-lookup"><span data-stu-id="8ec06-128">**What we learned**</span></span>

<span data-ttu-id="8ec06-129">Es mucho más difícil en 3D alertar a los usuarios lo que necesitan prestar atención a.</span><span class="sxs-lookup"><span data-stu-id="8ec06-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="8ec06-130">Con los directores de atención como [sonido espacial](spatial-sound.md), rayos con poca o burbujas de pensamiento, puede dar lugar a los usuarios a donde deben estar.</span><span class="sxs-lookup"><span data-stu-id="8ec06-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="8ec06-131">Problema #3: A veces, la interfaz de usuario puede bloquearse por otros hologramas</span><span class="sxs-lookup"><span data-stu-id="8ec06-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="8ec06-132">Hay veces cuando un usuario desea interactuar con un holograma y sus controles de interfaz de usuario asociadas, pero están bloqueados en la vista porque otro holograma está delante de ellas.</span><span class="sxs-lookup"><span data-stu-id="8ec06-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="8ec06-133">Mientras estábamos desarrollando HoloStudio, hemos usado la prueba y error para llegar a una solución para esto.</span><span class="sxs-lookup"><span data-stu-id="8ec06-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Un control de interfaz de usuario asociado con un holograma puede quedarse bloqueado si hay otro holograma entre ella y el usuario gastando de HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="8ec06-135">Se ha intentado mover el control de interfaz de usuario más cercano al usuario, por lo que no se pudo obtener bloqueada, pero se encontró que no le bastaba con el usuario examina un control que se ha producido cerca al mirar simultáneamente un holograma que era muy lejos.</span><span class="sxs-lookup"><span data-stu-id="8ec06-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="8ec06-136">Si, sin embargo, se mueve el control delante el holograma más cercano al usuario, sentía como se separó del holograma debe estar afectando a.</span><span class="sxs-lookup"><span data-stu-id="8ec06-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="8ec06-137">Por último terminé fantasma el control de interfaz de usuario y colocarlo en la misma distancia desde el usuario como el holograma que está asociado, por lo que ambos se sienten conectados.</span><span class="sxs-lookup"><span data-stu-id="8ec06-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="8ec06-138">Esto permite al usuario interactuar con el control, aunque se ha está oculto.</span><span class="sxs-lookup"><span data-stu-id="8ec06-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![La solución: se reflejó el control de interfaz de usuario, que permite la interacción con el control y llegó a sentirse está conectado a la holograma lo estaba afectando a.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="8ec06-140">**¿Qué hemos aprendido**</span><span class="sxs-lookup"><span data-stu-id="8ec06-140">**What we learned**</span></span>

<span data-ttu-id="8ec06-141">Los usuarios necesitan poder tener acceso fácilmente a los controles de interfaz de usuario incluso si ha bloqueados, así que descubra métodos para asegurarse de que los usuarios pueden completar sus tareas con independencia de dónde están sus hologramas en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="8ec06-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="8ec06-142">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="8ec06-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="8ec06-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="8ec06-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="8ec06-144">Diseñador holográfico senior @Microsoft</span><span class="sxs-lookup"><span data-stu-id="8ec06-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8ec06-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="8ec06-145">See also</span></span>
* [<span data-ttu-id="8ec06-146">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="8ec06-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
