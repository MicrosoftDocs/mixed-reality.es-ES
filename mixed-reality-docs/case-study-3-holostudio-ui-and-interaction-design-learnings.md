---
title: 'Caso práctico: 3 aprendizajes del diseño de la interfaz de usuario e interacción de HoloStudio'
description: Aprendizaje de la interfaz de usuario y diseño de interacción de HoloStudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974829"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="81d32-104">Caso práctico: 3 aprendizajes del diseño de la interfaz de usuario e interacción de HoloStudio</span><span class="sxs-lookup"><span data-stu-id="81d32-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="81d32-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) era una de las primeras aplicaciones de Microsoft para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="81d32-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="81d32-106">Por este motivo, teníamos que crear nuevas prácticas recomendadas para la interfaz de usuario y el diseño de interacción 3D.</span><span class="sxs-lookup"><span data-stu-id="81d32-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="81d32-107">Hicimos esto a través de una gran cantidad de pruebas de usuario, prototipos y errores.</span><span class="sxs-lookup"><span data-stu-id="81d32-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="81d32-108">Sabemos que no todos los usuarios tienen los recursos a su disposición para realizar este tipo de investigación, por lo que teníamos nuestro diseñador Sr. Holographic, Marcus Ghaly, compartimos tres cosas que hemos aprendido durante el desarrollo de HoloStudio sobre la interfaz de usuario y el diseño de interacción para aplicaciones de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="81d32-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="81d32-109">Ver el vídeo</span><span class="sxs-lookup"><span data-stu-id="81d32-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="81d32-110">Problema #1: Las personas no quieren desplazarse por sus creaciones</span><span class="sxs-lookup"><span data-stu-id="81d32-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="81d32-111">Originalmente diseñamos el Workbench en HoloStudio como un rectángulo, de forma muy similar a lo que encontraría en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="81d32-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="81d32-112">El problema es que las personas tienen una duración de experiencia que les indica que permanezcan cuando se encuentren en un escritorio o trabajen frente a un equipo, por lo que no se mueven por Workbench y exploran su creación en 3D desde todos los lados.</span><span class="sxs-lookup"><span data-stu-id="81d32-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![El diseño rectangular de Workbench en HoloStudio dissuaded que los usuarios desplazan y vean sus creaciones desde todos los lados.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="81d32-114">Teníamos la información para que el área de trabajo se redondee, de modo que no haya ningún "anverso" o claro que se supone que se debe.</span><span class="sxs-lookup"><span data-stu-id="81d32-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="81d32-115">Cuando lo probamos, las personas empezaron a desplazarse y explorar sus creaciones por su cuenta.</span><span class="sxs-lookup"><span data-stu-id="81d32-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![El diseño circular de Workbench anima a los usuarios a recorrer todo el proceso en torno a su creación.](images/circular-workbench-500px.jpg)

<span data-ttu-id="81d32-117">**Lo que hemos aprendido**</span><span class="sxs-lookup"><span data-stu-id="81d32-117">**What we learned**</span></span>

<span data-ttu-id="81d32-118">Siempre debe pensar en lo que se siente cómodo para el usuario.</span><span class="sxs-lookup"><span data-stu-id="81d32-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="81d32-119">Sacar partido de su espacio físico es una característica interesante de HoloLens y algo que no se puede hacer con otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="81d32-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="81d32-120">Problema #2: A veces, los cuadros de diálogo modales están fuera del marco holográfica</span><span class="sxs-lookup"><span data-stu-id="81d32-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="81d32-121">En ocasiones, es posible que el usuario esté buscando en una dirección diferente de algo que necesite su atención en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="81d32-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="81d32-122">En un equipo, puede simplemente mostrar un cuadro de diálogo, pero si lo hace en la superficie de alguien en un entorno 3D, puede parecer que el cuadro de diálogo se está obteniendo.</span><span class="sxs-lookup"><span data-stu-id="81d32-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="81d32-123">Los necesita para leer el mensaje, pero su instinto es intentar salir de él.</span><span class="sxs-lookup"><span data-stu-id="81d32-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="81d32-124">Esta reacción es excelente si juega un juego, pero en una herramienta diseñada para el trabajo, es menos que lo ideal.</span><span class="sxs-lookup"><span data-stu-id="81d32-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="81d32-125">Una vez que se han intentado algunas cosas diferentes, finalmente se ha liquidado el uso de un sistema de "burbuja de pensamiento" para nuestros cuadros de diálogo y se ha agregado tendrils que los usuarios pueden seguir a donde se requiere su atención en nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="81d32-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="81d32-126">También hemos realizado el pulso de tendrils, que implícitamente es una sensación de direccionalidad para que los usuarios supieran adónde ir.</span><span class="sxs-lookup"><span data-stu-id="81d32-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![El sistema de "pensamiento de pensamiento" incluía tendrils que ofrecían una sensación de dirección, los usuarios a los que se necesitaba su atención en la aplicación.](images/thought-bubble-500px.jpg)

<span data-ttu-id="81d32-128">**Lo que hemos aprendido**</span><span class="sxs-lookup"><span data-stu-id="81d32-128">**What we learned**</span></span>

<span data-ttu-id="81d32-129">Es mucho más difícil en 3D avisar a los usuarios de las cosas que necesitan prestar atención.</span><span class="sxs-lookup"><span data-stu-id="81d32-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="81d32-130">El uso de directores de atención, como [sonido espacial](spatial-sound.md), rayos claros o burbujas de pensamiento, puede conducir a los usuarios a dónde deben ser.</span><span class="sxs-lookup"><span data-stu-id="81d32-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="81d32-131">Problema #3: A veces, otros hologramas pueden bloquear la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="81d32-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="81d32-132">Hay veces en las que un usuario desea interactuar con un holograma y sus controles de interfaz de usuario asociados, pero se bloquea en la vista porque otro holograma está delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="81d32-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="81d32-133">Durante el desarrollo de HoloStudio, hemos usado la prueba y el error para obtener una solución.</span><span class="sxs-lookup"><span data-stu-id="81d32-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Un control de interfaz de usuario asociado a un holograma puede quedar bloqueado si hay otro holograma entre él y el usuario que contenga HoloLens.](images/ui-blocked-500px.jpg)

<span data-ttu-id="81d32-135">Se intentó desplazar el control de la interfaz de usuario para que no se pudiera bloquear, pero se encontró que no estaba familiarizado con el usuario de ver un control que estaba cerca de usted mientras examinaba simultáneamente un holograma que estaba lejos.</span><span class="sxs-lookup"><span data-stu-id="81d32-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="81d32-136">Sin embargo, si se mueve el control delante del holograma más cercano al usuario, parecía que se separó del holograma que debería estar afectando.</span><span class="sxs-lookup"><span data-stu-id="81d32-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="81d32-137">Finalmente, terminamos con fantasma el control de IU y lo colocamos a la misma distancia del usuario que el holograma al que está asociado, por lo que ambos se sienten conectados.</span><span class="sxs-lookup"><span data-stu-id="81d32-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="81d32-138">Esto permite al usuario interactuar con el control aunque esté oculto.</span><span class="sxs-lookup"><span data-stu-id="81d32-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![La solución: hemos convertido en fantasma el control de interfaz de usuario, que permitía la interacción con el control y lo hicieron conectados al holograma al que estaba afectando.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="81d32-140">**Lo que hemos aprendido**</span><span class="sxs-lookup"><span data-stu-id="81d32-140">**What we learned**</span></span>

<span data-ttu-id="81d32-141">Los usuarios deben poder acceder fácilmente a los controles de interfaz de usuario incluso si se han bloqueado, por lo que debe averiguar los métodos para asegurarse de que los usuarios puedan completar sus tareas independientemente de dónde se encuentren sus hologramas en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="81d32-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="81d32-142">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="81d32-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="81d32-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="81d32-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="81d32-144">Diseñador de Sr. Holographic@Microsoft</span><span class="sxs-lookup"><span data-stu-id="81d32-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="81d32-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="81d32-145">See also</span></span>
* [<span data-ttu-id="81d32-146">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="81d32-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
