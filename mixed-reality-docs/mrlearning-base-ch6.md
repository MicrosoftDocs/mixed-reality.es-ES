---
title: 'Tutoriales de introducción: 7. Creación de una aplicación de ejemplo de módulo lunar'
description: En esta lección, agruparás varios conceptos aprendidos de lecciones anteriores para crear una experiencia de ejemplo única.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031563"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="85963-105">7. Creación de una aplicación de ejemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="85963-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="85963-106">En este tutorial, se combinan varios conceptos de lecciones anteriores para crear una experiencia de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="85963-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="85963-107">Aprenderás a crear una aplicación de ensamblado de piezas con la que el usuario tendrá que usar el seguimiento de manos para seleccionar las piezas e intentar ensamblar un módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="85963-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="85963-108">Usarás botones presionables para activar y desactivar las sugerencias de colocación, restablecer la experiencia y lanzar el módulo lunar al espacio.</span><span class="sxs-lookup"><span data-stu-id="85963-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="85963-109">En futuros tutoriales, continuarás ampliando esta experiencia, lo que incluye casos de uso multiusuario que aprovechan Azure Spatial Anchors para la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="85963-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="85963-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="85963-110">Objectives</span></span>

* <span data-ttu-id="85963-111">Agrupar varios conceptos de lecciones anteriores para crear una experiencia única</span><span class="sxs-lookup"><span data-stu-id="85963-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="85963-112">Obtener información sobre cómo activar o desactivar los objetos</span><span class="sxs-lookup"><span data-stu-id="85963-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="85963-113">Desencadenar eventos complejos mediante los botones presionables</span><span class="sxs-lookup"><span data-stu-id="85963-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="85963-114">Usar la física y la fuerza de los cuerpos rígidos</span><span class="sxs-lookup"><span data-stu-id="85963-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="85963-115">Explorar el uso de la información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="85963-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="85963-116">Introducción a las piezas del módulo lunar</span><span class="sxs-lookup"><span data-stu-id="85963-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="85963-117">En esta sección, crearás un desafío de ensamblado de piezas sencillo en que el objetivo del usuario será colocar cinco piezas distribuidas en la tabla en la ubicación correcta en el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="85963-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="85963-118">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="85963-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="85963-119">Agregar el objeto prefabricado del lanzacohetes a la escena</span><span class="sxs-lookup"><span data-stu-id="85963-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="85963-120">Habilitar la manipulación de objetos para todas las piezas</span><span class="sxs-lookup"><span data-stu-id="85963-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="85963-121">Agregar y configurar el componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script])</span><span class="sxs-lookup"><span data-stu-id="85963-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="85963-122">El componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script]) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85963-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="85963-123">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="85963-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="85963-124">1. Agregar el objeto prefabricado del lanzacohetes a la escena</span><span class="sxs-lookup"><span data-stu-id="85963-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="85963-125">En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > carpeta Objetos prefabricados > RocketLauncher), arrastra el objeto prefabricado **RocketLauncher** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena y, a continuación, colócalo en una ubicación adecuada; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="85963-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="85963-126">Posición de transformación X = 1,5, Y = -0,4, Z = 0, a la derecha del usuario a la altura de la cintura</span><span class="sxs-lookup"><span data-stu-id="85963-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="85963-127">Giro de transformación X = 0, Y = 180, Z = 0, para que las características principales de la experiencia estén orientadas al usuario</span><span class="sxs-lookup"><span data-stu-id="85963-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="85963-129">2. Habilitar la manipulación de objetos para todas las piezas</span><span class="sxs-lookup"><span data-stu-id="85963-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="85963-130">En la ventana Hierarchy (Jerarquía), busca el objeto RocketLauncher > **LunarModuleParts** y selecciona todos los **objetos secundarios**, agrega el componente **Manipulation Handler (Script)** (Controlador de manipulación [script]) y el componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script]) y configura Manipulation Handler (Script) (Controlador de manipulación [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="85963-131">Desactiva la casilla **Allow Far Manipulation** (Permitir la manipulación lejana) para permitir solo la interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="85963-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="85963-132">Cambia **Two Handed Manipulation Type**(Tipo de manipulación de dos manos) a **Move Rotate** (Movimiento de giro) para deshabilitar el escalado.</span><span class="sxs-lookup"><span data-stu-id="85963-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="85963-134">Para obtener un recordatorio con instrucciones detalladas sobre cómo implementar la manipulación de objetos, puedes consultar las instrucciones de [Manipulación de objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects).</span><span class="sxs-lookup"><span data-stu-id="85963-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="85963-135">3. Agregar y configurar el componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script])</span><span class="sxs-lookup"><span data-stu-id="85963-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="85963-136">Con todos los objetos secundarios de LunarModuleParts todavía seleccionados, agrega un componente de **Audio Source** (Origen de audio) y, a continuación, configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="85963-137">Asigna un clip de audio adecuado al campo **AudioClip**; por ejemplo, MRKT_Scale_Start.</span><span class="sxs-lookup"><span data-stu-id="85963-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="85963-138">Desactiva la casilla **Play On Awake** (Reproducir al reactivar) para que el clip de audio no se reproduzca automáticamente cuando se cargue la escena.</span><span class="sxs-lookup"><span data-stu-id="85963-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="85963-139">Cambia la opción **Spatial Blend** (Combinación espacial) a 1 para habilitar el audio espacial.</span><span class="sxs-lookup"><span data-stu-id="85963-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="85963-141">Con todos los objetos secundarios de LunarModuleParts todavía seleccionados, agrega el componente **Part Assembly Demo (Script)** (Demostración de ensamblado de piezas [script]):</span><span class="sxs-lookup"><span data-stu-id="85963-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="85963-143">En la ventana Hierarchy (Jerarquía), selecciona el objeto **RoverEnclosure** y configura su componente **Part Assembly Demo (Script)** (Demostración de ensamblado de piezas [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="85963-144">En el campo **Object To Place** (Objeto que colocar), asigna el **propio** objeto; en este caso, el objeto RoverEnclosure.</span><span class="sxs-lookup"><span data-stu-id="85963-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="85963-145">En el campo **Location To Place** (Ubicación para colocar), asigna el objeto **PlacementHints** correspondiente; en este caso, el objeto RoverEnclosure_PlacementHint.</span><span class="sxs-lookup"><span data-stu-id="85963-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="85963-146">En el campo **Tool Tip Object** (Objeto de información sobre herramientas), asigna el valor de **ToolTip** (Información sobre herramientas) correspondiente. En este caso, el objeto RoverEnclosure_ToolTip.</span><span class="sxs-lookup"><span data-stu-id="85963-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="85963-147">En el campo **Audio Source** (Origen de audio), asigna el **propio** objeto; en este caso, el objeto RoverEnclosure.</span><span class="sxs-lookup"><span data-stu-id="85963-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="85963-149">**Repite** para cada uno de los demás objetos secundarios de LunarModuleParts; por ejemplo, FuelTank, EnergyCell, DockingPortal y ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="85963-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="85963-150">Si ahora entras en el modo de juego y mueve un objeto que colocar cerca de su ubicación para colocar correspondiente, observarás lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="85963-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="85963-151">El objeto se ajustará en su lugar y se colocará bajo el objeto principal LunarModule para que forme parte del módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="85963-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="85963-152">El origen de audio del objeto reproducirá el clip de audio asignado en la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="85963-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="85963-153">Se ocultará el objeto de información sobre herramientas correspondiente.</span><span class="sxs-lookup"><span data-stu-id="85963-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="85963-155">Para obtener un recordatorio sobre cómo usar la simulación de entrada del editor, puedes consultar la guía [Uso de la simulación de entrada de mano en el editor para probar una escena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="85963-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="85963-156">Configuración del módulo lunar</span><span class="sxs-lookup"><span data-stu-id="85963-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="85963-157">En esta sección, agregarás características adicionales a la aplicación del lanzacohetes para que el usuario pueda:</span><span class="sxs-lookup"><span data-stu-id="85963-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="85963-158">Interactuar con el módulo lunar</span><span class="sxs-lookup"><span data-stu-id="85963-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="85963-159">Lanzar el módulo lunar al espacio y reproducir un sonido al hacerlo</span><span class="sxs-lookup"><span data-stu-id="85963-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="85963-160">Restablecer la aplicación para que el módulo lunar y todas sus partes vuelvan a su posición original</span><span class="sxs-lookup"><span data-stu-id="85963-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="85963-161">Oculta las sugerencias de selección de ubicación para dificultar el desafío del ensamblado de piezas.</span><span class="sxs-lookup"><span data-stu-id="85963-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="85963-162">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="85963-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="85963-163">Habilitar la manipulación de objetos</span><span class="sxs-lookup"><span data-stu-id="85963-163">Enable object manipulation</span></span>
2. <span data-ttu-id="85963-164">Habilitar la física</span><span class="sxs-lookup"><span data-stu-id="85963-164">Enable physics</span></span>
3. <span data-ttu-id="85963-165">Agregar un componente de origen de audio</span><span class="sxs-lookup"><span data-stu-id="85963-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="85963-166">Agregar y configurar el componente Launch Lunar Module (Script) (Lanzar módulo lunar [script])</span><span class="sxs-lookup"><span data-stu-id="85963-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="85963-167">Agregar y configurar el componente Toggle Placement Hints (Script) (Activar o desactivar sugerencias de colocación [script])</span><span class="sxs-lookup"><span data-stu-id="85963-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="85963-168">Los componentes Launch Lunar Module (Script) (Lanzar módulo lunar [script]) y Toggle Placement Hints (Script) (Activar o desactivar sugerencias de colocación [script]) no forman parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="85963-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="85963-169">Se proporcionaron con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="85963-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="85963-170">1. Habilitar la manipulación de objetos</span><span class="sxs-lookup"><span data-stu-id="85963-170">1. Enable object manipulation</span></span>

<span data-ttu-id="85963-171">En la ventana Hierarchy (Jerarquía), selecciona el objeto RocketLauncher > **LunarModule**, agrega el componente **Manipulation Handler (Script)** (Controlador de manipulación [script]) y el componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script]) y configura Manipulation Handler (Script) (Controlador de manipulación [script]) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="85963-172">Desactiva la casilla **Allow Far Manipulation** (Permitir la manipulación lejana) para permitir solo la interacción cercana.</span><span class="sxs-lookup"><span data-stu-id="85963-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="85963-173">Cambia **Two Handed Manipulation Type**(Tipo de manipulación de dos manos) a Move Rotate (Movimiento de giro) para deshabilitar el escalado.</span><span class="sxs-lookup"><span data-stu-id="85963-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="85963-175">2. Habilitar la física</span><span class="sxs-lookup"><span data-stu-id="85963-175">2. Enable physics</span></span>

<span data-ttu-id="85963-176">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega un componente **Rigidbody** y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="85963-177">Desactiva la casilla **Use Gravity** (Usar gravedad) para que el módulo lunar no se vea afectado por la gravedad.</span><span class="sxs-lookup"><span data-stu-id="85963-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="85963-178">Activa la casilla **Is Kinematic** (Es cinemático) para que el módulo lunar no se vea inicialmente afectado por las fuerzas físicas.</span><span class="sxs-lookup"><span data-stu-id="85963-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="85963-180">3. Agregar un componente de origen de audio</span><span class="sxs-lookup"><span data-stu-id="85963-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="85963-181">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega un componente de **Audio Source** (Origen de audio) y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="85963-182">Cambia la opción **Spatial Blend** (Combinación espacial) a 1 para habilitar el audio espacial.</span><span class="sxs-lookup"><span data-stu-id="85963-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="85963-184">4. Agregar y configurar el componente Launch Lunar Module (Script) (Lanzar módulo lunar [script])</span><span class="sxs-lookup"><span data-stu-id="85963-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="85963-185">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega el componente **Launch Lunar Module (Script)** (Lanzar módulo lunar [script]) y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="85963-186">Cambia el valor de **Thrust** (Impulso) para que el módulo lunar vuele correctamente cuando se lance; por ejemplo, a 0,01.</span><span class="sxs-lookup"><span data-stu-id="85963-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="85963-188">5. Agregar y configurar el componente Toggle Placement Hints (Script) (Activar o desactivar sugerencias de colocación [script])</span><span class="sxs-lookup"><span data-stu-id="85963-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="85963-189">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega el componente **Toggle Placement Hints (Script)** (Activar o desactivar sugerencias de colocación [script]) y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="85963-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="85963-190">Establece la propiedad **Size** (Tamaño) de la matriz de objetos de juego en 5.</span><span class="sxs-lookup"><span data-stu-id="85963-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="85963-191">Asigna cada uno de los **objetos secundarios** del objeto **PlacementHints** a un campo **Element** (Elemento) de la matriz de objetos de juego:</span><span class="sxs-lookup"><span data-stu-id="85963-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="85963-193">Configuración del botón Launch (Lanzar)</span><span class="sxs-lookup"><span data-stu-id="85963-193">Configuring the Launch button</span></span>

<span data-ttu-id="85963-194">En la ventana Hierarchy (Jerarquía), selecciona RocketLauncher > Buttons (Botones) > objeto **LaunchButton**. A continuación, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento y define **LaunchLunarModule.StartThruster** como la acción que se desencadenará:</span><span class="sxs-lookup"><span data-stu-id="85963-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="85963-196">Para obtener un recordatorio sobre cómo implementar eventos, puedes hacer referencia a las instrucciones sobre [gestos de seguimiento de manos y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).</span><span class="sxs-lookup"><span data-stu-id="85963-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="85963-197">Con el objeto RocketLauncher > Buttons (Botones) > **LaunchButton** aún seleccionado, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento, define **AudioSource.PlayOneShot** como acción que se desencadenará y asigna un clip de audio adecuado al campo **Audio Clip** (Clip de audio); por ejemplo, el clip de audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="85963-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="85963-199">Con el objeto RocketLauncher > Buttons (Botones) > **LaunchButton** aún seleccionado, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Touch End ()** (Fin del toque []), configura el objeto **LunarModule** para recibir el evento y define **LaunchLunarModule.StopThruster** como la acción que se desencadenará:</span><span class="sxs-lookup"><span data-stu-id="85963-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="85963-201">Si ahora entras en el modo de juego y presionas el botón Launch (Iniciar), oirás el clip de audio reproduciéndose y, si mantienes presionado el botón Launch (Lanzar) un segundo o más, verás el lanzamiento del módulo lunar al espacio:</span><span class="sxs-lookup"><span data-stu-id="85963-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="85963-203">Configuración del botón Reset (Restablecer)</span><span class="sxs-lookup"><span data-stu-id="85963-203">Configuring the Reset button</span></span>

<span data-ttu-id="85963-204">En la ventana Hierarchy (Jerarquía), selecciona RocketLauncher > Buttons (Botones) > objeto **ResetButton**. A continuación, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento y define **LaunchLunarModule.ResetModule** como la acción que se desencadenará:</span><span class="sxs-lookup"><span data-stu-id="85963-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="85963-206">Con el objeto RocketLauncher > Buttons (Botones) > **ResetButton** aún seleccionado, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **RocketLauncher** para recibir el evento, define **GameObject.BroadcastMessage** como acción que se debe desencadenar y escribe **ResetPlacement** en el campo de mensaje:</span><span class="sxs-lookup"><span data-stu-id="85963-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="85963-208">La acción GameObject.BroadcastMessage envía el mensaje ResetPlacement del objeto RocketLauncher a todos sus objetos secundarios.</span><span class="sxs-lookup"><span data-stu-id="85963-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="85963-209">Cualquier objeto secundario que tenga la función ResetPlacement, que se define en el componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script]) que has agregado a todos los objetos secundarios de LunarModuleParts, invocará la función ResetPlacement, que restablece la posición del objeto secundario.</span><span class="sxs-lookup"><span data-stu-id="85963-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="85963-210">Si ahora entras en modo de juego, mueves algunas piezas o lanzas el módulo lunar y, a continuación, presionas el botón Reset (Restablecer), verás que se restaura la posición original de las piezas o el módulo lunar:</span><span class="sxs-lookup"><span data-stu-id="85963-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="85963-212">Configuración del botón Placement Hints (Sugerencias de selección de ubicación)</span><span class="sxs-lookup"><span data-stu-id="85963-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="85963-213">En la ventana Hierarchy (Jerarquía), selecciona RocketLauncher > Buttons (Botones) > objeto **HintsButton**. A continuación, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento y define **TogglePlacementHints.ToggleGameObjects** como la acción que se desencadenará:</span><span class="sxs-lookup"><span data-stu-id="85963-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="85963-215">Si ahora entras en el modo de juego, observarás que las sugerencias de selección de ubicación están deshabilitadas de forma predeterminada, pero puedes activarlas y desactivarlas presionando el botón Hints (Sugerencias):</span><span class="sxs-lookup"><span data-stu-id="85963-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="85963-217">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="85963-217">Congratulations</span></span>

<span data-ttu-id="85963-218">Ya has configurado totalmente esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="85963-218">You have fully configured this application.</span></span> <span data-ttu-id="85963-219">Ahora, la aplicación permite a los usuarios ensamblar completamente el módulo lunar, lanzarlo, activar o desactivar las sugerencias y reiniciar la aplicación para volver a empezar</span><span class="sxs-lookup"><span data-stu-id="85963-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
