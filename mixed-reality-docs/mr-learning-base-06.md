---
title: 'Tutoriales de introducción: 6. Creación de interfaces de usuario'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a7c4ea140a9c27f1a92680da6bbe1fb3a4bdc233
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306251"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="23074-105">6. Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="23074-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="23074-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="23074-106">Overview</span></span>

<span data-ttu-id="23074-107">En este tutorial, obtendrá información sobre cómo crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú de MRTK junto con el componente TextMeshPro de Unity.</span><span class="sxs-lookup"><span data-stu-id="23074-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="23074-108">También aprenderá a configurar los botones para desencadenar eventos y agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar a los usuarios información adicional.</span><span class="sxs-lookup"><span data-stu-id="23074-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="23074-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="23074-109">Objectives</span></span>

* <span data-ttu-id="23074-110">Aprender a organizar los botones de una colección</span><span class="sxs-lookup"><span data-stu-id="23074-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="23074-111">Aprender a usar los elementos prefabricados de menú de MRTK</span><span class="sxs-lookup"><span data-stu-id="23074-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="23074-112">Aprender a interactuar con hologramas mediante botones y elementos de la interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="23074-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="23074-113">Aprender a agregar elementos de texto</span><span class="sxs-lookup"><span data-stu-id="23074-113">Learn how to add text elements</span></span>
* <span data-ttu-id="23074-114">Aprender a generar información sobre herramientas en objetos dinámicamente</span><span class="sxs-lookup"><span data-stu-id="23074-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="23074-115">Creación de un panel estático de botones</span><span class="sxs-lookup"><span data-stu-id="23074-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="23074-116">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** ( Crear vacío)para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **Buttons** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="23074-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="23074-117">**Posición**: X = 0.6, Y = 0.036, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="23074-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="23074-118">**Rotación**: X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="23074-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="23074-119">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="23074-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="23074-121">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, haga clic y arrastre el elemento prefabricado **PressableRoundButton** sobre el objeto **Buttons** y, a continuación, haga clic con el botón derecho en PressableRoundButton, seleccione **Duplicate** (Duplicar) para crear una copia y repita el proceso hasta que tenga un total de tres objetos PressableRoundButton:</span><span class="sxs-lookup"><span data-stu-id="23074-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="23074-123">En la ventana Hierarchy (Jerarquía), seleccione el objeto **Buttons** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **GridObjectCollection** y configúrelo del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="23074-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="23074-124">**Tipo de orden**: Orden secundario</span><span class="sxs-lookup"><span data-stu-id="23074-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="23074-125">**Diseño**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="23074-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="23074-126">**Ancho de celda**: 0.2</span><span class="sxs-lookup"><span data-stu-id="23074-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="23074-127">**Ancla**: Centro a la izquierda</span><span class="sxs-lookup"><span data-stu-id="23074-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="23074-128">A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios del objeto Buttons:</span><span class="sxs-lookup"><span data-stu-id="23074-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="23074-130">En la ventana Hierarchy (Jerarquía), asigne el nombre **Hints**, **Explode** y **Reset** a los botones.</span><span class="sxs-lookup"><span data-stu-id="23074-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="23074-131">Para cada botón, seleccione el objeto secundario **SeeItSayItLabel** > **TextMeshPro** y, a continuación, en la ventana Inspector, cambie el texto del componente **TextMeshPro - Text** respectivo para que coincida con los nombres de los botones:</span><span class="sxs-lookup"><span data-stu-id="23074-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="23074-133">Una vez hecho esto, contraiga los objetos secundarios del objeto Buttons.</span><span class="sxs-lookup"><span data-stu-id="23074-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="23074-134">En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Hints** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="23074-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="23074-135">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="23074-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="23074-136">En la lista desplegable **No function** (Ninguna función), seleccione **PlacementHintsController** > **TogglePlacementHints ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="23074-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="23074-138">En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Explode** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="23074-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="23074-139">Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="23074-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="23074-140">En la lista desplegable **No function** (Ninguna función), seleccione **ExplodedViewController** > **ToggleExplodedView ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="23074-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="23074-142">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionada la barra espaciadora para activar la mano y use el mouse para presionar el botón **Hints** para activar y desactivar la visibilidad de los objetos de sugerencia de colocación:</span><span class="sxs-lookup"><span data-stu-id="23074-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="23074-144">y el botón **Explode** para activar y desactivar la vista seccionada:</span><span class="sxs-lookup"><span data-stu-id="23074-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="23074-146">Creación de un menú dinámico que sigue al usuario</span><span class="sxs-lookup"><span data-stu-id="23074-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="23074-147">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus**, haga clic y arrastre el elemento prefabricado **NearMenu4x1** en la ventana Hierarchy (Jerarquía), establezca su **posición** de transformación en X = 0, Y = -0.4, Z = 0 y configúrelo de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="23074-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="23074-148">Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Head** (Cabeza).</span><span class="sxs-lookup"><span data-stu-id="23074-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="23074-149">Marque la casilla junto al componente **RadialView** del solucionador para que esté habilitado de forma predeterminada</span><span class="sxs-lookup"><span data-stu-id="23074-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="23074-151">En la ventana Hierarchy (Jerarquía), cambie el nombre del objeto a **Menu** y, a continuación, expanda el objeto secundario **ButtonCollection** para mostrar los cuatro botones:</span><span class="sxs-lookup"><span data-stu-id="23074-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="23074-153">Cambie el nombre del primer botón por **Indicator** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="23074-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="23074-154">Cambie el**texto de la etiqueta principal** para que coincida con el nombre del botón.</span><span class="sxs-lookup"><span data-stu-id="23074-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="23074-155">Asigne el objeto **Indicator** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="23074-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="23074-156">En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="23074-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="23074-157">Compruebe que la casilla del argumento esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="23074-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="23074-158">Cambie el **icono** al icono de "búsqueda".</span><span class="sxs-lookup"><span data-stu-id="23074-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="23074-160">En la ventana Hierarchy (Jerarquía), seleccione el objeto **Indicator** y, a continuación, en la ventana Inspector, desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada:</span><span class="sxs-lookup"><span data-stu-id="23074-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window, uncheck the checkbox next to its name to make it inactive by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="23074-162">Ahora, cuando se inicia la aplicación, el objeto Indicator está deshabilitado de forma predeterminada y se puede habilitar presionando el botón Indicator.</span><span class="sxs-lookup"><span data-stu-id="23074-162">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="23074-163">Cambie el nombre del segundo botón por **TapToPlace** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="23074-163">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="23074-164">Cambie el**texto de la etiqueta principal** para que coincida con el nombre del botón.</span><span class="sxs-lookup"><span data-stu-id="23074-164">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="23074-165">Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="23074-165">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="23074-166">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="23074-166">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="23074-167">Compruebe que la casilla del argumento esté **activada**.</span><span class="sxs-lookup"><span data-stu-id="23074-167">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="23074-168">Cambie el **icono** al icono de "mano con rayo".</span><span class="sxs-lookup"><span data-stu-id="23074-168">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="23074-170">En la ventana Jerarquía, seleccione el objeto **RoverAssembly** y, a continuación, en la ventana Inspector, configure el componente **Tap To Place (Script)** (Pulsar para colocar [Script]) del modo siguiente:</span><span class="sxs-lookup"><span data-stu-id="23074-170">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="23074-171">Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="23074-171">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="23074-172">En la sección del evento **On Placing Started ()** , haga clic en el icono **+** para agregar un nuevo evento:</span><span class="sxs-lookup"><span data-stu-id="23074-172">In the **On Placing Started ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="23074-173">Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).</span><span class="sxs-lookup"><span data-stu-id="23074-173">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="23074-174">En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.</span><span class="sxs-lookup"><span data-stu-id="23074-174">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="23074-175">Compruebe que la casilla del argumento esté **desactivada**.</span><span class="sxs-lookup"><span data-stu-id="23074-175">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="23074-177">Ahora, cuando se inicia la aplicación, la funcionalidad Tap to Place (Tocar para colocar) está deshabilitada de forma predeterminada y se puede habilitar presionando el botón Tap to Place.</span><span class="sxs-lookup"><span data-stu-id="23074-177">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="23074-178">Además, cuando se complete la acción de tocar para colocar, se deshabilitará.</span><span class="sxs-lookup"><span data-stu-id="23074-178">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="23074-179">Agregación de texto a la escena</span><span class="sxs-lookup"><span data-stu-id="23074-179">Adding text to the scene</span></span>

<span data-ttu-id="23074-180">En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Table** (Tabla) y seleccione **3D Object** > **Text - TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para agregar un objeto de texto como elemento secundario del objeto Table y, a continuación, en la ventana Inspector, configure el componente **Rect Transform** (Transformación rectangular) como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="23074-180">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="23074-181">Cambie **Pos Y** (Posición Y) a 1.</span><span class="sxs-lookup"><span data-stu-id="23074-181">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="23074-182">Cambie **Width** (Ancho) a 1.</span><span class="sxs-lookup"><span data-stu-id="23074-182">Change **Width** to 1</span></span>
* <span data-ttu-id="23074-183">Cambie **Height** (Altura) a 1.</span><span class="sxs-lookup"><span data-stu-id="23074-183">Change **Height** to 1</span></span>
* <span data-ttu-id="23074-184">Cambie **Rotation X** (Rotación X) a 90.</span><span class="sxs-lookup"><span data-stu-id="23074-184">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="23074-186">A continuación, configure el componente **TextMeshPro - Text** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="23074-186">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="23074-187">Cambie **Text** (Texto) a Rover Explorer.</span><span class="sxs-lookup"><span data-stu-id="23074-187">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="23074-188">Cambie **Font Style** (Estilo de fuente) a Bold (Negrita).</span><span class="sxs-lookup"><span data-stu-id="23074-188">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="23074-189">Cambie **Font Size** (Tamaño de fuente) a 1.</span><span class="sxs-lookup"><span data-stu-id="23074-189">Change **Font Size** to 1</span></span>
* <span data-ttu-id="23074-190">Cambie Extra Settings > **Margins** (Configuración adicional > Márgenes) a 0.03.</span><span class="sxs-lookup"><span data-stu-id="23074-190">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="23074-192">Agregación de información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="23074-192">Adding tooltips</span></span>

<span data-ttu-id="23074-193">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** para buscar los objetos prefabricados de información sobre herramientas:</span><span class="sxs-lookup"><span data-stu-id="23074-193">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="23074-195">En la ventana Hierarchy (Jerarquía), expanda el objeto RoverExplorer > **RoverParts** y seleccione todos los objetos secundarios de partes, y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **ToolTipSpawner** y configúrelo de la forma siguiente:</span><span class="sxs-lookup"><span data-stu-id="23074-195">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="23074-196">Asegúrese de que la casilla de verificación **Focus enabled** (Enfoque habilitado) está activada para requerir que el usuario mire la parte para que aparezca la información sobre herramientas.</span><span class="sxs-lookup"><span data-stu-id="23074-196">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="23074-197">Asigne el elemento prefabricado **Simple Line ToolTip** (Información sobre herramientas de línea simple) desde la ventana Project (Proyecto) al campo **Tool Tip Prefab** (Elemento prefabricado de información de herramientas).</span><span class="sxs-lookup"><span data-stu-id="23074-197">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="23074-198">Cambie ToolTip Override Settings > **Settings Mode** (Configuración de invalidación de información sobre herramientas > Modo de configuración) a **Override** (Invalidar).</span><span class="sxs-lookup"><span data-stu-id="23074-198">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="23074-199">Cambie ToolTip Override Settings > **Manual Pivot Location Position Y** (Configuración de invalidación de información sobre herramientas > Posición Y de ubicación del pivote manual) a **1.5**.</span><span class="sxs-lookup"><span data-stu-id="23074-199">Change the ToolTip Override Settings > **Manual Pivot Location Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="23074-201">En la ventana Hierarchy (Jerarquía), seleccione la primera parte del rover, RoverParts > **Camera_Part** y configure el componente **ToolTipSpawner** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="23074-201">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="23074-202">Cambie **Tool Tip Text** para reflejar el nombre de la parte; por ejemplo, **Camera**.</span><span class="sxs-lookup"><span data-stu-id="23074-202">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="23074-204">**Repita** este paso para cada uno de los objetos de parte del rover para configurar el componente **ToolTipSpawner** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="23074-204">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="23074-205">Para **Generator_Part**, cambie **Tool Tip Text** a **Generator**.</span><span class="sxs-lookup"><span data-stu-id="23074-205">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="23074-206">Para **Lights_Part**, cambie **Tool Tip Text** a **Lights**.</span><span class="sxs-lookup"><span data-stu-id="23074-206">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="23074-207">Para **UHFAntenna_Part**, cambie **Tool Tip Text** a **UHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="23074-207">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="23074-208">Para **Spectrometer_Part**, cambie **Tool Tip Text** a **Spectrometer**.</span><span class="sxs-lookup"><span data-stu-id="23074-208">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="23074-209">Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionado el botón derecho del mouse mientras mueve el mouse hasta que la mirada entre en contacto con una de las partes y la información sobre herramientas de la parte se mostrará:</span><span class="sxs-lookup"><span data-stu-id="23074-209">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="23074-211">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="23074-211">Congratulations</span></span>

<span data-ttu-id="23074-212">En este tutorial, aprendió a crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú proporcionados por MRTK junto con el componente TextMeshPro de Unity y a configurar los botones para desencadenar eventos cuando se presionan.</span><span class="sxs-lookup"><span data-stu-id="23074-212">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="23074-213">También ha aprendido a agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar información adicional al usuario.</span><span class="sxs-lookup"><span data-stu-id="23074-213">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="23074-214">Tutorial siguiente: 7. Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="23074-214">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
