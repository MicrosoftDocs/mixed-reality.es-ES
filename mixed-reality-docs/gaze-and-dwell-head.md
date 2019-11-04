---
title: Mirada con la cabeza y permanencia
description: Introducción al modelo de entrada de mirada con la cabeza y permanencia
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, gaze, dwell, interaction, design
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439316"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="a0771-104">Mirada con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="a0771-104">Head-gaze and dwell</span></span>

<span data-ttu-id="a0771-105">Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible.</span><span class="sxs-lookup"><span data-stu-id="a0771-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="a0771-106">Los comandos de voz, al igual que los gestos, pueden ser poco fiables en determinados contextos, por ejemplo en condiciones de ruido excesivamente alto.</span><span class="sxs-lookup"><span data-stu-id="a0771-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="a0771-107">Además, aún no se ha generalizado el uso de la voz para controlar equipos, aunque claramente está ganando popularidad.</span><span class="sxs-lookup"><span data-stu-id="a0771-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="a0771-108">El mecanismo de mirada con la cabeza y permanencia es el más conocido y fácil de dominar para trabajar con visualización frontal y manos libres en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a0771-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="a0771-109">Además, el modelo de mirada con la cabeza y permanencia es completamente fiable, independientemente de las interferencias de ruido o las restricciones de silencio del entorno operativo.</span><span class="sxs-lookup"><span data-stu-id="a0771-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="a0771-110">Escenarios</span><span class="sxs-lookup"><span data-stu-id="a0771-110">Scenarios</span></span>

<span data-ttu-id="a0771-111">En los casos en los que las manos de una persona están ocupados con otras tareas y la voz no es del 100% confiable o disponible debido a las restricciones ambientales o sociales, el uso de la mano y los de la vivienda.</span><span class="sxs-lookup"><span data-stu-id="a0771-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="a0771-112">Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil.</span><span class="sxs-lookup"><span data-stu-id="a0771-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="a0771-113">Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor.</span><span class="sxs-lookup"><span data-stu-id="a0771-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="a0771-114">En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="a0771-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="a0771-115">El encabezado y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="a0771-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="a0771-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a0771-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a0771-117"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="a0771-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="a0771-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a0771-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a0771-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a0771-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a0771-120"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="a0771-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a0771-121">Mirada con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="a0771-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="a0771-122">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="a0771-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a0771-123">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="a0771-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="a0771-124">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="a0771-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="a0771-125">Principios de diseño</span><span class="sxs-lookup"><span data-stu-id="a0771-125">Design principles</span></span>

<span data-ttu-id="a0771-126">**Evite "mirarnos como un arma"**</span><span class="sxs-lookup"><span data-stu-id="a0771-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="a0771-127">El modelo de mirada con la cabeza y permanencia requiere información visual para ser intuitivo, pero demasiada información puede resultar estresante.</span><span class="sxs-lookup"><span data-stu-id="a0771-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="a0771-128">La información debe ayudar al usuario a saber qué está mirando, pero no seleccionar ese elemento automáticamente contra la voluntad del usuario.</span><span class="sxs-lookup"><span data-stu-id="a0771-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="a0771-129">La lectura de texto, iconos y etiquetas requiere una consideración especial para dar tiempo al usuario a absorber la información antes de seleccionar.</span><span class="sxs-lookup"><span data-stu-id="a0771-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="a0771-130">**Velocidad de búsqueda de Goldilocks**</span><span class="sxs-lookup"><span data-stu-id="a0771-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="a0771-131">Las interacciones de permanencia pueden tener distintos temporizadores, en función del impacto de la navegación. Para las funciones frecuentes, suele ser mejor un tiempo de relleno más rápido, mientras que para las funciones relevantes suele resultar mejor un tiempo de relleno más prolongado.</span><span class="sxs-lookup"><span data-stu-id="a0771-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="a0771-132">Si se usa un efecto de relleno para mostrar estos temporizadores, las curvas de animación del color de relleno pueden influir positivamente para transmitir una sensación de tiempo de relleno más rápido.</span><span class="sxs-lookup"><span data-stu-id="a0771-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="a0771-133">Debe prestarse especial atención para permitir al usuario decidir si cambiar a velocidad de relleno rápida, media o lenta.</span><span class="sxs-lookup"><span data-stu-id="a0771-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="a0771-134">**Decir, efecto no-no a yo-yo**</span><span class="sxs-lookup"><span data-stu-id="a0771-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="a0771-135">El efecto yo-yo es un patrón incómodo de movimiento de la cabeza que puede surgir cuando la ubicación del contenido y los controles de mirada con la cabeza y permanencia obligan al usuario a mirar hacia arriba y hacia abajo constantemente.</span><span class="sxs-lookup"><span data-stu-id="a0771-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="a0771-136">Por ejemplo, una lista de navegación con el botón de AvPág y el botón de permanencia en la parte inferior induce un bucle de-mirar a la vivienda, buscar en los resultados, buscar en la vivienda, etc. Este patrón resultante es incómodo y se debe evitar colocando los controles de navegación en una ubicación centralizada que requiere menos y después.</span><span class="sxs-lookup"><span data-stu-id="a0771-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="a0771-137">La ubicación de los botones de permanencia en relación con sus efectos resulta importante para la comodidad.</span><span class="sxs-lookup"><span data-stu-id="a0771-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="a0771-138">Directrices y procedimientos recomendados para la experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="a0771-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="a0771-139">Tamaños de los destinos</span><span class="sxs-lookup"><span data-stu-id="a0771-139">Target sizes</span></span>
  <span data-ttu-id="a0771-140">Para que sea fácilmente accesible, los objetivos de la vista de cabeza y de la vivienda deben ser lo suficientemente grandes como para examinarlos de forma cómoda y mantener el cabezal estable en el destino durante el tiempo previsto.</span><span class="sxs-lookup"><span data-stu-id="a0771-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="a0771-141">Se recomienda un tamaño mínimo de destino de 2 grados para lograr la experiencia más cómoda.</span><span class="sxs-lookup"><span data-stu-id="a0771-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="a0771-142">Comentarios visuales</span><span class="sxs-lookup"><span data-stu-id="a0771-142">Visual feedback</span></span>

<span data-ttu-id="a0771-143">Al utilizar un relleno radial para representar el temporizador de permanencia, empieza desde el centro del botón.</span><span class="sxs-lookup"><span data-stu-id="a0771-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="a0771-144">Una respuesta coherente es menos confusa que si cada botón tiene una dirección distinta.</span><span class="sxs-lookup"><span data-stu-id="a0771-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="a0771-145">No obstante, esta regla puede romperse para las interacciones direccionales (por ejemplo, navegar hacia arriba/abajo/izquierda/derecha, etc.).</span><span class="sxs-lookup"><span data-stu-id="a0771-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="a0771-146">Por ejemplo, Microsoft Dynamics 365 Guides hace una excepción para los botones SIGUIENTE/ATRÁS, que son rellenos de izquierda y derecha.</span><span class="sxs-lookup"><span data-stu-id="a0771-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="a0771-147">Considera la posibilidad de invertir un relleno radial desde fuera, para escenarios como desactivar un botón.</span><span class="sxs-lookup"><span data-stu-id="a0771-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="a0771-148">La sensación inversa a pulsar un botón es un patrón visual que resulta útil mantener.</span><span class="sxs-lookup"><span data-stu-id="a0771-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="a0771-149">Muestra progresiva</span><span class="sxs-lookup"><span data-stu-id="a0771-149">Progressive disclosure</span></span>

<span data-ttu-id="a0771-150">La muestra progresiva significa que solo se muestran los detalles pertinentes en cada etapa de una interacción.</span><span class="sxs-lookup"><span data-stu-id="a0771-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="a0771-151">En el caso de la permanencia, esto significa que el objetivo de permanencia se muestra resaltado (por ejemplo, en un control de lista).</span><span class="sxs-lookup"><span data-stu-id="a0771-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="a0771-152">Objetivos demasiado grandes</span><span class="sxs-lookup"><span data-stu-id="a0771-152">Oversized targets</span></span>
<span data-ttu-id="a0771-153">La región de permanencia puede ser mayor que el icono inactivo para que resulte más fácil de usar, al igual que el botón Atrás en Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="a0771-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="a0771-154">Evitar el parpadeo con información retrasada</span><span class="sxs-lookup"><span data-stu-id="a0771-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="a0771-155">Utiliza un breve retraso antes de iniciar la información visual para evitar el parpadeo cuando un usuario pase sobre un objetivo de permanencia.</span><span class="sxs-lookup"><span data-stu-id="a0771-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="a0771-156">En el caso de los botones INTERACTUADOS con frecuencia, mantenga el retraso muy breve para que la aplicación se sienta reactiva.</span><span class="sxs-lookup"><span data-stu-id="a0771-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="a0771-157">En el caso de los botones que se interactúan con poca frecuencia, un retraso más largo puede ser adecuado para evitar la sensación de interfaz twitchy.</span><span class="sxs-lookup"><span data-stu-id="a0771-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="a0771-158">Patrones de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="a0771-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="a0771-159">Botones de alta frecuencia</span><span class="sxs-lookup"><span data-stu-id="a0771-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a0771-160">Los botones de alta frecuencia son botones que se usan habitualmente en una aplicación.</span><span class="sxs-lookup"><span data-stu-id="a0771-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="a0771-161">Un buen ejemplo son los botones Siguiente y Atrás de Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="a0771-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="a0771-162">**Tenida**</span><span class="sxs-lookup"><span data-stu-id="a0771-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="a0771-163">Los botones de alta frecuencia deben ser grandes y más fáciles de visitar</span><span class="sxs-lookup"><span data-stu-id="a0771-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="a0771-164">Manténgase cerca de la altura para evitar una presión ergonómica.</span><span class="sxs-lookup"><span data-stu-id="a0771-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="a0771-165">*Imagen: botón siguiente de las guías de Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="a0771-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Botón siguiente de las guías de Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="a0771-167">Botones de baja frecuencia</span><span class="sxs-lookup"><span data-stu-id="a0771-167">Low frequency buttons</span></span>
<span data-ttu-id="a0771-168">Los botones de baja frecuencia son aquellos que no se accionan en la aplicación con demasiada frecuencia.</span><span class="sxs-lookup"><span data-stu-id="a0771-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="a0771-169">Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.</span><span class="sxs-lookup"><span data-stu-id="a0771-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="a0771-170">Intenta mantener estos botones apartados de las rutas frecuentes de la mirada con la cabeza para evitar activarlos accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="a0771-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="a0771-171">Confirmaciones</span><span class="sxs-lookup"><span data-stu-id="a0771-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a0771-172">Cuando una acción tiene un impacto significativo, como cobrar dinero, eliminar trabajo o iniciar un proceso largo, resulta útil confirmar que el usuario realmente quiere seleccionar ese botón.</span><span class="sxs-lookup"><span data-stu-id="a0771-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="a0771-173">**Tenida**</span><span class="sxs-lookup"><span data-stu-id="a0771-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="a0771-174">Muestra el resaltado de la selección en el botón principal.</span><span class="sxs-lookup"><span data-stu-id="a0771-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="a0771-175">Muestra el objetivo de permanencia al mismo tiempo que el resaltado de selección.</span><span class="sxs-lookup"><span data-stu-id="a0771-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="a0771-176">Para el botón secundario, muestra el objetivo de permanencia al mirar con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="a0771-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="a0771-177">*Imagen: cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="a0771-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="a0771-179">Botones de alternancia</span><span class="sxs-lookup"><span data-stu-id="a0771-179">Toggle buttons</span></span>
<span data-ttu-id="a0771-180">Los botones de alternancia requieren una lógica matizada para que funcionen correctamente.</span><span class="sxs-lookup"><span data-stu-id="a0771-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="a0771-181">Cuando una persona permanece sobre un botón de alternancia y lo activa, debe salir del botón y, a continuación, volver para reiniciar la lógica de permanencia.</span><span class="sxs-lookup"><span data-stu-id="a0771-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="a0771-182">Es importante que se distinga claramente el estado activo del inactivo de los botones de alternancia.</span><span class="sxs-lookup"><span data-stu-id="a0771-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="a0771-183">Vistas de lista</span><span class="sxs-lookup"><span data-stu-id="a0771-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="a0771-184">Las vistas de lista presentan un desafío determinado para la entrada de encabezado y de continuación.</span><span class="sxs-lookup"><span data-stu-id="a0771-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="a0771-185">Los usuarios deben poder recorrer el contenido sin la sensación de tener que ir pasando de puntillas por los distintos objetivos de permanencia.</span><span class="sxs-lookup"><span data-stu-id="a0771-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="a0771-186">**Tenida**</span><span class="sxs-lookup"><span data-stu-id="a0771-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="a0771-187">Hacer que la fila completa se resalte cuando se mira por la cabeza, pero no comienza la permanencia, a menos que la punta de la mirada esté en el destino de vivienda específico.</span><span class="sxs-lookup"><span data-stu-id="a0771-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="a0771-188">Muestre solo el destino de permanencia cuando la fila esté resaltada para reducir el ruido visual.</span><span class="sxs-lookup"><span data-stu-id="a0771-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="a0771-189">Ser claros y coherentes con la posición de los objetivos de la vivienda.</span><span class="sxs-lookup"><span data-stu-id="a0771-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="a0771-190">No muestre todos los destinos de permanencia a la vez para evitar la interfaz de usuario repetida.</span><span class="sxs-lookup"><span data-stu-id="a0771-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="a0771-191">Vuelva a usar el mismo patrón tantas veces como sea posible para establecer la familiaridad con la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="a0771-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="a0771-192">*Imagen: lista de guías de Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="a0771-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Lista de guías de Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="a0771-194">Consulta también</span><span class="sxs-lookup"><span data-stu-id="a0771-194">See also</span></span>
* [<span data-ttu-id="a0771-195">Miras y confirmaciones</span><span class="sxs-lookup"><span data-stu-id="a0771-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a0771-196">Manipulación práctica directa</span><span class="sxs-lookup"><span data-stu-id="a0771-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a0771-197">Gestos prácticos</span><span class="sxs-lookup"><span data-stu-id="a0771-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="a0771-198">Manos y confirmación</span><span class="sxs-lookup"><span data-stu-id="a0771-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="a0771-199">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="a0771-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="a0771-200">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="a0771-200">Voice input</span></span>](voice-input.md)
