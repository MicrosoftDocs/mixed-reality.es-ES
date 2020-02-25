---
title: 'Tutoriales de introducción: 4. Colocar contenido dinámico y usar solucionadores'
description: Realiza este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553908"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="de771-105">4. colocar contenido dinámico y usar solucionadores</span><span class="sxs-lookup"><span data-stu-id="de771-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="de771-106">Los hologramas llegan a la vida en HoloLens 2 cuando siguen de forma intuitiva al usuario y se colocan en el entorno físico de una manera que hace que la interacción sea fluida y elegante.</span><span class="sxs-lookup"><span data-stu-id="de771-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="de771-107">En este tutorial, se exploran las formas de colocar dinámicamente los hologramas con las herramientas de selección de ubicación disponibles de MRTK, conocidas como solucionadores, para solucionar escenarios complejos de colocación espacial.</span><span class="sxs-lookup"><span data-stu-id="de771-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="de771-108">En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usan para permitir que los elementos de la interfaz de usuario sigan el usuario, el usuario u otros objetos de juego de la escena.</span><span class="sxs-lookup"><span data-stu-id="de771-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="de771-109">También pueden usarse para acoplarse rápidamente en ciertas posiciones, haciendo que la aplicación sea más intuitiva.</span><span class="sxs-lookup"><span data-stu-id="de771-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="de771-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="de771-110">Objectives</span></span>

* <span data-ttu-id="de771-111">Introducción a los solucionadores de MRTK</span><span class="sxs-lookup"><span data-stu-id="de771-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="de771-112">Usar solucionadores para que una colección de botones siga al usuario</span><span class="sxs-lookup"><span data-stu-id="de771-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="de771-113">Usar solucionadores para que un objeto de juego siga las manos controladas por el usuario</span><span class="sxs-lookup"><span data-stu-id="de771-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="de771-114">Ubicación de los solucionadores en el MRTK</span><span class="sxs-lookup"><span data-stu-id="de771-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="de771-115">Los solucionadores de MRTK se encuentran en la carpeta MRTK SDK.</span><span class="sxs-lookup"><span data-stu-id="de771-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="de771-116">Para ver las resoluciones disponibles en el proyecto, en la ventana proyecto, vaya a **activos** > **MixedRealityToolkit. SDK** > **features** > **Utilities** > **resolvetions**:</span><span class="sxs-lookup"><span data-stu-id="de771-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="de771-118">En este tutorial, revisaremos la implementación del Solver orbital y el Solver de la vista radial.</span><span class="sxs-lookup"><span data-stu-id="de771-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="de771-119">Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, puede visitar la guía de [soluciones](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="de771-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="de771-120">Usar un Solver para seguir al usuario</span><span class="sxs-lookup"><span data-stu-id="de771-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="de771-121">En esta sección, mejorará la colección de botones que creó en el tutorial anterior para que siga la dirección del usuario.</span><span class="sxs-lookup"><span data-stu-id="de771-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="de771-122">Además, también configurará el Solver para que la colección de botones sea siempre:</span><span class="sxs-lookup"><span data-stu-id="de771-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="de771-123">Girado en paralelo a la dirección de lectura del usuario, para la lectura natural de izquierda a derecha</span><span class="sxs-lookup"><span data-stu-id="de771-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="de771-124">Se coloca ligeramente por debajo de la dirección de miración horizontal del usuario, por lo que no obstaculiza los otros objetos que se agregarán más adelante en este tutorial.</span><span class="sxs-lookup"><span data-stu-id="de771-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="de771-125">Se coloca aproximadamente a la longitud de un brazo del usuario, por lo que los botones se pueden presionar fácilmente</span><span class="sxs-lookup"><span data-stu-id="de771-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="de771-126">Para ello, usará el **Solver orbital** , que bloquea el objeto en una posición y desplazamiento especificados desde el objeto al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="de771-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="de771-127">1. agregar el Solver orbital</span><span class="sxs-lookup"><span data-stu-id="de771-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="de771-128">En la ventana jerarquía, seleccione el objeto **ButtonCollection** y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente **orbital (Script)** al objeto ButtonCollection.</span><span class="sxs-lookup"><span data-stu-id="de771-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="de771-129">Al agregar un Solver, en este caso, el componente orbital (Script), se agrega automáticamente el componente de controlador de Solver (Script) porque lo requiere el solucionador.</span><span class="sxs-lookup"><span data-stu-id="de771-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="de771-130">2. configurar el Solver orbital</span><span class="sxs-lookup"><span data-stu-id="de771-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="de771-131">Configurar el componente de **controlador de Solver (Script)** :</span><span class="sxs-lookup"><span data-stu-id="de771-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="de771-132">Compruebe que el tipo de destino del que se ha **realizado el seguimiento** está establecido en **principal**</span><span class="sxs-lookup"><span data-stu-id="de771-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="de771-133">Configure el componente **orbital (Script)** :</span><span class="sxs-lookup"><span data-stu-id="de771-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="de771-134">Comprobar que el **tipo de orientación** está establecido en seguimiento del **objeto controlado**</span><span class="sxs-lookup"><span data-stu-id="de771-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="de771-135">Restablecer **desplazamiento local** a X = 0, y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="de771-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="de771-136">Cambiar el **desplazamiento de mundo** a X = 0, y =-0,4, Z = 0,3</span><span class="sxs-lookup"><span data-stu-id="de771-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="de771-138">3. probar el Solver orbital mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="de771-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="de771-139">Presione el botón reproducir para entrar en el modo de juego y mantenga presionado el botón secundario del mouse para girar la dirección de miración y observe lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="de771-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="de771-140">La posición de transformación de ButtonCollection ahora está controlada por la configuración de Solver</span><span class="sxs-lookup"><span data-stu-id="de771-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="de771-141">El cubo, que no se ve afectado por el Solver, permanece en la misma posición</span><span class="sxs-lookup"><span data-stu-id="de771-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="de771-143">Si no ve el rayo de la cámara en la ventana de la escena, asegúrese de que el menú de Gizmos está habilitado.</span><span class="sxs-lookup"><span data-stu-id="de771-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="de771-144">Para más información sobre el menú Gizmos y cómo puede usarlo para optimizar la vista de escenas, puede visitar la documentación del <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menú Gizmos</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="de771-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="de771-145">Para mostrar la escena y la ventana de juego en paralelo, tal y como se muestra en la imagen anterior, basta con arrastrar la ventana de juego hasta el lado derecho de la ventana de la escena.</span><span class="sxs-lookup"><span data-stu-id="de771-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="de771-146">Para obtener más información sobre cómo personalizar el área de trabajo, puede visitar la documentación personalización de Unity en <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">el área de trabajo</a> .</span><span class="sxs-lookup"><span data-stu-id="de771-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="de771-147">Habilitar objetos para seguir manos de seguimiento</span><span class="sxs-lookup"><span data-stu-id="de771-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="de771-148">En esta sección, configurará el objeto de cubo que ha creado en el tutorial anterior para que siga las manos controladas por el usuario, en concreto la muñeca de la mano derecha.</span><span class="sxs-lookup"><span data-stu-id="de771-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="de771-149">Además, también configurará el Solver para que el cubo:</span><span class="sxs-lookup"><span data-stu-id="de771-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="de771-150">Cambia su orientación con la rotación del usuario.</span><span class="sxs-lookup"><span data-stu-id="de771-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="de771-151">Colocado en la muñeca del usuario</span><span class="sxs-lookup"><span data-stu-id="de771-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="de771-152">Para ello, usará la **vista radial Solver** , que mantiene el objeto dentro de un cono de vista convertido por el objeto al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="de771-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="de771-153">1. agregar la vista radial Solver</span><span class="sxs-lookup"><span data-stu-id="de771-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="de771-154">En la ventana jerarquía, seleccione el objeto de **cubo** y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el objeto de cubo componente de **vista radial (Script)** .</span><span class="sxs-lookup"><span data-stu-id="de771-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="de771-155">2. configurar el Solver de la vista radial</span><span class="sxs-lookup"><span data-stu-id="de771-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="de771-156">Configurar el componente de **controlador de Solver (Script)** :</span><span class="sxs-lookup"><span data-stu-id="de771-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="de771-157">Cambiar el tipo de destino del que se **realiza el seguimiento** a la **Unión manual**</span><span class="sxs-lookup"><span data-stu-id="de771-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="de771-158">Cambiar la **mano sometida a seguimiento** a la **derecha**</span><span class="sxs-lookup"><span data-stu-id="de771-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="de771-159">Cambio de **conjunto de mano** controlado a **muñeca**</span><span class="sxs-lookup"><span data-stu-id="de771-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="de771-160">Configure el componente de **vista radial (Script)** :</span><span class="sxs-lookup"><span data-stu-id="de771-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="de771-161">Cambiar la **dirección de referencia** a **orientada a objetos**y activar la casilla **orientar a la dirección de referencia**</span><span class="sxs-lookup"><span data-stu-id="de771-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="de771-162">Cambiar la **distancia mínima** y la **distancia máxima** a 0</span><span class="sxs-lookup"><span data-stu-id="de771-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="de771-164">3. probar la vista radial Solver mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="de771-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="de771-165">Presione el botón reproducir para entrar en el modo de juego y, a continuación, mantenga presionada la barra espaciadora para abrirla.</span><span class="sxs-lookup"><span data-stu-id="de771-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="de771-166">Mueva el cursor del mouse para mover la mano y haga clic y mantenga presionado el botón primario del mouse para girar la mano:</span><span class="sxs-lookup"><span data-stu-id="de771-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="de771-168">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="de771-168">Congratulations</span></span>

<span data-ttu-id="de771-169">En este tutorial, aprendió a usar los solucionadores de MRTK para que una interfaz de usuario pueda seguir de forma intuitiva al usuario.</span><span class="sxs-lookup"><span data-stu-id="de771-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="de771-170">También ha aprendido cómo adjuntar un Solver a un objeto (es decir, un cubo) para seguir las manos controladas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="de771-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="de771-171">Para obtener más información sobre estos y otros solucionadores que se incluyen en MRTK, puede visitar la guía de [soluciones](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="de771-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="de771-172">Siguiente tutorial: 5. interactuar con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="de771-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
