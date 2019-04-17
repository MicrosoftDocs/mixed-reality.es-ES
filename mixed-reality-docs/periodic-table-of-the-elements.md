---
title: Tabla periódica de los elementos
description: Tabla periódica de los elementos es una aplicación de ejemplo de código abierto de laboratorios de Microsoft Mixed Reality diseño donde puede aprender a diseñar una matriz de objetos en el espacio 3D con distintos tipos de superficie mediante una colección de objetos.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, la aplicación de ejemplo, los controles
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605581"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="d99ce-104">Tabla periódica de los elementos</span><span class="sxs-lookup"><span data-stu-id="d99ce-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="d99ce-105">Este artículo describe un ejemplo de exploración que hemos creado en el [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde se comparten la información que recabemos sobre y sugerencias para mezclan el desarrollo de aplicaciones de realidad.</span><span class="sxs-lookup"><span data-stu-id="d99ce-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="d99ce-106">Nuestros artículos relacionados con el diseño y código evolucionará a medida que introducimos nuevos descubrimientos.</span><span class="sxs-lookup"><span data-stu-id="d99ce-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="d99ce-107">[Tabla periódica de los elementos](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto de laboratorios de diseño de realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d99ce-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="d99ce-108">Con este proyecto, puede aprender a diseñar una matriz de objetos en el espacio 3D con distintos tipos de superficie mediante un  **[colección de objetos](object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="d99ce-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="d99ce-109">También aprenderá a crear objetos interactuable que responden a entradas estándares de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d99ce-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="d99ce-110">Puede usar los componentes de este proyecto para crear sus propios mixto experiencia de realidad la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d99ce-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Tabla de períodos de la aplicación de elementos](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="d99ce-112">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="d99ce-112">About the app</span></span>

<span data-ttu-id="d99ce-113">Tabla periódica de los elementos se visualizan los elementos químicos y cada uno de sus propiedades en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="d99ce-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="d99ce-114">Incorpora las interacciones básicas de HoloLens como tap mirada y air.</span><span class="sxs-lookup"><span data-stu-id="d99ce-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="d99ce-115">Los usuarios pueden obtener información acerca de los elementos con modelos 3D animados.</span><span class="sxs-lookup"><span data-stu-id="d99ce-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="d99ce-116">Shell de electron que un elemento y su núcleo - que se compone de protons y neutrones puedan entender visualmente.</span><span class="sxs-lookup"><span data-stu-id="d99ce-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="d99ce-117">Background</span><span class="sxs-lookup"><span data-stu-id="d99ce-117">Background</span></span>

<span data-ttu-id="d99ce-118">Una vez que experimentó en primer lugar HoloLens, una aplicación de table periódico era una idea que sabía que quería experimenten en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d99ce-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="d99ce-119">Puesto que cada elemento tiene muchos puntos de datos que se muestran con texto, pensé que sería excelente en la materia para explorar la composición tipográfica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="d99ce-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="d99ce-120">Poder visualizar el modelo del elemento electron fue otra parte interesante de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="d99ce-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="d99ce-121">Diseño</span><span class="sxs-lookup"><span data-stu-id="d99ce-121">Design</span></span>

<span data-ttu-id="d99ce-122">Para la vista predeterminada de la tabla periódico, imaginó cuadros tridimensionales que contengan el modelo de electrones de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="d99ce-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="d99ce-123">La superficie de cada cuadro sería translúcida para que el usuario podría obtener una idea aproximada del volumen del elemento.</span><span class="sxs-lookup"><span data-stu-id="d99ce-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="d99ce-124">Con solo pulsar mirada y aire, el usuario pudo abrir una vista detallada de cada elemento.</span><span class="sxs-lookup"><span data-stu-id="d99ce-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="d99ce-125">Para realizar la transición entre la vista de tabla y vista de detalle suave y natural, he realizado similar a la interacción física de un cuadro de apertura en la vida real.</span><span class="sxs-lookup"><span data-stu-id="d99ce-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="d99ce-126">![Boceto de diseño](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="d99ce-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="d99ce-127">*Bocetos de diseño*</span><span class="sxs-lookup"><span data-stu-id="d99ce-127">*Design sketches*</span></span>

<span data-ttu-id="d99ce-128">En la vista de detalle, quiero visualizar la información de cada elemento con el texto representado perfectamente en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="d99ce-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="d99ce-129">El modelo de electrones 3D animadas se muestra en el área central y puede verse desde distintos ángulos.</span><span class="sxs-lookup"><span data-stu-id="d99ce-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interacción](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="d99ce-131">![Prototipos](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="d99ce-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="d99ce-132">*Prototipos de interacción*</span><span class="sxs-lookup"><span data-stu-id="d99ce-132">*Interaction prototypes*</span></span>

<span data-ttu-id="d99ce-133">El usuario puede cambiar el tipo de superficie por aire pulsando en los botones de la parte inferior de la tabla, puede cambiar entre el plano de cilindros, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="d99ce-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="d99ce-134">Patrones que se usan en esta aplicación y los controles comunes</span><span class="sxs-lookup"><span data-stu-id="d99ce-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="d99ce-135">Objeto interactuable (botón)</span><span class="sxs-lookup"><span data-stu-id="d99ce-135">Interactable object (button)</span></span>

<span data-ttu-id="d99ce-136">[Objeto interactuable](interactable-object.md) es un objeto que puede responder a entradas básicas de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d99ce-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="d99ce-137">Se proporciona como un recurso prefabricado/script que se puede aplicar fácilmente a cualquier objeto.</span><span class="sxs-lookup"><span data-stu-id="d99ce-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="d99ce-138">Por ejemplo, puede realizar una taza de café en su escena interactuable y responder a entradas, como la mirada, en el aire, gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="d99ce-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="d99ce-139">Más información</span><span class="sxs-lookup"><span data-stu-id="d99ce-139">Learn more</span></span>](interactable-object.md)

![objeto nteractable](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="d99ce-141">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="d99ce-141">Object collection</span></span>

<span data-ttu-id="d99ce-142">[Colección de objetos](object-collection.md) es un objeto que ayuda a diseñar varios objetos en varias formas.</span><span class="sxs-lookup"><span data-stu-id="d99ce-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="d99ce-143">Admite el plano de cilindros, esfera y dispersión.</span><span class="sxs-lookup"><span data-stu-id="d99ce-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="d99ce-144">Puede configurar propiedades adicionales, como el radio, el número de filas y el espaciado.</span><span class="sxs-lookup"><span data-stu-id="d99ce-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="d99ce-145">Más información</span><span class="sxs-lookup"><span data-stu-id="d99ce-145">Learn more</span></span>](object-collection.md)

![Colección de objetos](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="d99ce-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="d99ce-147">Fitbox</span></span>

<span data-ttu-id="d99ce-148">De forma predeterminada, hologramas se colocarán en la ubicación donde se gazing el usuario en el momento en que se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d99ce-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="d99ce-149">A veces, esto conduce a resultados no deseados como hologramas colocadas detrás de una pared o en medio de una tabla.</span><span class="sxs-lookup"><span data-stu-id="d99ce-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="d99ce-150">Un fitbox permite al usuario utilizar a mirada para determinar la ubicación donde se colocará el holograma.</span><span class="sxs-lookup"><span data-stu-id="d99ce-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="d99ce-151">Se realiza con una textura de imagen PNG simple que se puede personalizar fácilmente con sus propias imágenes o los objetos 3D.</span><span class="sxs-lookup"><span data-stu-id="d99ce-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="d99ce-153">Detalles técnicos</span><span class="sxs-lookup"><span data-stu-id="d99ce-153">Technical details</span></span>

<span data-ttu-id="d99ce-154">Puede encontrar prefabricados y secuencias de comandos para la tabla periódico de la aplicación de los elementos en el [GitHub de laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="d99ce-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="d99ce-155">Ejemplos de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="d99ce-155">Application examples</span></span>

<span data-ttu-id="d99ce-156">Presentamos algunas ideas sobre lo que puede crear mediante el aprovechamiento de los componentes de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="d99ce-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="d99ce-157">Aplicación de visualización de datos de acciones</span><span class="sxs-lookup"><span data-stu-id="d99ce-157">Stock data visualization app</span></span>

<span data-ttu-id="d99ce-158">Con los mismos controles y el modelo de interacción que la tabla periódico de la muestra de los elementos, podría crear una aplicación que visualiza los datos del mercado.</span><span class="sxs-lookup"><span data-stu-id="d99ce-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="d99ce-159">En este ejemplo se usa el control de la colección de objetos para disponer de datos de acciones en una forma esférica.</span><span class="sxs-lookup"><span data-stu-id="d99ce-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="d99ce-160">Puede imaginar una vista de detalle donde podría mostrarse información adicional sobre cada acción de una forma interesante.</span><span class="sxs-lookup"><span data-stu-id="d99ce-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Ejemplo de aplicación: Finanzas (1 de 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Ejemplo de aplicación: Finanzas (2 de 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="d99ce-163">![Ejemplo de aplicación: Finanzas (3 de 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="d99ce-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="d99ce-164">*Un ejemplo de cómo se podría usar la colección de objetos usada en la tabla periódico de la aplicación de ejemplo de los elementos en una aplicación de finanzas*</span><span class="sxs-lookup"><span data-stu-id="d99ce-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="d99ce-165">Aplicación de deportes</span><span class="sxs-lookup"><span data-stu-id="d99ce-165">Sports app</span></span>

<span data-ttu-id="d99ce-166">Este es un ejemplo de visualización de datos deportivos mediante la colección de objetos y otros componentes de la tabla periódico de la aplicación de ejemplo de elementos.</span><span class="sxs-lookup"><span data-stu-id="d99ce-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Ejemplo de aplicación: Deportes (1 de 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Ejemplo de aplicación: Deportes (2 de 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="d99ce-169">![Ejemplo de aplicación: Deportes (3 de 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="d99ce-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="d99ce-170">*Un ejemplo de cómo usa la colección de objetos en la tabla periódico de la appcould de ejemplo de los elementos se usan en una aplicación de deportes*</span><span class="sxs-lookup"><span data-stu-id="d99ce-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d99ce-171">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="d99ce-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d99ce-172"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="d99ce-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d99ce-173">Diseñador UX @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d99ce-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d99ce-174">Vea también</span><span class="sxs-lookup"><span data-stu-id="d99ce-174">See also</span></span>

* [<span data-ttu-id="d99ce-175">Objeto interactuable</span><span class="sxs-lookup"><span data-stu-id="d99ce-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d99ce-176">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="d99ce-176">Object collection</span></span>](object-collection.md)
