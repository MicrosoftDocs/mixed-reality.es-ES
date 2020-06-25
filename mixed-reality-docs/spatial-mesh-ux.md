---
title: Visualización de malla espacial
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidad mixta, HoloLens, controles de IU, interacción, UI, experiencia de usuario, diseño de la experiencia del usuario, interfaz de usuario espacial, interacción espacial, interfaz de usuario 3D, UX en 3D
ms.openlocfilehash: 17a799dcaba5caf4dd7018f8289cad02b40f1277
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85346134"
---
# <a name="spatial-mesh"></a><span data-ttu-id="fd3f5-103">Malla espacial</span><span class="sxs-lookup"><span data-stu-id="fd3f5-103">Spatial mesh</span></span>

![Malla espacial](images/UX/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="fd3f5-105">A través de la visualización de malla espacial, el usuario puede obtener información sobre cómo un dispositivo percibe y entiende el entorno físico.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="fd3f5-106">Además de proporcionar el contexto espacial, la visualización correcta de la malla espacial puede crear una experiencia agradables y mágica.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="fd3f5-107">Directrices de diseño</span><span class="sxs-lookup"><span data-stu-id="fd3f5-107">Design guideline</span></span>
<span data-ttu-id="fd3f5-108">Dado que es importante permitir que el usuario se Centre e interactúe con el contenido, la visualización continua y repetida de la malla espacial en segundo plano podría ser distraer.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="fd3f5-109">Se recomienda visualizar el entorno de forma moderada, ya sea una sola vez en el inicio inicial o cuando el usuario muestra claramente la intención de ver la malla ambiental mediante el destino y el espacio de punteo aéreo.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="fd3f5-110">Puede observar este comportamiento en el shell de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="fd3f5-111">Visualización de malla espacial en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="fd3f5-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="fd3f5-112">MRTK proporciona varios materiales para la visualización de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="fd3f5-113">**MRTK_Wireframe. MAT, MRTK_Wireframe. MAT**: material de malla espacial estático predeterminado que muestra los contornos de la malla sin animación.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="fd3f5-114">Este material es útil para la depuración, ya que muestra todas las geometrías espaciales de la malla.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="fd3f5-115">Sin embargo, no se recomienda para la producción.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="fd3f5-116">**MRTK_SurfaceReconstruction. MAT**: este material proporciona un efecto de pulso animado en la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-116">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="fd3f5-117">Puede usar este material para visualizar el entorno en un momento concreto de su experiencia o en la entrada de punteo de aire del usuario.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="fd3f5-118">Consulte **PulseShaderExamples. Unity** Scene para ver los ejemplos.</span><span class="sxs-lookup"><span data-stu-id="fd3f5-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/UX/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="fd3f5-119">Para más información, consulte [MRTK-Spatial awareing](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) y [MRTK-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .</span><span class="sxs-lookup"><span data-stu-id="fd3f5-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="fd3f5-120">Vea también</span><span class="sxs-lookup"><span data-stu-id="fd3f5-120">See also</span></span>

* [<span data-ttu-id="fd3f5-121">Cursores</span><span class="sxs-lookup"><span data-stu-id="fd3f5-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="fd3f5-122">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="fd3f5-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="fd3f5-123">Botón</span><span class="sxs-lookup"><span data-stu-id="fd3f5-123">Button</span></span>](button.md)
* [<span data-ttu-id="fd3f5-124">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="fd3f5-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fd3f5-125">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="fd3f5-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="fd3f5-126">Manipulación</span><span class="sxs-lookup"><span data-stu-id="fd3f5-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fd3f5-127">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="fd3f5-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="fd3f5-128">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="fd3f5-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="fd3f5-129">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="fd3f5-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fd3f5-130">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="fd3f5-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="fd3f5-131">Teclado</span><span class="sxs-lookup"><span data-stu-id="fd3f5-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="fd3f5-132">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="fd3f5-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="fd3f5-133">Claqueta</span><span class="sxs-lookup"><span data-stu-id="fd3f5-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="fd3f5-134">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="fd3f5-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="fd3f5-135">Sombreador</span><span class="sxs-lookup"><span data-stu-id="fd3f5-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="fd3f5-136">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="fd3f5-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="fd3f5-137">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="fd3f5-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="fd3f5-138">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="fd3f5-138">Surface magnetism</span></span>](surface-magnetism.md)
