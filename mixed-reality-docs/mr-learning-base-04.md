---
title: 'Tutoriales de introducción: 4. Posicionamiento de los objetos en la escena'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 356bfa788cd28e8c763a45a2d44c3a1241b8467e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306468"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="13186-105">4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="13186-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="13186-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="13186-106">Overview</span></span>

<span data-ttu-id="13186-107">En este tutorial, importará los recursos del tutorial y colocará los objetos proporcionados en la escena.</span><span class="sxs-lookup"><span data-stu-id="13186-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="13186-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="13186-108">Objectives</span></span>

* <span data-ttu-id="13186-109">Obtener información sobre cómo colocar objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="13186-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="13186-110">Aprender a usar la característica de colección de objetos de la cuadrícula de MRTK</span><span class="sxs-lookup"><span data-stu-id="13186-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="13186-111">Importación de los recursos del tutorial</span><span class="sxs-lookup"><span data-stu-id="13186-111">Importing the tutorial assets</span></span>

<span data-ttu-id="13186-112">Descargue e importe el paquete personalizado de Unity siguiente:</span><span class="sxs-lookup"><span data-stu-id="13186-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="13186-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="13186-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="13186-114">Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="13186-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="13186-116">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="13186-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="13186-117">Creación del objeto principal</span><span class="sxs-lookup"><span data-stu-id="13186-117">Creating the parent object</span></span>

<span data-ttu-id="13186-118">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena:</span><span class="sxs-lookup"><span data-stu-id="13186-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="13186-120">Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena).</span><span class="sxs-lookup"><span data-stu-id="13186-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="13186-121">Para obtener más información sobre cómo personalizar el área de trabajo, puedes consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="13186-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="13186-122">Haga clic con el botón derecho en el objeto recién creado, seleccione **Rename** (Cambiar nombre) y cambie el nombre a **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="13186-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="13186-124">Con el objeto RoverExplorer todavía seleccionado, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="13186-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="13186-125">**Posición**: X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="13186-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="13186-126">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="13186-127">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="13186-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="13186-129">La cámara representa la cabeza del usuario y se coloca en el origen, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="13186-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="13186-130">En general, 1 unidad en Unity es aproximadamente 1 metro en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="13186-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="13186-131">Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.</span><span class="sxs-lookup"><span data-stu-id="13186-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="13186-132">En el escenario anterior, el objeto RoverExplorer se coloca a 2 metros por delante y 0,6 metros por debajo de la cabeza del usuario.</span><span class="sxs-lookup"><span data-stu-id="13186-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="13186-133">Adición de los elementos prefabricados del tutorial</span><span class="sxs-lookup"><span data-stu-id="13186-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="13186-134">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**:</span><span class="sxs-lookup"><span data-stu-id="13186-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="13186-136">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.</span><span class="sxs-lookup"><span data-stu-id="13186-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="13186-137">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **Table** (Tabla) sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="13186-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="13186-138">**Posición**: X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="13186-139">**Rotación**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="13186-140">**Escala**: X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="13186-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="13186-142">Para mostrar la escena tal y como se muestra en la imagen anterior, use <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo de escena), situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z, haga doble clic en el objeto MixedRealityPlayspace para enfocar la cámara y acérquese según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="13186-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="13186-143">En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **RoverAssembly** sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="13186-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="13186-144">**Posición**: X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="13186-145">**Rotación**: X = 0, Y = 135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="13186-146">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="13186-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="13186-148">Organización de los objetos de una colección</span><span class="sxs-lookup"><span data-stu-id="13186-148">Organizing objects in a collection</span></span>

<span data-ttu-id="13186-149">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **RoverParts** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="13186-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="13186-150">**Posición**: X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="13186-151">**Rotación**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="13186-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="13186-152">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="13186-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="13186-154">En la ventana Hierarchy (Jerarquía), seleccione todos los objetos secundarios de RoverExplorer > RoverAssembly > RoverModel > **Parts**, haga clic derecho en ellos y seleccione **Duplicate** (Duplicar) para crear una copia de cada una de las partes:</span><span class="sxs-lookup"><span data-stu-id="13186-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="13186-156">Para seleccionar varios objetos adyacentes, mantenga presionada la tecla Mayús mientras usa el mouse para seleccionar el primer y el último objeto.</span><span class="sxs-lookup"><span data-stu-id="13186-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="13186-157">Con los objetos secundarios de Parts recién duplicados todavía seleccionados, haga clic en ellos y arrástrelos sobre el objeto **RoverParts** para convertirlos en objetos secundarios del objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="13186-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="13186-159">Para que resulte más fácil trabajar con la escena, en la ventana Hierarchy (Jerarquía), haga clic en el icono del **ojo** situado a la izquierda del objeto para desactivar la **visibilidad de la escena** para el objeto **RoverExplorer**.</span><span class="sxs-lookup"><span data-stu-id="13186-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverExplorer** object off.</span></span> <span data-ttu-id="13186-160">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:</span><span class="sxs-lookup"><span data-stu-id="13186-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="13186-162">Para obtener más información sobre los controles de visibilidad de la escena y cómo puede usarlos para optimizar la vista de la escena y el flujo de trabajo, puede consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="13186-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="13186-163">En la ventana Hierarchy (Jerarquía), borre los nombres de los objetos secundarios de RoverParts reemplazando el **(1)** anexado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="13186-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="13186-165">En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverParts**; a continuación, en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione **GridObjectCollection** para agregar el componente GridObjectCollection al objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="13186-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="13186-167">Configure los valores del componente **GridObjectCollection** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="13186-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="13186-168">**Tipo de orden**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="13186-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="13186-169">**Diseño**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="13186-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="13186-170">**Ancho de celda**: 0.25</span><span class="sxs-lookup"><span data-stu-id="13186-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="13186-171">**Distancia desde el elemento principal**: 0.38</span><span class="sxs-lookup"><span data-stu-id="13186-171">**Distance from parent**: 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="13186-173">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios de RoverParts:</span><span class="sxs-lookup"><span data-stu-id="13186-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="13186-175">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="13186-175">Congratulations</span></span>

<span data-ttu-id="13186-176">En este tutorial, ha aprendido a colocar objetos en la escena en relación con el usuario y a usar la característica de colección de objetos de la cuadrícula de MRTK para organizar los objetos de una colección.</span><span class="sxs-lookup"><span data-stu-id="13186-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="13186-177">Tutorial siguiente: 5. Creación de contenido dinámico mediante el uso de solucionadores</span><span class="sxs-lookup"><span data-stu-id="13186-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
