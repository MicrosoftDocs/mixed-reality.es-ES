---
title: 'Tutoriales de introducción: 3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376142"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="96681-105">3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="96681-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="96681-106">En el tutorial anterior, descubriste algunas de las funcionalidades que ofrece Mixed Reality Toolkit (MRTK) e iniciaste tu primera aplicación para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="96681-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="96681-107">En este tutorial, aprenderás a crear y organizar los botones junto con los paneles de texto de la interfaz de usuario, y a usar la interacción predeterminada (táctil) para interactuar con cada botón.</span><span class="sxs-lookup"><span data-stu-id="96681-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="96681-108">También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos.</span><span class="sxs-lookup"><span data-stu-id="96681-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="96681-109">En este módulo se presentan los conceptos básicos sobre cómo modificar los perfiles de MRTK. Para empezar, se desactiva la visualización de malla de [asignación espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="96681-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="96681-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="96681-110">Objectives</span></span>

* <span data-ttu-id="96681-111">Personalizar y configurar los perfiles de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="96681-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="96681-112">Interacción con hologramas mediante botones y elementos de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="96681-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="96681-113">Entrada e interacciones básicas del seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="96681-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="96681-114">Configuración de los perfiles de Mixed Reality Toolkit (opción para cambiar la visualización de reconocimiento espacial)</span><span class="sxs-lookup"><span data-stu-id="96681-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="96681-115">En esta sección, aprenderás a personalizar y configurar los perfiles predeterminados de MRTK.</span><span class="sxs-lookup"><span data-stu-id="96681-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="96681-116">En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="96681-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="96681-117">Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="96681-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="96681-118">Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="96681-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="96681-119">Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="96681-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="96681-120">Habilitar el sistema de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="96681-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="96681-121">Clonar el perfil del sistema de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="96681-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="96681-122">Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="96681-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="96681-123">Cambiar la visibilidad de la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="96681-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="96681-124">De forma predeterminada, los perfiles de MRTK no son editables.</span><span class="sxs-lookup"><span data-stu-id="96681-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="96681-125">Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse.</span><span class="sxs-lookup"><span data-stu-id="96681-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="96681-126">Hay varias capas anidadas de perfiles.</span><span class="sxs-lookup"><span data-stu-id="96681-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="96681-127">Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.</span><span class="sxs-lookup"><span data-stu-id="96681-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="96681-128">1. Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="96681-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="96681-129">El perfil de configuración es el perfil de nivel superior.</span><span class="sxs-lookup"><span data-stu-id="96681-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="96681-130">Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="96681-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="96681-131">Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, cambia el valor de **Configuration Profile** (Perfil de configuración) de Mixed Reality Toolkit a **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="96681-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="96681-133">Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="96681-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="96681-135">En la ventana Clone Profile (Clonar perfil), haz clic en el botón **Clone** (Clonar) para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="96681-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="96681-137">El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:</span><span class="sxs-lookup"><span data-stu-id="96681-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="96681-139">En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.</span><span class="sxs-lookup"><span data-stu-id="96681-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="96681-140">Recuerda guardar el trabajo a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="96681-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="96681-141">2. Habilitar el sistema de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="96681-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="96681-142">Con el objeto **MixedRealityToolkit** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, selecciona la pestaña **Reconocimiento espacial** y, a continuación, activa la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):</span><span class="sxs-lookup"><span data-stu-id="96681-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="96681-144">3. Clonar el perfil del sistema de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="96681-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="96681-145">En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="96681-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="96681-147">En la ventana Clone Profile (Clonar perfil), haz clic en el botón **Clone** (Clonar) para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="96681-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="96681-149">Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:</span><span class="sxs-lookup"><span data-stu-id="96681-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="96681-151">4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado</span><span class="sxs-lookup"><span data-stu-id="96681-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="96681-152">Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):</span><span class="sxs-lookup"><span data-stu-id="96681-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="96681-154">En la ventana Clone Profile (Clonar perfil), haz clic en el botón **Clone** (Clonar) para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="96681-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="96681-156">Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:</span><span class="sxs-lookup"><span data-stu-id="96681-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="96681-158">5. Cambiar la visibilidad de la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="96681-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="96681-159">En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambia **Display Option** (Opción de visualización) a **Occlusion** (Oclusión) para que la malla de asignación espacial sea invisible y, al mismo tiempo, funcional:</span><span class="sxs-lookup"><span data-stu-id="96681-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="96681-161">Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional.</span><span class="sxs-lookup"><span data-stu-id="96681-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="96681-162">Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.</span><span class="sxs-lookup"><span data-stu-id="96681-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="96681-163">Acabas de aprender a modificar una configuración en el perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="96681-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="96681-164">Como puedes ver, para personalizar la configuración de MRTK, debes crear copias de los perfiles predeterminados.</span><span class="sxs-lookup"><span data-stu-id="96681-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="96681-165">Dado que los perfiles predeterminados no son editables, siempre los tendrás como referencia si quieres revertir la configuración predeterminada.</span><span class="sxs-lookup"><span data-stu-id="96681-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="96681-166">Para obtener más información sobre los perfiles de MRTK y su arquitectura, puedes visitar la [guía de configuración de perfiles de Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="96681-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="96681-167">Botones de interacción y gestos de seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="96681-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="96681-168">En esta sección, aprenderás a usar el seguimiento de manos para presionar un botón y desencadenar eventos para provocar una acción al presionar el botón.</span><span class="sxs-lookup"><span data-stu-id="96681-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="96681-169">En este ejemplo concreto, se muestra cómo cambiar el color de un cubo cuando se presiona el botón y cambiarlo a su color original cuando se suelta.</span><span class="sxs-lookup"><span data-stu-id="96681-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="96681-170">Sin embargo, puedes seguir estos mismos principios para crear otros eventos.</span><span class="sxs-lookup"><span data-stu-id="96681-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="96681-171">Los principales pasos que se deben seguir para cambiar el color del cubo son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="96681-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="96681-172">Agregar un objeto prefabricado de botón presionable a la escena</span><span class="sxs-lookup"><span data-stu-id="96681-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="96681-173">Agregar un cubo a la escena</span><span class="sxs-lookup"><span data-stu-id="96681-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="96681-174">Configurar el tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="96681-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="96681-175">Configurar el cubo para recibir el evento On Press (Al presionar)</span><span class="sxs-lookup"><span data-stu-id="96681-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="96681-176">Definir la acción que desencadenará el evento On Press (Al presionar)</span><span class="sxs-lookup"><span data-stu-id="96681-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="96681-177">Configurar el cubo para recibir el evento On Release (Al soltar)</span><span class="sxs-lookup"><span data-stu-id="96681-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="96681-178">Definir la acción que desencadenará el evento On Release (Al soltar)</span><span class="sxs-lookup"><span data-stu-id="96681-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="96681-179">Probar el botón mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="96681-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="96681-180">1. Agregar un objeto prefabricado de botón presionable a la escena</span><span class="sxs-lookup"><span data-stu-id="96681-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="96681-181">Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.</span><span class="sxs-lookup"><span data-stu-id="96681-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="96681-182">En la **ventana del proyecto**, busca **PressableButtonHoloLens2** para buscar el objeto prefabricado que usarás en este ejemplo:</span><span class="sxs-lookup"><span data-stu-id="96681-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="96681-184">En el resultado de la **búsqueda**, selecciona el objeto prefabricado **PressableButtonHoloLens2** y **arrástralo** a la ventana **Hierarchy** (Jerarquía) para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="96681-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="96681-186">Para mostrar la escena tal y como se muestra en la imagen siguiente, haz doble clic en el objeto PressableButtonHoloLens2 en la ventana Hierarchy (Jerarquía) para ponerlo en el foco y, a continuación, usa el <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">gizmo de escena</a>, situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z.</span><span class="sxs-lookup"><span data-stu-id="96681-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="96681-187">Con el objeto **PressableButtonHoloLens2** todavía seleccionado, en la ventana **Inspector**:</span><span class="sxs-lookup"><span data-stu-id="96681-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="96681-188">Cambia su **posición** de transformación para que se coloque delante de la cámara, que está situada en el origen; por ejemplo, x = 0, y = 0 y z = 0,5.</span><span class="sxs-lookup"><span data-stu-id="96681-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="96681-190">En general, 1 unidad de posición en Unity equivale, aproximadamente, a 1 metro en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="96681-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="96681-191">Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.</span><span class="sxs-lookup"><span data-stu-id="96681-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="96681-192">2. Agregar un cubo a la escena</span><span class="sxs-lookup"><span data-stu-id="96681-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="96681-193">Haz clic con el botón derecho en una zona vacía dentro de la ventana Hierarchy (Jerarquía) y selecciona **3D Object** > **Cube** (Objeto 3D > Cubo) para agregar un cubo a la escena:</span><span class="sxs-lookup"><span data-stu-id="96681-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="96681-195">Con el objeto **Cube** todavía seleccionado, en la ventana **Inspector**:</span><span class="sxs-lookup"><span data-stu-id="96681-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="96681-196">Cambia su **posición** de transformación para que esté cerca del botón que se pueda presionar, pero no se solape con él; por ejemplo, x = 0, y = 0,04 y z = 0,5</span><span class="sxs-lookup"><span data-stu-id="96681-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="96681-197">Cambia su **escala** de transformación a un tamaño adecuado; por ejemplo, x = 0,02, y = 0,02 y z = 0,02.</span><span class="sxs-lookup"><span data-stu-id="96681-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="96681-199">3. Configurar el tipo de evento InteractableOnPressReceiver</span><span class="sxs-lookup"><span data-stu-id="96681-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="96681-200">En la ventana Hierarchy (Jerarquía), selecciona el objeto **PressableButtonHoloLens2** y, a continuación, en la ventana **Inspector**, en el **menú de hamburguesa**, selecciona **Collapse All Components** (Contraer todos los componentes) para obtener una visión general de todos los componentes de este objeto:</span><span class="sxs-lookup"><span data-stu-id="96681-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="96681-202">Expande el componente **Interactable (Script)** (Interactuable [script]) y, a continuación, busca y expande la sección **Events** > **Receivers** (Eventos > Receptores):</span><span class="sxs-lookup"><span data-stu-id="96681-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="96681-204">Haz clic en el botón **Add Event** (Agregar evento) para crear un nuevo receptor de eventos del tipo **InteractableOnPressReceiver**:</span><span class="sxs-lookup"><span data-stu-id="96681-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="96681-206">El tipo de receptor de eventos InteractableOnPressReceiver permite que el botón responda a un evento presionado cuando una mano con seguimiento presiona el botón.</span><span class="sxs-lookup"><span data-stu-id="96681-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="96681-207">En el caso del receptor de eventos recién creado, cambia **Interaction Filter** (Filtro de interacción) a **Near and Far** (Cerca y lejos):</span><span class="sxs-lookup"><span data-stu-id="96681-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="96681-209">4. Configurar el cubo para recibir el evento On Press (Al presionar)</span><span class="sxs-lookup"><span data-stu-id="96681-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="96681-210">En la ventana Hierarchy (Jerarquía), **haz clic y arrastra** **Cube** (Cubo) al campo de objeto **Event Properties** (Propiedades de evento) para el evento **On Press ()** (Al presionar []) para asignar el cubo como receptor del evento On Press () (Al presionar []):</span><span class="sxs-lookup"><span data-stu-id="96681-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="96681-212">5. Definir la acción que desencadenará el evento On Press (Al presionar)</span><span class="sxs-lookup"><span data-stu-id="96681-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="96681-213">Haz clic en la lista desplegable de acción, asignada actualmente a **No Function** (Ninguna función) y selecciona **MeshRenderer** > **Material** para establecer la propiedad de material del cubo que se cambiará cuando se desencadene el evento On Press () (Al presionar []):</span><span class="sxs-lookup"><span data-stu-id="96681-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="96681-215">Haz clic en el pequeño icono de **círculo** situado junto al campo de material, actualmente con el valor**None (Material)** Ninguno (material), para abrir la ventana Select Material (Seleccionar material):</span><span class="sxs-lookup"><span data-stu-id="96681-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="96681-217">En la ventana Select Material (Seleccionar material), **busca** **MRTK_Standard** y selecciona un material adecuado; por ejemplo, **MRTK_Standard_Cyan** para que el color del cubo cambie a cian al presionar el botón:</span><span class="sxs-lookup"><span data-stu-id="96681-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="96681-219">6. Configurar el cubo para recibir el evento On Release (Al soltar)</span><span class="sxs-lookup"><span data-stu-id="96681-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="96681-220">**Repite** el paso 4 para el evento On Release (Al soltar) para asignar el **cubo** como receptor del evento **On Release ()** (Al soltar []).</span><span class="sxs-lookup"><span data-stu-id="96681-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="96681-221">7. Definir la acción que desencadenará el evento On Release (Al soltar)</span><span class="sxs-lookup"><span data-stu-id="96681-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="96681-222">**Repite** el paso 5 para el evento On Release (Al soltar), pero elige el material **MRTK_Standard_LightGray** para que el color del cubo vuelva a su gris claro original al soltar el botón:</span><span class="sxs-lookup"><span data-stu-id="96681-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="96681-224">8. Probar el botón mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="96681-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="96681-225">Presiona el botón **Play** (Jugar) para entrar en el modo de juego y usa la simulación de entrada del editor para probar el botón que acabas de configurar.</span><span class="sxs-lookup"><span data-stu-id="96681-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="96681-226">Botón sin presionar (barra espaciadora + rueda hacia atrás del ratón):</span><span class="sxs-lookup"><span data-stu-id="96681-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="96681-228">Botón presionado (barra espaciadora + rueda hacia adelante del ratón):</span><span class="sxs-lookup"><span data-stu-id="96681-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="96681-230">Para obtener información sobre cómo usar la simulación de entrada del editor, puedes consultar la guía [Uso de la simulación de entrada de mano en el editor para probar una escena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="96681-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="96681-231">Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK</span><span class="sxs-lookup"><span data-stu-id="96681-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="96681-232">En esta sección, aprenderás a alinear automáticamente varios botones en una interfaz de usuario nueva mediante la herramienta GridObjectCollection de MRTK.</span><span class="sxs-lookup"><span data-stu-id="96681-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="96681-233">En este ejemplo concreto se muestra cómo crear un panel con cinco botones alineados horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="96681-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="96681-234">Sin embargo, puedes seguir estos mismos principios para crear diseños.</span><span class="sxs-lookup"><span data-stu-id="96681-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="96681-235">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="96681-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="96681-236">Asignar los objetos de botón a un objeto principal</span><span class="sxs-lookup"><span data-stu-id="96681-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="96681-237">Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])</span><span class="sxs-lookup"><span data-stu-id="96681-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="96681-238">Probar los botones mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="96681-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="96681-239">1. Asignar los objetos de botón a un objeto principal</span><span class="sxs-lookup"><span data-stu-id="96681-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="96681-240">Haz clic con el botón derecho en una zona vacía dentro de la ventana Hierarchy (Jerarquía) y selecciona **Create Empty** (Crear objeto vacío):</span><span class="sxs-lookup"><span data-stu-id="96681-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="96681-242">Haz clic con el botón derecho en el objeto que acabas de crear, selecciona **Rename** (Cambiar nombre) y asígnale un nombre adecuado; por ejemplo, **ButtonCollection**:</span><span class="sxs-lookup"><span data-stu-id="96681-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="96681-244">Selecciona el objeto **PressableButtonHoloLens2** y **arrástralo** encima del objeto **ButtonCollection** para convertirlo en un elemento secundario de este objeto:</span><span class="sxs-lookup"><span data-stu-id="96681-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="96681-246">Haz clic con el botón derecho en el objeto **PressableButtonHoloLens2** y selecciona **Duplicar** para crear una copia de este:</span><span class="sxs-lookup"><span data-stu-id="96681-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="96681-248">**Repite** este paso cuatro veces más hasta que tengas un total de cinco objetos PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="96681-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="96681-249">2. Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])</span><span class="sxs-lookup"><span data-stu-id="96681-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="96681-250">Con el objeto ButtonCollection seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, haz clic en el botón **Add Component** (Agregar componente) y, a continuación, busca y selecciona **Grid Object Collection** (Colección de objetos de cuadrícula) para agregar un componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script]) al objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="96681-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="96681-252">Configura el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="96681-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="96681-253">Cambia **Num Rows** (Número de filas) a 1 para que todos los botones estén alineados en una sola fila.</span><span class="sxs-lookup"><span data-stu-id="96681-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="96681-254">Cambia **Cell Width** (Ancho de celda) a 0,05 para espaciar los botones dentro de la fila.</span><span class="sxs-lookup"><span data-stu-id="96681-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="96681-255">A continuación, haz clic en el botón **Actualizar colección** para aplicar la nueva configuración:</span><span class="sxs-lookup"><span data-stu-id="96681-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="96681-257">Los cambios de configuración que acabas de aplicar representan los cambios mínimos necesarios para lograr el objetivo de colocar los botones en una sola fila.</span><span class="sxs-lookup"><span data-stu-id="96681-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="96681-258">Sin embargo, en proyectos futuros, en función de factores como, por ejemplo, la orientación de los objetos principales y secundarios, es posible que necesites ajustar otras opciones de configuración, como, por ejemplo, el tipo de orientación.</span><span class="sxs-lookup"><span data-stu-id="96681-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="96681-259">Para obtener más información sobre la colección de objetos de cuadrícula de MRTK, puedes visitar la guía de [scripts de colección de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="96681-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="96681-260">Con el objeto ButtonCollection aún seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, cambia la **posición** de transformación del objeto ButtonCollection para que los objetos de botón secundarios se sitúen delante de la cámara, que se encuentra en el origen; por ejemplo, x = 0, y = 0 y z = 0,5:</span><span class="sxs-lookup"><span data-stu-id="96681-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="96681-262">La primera vez que se agregó el objeto prefabricado PressableButtonHoloLens2 a la escena en la sección [Botones de interacción y gestos de seguimiento de la mano](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) anterior, lo colocaste delante de la cámara.</span><span class="sxs-lookup"><span data-stu-id="96681-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="96681-263">Sin embargo, dado que la colección de objetos de cuadrícula controla la posición de sus objetos secundarios inmediatos, la posición Z de los objetos secundarios de PressableButtonHoloLens2 se restableció a 0 de acuerdo con la distancia predeterminada de la colección de objetos de cuadrícula del valor principal de 0.</span><span class="sxs-lookup"><span data-stu-id="96681-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="96681-264">Por este motivo, y para mantener organizada la relación de posición entre el objeto principal y el secundario, hemos movido la posición del objeto ButtonCollection hacia adelante en lugar de configurar la distancia del valor principal para que mueva los objetos secundarios de PressableButtonHoloLens2 hacia adelante.</span><span class="sxs-lookup"><span data-stu-id="96681-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="96681-265">3. Probar los botones mediante la simulación en el editor</span><span class="sxs-lookup"><span data-stu-id="96681-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="96681-266">Presiona el botón Play (Jugar) para entrar en el modo de juego y usa la simulación de entrada del editor para probar cada uno de los botones del panel de botones que acabas de crear:</span><span class="sxs-lookup"><span data-stu-id="96681-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="96681-268">Actualmente, cuando se presiona cualquiera de los cinco botones, el color del cubo cambia a cian.</span><span class="sxs-lookup"><span data-stu-id="96681-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="96681-269">Para que la experiencia sea más interesante, usa lo que acabas de aprender para configurar cada botón y cambiar el cubo a otro color.</span><span class="sxs-lookup"><span data-stu-id="96681-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="96681-270">Adición de texto a la escena</span><span class="sxs-lookup"><span data-stu-id="96681-270">Adding text into your scene</span></span>

<span data-ttu-id="96681-271">En esta sección, aprenderás a agregar texto a tus experiencias de realidad mixta con TextMesh Pro de Unity, que preparaste en la sección [Importación de recursos esenciales de TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) del tutorial anterior.</span><span class="sxs-lookup"><span data-stu-id="96681-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="96681-272">En este ejemplo concreto, agregarás una etiqueta sencilla bajo la colección de botones que creaste en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="96681-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="96681-273">Haz clic con el botón derecho en el objeto ButtonCollection y selecciona **3D Object** > **Text - TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para crear un objeto TextMeshPro como elemento secundario del objeto ButtonCollection:</span><span class="sxs-lookup"><span data-stu-id="96681-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="96681-275">Con el objeto TextMeshPro que acabas de crear, denominado Text (TMP), aún seleccionado, en la ventana Inspector, cambia su posición y tamaño para que la etiqueta se coloque estratégicamente bajo la colección de botones; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="96681-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="96681-276">Cambia el valor de **Pos Y** de transformación de rectángulo a 0,0425.</span><span class="sxs-lookup"><span data-stu-id="96681-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="96681-277">Cambia el valor **Width** (Ancho) de transformación de rectángulo a 0,24.</span><span class="sxs-lookup"><span data-stu-id="96681-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="96681-278">Cambia el valor **Height** (Altura) de transformación de rectángulo a 0,024.</span><span class="sxs-lookup"><span data-stu-id="96681-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="96681-279">A continuación, actualiza el texto para que refleje el propósito de la etiqueta y elige las propiedades de la fuente para que el texto se ajuste a la etiqueta; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="96681-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="96681-280">Cambia el valor **Text** (Texto) de Text Mesh Pro (Script) a Button Collection (Colección de botones).</span><span class="sxs-lookup"><span data-stu-id="96681-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="96681-281">Cambia el valor **Font Style** (Estilo de fuente) de Text Mesh Pro (Script) a Bold (Negrita).</span><span class="sxs-lookup"><span data-stu-id="96681-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="96681-282">Cambia el valor **Font Size** (Tamaño de fuente) de Text Mesh Pro (Script) a 0,2.</span><span class="sxs-lookup"><span data-stu-id="96681-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="96681-283">Cambia el valor **Alignment** (Alineación) de Text Mesh Pro (Script) a Center and Middle (Centro y medio).</span><span class="sxs-lookup"><span data-stu-id="96681-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="96681-285">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="96681-285">Congratulations</span></span>

<span data-ttu-id="96681-286">En este tutorial, has aprendido a clonar, personalizar y configurar las opciones de un perfil de MRTK.</span><span class="sxs-lookup"><span data-stu-id="96681-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="96681-287">También has aprendido a interactuar con botones para desencadenar eventos mediante el seguimiento de manos en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="96681-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="96681-288">Por último, has aprendido a crear una sencilla interfaz de usuario mediante el componente de colección de objetos de cuadrícula de MRTK y Text Mesh Pro de Unity.</span><span class="sxs-lookup"><span data-stu-id="96681-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="96681-289">Tutorial siguiente: 4. Colocación del contenido dinámico y uso de solucionadores</span><span class="sxs-lookup"><span data-stu-id="96681-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
