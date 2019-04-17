---
title: Guía de diseño de la aplicación 3D del iniciador
description: Un iniciador de aplicaciones 3D es un objeto "físico" en casa de realidad mixta del usuario que se puede seleccionar para iniciar una aplicación.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, el iniciador de aplicaciones 3D, auriculares envolventes, live cubo
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598548"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="80850-104">Guía de diseño de la aplicación 3D del iniciador</span><span class="sxs-lookup"><span data-stu-id="80850-104">3D app launcher design guidance</span></span>

<span data-ttu-id="80850-105">Cuando se coloca en un auriculares de Windows Mixed Reality envolventes (VR), escriba Windows Mixed Reality doméstica, visualizar como una casa en un precipicio rodeado por montañas y agua (aunque puede [elegir otros entornos e incluso crear sus propios](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="80850-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="80850-106">Dentro del espacio de este inicio, un usuario tiene libertad para organizar y organizar los objetos 3D y las aplicaciones que les interesa de forma que deseen.</span><span class="sxs-lookup"><span data-stu-id="80850-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="80850-107">Un **iniciador de aplicaciones 3D** es un objeto "físico" en el usuario del mixto casa realidad que se puede seleccionar para iniciar una aplicación.</span><span class="sxs-lookup"><span data-stu-id="80850-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="80850-108">![Ejemplo: Iniciador de aplicaciones 3D de pájaro flotante](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="80850-109">*Ejemplo de iniciador una aplicación 3D Bird flotante (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="80850-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="80850-110">Proceso de creación de una aplicación 3D del iniciador</span><span class="sxs-lookup"><span data-stu-id="80850-110">3D app launcher creation process</span></span>

<span data-ttu-id="80850-111">Hay 3 pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="80850-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="80850-112">Diseñar y concepting (este artículo)</span><span class="sxs-lookup"><span data-stu-id="80850-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="80850-113">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="80850-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="80850-114">La integración en la aplicación:</span><span class="sxs-lookup"><span data-stu-id="80850-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="80850-115">Aplicaciones para UWP</span><span class="sxs-lookup"><span data-stu-id="80850-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="80850-116">Aplicaciones de Win32</span><span class="sxs-lookup"><span data-stu-id="80850-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="80850-117">Conceptos de diseño</span><span class="sxs-lookup"><span data-stu-id="80850-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="80850-118">Fantástico aún familiar</span><span class="sxs-lookup"><span data-stu-id="80850-118">Fantastic yet familiar</span></span>

<span data-ttu-id="80850-119">El iniciador de aplicaciones se encuentra en el entorno de Windows Mixed Reality es parte familiar, parte fantásticos/sci-fi.</span><span class="sxs-lookup"><span data-stu-id="80850-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="80850-120">Los iniciadores mejor seguir las reglas de este mundo.</span><span class="sxs-lookup"><span data-stu-id="80850-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="80850-121">Piense en cómo puede tomar un objeto conocido, representativo desde su aplicación, pero algunas de las reglas de realidad real de plegado.</span><span class="sxs-lookup"><span data-stu-id="80850-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="80850-122">Dará como resultado la magia.</span><span class="sxs-lookup"><span data-stu-id="80850-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="80850-123">Intuitiva</span><span class="sxs-lookup"><span data-stu-id="80850-123">Intuitive</span></span>

<span data-ttu-id="80850-124">Al examinar el iniciador de aplicaciones, su finalidad - para iniciar la aplicación - debería ser obvio y no debe causar confusiones.</span><span class="sxs-lookup"><span data-stu-id="80850-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="80850-125">Por ejemplo, asegúrese de que el iniciador es un representante de la aplicación que no se pueda confundir para una parte de la decoración de los Cliff House obvia suficientemente.</span><span class="sxs-lookup"><span data-stu-id="80850-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="80850-126">El iniciador de aplicaciones debe invitar a personas a táctil o seleccionar.</span><span class="sxs-lookup"><span data-stu-id="80850-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="80850-127">![Ejemplo: Iniciador de aplicaciones 3D de nota nueva](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="80850-128">*Ejemplo de iniciador aplicación 3D de nueva nota (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="80850-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="80850-129">Escala principal</span><span class="sxs-lookup"><span data-stu-id="80850-129">Home scale</span></span>

<span data-ttu-id="80850-130">Los iniciadores de aplicaciones 3D en vivo en el Cliff House y su tamaño predeterminado debe sentido con los demás objetos "físicos" en el espacio.</span><span class="sxs-lookup"><span data-stu-id="80850-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="80850-131">Si coloca el iniciador del lateral, por ejemplo, una planta de casa o algunos de los muebles, sentirá en casa, size-wise.</span><span class="sxs-lookup"><span data-stu-id="80850-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="80850-132">Es un buen punto de partida ver su aspecto en 30 centímetros cúbicas, pero recuerde que los usuarios pueden escalar, arriba o hacia abajo si lo desean.</span><span class="sxs-lookup"><span data-stu-id="80850-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="80850-133">El propietario puede</span><span class="sxs-lookup"><span data-stu-id="80850-133">Own-able</span></span>

<span data-ttu-id="80850-134">El iniciador de aplicaciones debería sentir como un objeto de una persona sería encantada de tener en su espacio.</span><span class="sxs-lookup"><span data-stu-id="80850-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="80850-135">Deberá ser prácticamente rodeando de estas cosas, por lo que el iniciador debe parecer algo la idea del usuario era lo suficientemente recomendable buscan y mantener cercanos.</span><span class="sxs-lookup"><span data-stu-id="80850-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="80850-136">![Ejemplo: Iniciador de aplicaciones 3D de Astro Warp](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="80850-137">*Ejemplo del iniciador de aplicaciones 3D Astro Warp (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="80850-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="80850-138">Recognizable</span><span class="sxs-lookup"><span data-stu-id="80850-138">Recognizable</span></span>

<span data-ttu-id="80850-139">El iniciador de aplicaciones 3D al instante debe expresar "marca de la aplicación" a las personas que lo ven.</span><span class="sxs-lookup"><span data-stu-id="80850-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="80850-140">Si tiene un carácter de estrella o un objeto especialmente identificable en su aplicación, se recomienda usar como una parte importante de su diseño.</span><span class="sxs-lookup"><span data-stu-id="80850-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="80850-141">En un mundo de realidad mixta, un objeto dibujará más interés de los usuarios que solo un logotipo por sí solo.</span><span class="sxs-lookup"><span data-stu-id="80850-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="80850-142">Objetos reconocibles comunican marca rápidamente y con claridad.</span><span class="sxs-lookup"><span data-stu-id="80850-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="80850-143">Volumétricos</span><span class="sxs-lookup"><span data-stu-id="80850-143">Volumetric</span></span>

<span data-ttu-id="80850-144">La aplicación merece algo más que colocar su logotipo en un plano sin formato y dejarlo.</span><span class="sxs-lookup"><span data-stu-id="80850-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="80850-145">El iniciador debe sentirse como un objeto emocionante, 3D, físico en el espacio del usuario.</span><span class="sxs-lookup"><span data-stu-id="80850-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="80850-146">Un buen enfoque es imaginar que la aplicación se va a tener un globo en desfile de día de acción de gracias el Macy.</span><span class="sxs-lookup"><span data-stu-id="80850-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="80850-147">Hágase, ¿cuál sería realmente wow personas como proceden calle abajo?</span><span class="sxs-lookup"><span data-stu-id="80850-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="80850-148">¿Cuál tendría el aspecto excelente en todos los ángulos de visión?</span><span class="sxs-lookup"><span data-stu-id="80850-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="80850-149">Sugerencias para buenos modelos 3D</span><span class="sxs-lookup"><span data-stu-id="80850-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="80850-150">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="80850-150">Best practices</span></span>
* <span data-ttu-id="80850-151">Al planear las dimensiones para el iniciador de aplicaciones, merece la pena aspirar aproximadamente un cubo de 30cm.</span><span class="sxs-lookup"><span data-stu-id="80850-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="80850-152">Por lo tanto, un 1: proporción de tamaño de 1:1.</span><span class="sxs-lookup"><span data-stu-id="80850-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="80850-153">Los modelos deben ser menos de 10 000 polígonos.</span><span class="sxs-lookup"><span data-stu-id="80850-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="80850-154">Más información sobre recuentos de triángulo y niveles de detalles (LODs)</span><span class="sxs-lookup"><span data-stu-id="80850-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="80850-155">Probar en un auricular envolvente cuando sea posible.</span><span class="sxs-lookup"><span data-stu-id="80850-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="80850-156">Detalles de la compilación en la geometría de su modelo siempre que sea posible: no se basan en las texturas para obtener información detallada.</span><span class="sxs-lookup"><span data-stu-id="80850-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="80850-157">Crear geometría "agua estrecha" cerrado.</span><span class="sxs-lookup"><span data-stu-id="80850-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="80850-158">No hay huecos que no se modelan en.</span><span class="sxs-lookup"><span data-stu-id="80850-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="80850-159">Utilizar materiales naturales en el objeto.</span><span class="sxs-lookup"><span data-stu-id="80850-159">Use natural materials in your object.</span></span> <span data-ttu-id="80850-160">Imagine diseñar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="80850-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="80850-161">Asegúrese de que el modelo se lee correctamente en los tamaños y distancias.</span><span class="sxs-lookup"><span data-stu-id="80850-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="80850-162">Cuando el modelo está preparado para comenzar, lea el [exportar directrices activos](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="80850-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="80850-163">![El modelo con detalles sutiles en la textura](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="80850-164">*El modelo con detalles sutiles en la textura*</span><span class="sxs-lookup"><span data-stu-id="80850-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="80850-165">Lo que debe evitar</span><span class="sxs-lookup"><span data-stu-id="80850-165">What to avoid</span></span>
* <span data-ttu-id="80850-166">No utilice los detalles de alto contraste o patrones pequeño, ocupados y texturas.</span><span class="sxs-lookup"><span data-stu-id="80850-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="80850-167">No use fino geometría: no funcionan bien a una distancia y le alias incorrecto.</span><span class="sxs-lookup"><span data-stu-id="80850-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="80850-168">No se permiten elementos del modelo ampliar mucho más allá de la 1: proporción de tamaño de 1:1.</span><span class="sxs-lookup"><span data-stu-id="80850-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="80850-169">Crea problemas de escalado.</span><span class="sxs-lookup"><span data-stu-id="80850-169">It will create scaling problems.</span></span>

<span data-ttu-id="80850-170">![Evitar pequeñas, de alto contraste patrones ocupados](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="80850-171">*Evitar los patrones de alto contraste, pequeño, ocupados*</span><span class="sxs-lookup"><span data-stu-id="80850-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="80850-172">Cómo controlar el tipo</span><span class="sxs-lookup"><span data-stu-id="80850-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="80850-173">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="80850-173">Best practices</span></span>
* <span data-ttu-id="80850-174">Se recomienda que el tipo consta de aproximadamente 1/3 de su iniciador de aplicaciones (o más).</span><span class="sxs-lookup"><span data-stu-id="80850-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="80850-175">El tipo es lo más importante que ofrece una idea de que el iniciador es, de hecho, un selector, por lo que es bueno si resulta bastante considerable a las personas.</span><span class="sxs-lookup"><span data-stu-id="80850-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="80850-176">Evitar la realización de tipo muy amplia: intenta que esté dentro de los confines de los iniciadores de aplicaciones de dimensiones principal (más o menos).</span><span class="sxs-lookup"><span data-stu-id="80850-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="80850-177">Tipo sin formato puede funcionar, pero tenga en cuenta que puede ser difícil ver desde determinadas ángulos y en algunos entornos.</span><span class="sxs-lookup"><span data-stu-id="80850-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="80850-178">Considere la posibilidad de colocarlo en un objeto sólido o telón de fondo detrás de él para ayudar con esto.</span><span class="sxs-lookup"><span data-stu-id="80850-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="80850-179">Agregar dimensión a su tipo se siente bien en 3D.</span><span class="sxs-lookup"><span data-stu-id="80850-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="80850-180">Los lados del tipo de sombreado un color diferente y más oscuro puede ayudar a mejorar la legibilidad.</span><span class="sxs-lookup"><span data-stu-id="80850-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="80850-181">**Colores de tipo que funcionan**</span><span class="sxs-lookup"><span data-stu-id="80850-181">**Type colors that work**</span></span>
* <span data-ttu-id="80850-182">Blanco</span><span class="sxs-lookup"><span data-stu-id="80850-182">White</span></span>
* <span data-ttu-id="80850-183">Negro</span><span class="sxs-lookup"><span data-stu-id="80850-183">Black</span></span>
* <span data-ttu-id="80850-184">Color brillante de saturados parcial</span><span class="sxs-lookup"><span data-stu-id="80850-184">Bright semi-saturated color</span></span>

<span data-ttu-id="80850-185">![Escriba los colores que funcionan.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="80850-186">*Colores de tipo que funcionan*</span><span class="sxs-lookup"><span data-stu-id="80850-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="80850-187">Lo que debe evitar</span><span class="sxs-lookup"><span data-stu-id="80850-187">What to avoid</span></span>

<span data-ttu-id="80850-188">**Colores de tipo que causan problemas**</span><span class="sxs-lookup"><span data-stu-id="80850-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="80850-189">Semitonos</span><span class="sxs-lookup"><span data-stu-id="80850-189">Mid-tones</span></span>
* <span data-ttu-id="80850-190">Gris</span><span class="sxs-lookup"><span data-stu-id="80850-190">Gray</span></span>
* <span data-ttu-id="80850-191">Exceso saturados colores o colores desaturados</span><span class="sxs-lookup"><span data-stu-id="80850-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="80850-192">![Escriba los colores que provocan problemas.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="80850-193">*Colores de tipo que causan problemas*</span><span class="sxs-lookup"><span data-stu-id="80850-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="80850-194">Iluminación</span><span class="sxs-lookup"><span data-stu-id="80850-194">Lighting</span></span>

<span data-ttu-id="80850-195">La iluminación para su iniciador de aplicaciones procedentes del entorno de Cliff House.</span><span class="sxs-lookup"><span data-stu-id="80850-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="80850-196">No olvide probar el iniciador en varios lugares de la casa por lo que se ve bien en claro y sombras.</span><span class="sxs-lookup"><span data-stu-id="80850-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="80850-197">La buena noticia es que, si ha seguido la Guía de diseño otros en este documento, el iniciador debe estar en forma bastante bueno para la mayoría de iluminación en el Cliff House.</span><span class="sxs-lookup"><span data-stu-id="80850-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="80850-198">Buenos lugares para probar cómo se ve el iniciador en las diversas luces en el entorno son el estudio, la sala de medios, fuera de cualquier lugar y en el Patio atrás (el área concreto con el césped).</span><span class="sxs-lookup"><span data-stu-id="80850-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="80850-199">Otra buena prueba es colocarlo en la mitad de luz y sombra mitad y ver su aspecto.</span><span class="sxs-lookup"><span data-stu-id="80850-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="80850-200">![Asegúrese de que el iniciador se ve bien en claro y sombras.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="80850-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="80850-201">*Asegúrese de que el iniciador se ve bien en claro y sombras*</span><span class="sxs-lookup"><span data-stu-id="80850-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="80850-202">Las texturas</span><span class="sxs-lookup"><span data-stu-id="80850-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="80850-203">Las texturas de creación</span><span class="sxs-lookup"><span data-stu-id="80850-203">Authoring your textures</span></span>

<span data-ttu-id="80850-204">El formato de final de su iniciador de aplicaciones 3D será un archivo .glb, que se realiza mediante la canalización PBR (físicamente en función de representación).</span><span class="sxs-lookup"><span data-stu-id="80850-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="80850-205">Esto puede ser un proceso complicado, ahora es un buen momento para emplear un artista técnico si no lo ha hecho ya.</span><span class="sxs-lookup"><span data-stu-id="80850-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="80850-206">Si eres un feliz implementación personal-er, dedicar tiempo a [investigar y obtenga información sobre terminología PBR](http://wiki.polycount.com/wiki/PBR) y lo que sucede en segundo plano antes de comenzar le ayudará a evitar errores comunes.</span><span class="sxs-lookup"><span data-stu-id="80850-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="80850-207">![Ejemplo: Aplicación de una nota nueva](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="80850-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="80850-208">*Ejemplo de iniciador aplicación 3D de nueva nota (aplicación ficticia)*</span><span class="sxs-lookup"><span data-stu-id="80850-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="80850-209">**Recomienda la herramienta de creación**</span><span class="sxs-lookup"><span data-stu-id="80850-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="80850-210">Se recomienda usar [sustancia pintor](https://www.allegorithmic.com/products/substance-painter) por Allegorithmic para crear el archivo final.</span><span class="sxs-lookup"><span data-stu-id="80850-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="80850-211">Si no está familiarizado con la creación de sombreadores PBR en sustancia pintor, aquí un [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="80850-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="80850-212">(O bien [3D Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), o [Marmoset Toolbag](https://www.marmoset.co/toolbag/) también funcionaría si está más familiarizado con uno de ellos.)</span><span class="sxs-lookup"><span data-stu-id="80850-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="80850-213">Procedimiento recomendado</span><span class="sxs-lookup"><span data-stu-id="80850-213">Best practices</span></span>

* <span data-ttu-id="80850-214">Si el objeto de selector de aplicación se creó para PBR, debe ser bastante sencillo convertirlo para el entorno Cliff House.</span><span class="sxs-lookup"><span data-stu-id="80850-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="80850-215">Nuestro sombreador espera un flujo de trabajo de rugosidad/sin sistema operativo: sombreador PBR Unreal el es un facsímil cerrar.</span><span class="sxs-lookup"><span data-stu-id="80850-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="80850-216">Al exportar las texturas, tenga la [textura tamaños recomendados](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) en mente.</span><span class="sxs-lookup"><span data-stu-id="80850-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="80850-217">Asegúrese de crear los objetos de la iluminación en tiempo real, esto significa que:</span><span class="sxs-lookup"><span data-stu-id="80850-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="80850-218">Evitar sombras al horno – o pintadas sombras</span><span class="sxs-lookup"><span data-stu-id="80850-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="80850-219">Evitar la iluminación al horno de las texturas</span><span class="sxs-lookup"><span data-stu-id="80850-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="80850-220">Use uno de los materiales PBR creación de paquetes para obtener los mapas derechos generados para nuestro sombreador de</span><span class="sxs-lookup"><span data-stu-id="80850-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="80850-221">Vea también</span><span class="sxs-lookup"><span data-stu-id="80850-221">See also</span></span>

* [<span data-ttu-id="80850-222">Crear modelos 3D para su uso en la realidad mixta principal</span><span class="sxs-lookup"><span data-stu-id="80850-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="80850-223">Implementar los iniciadores de aplicaciones 3D (aplicaciones UWP)</span><span class="sxs-lookup"><span data-stu-id="80850-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="80850-224">Implementar los iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="80850-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
