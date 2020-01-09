---
title: Sombreador
description: El sombreador estándar de MRTK proporciona varios tipos de efectos visuales que se pueden usar con hologramas.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, IU, experiencia de usuario
ms.openlocfilehash: 4d95e335b3f7020766beae916423d0588ee66572
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694169"
---
# <a name="shader"></a><span data-ttu-id="d2546-104">Sombreador</span><span class="sxs-lookup"><span data-stu-id="d2546-104">Shader</span></span>

![Sombreador](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="d2546-106">Dado que los objetos holográficas se mezclan con los físicos del entorno, es importante proporcionar indicaciones visuales en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d2546-106">Since holographic objects are mixed with the physical ones in the environment, it's important to provide visual cues in mixed reality.</span></span> <span data-ttu-id="d2546-107">El sombreador estándar de MRTK proporciona varios tipos de efectos visuales que se pueden usar con hologramas.</span><span class="sxs-lookup"><span data-stu-id="d2546-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="d2546-108">El sistema de sombreado estándar de MRTK emplea un sombreador único y flexible que puede lograr objetos visuales similares al sombreador estándar de Unity, implementa [principios del sistema de diseño fluida](https://www.microsoft.com/design/fluent/#/)y sigue teniendo rendimiento en dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d2546-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="d2546-109">Ejemplos de efectos visuales con el sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="d2546-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="d2546-110">![Mover](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d2546-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="d2546-111">**Luz de proximidad**</span><span class="sxs-lookup"><span data-stu-id="d2546-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d2546-112">![Girar](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d2546-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="d2546-113">**Borde claro**</span><span class="sxs-lookup"><span data-stu-id="d2546-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d2546-114">Sombreador estándar de MRTK en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="d2546-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="d2546-115">MRTK: sombreador estándar</span><span class="sxs-lookup"><span data-stu-id="d2546-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="d2546-116">Consulta también</span><span class="sxs-lookup"><span data-stu-id="d2546-116">See also</span></span>

* [<span data-ttu-id="d2546-117">Cursores</span><span class="sxs-lookup"><span data-stu-id="d2546-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d2546-118">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="d2546-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d2546-119">Button</span><span class="sxs-lookup"><span data-stu-id="d2546-119">Button</span></span>](button.md)
* [<span data-ttu-id="d2546-120">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="d2546-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d2546-121">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="d2546-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d2546-122">Manipulación</span><span class="sxs-lookup"><span data-stu-id="d2546-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d2546-123">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="d2546-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d2546-124">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="d2546-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d2546-125">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="d2546-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d2546-126">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="d2546-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d2546-127">Teclado</span><span class="sxs-lookup"><span data-stu-id="d2546-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d2546-128">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="d2546-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d2546-129">Claqueta</span><span class="sxs-lookup"><span data-stu-id="d2546-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="d2546-130">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="d2546-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="d2546-131">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="d2546-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d2546-132">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="d2546-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d2546-133">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="d2546-133">Surface magnetism</span></span>](surface-magnetism.md)
