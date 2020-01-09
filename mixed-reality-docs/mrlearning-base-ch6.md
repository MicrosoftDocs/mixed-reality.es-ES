---
title: 'Tutoriales de introducción: 7. Crear una aplicación de ejemplo de módulo lunar'
description: En esta lección, combinará varios conceptos aprendidos en lecciones anteriores para crear una experiencia de ejemplo única.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3127ffceea08202fe9d978ad77f8fddb6fba60a3
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334378"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="ef46a-105">7. crear una aplicación de ejemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="ef46a-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="ef46a-106">En este tutorial, se combinan varios conceptos de lecciones anteriores para crear una experiencia de ejemplo única.</span><span class="sxs-lookup"><span data-stu-id="ef46a-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="ef46a-107">Aprenderá a crear una aplicación de ensamblado de módulo lunar en la que un usuario necesita usar manos con seguimiento para recoger los elementos del módulo lunar e intentar ensamblar un módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="ef46a-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="ef46a-108">Usamos botones que se utilizan para alternar las sugerencias de colocación, restablecer nuestra experiencia y lanzar el módulo lunar en el espacio.</span><span class="sxs-lookup"><span data-stu-id="ef46a-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="ef46a-109">En los tutoriales futuros, se seguirá generando a partir de esta experiencia, que incluye eficaces casos de uso de varios usuarios que aprovechan los delimitadores espaciales de Azure para la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="ef46a-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="ef46a-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ef46a-110">Objectives</span></span>

- <span data-ttu-id="ef46a-111">Agrupar varios conceptos de lecciones anteriores para crear una experiencia única</span><span class="sxs-lookup"><span data-stu-id="ef46a-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="ef46a-112">Obtener información sobre cómo activar o desactivar los objetos</span><span class="sxs-lookup"><span data-stu-id="ef46a-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="ef46a-113">Desencadenar eventos complejos mediante los botones presionables</span><span class="sxs-lookup"><span data-stu-id="ef46a-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="ef46a-114">Usar la física y la fuerza de los cuerpos rígidos</span><span class="sxs-lookup"><span data-stu-id="ef46a-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="ef46a-115">Explorar el uso de la información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="ef46a-115">Explore the use of tool tips</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="ef46a-116">Configuración del módulo lunar</span><span class="sxs-lookup"><span data-stu-id="ef46a-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="ef46a-117">En esta sección, se presentan los distintos componentes necesarios para crear nuestra experiencia de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-117">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="ef46a-118">Agregue el ensamblado del módulo lunar recurso prefabricado a la escena base.</span><span class="sxs-lookup"><span data-stu-id="ef46a-118">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="ef46a-119">Para ello, en la pestaña proyecto, vaya a activos > BaseModuleAssets > Prefabs.</span><span class="sxs-lookup"><span data-stu-id="ef46a-119">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="ef46a-120">Verá dos Prefabs del selector de Rocket, arrastre el Rocket Launcher_Tutorial recurso prefabricado a la escena y colóquelo como desee.</span><span class="sxs-lookup"><span data-stu-id="ef46a-120">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="ef46a-121">El Rocket Launcher_Complete recurso prefabricado es el selector completado, proporcionado como referencia.</span><span class="sxs-lookup"><span data-stu-id="ef46a-121">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Imagen de la lección 6, capítulo 1, paso 1](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="ef46a-123">Si expande el objeto Rocket Launcher_Tutorial Game en la jerarquía y expande aún más el objeto de módulo lunar, encontrará varios objetos secundarios que tienen un material denominado "x-Ray".</span><span class="sxs-lookup"><span data-stu-id="ef46a-123">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="ef46a-124">El material "x-Ray" permite un color ligeramente translúcido que se usará como sugerencias de selección de ubicación para el usuario.</span><span class="sxs-lookup"><span data-stu-id="ef46a-124">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span>

    ![Lesson6 archivo chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="ef46a-126">Hay cinco partes en el módulo lunar con las que interactuará el usuario, tal como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="ef46a-126">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="ef46a-127">El alojamiento del vehículo lunar</span><span class="sxs-lookup"><span data-stu-id="ef46a-127">The Rover Enclosure</span></span>
    2. <span data-ttu-id="ef46a-128">El depósito de combustible</span><span class="sxs-lookup"><span data-stu-id="ef46a-128">The Fuel Tank</span></span>
    3. <span data-ttu-id="ef46a-129">La célula de energía</span><span class="sxs-lookup"><span data-stu-id="ef46a-129">The Energy Cell</span></span>
    4. <span data-ttu-id="ef46a-130">El portal de acoplamiento</span><span class="sxs-lookup"><span data-stu-id="ef46a-130">The Docking Portal</span></span>
    5. <span data-ttu-id="ef46a-131">El sensor externo</span><span class="sxs-lookup"><span data-stu-id="ef46a-131">The External sensor</span></span>

    ![Imagen de la lección 6, capítulo 1, nota b](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="ef46a-133">Los nombres de los objetos del juego que se ven en la jerarquía de la escena base no se corresponden con los nombres de los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="ef46a-133">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="ef46a-134">Agregue un origen de audio al objeto de juego LunarModule.</span><span class="sxs-lookup"><span data-stu-id="ef46a-134">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="ef46a-135">Asegúrese de que LunarModule está seleccionado en la jerarquía de la escena y haga clic en Agregar componente.</span><span class="sxs-lookup"><span data-stu-id="ef46a-135">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="ef46a-136">Busque el origen de audio y agréguelo al objeto Game.</span><span class="sxs-lookup"><span data-stu-id="ef46a-136">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="ef46a-137">Deje el campo AudioClip en blanco por ahora, pero cambie la configuración de Blend especial de 0 a 1 para habilitar el audio espacial.</span><span class="sxs-lookup"><span data-stu-id="ef46a-137">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="ef46a-138">Usará este origen de audio para reproducir el sonido de inicio más adelante.</span><span class="sxs-lookup"><span data-stu-id="ef46a-138">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 archivo chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="ef46a-140">Agregue las sugerencias de alternancia de colocación del script.</span><span class="sxs-lookup"><span data-stu-id="ef46a-140">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="ef46a-141">Haga clic en Agregar componente y busque sugerencias de alternancia de ubicación.</span><span class="sxs-lookup"><span data-stu-id="ef46a-141">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="ef46a-142">Se trata de un script personalizado que le permite activar y desactivar las sugerencias translúcidas (objetos con el material de rayos x), como se mencionó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ef46a-142">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 archivo chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="ef46a-144">Dado que tenemos cinco objetos, escriba "5" para el tamaño de la matriz de objetos de juego.</span><span class="sxs-lookup"><span data-stu-id="ef46a-144">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="ef46a-145">Verá que aparecen cinco nuevos elementos.</span><span class="sxs-lookup"><span data-stu-id="ef46a-145">You will then see five new elements appear.</span></span>

    ![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="ef46a-147">Arrastre cada uno de los objetos translúcidos a todos los cuadros nombre (objeto de juego).</span><span class="sxs-lookup"><span data-stu-id="ef46a-147">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="ef46a-148">Arrastre los siguientes objetos desde el módulo lunar de la escena hasta los campos de la matriz de objetos, tal como se muestra en la imagen anterior:</span><span class="sxs-lookup"><span data-stu-id="ef46a-148">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Imagen de la lección 6, capítulo 1, paso 4](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="ef46a-150">El script Toggle Placement hints se ha configurado ahora, lo que nos permite activar y desactivar las sugerencias.</span><span class="sxs-lookup"><span data-stu-id="ef46a-150">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="ef46a-151">Agregue el script Launch lunar del módulo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-151">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="ef46a-152">Haga clic en el botón Agregar componente, busque "iniciar módulo lunar" y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-152">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="ef46a-153">Este script inicia el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="ef46a-153">This script launches the lunar module.</span></span> <span data-ttu-id="ef46a-154">Cuando se presiona un botón configurado, agrega una fuerza ascendente al componente del cuerpo rígido del módulo lunar y hace que el módulo se inicie hacia arriba.</span><span class="sxs-lookup"><span data-stu-id="ef46a-154">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="ef46a-155">Si estás en el interior, el módulo lunar puede chocar con la malla del techo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-155">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="ef46a-156">Si se encuentran en un área con límites máximos o sin límites, el módulo lunar entrará en el espacio indefinidamente.</span><span class="sxs-lookup"><span data-stu-id="ef46a-156">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Imagen de la lección 6, capítulo 1, paso 5](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="ef46a-158">Ajusta el impulso de modo que el módulo lunar vuele hacia arriba con elegancia.</span><span class="sxs-lookup"><span data-stu-id="ef46a-158">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="ef46a-159">Prueba con un valor de 0,01.</span><span class="sxs-lookup"><span data-stu-id="ef46a-159">Try a value of 0.01.</span></span> <span data-ttu-id="ef46a-160">Deja en blanco el campo "Rb".</span><span class="sxs-lookup"><span data-stu-id="ef46a-160">Leave the "Rb" field blank.</span></span> <span data-ttu-id="ef46a-161">RB significa cuerpo rígido y este campo se rellenará automáticamente durante el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="ef46a-161">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Imagen de la lección 6, capítulo 1, paso 6](images/Lesson6_Chapter1_step6im.PNG)

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="ef46a-163">Información general sobre los elementos del módulo lunar</span><span class="sxs-lookup"><span data-stu-id="ef46a-163">Lunar Module Parts overview</span></span>

<span data-ttu-id="ef46a-164">El objeto primario de los elementos de módulo lunar es la colección de los objetos con los que el usuario interactúa.</span><span class="sxs-lookup"><span data-stu-id="ef46a-164">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="ef46a-165">Los nombres de los objetos de juego con la escena con la etiqueta nombres entre paréntesis se muestran en la lista siguiente:</span><span class="sxs-lookup"><span data-stu-id="ef46a-165">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="ef46a-166">Mochila (célula de energía)</span><span class="sxs-lookup"><span data-stu-id="ef46a-166">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="ef46a-167">GasTank (depósito de combustible)</span><span class="sxs-lookup"><span data-stu-id="ef46a-167">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="ef46a-168">TopLeftBody (Alojamiento del vehículo lunar)</span><span class="sxs-lookup"><span data-stu-id="ef46a-168">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="ef46a-169">Nose (Portal de acoplamiento)</span><span class="sxs-lookup"><span data-stu-id="ef46a-169">Nose (Docking Portal)</span></span>
- <span data-ttu-id="ef46a-170">LeftTwirler (Sensor externo)</span><span class="sxs-lookup"><span data-stu-id="ef46a-170">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="ef46a-171">Observe que cada uno de estos objetos tiene un controlador de manipulación, como se explica en la lección 4.</span><span class="sxs-lookup"><span data-stu-id="ef46a-171">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="ef46a-172">Esta característica permite a los usuarios tomar y manipular el objeto.</span><span class="sxs-lookup"><span data-stu-id="ef46a-172">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="ef46a-173">Tenga en cuenta también que el valor, el tipo de manipulación de dos manos, se establece en Move y rotate.</span><span class="sxs-lookup"><span data-stu-id="ef46a-173">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="ef46a-174">Esta opción solo permite al usuario desplace el objeto y no cambie su tamaño, que es la funcionalidad deseada para una aplicación de ensamblado.</span><span class="sxs-lookup"><span data-stu-id="ef46a-174">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="ef46a-175">Además, la manipulación lejana está desactivada para permitir solo la interacción directa de las partes del módulo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-175">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Imagen de la lección 6, capítulo 2](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="ef46a-177">El script de demostración del ensamblado de elementos (mostrado anteriormente) es el script que administra los objetos que el usuario coloca en el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="ef46a-177">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="ef46a-178">El campo objeto que se va a colocar es la transformación seleccionada, tal como se muestra en la imagen anterior, el tanque de la mochila/combustible asociado al objeto al que se conecta.</span><span class="sxs-lookup"><span data-stu-id="ef46a-178">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="ef46a-179">La configuración de la distancia cercana y de la distancia determina la proximidad a la que se ajustan o se pueden liberar los elementos.</span><span class="sxs-lookup"><span data-stu-id="ef46a-179">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="ef46a-180">Por ejemplo, el tanque de la mochila o el depósito de combustible debe ser de 0,1 unidades del módulo lunar antes de que se ajuste.</span><span class="sxs-lookup"><span data-stu-id="ef46a-180">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="ef46a-181">La configuración de distancia de distancia establece la ubicación donde puede estar el objeto antes de que se pueda desasociar del módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="ef46a-181">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="ef46a-182">En este caso, la mano del usuario debe sujetar la mochila o depósito de combustible y alejarla 0,2 unidades del módulo lunar para evitar que vuelva a acoplarse en su lugar.</span><span class="sxs-lookup"><span data-stu-id="ef46a-182">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="ef46a-183">El objeto de información sobre herramientas es la etiqueta de información sobre herramientas de la escena.</span><span class="sxs-lookup"><span data-stu-id="ef46a-183">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="ef46a-184">Cuando se ajustan los objetos en su lugar, la etiqueta está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="ef46a-184">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="ef46a-185">El origen de audio se captura automáticamente.</span><span class="sxs-lookup"><span data-stu-id="ef46a-185">The Audio Source is automatically grabbed.</span></span>

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="ef46a-186">Configuración del botón sugerencias de selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="ef46a-186">Configuring the Placement Hints button</span></span>

<span data-ttu-id="ef46a-187">En la [Lección 2](mrlearning-base-ch2.md), ha aprendido a colocar y configurar botones para realizar acciones como cambiar el color de un elemento o hacer que se reproduzca un sonido al insertarlo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-187">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="ef46a-188">Seguiremos utilizando estos principios a medida que configuramos nuestros botones para alternar las sugerencias de colocación.</span><span class="sxs-lookup"><span data-stu-id="ef46a-188">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="ef46a-189">El objetivo es configurar nuestro botón para que cada vez que el usuario presione el botón de la sugerencia de selección de ubicación, alterne la visibilidad de las sugerencias de colocación translúcidas.</span><span class="sxs-lookup"><span data-stu-id="ef46a-189">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="ef46a-190">Mueva el módulo lunar a la ranura vacío en tiempo de ejecución en el panel Inspector mientras el objeto sugerencias de colocación está seleccionado en la jerarquía de escenas base.</span><span class="sxs-lookup"><span data-stu-id="ef46a-190">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="ef46a-192">Haga clic en la lista desplegable ninguna función.</span><span class="sxs-lookup"><span data-stu-id="ef46a-192">Click the No Function dropdown list.</span></span> <span data-ttu-id="ef46a-193">Vaya a TogglePlacementHints y seleccione ToggleGameObjects () en ese menú.</span><span class="sxs-lookup"><span data-stu-id="ef46a-193">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="ef46a-194">ToggleGameObjects () activa y desactiva las sugerencias de selección de ubicación para que sean visibles o invisibles cada vez que se presiona el botón.</span><span class="sxs-lookup"><span data-stu-id="ef46a-194">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="ef46a-196">Configuración del botón restablecer</span><span class="sxs-lookup"><span data-stu-id="ef46a-196">Configuring the Reset button</span></span>

<span data-ttu-id="ef46a-197">Habrá situaciones en las que el usuario comete un error, produce accidentalmente el objeto o simplemente desea restablecer la experiencia.</span><span class="sxs-lookup"><span data-stu-id="ef46a-197">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="ef46a-198">El botón Restablecer agrega la posibilidad de reiniciar la experiencia.</span><span class="sxs-lookup"><span data-stu-id="ef46a-198">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="ef46a-199">Seleccione el botón Restablecer.</span><span class="sxs-lookup"><span data-stu-id="ef46a-199">Select the Reset button.</span></span> <span data-ttu-id="ef46a-200">En la escena base, se denomina ResetRoundButton.</span><span class="sxs-lookup"><span data-stu-id="ef46a-200">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="ef46a-201">Arrastre el módulo lunar desde la jerarquía de escenas base hasta la ranura vacía en el botón presionado en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="ef46a-201">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="ef46a-203">Seleccione el menú desplegable ninguna función y mantenga el mouse sobre LaunchLunarModule y, a continuación, seleccione resetModule ().</span><span class="sxs-lookup"><span data-stu-id="ef46a-203">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Imagen de la lección 6, capítulo 4, paso 3](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="ef46a-205">Tenga en cuenta que, de forma predeterminada, GameObject. BroadcastMessage se configura como ResetPlacement.</span><span class="sxs-lookup"><span data-stu-id="ef46a-205">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="ef46a-206">Esto difunde un mensaje denominado ResetPlacement para cada objeto secundario del RocketLauncher_Tutorial.</span><span class="sxs-lookup"><span data-stu-id="ef46a-206">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="ef46a-207">Cualquier objeto que tenga un método para ResetPlacement () responde a ese mensaje restableciendo su posición.</span><span class="sxs-lookup"><span data-stu-id="ef46a-207">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

## <a name="configuring-the-launch-button"></a><span data-ttu-id="ef46a-208">Configuración del botón Launch</span><span class="sxs-lookup"><span data-stu-id="ef46a-208">Configuring the Launch button</span></span>

<span data-ttu-id="ef46a-209">En esta sección se explica cómo configurar el botón Launch, que permite al usuario presionar el botón e iniciar el módulo lunar en el espacio.</span><span class="sxs-lookup"><span data-stu-id="ef46a-209">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="ef46a-210">Seleccione el botón Launch (iniciar).</span><span class="sxs-lookup"><span data-stu-id="ef46a-210">Select the Launch button.</span></span> <span data-ttu-id="ef46a-211">En la escena base, se denomina LaunchRoundButton.</span><span class="sxs-lookup"><span data-stu-id="ef46a-211">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="ef46a-212">Arrastre el módulo lunar a la ranura vacía de Touch end en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="ef46a-212">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="ef46a-214">Seleccione el menú desplegable ninguna función y mantenga el mouse sobre LaunchLunarModule y seleccione StopThruster ().</span><span class="sxs-lookup"><span data-stu-id="ef46a-214">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="ef46a-215">Controla la cantidad de empuje que el usuario desea dar al módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="ef46a-215">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="ef46a-217">Arrastre el módulo lunar desde la jerarquía de escenas base hasta la ranura vacía en el botón presionado en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="ef46a-217">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="ef46a-218">Haga clic en el menú desplegable ninguna función y, a continuación, en LaunchLunarModule y seleccione StartThruster ().</span><span class="sxs-lookup"><span data-stu-id="ef46a-218">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="ef46a-220">Agregue música al módulo lunar para que se reproduzca cuando se desactive el cohete.</span><span class="sxs-lookup"><span data-stu-id="ef46a-220">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="ef46a-221">Para ello, arrastre el módulo lunar a la siguiente ranura vacía en el botón presionado ().</span><span class="sxs-lookup"><span data-stu-id="ef46a-221">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="ef46a-222">Seleccione el menú desplegable ninguna función, mantenga el mouse sobre AudioSource y seleccione PlayOneShot (AudioClip).</span><span class="sxs-lookup"><span data-stu-id="ef46a-222">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="ef46a-223">No dudes en explorar la variedad de sonidos que se incluyen con MRTK.</span><span class="sxs-lookup"><span data-stu-id="ef46a-223">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="ef46a-224">En este ejemplo, usaremos "MRTK_Gem".</span><span class="sxs-lookup"><span data-stu-id="ef46a-224">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ef46a-226">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ef46a-226">Congratulations</span></span>

<span data-ttu-id="ef46a-227">Ha configurado completamente esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="ef46a-227">You have fully configured this application.</span></span> <span data-ttu-id="ef46a-228">Ahora, cuando presione reproducir, puede ensamblar completamente el módulo lunar, alternar sugerencias, iniciar el módulo lunar y restablecerlo para que se inicie de nuevo.</span><span class="sxs-lookup"><span data-stu-id="ef46a-228">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
