---
title: 'Tutoriales de introducción: 5. Interacción con objetos 3D'
description: Obtén información sobre el contenido 3D básico y las experiencias de usuario, como la organización de objetos 3D y cuadros de límite para la manipulación básica.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 419b381c1240b2cc10708eab03245ed3aabfa859
ms.sourcegitcommit: 61291e83536c8cb2e8401a8e66060128ede35922
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416137"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="9d5a4-105">5. Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="9d5a4-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="9d5a4-106">En este tutorial, obtendrás información sobre el contenido 3D básico y la experiencia del usuario; por ejemplo, la organización de objetos 3D como parte de una colección, cuadros de límite para la manipulación básica, interacción próxima y lejana, y gestos de tocar y agarrar con seguimiento de manos.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="9d5a4-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9d5a4-107">Objectives</span></span>

* <span data-ttu-id="9d5a4-108">Crear un panel de objetos 3D que se usará para otros objetivos de aprendizaje</span><span class="sxs-lookup"><span data-stu-id="9d5a4-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="9d5a4-109">Implementar rectángulos de selección</span><span class="sxs-lookup"><span data-stu-id="9d5a4-109">Implement bounding boxes</span></span>
* <span data-ttu-id="9d5a4-110">Configurar objetos 3D para la manipulación básica, como mover, girar y escalar</span><span class="sxs-lookup"><span data-stu-id="9d5a4-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="9d5a4-111">Explorar la interacción próxima y lejana</span><span class="sxs-lookup"><span data-stu-id="9d5a4-111">Explore near and far interaction</span></span>
* <span data-ttu-id="9d5a4-112">Más información sobre otros gestos de seguimiento de manos, como agarrar y tocar</span><span class="sxs-lookup"><span data-stu-id="9d5a4-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9d5a4-113">Importación de los activos del tutorial</span><span class="sxs-lookup"><span data-stu-id="9d5a4-113">Importing the tutorial assets</span></span>

<span data-ttu-id="9d5a4-114">Descarga e importa el paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="9d5a4-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9d5a4-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="9d5a4-116">Después de importar los recursos del tutorial, la ventana del proyecto debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="9d5a4-118">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="9d5a4-119">Limpieza de la vista de escena</span><span class="sxs-lookup"><span data-stu-id="9d5a4-119">Decluttering the scene view</span></span>

<span data-ttu-id="9d5a4-120">Para que resulte más fácil trabajar con la escena, define la **visibilidad de la escena** para los objetos **Cube** y **ButtonCollection** como desactivada haciendo clic en el icono de **ojo** situado a la izquierda de los objetos.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="9d5a4-121">Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="9d5a4-123">Para obtener más información sobre los controles de visibilidad de la escena y cómo puedes usarlos para optimizar la vista de la escena y el flujo de trabajo, visita la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="9d5a4-124">Organización de los objetos 3D de una colección</span><span class="sxs-lookup"><span data-stu-id="9d5a4-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="9d5a4-125">En esta sección, crearás un panel de objetos 3D que usarás al explorar varias formas de interactuar con objetos 3D en las siguientes secciones de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="9d5a4-126">En concreto, configurarás los objetos 3D para que se coloquen en una cuadrícula de 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="9d5a4-127">Del mismo modo que cuando [creaste un panel de botones](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9d5a4-128">Asignar los objetos 3D a un objeto principal</span><span class="sxs-lookup"><span data-stu-id="9d5a4-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="9d5a4-129">Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="9d5a4-130">1. Asignar los objetos 3D a un objeto principal</span><span class="sxs-lookup"><span data-stu-id="9d5a4-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="9d5a4-131">En la ventana Hierarchy (Jerarquía), **crea un objeto vacío**, asígnale un nombre adecuado; por ejemplo, **3DObjectCollection** y colócalo en una ubicación adecuada, como X = 0, Y = -0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="9d5a4-132">En la ventana Project (Proyecto), ve a **Assets** (Recursos) > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Objetos prefabricados) y, a continuación, **asigna** los siguientes objetos prefabricados a la colección **3DObjectCollection** principal:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="9d5a4-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="9d5a4-133">Cheese</span></span>
* <span data-ttu-id="9d5a4-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="9d5a4-134">CoffeeCup</span></span>
* <span data-ttu-id="9d5a4-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="9d5a4-135">EarthCore</span></span>
* <span data-ttu-id="9d5a4-136">Octa</span><span class="sxs-lookup"><span data-stu-id="9d5a4-136">Octa</span></span>
* <span data-ttu-id="9d5a4-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="9d5a4-137">Platonic</span></span>
* <span data-ttu-id="9d5a4-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="9d5a4-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="9d5a4-140">En la ventana Hierarchy (Jerarquía), **crea tres cubos** como objetos secundarios de **3DObjectCollection** y define su **escala** de transformación como X = 0,15, Y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="9d5a4-142">Para obtener un recordatorio sobre cómo realizar los pasos indicados anteriormente, consulta el tutorial [Crear la interfaz de usuario y configurar Mixed Reality Toolkit](mrlearning-base-ch2.md).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="9d5a4-143">Cambia la posición de los cubos para poder verlos todos:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="9d5a4-145">En la ventana Project (Proyecto), desplázate hasta **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** (Recursos > MixedRealityToolkit.SDK > StandardAssets > Materials) para ver los materiales proporcionados con MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="9d5a4-146">**Haz clic y arrastra** un material adecuado a la propiedad 0 del elemento **Materials** (Materiales) del representador de malla de cada cubo; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="9d5a4-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="9d5a4-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="9d5a4-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="9d5a4-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="9d5a4-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="9d5a4-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="9d5a4-151">2. Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="9d5a4-152">Agrega un componente **Grid Object Collection (Script)** (Colección de objetos de cuadrícula [script]) al objeto **3DObjectCollection** y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="9d5a4-153">Cambia el valor de **Sort Type** (Tipo de orden) a **Child Order** (Orden secundario) para asegurarte de que los objetos secundarios se ordenan en el orden en el que los coloques bajo el objeto principal.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="9d5a4-154">A continuación, haz clic en el botón **Actualizar colección** para aplicar la nueva configuración:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="9d5a4-156">Manipulación de objetos 3D</span><span class="sxs-lookup"><span data-stu-id="9d5a4-156">Manipulating 3D objects</span></span>

<span data-ttu-id="9d5a4-157">En esta sección, agregarás la capacidad de manipular todos los objetos 3D del panel que creaste en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="9d5a4-158">Además, en el caso de los objetos prefabricados, permitirás que los usuarios accedan a los objetos y los agarren con el seguimiento de manos.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="9d5a4-159">A continuación, explorarás algunos comportamientos de manipulación que puedes aplicar a los objetos.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="9d5a4-160">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9d5a4-161">Agregar el componente Manipulation Handler (Script) (Controlador de manipulación [script]) a todos los objetos</span><span class="sxs-lookup"><span data-stu-id="9d5a4-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="9d5a4-162">Agregar el componente Near Interaction Grabbable (Script) (Interacción próxima de agarre [script]) a los objetos prefabricados</span><span class="sxs-lookup"><span data-stu-id="9d5a4-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="9d5a4-163">Configurar el componente Manipulation Handler (Script) (Controlador de manipulación [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d5a4-164">Para poder **manipular un objeto**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9d5a4-165">Componente **Collider**; por ejemplo, un colisionador de cuadro</span><span class="sxs-lookup"><span data-stu-id="9d5a4-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="9d5a4-166">Componente **Manipulation Handler (Script)** (Controlador de manipulación [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="9d5a4-167">Para poder **manipular** y **agarrar un objeto con seguimiento de manos**, el objeto debe tener los componentes siguientes:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9d5a4-168">Componente **Collider**; por ejemplo, un colisionador de cuadro</span><span class="sxs-lookup"><span data-stu-id="9d5a4-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="9d5a4-169">Componente **Manipulation Handler (Script)** (Controlador de manipulación [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="9d5a4-170">Componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="9d5a4-171">1. Agregar el componente Manipulation Handler (Script) (Controlador de manipulación [script]) a todos los objetos</span><span class="sxs-lookup"><span data-stu-id="9d5a4-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="9d5a4-172">En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cheese**, mantén presionada la tecla **Mayús** y, a continuación, selecciona el objeto **Cube () 2** y agrega el componente **Manipulation Handler (Script)** (Controlador de manipulación [script]) a todos los objetos:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9d5a4-174">Para los fines de este tutorial, los colisionadores ya se han agregado a los objetos prefabricados.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="9d5a4-175">En el caso de los elementos primitivos de Unity, como los objetos Cube, el componente Collider se agrega automáticamente al crear el objeto.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="9d5a4-176">En la imagen anterior, los colisionadores se representan mediante contornos verdes.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="9d5a4-177">Para obtener más información sobre los colisionadores, visita la documentación sobre <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">colisionadores</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="9d5a4-178">2. Agregar el componente Near Interaction Grabbable (Script) (Interacción próxima de agarre [script]) a los objetos prefabricados</span><span class="sxs-lookup"><span data-stu-id="9d5a4-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="9d5a4-179">En la ventana Jerarquía, selecciona el objeto **Cheese**, mantén presionada la tecla **Mayús** y, a continuación, selecciona el objeto **TheModule** y agrega el componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script]) a todos los objetos:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="9d5a4-181">3. Configurar el componente Manipulation Handler (Script) (Controlador de manipulación [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="9d5a4-182">Manipulación predeterminada</span><span class="sxs-lookup"><span data-stu-id="9d5a4-182">Default manipulation</span></span>

<span data-ttu-id="9d5a4-183">Para el objeto **Cube**, deja todas las propiedades en el valor predeterminado para experimentar el comportamiento de manipulación predeterminado:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="9d5a4-185">Para restablecer los valores predeterminados de un componente, puedes seleccionar el icono de configuración del componente y seleccionar Restablecer.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="9d5a4-186">Restringir la manipulación solo a escala</span><span class="sxs-lookup"><span data-stu-id="9d5a4-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="9d5a4-187">En el caso del objeto **Cube (1)** , cambia **Two Handed Manipulation Type** (Manipulación con dos manos) a **Escala** para que solo el usuario pueda cambiar el tamaño del objeto:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="9d5a4-189">Restringir el movimiento a una distancia fija del usuario</span><span class="sxs-lookup"><span data-stu-id="9d5a4-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="9d5a4-190">En el caso del objeto **Cube (2)** , cambia **Constraint On Movement** (Limitación del movimiento) a **Fix Distance From Head** (Corregir distancia de la cabeza) para que, cuando el objeto se mueva, permanezca a la misma distancia del usuario:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="9d5a4-192">Manipulación de agarre predeterminada</span><span class="sxs-lookup"><span data-stu-id="9d5a4-192">Default grabbable manipulation</span></span>

<span data-ttu-id="9d5a4-193">En el caso de los objetos **Cheese**, **CoffeCup** y **EarthCore**, deja todas las propiedades con sus valores predeterminados para experimentar el comportamiento de manipulación de agarre predeterminado:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="9d5a4-195">Quitar la capacidad de manipulación remota</span><span class="sxs-lookup"><span data-stu-id="9d5a4-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="9d5a4-196">En el caso del objeto **Octa**, desactiva la casilla **Allow Far Manipulation** (Permitir manipulación remota) para que el usuario solo pueda interactuar con el objeto directamente mediante el seguimiento de manos:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="9d5a4-198">Hacer que un objeto gire alrededor de su centro</span><span class="sxs-lookup"><span data-stu-id="9d5a4-198">Make an object rotate around its center</span></span>

<span data-ttu-id="9d5a4-199">En el caso del objeto **Platonic**, cambia **One Hand Rotation Mode Near** (Modo de rotación de una mano próximo) y **One Hand Rotation Mode Far** (Modo de rotación de una mano remoto) a **Rotate About Object Center** (Girar alrededor del centro de un objeto) para que, cuando el usuario gire el objeto con una mano, gire alrededor del centro del objeto:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="9d5a4-201">Mantener el movimiento después de liberar el objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-201">Keep movement after object is released</span></span>

<span data-ttu-id="9d5a4-202">Para el objeto **TheModule**, agrega un componente **Rigidbody** para habilitar la física y, a continuación, desactiva la casilla **Use Gravity** (Usar gravedad) para que el objeto no se vea afectado por la gravedad:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="9d5a4-204">De nuevo en el componente Manipulation Handler (Script) (Controlador de manipulación [script]), comprueba que **Release Behavior** (Comportamiento de liberación) se haya establecido en **Keep Velocity** (Conservar velocidad) y **Keep Angular Velocity** (Conservar velocidad angular) para que, una vez que el objeto se libere de la mano del usuario, siga moviéndose:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="9d5a4-206">Para obtener más información sobre el componente controlador de manipulación y sus propiedades asociadas, consulta la guía del [controlador de manipulación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="9d5a4-207">Adición de cuadros de límite</span><span class="sxs-lookup"><span data-stu-id="9d5a4-207">Adding bounding boxes</span></span>

<span data-ttu-id="9d5a4-208">Los cuadros de límite hacen que manipular objetos con una mano sea más sencillo e intuitivo tanto para la interacción próxima como remota, ya que proporcionan controladores que se pueden usar para el escalado y la rotación.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="9d5a4-209">En este ejemplo, agregarás un cuadro de límite al objeto EarthCore, de modo que se podrá interactuar con este objeto mediante la manipulación de objetos configurada en la sección anterior. También se podrá escalar y girar con los controladores de cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d5a4-210">Para poder usar un **cuadro de límite**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9d5a4-211">Componente **Collider**; por ejemplo, un colisionador de cuadro</span><span class="sxs-lookup"><span data-stu-id="9d5a4-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="9d5a4-212">Componente **Bounding Box (Script)** (Cuadro de límite [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="9d5a4-213">1. Agregar el componenteBounding Box (Script) (Cuadro de límite [script]) al objeto EarthCore</span><span class="sxs-lookup"><span data-stu-id="9d5a4-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="9d5a4-214">En la ventana Inspector, selecciona el objeto **EarthCore** y agrega el componente **Bounding Box (Script)** (Cuadro de límite [script]) al objeto EarthCore:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9d5a4-216">Las visualizaciones del cuadro de límite se crean en tiempo de ejecución y, por tanto, no son visibles antes de entrar en el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="9d5a4-217">2. Visualizar y probar el cuadro de límite mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="9d5a4-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="9d5a4-218">Presiona el botón Jugar para acceder al modo de juego.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="9d5a4-219">A continuación, mantén presionada la barra espaciadora para que aparezca la mano y usa el ratón para interactuar con el cuadro de límite:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="9d5a4-221">Para obtener más información sobre el componente de cuadro de límite y sus propiedades asociadas, puedes visitar la guía sobre el [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="9d5a4-222">Adición de efectos táctiles</span><span class="sxs-lookup"><span data-stu-id="9d5a4-222">Adding touch effects</span></span>

<span data-ttu-id="9d5a4-223">En este ejemplo, permitirás que se desencadenen eventos al tocar un objeto con la mano.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="9d5a4-224">En concreto, configurarás el objeto Octa para que se produzca un efecto sonoro cuando el usuario lo toque.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="9d5a4-225">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="9d5a4-226">Agregar un componente de origen de audio al objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="9d5a4-227">Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script]) al objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="9d5a4-228">Agregar el componente Hand Interaction Touch (Script) (Componente de interacción de mano [script]) al objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="9d5a4-229">Implementar el evento On Touch Started (Iniciado con el tacto)</span><span class="sxs-lookup"><span data-stu-id="9d5a4-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="9d5a4-230">Probar la interacción táctil mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="9d5a4-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d5a4-231">Para poder **desencadenar eventos táctiles**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="9d5a4-232">Componente **Collider** (Colisionador), preferiblemente un colisionador de cuadro</span><span class="sxs-lookup"><span data-stu-id="9d5a4-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="9d5a4-233">Componente **Near Interaction Touchable (Script)** (Interacción próxima táctil [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="9d5a4-234">Componente **Hand Interaction Touch (Script)** (Interacción con la mano táctil [script])</span><span class="sxs-lookup"><span data-stu-id="9d5a4-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="9d5a4-235">El componente Hand Interaction Touch (Script) (Interacción con la mano táctil [script]) no forma parte del MRTK.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9d5a4-236">Se importó con los recursos de este tutorial y, originalmente, formaba parte de los ejemplos de Unity de Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="9d5a4-237">1. Agregar un componente de origen de audio al objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="9d5a4-238">En la ventana Jerarquía, selecciona el objeto **Octa**, agrega un componente de **origen de audio** al objeto Octa y, a continuación, cambia el valor de **Spatial Blend** (Combinación espacial) a 1 para habilitar el audio espacial:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="9d5a4-240">2. Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script]) al objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="9d5a4-241">Con el objeto **Octa** todavía seleccionado, agrega el componente **Near Interaction Touchable (Script)** (Interacción próxima táctil [script]) al objeto Octa y, a continuación, haz clic en los botones **Fix Bounds** (Corregir límites) y **Fix Center** (Corregir centro) para actualizar el centro local y las propiedades de los límites de la interacción próxima táctil (script) para que coincidan con BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="9d5a4-243">3. Agregar el componente Hand Interaction Touch (Script) (Componente de interacción de mano [script]) al objeto</span><span class="sxs-lookup"><span data-stu-id="9d5a4-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="9d5a4-244">Con el objeto **Octa** aún seleccionado, agrega el componente **Hand Interaction Touch (Script)** (Interacción con la mano táctil [script]) al objeto Octa:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="9d5a4-246">4. Implementar el evento On Touch Started (Iniciado con el tacto)</span><span class="sxs-lookup"><span data-stu-id="9d5a4-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="9d5a4-247">En el componente **Hand Interaction Touch (Script)** (Interacción con la mano táctil [script]), haz clic en el pequeño icono **+** para crear un nuevo evento **On Touch Started ()** (Iniciado con el tacto []).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="9d5a4-248">A continuación, configura el objeto **Octa** para recibir el evento y define **AudioSource.PlayOneShot** como la acción que se desencadenará:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="9d5a4-250">Ve a **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials (Assets > MixedRealityToolkit.SDK > StandardAssets > Materiales) para ver los clips de audio que se incluyen con el MRTK y asigna un clip de audio adecuado al campo **Clip de audio**; por ejemplo, el clip de audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="9d5a4-252">Para obtener un recordatorio sobre cómo implementar eventos, puedes hacer referencia a las instrucciones sobre [gestos de seguimiento de manos y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="9d5a4-253">5. Probar la interacción táctil mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="9d5a4-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="9d5a4-254">Presiona el botón Jugar para acceder al modo de juego.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="9d5a4-255">A continuación, mantén presionada la barra espaciadora para abrir la mano y usa el ratón para tocar el objeto Octa y desencadenar el efecto de sonido:</span><span class="sxs-lookup"><span data-stu-id="9d5a4-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="9d5a4-257">Como viste al probar la interacción táctil y como se muestra en la imagen anterior, el color del objeto Octa se contraía al tocarlo.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="9d5a4-258">Este efecto está codificado de forma rígida en el componente Hand Interaction Touch (Script) (Componente de interacción de mano [script]) y no como resultado de la configuración de los eventos que completaste en los pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="9d5a4-259">Si quieres deshabilitar este efecto, puedes, por ejemplo, comentar la línea 32 "TargetRenderer = GetComponentInChildren<Renderer>();", lo que provocará que TargetRenderer siga teniendo un valor null y que el color no se contraiga.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9d5a4-260">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="9d5a4-260">Congratulations</span></span>

<span data-ttu-id="9d5a4-261">En este tutorial has aprendido a organizar objetos 3D en una colección de cuadrícula y a manipular estos objetos (escalado, giro y movimiento) con interacción próxima (agarrándolos directamente con las manos con seguimiento) y lejana (con el haz de mano o mirada).</span><span class="sxs-lookup"><span data-stu-id="9d5a4-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="9d5a4-262">También has aprendido a colocar cuadros de límite alrededor de objetos 3D, y a usar y personalizar los controladores en los cuadros de límite.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="9d5a4-263">Por último, has aprendido a desencadenar eventos al tocar objetos.</span><span class="sxs-lookup"><span data-stu-id="9d5a4-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="9d5a4-264">Siguiente lección: 6. Exploración de opciones avanzadas de entrada</span><span class="sxs-lookup"><span data-stu-id="9d5a4-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
