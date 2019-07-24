---
title: Tabla periódica de los elementos
description: La tabla periódica de los elementos es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft, donde puede aprender a diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una colección de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525353"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="de2c5-104">Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="de2c5-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="de2c5-105">En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="de2c5-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="de2c5-106">Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.</span><span class="sxs-lookup"><span data-stu-id="de2c5-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="de2c5-107">[La tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de los laboratorios de diseño de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="de2c5-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="de2c5-108">Con este proyecto, puede obtener información sobre cómo diseñar una matriz de objetos en el espacio 3D con varios tipos de superficie mediante una **[colección de objetos](object-collection.md)** .</span><span class="sxs-lookup"><span data-stu-id="de2c5-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="de2c5-109">También aprenderá a crear objetos interactivos que respondan a entradas estándar de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="de2c5-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="de2c5-110">Puede usar los componentes de este proyecto para crear su propia experiencia de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="de2c5-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabla de puntos de la aplicación Elements](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="de2c5-112">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="de2c5-112">About the app</span></span>

<span data-ttu-id="de2c5-113">La tabla periódica de los elementos visualiza los elementos químicos y cada una de sus propiedades en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="de2c5-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="de2c5-114">Incorpora las interacciones básicas de HoloLens, como mira fijamente y el aire TAP.</span><span class="sxs-lookup"><span data-stu-id="de2c5-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="de2c5-115">Los usuarios pueden obtener información sobre los elementos con modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="de2c5-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="de2c5-116">Pueden comprender visualmente el shell de electrones de un elemento y su núcleo, que se compone de protoneladas y neutrons.</span><span class="sxs-lookup"><span data-stu-id="de2c5-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="de2c5-117">Background</span><span class="sxs-lookup"><span data-stu-id="de2c5-117">Background</span></span>

<span data-ttu-id="de2c5-118">Después de la primera vez que se experimentó HoloLens, una aplicación de tabla periódica era una idea de la que quería experimentar en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="de2c5-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="de2c5-119">Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería una buena cuestión para explorar la composición tipográfica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="de2c5-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="de2c5-120">Ser capaz de visualizar el modelo de electrones del elemento fue otra parte interesante de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="de2c5-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="de2c5-121">Diseño</span><span class="sxs-lookup"><span data-stu-id="de2c5-121">Design</span></span>

<span data-ttu-id="de2c5-122">En la vista predeterminada de la tabla periódica, se imaginan cuadros tridimensionales que contendrían el modelo de electrones de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="de2c5-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="de2c5-123">La superficie de cada cuadro sería traslúcida, de modo que el usuario podría obtener una idea aproximada del volumen del elemento.</span><span class="sxs-lookup"><span data-stu-id="de2c5-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="de2c5-124">Con fijamente y TAP, el usuario podría abrir una vista detallada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="de2c5-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="de2c5-125">Para que la transición entre la vista de tabla y la vista de detalles sea suave y natural, lo hice de manera similar a la interacción física de una caja de apertura en la vida real.</span><span class="sxs-lookup"><span data-stu-id="de2c5-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="de2c5-126">![Boceto de diseño](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="de2c5-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="de2c5-127">*Dibujos de diseño*</span><span class="sxs-lookup"><span data-stu-id="de2c5-127">*Design sketches*</span></span>

<span data-ttu-id="de2c5-128">En la vista de detalle, quería visualizar la información de cada elemento con texto representado con un gran espacio en 3D.</span><span class="sxs-lookup"><span data-stu-id="de2c5-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="de2c5-129">El modelo de electrones 3D animado se muestra en el área central y se puede ver desde distintos ángulos.</span><span class="sxs-lookup"><span data-stu-id="de2c5-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interacción](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="de2c5-131">![Prototipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="de2c5-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="de2c5-132">*Prototipos de interacción*</span><span class="sxs-lookup"><span data-stu-id="de2c5-132">*Interaction prototypes*</span></span>

<span data-ttu-id="de2c5-133">El usuario puede cambiar el tipo de superficie mediante la pulsación de los botones de la parte inferior de la tabla. puede cambiar entre plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="de2c5-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="de2c5-134">Controles comunes y patrones usados en esta aplicación</span><span class="sxs-lookup"><span data-stu-id="de2c5-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="de2c5-135">Objeto interactuable (botón)</span><span class="sxs-lookup"><span data-stu-id="de2c5-135">Interactable object (button)</span></span>

<span data-ttu-id="de2c5-136">[Objeto](interactable-object.md) interactuable es un objeto que puede responder a entradas básicas de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="de2c5-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="de2c5-137">Se proporciona como recurso prefabricado/script, que se puede aplicar fácilmente a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="de2c5-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="de2c5-138">Por ejemplo, puede hacer que una copa de café en la escena sea interactuable y responder a entradas como, por ejemplo, gestos de toque, pulsación de aire, navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="de2c5-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="de2c5-139">Más información</span><span class="sxs-lookup"><span data-stu-id="de2c5-139">Learn more</span></span>](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="de2c5-141">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="de2c5-141">Object collection</span></span>

<span data-ttu-id="de2c5-142">[Colección de objetos](object-collection.md) es un objeto que ayuda a diseñar varios objetos en varias formas.</span><span class="sxs-lookup"><span data-stu-id="de2c5-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="de2c5-143">Admite plano, cilindro, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="de2c5-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="de2c5-144">Puede configurar propiedades adicionales como RADIUS, el número de filas y el espaciado.</span><span class="sxs-lookup"><span data-stu-id="de2c5-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="de2c5-145">Más información</span><span class="sxs-lookup"><span data-stu-id="de2c5-145">Learn more</span></span>](object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="de2c5-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="de2c5-147">Fitbox</span></span>

<span data-ttu-id="de2c5-148">De forma predeterminada, los hologramas se colocarán en la ubicación donde se Gazing el usuario en el momento en que se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="de2c5-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="de2c5-149">En ocasiones, esto da lugar a resultados no deseados, como los hologramas que se colocan detrás de un muro o en el medio de una tabla.</span><span class="sxs-lookup"><span data-stu-id="de2c5-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="de2c5-150">Un fitbox permite al usuario usar miradamente para determinar la ubicación donde se colocará el holograma.</span><span class="sxs-lookup"><span data-stu-id="de2c5-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="de2c5-151">Se crea con una textura de imagen PNG simple que se puede personalizar fácilmente con sus propias imágenes o objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="de2c5-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="de2c5-153">Detalles técnicos</span><span class="sxs-lookup"><span data-stu-id="de2c5-153">Technical details</span></span>

<span data-ttu-id="de2c5-154">Puede encontrar scripts y Prefabs para la tabla periódica de la aplicación Elements en el laboratorio de diseño de la [realidad mixta de github](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="de2c5-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="de2c5-155">Ejemplos de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="de2c5-155">Application examples</span></span>

<span data-ttu-id="de2c5-156">Estas son algunas ideas sobre lo que podría crear aprovechando los componentes de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="de2c5-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="de2c5-157">Aplicación de visualización de datos bursátiles</span><span class="sxs-lookup"><span data-stu-id="de2c5-157">Stock data visualization app</span></span>

<span data-ttu-id="de2c5-158">Con los mismos controles y el mismo modelo de interacción que la tabla periódica del ejemplo de elementos, podría crear una aplicación que visualiza los datos de los mercados de acciones.</span><span class="sxs-lookup"><span data-stu-id="de2c5-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="de2c5-159">En este ejemplo se usa el control de colección de objetos para diseñar los datos bursátiles en una forma esférica.</span><span class="sxs-lookup"><span data-stu-id="de2c5-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="de2c5-160">Puede imaginarse una vista de detalle en la que se pueda mostrar información adicional sobre cada acción de forma interesante.</span><span class="sxs-lookup"><span data-stu-id="de2c5-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Ejemplo de aplicación: Finance (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Ejemplo de aplicación: Finanzas (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="de2c5-163">![Ejemplo de aplicación: Finanzas (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="de2c5-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="de2c5-164">*Un ejemplo de cómo se puede usar la colección de objetos utilizada en la tabla periódica de la aplicación de ejemplo Elements en una aplicación Finance*</span><span class="sxs-lookup"><span data-stu-id="de2c5-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="de2c5-165">Aplicación Sports</span><span class="sxs-lookup"><span data-stu-id="de2c5-165">Sports app</span></span>

<span data-ttu-id="de2c5-166">Este es un ejemplo de visualización de datos deportivos mediante la colección de objetos y otros componentes de la tabla periódica de la aplicación de ejemplo Elements.</span><span class="sxs-lookup"><span data-stu-id="de2c5-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Ejemplo de aplicación: Deportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Ejemplo de aplicación: Deportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="de2c5-169">![Ejemplo de aplicación: Deportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="de2c5-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="de2c5-170">*Un ejemplo de cómo se usa la colección de objetos en la tabla periódica de los elementos de ejemplo appcould en una aplicación Sports*</span><span class="sxs-lookup"><span data-stu-id="de2c5-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="de2c5-171">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="de2c5-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="de2c5-172"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="de2c5-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="de2c5-173">Diseñador de la experiencia del usuario@Microsoft</span><span class="sxs-lookup"><span data-stu-id="de2c5-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="de2c5-174">Vea también</span><span class="sxs-lookup"><span data-stu-id="de2c5-174">See also</span></span>

* [<span data-ttu-id="de2c5-175">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="de2c5-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="de2c5-176">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="de2c5-176">Object collection</span></span>](object-collection.md)
