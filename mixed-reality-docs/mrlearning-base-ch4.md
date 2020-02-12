---
title: 'Tutoriales de introducción: 5. Interactuar con objetos 3D'
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130286"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="86899-104">5. interactuar con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="86899-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="86899-105">En este tutorial, obtendrá información sobre el contenido 3D básico y la experiencia del usuario, como la organización de objetos 3D como parte de una colección, los cuadros de límite para la manipulación básica, la interacción aproximada y lejana, y los gestos táctiles y de agarre con seguimiento manual.</span><span class="sxs-lookup"><span data-stu-id="86899-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="86899-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="86899-106">Objectives</span></span>

* <span data-ttu-id="86899-107">Crear un panel de objetos 3D que se usará para los otros objetivos de aprendizaje</span><span class="sxs-lookup"><span data-stu-id="86899-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="86899-108">Implementar rectángulos de selección</span><span class="sxs-lookup"><span data-stu-id="86899-108">Implement bounding boxes</span></span>
* <span data-ttu-id="86899-109">Configurar objetos 3D para la manipulación básica, como movimiento, rotación y escala</span><span class="sxs-lookup"><span data-stu-id="86899-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="86899-110">Explorar la interacción próxima y lejana</span><span class="sxs-lookup"><span data-stu-id="86899-110">Explore near and far interaction</span></span>
* <span data-ttu-id="86899-111">Más información acerca de los gestos de seguimiento de la mano, como captar y tocar</span><span class="sxs-lookup"><span data-stu-id="86899-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="86899-112">Importar los activos del tutorial</span><span class="sxs-lookup"><span data-stu-id="86899-112">Importing the tutorial assets</span></span>

<span data-ttu-id="86899-113">Descargue e importe el paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="86899-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="86899-114">MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.2.0.0. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="86899-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

<span data-ttu-id="86899-115">Después de haber importado los recursos del tutorial, la ventana del proyecto debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="86899-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="86899-117">Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, puede consultar las instrucciones para [importar el kit de herramientas de realidad mixta](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .</span><span class="sxs-lookup"><span data-stu-id="86899-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="86899-118">Desenredo de la vista de escena</span><span class="sxs-lookup"><span data-stu-id="86899-118">Decluttering the scene view</span></span>

<span data-ttu-id="86899-119">Para que resulte más fácil trabajar con la escena, establezca la visibilidad de la **escena** del cubo y los objetos ButtonCollection en OFF; para ello, haga clic en el icono de **ojo** situado a la izquierda de los objetos.</span><span class="sxs-lookup"><span data-stu-id="86899-119">To make it easier to work with your scene, set the **scene visibility** for the Cube and ButtonCollection objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="86899-120">Esto oculta el objeto en la ventana de la escena sin cambiar su visibilidad en el juego:</span><span class="sxs-lookup"><span data-stu-id="86899-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="86899-122">Para obtener más información sobre los controles de visibilidad de escenas y cómo puede usarlos para optimizar la vista de escenas y el flujo de trabajo, puede visitar la documentación de visibilidad de la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">escena</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="86899-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="86899-123">Organizar objetos 3D en una colección</span><span class="sxs-lookup"><span data-stu-id="86899-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="86899-124">En esta sección, creará un panel de objetos 3D que se utilizará al explorar varias formas de interactuar con objetos 3D en las siguientes secciones de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="86899-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="86899-125">En concreto, configurará los objetos 3D para que se coloquen en una cuadrícula de 3 x 3.</span><span class="sxs-lookup"><span data-stu-id="86899-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="86899-126">Del mismo modo que cuando se [crea un panel de botones](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="86899-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="86899-127">Parent los objetos 3D a un objeto primario</span><span class="sxs-lookup"><span data-stu-id="86899-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="86899-128">Agregar y configurar el componente de colección de objetos de cuadrícula (Script)</span><span class="sxs-lookup"><span data-stu-id="86899-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="86899-129">1. Parent los objetos 3D a un objeto primario</span><span class="sxs-lookup"><span data-stu-id="86899-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="86899-130">En la ventana jerarquía, **cree un objeto vacío**, asígnele un nombre adecuado, por ejemplo, **3DObjectCollection**, y colóquelo en una ubicación adecuada, por ejemplo, X = 0, y =-0,2, Z = 2.</span><span class="sxs-lookup"><span data-stu-id="86899-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="86899-131">En la ventana del proyecto, vaya a **activos** > **MRTK. Tutoriales. GettingStarted** > **Prefabs**y, a continuación, el **elemento primario** del Prefabs siguiente al **3DObjectCollection**:</span><span class="sxs-lookup"><span data-stu-id="86899-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **Parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="86899-132">Quesos</span><span class="sxs-lookup"><span data-stu-id="86899-132">Cheese</span></span>
* <span data-ttu-id="86899-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="86899-133">CoffeeCup</span></span>
* <span data-ttu-id="86899-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="86899-134">EarthCore</span></span>
* <span data-ttu-id="86899-135">Octa</span><span class="sxs-lookup"><span data-stu-id="86899-135">Octa</span></span>
* <span data-ttu-id="86899-136">Platonic</span><span class="sxs-lookup"><span data-stu-id="86899-136">Platonic</span></span>
* <span data-ttu-id="86899-137">Módulo</span><span class="sxs-lookup"><span data-stu-id="86899-137">TheModule</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="86899-139">En la ventana de jerarquía, **cree tres cubos** como objetos secundarios de **3DObjectCollection** y establezca su **escala** de transformación en X = 0,15, y = 0,15, Z = 0,15:</span><span class="sxs-lookup"><span data-stu-id="86899-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> <span data-ttu-id="86899-141">Para obtener un recordatorio sobre cómo realizar los pasos indicados anteriormente, puede consultar el tutorial creación de la [interfaz de usuario y configuración del kit de herramientas de realidad mixta](mrlearning-base-ch2.md) .</span><span class="sxs-lookup"><span data-stu-id="86899-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="86899-142">Cambie la posición de los cubos para que pueda ver cada cubo:</span><span class="sxs-lookup"><span data-stu-id="86899-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="86899-144">En la ventana del proyecto, vaya a **activos** > **MixedRealityToolkit. SDK** > **StandardAssets** > **material** para ver los materiales proporcionados con el MRTK.</span><span class="sxs-lookup"><span data-stu-id="86899-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="86899-145">**Haga clic y arrastre** un material adecuado a la propiedad 0 del elemento de **materiales** del representador de la malla del cubo, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="86899-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="86899-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="86899-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="86899-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="86899-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="86899-148">MRTK_Standard_Green:</span><span class="sxs-lookup"><span data-stu-id="86899-148">MRTK_Standard_Green:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="86899-150">2. agregar y configurar el componente de colección de objetos de cuadrícula (Script)</span><span class="sxs-lookup"><span data-stu-id="86899-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="86899-151">Agregue un componente de la **colección de objetos de cuadrícula (Script)** al objeto 3DObjectCollection y configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="86899-151">Add a **Grid Object Collection (Script)** component to the 3DObjectCollection object, and configure it as follows:</span></span>

* <span data-ttu-id="86899-152">Cambie **tipo de ordenación** a orden secundario para asegurarse de que los objetos secundarios se ordenan en el orden en el que los colocó en el objeto primario.</span><span class="sxs-lookup"><span data-stu-id="86899-152">Change **Sort Type** to Child Order to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="86899-153">A continuación, haga clic en el botón **Actualizar colección** para aplicar la nueva configuración:</span><span class="sxs-lookup"><span data-stu-id="86899-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="86899-155">Manipular objetos 3D</span><span class="sxs-lookup"><span data-stu-id="86899-155">Manipulating 3D objects</span></span>

<span data-ttu-id="86899-156">En esta sección, agregará la capacidad de manipular todos los objetos 3D del panel que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="86899-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="86899-157">Además, en el caso de los objetos recurso prefabricado, permitirá que los usuarios accedan a los objetos y los capten con manos con seguimiento.</span><span class="sxs-lookup"><span data-stu-id="86899-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="86899-158">A continuación, explorará algunos comportamientos de manipulación que puede aplicar a los objetos.</span><span class="sxs-lookup"><span data-stu-id="86899-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="86899-159">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="86899-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="86899-160">Agregar el componente de controlador de manipulación (Script) a todos los objetos</span><span class="sxs-lookup"><span data-stu-id="86899-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="86899-161">Agregar el componente de captura de interacción cercana (Script) a los objetos recurso prefabricado</span><span class="sxs-lookup"><span data-stu-id="86899-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="86899-162">Configurar el componente de controlador de manipulación (Script)</span><span class="sxs-lookup"><span data-stu-id="86899-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86899-163">Para poder **manipular un objeto**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="86899-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="86899-164">Componente de **Colisionador** , por ejemplo, un Colisionador de caja</span><span class="sxs-lookup"><span data-stu-id="86899-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="86899-165">Componente de **controlador de manipulación (Script)**</span><span class="sxs-lookup"><span data-stu-id="86899-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="86899-166">Para poder **manipular** y **captar un objeto con manos sometidas a seguimiento**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="86899-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="86899-167">Componente de **Colisionador** , por ejemplo, un Colisionador de caja</span><span class="sxs-lookup"><span data-stu-id="86899-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="86899-168">Componente de **controlador de manipulación (Script)**</span><span class="sxs-lookup"><span data-stu-id="86899-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="86899-169">Componente de captura de la **interacción cercana (Script)**</span><span class="sxs-lookup"><span data-stu-id="86899-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="86899-170">1. Agregue el componente de controlador de manipulación (Script) a todos los objetos.</span><span class="sxs-lookup"><span data-stu-id="86899-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="86899-171">En la ventana jerarquía, seleccione el objeto **queso** , mantenga presionada la tecla **MAYÚS** y, a continuación, seleccione el objeto **Cube ()** y agregue el componente de **controlador de manipulación (Script)** a todos los objetos:</span><span class="sxs-lookup"><span data-stu-id="86899-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube ()** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="86899-173">En este tutorial, los colisionadores ya se han agregado a Prefabs.</span><span class="sxs-lookup"><span data-stu-id="86899-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="86899-174">En el caso de los primitivos de Unity, como los objetos de cubo, el componente de Colisionador se agrega automáticamente cuando se crea el objeto.</span><span class="sxs-lookup"><span data-stu-id="86899-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="86899-175">En la imagen anterior, los colisionadores se representan mediante los contornos verdes.</span><span class="sxs-lookup"><span data-stu-id="86899-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="86899-176">Para más información sobre los colisionadores, puede visitar la documentación del <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisionador</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="86899-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="86899-177">2. agregar el componente de captura de interacción cercana (Script) a los objetos recurso prefabricado</span><span class="sxs-lookup"><span data-stu-id="86899-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="86899-178">En la ventana de jerarquía, seleccione el objeto de **queso** , mantenga presionada la tecla **MAYÚS** y, a continuación, seleccione el objeto **módulo** y agregue el componente de **captura de interacción cercana (Script)** a todos los objetos:</span><span class="sxs-lookup"><span data-stu-id="86899-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="86899-180">3. configurar el componente de controlador de manipulación (Script)</span><span class="sxs-lookup"><span data-stu-id="86899-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="86899-181">Manipulación predeterminada</span><span class="sxs-lookup"><span data-stu-id="86899-181">Default manipulation</span></span>

<span data-ttu-id="86899-182">Para el objeto de **cubo** , deje todas las propiedades en el valor predeterminado para experimentar el comportamiento de manipulación predeterminado:</span><span class="sxs-lookup"><span data-stu-id="86899-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="86899-184">Para restablecer los valores predeterminados de un componente, puede seleccionar el icono de configuración del componente y seleccionar restablecer.</span><span class="sxs-lookup"><span data-stu-id="86899-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="86899-185">Restringir la manipulación solo a escala</span><span class="sxs-lookup"><span data-stu-id="86899-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="86899-186">En el caso del objeto **Cube (1)** , cambie el **tipo de manipulación dos manos** a escala para permitir solo al usuario cambiar el tamaño del objeto:</span><span class="sxs-lookup"><span data-stu-id="86899-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to Scale to only allow the user to change the object's size:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="86899-188">Restringir el movimiento a una distancia fija del usuario</span><span class="sxs-lookup"><span data-stu-id="86899-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="86899-189">Para el objeto **Cube (2)** , cambie **Constraint en** Move para corregir la distancia desde Head, de modo que cuando se mueva el objeto se mantenga a la misma distancia del usuario:</span><span class="sxs-lookup"><span data-stu-id="86899-189">For the **Cube (2)** object, change **Constraint On Movement** to Fix Distance From Head so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="86899-191">Manipulación capturable predeterminada</span><span class="sxs-lookup"><span data-stu-id="86899-191">Default grabbable manipulation</span></span>

<span data-ttu-id="86899-192">En el caso de los objetos **queso**, **CoffeCup**y **EarthCore** , deje todas las propiedades en el valor predeterminado para experimentar el comportamiento de la manipulación de capturas predeterminada:</span><span class="sxs-lookup"><span data-stu-id="86899-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="86899-194">Eliminación de la capacidad de manipulación lejana</span><span class="sxs-lookup"><span data-stu-id="86899-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="86899-195">Para el objeto **OCTA** , desactive la casilla **permitir la manipulación lejana** para que el usuario solo pueda interactuar con el objeto directamente mediante las manos controladas:</span><span class="sxs-lookup"><span data-stu-id="86899-195">For the **Octa** object, uncheck the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="86899-197">Hacer que un objeto gire alrededor de su centro</span><span class="sxs-lookup"><span data-stu-id="86899-197">Make an object rotate around its center</span></span>

<span data-ttu-id="86899-198">En el caso del objeto **Platonic** , cambie el **modo de rotación de una mano cerca** del **modo de rotación de una mano** hacia la gira sobre el centro de objetos para que sea así cuando el usuario gire el objeto con una mano, se rote alrededor del centro del objeto:</span><span class="sxs-lookup"><span data-stu-id="86899-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to Rotate About Object Center to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a><span data-ttu-id="86899-200">Impedir el movimiento después de liberar el objeto</span><span class="sxs-lookup"><span data-stu-id="86899-200">Prevent movement after object is released</span></span>

<span data-ttu-id="86899-201">En el caso del objeto de **módulo** , cambie el comportamiento de la **versión** a nada para que una vez que el objeto se libere de la mano del usuario, no siga moviendo:</span><span class="sxs-lookup"><span data-stu-id="86899-201">For the **TheModule** object, change **Release Behavior** to Nothing so that once the object is released from the user's hand, it doesn’t continue to move:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="86899-203">Para obtener más información sobre el componente de controlador de manipulación y sus propiedades asociadas, puede visitar la guía de [control de manipulaciones](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="86899-203">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="86899-204">Agregar cuadros de límite</span><span class="sxs-lookup"><span data-stu-id="86899-204">Adding bounding boxes</span></span>

<span data-ttu-id="86899-205">Los cuadros de límite facilitan y simplifican la manipulación de objetos con una mano para una interacción cercana y lejana al proporcionar controladores que se pueden usar para el escalado y la rotación.</span><span class="sxs-lookup"><span data-stu-id="86899-205">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="86899-206">En este ejemplo, agregará un cuadro de límite al objeto EarthCore, por lo que ahora se puede interactuar con este objeto con la manipulación de objetos configurada en la sección anterior, así como, escalado y girado con los manipuladores del cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="86899-206">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86899-207">Para poder utilizar un cuadro de **límite**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="86899-207">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="86899-208">Componente de **Colisionador** , por ejemplo, un Colisionador de caja</span><span class="sxs-lookup"><span data-stu-id="86899-208">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="86899-209">Componente de **cuadro de límite (Script)**</span><span class="sxs-lookup"><span data-stu-id="86899-209">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="86899-210">1. Agregue el componente de cuadro de límite (Script) al objeto EarthCore</span><span class="sxs-lookup"><span data-stu-id="86899-210">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="86899-211">En la ventana del inspector, seleccione el objeto **EarthCore** y agregue el componente del **cuadro de límite (Script)** al objeto EarthCore:</span><span class="sxs-lookup"><span data-stu-id="86899-211">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="86899-213">Las visualizaciones del cuadro de límite se crean en tiempo de ejecución y, por tanto, no son visibles antes de entrar en el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="86899-213">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="86899-214">2. visualizar y probar el cuadro de límite mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="86899-214">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="86899-215">Presione el botón reproducir para entrar en el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="86899-215">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="86899-216">A continuación, mantenga presionada la barra espaciadora para abrir la mano y use el mouse para interactuar con el cuadro de límite:</span><span class="sxs-lookup"><span data-stu-id="86899-216">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="86899-218">Para obtener más información acerca del componente de cuadro de límite y sus propiedades asociadas, puede visitar la guía del [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) en el portal de [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="86899-218">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="86899-219">Agregar efectos de toque</span><span class="sxs-lookup"><span data-stu-id="86899-219">Adding touch effects</span></span>

<span data-ttu-id="86899-220">En este ejemplo, permitirá que los eventos se desencadenen al tocar un objeto con la mano.</span><span class="sxs-lookup"><span data-stu-id="86899-220">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="86899-221">En concreto, configurará el objeto OCTA para que se produzca un efecto sonoro cuando el usuario lo toque.</span><span class="sxs-lookup"><span data-stu-id="86899-221">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="86899-222">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="86899-222">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="86899-223">Agregar un componente de origen de audio al objeto</span><span class="sxs-lookup"><span data-stu-id="86899-223">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="86899-224">Agregar el componente de la interacción táctil (Script) cerca del objeto</span><span class="sxs-lookup"><span data-stu-id="86899-224">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="86899-225">Agregar el componente de interacción a mano (Script) al objeto</span><span class="sxs-lookup"><span data-stu-id="86899-225">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="86899-226">Implementar el evento on Touch Started</span><span class="sxs-lookup"><span data-stu-id="86899-226">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="86899-227">Prueba de la interacción táctil mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="86899-227">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86899-228">Para poder **desencadenar eventos táctiles**, el objeto debe tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="86899-228">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="86899-229">Componente de **Colisionador** , preferiblemente un Colisionador de caja</span><span class="sxs-lookup"><span data-stu-id="86899-229">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="86899-230">Componente de la **interacción táctil (Script) cercano**</span><span class="sxs-lookup"><span data-stu-id="86899-230">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="86899-231">Componente de **toque de interacción manual (Script)**</span><span class="sxs-lookup"><span data-stu-id="86899-231">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="86899-232">El componente de interacción manuscrita de mano (Script) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="86899-232">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="86899-233">Se importó con los recursos de este tutorial y parte originalmente de los ejemplos de Unity de MixedReality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="86899-233">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="86899-234">1. agregar un componente de origen de audio al objeto</span><span class="sxs-lookup"><span data-stu-id="86899-234">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="86899-235">En la ventana de jerarquía, seleccione el objeto **OCTA** , agregue un componente de **origen de audio** al objeto OCTA y, a continuación, cambie la **mezcla espacial** a 1 para habilitar el audio espacial:</span><span class="sxs-lookup"><span data-stu-id="86899-235">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="86899-237">2. agregar el componente de la interacción táctil (Script) cerca del objeto</span><span class="sxs-lookup"><span data-stu-id="86899-237">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="86899-238">Con el objeto **OCTA** aún seleccionado, agregue el componente de **secuencia de comandos táctil (Script) cerca** de la interacción al objeto OCTA y, a continuación, haga clic en los botones **corregir límites** y **centro de corrección** para actualizar el centro local y las propiedades de los límites del elemento táctil de interacción cercana (Script) para que coincida con BoxCollider:</span><span class="sxs-lookup"><span data-stu-id="86899-238">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="86899-240">3. agregar el componente de toque de interacción de mano (Script) al objeto</span><span class="sxs-lookup"><span data-stu-id="86899-240">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="86899-241">Con el objeto **OCTA** aún seleccionado, agregue el componente de **toque de interacción de mano (Script)** al objeto OCTA:</span><span class="sxs-lookup"><span data-stu-id="86899-241">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="86899-243">4. implementar el evento on Touch Started</span><span class="sxs-lookup"><span data-stu-id="86899-243">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="86899-244">En el componente de toque de interacción de mano (Script), haga clic en el icono de **+** pequeño para crear un nuevo evento **on Touch Started ()** .</span><span class="sxs-lookup"><span data-stu-id="86899-244">On the Hand Interaction Touch (Script) component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="86899-245">A continuación, configure el objeto **OCTA** para recibir el evento y defina **AudioSource. PlayOneShot** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="86899-245">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="86899-247">Vaya a **activos** > **MixedRealityToolkit. SDK** > **StandardAssets** > material para ver los clips de audio que se proporcionan con el MRTK y, a continuación, asigne un clip de audio adecuado al campo **clip de audio** , por ejemplo, el clip de audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="86899-247">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="86899-249">Para obtener un recordatorio sobre cómo implementar eventos, puede consultar las instrucciones de [gestos de seguimiento de mano e](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) interactivos.</span><span class="sxs-lookup"><span data-stu-id="86899-249">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="86899-250">5. probar la interacción táctil mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="86899-250">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="86899-251">Presione el botón reproducir para entrar en el modo de juego.</span><span class="sxs-lookup"><span data-stu-id="86899-251">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="86899-252">A continuación, mantenga presionada la barra espaciadora para abrir la mano y use el mouse para tocar el objeto OCTA y desencadenar el efecto de sonido:</span><span class="sxs-lookup"><span data-stu-id="86899-252">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="86899-254">Como vio al probar la interacción táctil y como se muestra en la imagen anterior, el objeto OCTA color pulsated mientras se toca.</span><span class="sxs-lookup"><span data-stu-id="86899-254">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="86899-255">Este efecto está codificado de forma rígida en el componente de toque de interacción (Script) de mano y no en el resultado de la configuración de eventos completada en los pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="86899-255">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="86899-256">Si desea deshabilitar este efecto, puede, por ejemplo, comentar como comentario o la línea 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); ', lo que dará lugar a que el TargetRenderer quede nulo y el color no sea pulsating.</span><span class="sxs-lookup"><span data-stu-id="86899-256">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="86899-257">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="86899-257">Congratulations</span></span>

<span data-ttu-id="86899-258">En este tutorial, aprendió a organizar objetos 3D en una colección de cuadrículas y cómo manipular estos objetos (escalado, rotación y movimiento) mediante la interacción aproximada (captando directamente con manos sometidas a seguimiento) e interacción lejana (mediante rayos de miración o rayos de mano).</span><span class="sxs-lookup"><span data-stu-id="86899-258">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="86899-259">También ha aprendido cómo colocar los rectángulos de selección alrededor de los objetos 3D, y ha aprendido a usar y personalizar los controladores en los cuadros de límite.</span><span class="sxs-lookup"><span data-stu-id="86899-259">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="86899-260">Por último, has aprendido a desencadenar eventos al tocar objetos.</span><span class="sxs-lookup"><span data-stu-id="86899-260">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="86899-261">Lección siguiente: 6. explorar opciones de entrada avanzadas</span><span class="sxs-lookup"><span data-stu-id="86899-261">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
