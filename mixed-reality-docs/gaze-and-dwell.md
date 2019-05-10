---
title: Mirada y permanencia
description: Información general sobre el modelo de entrada de mirada y permanencia
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Diseñar la realidad, mirada, permanencia, interacción, mixta
ms.openlocfilehash: d99180b6eb278eb6d7bf322c01a1c7cceb7fad1f
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469062"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="59e9b-104">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="59e9b-104">Gaze and dwell</span></span>

<span data-ttu-id="59e9b-105">Cuando las manos están ocupadas con herramientas y los elementos, gestos pueden ser tedioso o imposible.</span><span class="sxs-lookup"><span data-stu-id="59e9b-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="59e9b-106">Comandos de voz, como movimiento, pueden resultar poco confiables, por ejemplo en condiciones excesivamente altos.</span><span class="sxs-lookup"><span data-stu-id="59e9b-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="59e9b-107">Además, el uso de voz a los equipos de control no es aún una interacción estándar, pero ciertamente está ganando vapor!</span><span class="sxs-lookup"><span data-stu-id="59e9b-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="59e9b-108">Mirada permanencia ofrece el mecanismo más familiar y fácil de patrón para sobreimpresa trabajo manos libres en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="59e9b-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="59e9b-109">Además, mirada permanencia es 100% confiable independientemente de las restricciones de interferencias ni silencio de ruido en el entorno operativo.</span><span class="sxs-lookup"><span data-stu-id="59e9b-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="59e9b-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="59e9b-110">Goals</span></span>

<span data-ttu-id="59e9b-111">Proporcionan un mecanismo para interacciones completa manos libres, sin utilizar la voz.</span><span class="sxs-lookup"><span data-stu-id="59e9b-111">Provide a mechanism for full hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="59e9b-112">Principios de diseño</span><span class="sxs-lookup"><span data-stu-id="59e9b-112">Design principles</span></span>

1. <span data-ttu-id="59e9b-113">Mirada no es un arma</span><span class="sxs-lookup"><span data-stu-id="59e9b-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="59e9b-114">Mirada requiere comentarios visuales para la interacción intuitiva, pero pueden provocar la ansiedad demasiada comentarios.</span><span class="sxs-lookup"><span data-stu-id="59e9b-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="59e9b-115">Los comentarios deben ayudan a los usuarios saber lo tiene como destino, pero no selección automática en su intención.</span><span class="sxs-lookup"><span data-stu-id="59e9b-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="59e9b-116">Leer texto requiere una consideración adicional para proporcionar un espacio de usuario para absorber la información antes de seleccionar.</span><span class="sxs-lookup"><span data-stu-id="59e9b-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="59e9b-117">Buscar la velocidad de Rubiales</span><span class="sxs-lookup"><span data-stu-id="59e9b-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="59e9b-118">El relleno de permanencia puede tener temporizadores diferentes según el impacto de navegación: funciones utilizadas con más frecuencia generalmente se beneficiarán de tiempos más rápidos de relleno, mientras que las funciones más daños consecuenciales pueden beneficiarse de tiempos más largos de relleno.</span><span class="sxs-lookup"><span data-stu-id="59e9b-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="59e9b-119">Las curvas de animación del color de relleno positivamente pueden influir en una sensación de tiempos más rápidos de relleno.</span><span class="sxs-lookup"><span data-stu-id="59e9b-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="59e9b-120">Deben tener en cuenta consideraciones para habilitar la Decisión del usuario de fast/medium/lento invalidaciones de velocidad de relleno.</span><span class="sxs-lookup"><span data-stu-id="59e9b-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="59e9b-121">Diga definitivamente a efecto yo-yo</span><span class="sxs-lookup"><span data-stu-id="59e9b-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="59e9b-122">El efecto de yo-yo (también conocido como "noche en the Roxbury") es un patrón incómodo que puede surgir de cierta selección de ubicación de contenido y los controles basados en la mirada.</span><span class="sxs-lookup"><span data-stu-id="59e9b-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="59e9b-123">Por ejemplo, una barra de navegación de la lista con el botón de relleno en la parte inferior provoca un bucle de - vistazo hacia abajo para profundizaré, buscar en los resultados, busque hacia abajo para permanencia, etcetera. Este patrón resultante no resulta cómodo y debe evitarse mediante la colocación de controles de navegación en una ubicación centralizada que requiere menos atrás y adelante.</span><span class="sxs-lookup"><span data-stu-id="59e9b-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="59e9b-124">Selección de ubicación de los botones de permanencia en relación con sus efectos se vuelve importante para su comodidad.</span><span class="sxs-lookup"><span data-stu-id="59e9b-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="59e9b-125">Patrones de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="59e9b-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="59e9b-126">Botones de alta frecuencia</span><span class="sxs-lookup"><span data-stu-id="59e9b-126">High frequency buttons</span></span>
    
* <span data-ttu-id="59e9b-127">Botones siguiente y atrás</span><span class="sxs-lookup"><span data-stu-id="59e9b-127">Next/Back buttons</span></span>
  * <span data-ttu-id="59e9b-128">Relleno de previo muy breve retraso (búfer del parpadeo paso elevado)</span><span class="sxs-lookup"><span data-stu-id="59e9b-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="59e9b-129">Los botones más grandes son más fáciles de posicionamiento con mirada</span><span class="sxs-lookup"><span data-stu-id="59e9b-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="59e9b-130">Bueno para no mantenerlos a la altura del ojo por lo tanto, ningún esfuerzo para interactuar en</span><span class="sxs-lookup"><span data-stu-id="59e9b-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="59e9b-131">Región de permanencia puede ser mayor que el icono inactivo que resulte más fácil de usar (atrás)</span><span class="sxs-lookup"><span data-stu-id="59e9b-131">Dwell region can be larger than inactive icon to make it easier to use (Back)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="59e9b-132">Botones de baja frecuencia</span><span class="sxs-lookup"><span data-stu-id="59e9b-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="59e9b-133">Activar el menú de configuración</span><span class="sxs-lookup"><span data-stu-id="59e9b-133">Activate settings menu</span></span>
  * <span data-ttu-id="59e9b-134">Retrasar ya relleno previo acuerdo (búfer del parpadeo paso elevado)</span><span class="sxs-lookup"><span data-stu-id="59e9b-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="59e9b-135">Intente mantener estos botones interfiera pathways cursor frecuentes</span><span class="sxs-lookup"><span data-stu-id="59e9b-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="59e9b-136">Confirmaciones (es decir, flujo de análisis, los cuadros de diálogo)</span><span class="sxs-lookup"><span data-stu-id="59e9b-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="59e9b-137">Mostrar resaltado de la selección en el botón principal</span><span class="sxs-lookup"><span data-stu-id="59e9b-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="59e9b-138">Revelar permanencia destino al mismo tiempo que resalte de la selección</span><span class="sxs-lookup"><span data-stu-id="59e9b-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="59e9b-139">Use hincapié que rodea el icono para simplificar la interfaz de destino</span><span class="sxs-lookup"><span data-stu-id="59e9b-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="59e9b-140">Decisión importante, por lo que no activa el resaltado, revela permanencia destino para la revisión</span><span class="sxs-lookup"><span data-stu-id="59e9b-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="59e9b-141">Botones de alternancia</span><span class="sxs-lookup"><span data-stu-id="59e9b-141">Toggle buttons</span></span>

* <span data-ttu-id="59e9b-142">Anclar</span><span class="sxs-lookup"><span data-stu-id="59e9b-142">Pin</span></span>
  * <span data-ttu-id="59e9b-143">Estado visual clara activas e inactivas</span><span class="sxs-lookup"><span data-stu-id="59e9b-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="59e9b-144">Relleno radial ayuda al usuario centrarse y proporciona un curso natural</span><span class="sxs-lookup"><span data-stu-id="59e9b-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="59e9b-145">Opciones de configuración individuales</span><span class="sxs-lookup"><span data-stu-id="59e9b-145">Individual settings</span></span>
  * <span data-ttu-id="59e9b-146">Estados desactive activas e inactivas</span><span class="sxs-lookup"><span data-stu-id="59e9b-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="59e9b-147">Profundizaré destinos todos en el icono circundante izquierda</span><span class="sxs-lookup"><span data-stu-id="59e9b-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="59e9b-148">Permanencia tiene como destino solo aparecen cuando resaltada de la selección activa</span><span class="sxs-lookup"><span data-stu-id="59e9b-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="59e9b-149">"Hincapié en el control deslizante" en el lado derecho para activar/desactivar configuración</span><span class="sxs-lookup"><span data-stu-id="59e9b-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="59e9b-150">Vistas de lista</span><span class="sxs-lookup"><span data-stu-id="59e9b-150">List views</span></span>

* <span data-ttu-id="59e9b-151">Vista de lista exploración: archivos de la guía para abrir</span><span class="sxs-lookup"><span data-stu-id="59e9b-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="59e9b-152">Información destacada de cursor de fila desde cualquier parte en la fila, pero no comienza permanencia</span><span class="sxs-lookup"><span data-stu-id="59e9b-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="59e9b-153">Cuando se resalte la fila cursor, el destino de permanencia aparece a la izquierda</span><span class="sxs-lookup"><span data-stu-id="59e9b-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="59e9b-154">Profundizaré siempre un círculo en el lado izquierdo del texto en todas las vistas de lista de destino</span><span class="sxs-lookup"><span data-stu-id="59e9b-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="59e9b-155">No se muestran que todos profundizaré destinos al mismo tiempo para evitar la interfaz de usuario repetitivo</span><span class="sxs-lookup"><span data-stu-id="59e9b-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="59e9b-156">Volver a usar el mismo patrón para establecer la familiaridad de la experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="59e9b-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="59e9b-157">Exploración de la vista de lista - jerarquía de tareas y pasos de una guía</span><span class="sxs-lookup"><span data-stu-id="59e9b-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="59e9b-158">Profundizaré siempre un círculo en el lado izquierdo del texto de destino</span><span class="sxs-lookup"><span data-stu-id="59e9b-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="59e9b-159">Contraer o expandir la prestación de permanencia</span><span class="sxs-lookup"><span data-stu-id="59e9b-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="59e9b-160">Vista de lista exploración: selección del modo</span><span class="sxs-lookup"><span data-stu-id="59e9b-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="59e9b-161">Siga patrones establecidas anteriormente</span><span class="sxs-lookup"><span data-stu-id="59e9b-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="59e9b-162">Botones contextuales</span><span class="sxs-lookup"><span data-stu-id="59e9b-162">Contextual buttons</span></span>

* <span data-ttu-id="59e9b-163">Mostrar u ocultar 3D - muestra copia en 3D a lo largo de anclaje cerca hologramas</span><span class="sxs-lookup"><span data-stu-id="59e9b-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="59e9b-164">Estado visual clara activas e inactivas</span><span class="sxs-lookup"><span data-stu-id="59e9b-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="59e9b-165">Tablas dinámicas</span><span class="sxs-lookup"><span data-stu-id="59e9b-165">Pivots</span></span>

* <span data-ttu-id="59e9b-166">Lista de recientes/All guías</span><span class="sxs-lookup"><span data-stu-id="59e9b-166">Recent/All guides list</span></span>
  * <span data-ttu-id="59e9b-167">Rellenar la prestación de la interfaz de usuario que queda para indicar qué pestaña está activa</span><span class="sxs-lookup"><span data-stu-id="59e9b-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="59e9b-168">Para los ejes corto de una sola palabra, decidimos omitan el patrón de destino de permanencia</span><span class="sxs-lookup"><span data-stu-id="59e9b-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="59e9b-169">Se prefiere la interfaz simplificada destinos de otro círculo 2 y una interfaz de usuario más amplia</span><span class="sxs-lookup"><span data-stu-id="59e9b-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="59e9b-170">En nuestro caso, son lo suficientemente cortos para que un retraso proporciona suficiente confort antes de rellenar las palabras</span><span class="sxs-lookup"><span data-stu-id="59e9b-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="59e9b-171">Directrices de experiencia de usuario y procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="59e9b-171">UX guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="59e9b-172">Tamaños de los destinos</span><span class="sxs-lookup"><span data-stu-id="59e9b-172">Target sizes</span></span>

  * <span data-ttu-id="59e9b-173">Tamaño mínimo del icono de PIN: 6cm en el espacio global en Unity, 30 MRU (30cm @ 2m)</span><span class="sxs-lookup"><span data-stu-id="59e9b-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="59e9b-174">¿Son los destinos "magnetizar" o "permanente" en absoluto?</span><span class="sxs-lookup"><span data-stu-id="59e9b-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="59e9b-175">(es decir, que mirar suavizado del cursor)</span><span class="sxs-lookup"><span data-stu-id="59e9b-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="59e9b-176">Animación</span><span class="sxs-lookup"><span data-stu-id="59e9b-176">Animation</span></span>

  * <span data-ttu-id="59e9b-177">Retraso antes de permanencia desencadenadores visual .5sec</span><span class="sxs-lookup"><span data-stu-id="59e9b-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="59e9b-178">Duración del objeto visual de permanencia 1,2 s</span><span class="sxs-lookup"><span data-stu-id="59e9b-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="59e9b-179">¿Animación de curva?</span><span class="sxs-lookup"><span data-stu-id="59e9b-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="59e9b-180">Información visual</span><span class="sxs-lookup"><span data-stu-id="59e9b-180">Visual feedback</span></span>

  * <span data-ttu-id="59e9b-181">Relleno radial de ubicación de inicio del cursor de mirada</span><span class="sxs-lookup"><span data-stu-id="59e9b-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="59e9b-182">Relleno radial siempre desde el centro del botón.</span><span class="sxs-lookup"><span data-stu-id="59e9b-182">Always radial fill from center of button.</span></span> <span data-ttu-id="59e9b-183">Una respuesta coherente es menos confusa que todas las direcciones diferentes en los botones diferentes.</span><span class="sxs-lookup"><span data-stu-id="59e9b-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="59e9b-184">Esta regla puede interrumpirse aunque interacciones direccionales (p. ej., nav arriba/abajo/izquierda/derecha, etcetera.).</span><span class="sxs-lookup"><span data-stu-id="59e9b-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="59e9b-185">Por ejemplo, a la derecha hace que las guías una excepción en la siguiente y atrás ha dejado rellenos.</span><span class="sxs-lookup"><span data-stu-id="59e9b-185">For example, Guides makes an exception on Next/Back being left right fills.</span></span>
    * <span data-ttu-id="59e9b-186">Considere la posibilidad de invertir radial relleno desde fuera (si alternancia desactivado).</span><span class="sxs-lookup"><span data-stu-id="59e9b-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="59e9b-187">Inversa sensación de pulsar un botón es un práctico patrón visual para mantener.</span><span class="sxs-lookup"><span data-stu-id="59e9b-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="59e9b-188">Revelación progresiva</span><span class="sxs-lookup"><span data-stu-id="59e9b-188">Progressive disclosure</span></span>

 * <span data-ttu-id="59e9b-189">Revelación progresiva significa que el destino de permanencia se revela en resaltado (por ejemplo, en un control de lista)</span><span class="sxs-lookup"><span data-stu-id="59e9b-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="59e9b-190">Revela información destacada de la barra de texto con spotlight en mirada en cualquier parte de texto</span><span class="sxs-lookup"><span data-stu-id="59e9b-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="59e9b-191">Destino de relleno mirada siempre aparece en la izquierda, pero solo para el elemento de lista que aparece resaltado</span><span class="sxs-lookup"><span data-stu-id="59e9b-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="59e9b-192">Evite tener todos los destinos de permanencia en todo momento debido a la apariencia repetitiva de círculos apiladas</span><span class="sxs-lookup"><span data-stu-id="59e9b-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="59e9b-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="59e9b-193">See also</span></span>
* [<span data-ttu-id="59e9b-194">Manipulación directa</span><span class="sxs-lookup"><span data-stu-id="59e9b-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="59e9b-195">Señalar y confirmar</span><span class="sxs-lookup"><span data-stu-id="59e9b-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="59e9b-196">Conceptos básicos de la interacción</span><span class="sxs-lookup"><span data-stu-id="59e9b-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="59e9b-197">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="59e9b-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="59e9b-198">Mirada y voz</span><span class="sxs-lookup"><span data-stu-id="59e9b-198">Gaze and voice</span></span>](voice-design.md)
