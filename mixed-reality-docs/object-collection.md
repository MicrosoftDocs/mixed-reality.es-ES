---
title: Colección de objetos
description: Colección de objetos es un control de diseño que ayuda a diseñar una matriz de objetos en una forma tridimensional predefinida.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controles, diseño
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438171"
---
# <a name="object-collection"></a><span data-ttu-id="ad95f-104">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="ad95f-104">Object collection</span></span>

![Colección de objetos utilizada en la tabla periódica de la aplicación Elements](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="ad95f-106">Colección de objetos es un control de diseño que ayuda a diseñar una matriz de objetos en una forma tridimensional predefinida.</span><span class="sxs-lookup"><span data-stu-id="ad95f-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="ad95f-107">Admite varios estilos de superficie: **plano, cilindro, esfera** y **radial**.</span><span class="sxs-lookup"><span data-stu-id="ad95f-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="ad95f-108">Puede ajustar el radio y el tamaño de los objetos y el espacio que hay entre ellos.</span><span class="sxs-lookup"><span data-stu-id="ad95f-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="ad95f-109">La colección de objetos admite cualquier objeto de Unity, tanto en 2D como en 3D.</span><span class="sxs-lookup"><span data-stu-id="ad95f-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="ad95f-110">En el **[Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , hemos creado scripts de Unity y ejemplos que le ayudarán a crear una colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="ad95f-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="ad95f-111">Ejemplos de colección de objetos</span><span class="sxs-lookup"><span data-stu-id="ad95f-111">Object collection examples</span></span>

<span data-ttu-id="ad95f-112">[La tabla periódica de los elementos](periodic-table-of-the-elements.md) es una aplicación de ejemplo que muestra cómo funciona la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="ad95f-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="ad95f-113">Utiliza la colección de objetos para colocar los cuadros de elementos químicos 3D en diferentes formas.</span><span class="sxs-lookup"><span data-stu-id="ad95f-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="ad95f-114">![ejemplos de colección de objetos que se muestran en la tabla periódica de la aplicación Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ad95f-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="ad95f-115">*Ejemplos de colección de objetos mostrados en la tabla periódica de la aplicación de ejemplo Elements*</span><span class="sxs-lookup"><span data-stu-id="ad95f-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="ad95f-116">objetos 3D</span><span class="sxs-lookup"><span data-stu-id="ad95f-116">3D objects</span></span>

<span data-ttu-id="ad95f-117">Puede utilizar la colección de objetos para colocar los objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="ad95f-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="ad95f-118">En el ejemplo siguiente se muestra un plano y una distribución cilíndrica de algunos objetos de la silla 3D.</span><span class="sxs-lookup"><span data-stu-id="ad95f-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="ad95f-119">![ejemplos de diseños de plano y cilíndrico de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ad95f-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="ad95f-120">*Ejemplos de diseños de plano y cilíndrico de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="ad95f-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="ad95f-121">objetos 2D</span><span class="sxs-lookup"><span data-stu-id="ad95f-121">2D objects</span></span>

<span data-ttu-id="ad95f-122">También puede usar imágenes 2D con la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="ad95f-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="ad95f-123">En los siguientes ejemplos se muestra cómo se pueden mostrar imágenes 2D en una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="ad95f-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Ejemplo de imágenes 2D con colección de objetos](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="ad95f-125">![un ejemplo de imágenes 2D con colección de objetos](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="ad95f-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="ad95f-126">*Ejemplos de uso de colecciones de objetos con imágenes 2D*</span><span class="sxs-lookup"><span data-stu-id="ad95f-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="ad95f-127">Consulta también</span><span class="sxs-lookup"><span data-stu-id="ad95f-127">See also</span></span>
* [<span data-ttu-id="ad95f-128">Scripts y Prefabs para la colección de objetos en el kit de herramientas de realidad mixta en GitHub</span><span class="sxs-lookup"><span data-stu-id="ad95f-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="ad95f-129">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="ad95f-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ad95f-130">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="ad95f-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
