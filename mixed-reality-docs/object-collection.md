---
title: Colección de objetos
description: Colección de objetos es un control de diseño que le permite disponer de una matriz de objetos en una forma 3D predefinida.
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
# <a name="object-collection"></a><span data-ttu-id="710d3-104">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="710d3-104">Object collection</span></span>

<span data-ttu-id="710d3-105">Colección de objetos es un control de diseño que le permite disponer de una matriz de objetos en una forma 3D predefinida.</span><span class="sxs-lookup"><span data-stu-id="710d3-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="710d3-106">Admite diversos estilos de superficie - **plano, cilindro, esfera** y **radial**.</span><span class="sxs-lookup"><span data-stu-id="710d3-106">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="710d3-107">Puede ajustar el radio y el tamaño de los objetos y el espacio entre ellos.</span><span class="sxs-lookup"><span data-stu-id="710d3-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="710d3-108">Colección de objetos es compatible con cualquier objeto desde Unity - 2D y 3D.</span><span class="sxs-lookup"><span data-stu-id="710d3-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="710d3-109">En el  **[Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** , hemos creado el script de Unity y ejemplos que le ayudarán a crean una colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="710d3-109">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

<span data-ttu-id="710d3-110">![Colección de objetos usado en la tabla periódico de la aplicación de elementos](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="710d3-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="710d3-111">*Ejemplos del uso de la colección de objetos*</span><span class="sxs-lookup"><span data-stu-id="710d3-111">*Examples of using object collection*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="710d3-112">Ejemplos de la colección de objetos</span><span class="sxs-lookup"><span data-stu-id="710d3-112">Object collection examples</span></span>

<span data-ttu-id="710d3-113">[Tabla periódica de los elementos](periodic-table-of-the-elements.md) es una aplicación de ejemplo que muestra cómo funciona la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="710d3-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="710d3-114">Colección de objetos utiliza para diseñar los cuadros de elemento químico 3D en formas diferentes.</span><span class="sxs-lookup"><span data-stu-id="710d3-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="710d3-115">![Ejemplos de colección de objetos que se muestra en la tabla periódico de la aplicación de elementos](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="710d3-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="710d3-116">*Ejemplos de colección de objetos que se muestra en la tabla periódico de la aplicación de ejemplo de elementos*</span><span class="sxs-lookup"><span data-stu-id="710d3-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="710d3-117">Objetos 3D</span><span class="sxs-lookup"><span data-stu-id="710d3-117">3D objects</span></span>

<span data-ttu-id="710d3-118">Puede usar la colección de objetos para diseñar objetos 3D importados.</span><span class="sxs-lookup"><span data-stu-id="710d3-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="710d3-119">El ejemplo siguiente muestra un plano y un diseño de cilindro de algunos objetos 3D silla.</span><span class="sxs-lookup"><span data-stu-id="710d3-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="710d3-120">![Ejemplos de plano y los diseños cilíndricos de objetos 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="710d3-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="710d3-121">*Ejemplos de plano y los diseños cilíndricos de objetos 3D*</span><span class="sxs-lookup"><span data-stu-id="710d3-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="710d3-122">Objetos 2D</span><span class="sxs-lookup"><span data-stu-id="710d3-122">2D objects</span></span>

<span data-ttu-id="710d3-123">También puede usar imágenes en 2D con la colección de objetos.</span><span class="sxs-lookup"><span data-stu-id="710d3-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="710d3-124">Los ejemplos siguientes muestran cómo 2D imágenes se pueden mostrar en una cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="710d3-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Un ejemplo de imágenes en 2D con la colección de objetos](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="710d3-126">![Un ejemplo de imágenes en 2D con la colección de objetos](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="710d3-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="710d3-127">*Ejemplos del uso de colección de objetos con imágenes en 2D*</span><span class="sxs-lookup"><span data-stu-id="710d3-127">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="710d3-128">Vea también</span><span class="sxs-lookup"><span data-stu-id="710d3-128">See also</span></span>
* [<span data-ttu-id="710d3-129">Secuencias de comandos y prefabricados para la colección de objetos en el Kit de herramientas de realidad mixta en GitHub</span><span class="sxs-lookup"><span data-stu-id="710d3-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="710d3-130">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="710d3-130">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="710d3-131">Cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="710d3-131">Bounding Box</span></span>](app-bar-and-bounding-box.md)
