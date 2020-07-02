---
title: 2. Inicialización de tu proyecto y primera aplicación
description: Parte 2 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345735"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="db5cc-104">2. Inicialización de tu proyecto y primera aplicación</span><span class="sxs-lookup"><span data-stu-id="db5cc-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="db5cc-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="db5cc-105">Overview</span></span>

<span data-ttu-id="db5cc-106">En este primer tutorial, comenzará con una nueva aplicación de Unreal para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="db5cc-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="db5cc-107">Incluirá agregar el complemento de HoloLens, crear e iluminar un nivel y rellenarlo con un tablero de juegos y una pieza de ajedrez.</span><span class="sxs-lookup"><span data-stu-id="db5cc-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="db5cc-108">Usará recursos predefinidos para los materiales de los objetos y la pieza de ajedrez 3D, por lo que no deberá preocuparse por un modelado desde cero.</span><span class="sxs-lookup"><span data-stu-id="db5cc-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="db5cc-109">Al final de este tutorial tendrá un lienzo en blanco listo para la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="db5cc-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="db5cc-110">Antes de continuar, asegúrese de que tiene todos los requisitos previos de la página [Introducción](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="db5cc-110">Before continuing, make sure you have all the prerequisites from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="db5cc-111">Objetivos</span><span class="sxs-lookup"><span data-stu-id="db5cc-111">Objectives</span></span>
* <span data-ttu-id="db5cc-112">Configuración de un proyecto de Unreal para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="db5cc-112">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="db5cc-113">Importación de recursos y configuración de una escena</span><span class="sxs-lookup"><span data-stu-id="db5cc-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="db5cc-114">Creación de actores y eventos de nivel de script con planos técnicos</span><span class="sxs-lookup"><span data-stu-id="db5cc-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="db5cc-115">Creación de un nuevo proyecto de Unreal</span><span class="sxs-lookup"><span data-stu-id="db5cc-115">Creating a new Unreal project</span></span>
<span data-ttu-id="db5cc-116">Lo primero que necesita es un proyecto con el que trabajar.</span><span class="sxs-lookup"><span data-stu-id="db5cc-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="db5cc-117">Si esta es la primera vez que crea una aplicación de Unreal para HoloLens, deberá [descargar los archivos auxiliares](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) desde el iniciador de Epic.</span><span class="sxs-lookup"><span data-stu-id="db5cc-117">If this is your first time creating an Unreal app for HoloLens, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) from the Epic Launcher.</span></span>

1. <span data-ttu-id="db5cc-118">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="db5cc-118">Launch Unreal Engine</span></span>

2. <span data-ttu-id="db5cc-119">En **Games** (Juegos), seleccione **New Project Categories** (Nuevas categorías de proyecto) y haga clic en **Next** (Siguiente).</span><span class="sxs-lookup"><span data-stu-id="db5cc-119">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Selección de la plantilla del proyecto Games](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="db5cc-121">Seleccione una plantilla **Blank** (En blanco) y haga clic en **Next** (Siguiente).</span><span class="sxs-lookup"><span data-stu-id="db5cc-121">Select the **Blank** Template and click **Next**.</span></span> 

![Seleccionar la plantilla en blanco](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="db5cc-123">Defina **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Móvil o tableta escalable 3D o 2D) y **No Starter Content** (Sin contenido de inicio) como **Configuración del proyecto**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-123">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**.</span></span> 
    * <span data-ttu-id="db5cc-124">Elija una ubicación para guardarlo y haga clic en **Crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-124">Choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="db5cc-125">Debe seleccionar un proyecto de C++ en lugar de un proyecto de plano técnico para compilar el complemento de herramientas de la experiencia del usuario, que configurará más adelante en la sección 4.</span><span class="sxs-lookup"><span data-stu-id="db5cc-125">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Configuración del proyecto inicial](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="db5cc-127">El proyecto deberá abrirse automáticamente en el editor de Unreal, lo que significa que está listo para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="db5cc-127">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="db5cc-128">Habilitación de los complementos necesarios</span><span class="sxs-lookup"><span data-stu-id="db5cc-128">Enabling required plugins</span></span>
<span data-ttu-id="db5cc-129">Antes de empezar a agregar objetos a la escena, deberá habilitar dos complementos.</span><span class="sxs-lookup"><span data-stu-id="db5cc-129">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="db5cc-130">Abra **Edit > Plugins** (Editar > Complementos) y seleccione **Augmented Reality** (Realidad aumentada) en la lista opciones integradas.</span><span class="sxs-lookup"><span data-stu-id="db5cc-130">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="db5cc-131">Desplácese hacia abajo hasta **HoloLens** y marque **Enabled** (Habilitado).</span><span class="sxs-lookup"><span data-stu-id="db5cc-131">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Habilitación de complementos de HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="db5cc-133">Seleccione **Realidad virtual** en la lista opciones integradas.</span><span class="sxs-lookup"><span data-stu-id="db5cc-133">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="db5cc-134">Desplácese hacia abajo hasta **Microsoft Windows Mixed Reality**, marque **Habilitado** y reinicie el editor.</span><span class="sxs-lookup"><span data-stu-id="db5cc-134">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Habilitación del complemento Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="db5cc-136">Ambos complementos son necesarios para el desarrollo para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="db5cc-136">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="db5cc-137">Después de esto, el nivel vacío está listo para llenarlo.</span><span class="sxs-lookup"><span data-stu-id="db5cc-137">With that done your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="db5cc-138">Creación de un nivel</span><span class="sxs-lookup"><span data-stu-id="db5cc-138">Creating a level</span></span>
<span data-ttu-id="db5cc-139">La siguiente tarea consiste en crear una configuración sencilla de un jugador con un punto inicial y un cubo para referencia y escala.</span><span class="sxs-lookup"><span data-stu-id="db5cc-139">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="db5cc-140">Seleccione **File > New Level** (Archivo > Nuevo nivel) y elija **Empty Level** (Nivel vacío).</span><span class="sxs-lookup"><span data-stu-id="db5cc-140">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="db5cc-141">Ahora, la escena predeterminada en la ventanilla debe estar vacía.</span><span class="sxs-lookup"><span data-stu-id="db5cc-141">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="db5cc-142">Seleccione **Basic** (Básico) en la pestaña **Modes** (Modos) y arrastre **PlayerStart** a la escena.</span><span class="sxs-lookup"><span data-stu-id="db5cc-142">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="db5cc-143">Establezca **Location** (Ubicación) en **X = 0**, **Y = 0** y **Z = 0** en la pestaña **Details** (Detalles). De este modo se establece al usuario en el centro de la escena cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="db5cc-143">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![Ventanilla con PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="db5cc-145">Arrastre un **Cube** (Cubo) desde la pestaña **Basic** (Básico) a la escena.</span><span class="sxs-lookup"><span data-stu-id="db5cc-145">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="db5cc-146">Establezca **Location** (Ubicación) en **X = 50**, **Y = 0** y **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-146">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="db5cc-147">Así, se coloca el cubo a 50 cm del jugador en el momento del inicio.</span><span class="sxs-lookup"><span data-stu-id="db5cc-147">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="db5cc-148">Cambie **Scale** (Escala) a **X = 0,2**, **Y = 0,2** y **Z = 0,2** para reducir el cubo.</span><span class="sxs-lookup"><span data-stu-id="db5cc-148">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="db5cc-149">No podrá ver el cubo a menos que agregue una luz a la escena, que es la última tarea antes de probar la escena.</span><span class="sxs-lookup"><span data-stu-id="db5cc-149">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="db5cc-150">Cambie a la pestaña **Ligths** (Luces) del panel **Modes** (Modos) y arrastre **Directional Light** (Luz direccional) a la escena.</span><span class="sxs-lookup"><span data-stu-id="db5cc-150">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="db5cc-151">Coloque la luz sobre **PlayerStart** para que pueda verlo.</span><span class="sxs-lookup"><span data-stu-id="db5cc-151">Position the light above **PlayerStart** so you can see it.</span></span>

![Ventanilla con luz agregada](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="db5cc-153">Vaya a **File > Save Current** (Archivo > Guardar actual), asigne un nombre al nivel **Main** (Principal) y haga clic en **Save** (Guardar).</span><span class="sxs-lookup"><span data-stu-id="db5cc-153">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="db5cc-154">Con la escena definida, presione **Play** (Jugar) en la barra de herramientas para ver el cubo en acción.</span><span class="sxs-lookup"><span data-stu-id="db5cc-154">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="db5cc-155">Cuando haya terminado de admirar su trabajo, presione **Esc** para detener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="db5cc-155">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Cubo en la ventanilla](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="db5cc-157">Ahora que la escena está configurada, puede empezar a agregar el panel de ajedrez y la pieza para completar el entorno de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="db5cc-157">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="db5cc-158">Importación de recursos</span><span class="sxs-lookup"><span data-stu-id="db5cc-158">Importing assets</span></span>
<span data-ttu-id="db5cc-159">La escena está un poco vacía en este momento, pero se solucionará al importar los recursos ya preparados al proyecto.</span><span class="sxs-lookup"><span data-stu-id="db5cc-159">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="db5cc-160">Descargue y descomprima la carpeta de recursos de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span><span class="sxs-lookup"><span data-stu-id="db5cc-160">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="db5cc-161">Haga clic en **Add New > New Folder** (Agregar nuevo > Nueva carpeta) en **Content Browser** (Explorador de contenido) y asígnele el nombre **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-161">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="db5cc-162">Haga doble clic en la nueva carpeta; ahí es donde importará los recursos 3D.</span><span class="sxs-lookup"><span data-stu-id="db5cc-162">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![Mostrar u ocultar el panel de orígenes](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="db5cc-164">Haga clic en **Import** (Importar) en **Content Browser** (Explorador de contenido), seleccione todos los elementos de la carpeta de recursos descomprimidos y haga clic en **Open** (Abrir).</span><span class="sxs-lookup"><span data-stu-id="db5cc-164">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="db5cc-165">Esta carpeta contiene las mallas de objetos 3D para el tablero de ajedrez, las piezas en formato FBX y los mapas de textura en formato TGA que usará para los materiales.</span><span class="sxs-lookup"><span data-stu-id="db5cc-165">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="db5cc-166">Cuando aparezca la ventana de opciones de importación de FBX, expanda la sección **Material** y cambie **Material Import Method** (Método de importación de material) a **Do Not Create Material** (No crear material).</span><span class="sxs-lookup"><span data-stu-id="db5cc-166">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="db5cc-167">Haga clic en **Import All** (Importar todo).</span><span class="sxs-lookup"><span data-stu-id="db5cc-167">Click **Import All**.</span></span>

![Opciones de importación de FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="db5cc-169">Es todo lo que debe hacer para los recursos.</span><span class="sxs-lookup"><span data-stu-id="db5cc-169">That's all you need to do for the assets.</span></span> <span data-ttu-id="db5cc-170">El siguiente conjunto de tareas consiste en crear los bloques de creación de la aplicación con planos técnicos.</span><span class="sxs-lookup"><span data-stu-id="db5cc-170">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="db5cc-171">Adición de planos técnicos</span><span class="sxs-lookup"><span data-stu-id="db5cc-171">Adding blueprints</span></span>

1. <span data-ttu-id="db5cc-172">Haga clic en **Add New > New Folder** (Agregar nuevo > Nueva carpeta) en **Content Browser** (Explorador de contenido) y asígnele el nombre **Explorador de contenido**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-172">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="db5cc-173">Los [planos técnicos](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) son recursos especiales que proporcionan una interfaz basada en nodos para crear nuevos tipos de actores y eventos de nivel de script.</span><span class="sxs-lookup"><span data-stu-id="db5cc-173">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="db5cc-174">Haga doble clic en la carpeta **Blueprints** (Planos técnicos), haga clic con el botón derecho y seleccione **Blueprint Class** (Clase de plano técnico).</span><span class="sxs-lookup"><span data-stu-id="db5cc-174">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="db5cc-175">Seleccione **Actor** y asigne el nombre **Board** al nuevo plano técnico.</span><span class="sxs-lookup"><span data-stu-id="db5cc-175">Select **Actor** and name the blueprint **Board**.</span></span> 

![Selecciona una clase principal para el plano técnico](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="db5cc-177">El nuevo plano técnico **Board** ahora aparece en la carpeta **Blueprints** (Planos técnicos) como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="db5cc-177">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Nuevo plano técnico Board](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="db5cc-179">Está listo para empezar a agregar materiales a los objetos creados.</span><span class="sxs-lookup"><span data-stu-id="db5cc-179">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="db5cc-180">Utilización de materiales</span><span class="sxs-lookup"><span data-stu-id="db5cc-180">Working with materials</span></span>
<span data-ttu-id="db5cc-181">Los objetos que ha creado son de color gris de forma predeterminada, lo que no es muy alegre.</span><span class="sxs-lookup"><span data-stu-id="db5cc-181">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="db5cc-182">La adición de materiales y mallas a los objetos es el último conjunto de tareas de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="db5cc-182">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="db5cc-183">Haga doble clic en **Board** para abrir el editor de planos técnicos.</span><span class="sxs-lookup"><span data-stu-id="db5cc-183">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="db5cc-184">Haga clic en **Add Component > Scene**  (Agregar componente > Escena) en el panel **Components** (Componentes) y asígnele el nombre **Root**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-184">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="db5cc-185">Observe que **Root** se muestra como un elemento secundario de **DefaultSceneRoot** en la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="db5cc-185">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Reemplazar la raíz](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="db5cc-187">Haga clic y arrastre **Root** a **DefaultSceneRoot** para reemplazarlo y eliminar la esfera en la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="db5cc-187">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Reemplazar la raíz](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="db5cc-189">Haga clic en **Add Component > Static Mesh** (Agregar componente > Malla estática) en el panel **Components** (Componentes) y asígnele el nombre **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-189">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="db5cc-190">Aparecerá como un objeto secundario en **Root**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-190">It will appear as a child object under **Root**.</span></span>

![Adición de una malla estática](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="db5cc-192">Haga clic en **SM_Board**, desplácese hacia abajo hasta la sección **Static Mesh** (Malla estática) del panel **Details** (Detalles) y seleccione **ChessBoard** en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="db5cc-192">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Malla del tablero en la ventanilla](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="db5cc-194">En el panel **Details** (Detalles), expanda la sección **Materials** (Materiales) y haga clic en **Create New Asset > Material** (Crear nuevo recurso > Material) en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="db5cc-194">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="db5cc-195">Asigne al material el nombre **M_ChessBoard** y guárdelo en la carpeta **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-195">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Crear un material nuevo](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="db5cc-197">Haga doble clic en la imagen del material **M_ChessBoard** para abrir el editor de materiales.</span><span class="sxs-lookup"><span data-stu-id="db5cc-197">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Apertura del editor de materiales](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="db5cc-199">En el editor de materiales, haga clic con el botón derecho y busque **Texture Sample** (Muestra de textura).</span><span class="sxs-lookup"><span data-stu-id="db5cc-199">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="db5cc-200">Expanda la sección **Material Expression Texture Base** (Base de textura de expresión de material) del panel **Details** (Detalles) y defina **Texture** (Textura) en **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-200">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="db5cc-201">Arrastre la marca de salida de **RGB** a la marca de color base de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-201">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Establecer el color de base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="db5cc-203">Repita el paso anterior cuatro veces más para crear cuatro nodos de **Texture Sample** (Muestra de textura) con la siguiente configuración:</span><span class="sxs-lookup"><span data-stu-id="db5cc-203">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="db5cc-204">Establezca **Texture** (Textura) en **ChessBoard_AO** y vincule **RGB** a la marca de **Ambient Occlusion** (Oclusión ambiental).</span><span class="sxs-lookup"><span data-stu-id="db5cc-204">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="db5cc-205">Establezca **Texture** (Textura) en **ChessBoard_Metal** y vincule **RGB** a la marca de **Metallic** (Metálico).</span><span class="sxs-lookup"><span data-stu-id="db5cc-205">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="db5cc-206">Establezca **Texture** (Textura) en **ChessBoard_Normal** y vincule **RGB** a la marca de **Normal**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-206">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="db5cc-207">Establezca **Texture** (Textura) en **ChessBoard_Rough** y vincule **RGB** a la marca de **Roughness** (Rugosidad).</span><span class="sxs-lookup"><span data-stu-id="db5cc-207">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="db5cc-208">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-208">Click **Save**.</span></span> 

![Enlazar las texturas restantes](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="db5cc-210">Asegúrese de que la configuración del material sea similar a la captura de pantalla anterior antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="db5cc-210">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="db5cc-211">Rellenado de la escena</span><span class="sxs-lookup"><span data-stu-id="db5cc-211">Populating the scene</span></span>
<span data-ttu-id="db5cc-212">Si vuelve al plano técnico **Board**, verá que se ha aplicado el material que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="db5cc-212">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="db5cc-213">Lo único que queda es configurar la escena.</span><span class="sxs-lookup"><span data-stu-id="db5cc-213">All that's left is setting up the scene!</span></span> <span data-ttu-id="db5cc-214">En primer lugar, cambie las siguientes propiedades para asegurarse de que el tablero tiene un tamaño razonable y que tiene el ángulo correcto cuando se coloca en la escena:</span><span class="sxs-lookup"><span data-stu-id="db5cc-214">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="db5cc-215">Establezca **Scale** (Escala) en **(0,05, 0,05, 0,05)** y **Z Rotation** (Rotación Z) en **90**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-215">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="db5cc-216">Haga clic en **Compile** (Compilar) en la barra de herramientas superior, luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="db5cc-216">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Tablero de ajedrez con el material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="db5cc-218">Haga clic con el botón derecho en **Cube > Edit > Delete** (Cubo > Editar > Eliminar) y arrastre **Board** desde **Content Browser** (Explorador de contenido) a la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="db5cc-218">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="db5cc-219">Establezca **Location** (Ubicación) en **X = 80**, **Y = 0** y **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-219">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="db5cc-220">Haga clic en el botón **Play** (Jugar) para ver el nuevo tablero en el nivel.</span><span class="sxs-lookup"><span data-stu-id="db5cc-220">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="db5cc-221">Presiona **Esc** para volver al editor.</span><span class="sxs-lookup"><span data-stu-id="db5cc-221">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="db5cc-222">Ahora seguirá los mismos pasos para crear una pieza de ajedrez como hizo con el tablero:</span><span class="sxs-lookup"><span data-stu-id="db5cc-222">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="db5cc-223">Vaya a la carpeta **Blueprints** (Planos técnicos), haga clic con el botón derecho, seleccione **Blueprint Class** (Clase de plano técnico) y elija **Actor**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-223">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="db5cc-224">Asigne al actor el nombre **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-224">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="db5cc-225">Haga doble clic en **WhiteKing** para abrirlo en el editor de planos técnicos, haga clic en **Add Component > Scene** (Agregar componente > Escena) y asígnele el nombre **Root**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-225">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="db5cc-226">Arrastre y coloque **Root** en **DefaultSceneRoot** para reemplazarlo.</span><span class="sxs-lookup"><span data-stu-id="db5cc-226">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="db5cc-227">Haga clic en **Add Component > Static Mesh** (Agregar componente > Malla estática) y asígnele el nombre **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-227">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="db5cc-228">Establezca **Static Mesh** (Malla estática) en **Chess_King** y **Material** en un nuevo material denominado **M_ChessWhite** en el panel de detalles.</span><span class="sxs-lookup"><span data-stu-id="db5cc-228">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="db5cc-229">Abra **M_ChessWhite** en el editor de materiales y enlace los siguientes nodos de **Texture Sample** (Muestra de textura) a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="db5cc-229">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="db5cc-230">Establezca **Texture** (Textura) en **ChessWhite_AO** y vincule **RGB** a la marca de **Ambient Occlusion** (Oclusión ambiental).</span><span class="sxs-lookup"><span data-stu-id="db5cc-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="db5cc-231">Establezca **Texture** (Textura) en **ChessWhite_Metal** y vincule **RGB** a la marca de **Metallic** (Metálico).</span><span class="sxs-lookup"><span data-stu-id="db5cc-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="db5cc-232">Establezca **Texture** (Textura) en **ChessWhite_Metal** y vincule **RGB** a la marca de **Normal**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="db5cc-233">Establezca **Texture** (Textura) en **ChessWhite_Rough** y vincule **RGB** a la marca de **Roughness** (Rugosidad).</span><span class="sxs-lookup"><span data-stu-id="db5cc-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="db5cc-234">Haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-234">Click **Save**.</span></span> 

<span data-ttu-id="db5cc-235">El material de **M_ChessKing** debe parecerse a la siguiente imagen antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="db5cc-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Crear el material para el rey del ajedrez](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="db5cc-237">Casi está, solo tiene que agregar la nueva pieza de ajedrez a la escena:</span><span class="sxs-lookup"><span data-stu-id="db5cc-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="db5cc-238">Abra el plano técnico **WhiteKing**, cambie el valor de **Scale** (Escala) a **(0,05, 0,05, 0,05)** y de **Z Rotation** (Rotación Z) a **90**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="db5cc-239">Compile y guarde el plano técnico y, a continuación, vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="db5cc-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="db5cc-240">Arrastre **WhiteKing** a la ventanilla, cambie al panel **World Outliner** (Esquematizador del mundo), arrastre **WhiteKing** a **Board** para convertirlo en un objeto secundario.</span><span class="sxs-lookup"><span data-stu-id="db5cc-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![World Outliner (Esquematizador del mundo)](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="db5cc-242">En el panel **Details** (Detalles) en **Transform** (Transformar), establezca el valor de **Location** (Ubicación) de **WhiteKing** en **X = -26**, **Y = 4** y **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="db5cc-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="db5cc-243">Ya está.</span><span class="sxs-lookup"><span data-stu-id="db5cc-243">That's a wrap!</span></span> <span data-ttu-id="db5cc-244">Haga clic en **Play** (Jugar) para ver el nivel rellenado en acción y presione **Esc** cuando esté listo para salir.</span><span class="sxs-lookup"><span data-stu-id="db5cc-244">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="db5cc-245">En este tutorial se ha tratado una gran cantidad de información sobre la creación de un proyecto sencillo, pero el proyecto está listo para pasar a la siguiente parte de la serie: configuración de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="db5cc-245">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="db5cc-246">Sección siguiente: 3. Configuración del proyecto para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="db5cc-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
