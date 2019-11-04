---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437540"
---
# <a name="displaying-progress"></a><span data-ttu-id="9a55f-104">Mostrar progreso</span><span class="sxs-lookup"><span data-stu-id="9a55f-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="9a55f-105">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="9a55f-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="9a55f-106">Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.</span><span class="sxs-lookup"><span data-stu-id="9a55f-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="9a55f-107">Tipos de progreso</span><span class="sxs-lookup"><span data-stu-id="9a55f-107">Types of progress</span></span>

<span data-ttu-id="9a55f-108">Es importante proporcionar información de usuario sobre lo que está ocurriendo.</span><span class="sxs-lookup"><span data-stu-id="9a55f-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="9a55f-109">En realidad, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no proporciona buenos comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="9a55f-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="9a55f-110">En situaciones en las que se tardan unos segundos, como cuando se cargan datos o se actualiza una escena, es conveniente mostrar un indicador visual.</span><span class="sxs-lookup"><span data-stu-id="9a55f-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="9a55f-111">Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.</span><span class="sxs-lookup"><span data-stu-id="9a55f-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="9a55f-112">Barra de progreso</span><span class="sxs-lookup"><span data-stu-id="9a55f-112">Progress bar</span></span><br>
        <span data-ttu-id="9a55f-113">Una barra de progreso muestra el porcentaje completado de una tarea.</span><span class="sxs-lookup"><span data-stu-id="9a55f-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="9a55f-114">Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9a55f-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="9a55f-115">*Imagen: ejemplo de barra de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="9a55f-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9a55f-116">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9a55f-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9a55f-117">![ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="9a55f-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="9a55f-118">Círculo de progreso</span><span class="sxs-lookup"><span data-stu-id="9a55f-118">Progress ring</span></span><br>
        <span data-ttu-id="9a55f-119">Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea cualquier interacción del usuario adicional hasta que se haya completado la operación.</span><span class="sxs-lookup"><span data-stu-id="9a55f-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="9a55f-120">*Imagen: ejemplo de anillo de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="9a55f-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9a55f-121">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9a55f-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9a55f-122">![ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="9a55f-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="9a55f-123">Progreso con un objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="9a55f-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="9a55f-124">Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="9a55f-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="9a55f-125">*Imagen: progreso con el ejemplo de malla personalizada en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="9a55f-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="9a55f-126">espacio ![](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="9a55f-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="9a55f-127">![progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="9a55f-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="9a55f-128">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="9a55f-128">Best practices</span></span>
* <span data-ttu-id="9a55f-129">Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto.</span><span class="sxs-lookup"><span data-stu-id="9a55f-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="9a55f-130">La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada.</span><span class="sxs-lookup"><span data-stu-id="9a55f-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="9a55f-131">La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.</span><span class="sxs-lookup"><span data-stu-id="9a55f-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="9a55f-132">Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario.</span><span class="sxs-lookup"><span data-stu-id="9a55f-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="9a55f-133">El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado.</span><span class="sxs-lookup"><span data-stu-id="9a55f-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="9a55f-134">También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9a55f-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="9a55f-135">Consulta también</span><span class="sxs-lookup"><span data-stu-id="9a55f-135">See also</span></span>
* [<span data-ttu-id="9a55f-136">Scripts de progreso y Prefabs en el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9a55f-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="9a55f-137">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="9a55f-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9a55f-138">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="9a55f-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9a55f-139">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="9a55f-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9a55f-140">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="9a55f-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
