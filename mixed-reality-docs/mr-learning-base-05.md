---
title: 'Tutoriales de introducción: 5. Creación de contenido dinámico mediante solucionadores'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 1a5017d8bc18ef239db88ee62cb2b65c77b2ab6f
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376617"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="51020-105">5. Creación de contenido dinámico mediante solucionadores</span><span class="sxs-lookup"><span data-stu-id="51020-105">5. Creating dynamic content using Solvers</span></span>

## <a name="overview"></a><span data-ttu-id="51020-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="51020-106">Overview</span></span>

<span data-ttu-id="51020-107">En este tutorial, explorará distintas formas de colocar hologramas de forma dinámica mediante las herramientas de selección de ubicación disponibles de MRTK, conocidas como "solucionadores", para resolver escenarios de selección de ubicación espacial complejos.</span><span class="sxs-lookup"><span data-stu-id="51020-107">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="51020-108">En MRTK, los solucionadores son un sistema de scripts y comportamientos que se usaron para permitir que los objetos sigan al usuario o a otros objetos de juego en la escena.</span><span class="sxs-lookup"><span data-stu-id="51020-108">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="51020-109">También pueden usarse para acoplarse en ciertas posiciones, de modo que la aplicación sea más intuitiva.</span><span class="sxs-lookup"><span data-stu-id="51020-109">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="51020-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="51020-110">Objectives</span></span>

* <span data-ttu-id="51020-111">Introducir los solucionadores de MRTK</span><span class="sxs-lookup"><span data-stu-id="51020-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="51020-112">Aprender a usar los solucionadores para dirigir al usuario a objetos</span><span class="sxs-lookup"><span data-stu-id="51020-112">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="51020-113">Aprender a usar los solucionadores para cambiar la posición de los objetos</span><span class="sxs-lookup"><span data-stu-id="51020-113">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="51020-114">Ubicación de los solucionadores en MRTK</span><span class="sxs-lookup"><span data-stu-id="51020-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="51020-115">Los solucionadores de MRTK se encuentran en la carpeta del SDK de MRTK.</span><span class="sxs-lookup"><span data-stu-id="51020-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="51020-116">Para ver los solucionadores disponibles en el proyecto, en la ventana Project (Proyecto), navegue a **Assets** (Recursos)  > **MRTK** > **SDK** > **Features** (Características)  > **Utilities** (Utilidades)  > **Solvers** (Solucionadores):</span><span class="sxs-lookup"><span data-stu-id="51020-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="51020-118">En este tutorial, revisaremos la implementación de los solucionadores Directional Indicator (Indicador direccional) y Tap To Place (Pulsar para colocar).</span><span class="sxs-lookup"><span data-stu-id="51020-118">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="51020-119">Para obtener más información acerca de la gama completa de solucionadores disponibles en MRTK, puede consultar la guía [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="51020-119">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!NOTE]
> <span data-ttu-id="51020-120">El solucionador de indicador direccional no se encuentra en las carpetas de solucionadores a las que se hace referencia anteriormente, sino en las carpetas Assets > MRTK > SDK > Experimental > Features > Utilities (Recursos > MRTK > SDK > Experimental > Características > Utilidades), ya que es una característica experimental.</span><span class="sxs-lookup"><span data-stu-id="51020-120">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Assets > MRTK > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="51020-121">Uso del solucionador Directional Indicator (Indicador direccional) para dirigir al usuario a objetos</span><span class="sxs-lookup"><span data-stu-id="51020-121">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="51020-122">En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.GettingStarted** > carpeta **Prefabs** (Recursos prefabricados), haga clic y arrastre el elemento prefabricado **Chevron** (Botón de contenido adicional) a la ventana Jerarquía y establezca su **Posición** de transformación en X = 0, Y = 0, Z = 2 para colocarlo cerca del objeto RoverExplorer:</span><span class="sxs-lookup"><span data-stu-id="51020-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="51020-124">Si observa que la cámara u otros iconos de la escena ocultan otros objetos o son distracciones, puede ocultarlos al <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">desactivar el menú Gizmos</a>, tal como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="51020-124">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="51020-125">Para obtener más información sobre el menú Gizmos y cómo puede usarlo para optimizar la vista de escenas, consulte la documentación sobre el <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menú de Gizmos </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="51020-125">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="51020-126">Cambie el nombre del objeto de botón de contenido adicional **Indicator** recién agregado y, a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar el componente **DirectionalIndicator** y **Directional Indicator Controller (Script)** (Controlador de indicador direccional [script]):</span><span class="sxs-lookup"><span data-stu-id="51020-126">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator** and the **Directional Indicator Controller (Script)** component:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="51020-128">Al agregar un solucionador (en este caso, el componente DirectionalIndicator), se agrega automáticamente el componente SolverHandler porque los solucionadores lo requieren.</span><span class="sxs-lookup"><span data-stu-id="51020-128">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="51020-129">El componente Directional Indicator Controller (Script) (Controlador de indicador direccional [script]) no forma parte de MRTK, pero se incluyó con los recursos del tutorial.</span><span class="sxs-lookup"><span data-stu-id="51020-129">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="51020-130">Configure los componentes DirectionalIndicator y SolverHandler como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="51020-130">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="51020-131">Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Cabeza**.</span><span class="sxs-lookup"><span data-stu-id="51020-131">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="51020-132">Asigne **RoverExplorer** al campo **Directional Target** (Objetivo direccional) del componente **DirectionalIndicator**; para ello, arrástrelo desde la ventana Jerarquía hasta el campo **None (Transform)** (Ninguno [transformación]).</span><span class="sxs-lookup"><span data-stu-id="51020-132">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="51020-133">Cambie el valor de **View Offset** (Desplazamiento de vista) a 0,2.</span><span class="sxs-lookup"><span data-stu-id="51020-133">Change the **View Offset** to 0.2</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="51020-135">Presione el botón Play (Jugar) para entrar en el modo de juego y mantenga presionado el botón derecho del mouse mientras mueve el mouse hacia la izquierda o derecha para girar la dirección de la mirada y observe lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="51020-135">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="51020-136">Cuando aparte la mirada del objeto RoverExplorer, el objeto Indicator aparecerá y apuntará hacia el objeto RoverExplorer.</span><span class="sxs-lookup"><span data-stu-id="51020-136">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="51020-138">Si no ve el rayo de la cámara en la ventana de la escena, asegúrese de que el menú Gizmos esté habilitado como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="51020-138">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="51020-139">Para obtener información sobre cómo usar la simulación de entrada del editor, puedes consultar la guía [Uso de la simulación de entrada de mano en el editor para probar una escena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="51020-139">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!TIP]
> <span data-ttu-id="51020-140">Si el equipo tiene un micrófono, puede alternar fácilmente el estado activo del panel Diagnóstico que aparece en la ventana del juego mediante el comando de voz "toggle diagnostics" (alternar diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="51020-140">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="51020-141">También puede deshabilitarlo en MRTK Configuration Profile > Diagnostics > Enable Diagnostics System (Perfil de configuración de MRTK > Diagnóstico > Habilitar sistema de diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="51020-141">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="51020-142">Sin embargo, por lo general, se recomienda mantener el sistema de diagnóstico activo durante el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="51020-142">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="51020-143">Uso del solucionador Tap to Place (Pulsar para colocar) para cambiar la posición de los objetos</span><span class="sxs-lookup"><span data-stu-id="51020-143">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="51020-144">En la ventana Jerarquía, seleccione RoverExplorer > objeto **RoverAssembly** y, a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar el componente **Tap To Place (Script)** (Pulsar para colocar [script]) y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="51020-144">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="51020-145">Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Cabeza**.</span><span class="sxs-lookup"><span data-stu-id="51020-145">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="51020-146">Active la casilla **Keep Orientation Vertical** (Mantener la orientación vertical).</span><span class="sxs-lookup"><span data-stu-id="51020-146">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="51020-147">En la lista desplegable **Magnetic Surfaces** (Superficies magnéticas)  > **Elemento 0**, desactive todas las opciones excepto **Spatial Awareness** (Reconocimiento espacial).</span><span class="sxs-lookup"><span data-stu-id="51020-147">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="51020-149">La configuración de superficies magnéticas determina qué objetos puede detectar el componente Tap to Place (Pulsar para colocar) al colocar un objeto.</span><span class="sxs-lookup"><span data-stu-id="51020-149">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="51020-150">Al cambiar la configuración a solo Reconocimiento espacial, el componente Tap To Place (Script) (Pulsar para colocar [script]) solo podrá colocar el Rover en objetos de la capa de Unity denominada Spatial Awareness, que de forma predeterminada es la malla de reconocimiento espacial generada por HoloLens.</span><span class="sxs-lookup"><span data-stu-id="51020-150">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="51020-151">Para obtener más información sobre las capas, puede consultas la documentación sobre <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">capas</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="51020-151">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="51020-152">Si quiere ver la malla de reconocimiento espacial al probar la función Tap To Place (Pulsar para colocar) en HoloLens, puede establecer temporalmente la opción de visualización del observador de malla espacial en Visible.</span><span class="sxs-lookup"><span data-stu-id="51020-152">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="51020-153">Para recibir un recordatorio sobre cómo cambiar la opción de visualización, puede consultar las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="51020-153">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="51020-154">Con el objeto RoverAssembly aún seleccionado en la ventana Jerarquía, desde la ventana Inspector, busque el evento **On Placing Started ()** y haga clic en el icono **+** para agregar un nuevo evento:</span><span class="sxs-lookup"><span data-stu-id="51020-154">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="51020-156">Configure el evento de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="51020-156">Configure the event as follows:</span></span>

* <span data-ttu-id="51020-157">Asigne el objeto **RoverAssembly** como cliente de escucha para el evento On Placing Started () arrastrándolo desde la ventana Jerarquía hasta el campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="51020-157">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="51020-158">En la lista desplegable **Ninguna función**, seleccione **TapToPlace** > **float SurfaceNormalOffset** (SurfaceNormalOffset tipo float) para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="51020-158">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="51020-159">Compruebe que el argumento esté establecido en **0**</span><span class="sxs-lookup"><span data-stu-id="51020-159">Verify that the argument is set to **0**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="51020-161">En la ventana Jerarquía, haga clic con el botón secundario en una zona vacía y seleccione **Objeto 3D** > **Cubo**, para crear un objeto temporal que represente el suelo y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="51020-161">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="51020-162">**Posición**: X = 0, Y = -1,65, Z = 6</span><span class="sxs-lookup"><span data-stu-id="51020-162">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="51020-163">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="51020-163">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="51020-164">**Escala**: X = 10, Y = 0,2, Z = 10</span><span class="sxs-lookup"><span data-stu-id="51020-164">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="51020-166">Con el cubo temporal seleccionado todavía en la ventana Jerarquía, desde la ventana Inspector, use la lista desplegable **Capas** para cambiar la configuración de la capa del cubo únicamente para incluir la capa **Spatial Awareness** (Reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="51020-166">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="51020-168">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionado el botón derecho del mouse mientras mueve el mouse hacia abajo hasta que la mirada entre en contacto con el objeto RoverAssembly:</span><span class="sxs-lookup"><span data-stu-id="51020-168">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="51020-170">Haga clic en el botón izquierdo del mouse para iniciar el proceso para pulsar y colocar:</span><span class="sxs-lookup"><span data-stu-id="51020-170">Click the left mouse button to start the tap-to-place process:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="51020-172">Mantenga presionado el botón derecho del mouse mientras mueve el mouse hacia la izquierda o derecha para girar la dirección de la mirada; cuando esté satisfecho con su ubicación, haga clic con el botón izquierdo del mouse:</span><span class="sxs-lookup"><span data-stu-id="51020-172">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="51020-174">Una vez que haya terminado de probar la característica en el modo de juego, haga clic con el botón derecho en el objeto de cubo y seleccione **Eliminar** para quitarlo de la escena:</span><span class="sxs-lookup"><span data-stu-id="51020-174">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="51020-176">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="51020-176">Congratulations</span></span>

<span data-ttu-id="51020-177">En este tutorial, aprendió a usar el solucionador Directional Indicator (Indicador direccional) de MRTK para que un elemento de la interfaz de usuario dirige de forma intuitiva al usuario a los objetos.</span><span class="sxs-lookup"><span data-stu-id="51020-177">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="51020-178">También aprendió a usar el solucionador Tap To Place (Pulsar para colocar) para cambiar la posición de los objetos fácilmente.</span><span class="sxs-lookup"><span data-stu-id="51020-178">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="51020-179">Para más información sobre estos y otros solucionadores incluidos con MRTK, consulte la guía de [solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="51020-179">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="51020-180">Tutorial siguiente: 6. Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="51020-180">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
