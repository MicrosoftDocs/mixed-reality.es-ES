---
title: 'Tutoriales de introducción: 4. Colocación del contenido dinámico y uso de solucionadores'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362034"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="0494b-105">4. Colocación del contenido dinámico y uso de solucionadores</span><span class="sxs-lookup"><span data-stu-id="0494b-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="0494b-106">Los hologramas cobran vida en HoloLens 2 cuando, intuitivamente, siguen al usuario y se colocan en el entorno físico, de forma que la interacción resulta fluida y elegante.</span><span class="sxs-lookup"><span data-stu-id="0494b-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="0494b-107">En este tutorial, exploramos distintas formas de colocar hologramas de forma dinámica mediante las herramientas de selección de ubicación disponibles de MRTK, conocidas como "solucionadores", para resolver escenarios de selección de ubicación espacial complejos.</span><span class="sxs-lookup"><span data-stu-id="0494b-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="0494b-108">En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usan para permitir que los elementos de la interfaz de usuario te sigan, sigan al usuario o sigan a otros objetos de juego en la escena.</span><span class="sxs-lookup"><span data-stu-id="0494b-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="0494b-109">También pueden usarse para acoplarse rápidamente en ciertas posiciones, haciendo que la aplicación sea más intuitiva.</span><span class="sxs-lookup"><span data-stu-id="0494b-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="0494b-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0494b-110">Objectives</span></span>

* <span data-ttu-id="0494b-111">Introducir los solucionadores de MRTK</span><span class="sxs-lookup"><span data-stu-id="0494b-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="0494b-112">Usa solucionadores para tener una colección de botones que sigan al usuario</span><span class="sxs-lookup"><span data-stu-id="0494b-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="0494b-113">Usa solucionadores para tener un objeto de juego que siga las manos con seguimiento del usuario</span><span class="sxs-lookup"><span data-stu-id="0494b-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="0494b-114">Ubicación de los solucionadores en MRTK</span><span class="sxs-lookup"><span data-stu-id="0494b-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="0494b-115">Los solucionadores de MRTK se encuentran en la carpeta del SDK de MRTK.</span><span class="sxs-lookup"><span data-stu-id="0494b-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="0494b-116">Para ver los solucionadores disponibles en el proyecto, en la ventana Project (Proyecto), navega a **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers** (Recursos > MixedRealityToolkit.SDK > Características > Utilidades > Solucionadores):</span><span class="sxs-lookup"><span data-stu-id="0494b-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="0494b-118">En este tutorial, revisaremos la implementación de los solucionadores Orbital y Radial View (Vista radial).</span><span class="sxs-lookup"><span data-stu-id="0494b-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="0494b-119">Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, puedes visitar la guía [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0494b-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="0494b-120">Uso de un solucionador para seguir al usuario</span><span class="sxs-lookup"><span data-stu-id="0494b-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="0494b-121">En esta sección, mejorarás la colección de botones que creaste en el tutorial anterior para que siga la dirección de la mirada del usuario.</span><span class="sxs-lookup"><span data-stu-id="0494b-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="0494b-122">Además, también configurarás el solucionador para que la colección de botones siempre:</span><span class="sxs-lookup"><span data-stu-id="0494b-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="0494b-123">se gire en paralelo a la dirección de lectura del usuario, para proporcionar una lectura natural de izquierda a derecha;</span><span class="sxs-lookup"><span data-stu-id="0494b-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="0494b-124">se coloque por debajo de la dirección de mirada horizontal del usuario para no obstaculizar otros objetos que se agregarán más adelante en este tutorial;</span><span class="sxs-lookup"><span data-stu-id="0494b-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="0494b-125">se coloque, aproximadamente, a la distancia de la longitud de un brazo del usuario para que los botones se puedan presionar fácilmente.</span><span class="sxs-lookup"><span data-stu-id="0494b-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="0494b-126">Para ello, usarás el **solucionador Orbital**, que bloquea el objeto en una posición y desplazamiento especificados respecto al objeto al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="0494b-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="0494b-127">1. Agregar el solucionador Orbital</span><span class="sxs-lookup"><span data-stu-id="0494b-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="0494b-128">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **ButtonCollection** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Orbital (Script)** (Orbital [script]) al objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="0494b-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="0494b-129">Al agregar un solucionador, en este caso, el componente Orbital (Script), se agrega automáticamente el componente Solver Handler (Script) porque lo requiere el solucionador.</span><span class="sxs-lookup"><span data-stu-id="0494b-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="0494b-130">2. Configurar el solucionador Orbital</span><span class="sxs-lookup"><span data-stu-id="0494b-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="0494b-131">Configura el componente **Solver Handler (Script)** (Controlador de solucionador [script]):</span><span class="sxs-lookup"><span data-stu-id="0494b-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="0494b-132">Comprueba que **Tracked Target Type** (Tipo de destino de seguimiento) esté definido como **Head** (Cabeza).</span><span class="sxs-lookup"><span data-stu-id="0494b-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="0494b-133">Configura el componente **Orbital (Script)** :</span><span class="sxs-lookup"><span data-stu-id="0494b-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="0494b-134">Comprueba que **Orientation Type** (Tipo de orientación) se haya definido como **Follow Tracked Object** (Hacer seguimiento del objeto que se sigue).</span><span class="sxs-lookup"><span data-stu-id="0494b-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="0494b-135">Restaura **Local Offset** (Desplazamiento local) a X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="0494b-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="0494b-136">Cambia **World Offset** (Desplazamiento del mundo) a X = 0, Y = -0,4, Z = 0,3.</span><span class="sxs-lookup"><span data-stu-id="0494b-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="0494b-138">3. Probar el solucionador orbital mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="0494b-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="0494b-139">Presiona el botón Play (Jugar) para entrar en el modo de juego y mantén presionado el botón derecho del mouse para girar la dirección de la mirada y observa lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0494b-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="0494b-140">La posición de transformación de ButtonCollection está controlada por la configuración del solucionador.</span><span class="sxs-lookup"><span data-stu-id="0494b-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="0494b-141">El cubo, que no se ve afectado por el solucionador, sigue en la misma posición.</span><span class="sxs-lookup"><span data-stu-id="0494b-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="0494b-143">Si no ves el rayo de la cámara en la ventana de la escena, asegúrate de que el menú Gizmos esté habilitado.</span><span class="sxs-lookup"><span data-stu-id="0494b-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="0494b-144">Para obtener más información sobre el menú Gizmos y cómo puedes usarlo para optimizar la vista de escenas, visita la documentación sobre el <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menú de Gizmos </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="0494b-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="0494b-145">Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena).</span><span class="sxs-lookup"><span data-stu-id="0494b-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="0494b-146">Para obtener más información sobre cómo personalizar el área de trabajo, puedes visitar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="0494b-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="0494b-147">Habilitación de los objetos para que sigan a las manos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="0494b-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="0494b-148">En esta sección, configurarás el objeto de cubo que creaste en el tutorial anterior para que siga las manos con seguimiento del usuario, en concreto, la muñeca de la mano derecha.</span><span class="sxs-lookup"><span data-stu-id="0494b-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="0494b-149">Además, también configurarás el solucionador para que el cubo:</span><span class="sxs-lookup"><span data-stu-id="0494b-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="0494b-150">cambie su orientación con la rotación de la mano del usuario;</span><span class="sxs-lookup"><span data-stu-id="0494b-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="0494b-151">esté situado sobre la muñeca del usuario.</span><span class="sxs-lookup"><span data-stu-id="0494b-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="0494b-152">Para ello, usarás el **solucionador de vista radial**, que mantiene el objeto dentro de un cono de vista convertido por el objeto al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="0494b-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="0494b-153">1. Agregar el solucionador de vista radial</span><span class="sxs-lookup"><span data-stu-id="0494b-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="0494b-154">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cube** (Cubo) y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Radial View (Script)** (Vista radial [script]) al objeto Cube (Cubo).</span><span class="sxs-lookup"><span data-stu-id="0494b-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="0494b-155">2. Configurar el solucionador de vista radial</span><span class="sxs-lookup"><span data-stu-id="0494b-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="0494b-156">Configura el componente **Solver Handler (Script)** (Controlador de solucionador [script]):</span><span class="sxs-lookup"><span data-stu-id="0494b-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="0494b-157">Cambia **Tracked Target Type** (Tipo de destino de seguimiento) a **Hand Joint** (Articulación de la mano).</span><span class="sxs-lookup"><span data-stu-id="0494b-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="0494b-158">Cambia **Tracked Handness** (Mano de seguimiento) a **Right** (Derecha)</span><span class="sxs-lookup"><span data-stu-id="0494b-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="0494b-159">Cambia **Tracked Hand Joint** (Articulación de mano de seguimiento) a **Wrist** (Muñeca)</span><span class="sxs-lookup"><span data-stu-id="0494b-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="0494b-160">Configura el componente **Radial View (Script)** (Vista radial [script]):</span><span class="sxs-lookup"><span data-stu-id="0494b-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="0494b-161">Cambia **Reference Direction** (Dirección de referencia) a **Object Oriented** (Orientada a objetos) y activa la casilla **Orient To Reference Direction** (Orientar a dirección de referencia)</span><span class="sxs-lookup"><span data-stu-id="0494b-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="0494b-162">Cambia **Min Distance** (Distancia mínima) y **Max Distance** (Distancia máxima) a 0</span><span class="sxs-lookup"><span data-stu-id="0494b-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="0494b-164">3. Probar el solucionador de vista radial mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="0494b-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="0494b-165">Presiona el botón Play (Jugar) para entrar en el modo de juego y, a continuación, mantén presionada la barra espaciadora para mostrar la mano.</span><span class="sxs-lookup"><span data-stu-id="0494b-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="0494b-166">Mueve el cursor del mouse para mover la mano y haz clic y mantén presionado el botón del ratón para girar la mano:</span><span class="sxs-lookup"><span data-stu-id="0494b-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="0494b-168">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="0494b-168">Congratulations</span></span>

<span data-ttu-id="0494b-169">En este tutorial, has aprendido a usar los solucionadores de MRTK para tener una interfaz de usuario intuitiva que siga al usuario.</span><span class="sxs-lookup"><span data-stu-id="0494b-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="0494b-170">También has aprendido cómo adjuntar un solucionador a un objeto (es decir, el cubo) para seguir a las manos con seguimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="0494b-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="0494b-171">Para más información sobre estos y otros solucionadores incluidos con MRTK, visita la guía de [solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0494b-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="0494b-172">Tutorial siguiente: 5. Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="0494b-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
