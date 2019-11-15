---
title: Colección de objetos
description: Colección de objetos es un control de diseño que ayuda a diseñar una matriz de objetos en una forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controles, diseño
ms.openlocfilehash: 98fec76558502658511faf3f18d623bfa5a49dc2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106002"
---
# <a name="object-collection"></a><span data-ttu-id="8b390-104">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="8b390-104">Object collection</span></span>

![Colección de objetos utilizada en la tabla periódica de la aplicación Elements](images/UX/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="8b390-106">Colección de objetos es un control de diseño que ayuda a diseñar una matriz de objetos en una forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="8b390-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="8b390-107">Admite varios estilos de superficie: **plano, cilindro, esfera** y **radial**.</span><span class="sxs-lookup"><span data-stu-id="8b390-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="8b390-108">Puede ajustar el radio y el tamaño de los objetos y el espacio que hay entre ellos.</span><span class="sxs-lookup"><span data-stu-id="8b390-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="8b390-109">La colección de objetos admite cualquier objeto de Unity, tanto en 2D como en 3D.</span><span class="sxs-lookup"><span data-stu-id="8b390-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="8b390-110">En el **[Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , hemos creado scripts de Unity y ejemplos que le ayudarán a crear una colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="8b390-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="8b390-111">Ejemplos de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="8b390-111">Object collection examples</span></span>

<span data-ttu-id="8b390-112">[La tabla periódica de los elementos](periodic-table-of-the-elements.md) es una aplicación de ejemplo que muestra cómo funciona la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="8b390-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="8b390-113">Utiliza la colección de objetos para colocar los cuadros de elementos químicos 3D en diferentes formas.</span><span class="sxs-lookup"><span data-stu-id="8b390-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="8b390-114">![ejemplos de colección de objetos que se muestran en la tabla periódica de la aplicación Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8b390-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="8b390-115">*Ejemplos de colección de objetos mostrados en la tabla periódica de la aplicación de ejemplo Elements*</span><span class="sxs-lookup"><span data-stu-id="8b390-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="8b390-116">objetos 3D</span><span class="sxs-lookup"><span data-stu-id="8b390-116">3D objects</span></span>

<span data-ttu-id="8b390-117">Puede utilizar la colección de objetos para colocar los objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="8b390-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="8b390-118">En el ejemplo siguiente se muestra un plano y una distribución cilíndrica de algunos objetos de la silla 3D.</span><span class="sxs-lookup"><span data-stu-id="8b390-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="8b390-119">![ejemplos de diseños de plano y cilíndrico de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8b390-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="8b390-120">*Ejemplos de diseños de plano y cilíndrico de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="8b390-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="8b390-121">objetos 2D</span><span class="sxs-lookup"><span data-stu-id="8b390-121">2D objects</span></span>

<span data-ttu-id="8b390-122">También puede usar imágenes 2D con la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="8b390-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="8b390-123">En los siguientes ejemplos se muestra cómo se pueden mostrar imágenes 2D en una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="8b390-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Ejemplo de imágenes 2D con colección de objetos](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="8b390-125">![un ejemplo de imágenes 2D con colección de objetos](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="8b390-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="8b390-126">*Ejemplos de uso de colecciones de objetos con imágenes 2D*</span><span class="sxs-lookup"><span data-stu-id="8b390-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="8b390-127">Colección de objetos en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="8b390-127">Object collection in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="8b390-128">MRTK: colección de objetos</span><span class="sxs-lookup"><span data-stu-id="8b390-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="8b390-129">Consulta también</span><span class="sxs-lookup"><span data-stu-id="8b390-129">See also</span></span>

* [<span data-ttu-id="8b390-130">Cursores</span><span class="sxs-lookup"><span data-stu-id="8b390-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="8b390-131">Rayo de mano</span><span class="sxs-lookup"><span data-stu-id="8b390-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="8b390-132">Button</span><span class="sxs-lookup"><span data-stu-id="8b390-132">Button</span></span>](button.md)
* [<span data-ttu-id="8b390-133">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="8b390-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="8b390-134">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="8b390-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="8b390-135">Manipula</span><span class="sxs-lookup"><span data-stu-id="8b390-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8b390-136">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="8b390-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="8b390-137">Menú Near</span><span class="sxs-lookup"><span data-stu-id="8b390-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="8b390-138">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="8b390-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="8b390-139">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="8b390-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="8b390-140">Teclado</span><span class="sxs-lookup"><span data-stu-id="8b390-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="8b390-141">Herramienta</span><span class="sxs-lookup"><span data-stu-id="8b390-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="8b390-142">Tabletas</span><span class="sxs-lookup"><span data-stu-id="8b390-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="8b390-143">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="8b390-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="8b390-144">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="8b390-144">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="8b390-145">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="8b390-145">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="8b390-146">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="8b390-146">Surface magnetism</span></span>](surface-magnetism.md)
