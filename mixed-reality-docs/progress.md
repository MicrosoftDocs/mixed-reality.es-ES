---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, la interfaz de usuario, experiencia de usuario
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605356"
---
# <a name="displaying-progress"></a><span data-ttu-id="e3a21-104">Mostrar progreso</span><span class="sxs-lookup"><span data-stu-id="e3a21-104">Displaying progress</span></span>

<span data-ttu-id="e3a21-105">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="e3a21-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="e3a21-106">Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.</span><span class="sxs-lookup"><span data-stu-id="e3a21-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="e3a21-107">![Ejemplo de anillo de progreso en HoloLens](images/640px-progress-hero.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3a21-107">![Progress ring example in HoloLens](images/640px-progress-hero.jpg)</span></span><br>
<span data-ttu-id="e3a21-108">*Ejemplo de anillo de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="e3a21-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="e3a21-109">Tipos de progreso</span><span class="sxs-lookup"><span data-stu-id="e3a21-109">Types of progress</span></span>

<span data-ttu-id="e3a21-110">Es importante proporcionar al usuario información sobre lo que sucede.</span><span class="sxs-lookup"><span data-stu-id="e3a21-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="e3a21-111">En realidad mixta los usuarios pueden fácilmente distraerse por entorno físico u objetos si la aplicación no da buenos comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="e3a21-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="e3a21-112">Para situaciones que tardan unos segundos, por ejemplo, cuando se está cargando datos o una escena se está actualizando, es buena idea para mostrar un indicador visual.</span><span class="sxs-lookup"><span data-stu-id="e3a21-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="e3a21-113">Hay dos opciones para mostrar al usuario que una operación está en curso: un **barra de progreso** o un **anillo de progreso**.</span><span class="sxs-lookup"><span data-stu-id="e3a21-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="e3a21-114">Barra de progreso</span><span class="sxs-lookup"><span data-stu-id="e3a21-114">Progress bar</span></span>

![Ejemplo de la barra de progreso en HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="e3a21-116">Una barra de progreso muestra el porcentaje completado de una tarea.</span><span class="sxs-lookup"><span data-stu-id="e3a21-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="e3a21-117">Se debe usar durante una operación cuya duración se conoce (determinada), pero su progreso no debe bloquear la interacción del usuario con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e3a21-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="e3a21-118">Círculo de progreso</span><span class="sxs-lookup"><span data-stu-id="e3a21-118">Progress ring</span></span>

![Ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="e3a21-120">Un anillo de progreso debe usarse cuando ninguna intervención del usuario se bloquea hasta que se ha completado la operación y solo tiene un estado indeterminado.</span><span class="sxs-lookup"><span data-stu-id="e3a21-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="e3a21-121">Progreso con un objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="e3a21-121">Progress with a custom object</span></span>

![Progreso de la malla personalizada de ejemplo en HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="e3a21-123">Puede agregar a la personalidad de la aplicación y la identidad de marca personalizando el control de progreso con sus propios objetos 2D o 3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="e3a21-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="e3a21-124">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="e3a21-124">Best practices</span></span>
* <span data-ttu-id="e3a21-125">Acoplando [vallas publicitarias o tag-along](billboarding-and-tag-along.md) a la pantalla de progreso, ya que el usuario puede mover su cabeza a un espacio vacío fácilmente y perder contexto de.</span><span class="sxs-lookup"><span data-stu-id="e3a21-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="e3a21-126">La aplicación puede parecer que se ha bloqueado si el usuario no puede ver nada.</span><span class="sxs-lookup"><span data-stu-id="e3a21-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="e3a21-127">Billboarding y tag-along está integrado en el recurso prefabricado de progreso.</span><span class="sxs-lookup"><span data-stu-id="e3a21-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="e3a21-128">Siempre es bueno proporcionar información de estado sobre lo que sucede al usuario.</span><span class="sxs-lookup"><span data-stu-id="e3a21-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="e3a21-129">El recurso prefabricado de progreso proporciona varios estilos visuales, incluidos el progreso de tipo de anillo estándar de Windows para proporcionar el estado.</span><span class="sxs-lookup"><span data-stu-id="e3a21-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="e3a21-130">También puede usar una malla personalizada con una animación si desea que el estilo de su progreso para alinearse con la marca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e3a21-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3a21-131">Vea también</span><span class="sxs-lookup"><span data-stu-id="e3a21-131">See also</span></span>
* [<span data-ttu-id="e3a21-132">Secuencias de comandos y prefabricados para el progreso en el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="e3a21-132">Scripts and prefabs for Progress on Mixed Reality Toolkit</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [<span data-ttu-id="e3a21-133">Objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="e3a21-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e3a21-134">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="e3a21-134">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e3a21-135">Vallas publicitarias y tag-along</span><span class="sxs-lookup"><span data-stu-id="e3a21-135">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
