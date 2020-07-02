---
title: 3. Configuración del proyecto para la realidad mixta
description: Parte 3 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: f79985b2ce9e26971c23acf36a3538bf7f3c166e
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "84879557"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="9965d-104">3. Configuración del proyecto para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9965d-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="9965d-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="9965d-105">Overview</span></span>

<span data-ttu-id="9965d-106">En el tutorial anterior, ha dedicado tiempo a configurar el proyecto de aplicación de ajedrez.</span><span class="sxs-lookup"><span data-stu-id="9965d-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="9965d-107">En esta sección se le guiará en la configuración de la aplicación para el desarrollo de realidad mixta, lo que significa la adición de una sesión de AR.</span><span class="sxs-lookup"><span data-stu-id="9965d-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="9965d-108">Usará un recurso de datos ARSessionConfig para esta tarea, que dispone una gran cantidad de opciones útiles de AR, como el mapeo espacial y la oclusión.</span><span class="sxs-lookup"><span data-stu-id="9965d-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="9965d-109">Si desea profundizar más, en la documentación de Unreal Engine se incluyen más detalles sobre el recurso [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) y la clase [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="9965d-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="9965d-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9965d-110">Objectives</span></span>
* <span data-ttu-id="9965d-111">Trabajo con la configuración de AR de Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="9965d-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="9965d-112">Uso de un recurso de datos ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="9965d-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="9965d-113">Configuración de un peón y el modo de juego</span><span class="sxs-lookup"><span data-stu-id="9965d-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="9965d-114">Adición del recurso de sesión</span><span class="sxs-lookup"><span data-stu-id="9965d-114">Adding the session asset</span></span>
<span data-ttu-id="9965d-115">Las sesiones de AR en Unreal no aparecen por sí mismas.</span><span class="sxs-lookup"><span data-stu-id="9965d-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="9965d-116">Para usar una sesión, necesita un recurso de datos ARSessionConfig con el que trabajar, que será la tarea siguiente:</span><span class="sxs-lookup"><span data-stu-id="9965d-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="9965d-117">Haga clic en **Add New > Miscellaneous > Data Asset** (Agregar nuevo > Varios > Recursos de datos) en **Content Browser** (Explorador de contenido).</span><span class="sxs-lookup"><span data-stu-id="9965d-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="9965d-118">Asegúrese de que se encuentra en el nivel raíz de la carpeta **Content** (Contenido).</span><span class="sxs-lookup"><span data-stu-id="9965d-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="9965d-119">Seleccione **ARSessionConfig**, haga clic en **Select** (Seleccionar) y asigne al recurso el nombre **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="9965d-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Crear un recurso de datos](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="9965d-121">Haga doble clic en **ARSessionConfig** para abrirlo, deje la configuración predeterminada y haga clic en **Save** (Guardar).</span><span class="sxs-lookup"><span data-stu-id="9965d-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="9965d-122">Vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="9965d-122">Return to the Main window.</span></span> 

![Configuración de sesión de AR](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="9965d-124">Una vez hecho esto, el paso siguiente consiste en asegurarse de que la sesión de AR se inicia cuando se carga el nivel y se detiene cuando este finaliza.</span><span class="sxs-lookup"><span data-stu-id="9965d-124">With that done, your next step is to make sure that the AR session starts when the level loads and stops when the level ends.</span></span> <span data-ttu-id="9965d-125">Por suerte, Unreal tiene un tipo especial de plano técnico denominado **Level Blueprint** (Plano técnico de nivel) que actúa como un gráfico de eventos global de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="9965d-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="9965d-126">La conexión del recurso ARSessionConfig en **Level Blueprint** (Plano técnico de nivel) garantiza que la sesión de AR se activará cuando se inicie la reproducción del juego.</span><span class="sxs-lookup"><span data-stu-id="9965d-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="9965d-127">Haga clic en **Blueprints > Open Level Blueprint** (Planos técnicos > Abrir plano técnico de nivel) en la barra de herramientas del editor:</span><span class="sxs-lookup"><span data-stu-id="9965d-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Abrir plano técnico de nivel](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="9965d-129">Arrastre el nodo de ejecución (icono de flecha hacia la izquierda) fuera de **Event BeginPlay** (Evento BeginPlay) y suéltelo.</span><span class="sxs-lookup"><span data-stu-id="9965d-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="9965d-130">Busque el nodo **Start AR Session** (Iniciar sesión de AR) y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="9965d-130">Search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="9965d-131">Haga clic en la lista desplegable **Select Asset** (Seleccionar recurso) en **Session Config** (Configuración de sesión) y elija el recurso **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="9965d-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 

![Iniciar sesión de AR](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="9965d-133">Haga clic con el botón derecho en EventGraph y cree un nuevo nodo **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="9965d-133">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="9965d-134">Arrastre la marca de ejecución y suéltela.</span><span class="sxs-lookup"><span data-stu-id="9965d-134">Drag the execution pin and release.</span></span> <span data-ttu-id="9965d-135">Busque el nodo **Start AR Session** (Iniciar sesión de AR) y presione Entrar.</span><span class="sxs-lookup"><span data-stu-id="9965d-135">Search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="9965d-136">Si la sesión de AR no se detiene cuando el nivel finaliza, algunas características pueden dejar de funcionar si reinicia la aplicación durante el streaming a un casco de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9965d-136">If the AR session isn't stopped when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span> 
    * <span data-ttu-id="9965d-137">Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="9965d-137">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Detener sesión de AR](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="9965d-139">Creación de un peón</span><span class="sxs-lookup"><span data-stu-id="9965d-139">Create a Pawn</span></span>
<span data-ttu-id="9965d-140">En este punto, el proyecto todavía necesita un objeto que sea el jugador.</span><span class="sxs-lookup"><span data-stu-id="9965d-140">At this point, the project still needs a player object.</span></span> <span data-ttu-id="9965d-141">En Unreal, **Pawn** (Peón) representa al usuario del juego; pero, en este caso, será la experiencia de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9965d-141">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="9965d-142">Haga clic en **Add New > Blueprint Class** (Agregar nuevo > Clase de plano técnico) en la carpeta **Content** (Contenido) y expanda la sección **All Classes** (Todas las clases) en la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="9965d-142">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="9965d-143">Busque **DefaultPawn**, haga clic en **Select** (Seleccionar) y haga doble clic en el recurso para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="9965d-143">Search for **DefaultPawn**, click **Select** and double-click the asset to open.</span></span> 

![Crear un nuevo peón que herede de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="9965d-145">De forma predeterminada, los peones tienen componentes de malla y colisión.</span><span class="sxs-lookup"><span data-stu-id="9965d-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="9965d-146">En la mayoría de los proyectos de Unreal, los peones son objetos sólidos que pueden colisionar con otros componentes.</span><span class="sxs-lookup"><span data-stu-id="9965d-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="9965d-147">Dado que el peón y el usuario son los mismos en la realidad mixta, querrá poder pasar a través de hologramas sin colisiones.</span><span class="sxs-lookup"><span data-stu-id="9965d-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="9965d-148">Seleccione **CollisionComponent** en el panel **Components** (Componentes) y desplácese hacia abajo hasta la sección **Collision** (Colisión) del panel **Details** (Detalles).</span><span class="sxs-lookup"><span data-stu-id="9965d-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="9965d-149">Haga clic en la lista desplegable **Collision Presets** (Valores preestablecidos de colisión) y cambie el valor a **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="9965d-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="9965d-150">Haga lo mismo para **MeshComponent**, después **compile** y **guarde** el plano técnico.</span><span class="sxs-lookup"><span data-stu-id="9965d-150">Do the same for the **MeshComponent**, then **Compile** and **Save** the Blueprint.</span></span> 

![Ajustar los valores preestablecidos de colisión del peón](images/unreal-uxt/3-nocollision.PNG)

<span data-ttu-id="9965d-152">Con el trabajo que ha realizado aquí, vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="9965d-152">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="9965d-153">Creación de un modo de juego</span><span class="sxs-lookup"><span data-stu-id="9965d-153">Create a Game Mode</span></span>
<span data-ttu-id="9965d-154">La última pieza del rompecabezas de la configuración de la realidad mixta es el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="9965d-154">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="9965d-155">El modo de juego determina una serie de opciones de configuración para el juego o la experiencia, incluido el peón predeterminado que se usará.</span><span class="sxs-lookup"><span data-stu-id="9965d-155">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="9965d-156">Haga clic en **Add New > Blueprint Class** (Agregar nuevo > Clase de plano técnico) en la carpeta **Content** (Contenido) y expanda la sección **All Classes** (Todas las clases) en la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="9965d-156">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="9965d-157">Busque **Game Mode Base** (Base de modo de juego), asígnele el nombre **MRGameMode** y haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="9965d-157">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![MRGameMode en el explorador de contenido](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="9965d-159">Vaya a la sección **Classes** (Clases) en el panel **Details** (Detalles) y cambie **Default Pawn Class** (Clase de peón predeterminado) a **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="9965d-159">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="9965d-160">Pulse en **Compile** (Compilar), luego en **Save** (Guardar) y vuelva a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="9965d-160">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Establecer la clase de peón predeterminada](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="9965d-162">Seleccione **Edit > Projects Settings** (Editar > Configuración de proyectos) y haga clic en **Maps & Modes** (Mapas y modos) en la lista de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9965d-162">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="9965d-163">Expanda **Default Modes** (Modos predeterminados) y cambie **Default Game Mode** (Modo de juego predeterminado) a **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="9965d-163">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="9965d-164">Expanda **Default Maps** (Mapas predeterminados) y cambie **EditorStartupMap** y **GameDefaultMap** a **Main** (Principal).</span><span class="sxs-lookup"><span data-stu-id="9965d-164">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="9965d-165">De este modo, cuando cierre el editor y vuelva a abrirlo o cuando juegue una partida, se seleccionará el mapa principal de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9965d-165">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Configuración del proyecto: mapas y modos](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="9965d-167">Una vez que el proyecto se haya configurado completamente para la realidad mixta, está listo para pasar al siguiente tutorial y empezar a agregar datos proporcionados por el usuario a la escena.</span><span class="sxs-lookup"><span data-stu-id="9965d-167">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="9965d-168">Sección siguiente: 4. Creación de escenas interactivas</span><span class="sxs-lookup"><span data-stu-id="9965d-168">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)