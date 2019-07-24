---
title: Colección de objetos
description: Colección de objetos es un control de diseño que ayuda a diseñar una matriz de objetos en una forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controles, diseño
ms.openlocfilehash: 7c3bbd82ec909b5a2e3c81f122366be564934f4d
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813891"
---
# <a name="object-collection"></a><span data-ttu-id="4c2ad-104">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="4c2ad-104">Object collection</span></span>

<span data-ttu-id="4c2ad-105">Colección de objetos es un control de diseño que ayuda a diseñar una matriz de objetos en una forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="4c2ad-106">Admite varios estilos de superficie: **plano, cilindro, esfera** y **radial**.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="4c2ad-107">Puede ajustar el radio y el tamaño de los objetos y el espacio que hay entre ellos.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="4c2ad-108">La colección de objetos admite cualquier objeto de Unity, tanto en 2D como en 3D.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="4c2ad-109">En el **[Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , hemos creado scripts de Unity y ejemplos que le ayudarán a crear una colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="4c2ad-110">![Colección de objetos utilizada en la tabla periódica de la aplicación Elements](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c2ad-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="4c2ad-111">*Ejemplos de uso de la colección de objetos*</span><span class="sxs-lookup"><span data-stu-id="4c2ad-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="4c2ad-112">Ejemplos de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="4c2ad-112">Object collection examples</span></span>

<span data-ttu-id="4c2ad-113">[La tabla periódica de los elementos](periodic-table-of-the-elements.md) es una aplicación de ejemplo que muestra cómo funciona la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="4c2ad-114">Utiliza la colección de objetos para colocar los cuadros de elementos químicos 3D en diferentes formas.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="4c2ad-115">![Ejemplos de colección de objetos que se muestran en la tabla periódica de la aplicación Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c2ad-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="4c2ad-116">*Ejemplos de colección de objetos mostrados en la tabla periódica de la aplicación de ejemplo Elements*</span><span class="sxs-lookup"><span data-stu-id="4c2ad-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="4c2ad-117">objetos 3D</span><span class="sxs-lookup"><span data-stu-id="4c2ad-117">3D objects</span></span>

<span data-ttu-id="4c2ad-118">Puede utilizar la colección de objetos para colocar los objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="4c2ad-119">En el ejemplo siguiente se muestra un plano y una distribución cilíndrica de algunos objetos de la silla 3D.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="4c2ad-120">![Ejemplos de diseños de plano y cilíndrico de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c2ad-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="4c2ad-121">*Ejemplos de diseños de plano y cilíndrico de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="4c2ad-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="4c2ad-122">objetos 2D</span><span class="sxs-lookup"><span data-stu-id="4c2ad-122">2D objects</span></span>

<span data-ttu-id="4c2ad-123">También puede usar imágenes 2D con la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="4c2ad-124">En los siguientes ejemplos se muestra cómo se pueden mostrar imágenes 2D en una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="4c2ad-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Ejemplo de imágenes 2D con colección de objetos](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="4c2ad-126">![Ejemplo de imágenes 2D con colección de objetos](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c2ad-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="4c2ad-127">*Ejemplos de uso de colecciones de objetos con imágenes 2D*</span><span class="sxs-lookup"><span data-stu-id="4c2ad-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="4c2ad-128">Vea también</span><span class="sxs-lookup"><span data-stu-id="4c2ad-128">See also</span></span>
* [<span data-ttu-id="4c2ad-129">Scripts y Prefabs para la colección de objetos en el kit de herramientas de realidad mixta en GitHub</span><span class="sxs-lookup"><span data-stu-id="4c2ad-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="4c2ad-130">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="4c2ad-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4c2ad-131">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="4c2ad-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
