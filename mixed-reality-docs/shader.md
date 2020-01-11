---
title: Sombreador
description: El sombreador estándar de MRTK proporciona varios tipos de efectos visuales que se pueden usar con hologramas.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realidad mixta, controles, interacción, IU, experiencia de usuario
ms.openlocfilehash: 8d0e01bb26347d95a80703884c4e9408653e03ed
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901456"
---
# <a name="shader"></a><span data-ttu-id="7d60d-104">Sombreador</span><span class="sxs-lookup"><span data-stu-id="7d60d-104">Shader</span></span>

![Sombreador](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="7d60d-106">Dado que los objetos holográficas se mezclan con los físicos en el entorno real, es importante proporcionar indicaciones visuales al usuario.</span><span class="sxs-lookup"><span data-stu-id="7d60d-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="7d60d-107">El sombreador estándar de MRTK proporciona varios tipos de efectos visuales que se pueden usar con hologramas.</span><span class="sxs-lookup"><span data-stu-id="7d60d-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="7d60d-108">El sistema de sombreado estándar de MRTK emplea un sombreador único y flexible que puede lograr objetos visuales similares al sombreador estándar de Unity, implementa [principios del sistema de diseño fluida](https://www.microsoft.com/design/fluent/#/)y sigue teniendo el rendimiento de los dispositivos de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="7d60d-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="7d60d-109">Ejemplos de efectos visuales con el sombreador estándar de MRTK</span><span class="sxs-lookup"><span data-stu-id="7d60d-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="7d60d-110">![Mover](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d60d-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="7d60d-111">**Luz de proximidad**</span><span class="sxs-lookup"><span data-stu-id="7d60d-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7d60d-112">![Girar](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="7d60d-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="7d60d-113">**Borde claro**</span><span class="sxs-lookup"><span data-stu-id="7d60d-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="7d60d-114">Sombreador estándar de MRTK en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="7d60d-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="7d60d-115">MRTK: sombreador estándar</span><span class="sxs-lookup"><span data-stu-id="7d60d-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="7d60d-116">Consulta también</span><span class="sxs-lookup"><span data-stu-id="7d60d-116">See also</span></span>

* [<span data-ttu-id="7d60d-117">Cursores</span><span class="sxs-lookup"><span data-stu-id="7d60d-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7d60d-118">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="7d60d-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="7d60d-119">Button</span><span class="sxs-lookup"><span data-stu-id="7d60d-119">Button</span></span>](button.md)
* [<span data-ttu-id="7d60d-120">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="7d60d-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="7d60d-121">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="7d60d-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="7d60d-122">Manipulación</span><span class="sxs-lookup"><span data-stu-id="7d60d-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7d60d-123">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="7d60d-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="7d60d-124">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="7d60d-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="7d60d-125">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="7d60d-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="7d60d-126">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="7d60d-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="7d60d-127">Teclado</span><span class="sxs-lookup"><span data-stu-id="7d60d-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="7d60d-128">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="7d60d-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="7d60d-129">Claqueta</span><span class="sxs-lookup"><span data-stu-id="7d60d-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="7d60d-130">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="7d60d-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="7d60d-131">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="7d60d-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="7d60d-132">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="7d60d-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="7d60d-133">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="7d60d-133">Surface magnetism</span></span>](surface-magnetism.md)
