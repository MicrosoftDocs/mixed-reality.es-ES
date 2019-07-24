---
title: Mostrar progreso
description: Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, IU, experiencia de usuario
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523254"
---
# <a name="displaying-progress"></a><span data-ttu-id="ff4e3-104">Mostrar progreso</span><span class="sxs-lookup"><span data-stu-id="ff4e3-104">Displaying progress</span></span>

<span data-ttu-id="ff4e3-105">Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="ff4e3-106">Esto puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar el tiempo de espera aproximado, según el indicador que usa.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="ff4e3-107">![Ejemplo de anillo de progreso en HoloLens](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="ff4e3-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="ff4e3-108">*Ejemplo de anillo de progreso en HoloLens*</span><span class="sxs-lookup"><span data-stu-id="ff4e3-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="ff4e3-109">Tipos de progreso</span><span class="sxs-lookup"><span data-stu-id="ff4e3-109">Types of progress</span></span>

<span data-ttu-id="ff4e3-110">Es importante proporcionar información de usuario sobre lo que está ocurriendo.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="ff4e3-111">En realidad, los usuarios pueden distraerse fácilmente por el entorno físico u objetos si la aplicación no proporciona buenos comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="ff4e3-112">En situaciones en las que se tardan unos segundos, como cuando se cargan datos o se actualiza una escena, es conveniente mostrar un indicador visual.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="ff4e3-113">Hay dos opciones para mostrar el usuario que está realizando una operación: una **barra de progreso** o un **anillo de progreso**.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="ff4e3-114">Barra de progreso</span><span class="sxs-lookup"><span data-stu-id="ff4e3-114">Progress bar</span></span>

![Ejemplo de barra de progreso en HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="ff4e3-116">Una barra de progreso muestra el porcentaje completado de una tarea.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="ff4e3-117">Se debe usar durante una operación cuya duración se conoce (determinan), pero su progreso no debe bloquear la interacción del usuario con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="ff4e3-118">Círculo de progreso</span><span class="sxs-lookup"><span data-stu-id="ff4e3-118">Progress ring</span></span>

![Ejemplo de anillo de progreso en HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="ff4e3-120">Un anillo de progreso solo tiene un estado indeterminado y debe usarse cuando se bloquea cualquier interacción del usuario adicional hasta que se haya completado la operación.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="ff4e3-121">Progreso con un objeto personalizado</span><span class="sxs-lookup"><span data-stu-id="ff4e3-121">Progress with a custom object</span></span>

![Progreso con el ejemplo de malla personalizada en HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="ff4e3-123">Puede Agregar a la identidad de personalidad y marca de la aplicación personalizando el control de progreso con sus propios objetos 2D/3D personalizados.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="ff4e3-124">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="ff4e3-124">Best practices</span></span>
* <span data-ttu-id="ff4e3-125">Encadenar estrechamente la [cartelera o etiqueta, junto](billboarding-and-tag-along.md) con la presentación de progreso, ya que el usuario puede trasladar fácilmente el encabezado a un espacio vacío y perder el contexto.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="ff4e3-126">La aplicación podría parecerse a que se ha bloqueado si el usuario no puede ver nada.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="ff4e3-127">La cartelera y el etiquetado están integrados en el recurso prefabricado de progreso.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="ff4e3-128">Siempre es conveniente proporcionar información de estado sobre lo que está ocurriendo al usuario.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="ff4e3-129">El recurso prefabricado de progreso proporciona varios estilos visuales, incluido el progreso de tipo anillo estándar de Windows para proporcionar el estado.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="ff4e3-130">También puede usar una malla personalizada con una animación si desea que el estilo del progreso se alinee con la marca de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ff4e3-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff4e3-131">Vea también</span><span class="sxs-lookup"><span data-stu-id="ff4e3-131">See also</span></span>
* [<span data-ttu-id="ff4e3-132">Scripts de progreso y Prefabs en el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="ff4e3-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="ff4e3-133">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="ff4e3-133">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ff4e3-134">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="ff4e3-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ff4e3-135">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="ff4e3-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ff4e3-136">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="ff4e3-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
