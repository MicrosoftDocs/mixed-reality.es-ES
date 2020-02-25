---
title: 'Tutoriales de introducción: 7. Crear una aplicación de ejemplo de módulo lunar'
description: En esta lección, combinará varios conceptos aprendidos en lecciones anteriores para crear una experiencia de ejemplo única.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555284"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="d371a-105">7. crear una aplicación de ejemplo de módulo lunar</span><span class="sxs-lookup"><span data-stu-id="d371a-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="d371a-106">En este tutorial, se combinan varios conceptos de lecciones anteriores para crear una experiencia de ejemplo única.</span><span class="sxs-lookup"><span data-stu-id="d371a-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="d371a-107">Aprenderá a crear una aplicación de ensamblado de elementos en la que un usuario necesita usar manos con seguimiento para recoger piezas e intentar ensamblar un módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="d371a-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="d371a-108">Usará los botones que se puede presionar para activar o desactivar las sugerencias de colocación, para restablecer la experiencia y para iniciar el módulo lunar en el espacio.</span><span class="sxs-lookup"><span data-stu-id="d371a-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="d371a-109">En los tutoriales futuros, continuará teniendo en cuenta esta experiencia, que incluye eficaces casos de uso de varios usuarios que aprovechan los delimitadores espaciales de Azure para la alineación espacial.</span><span class="sxs-lookup"><span data-stu-id="d371a-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="d371a-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d371a-110">Objectives</span></span>

* <span data-ttu-id="d371a-111">Agrupar varios conceptos de lecciones anteriores para crear una experiencia única</span><span class="sxs-lookup"><span data-stu-id="d371a-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="d371a-112">Obtener información sobre cómo activar o desactivar los objetos</span><span class="sxs-lookup"><span data-stu-id="d371a-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="d371a-113">Desencadenar eventos complejos mediante los botones presionables</span><span class="sxs-lookup"><span data-stu-id="d371a-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="d371a-114">Usar la física y la fuerza de los cuerpos rígidos</span><span class="sxs-lookup"><span data-stu-id="d371a-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="d371a-115">Explorar el uso de la información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="d371a-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="d371a-116">Información general sobre los elementos del módulo lunar</span><span class="sxs-lookup"><span data-stu-id="d371a-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="d371a-117">En esta sección, creará un desafío de ensamblado de elemento simple en el que el objetivo del usuario es colocar cinco partes que se distribuyen en la tabla en la ubicación correcta en el módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="d371a-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="d371a-118">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="d371a-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d371a-119">Agregar el selector de Rocket recurso prefabricado a la escena</span><span class="sxs-lookup"><span data-stu-id="d371a-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="d371a-120">Habilitar la manipulación de objetos para todos los elementos</span><span class="sxs-lookup"><span data-stu-id="d371a-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="d371a-121">Agregar y configurar el componente de demostración (Script) del ensamblado de elementos</span><span class="sxs-lookup"><span data-stu-id="d371a-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="d371a-122">El componente de demostración del ensamblado de elementos (Script) no forma parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d371a-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="d371a-123">Se proporcionó con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="d371a-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="d371a-124">1. agregar el selector de Rocket recurso prefabricado a la escena</span><span class="sxs-lookup"><span data-stu-id="d371a-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="d371a-125">En la ventana de proyecto, navegue a los **recursos** > **MRTK. Tutoriales. GettingStarted** > **Prefabs** > carpeta **RocketLauncher** , arrastre **RocketLauncher** recurso prefabricado a la ventana jerarquía para agregarlo a la escena y, a continuación, colóquelo en una ubicación adecuada, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d371a-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="d371a-126">Posición de transformación X = 1,5, Y =-0,4, Z = 0, por lo que se coloca a la derecha del usuario en Waist height</span><span class="sxs-lookup"><span data-stu-id="d371a-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="d371a-127">Transformación de giro X = 0, Y = 180, Z = 0, por lo que las características principales de la experiencia enfrentan al usuario</span><span class="sxs-lookup"><span data-stu-id="d371a-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="d371a-129">2. habilitar la manipulación de objetos para todos los elementos</span><span class="sxs-lookup"><span data-stu-id="d371a-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="d371a-130">En la ventana de jerarquía, busque el objeto RocketLauncher > **LunarModuleParts** y seleccione todos los **objetos secundarios**, agregue el componente de **controlador de manipulación (Script)** y el componente de **captura de interacción cercana (Script)** y, a continuación, configure el controlador de manipulación (Script) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d371a-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="d371a-131">Desactive la casilla **permitir la manipulación lejana** para permitir solo la interacción aproximada</span><span class="sxs-lookup"><span data-stu-id="d371a-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="d371a-132">Cambiar el **tipo de manipulación bidireccionales** para **pasar el giro** de modo que el escalado esté deshabilitado</span><span class="sxs-lookup"><span data-stu-id="d371a-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="d371a-134">Para obtener un recordatorio con instrucciones paso a paso sobre cómo implementar la manipulación de objetos, puede consultar las instrucciones de [manipulación de objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects) .</span><span class="sxs-lookup"><span data-stu-id="d371a-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="d371a-135">3. agregar y configurar el componente de demostración (Script) del ensamblado de elementos</span><span class="sxs-lookup"><span data-stu-id="d371a-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="d371a-136">Con todos los objetos secundarios de LunarModuleParts todavía seleccionados, agregue un componente de **origen de audio** y, a continuación, configúrelo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d371a-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="d371a-137">Asigne un clip de audio adecuado al campo **AudioClip** , por ejemplo, MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="d371a-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="d371a-138">Desactive la casilla **reproducir en activo** , de modo que el clip de audio no se reproduzca automáticamente cuando se cargue la escena.</span><span class="sxs-lookup"><span data-stu-id="d371a-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="d371a-139">Cambiar la **mezcla espacial** a 1 para habilitar el audio espacial</span><span class="sxs-lookup"><span data-stu-id="d371a-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="d371a-141">Con todos los objetos secundarios LunarModuleParts todavía seleccionados, agregue el componente **Demo (Script) del ensamblado de elementos** :</span><span class="sxs-lookup"><span data-stu-id="d371a-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="d371a-143">En la ventana jerarquía, seleccione el objeto **RoverEnclosure** y configure su componente **Demo (Script) de ensamblado de elementos** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="d371a-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="d371a-144">En el campo **objeto que se va a colocar** , asigne **el objeto en este caso, el**objeto RoverEnclosure</span><span class="sxs-lookup"><span data-stu-id="d371a-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="d371a-145">En el campo **Ubicación para colocar** , asigne el objeto **PlacementHints** correspondiente, en este caso, el objeto RoverEnclosure_PlacementHint</span><span class="sxs-lookup"><span data-stu-id="d371a-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="d371a-146">En el campo **objeto de información sobre herramientas** , asigne la **información sobre herramientas**correspondiente, en este caso, el objeto RoverEnclosure_ToolTip</span><span class="sxs-lookup"><span data-stu-id="d371a-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="d371a-147">En el campo **origen de audio** , asigne el **propio**objeto, en este caso, el objeto RoverEnclosure</span><span class="sxs-lookup"><span data-stu-id="d371a-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="d371a-149">**Repita el procedimiento** para cada uno de los demás objetos secundarios LunarModuleParts, es decir, Fueltank, EnergyCell, DockingPortal y ExternalSensor.</span><span class="sxs-lookup"><span data-stu-id="d371a-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="d371a-150">Si ahora entra en el modo de juego y mueve un "objeto que se va a colocar" cerca de su correspondiente "ubicación para colocar", observará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d371a-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="d371a-151">El objeto se ajustará en su lugar y será primario en el objeto LunarModule para que se convierta en parte del módulo lunar.</span><span class="sxs-lookup"><span data-stu-id="d371a-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="d371a-152">El origen de audio del objeto reproducirá el clip de audio asignado en la ubicación del objeto.</span><span class="sxs-lookup"><span data-stu-id="d371a-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="d371a-153">Se ocultará el objeto de información sobre herramientas correspondiente</span><span class="sxs-lookup"><span data-stu-id="d371a-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="d371a-155">Para obtener un recordatorio sobre cómo usar la simulación de entrada en el editor, puede consultar el [uso de la simulación de entrada de la mano del editor para probar una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guía de escenas en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="d371a-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="d371a-156">Configuración del módulo lunar</span><span class="sxs-lookup"><span data-stu-id="d371a-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="d371a-157">En esta sección, agregará características adicionales a la aplicación Rocket Launcher para que el usuario pueda:</span><span class="sxs-lookup"><span data-stu-id="d371a-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="d371a-158">Interacción con el módulo lunar</span><span class="sxs-lookup"><span data-stu-id="d371a-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="d371a-159">Iniciar el módulo lunar en el espacio y reproducir un sonido cuando se inicie</span><span class="sxs-lookup"><span data-stu-id="d371a-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="d371a-160">Restablecer la aplicación para que el módulo lunar y todas las partes se vuelvan a colocar en su posición original</span><span class="sxs-lookup"><span data-stu-id="d371a-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="d371a-161">Oculte las sugerencias de selección de ubicación para dificultar el desafío del ensamblado de elementos.</span><span class="sxs-lookup"><span data-stu-id="d371a-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="d371a-162">Los principales pasos que se deben seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="d371a-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d371a-163">Habilitar la manipulación de objetos</span><span class="sxs-lookup"><span data-stu-id="d371a-163">Enable object manipulation</span></span>
2. <span data-ttu-id="d371a-164">Habilitar física</span><span class="sxs-lookup"><span data-stu-id="d371a-164">Enable physics</span></span>
3. <span data-ttu-id="d371a-165">Agregar un componente de origen de audio</span><span class="sxs-lookup"><span data-stu-id="d371a-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="d371a-166">Agregar y configurar el componente de módulo lunar de inicio (Script)</span><span class="sxs-lookup"><span data-stu-id="d371a-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="d371a-167">Agregar y configurar el componente de alternar sugerencias de colocación (Script)</span><span class="sxs-lookup"><span data-stu-id="d371a-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="d371a-168">El componente módulo lunar de inicio (Script) y el componente sugerencias de selección de ubicación de alternancia (Script) no forman parte de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d371a-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="d371a-169">Se proporcionaron con los recursos de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="d371a-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="d371a-170">1. habilitar la manipulación de objetos</span><span class="sxs-lookup"><span data-stu-id="d371a-170">1. Enable object manipulation</span></span>

<span data-ttu-id="d371a-171">En la ventana jerarquía, seleccione el objeto RocketLauncher > **LunarModule** , agregue el componente de **controlador de manipulación (Script)** y el componente de **captura de interacción cercana (Script)** y, a continuación, configure el controlador de manipulación (Script) como sigue:</span><span class="sxs-lookup"><span data-stu-id="d371a-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="d371a-172">Desactive la casilla **permitir la manipulación lejana** para permitir solo la interacción aproximada</span><span class="sxs-lookup"><span data-stu-id="d371a-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="d371a-173">Cambiar el **tipo de manipulación bidireccionales** para pasar el giro de modo que el escalado esté deshabilitado</span><span class="sxs-lookup"><span data-stu-id="d371a-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="d371a-175">2. habilitar la física</span><span class="sxs-lookup"><span data-stu-id="d371a-175">2. Enable physics</span></span>

<span data-ttu-id="d371a-176">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue un componente **cuerpo rígido** y, a continuación, configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d371a-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="d371a-177">Desactive la casilla **usar gravedad** para que el módulo lunar no se vea afectado por la gravedad</span><span class="sxs-lookup"><span data-stu-id="d371a-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="d371a-178">Active la casilla **es cinemático** para que el módulo lunar inicialmente no se vea afectado por las fuerzas preparadas.</span><span class="sxs-lookup"><span data-stu-id="d371a-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="d371a-180">3. agregar un componente de origen de audio</span><span class="sxs-lookup"><span data-stu-id="d371a-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="d371a-181">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue un componente de **origen de audio** y, a continuación, configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d371a-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="d371a-182">Cambiar la **mezcla espacial** a 1 para habilitar el audio espacial</span><span class="sxs-lookup"><span data-stu-id="d371a-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="d371a-184">4. agregar y configurar el componente de módulo lunar de inicio (Script)</span><span class="sxs-lookup"><span data-stu-id="d371a-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="d371a-185">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue el componente **iniciar el módulo lunar (Script)** y, a continuación, configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d371a-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="d371a-186">Cambiar el valor de **empuje** para que el módulo lunar se vuele correctamente cuando se inicie, por ejemplo, en 0,01</span><span class="sxs-lookup"><span data-stu-id="d371a-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="d371a-188">5. agregar y configurar el componente sugerencias de colocación de alternancia (Script)</span><span class="sxs-lookup"><span data-stu-id="d371a-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="d371a-189">Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue el componente **sugerencias de colocación de alternancia (Script)** y, a continuación, configúrelo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="d371a-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="d371a-190">Establezca la propiedad **tamaño** de la matriz de objetos de juego en 5.</span><span class="sxs-lookup"><span data-stu-id="d371a-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="d371a-191">Asigne cada uno de los **objetos secundarios** del objeto RocketLauncher > LunarModule > **PlacementHints** al campo un **elemento** de la matriz de objetos de juego:</span><span class="sxs-lookup"><span data-stu-id="d371a-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="d371a-193">Configuración del botón Launch</span><span class="sxs-lookup"><span data-stu-id="d371a-193">Configuring the Launch button</span></span>

<span data-ttu-id="d371a-194">En la ventana jerarquía, seleccione los botones de RocketLauncher > > objeto **LaunchButton** y, a continuación, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón pressed ()** , configure el objeto **LunarModule** para recibir el evento y defina **LaunchLunarModule. StartThruster** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="d371a-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="d371a-196">Para obtener un recordatorio sobre cómo implementar eventos, puede consultar las instrucciones de [gestos de seguimiento de mano e](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) interactivos.</span><span class="sxs-lookup"><span data-stu-id="d371a-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="d371a-197">Con los botones de > RocketLauncher > objeto **LaunchButton** todavía seleccionado, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón ()** , configure el objeto **LunarModule** para recibir el evento, defina **AudioSource. PlayOneShot** como la acción que se va a desencadenar y asigne un clip de audio adecuado al campo **clip** de audio, por ejemplo, el clip de audio MRTK_Gem:</span><span class="sxs-lookup"><span data-stu-id="d371a-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="d371a-199">Con los botones de > RocketLauncher > objeto **LaunchButton** todavía seleccionado, en el componente de **botón (Script)** que se puede presionar, cree un nuevo evento **Touch end ()** , configure el objeto **LunarModule** para recibir el evento y defina **LaunchLunarModule. StopThruster** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="d371a-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="d371a-201">Si ahora entra en el modo de juego y presiona el botón Launch (iniciar), oirá el recorte de audio y, si mantiene presionado el botón Launch (iniciar) durante aproximadamente un segundo o más, verá el lanzamiento del módulo lunar en el espacio:</span><span class="sxs-lookup"><span data-stu-id="d371a-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="d371a-203">Configuración del botón restablecer</span><span class="sxs-lookup"><span data-stu-id="d371a-203">Configuring the Reset button</span></span>

<span data-ttu-id="d371a-204">En la ventana jerarquía, seleccione los botones de RocketLauncher > > objeto **ResetButton** y, a continuación, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón pressed ()** , configure el objeto **LunarModule** para recibir el evento y defina **LaunchLunarModule. ResetModule** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="d371a-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="d371a-206">Con los botones de > RocketLauncher > objeto **ResetButton** todavía seleccionado, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón ()** , configure el objeto **RocketLauncher** para recibir el evento, defina **GameObject. BroadcastMessage** como la acción que se va a desencadenar y escriba **ResetPlacement** en el campo de mensaje:</span><span class="sxs-lookup"><span data-stu-id="d371a-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="d371a-208">La acción GameObject. BroadcastMessage envía el mensaje ResetPlacement desde el objeto RocketLauncher a todos sus objetos secundarios.</span><span class="sxs-lookup"><span data-stu-id="d371a-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="d371a-209">Cualquier objeto secundario que tenga la función ResetPlacement, que se define en el componente de demostración (Script) del ensamblado de elementos que ha agregado a todos los objetos secundarios LunarModuleParts, invocará a la función ResetPlacement que restablece la posición del objeto secundario.</span><span class="sxs-lookup"><span data-stu-id="d371a-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="d371a-210">Si ahora entra en el modo de juego, mueve algunas partes o inicia el módulo lunar y, a continuación, presiona el botón de restablecimiento, verá que las partes y/o el módulo lunar se restablecen a su posición original:</span><span class="sxs-lookup"><span data-stu-id="d371a-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="d371a-212">Configuración del botón sugerencias de selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="d371a-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="d371a-213">En la ventana jerarquía, seleccione los botones de RocketLauncher > > objeto **HintsButton** y, a continuación, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón pressed ()** , configure el objeto **LunarModule** para recibir el evento y defina **TogglePlacementHints. ToggleGameObjects** como la acción que se va a desencadenar:</span><span class="sxs-lookup"><span data-stu-id="d371a-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="d371a-215">Si ahora entra en el modo de juego, observará que las sugerencias de colocación translúcida están deshabilitadas de forma predeterminada, pero que puede activarlas y desactivarlas si presiona el botón sugerencias:</span><span class="sxs-lookup"><span data-stu-id="d371a-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="d371a-217">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="d371a-217">Congratulations</span></span>

<span data-ttu-id="d371a-218">Ha configurado completamente esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="d371a-218">You have fully configured this application.</span></span> <span data-ttu-id="d371a-219">Ahora, la aplicación permite a los usuarios ensamblar completamente el módulo lunar, iniciar el módulo lunar, alternar sugerencias y restablecer la aplicación para que se inicie de nuevo.</span><span class="sxs-lookup"><span data-stu-id="d371a-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
