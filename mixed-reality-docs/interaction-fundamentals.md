---
title: Aspectos básicos de interacción
description: Como hemos creado las experiencias en HoloLens (gen 1), 2 de HoloLens e inmersivos, hemos iniciado anotar algunas cosas que se han encontrado útiles para compartir.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Diseño de interacción, la realidad mixta
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597548"
---
# <a name="interaction-fundamentals"></a><span data-ttu-id="a978a-104">Aspectos básicos de interacción</span><span class="sxs-lookup"><span data-stu-id="a978a-104">Interaction fundamentals</span></span>

<span data-ttu-id="a978a-105">Como hemos creado las experiencias en HoloLens e inmersivos, comenzamos anotar algunas cosas que se han encontrado útiles para compartir.</span><span class="sxs-lookup"><span data-stu-id="a978a-105">As we've built experiences across HoloLens and immersive headsets, we've started writing down some things we found useful to share.</span></span> <span data-ttu-id="a978a-106">Piense en estos elementos como los bloques constitutivos fundamentales para el diseño de interacción de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a978a-106">Think of these as the fundamental building blocks for mixed reality interaction design.</span></span>

## <a name="device-support"></a><span data-ttu-id="a978a-107">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a978a-107">Device support</span></span>

<span data-ttu-id="a978a-108">Aquí tiene un resumen de los artículos de diseño de interacción disponibles y qué tipo de dispositivo o tipos que se aplican a.</span><span class="sxs-lookup"><span data-stu-id="a978a-108">Here's an outline of the available Interaction design articles and which device type or types they apply to.</span></span>
<br>

<table>

<th>
<tr>

<td style="width:150px;"><span data-ttu-id="a978a-109"><strong>entrada</strong></span><span class="sxs-lookup"><span data-stu-id="a978a-109"><strong>Input</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="a978a-110"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a978a-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="a978a-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a978a-111"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="a978a-112"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="a978a-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
 
<tr>
<td> <span data-ttu-id="a978a-113"><a href="gestures.md">Manos articuladas</a></span><span class="sxs-lookup"><span data-stu-id="a978a-113"><a href="gestures.md">Articulated hands</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="a978a-114">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-114">✔️</span></span></td><td></td>

</tr><tr>
<td> <span data-ttu-id="a978a-115"><a href="gaze-targeting.md">Destinatarios de ojo</a></span><span class="sxs-lookup"><span data-stu-id="a978a-115"><a href="gaze-targeting.md">Eye targeting</a></span></span></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="a978a-116">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-116">✔️</span></span></td><td style="text-align: center;"></td>
</tr><tr>
<td> <span data-ttu-id="a978a-117"><a href="gaze-targeting.md">Mirada destinadas a</a></span><span class="sxs-lookup"><span data-stu-id="a978a-117"><a href="gaze-targeting.md">Gaze targeting</a></span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-118">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-118">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-119">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-119">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-120">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-120">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a978a-121"><a href="gestures.md">Gestos</a></span><span class="sxs-lookup"><span data-stu-id="a978a-121"><a href="gestures.md">Gestures</a></span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-122">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-122">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-123">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="a978a-124"><a href="voice-design.md">Diseño de voz</a></span><span class="sxs-lookup"><span data-stu-id="a978a-124"><a href="voice-design.md">Voice design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-125">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-125">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-126">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-126">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-127">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-127">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a978a-128">Controlador para juegos</span><span class="sxs-lookup"><span data-stu-id="a978a-128">Gamepad</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-129">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-129">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-130">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-130">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-131">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-131">✔️</span></span></td>
</tr>
<tr>
<td> <span data-ttu-id="a978a-132"><a href="motion-controllers.md">Controladores de movimiento</a></span><span class="sxs-lookup"><span data-stu-id="a978a-132"><a href="motion-controllers.md">Motion controllers</a></span></span></td><td></td><td style="text-align: center;"></td><td style="text-align: center;"><span data-ttu-id="a978a-133">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-133">✔️</span></span></td>

</tr>
<th>
<tr>
<td style="width:150px;"><span data-ttu-id="a978a-134"><strong>Percepción y las características espaciales</strong></span><span class="sxs-lookup"><span data-stu-id="a978a-134"><strong>Perception and spatial features</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="a978a-135"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a978a-135"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="a978a-136"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a978a-136"><strong>HoloLens 2</strong></span></span></td>
<td style="width:150px; text-align: center;"><span data-ttu-id="a978a-137"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="a978a-137"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
</th>
<tr>

<td> <span data-ttu-id="a978a-138"><a href="spatial-sound-design.md">Diseño espacial de sonido</a></span><span class="sxs-lookup"><span data-stu-id="a978a-138"><a href="spatial-sound-design.md">Spatial sound design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-139">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-139">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-140">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-140">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-141">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-141">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="a978a-142"><a href="spatial-mapping-design.md">Diseño de la asignación espacial</a></span><span class="sxs-lookup"><span data-stu-id="a978a-142"><a href="spatial-mapping-design.md">Spatial mapping design</a></span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-143">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-143">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-144">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-144">✔️</span></span></td><td></td>
</tr><tr>
<td> <span data-ttu-id="a978a-145"><a href="hologram.md">Hologramas</a></span><span class="sxs-lookup"><span data-stu-id="a978a-145"><a href="hologram.md">Holograms</a></span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-146">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-146">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="a978a-147">✔️</span><span class="sxs-lookup"><span data-stu-id="a978a-147">✔️</span></span></td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a><span data-ttu-id="a978a-148">El usuario es la cámara</span><span class="sxs-lookup"><span data-stu-id="a978a-148">The user is the camera</span></span>

![Usuario es la cámara](images/useriscamera-640px.jpg)

<span data-ttu-id="a978a-150">Piense sobre el diseño para el punto de vista de los usuarios siempre cuando pasen sobre sus ámbitos reales y virtuales.</span><span class="sxs-lookup"><span data-stu-id="a978a-150">Always think about design for your user's point of view as they move about their real and virtual worlds.</span></span>

<span data-ttu-id="a978a-151">**Algunas preguntas que debe hacer**</span><span class="sxs-lookup"><span data-stu-id="a978a-151">**Some questions to ask**</span></span>
* <span data-ttu-id="a978a-152">¿Es el usuario la oportunidad de sentarse, reclinables, permanente o caminar al usar su experiencia?</span><span class="sxs-lookup"><span data-stu-id="a978a-152">Is the user sitting, reclining, standing, or walking while using your experience?</span></span>
* <span data-ttu-id="a978a-153">¿Cómo se ajustar su contenido en diferentes posiciones?</span><span class="sxs-lookup"><span data-stu-id="a978a-153">How does your content adjust to different positions?</span></span>
* <span data-ttu-id="a978a-154">¿El usuario puede ajustarlo?</span><span class="sxs-lookup"><span data-stu-id="a978a-154">Can the user adjust it?</span></span>
* <span data-ttu-id="a978a-155">¿El usuario estará familiarizado con el uso de la aplicación?</span><span class="sxs-lookup"><span data-stu-id="a978a-155">Will the user be comfortable using your app?</span></span>

<span data-ttu-id="a978a-156">**Procedimientos recomendados**</span><span class="sxs-lookup"><span data-stu-id="a978a-156">**Best practices**</span></span>
* <span data-ttu-id="a978a-157">El usuario es la cámara y controlan el movimiento.</span><span class="sxs-lookup"><span data-stu-id="a978a-157">The user is the camera and they control the movement.</span></span> <span data-ttu-id="a978a-158">Deje que su unidad.</span><span class="sxs-lookup"><span data-stu-id="a978a-158">Let them drive.</span></span>
* <span data-ttu-id="a978a-159">Si tiene que transportar prácticamente el usuario, ser sensibles a los problemas en torno a vestibular molestias.</span><span class="sxs-lookup"><span data-stu-id="a978a-159">If you need to virtually transport the user, be sensitive to issues around vestibular discomfort.</span></span>
* <span data-ttu-id="a978a-160">Usar animaciones más cortas</span><span class="sxs-lookup"><span data-stu-id="a978a-160">Use shorter animations</span></span>
* <span data-ttu-id="a978a-161">Animar desde abajo, izquierda y derecha o Fundido de entrada en lugar de Z</span><span class="sxs-lookup"><span data-stu-id="a978a-161">Animate from down/left/right or fade in instead of Z</span></span>
* <span data-ttu-id="a978a-162">Ralentizar el tiempo</span><span class="sxs-lookup"><span data-stu-id="a978a-162">Slow down timing</span></span>
* <span data-ttu-id="a978a-163">Permitir al usuario ver el mundo en segundo plano</span><span class="sxs-lookup"><span data-stu-id="a978a-163">Allow user to see the world in the background</span></span>

<span data-ttu-id="a978a-164">**Lo que debe evitar**</span><span class="sxs-lookup"><span data-stu-id="a978a-164">**What to avoid**</span></span>
* <span data-ttu-id="a978a-165">No agite la cámara o deliberadamente bloquearla en 3DOF (sólo orientación, ninguna traducción), puede hacer que los usuarios sienten incómodos.</span><span class="sxs-lookup"><span data-stu-id="a978a-165">Don't shake the camera or purposely lock it to 3DOF (only orientation, no translation), it can make users feel uncomfortable.</span></span>
* <span data-ttu-id="a978a-166">Ningún movimiento abrupta.</span><span class="sxs-lookup"><span data-stu-id="a978a-166">No abrupt movement.</span></span> <span data-ttu-id="a978a-167">Si tiene que poner el contenido a o desde el usuario, muévalo lentamente y sin problemas hacia ellos para obtener la máxima comodidad.</span><span class="sxs-lookup"><span data-stu-id="a978a-167">If you need to bring content to or from the user, move it slowly and smoothly toward them for maximum comfort.</span></span> <span data-ttu-id="a978a-168">Los usuarios reaccionará a menús grandes estará disponible en ellos.</span><span class="sxs-lookup"><span data-stu-id="a978a-168">Users will react to large menus coming at them.</span></span>
* <span data-ttu-id="a978a-169">No acelerar o activar la cámara del usuario.</span><span class="sxs-lookup"><span data-stu-id="a978a-169">Don't accelerate or turn the user's camera.</span></span> <span data-ttu-id="a978a-170">Los usuarios son sensibles a la aceleración (angular y traslación).</span><span class="sxs-lookup"><span data-stu-id="a978a-170">Users are sensitive to acceleration (both angular and translational).</span></span>

## <a name="leverage-the-users-perspective"></a><span data-ttu-id="a978a-171">Aproveche la perspectiva del usuario</span><span class="sxs-lookup"><span data-stu-id="a978a-171">Leverage the user's perspective</span></span>

<span data-ttu-id="a978a-172">Los usuarios ver el mundo de la realidad mixta a través de la muestra en los dispositivos envolventes y holográficas.</span><span class="sxs-lookup"><span data-stu-id="a978a-172">Users see the world of mixed reality through displays on immersive and holographic devices.</span></span> <span data-ttu-id="a978a-173">En el HoloLens, se llama a esta pantalla el [marco holográfica](holographic-frame.md).</span><span class="sxs-lookup"><span data-stu-id="a978a-173">On the HoloLens, this display is called the [holographic frame](holographic-frame.md).</span></span>

<span data-ttu-id="a978a-174">En el desarrollo 2D, se puede colocar contenido a los que accede con frecuencia y la configuración en las esquinas de una pantalla para hacerlos fácilmente accesibles.</span><span class="sxs-lookup"><span data-stu-id="a978a-174">In 2D development, frequently accessed content and settings may be placed in the corners of a screen to make them easily accessible.</span></span> <span data-ttu-id="a978a-175">Sin embargo, en aplicaciones holográficas, puede ser incómodo para tener acceso a contenido en las esquinas de la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="a978a-175">However, in holographic apps, content in the corners of the user's view may be uncomfortable to access.</span></span> <span data-ttu-id="a978a-176">En este caso, el centro del marco holográfico es la ubicación principal para el contenido.</span><span class="sxs-lookup"><span data-stu-id="a978a-176">In this case, the center of the holographic frame is the prime location for content.</span></span>

<span data-ttu-id="a978a-177">El usuario deba ser guiada por perfiles para ayudar a localizar los eventos importantes u objetos más allá de su vista inmediata.</span><span class="sxs-lookup"><span data-stu-id="a978a-177">The user may need to be guided to help locate important events or objects beyond their immediate view.</span></span> <span data-ttu-id="a978a-178">Puede usar flechas, seguimientos de luz, movimiento carácter, bocadillos, punteros, sonido espacial y los mensajes de voz para ayudar a guiar al usuario al contenido importante en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a978a-178">You can use arrows, light trails, character head movement, thought bubbles, pointers, spatial sound, and voice prompts to help guide the user to important content in your app.</span></span>

<span data-ttu-id="a978a-179">Se recomienda no bloquear contenido en la pantalla para mayor comodidad del usuario.</span><span class="sxs-lookup"><span data-stu-id="a978a-179">It is recommended to not lock content to the screen for the user's comfort.</span></span> <span data-ttu-id="a978a-180">Si tiene que conservar el contenido de la vista, colóquelo en el mundo y hacer que el contenido "tag-along" como el menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="a978a-180">If you need to keep content in view, place it in the world and make the content "tag-along" like the Start menu.</span></span> <span data-ttu-id="a978a-181">Se sentirá más natural en el entorno de contenido que se extrae junto con la perspectiva del usuario.</span><span class="sxs-lookup"><span data-stu-id="a978a-181">Content that gets pulled along with the user's perspective will feel more natural in the environment.</span></span>

<span data-ttu-id="a978a-182">![El menú inicio sigue a la vista del usuario cuando se alcanza el borde del marco](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a978a-182">![The start menu follows the user's view when it reaches the edge of the frame](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="a978a-183">*El menú inicio sigue a la vista del usuario cuando se alcanza el borde del marco*</span><span class="sxs-lookup"><span data-stu-id="a978a-183">*The Start menu follows the user's view when it reaches the edge of the frame*</span></span>

<span data-ttu-id="a978a-184">En HoloLens, hologramas sentirse real cuando ya que no se recorten caben dentro del marco holográfico.</span><span class="sxs-lookup"><span data-stu-id="a978a-184">On HoloLens, holograms feel real when they fit within the holographic frame since they don't get cut off.</span></span> <span data-ttu-id="a978a-185">Los usuarios se moverán para ver los límites de un holograma dentro del marco.</span><span class="sxs-lookup"><span data-stu-id="a978a-185">Users will move in order to see the bounds of a hologram within the frame.</span></span> <span data-ttu-id="a978a-186">En HoloLens, es importante simplificar la interfaz de usuario para ajustarse a la vista del usuario y mantiene el foco en la acción principal.</span><span class="sxs-lookup"><span data-stu-id="a978a-186">On HoloLens, it's important to simplify your UI to fit within the user's view and keep your focus on the main action.</span></span> <span data-ttu-id="a978a-187">Para inmersivos, es importante mantener la ilusión de un mundo virtual persistente dentro campo de la vista del dispositivo en el.</span><span class="sxs-lookup"><span data-stu-id="a978a-187">For immersive headsets, it's important to maintain the illusion of a persistent virtual world within the device's field of view.</span></span>

## <a name="user-comfort"></a><span data-ttu-id="a978a-188">Comodidad del usuario</span><span class="sxs-lookup"><span data-stu-id="a978a-188">User comfort</span></span>

<span data-ttu-id="a978a-189">Para garantizar el máximo [confort](comfort.md) en pantallas montada head, es importante para los diseñadores y desarrolladores a crear y presentar el contenido de forma que se asemeje a cómo los seres humanos interpretan las formas 3D y la posición relativa de los objetos en natural mundo.</span><span class="sxs-lookup"><span data-stu-id="a978a-189">To ensure maximum [comfort](comfort.md) on head-mounted displays, it’s important for designers and developers to create and present content in a way that mimics how humans interpret 3D shapes and the relative position of objects in the natural world.</span></span> <span data-ttu-id="a978a-190">Desde una perspectiva física, también es importante diseñar el contenido que no requiera la fatiga de los movimientos del cuello o armas.</span><span class="sxs-lookup"><span data-stu-id="a978a-190">From a physical perspective, it is also important to design content that does not require fatiguing motions of the neck or arms.</span></span>

<span data-ttu-id="a978a-191">Si el desarrollo para HoloLens o inmersivos, es importante representar objetos visuales para ambos ojos.</span><span class="sxs-lookup"><span data-stu-id="a978a-191">Whether developing for HoloLens or immersive headsets, it is important to render visuals for both eyes.</span></span> <span data-ttu-id="a978a-192">Representación de una pantalla informativa en un ojo solo puede realizar una interfaz difíciles de entender, así como causando uneasiness al ojo y el cerebro del usuario.</span><span class="sxs-lookup"><span data-stu-id="a978a-192">Rendering a heads-up display in one eye only can make an interface hard to understand, as well as causing uneasiness to the user's eye and brain.</span></span>

## <a name="share-your-experience"></a><span data-ttu-id="a978a-193">Comparta su experiencia</span><span class="sxs-lookup"><span data-stu-id="a978a-193">Share your experience</span></span>

<span data-ttu-id="a978a-194">Uso de [mixto captura realidad](mixed-reality-capture.md), los usuarios pueden capturar fotos o vídeos de su experiencia en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="a978a-194">Using [mixed reality capture](mixed-reality-capture.md), users can capture a photo or video of their experience at any time.</span></span> <span data-ttu-id="a978a-195">Considere la posibilidad de experiencias en la aplicación donde que desea animar a las instantáneas o los vídeos.</span><span class="sxs-lookup"><span data-stu-id="a978a-195">Consider experiences in your app where you may want to encourage snapshots or videos.</span></span>

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a><span data-ttu-id="a978a-196">Aproveche los elementos básicos de la interfaz de usuario de Windows Mixed Reality principal</span><span class="sxs-lookup"><span data-stu-id="a978a-196">Leverage basic UI elements of the Windows Mixed Reality home</span></span>

<span data-ttu-id="a978a-197">Al igual que la experiencia de PC de Windows se inicia con el escritorio, Windows Mixed Reality comienza con la página principal.</span><span class="sxs-lookup"><span data-stu-id="a978a-197">Just like the Windows PC experience starts with the desktop, Windows Mixed Reality starts with the home.</span></span> <span data-ttu-id="a978a-198">El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) aprovecha nuestra capacidad para comprender y navegar por los lugares 3D innata.</span><span class="sxs-lookup"><span data-stu-id="a978a-198">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) leverages our innate ability to understand and navigate 3D places.</span></span> <span data-ttu-id="a978a-199">Con HoloLens, su casa es el espacio físico.</span><span class="sxs-lookup"><span data-stu-id="a978a-199">With HoloLens, your home is your physical space.</span></span> <span data-ttu-id="a978a-200">Con inmersivos, su casa es un espacio virtual.</span><span class="sxs-lookup"><span data-stu-id="a978a-200">With immersive headsets, your home is a virtual place.</span></span>

<span data-ttu-id="a978a-201">Su casa es también donde usará el menú Inicio para abrir y colocar las aplicaciones y el contenido.</span><span class="sxs-lookup"><span data-stu-id="a978a-201">Your home is also where you’ll use the Start menu to open and place apps and content.</span></span> <span data-ttu-id="a978a-202">Puede rellenar su hogar con contenido de realidad mixta y realizar varias tareas mediante el uso de varias aplicaciones al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="a978a-202">You can fill your home with mixed reality content and multitask by using multiple apps at the same time.</span></span> <span data-ttu-id="a978a-203">Las cosas que se coloca en su hogar permanecen allí, incluso si reinicia el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a978a-203">The things you place in your home stay there, even if you restart your device.</span></span>

## <a name="see-also"></a><span data-ttu-id="a978a-204">Vea también</span><span class="sxs-lookup"><span data-stu-id="a978a-204">See also</span></span>
* [<span data-ttu-id="a978a-205">Mirada destinadas a</span><span class="sxs-lookup"><span data-stu-id="a978a-205">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="a978a-206">Gestos</span><span class="sxs-lookup"><span data-stu-id="a978a-206">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a978a-207">Diseño de voz</span><span class="sxs-lookup"><span data-stu-id="a978a-207">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="a978a-208">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="a978a-208">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="a978a-209">Diseño espacial de sonido</span><span class="sxs-lookup"><span data-stu-id="a978a-209">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="a978a-210">Diseño de la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="a978a-210">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="a978a-211">Comodidad</span><span class="sxs-lookup"><span data-stu-id="a978a-211">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="a978a-212">Navegar por el inicio de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a978a-212">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
