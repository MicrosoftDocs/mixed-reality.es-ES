---
title: Objeto interactuable
description: Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D. En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, interfaz de usuario, experiencia de usuario
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601178"
---
# <a name="interactable-object"></a><span data-ttu-id="99748-105">Objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="99748-105">Interactable object</span></span>

<span data-ttu-id="99748-106">Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D.</span><span class="sxs-lookup"><span data-stu-id="99748-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="99748-107">En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya.</span><span class="sxs-lookup"><span data-stu-id="99748-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="99748-108">Nada puede ser un **Interactuable objeto** que desencadena un evento.</span><span class="sxs-lookup"><span data-stu-id="99748-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="99748-109">Un objeto interactuable puede representarse como nada una taza de café en la tabla a un globo flotante en el aire.</span><span class="sxs-lookup"><span data-stu-id="99748-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="99748-110">Todavía hacemos uso de los botones tradicionales en determinados situación tal como se muestra en la interfaz de usuario del cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="99748-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="99748-111">La representación visual del botón depende del contexto.</span><span class="sxs-lookup"><span data-stu-id="99748-111">The visual representation of the button depends on the context.</span></span>

![Imagen de hero objeto interactible](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="99748-113">En el  **[Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, hemos creado una serie de scripts de Unity y prefabricados que le ayudarán a crean objetos Interactuable.</span><span class="sxs-lookup"><span data-stu-id="99748-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="99748-114">Puede usarlas para crear cualquier tipo de objeto que el usuario puede interactuar con, uso de estos Estados interacción estándar: observación, destino y presionado.</span><span class="sxs-lookup"><span data-stu-id="99748-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="99748-115">Puede personalizar fácilmente el diseño visual con sus propios recursos.</span><span class="sxs-lookup"><span data-stu-id="99748-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="99748-116">Animaciones detalladas pueden personalizarse mediante la creación y asignación correspondientes clips de animación para los Estados de interacción en el controlador de animación de Unity o utilizar offset y escala.</span><span class="sxs-lookup"><span data-stu-id="99748-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="99748-117">Comentarios visuales para los Estados de interacción de entrada diferente</span><span class="sxs-lookup"><span data-stu-id="99748-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="99748-118">En realidad mixta, puesto que los objetos holográficas se mezclan con el entorno real, podría ser difícil de entender qué objetos son interactuable.</span><span class="sxs-lookup"><span data-stu-id="99748-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="99748-119">Para los objetos interactuable en su experiencia, es importante proporcionar comentarios visuales diferenciadas para cada estado de entrada.</span><span class="sxs-lookup"><span data-stu-id="99748-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="99748-120">Esto ayuda al usuario a entender qué parte de su experiencia es interactuable y hace que el usuario seguro con el método de interacción coherente.</span><span class="sxs-lookup"><span data-stu-id="99748-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="99748-121">Para todos los objetos que el usuario puede interactuar con, se recomienda tener comentarios visuales diferentes para estos tres estados de entrada:</span><span class="sxs-lookup"><span data-stu-id="99748-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="99748-122">**Observación**: Estado de inactividad predeterminado del objeto.</span><span class="sxs-lookup"><span data-stu-id="99748-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="99748-123">**Destino**: Cuando el objeto se destina a cursor mirada, un toque el puntero de movimiento o proximidad del controlador.</span><span class="sxs-lookup"><span data-stu-id="99748-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="99748-124">**Presiona**: Cuando se presiona el objeto con el gesto de pulsar en el aire, presione dedo o botón de selección del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="99748-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="99748-125">![Botón holográfica](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="99748-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="99748-126">*Observación de estado, estado de destino y estado presionado*</span><span class="sxs-lookup"><span data-stu-id="99748-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="99748-127">En Windows Mixed Reality, puede encontrar los ejemplos de visualización de los distintos Estados de entrada en el menú Inicio y los botones de barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99748-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="99748-128">Puede usar técnicas como el resaltado o la escala para proporcionar comentarios visuales a los Estados de entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="99748-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="99748-129">En el 2 de HoloLens, ya que admite mano totalmente articulados y seguimiento de entrada, podemos proporcionar prestaciones adicionales según la proximidad a las manos.</span><span class="sxs-lookup"><span data-stu-id="99748-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="99748-130">El [botón en 2 HoloLens](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) se muestra en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="99748-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Botón pressable](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="99748-132">Ejemplos de objetos interactuable</span><span class="sxs-lookup"><span data-stu-id="99748-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="99748-133">Botón de malla</span><span class="sxs-lookup"><span data-stu-id="99748-133">Mesh button</span></span>

![Botón de malla](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="99748-135">Estos son ejemplos de uso de tipos primitivos y mallas 3D importadas como objetos Interactuable.</span><span class="sxs-lookup"><span data-stu-id="99748-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="99748-136">Puede asignar fácilmente diferentes valores de escala, desplazamiento y color para responder a cada estado de interacción de entrada.</span><span class="sxs-lookup"><span data-stu-id="99748-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="99748-137">Barra de herramientas</span><span class="sxs-lookup"><span data-stu-id="99748-137">Toolbar</span></span>

![Barra de herramientas](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="99748-139">Una barra de herramientas es un patrón ampliamente utilizado en las experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="99748-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="99748-140">Es una colección simple de botones con comportamientos adicionales como [Billboarding y tag-along](billboarding-and-tag-along.md).</span><span class="sxs-lookup"><span data-stu-id="99748-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="99748-141">Este ejemplo utiliza una secuencia de comandos Billboarding y tag-along desde el MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="99748-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="99748-142">Puede controlar comportamientos detallados como distancia, mover los valores de velocidad y el umbral.</span><span class="sxs-lookup"><span data-stu-id="99748-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="99748-143">Botón tradicional</span><span class="sxs-lookup"><span data-stu-id="99748-143">Traditional button</span></span>

![Botón tradicional](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="99748-145">En este ejemplo se muestra un botón de estilo tradicional de 2D.</span><span class="sxs-lookup"><span data-stu-id="99748-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="99748-146">El estado de cada entrada tiene una profundidad ligeramente diferente y la propiedad de animación.</span><span class="sxs-lookup"><span data-stu-id="99748-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="99748-147">Otros ejemplos</span><span class="sxs-lookup"><span data-stu-id="99748-147">Other examples</span></span>

<span data-ttu-id="99748-148">![Botón de comando](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="99748-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="99748-149">*Botón de comando*</span><span class="sxs-lookup"><span data-stu-id="99748-149">*Push button*</span></span>
<br>
<span data-ttu-id="99748-150">![Objeto vida real](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="99748-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="99748-151">*Objeto de la vida real*</span><span class="sxs-lookup"><span data-stu-id="99748-151">*Real life object*</span></span>

<span data-ttu-id="99748-152">Con HoloLens, puede aprovechar el espacio físico.</span><span class="sxs-lookup"><span data-stu-id="99748-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="99748-153">Imagine un botón de comando holográfico en una pared físico.</span><span class="sxs-lookup"><span data-stu-id="99748-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="99748-154">O ¿qué le parece una taza de café en una tabla real?</span><span class="sxs-lookup"><span data-stu-id="99748-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="99748-155">Con modelos 3D importados de modelado de software, podemos crear un objeto Interactuable similar al objeto de la vida real.</span><span class="sxs-lookup"><span data-stu-id="99748-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="99748-156">Puesto que es un objeto digital, podemos agregar interacciones mágicos a él.</span><span class="sxs-lookup"><span data-stu-id="99748-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="99748-157">Objeto interactuable en el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="99748-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="99748-158">Puede encontrar el [ejemplos de Interactable de objeto en el Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="99748-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="99748-159">Vea también</span><span class="sxs-lookup"><span data-stu-id="99748-159">See also</span></span>
* [<span data-ttu-id="99748-160">Botón pressable en realidad mixta Kit de herramientas de Unity</span><span class="sxs-lookup"><span data-stu-id="99748-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="99748-161">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="99748-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="99748-162">Vallas publicitarias y tag-along</span><span class="sxs-lookup"><span data-stu-id="99748-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
