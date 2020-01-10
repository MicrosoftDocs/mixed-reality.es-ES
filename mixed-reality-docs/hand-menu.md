---
title: Menú de la mano
description: Los menús de mano permiten a los usuarios poner en marcha rápidamente la interfaz de usuario asociada a las funciones de uso frecuente. Estos son los procedimientos recomendados y las recomendaciones para los menús de la mano.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menú, botón, acceso rápido, diseño
ms.openlocfilehash: c0e1800be69a15706e17f40b1601fc79d05e5d75
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723264"
---
# <a name="hand-menu"></a><span data-ttu-id="15910-105">Menú de la mano</span><span class="sxs-lookup"><span data-stu-id="15910-105">Hand menu</span></span>

![Ubicación del lado de ulnar](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="15910-107">Los menús de mano permiten a los usuarios poner en marcha rápidamente la interfaz de usuario asociada a las funciones de uso frecuente.</span><span class="sxs-lookup"><span data-stu-id="15910-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="15910-108">A continuación se muestran los procedimientos recomendados para los menús de la mano.</span><span class="sxs-lookup"><span data-stu-id="15910-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="15910-109">También puede encontrar una escena de ejemplo en la que se muestra el menú de la mano en [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span><span class="sxs-lookup"><span data-stu-id="15910-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="15910-110">Prácticas recomendadas de comportamiento</span><span class="sxs-lookup"><span data-stu-id="15910-110">Behavior best practices</span></span>
<span data-ttu-id="15910-111">**A. mantener el número de botones pequeños:** debido a la distancia de cierre entre un menú bloqueado a mano y los ojos, y también la tendencia del usuario a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de visión es aproximadamente de 10 grados), se recomienda mantener el número de botones pequeños.</span><span class="sxs-lookup"><span data-stu-id="15910-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="15910-112">En función de la exploración, una columna con tres botones funciona bien manteniendo todo el contenido dentro del campo de vista (campo de contenido) incluso cuando los usuarios mueven sus manos al centro del campo de campo.</span><span class="sxs-lookup"><span data-stu-id="15910-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="15910-113">**B. usar el menú de la mano para una acción rápida:** la elevación de un brazo y el mantenimiento de la posición pueden provocar una fatiga ARM.</span><span class="sxs-lookup"><span data-stu-id="15910-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="15910-114">Use un método bloqueado manualmente para el menú que requiera una breve interacción.</span><span class="sxs-lookup"><span data-stu-id="15910-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="15910-115">Si el menú es complejo y requiere tiempos de interacción extendidos, considere la posibilidad de usar en su lugar el uso de bloqueos internacionales o del cuerpo.</span><span class="sxs-lookup"><span data-stu-id="15910-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="15910-116">**C. botón/ángulo del panel:** los menús deben encabezarse hacia el hombro opuesto y el centro del cabezal: Esto permite que un movimiento de mano natural interactúe con el menú con la mano opuesta y evite las posiciones de mano extrañas o inconvenientes al tocar botones.</span><span class="sxs-lookup"><span data-stu-id="15910-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="15910-117">**D. considere la posibilidad de admitir operaciones Monodireccionales o gratuitas:** no asuma que las dos manos del usuario están siempre disponibles.</span><span class="sxs-lookup"><span data-stu-id="15910-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="15910-118">Tenga en cuenta una amplia gama de contextos cuando una o ambas manecillas no estén disponibles y asegúrese de que su diseño tiene en cuenta esas situaciones.</span><span class="sxs-lookup"><span data-stu-id="15910-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="15910-119">Para admitir un menú de una mano, puede intentar realizar la transición de la ubicación del menú desde el bloque bloqueado a un mundo bloqueado cuando la mano se voltee (se desplace hacia abajo).</span><span class="sxs-lookup"><span data-stu-id="15910-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="15910-120">En escenarios gratuitos, considere la posibilidad de usar un comando de voz para invocar los botones de menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="15910-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="15910-121">**E. invocación en dos pasos:** si usa solo Palm como un evento para desencadenar el menú de la mano, puede aparecer accidentalmente cuando no lo necesite (falsos positivos), ya que los usuarios mueven las manos de forma intencionada (para la comunicación y la manipulación de objetos) y de manera no intencionada.</span><span class="sxs-lookup"><span data-stu-id="15910-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="15910-122">Si experimenta falsos positivos en la aplicación, considere la posibilidad de agregar un paso adicional además del evento de mano para invocar el menú de la mano, como los dedos completamente abiertos.</span><span class="sxs-lookup"><span data-stu-id="15910-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="15910-123">**F. evitar agregar botones cerca de la muñeca (botón Inicio del sistema):** si los botones del menú mano se colocan demasiado cerca del botón Inicio, puede que se desencadene accidentalmente al interactuar con el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="15910-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="15910-124">**G. test, test, test:** los usuarios tienen cuerpos distintos, con distintos umbrales de comodidad y comodidad, etc. Asegúrese de probar el diseño y obtener comentarios de varias personas.</span><span class="sxs-lookup"><span data-stu-id="15910-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="15910-125">Procedimientos recomendados de selección de ubicación de menús</span><span class="sxs-lookup"><span data-stu-id="15910-125">Hand menu placement best practices</span></span>

<span data-ttu-id="15910-126">En la anatomía humana, el ulnar Nerve es un Nerve que se ejecuta cerca del hueso de Ulna.</span><span class="sxs-lookup"><span data-stu-id="15910-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="15910-127">Ulna es un hueso largo que se encuentra en el Forearm que se estira desde el codo hasta el dedo más pequeño.</span><span class="sxs-lookup"><span data-stu-id="15910-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="15910-128">A continuación se muestran dos ubicaciones recomendadas basadas en nuestras exploraciones:</span><span class="sxs-lookup"><span data-stu-id="15910-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="15910-129">![Ubicación del lado ulnar](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="15910-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="15910-130">**A. ulnar en Palm**</span><span class="sxs-lookup"><span data-stu-id="15910-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="15910-131">Esta posición es confiable porque las manos no se superponen entre sí.</span><span class="sxs-lookup"><span data-stu-id="15910-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="15910-132">Esto es fundamental para la detección y el seguimiento precisos de la mano.</span><span class="sxs-lookup"><span data-stu-id="15910-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15910-133">![Ubicación del lado ulnar](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="15910-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="15910-134">**B. ulnar por encima de la mano**</span><span class="sxs-lookup"><span data-stu-id="15910-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="15910-135">Esta ubicación es cómoda para los usuarios porque no necesitan aumentar demasiado el brazo para interactuar con el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="15910-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="15910-136">Se recomienda colocar los menús **13cm** sobre la palma y alinear los botones dentro de la palma de ulnar.</span><span class="sxs-lookup"><span data-stu-id="15910-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="15910-137">Obtenga más información sobre el tamaño óptimo del botón</span><span class="sxs-lookup"><span data-stu-id="15910-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="15910-138">Por motivos técnicos, recomendamos esta ubicación con una implementación necesaria: el desarrollador deberá inmovilizar el menú cuando la mano del usuario se acerque a la interacción con él.</span><span class="sxs-lookup"><span data-stu-id="15910-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="15910-139">Esto evitará la vibración de las manos superpuestas y también permite un destino más rápido de los botones.</span><span class="sxs-lookup"><span data-stu-id="15910-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="15910-140">Las cámaras de HoloLens 2 identifican las manos con precisión cuando son independientes entre sí.</span><span class="sxs-lookup"><span data-stu-id="15910-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="15910-141">Las manos superpuestas pueden provocar que los menús de la mano se alejen de la ubicación del delimitador.</span><span class="sxs-lookup"><span data-stu-id="15910-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="15910-142">Posiciones de menú no recomendadas</span><span class="sxs-lookup"><span data-stu-id="15910-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="15910-143">Hemos realizado una investigación de usuario con distintos diseños y ubicaciones de menús; **no se recomiendan**las siguientes ubicaciones de menú:</span><span class="sxs-lookup"><span data-stu-id="15910-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="15910-144">![sobre ARM](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="15910-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="15910-145">**Por encima del brazo**</span><span class="sxs-lookup"><span data-stu-id="15910-145">**Above the arm**</span></span><br>
        <span data-ttu-id="15910-146">1-difícil de mantener un buen seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="15910-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="15910-147">2-causa fatiga del usuario debido a una posición no natural</span><span class="sxs-lookup"><span data-stu-id="15910-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15910-148">![sobre los dedos](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="15910-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="15910-149">**Los dedos anteriores**</span><span class="sxs-lookup"><span data-stu-id="15910-149">**Above fingers**</span></span><br>
        <span data-ttu-id="15910-150">fatiga de 1 mano debido a la entrega de la mano durante mucho tiempo</span><span class="sxs-lookup"><span data-stu-id="15910-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="15910-151">2-problemas de seguimiento en el índice y el dedo central</span><span class="sxs-lookup"><span data-stu-id="15910-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="15910-152">![por encima del centro Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="15910-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="15910-153">**Anterior: Palm del centro**</span><span class="sxs-lookup"><span data-stu-id="15910-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="15910-154">1-problemas de seguimiento debidos a manos superpuestas</span><span class="sxs-lookup"><span data-stu-id="15910-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="15910-155">fatiga de 2 a mano debido a la conservación de las manos durante mucho tiempo para interactuar con los menús</span><span class="sxs-lookup"><span data-stu-id="15910-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15910-156">![primera mano](images/TopFingerTip.gif) **primera mano**</span><span class="sxs-lookup"><span data-stu-id="15910-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="15910-157">1-problemas de seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="15910-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="15910-158">fatiga de 2 manos manteniendo la mano por encima de la postura normal</span><span class="sxs-lookup"><span data-stu-id="15910-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="15910-159">3-problemas al presionar botones con otros dedos por accidente debido a un espacio limitado entre los dedos</span><span class="sxs-lookup"><span data-stu-id="15910-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="15910-160">![parte posterior del brazo](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="15910-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="15910-161">**Parte posterior del brazo**</span><span class="sxs-lookup"><span data-stu-id="15910-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="15910-162">1-puede desencadenar el botón Inicio por accidente</span><span class="sxs-lookup"><span data-stu-id="15910-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="15910-163">2-no es una posición natural o cómoda para los usuarios</span><span class="sxs-lookup"><span data-stu-id="15910-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="15910-164">Menú de la mano en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="15910-164">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="15910-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y escenas de ejemplo para el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="15910-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="15910-166">HandConstraintPalmUp el script de Solver le permite adjuntar fácilmente cualquier objeto a las manos con varias opciones configurables.</span><span class="sxs-lookup"><span data-stu-id="15910-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="15910-167">Menú MRTK con HandConstraint y HandConstraintPalmUp</span><span class="sxs-lookup"><span data-stu-id="15910-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="15910-168">Consulta también</span><span class="sxs-lookup"><span data-stu-id="15910-168">See also</span></span>

* [<span data-ttu-id="15910-169">Cursores</span><span class="sxs-lookup"><span data-stu-id="15910-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="15910-170">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="15910-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="15910-171">Button</span><span class="sxs-lookup"><span data-stu-id="15910-171">Button</span></span>](button.md)
* [<span data-ttu-id="15910-172">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="15910-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="15910-173">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="15910-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="15910-174">Manipulación</span><span class="sxs-lookup"><span data-stu-id="15910-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="15910-175">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="15910-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="15910-176">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="15910-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="15910-177">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="15910-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="15910-178">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="15910-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="15910-179">Teclado</span><span class="sxs-lookup"><span data-stu-id="15910-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="15910-180">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="15910-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="15910-181">Claqueta</span><span class="sxs-lookup"><span data-stu-id="15910-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="15910-182">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="15910-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="15910-183">Sombreador</span><span class="sxs-lookup"><span data-stu-id="15910-183">Shader</span></span>](shader.md)
* [<span data-ttu-id="15910-184">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="15910-184">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="15910-185">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="15910-185">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="15910-186">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="15910-186">Surface magnetism</span></span>](surface-magnetism.md)
