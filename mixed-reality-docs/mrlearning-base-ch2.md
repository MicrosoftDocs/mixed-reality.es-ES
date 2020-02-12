---
title: 'Tutoriales de introducción: 3. Crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130720"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="853ec-105">3. crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="853ec-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="853ec-106">En el tutorial anterior, aprendió sobre algunas de las funcionalidades que el kit de herramientas de realidad mixta (MRTK) tiene que ofrecer al iniciar su primera aplicación para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="853ec-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="853ec-107">En este tutorial aprenderá a crear y organizar botones junto con paneles de texto de la interfaz de usuario y a usar interacción predeterminada (Touch) para interactuar con cada botón.</span><span class="sxs-lookup"><span data-stu-id="853ec-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="853ec-108">También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos.</span><span class="sxs-lookup"><span data-stu-id="853ec-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="853ec-109">Este módulo presentará conceptos básicos sobre la modificación de perfiles de MRTK, empezando por desactivar la visualización de la malla de [asignación espacial](spatial-mapping.md) .</span><span class="sxs-lookup"><span data-stu-id="853ec-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="853ec-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="853ec-110">Objectives</span></span>

* <span data-ttu-id="853ec-111">Personalizar y configurar los perfiles de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="853ec-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="853ec-112">Interacción con hologramas mediante elementos y botones de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="853ec-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="853ec-113">Entrada e interacciones básicas del seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="853ec-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="853ec-114">Configuración de los perfiles de kit de herramientas de realidad mixta (cambiar la opción de visualización de reconocimiento espacial)</span><span class="sxs-lookup"><span data-stu-id="853ec-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="853ec-115">En esta sección, aprenderá a personalizar y configurar los perfiles predeterminados de MRTK.</span><span class="sxs-lookup"><span data-stu-id="853ec-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="853ec-116">En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="853ec-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="853ec-117">Sin embargo, puede seguir estos mismos principios para personalizar cualquier configuración o valor en los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="853ec-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="853ec-118">Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son:</span><span class="sxs-lookup"><span data-stu-id="853ec-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="853ec-119">Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="853ec-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="853ec-120">Habilitación del sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="853ec-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="853ec-121">Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="853ec-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="853ec-122">Clonar el perfil de observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="853ec-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="853ec-123">Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="853ec-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="853ec-124">De forma predeterminada, los perfiles de MRTK no son editables.</span><span class="sxs-lookup"><span data-stu-id="853ec-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="853ec-125">Estas son las plantillas de perfil predeterminadas que se deben clonar antes de que se puedan editar.</span><span class="sxs-lookup"><span data-stu-id="853ec-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="853ec-126">Hay varias capas anidadas de perfiles.</span><span class="sxs-lookup"><span data-stu-id="853ec-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="853ec-127">Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios valores.</span><span class="sxs-lookup"><span data-stu-id="853ec-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="853ec-128">1. clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="853ec-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="853ec-129">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="853ec-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="853ec-130">Por lo tanto, para poder editar cualquier otro perfil, primero debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="853ec-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="853ec-131">Con el objeto **MixedRealityToolkit** seleccionado en la ventana jerarquía, en la ventana del inspector, haga clic en el botón **copiar & personalizar** para abrir la ventana Perfil de clonación:</span><span class="sxs-lookup"><span data-stu-id="853ec-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="853ec-133">En la ventana clonar perfil, haga clic en el botón **clonar** para crear una copia modificable de la **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="853ec-133">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="853ec-135">El perfil de configuración recién creado se asigna ahora como el perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="853ec-135">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="853ec-137">En el menú de Unity, seleccione **archivo** > **Guardar** para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="853ec-137">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="853ec-138">Recuerde guardar el trabajo en el tutorial.</span><span class="sxs-lookup"><span data-stu-id="853ec-138">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="853ec-139">2. habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="853ec-139">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="853ec-140">Con el objeto **MixedRealityToolkit** todavía seleccionado en la ventana jerarquía, en la ventana inspector, seleccione la pestaña **reconocimiento espacial** y active la casilla **Habilitar sistema de reconocimiento espacial** :</span><span class="sxs-lookup"><span data-stu-id="853ec-140">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="853ec-142">3. clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="853ec-142">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="853ec-143">En la pestaña **reconocimiento espacial** , haga clic en el botón **clonar** para abrir la ventana Perfil de clonación:</span><span class="sxs-lookup"><span data-stu-id="853ec-143">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="853ec-145">En la ventana clonar perfil, haga clic en el botón **clonar** para crear una copia modificable de la **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="853ec-145">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="853ec-147">Ahora el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="853ec-147">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="853ec-149">4. clonar el perfil de observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="853ec-149">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="853ec-150">Con la pestaña **reconocimiento espacial** todavía seleccionada, expanda la sección observador de la **malla espacial de Windows Mixed Reality** y haga clic en el botón **clonar** para abrir la ventana Perfil de clonación:</span><span class="sxs-lookup"><span data-stu-id="853ec-150">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="853ec-152">En la ventana clonar perfil, haga clic en el botón **clonar** para crear una copia modificable de la **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="853ec-152">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="853ec-154">El perfil de observador de la malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="853ec-154">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="853ec-156">5. cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="853ec-156">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="853ec-157">En la **configuración del observador de la malla espacial**, cambie la **opción de visualización** a **oclusión** para que la malla de asignación espacial sea invisible mientras sigue funcionando:</span><span class="sxs-lookup"><span data-stu-id="853ec-157">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="853ec-159">Aunque la malla de asignación espacial no es visible, sigue estando presente y funcional.</span><span class="sxs-lookup"><span data-stu-id="853ec-159">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="853ec-160">Por ejemplo, los hologramas detrás de la malla de asignación espacial, como un holograma detrás de un muro física, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="853ec-160">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="853ec-161">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="853ec-161">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="853ec-162">Como puede ver, para personalizar la configuración de MRTK, primero debe crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="853ec-162">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="853ec-163">Dado que los perfiles predeterminados no son editables, siempre tendrá como referencia si desea revertir a la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="853ec-163">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="853ec-164">Para obtener más información acerca de los perfiles de MRTK y su arquitectura, puede visitar la guía de configuración del perfil de el [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="853ec-164">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="853ec-165">Gestos de seguimiento de mano y botones interactivos</span><span class="sxs-lookup"><span data-stu-id="853ec-165">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="853ec-166">En esta sección, aprenderá a usar el seguimiento de manos para presionar un botón y desencadenar eventos para producir una acción cuando se presiona el botón.</span><span class="sxs-lookup"><span data-stu-id="853ec-166">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="853ec-167">En este ejemplo concreto se muestra cómo cambiar el color de un cubo cuando se presiona el botón y cambiarlo a su color original cuando se suelta el botón.</span><span class="sxs-lookup"><span data-stu-id="853ec-167">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="853ec-168">Sin embargo, puede seguir estos mismos principios para crear otros eventos.</span><span class="sxs-lookup"><span data-stu-id="853ec-168">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="853ec-169">Los principales pasos que se deben seguir para cambiar el color del cubo son:</span><span class="sxs-lookup"><span data-stu-id="853ec-169">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="853ec-170">Agregar un botón que se pueda presionar recurso prefabricado a la escena</span><span class="sxs-lookup"><span data-stu-id="853ec-170">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="853ec-171">Agregar un cubo a la escena</span><span class="sxs-lookup"><span data-stu-id="853ec-171">Add a cube to the scene</span></span>
3. <span data-ttu-id="853ec-172">Configurar el tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="853ec-172">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="853ec-173">Configurar el cubo para recibir el evento on press</span><span class="sxs-lookup"><span data-stu-id="853ec-173">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="853ec-174">Definir la acción que va a desencadenar el evento on press</span><span class="sxs-lookup"><span data-stu-id="853ec-174">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="853ec-175">Configurar el cubo para recibir el evento on Release</span><span class="sxs-lookup"><span data-stu-id="853ec-175">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="853ec-176">Definir la acción que va a desencadenar el evento on Release</span><span class="sxs-lookup"><span data-stu-id="853ec-176">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="853ec-177">Probar el botón mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="853ec-177">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="853ec-178">1. agregar un botón que se pueda presionar recurso prefabricado a la escena</span><span class="sxs-lookup"><span data-stu-id="853ec-178">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="853ec-179">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">recurso prefabricado</a> es un GameObject preconfigurado que se almacena como un recurso de Unity y se puede reutilizar en todo el proyecto.</span><span class="sxs-lookup"><span data-stu-id="853ec-179">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="853ec-180">En la **ventana de proyecto**, busque **PressableButtonHoloLens2** para buscar el recurso prefabricado que va a usar en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="853ec-180">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="853ec-182">En el resultado de la **búsqueda** , seleccione **PressableButtonHoloLens2** recurso prefabricado y **arrástrelo** a la ventana de la **jerarquía** para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="853ec-182">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="853ec-184">Para mostrar la escena tal como se muestra en la imagen siguiente, haga doble clic en el objeto PressableButtonHoloLens2 en la ventana de jerarquía para ponerlo en el foco y, a continuación, use el Gizmo de la <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">escena</a>, situado en la esquina superior derecha de la ventana de la escena, para ajustar el ángulo de visualización a lo largo del eje Z hacia delante.</span><span class="sxs-lookup"><span data-stu-id="853ec-184">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="853ec-185">Con el objeto PressableButtonHoloLens2 aún seleccionado, en la ventana del **Inspector** :</span><span class="sxs-lookup"><span data-stu-id="853ec-185">With the PressableButtonHoloLens2 object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="853ec-186">Cambiar su **posición** de transformación para colocarla delante de la cámara, que se coloca en el origen, por ejemplo, x = 0, y = 0 y z = 0,5</span><span class="sxs-lookup"><span data-stu-id="853ec-186">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="853ec-188">En general, 1 unidad de posición en Unity es aproximadamente equivalente a 1 metro en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="853ec-188">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="853ec-189">Sin embargo, hay excepciones para esto, por ejemplo, cuando los objetos son elementos secundarios de objetos escalados.</span><span class="sxs-lookup"><span data-stu-id="853ec-189">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="853ec-190">2. agregar un cubo a la escena</span><span class="sxs-lookup"><span data-stu-id="853ec-190">2. Add a cube to the scene</span></span>

<span data-ttu-id="853ec-191">Haga clic con el botón secundario en una zona vacía dentro de la ventana de jerarquía y seleccione **objeto 3d** > **cubo** para agregar un cubo a la escena:</span><span class="sxs-lookup"><span data-stu-id="853ec-191">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="853ec-193">Con el objeto de cubo todavía seleccionado, en la ventana del **Inspector** :</span><span class="sxs-lookup"><span data-stu-id="853ec-193">With the Cube object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="853ec-194">Cambie su **posición** de transformación para que se encuentre cerca del botón que se pueda presionar, pero no se superponga con él, por ejemplo, x = 0, y = 0,04 y z = 0,5</span><span class="sxs-lookup"><span data-stu-id="853ec-194">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="853ec-195">Cambie la **escala** de transformación a un tamaño adecuado, por ejemplo, x = 0,02, y = 0,02 y z = 0,02</span><span class="sxs-lookup"><span data-stu-id="853ec-195">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="853ec-197">3. configurar el tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="853ec-197">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="853ec-198">Con el objeto PressableButtonHoloLens2 seleccionado en la ventana jerarquía, en el **menú**de la ventana del **Inspector** , seleccione **contraer todos los componentes** para obtener una visión general de todos los componentes de este objeto:</span><span class="sxs-lookup"><span data-stu-id="853ec-198">With the PressableButtonHoloLens2 object selected in the Hierarchy window, in the **Inspector** window **hamburger menu**, select **Collaps All Components** to get an overview of all components on this object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="853ec-200">Expanda el componente **interactuable (Script)** y, a continuación, busque y expanda la sección **eventos** > **receptores** :</span><span class="sxs-lookup"><span data-stu-id="853ec-200">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="853ec-202">Para el tipo de receptor de eventos **InteractableOnPressReceiver**, cambie el **filtro de interacción** a **Near y Far**:</span><span class="sxs-lookup"><span data-stu-id="853ec-202">For the Event Receiver Type **InteractableOnPressReceiver**, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="853ec-204">El tipo de receptor de eventos denominado InteractableOnPressReceiver permite al botón responder a un evento presionado cuando una mano a la que se hace un seguimiento presiona el botón.</span><span class="sxs-lookup"><span data-stu-id="853ec-204">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="853ec-205">4. configurar el cubo para recibir el evento on press</span><span class="sxs-lookup"><span data-stu-id="853ec-205">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="853ec-206">En la ventana jerarquía, **haga clic y arrastre** el **cubo** al campo objeto de **propiedades de evento** para el evento **on press ()** para asignar el cubo como receptor del evento on press ():</span><span class="sxs-lookup"><span data-stu-id="853ec-206">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="853ec-208">5. definir la acción que va a desencadenar el evento on press</span><span class="sxs-lookup"><span data-stu-id="853ec-208">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="853ec-209">Haga clic en la lista desplegable acción, actualmente **no hay ninguna función**asignada y seleccione **MeshRenderer** \*\* > material material para\*\* establecer la propiedad material del cubo que se cambiará cuando se desencadene el evento on press ():</span><span class="sxs-lookup"><span data-stu-id="853ec-209">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="853ec-211">Haga clic en el icono de **círculo** pequeño situado junto al campo material, actualmente rellenado con **ninguno (material)** , para abrir la ventana Seleccionar material:</span><span class="sxs-lookup"><span data-stu-id="853ec-211">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="853ec-213">En la ventana Seleccionar material, **busque** **MRTK_Standard** y seleccione un material adecuado, por ejemplo, **MRTK_Standard_Cyan** para que el color del cubo cambie a Aguamarina cuando se presione el botón:</span><span class="sxs-lookup"><span data-stu-id="853ec-213">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="853ec-215">6. configurar el cubo para recibir el evento on Release</span><span class="sxs-lookup"><span data-stu-id="853ec-215">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="853ec-216">**Repetir** Paso 4 para el evento on Release para asignar el cubo como receptor del evento on Release ().</span><span class="sxs-lookup"><span data-stu-id="853ec-216">**Repeat** Step 4 for the On Release event to assign the Cube as a receiver of the On Release () event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="853ec-217">7. definir la acción que va a desencadenar el evento on Release</span><span class="sxs-lookup"><span data-stu-id="853ec-217">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="853ec-218">**Repetir** Paso 5 para el evento on release, pero elija el **MRTK_Standard_LightGray** material para que el color del cubo vuelva a su color gris claro original al soltar el botón:</span><span class="sxs-lookup"><span data-stu-id="853ec-218">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="853ec-220">8. probar el botón mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="853ec-220">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="853ec-221">Presione el botón **reproducir** para entrar en el modo de juego y use la simulación de entrada del editor para probar el botón que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="853ec-221">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="853ec-222">Botón no presionado (barra espaciadora + rueda hacia atrás del mouse):</span><span class="sxs-lookup"><span data-stu-id="853ec-222">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="853ec-224">Botón presionado (barra espaciadora + rueda de desplazamiento hacia delante):</span><span class="sxs-lookup"><span data-stu-id="853ec-224">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="853ec-226">Para obtener información sobre cómo usar la simulación de entrada del editor, puede consultar el [uso de la simulación de entrada de la mano del editor para probar una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guía de escenas en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="853ec-226">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="853ec-227">Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK</span><span class="sxs-lookup"><span data-stu-id="853ec-227">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="853ec-228">En esta sección, aprenderá a alinear automáticamente varios botones en una interfaz de usuario ordenada mediante la herramienta de colección de objetos de cuadrícula de MRTK.</span><span class="sxs-lookup"><span data-stu-id="853ec-228">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="853ec-229">En este ejemplo concreto se muestra cómo crear un panel con cinco botones alineados horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="853ec-229">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="853ec-230">Sin embargo, puede seguir estos mismos principios para crear otros diseños.</span><span class="sxs-lookup"><span data-stu-id="853ec-230">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="853ec-231">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="853ec-231">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="853ec-232">Primaria de los objetos de botón en un objeto primario</span><span class="sxs-lookup"><span data-stu-id="853ec-232">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="853ec-233">Agregar y configurar el componente de colección de objetos de cuadrícula (Script)</span><span class="sxs-lookup"><span data-stu-id="853ec-233">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="853ec-234">Prueba de los botones mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="853ec-234">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="853ec-235">1. primaria de los objetos de botón en un objeto primario</span><span class="sxs-lookup"><span data-stu-id="853ec-235">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="853ec-236">Haga clic con el botón derecho en una zona vacía dentro de la ventana de jerarquía y seleccione **crear vacío**:</span><span class="sxs-lookup"><span data-stu-id="853ec-236">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="853ec-238">Haga clic con el botón derecho en el objeto recién creado, seleccione **cambiar nombre**y asígnele un nombre adecuado, por ejemplo, **ButtonCollection**:</span><span class="sxs-lookup"><span data-stu-id="853ec-238">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="853ec-240">Seleccione el objeto **PressableButtonHoloLens2** y **arrástrelo** sobre el objeto **ButtonCollection** para convertirlo en un elemento secundario del objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="853ec-240">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="853ec-242">Haga clic con el botón secundario en el objeto **PressableButtonHoloLens2** y seleccione **duplicar** para crear una copia de él:</span><span class="sxs-lookup"><span data-stu-id="853ec-242">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="853ec-244">**Repita** este paso cuatro veces más hasta que tenga un total de cinco objetos PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="853ec-244">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="853ec-245">2. agregar y configurar el componente de colección de objetos de cuadrícula (Script)</span><span class="sxs-lookup"><span data-stu-id="853ec-245">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="853ec-246">Con el objeto ButtonCollection seleccionado en la ventana jerarquía, en la ventana inspector, haga clic en el botón **Agregar componente** , busque y seleccione **colección de objetos de cuadrícula** para agregar un componente de colección de objetos de cuadrícula (Script) al objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="853ec-246">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="853ec-248">Configure la colección de objetos de cuadrícula (Script) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="853ec-248">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="853ec-249">Cambie **NUM Rows** a 1 para que todos los botones estén alineados en una sola fila.</span><span class="sxs-lookup"><span data-stu-id="853ec-249">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="853ec-250">Cambiar el **ancho de celda** a 0,05 para descartar los botones de la fila</span><span class="sxs-lookup"><span data-stu-id="853ec-250">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="853ec-251">A continuación, haga clic en el botón **Actualizar colección** para aplicar la nueva configuración:</span><span class="sxs-lookup"><span data-stu-id="853ec-251">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="853ec-253">Los cambios de configuración que acaba de aplicar representan los cambios mínimos necesarios para lograr el objetivo de colocar los botones en una sola fila.</span><span class="sxs-lookup"><span data-stu-id="853ec-253">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="853ec-254">Sin embargo, en proyectos futuros, en función de factores como, por ejemplo, la orientación de los objetos primarios y secundarios, es posible que necesite ajustar otras opciones de configuración como, por ejemplo, el tipo de orientación.</span><span class="sxs-lookup"><span data-stu-id="853ec-254">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="853ec-255">Para obtener más información sobre la colección de objetos de cuadrícula de MRTK, puede visitar la guía de [scripts de colección de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="853ec-255">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="853ec-256">Con el objeto ButtonCollection todavía seleccionado en la ventana de la jerarquía, en la ventana del inspector, cambie la **posición** de transformación del objeto ButtonCollection para que sus objetos de botón secundarios se coloquen delante de la cámara, que se coloca en el origen, por ejemplo, x = 0, y = 0 y z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="853ec-256">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="853ec-258">La primera vez que se agregó el recurso prefabricado PressableButtonHoloLens2 a la escena en la sección [gestos de seguimiento de mano y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) anteriores, se coloca delante de la cámara.</span><span class="sxs-lookup"><span data-stu-id="853ec-258">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="853ec-259">Sin embargo, dado que la colección de objetos Grid controla su posición de los objetos secundarios inmediatos, la posición Z de los objetos secundarios PressableButtonHoloLens2 se restableció a 0 según la distancia predeterminada de la colección de objetos de cuadrícula del valor 0.</span><span class="sxs-lookup"><span data-stu-id="853ec-259">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="853ec-260">Esto, y para mantener la relación posicional de elementos primarios y secundarios organizada, es el motivo por el que se ha movido la posición del objeto primario ButtonCollection hacia delante en lugar de configurar la distancia desde el valor primario para mover los objetos secundarios PressableButtonHoloLens2 hacia delante.</span><span class="sxs-lookup"><span data-stu-id="853ec-260">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="853ec-261">3. probar los botones mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="853ec-261">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="853ec-262">Presione el botón reproducir para entrar en el modo de juego y use la simulación de entrada del editor para probar cada uno de los botones de en el panel de botones recién creado:</span><span class="sxs-lookup"><span data-stu-id="853ec-262">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="853ec-264">Actualmente, cuando se presiona cualquiera de los cinco botones, el color del cubo cambia a aguamarina.</span><span class="sxs-lookup"><span data-stu-id="853ec-264">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="853ec-265">Para que la experiencia sea más interesante, use lo que acaba de aprender para configurar cada botón y cambiar el cubo a un color diferente.</span><span class="sxs-lookup"><span data-stu-id="853ec-265">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="853ec-266">Agregar texto a la escena</span><span class="sxs-lookup"><span data-stu-id="853ec-266">Adding text into your scene</span></span>

<span data-ttu-id="853ec-267">En esta sección, aprenderá a agregar texto a sus experiencias de realidad mixta con TextMesh pro de Unity, que preparó en la sección [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) del tutorial anterior.</span><span class="sxs-lookup"><span data-stu-id="853ec-267">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="853ec-268">En este ejemplo concreto, agregará una etiqueta simple debajo de la colección de botones que creó en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="853ec-268">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="853ec-269">Haga clic con el botón derecho en el objeto ButtonCollection y seleccione **objeto 3d** > **Text-TextMeshPro** para crear un objeto TextMeshPro como elemento secundario del objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="853ec-269">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="853ec-271">Con el objeto TextMeshPro que se acaba de crear, denominado Text (TMP), aún seleccionado, en la ventana del inspector, cambie su posición y tamaño para que la etiqueta se coloque en el interior de la colección de botones, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="853ec-271">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="853ec-272">Cambie la transformación de rectángulo **Y** a-0,0425</span><span class="sxs-lookup"><span data-stu-id="853ec-272">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="853ec-273">Cambiar el **ancho** de la transformación Rect a 0,24</span><span class="sxs-lookup"><span data-stu-id="853ec-273">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="853ec-274">Cambiar el **alto** de la transformación Rect a 0,024</span><span class="sxs-lookup"><span data-stu-id="853ec-274">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="853ec-275">A continuación, actualice el texto para que refleje el contenido de la etiqueta y elija Propiedades de fuente para que el texto quepa dentro de la etiqueta, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="853ec-275">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="853ec-276">Cambiar el texto de la malla de texto Pro ( **script) a** la colección de botones</span><span class="sxs-lookup"><span data-stu-id="853ec-276">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="853ec-277">Cambiar el **estilo de fuente** de la malla de texto Pro (Script) a negrita</span><span class="sxs-lookup"><span data-stu-id="853ec-277">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="853ec-278">Cambiar el **tamaño de fuente** de la malla de texto Pro (Script) a 0,2</span><span class="sxs-lookup"><span data-stu-id="853ec-278">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="853ec-279">Cambiar la **alineación** de la malla de texto Pro (Script) al centro y el medio</span><span class="sxs-lookup"><span data-stu-id="853ec-279">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning: base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="853ec-281">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="853ec-281">Congratulations</span></span>

<span data-ttu-id="853ec-282">En este tutorial, aprendió a clonar, personalizar y configurar una configuración de Perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="853ec-282">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="853ec-283">También aprendió a interactuar con los botones para desencadenar eventos mediante las manos del seguimiento en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="853ec-283">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="853ec-284">Por último, aprendió a crear una interfaz de usuario simple mediante el componente de colección de objetos de cuadrícula de MRTK y el pro de malla de texto de Unity.</span><span class="sxs-lookup"><span data-stu-id="853ec-284">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="853ec-285">Siguiente tutorial: 4. colocar contenido dinámico y usar solucionadores</span><span class="sxs-lookup"><span data-stu-id="853ec-285">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
