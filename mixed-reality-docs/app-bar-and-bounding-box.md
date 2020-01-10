---
title: Cuadro de límite y barra de la aplicación
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite
ms.openlocfilehash: dab41207c2558fe8bb3fe07fca666cb2668f4e45
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723204"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="400f6-104">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="400f6-104">Bounding box and App bar</span></span>
<span data-ttu-id="400f6-105">![límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/UX/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="400f6-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="400f6-106">¿Cuál es el cuadro de límite?</span><span class="sxs-lookup"><span data-stu-id="400f6-106">What is the Bounding box?</span></span>

<span data-ttu-id="400f6-107">El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="400f6-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="400f6-108">Proporciona al usuario una asequibilidad de que el objeto es ajustable actualmente.</span><span class="sxs-lookup"><span data-stu-id="400f6-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="400f6-109">En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario.</span><span class="sxs-lookup"><span data-stu-id="400f6-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="400f6-110">Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="400f6-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="400f6-111">Escalado de un objeto</span><span class="sxs-lookup"><span data-stu-id="400f6-111">Scaling an object</span></span><br>
        <span data-ttu-id="400f6-112">Las esquinas del cuadro de límite indican al usuario que el objeto se puede escalar.</span><span class="sxs-lookup"><span data-stu-id="400f6-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="400f6-113">Los identificadores siguen un patrón muy entendido para ajustar la escala.</span><span class="sxs-lookup"><span data-stu-id="400f6-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="400f6-114">Esta prestación visual muestra a los usuarios el área total del objeto, aunque no sea visible fuera de un modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="400f6-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="400f6-115">Esto es especialmente importante porque, si no estuviera allí, es posible que un objeto ajustado a otro objeto o superficie parezca que se comporte como si hubiera espacio alrededor que no debiera estar ahí.</span><span class="sxs-lookup"><span data-stu-id="400f6-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="400f6-116">*Bucle de vídeo: escalado de un objeto a través del cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="400f6-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="400f6-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="400f6-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="400f6-118">![punto de vista de HoloLens de escalado de un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="400f6-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="400f6-119">Girar un objeto</span><span class="sxs-lookup"><span data-stu-id="400f6-119">Rotating an object</span></span><br>
        <span data-ttu-id="400f6-120">Las prestaciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación.</span><span class="sxs-lookup"><span data-stu-id="400f6-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="400f6-121">Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados.</span><span class="sxs-lookup"><span data-stu-id="400f6-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="400f6-122">No solo se pueden ajustar y escalar, sino que ahora giran.</span><span class="sxs-lookup"><span data-stu-id="400f6-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="400f6-123">*Bucle de vídeo: girar un objeto a través del cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="400f6-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="400f6-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="400f6-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="400f6-125">![punto de vista de HoloLens de girar un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="400f6-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="400f6-126">Comentarios visuales sobre la proximidad en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="400f6-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="400f6-127">En HoloLens 2, hay una indicación visual adicional que puede ayudar a la percepción del usuario de la profundidad.</span><span class="sxs-lookup"><span data-stu-id="400f6-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="400f6-128">Se muestra un anillo cerca de su dedo y se reduce verticalmente a medida que la mano se acerca al objeto.</span><span class="sxs-lookup"><span data-stu-id="400f6-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="400f6-129">El anillo finalmente converge en un punto cuando se alcanza el estado presionado.</span><span class="sxs-lookup"><span data-stu-id="400f6-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="400f6-130">Esta prestación visual ayuda al usuario a comprender hasta qué punto proceden del objeto.</span><span class="sxs-lookup"><span data-stu-id="400f6-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="400f6-131">*Bucle de vídeo: ejemplo de comentarios visuales basados en proximidad a un cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="400f6-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="400f6-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="400f6-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="400f6-133">![comentarios visuales sobre la proximidad](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="400f6-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="400f6-134">**Para el desarrollo de aplicaciones de Unity, consulte [cuadro de límite en el kit de herramientas de realidad mixta (Unity).](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span><span class="sxs-lookup"><span data-stu-id="400f6-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="400f6-135">¿Qué es la barra de la aplicación?</span><span class="sxs-lookup"><span data-stu-id="400f6-135">What is the App bar?</span></span>

<span data-ttu-id="400f6-136">La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.</span><span class="sxs-lookup"><span data-stu-id="400f6-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="400f6-137">Este patrón se usa normalmente para proporcionar a los usuarios la capacidad de quitar y ajustar los hologramas.</span><span class="sxs-lookup"><span data-stu-id="400f6-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="400f6-138">La barra de la aplicación se diseñó principalmente como una manera de administrar objetos colocados en el entorno de un usuario.</span><span class="sxs-lookup"><span data-stu-id="400f6-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="400f6-139">Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="400f6-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="400f6-140">La barra de la aplicación sigue al usuario</span><span class="sxs-lookup"><span data-stu-id="400f6-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="400f6-141">Puesto que este patrón se usa con objetos que están bloqueados por todo el mundo, a medida que un usuario se desplaza por el objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario.</span><span class="sxs-lookup"><span data-stu-id="400f6-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="400f6-142">Aunque esto no se está desformando, se consigue el mismo resultado; impedir que la posición de un usuario tapaba o bloquee la funcionalidad que, de otro modo, estará disponible desde una ubicación diferente en su entorno.</span><span class="sxs-lookup"><span data-stu-id="400f6-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="400f6-143">*Bucle de vídeo: desplazarse por un holograma, la barra de la aplicación sigue*</span><span class="sxs-lookup"><span data-stu-id="400f6-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="400f6-144">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="400f6-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="400f6-145">![recorrer un holograma.</span><span class="sxs-lookup"><span data-stu-id="400f6-145">![Walking around a hologram.</span></span> <span data-ttu-id="400f6-146">A continuación se muestra la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="400f6-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="400f6-147">Cuadro de límite en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="400f6-147">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="400f6-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y Prefabs para el cuadro de límite y la barra de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="400f6-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="400f6-149">Para agregar un cuadro de límite, basta con asignar el script BoundingBox.cs a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="400f6-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="400f6-150">MRTK: cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="400f6-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="400f6-151">Consulta también</span><span class="sxs-lookup"><span data-stu-id="400f6-151">See also</span></span>

* [<span data-ttu-id="400f6-152">Cursores</span><span class="sxs-lookup"><span data-stu-id="400f6-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="400f6-153">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="400f6-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="400f6-154">Button</span><span class="sxs-lookup"><span data-stu-id="400f6-154">Button</span></span>](button.md)
* [<span data-ttu-id="400f6-155">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="400f6-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="400f6-156">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="400f6-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="400f6-157">Manipulación</span><span class="sxs-lookup"><span data-stu-id="400f6-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="400f6-158">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="400f6-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="400f6-159">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="400f6-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="400f6-160">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="400f6-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="400f6-161">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="400f6-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="400f6-162">Teclado</span><span class="sxs-lookup"><span data-stu-id="400f6-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="400f6-163">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="400f6-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="400f6-164">Claqueta</span><span class="sxs-lookup"><span data-stu-id="400f6-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="400f6-165">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="400f6-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="400f6-166">Sombreador</span><span class="sxs-lookup"><span data-stu-id="400f6-166">Shader</span></span>](shader.md)
* [<span data-ttu-id="400f6-167">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="400f6-167">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="400f6-168">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="400f6-168">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="400f6-169">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="400f6-169">Surface magnetism</span></span>](surface-magnetism.md)
