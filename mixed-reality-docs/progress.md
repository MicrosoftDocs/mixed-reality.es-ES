---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario
ms.openlocfilehash: 4befaa6f55bff6a820c976db969fdad7b64a2214
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143246"
---
# <a name="progress-indicator"></a><span data-ttu-id="aac2e-104">Indicador de progreso</span><span class="sxs-lookup"><span data-stu-id="aac2e-104">Progress indicator</span></span>

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="aac2e-105">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="aac2e-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="aac2e-106">Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.</span><span class="sxs-lookup"><span data-stu-id="aac2e-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="aac2e-107">Tipos de progreso</span><span class="sxs-lookup"><span data-stu-id="aac2e-107">Types of progress</span></span>

<span data-ttu-id="aac2e-108">Es importante proporcionar información de usuario sobre lo que está ocurriendo.</span><span class="sxs-lookup"><span data-stu-id="aac2e-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="aac2e-109">En realidad, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no proporciona buenos comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="aac2e-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="aac2e-110">En situaciones en las que se tardan unos segundos, como cuando se cargan datos o se actualiza una escena, es conveniente mostrar un indicador visual.</span><span class="sxs-lookup"><span data-stu-id="aac2e-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="aac2e-111">Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.</span><span class="sxs-lookup"><span data-stu-id="aac2e-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="aac2e-112">Barra de progreso</span><span class="sxs-lookup"><span data-stu-id="aac2e-112">Progress bar</span></span><br>
        <span data-ttu-id="aac2e-113">Una barra de progreso muestra el porcentaje completado de una tarea.</span><span class="sxs-lookup"><span data-stu-id="aac2e-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="aac2e-114">Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="aac2e-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="aac2e-115">*Imagen: ejemplo de barra de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="aac2e-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="aac2e-116">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="aac2e-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="aac2e-117">![ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="aac2e-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="aac2e-118">Círculo de progreso</span><span class="sxs-lookup"><span data-stu-id="aac2e-118">Progress ring</span></span><br>
        <span data-ttu-id="aac2e-119">Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea cualquier interacción del usuario adicional hasta que se haya completado la operación.</span><span class="sxs-lookup"><span data-stu-id="aac2e-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="aac2e-120">*Imagen: ejemplo de anillo de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="aac2e-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="aac2e-121">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="aac2e-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="aac2e-122">![ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="aac2e-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="aac2e-123">Progreso con un objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="aac2e-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="aac2e-124">Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="aac2e-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="aac2e-125">*Imagen: progreso con el ejemplo de malla personalizada en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="aac2e-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="aac2e-126">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="aac2e-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="aac2e-127">![progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="aac2e-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="aac2e-128">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="aac2e-128">Best practices</span></span>
* <span data-ttu-id="aac2e-129">Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto.</span><span class="sxs-lookup"><span data-stu-id="aac2e-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="aac2e-130">La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada.</span><span class="sxs-lookup"><span data-stu-id="aac2e-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="aac2e-131">La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.</span><span class="sxs-lookup"><span data-stu-id="aac2e-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="aac2e-132">Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario.</span><span class="sxs-lookup"><span data-stu-id="aac2e-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="aac2e-133">El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado.</span><span class="sxs-lookup"><span data-stu-id="aac2e-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="aac2e-134">También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="aac2e-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="aac2e-135">Indicador de progreso en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="aac2e-135">Progress indicator in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="aac2e-136">MRTK: indicador de progreso Prefabs</span><span class="sxs-lookup"><span data-stu-id="aac2e-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="aac2e-137">MRTK: servicio de transición de escenas</span><span class="sxs-lookup"><span data-stu-id="aac2e-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="aac2e-138">Consulta también</span><span class="sxs-lookup"><span data-stu-id="aac2e-138">See also</span></span>

* [<span data-ttu-id="aac2e-139">Cursores</span><span class="sxs-lookup"><span data-stu-id="aac2e-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="aac2e-140">Rayo de mano</span><span class="sxs-lookup"><span data-stu-id="aac2e-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="aac2e-141">Button</span><span class="sxs-lookup"><span data-stu-id="aac2e-141">Button</span></span>](button.md)
* [<span data-ttu-id="aac2e-142">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="aac2e-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="aac2e-143">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="aac2e-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="aac2e-144">Manipula</span><span class="sxs-lookup"><span data-stu-id="aac2e-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="aac2e-145">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="aac2e-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="aac2e-146">Menú Near</span><span class="sxs-lookup"><span data-stu-id="aac2e-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="aac2e-147">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="aac2e-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="aac2e-148">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="aac2e-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="aac2e-149">Teclado</span><span class="sxs-lookup"><span data-stu-id="aac2e-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="aac2e-150">Herramienta</span><span class="sxs-lookup"><span data-stu-id="aac2e-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="aac2e-151">Tabletas</span><span class="sxs-lookup"><span data-stu-id="aac2e-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="aac2e-152">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="aac2e-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="aac2e-153">Sombreador</span><span class="sxs-lookup"><span data-stu-id="aac2e-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="aac2e-154">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="aac2e-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="aac2e-155">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="aac2e-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="aac2e-156">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="aac2e-156">Surface magnetism</span></span>](surface-magnetism.md)
