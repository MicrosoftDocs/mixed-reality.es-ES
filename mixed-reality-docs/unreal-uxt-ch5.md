---
title: 5. Adición de un botón y restablecimiento de la ubicación de las piezas
description: Parte 5 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 473f47884bbc492451007436f80e8d9762cf1ab7
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720261"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="08dd5-104">5. Adición de un botón y restablecimiento de la ubicación de las piezas</span><span class="sxs-lookup"><span data-stu-id="08dd5-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="08dd5-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="08dd5-105">Overview</span></span>

<span data-ttu-id="08dd5-106">En el tutorial anterior, agregó actores de interacción manual a los componentes Peón y Manipulador en el tablero de ajedrez para que fueran interactivos.</span><span class="sxs-lookup"><span data-stu-id="08dd5-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="08dd5-107">En esta sección, continuará trabajando con el complemento UX Tools de Mixed Reality Toolkit compilando las características de la aplicación de ajedrez.</span><span class="sxs-lookup"><span data-stu-id="08dd5-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="08dd5-108">Esto incluye la creación de una nueva función y el aprendizaje sobre cómo obtener referencias a actores en un plano técnico.</span><span class="sxs-lookup"><span data-stu-id="08dd5-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="08dd5-109">Al final de esta sección, estará listo para empaquetar e implementar la aplicación de realidad mixta en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="08dd5-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="08dd5-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="08dd5-110">Objectives</span></span>

* <span data-ttu-id="08dd5-111">Adición de un botón interactivo</span><span class="sxs-lookup"><span data-stu-id="08dd5-111">Adding an interactive button</span></span>
* <span data-ttu-id="08dd5-112">Creación de una función para restablecer la ubicación de las piezas</span><span class="sxs-lookup"><span data-stu-id="08dd5-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="08dd5-113">Enlace del botón para que desencadene la función cuando se presione</span><span class="sxs-lookup"><span data-stu-id="08dd5-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="08dd5-114">Creación de una función de restablecimiento</span><span class="sxs-lookup"><span data-stu-id="08dd5-114">Creating a reset function</span></span>
<span data-ttu-id="08dd5-115">La primera tarea consiste en crear un plano técnico de función que reestablezca una pieza de ajedrez a su posición original en la escena.</span><span class="sxs-lookup"><span data-stu-id="08dd5-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="08dd5-116">Abra **WhiteKing**, haga clic en el icono **+** situado junto a la sección **Functions** (Funciones) de **My Blueprint** (Mi plano técnico) y asígnele el nombre **Reset Location**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-116">Open **WhiteKing**, click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span> 

2.  <span data-ttu-id="08dd5-117">Arrastre la ejecución desde **Reset Location** y suéltela en la cuadrícula del plano técnico para crear un nodo **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="08dd5-118">Esta función define la transformación (ubicación, rotación y escala) de un actor en relación con su elemento principal.</span><span class="sxs-lookup"><span data-stu-id="08dd5-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="08dd5-119">Usará esta función para restablecer la posición del rey en el tablero, incluso si la posición original del tablero ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="08dd5-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="08dd5-120">Haga clic con el botón derecho en el gráfico de eventos, seleccione **Make Transform** (Realizar transformación) y cambie su **Location** (Ubicación) a **X =-26**, **Y = 4**, **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-120">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="08dd5-121">Conecte su **Return Value** (Valor devuelto) a la marca de **New Relative Transform** (Nueva transformación relativa) en **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span> 

![Función Reset Location (Restablecer ubicación)](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="08dd5-123">**Compile** y **guarde** el proyecto antes de volver a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="08dd5-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="08dd5-124">Agregar un botón</span><span class="sxs-lookup"><span data-stu-id="08dd5-124">Adding a button</span></span>
<span data-ttu-id="08dd5-125">Ahora que la función está configurada correctamente, la siguiente tarea consiste en crear un botón que la desencadene cuando se toque.</span><span class="sxs-lookup"><span data-stu-id="08dd5-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 

1.  <span data-ttu-id="08dd5-126">Haga clic en **Add New > Blueprint Class** (Agregar nuevo > Clase de plano técnico), expanda la sección **All Classes** (Todas las clases) y busque **SimpleButton**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-126">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **SimpleButton**.</span></span> 
    * <span data-ttu-id="08dd5-127">Asigne a este botón el nombre **ResetButton** y haga doble clic para abrir el plano técnico.</span><span class="sxs-lookup"><span data-stu-id="08dd5-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="08dd5-128">**SimpleButton** es un actor de plano técnico de botón 3D que forma parte del complemento UX Tools.</span><span class="sxs-lookup"><span data-stu-id="08dd5-128">**SimpleButton** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span> <span data-ttu-id="08dd5-129">.</span><span class="sxs-lookup"><span data-stu-id="08dd5-129">.</span></span> 

![Subclase del nuevo plano técnico de SimpleButton](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="08dd5-131">Haga clic en **PressableButton (Inherited)** [PressableButton (heredado)] del panel **Components** (Componentes) y desplácese hacia abajo en el panel **Details** (Detalles) hasta la sección **Events** (Eventos).</span><span class="sxs-lookup"><span data-stu-id="08dd5-131">Click **Pressable Button (Inherited)** from the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="08dd5-132">Haga clic en el botón verde **+** situado junto a **On Button Pressed** (Al presionar un botón) para agregar un evento al gráfico de eventos, que se llamará cuando se presione el botón.</span><span class="sxs-lookup"><span data-stu-id="08dd5-132">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="08dd5-133">Desde aquí, llamará a la función **Reset Location** de **WhiteKing**, que necesita una referencia al actor **WhiteKing** en el nivel.</span><span class="sxs-lookup"><span data-stu-id="08dd5-133">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

1.  <span data-ttu-id="08dd5-134">Desplácese hasta la sección **Variables** en el panel **Details** (Detalles), haga clic en el botón **+** y asigne a la variable el nombre **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-134">Scroll to the **Variables** section in the **Details** panel, click the **+** button and name the variable **WhiteKing**.</span></span> 
    * <span data-ttu-id="08dd5-135">Seleccione la lista desplegable situada junto a **Variable Type** (Tipo de variable), busque **WhiteKing** y seleccione **Object Reference** (Referencia de objetos).</span><span class="sxs-lookup"><span data-stu-id="08dd5-135">Select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span> 
    * <span data-ttu-id="08dd5-136">Marque la casilla situada junto a **Instance Editable** (Instance editable).</span><span class="sxs-lookup"><span data-stu-id="08dd5-136">Check the box next to **Instance Editable**.</span></span> <span data-ttu-id="08dd5-137">Esto permitirá que la variable se defina desde el nivel principal.</span><span class="sxs-lookup"><span data-stu-id="08dd5-137">This will allow the variable to be set from the Main Level.</span></span> 

![Crear una variable](images/unreal-uxt/5-var.PNG)

2.  <span data-ttu-id="08dd5-139">Arrastre la variable de WhiteKing desde **My Blueprint > Variables** (Mi plano técnico > Variables) hasta el gráfico de eventos del botón de restablecimiento y elija **Get WhiteKing** (Obtener WhiteKing).</span><span class="sxs-lookup"><span data-stu-id="08dd5-139">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="08dd5-140">Activación de la función</span><span class="sxs-lookup"><span data-stu-id="08dd5-140">Firing the function</span></span>
<span data-ttu-id="08dd5-141">Lo único que queda es activar oficialmente la función de restablecimiento cuando se presiona el botón.</span><span class="sxs-lookup"><span data-stu-id="08dd5-141">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="08dd5-142">Arrastra la marca de salida de WhiteKing y suéltala para colocar un nodo nuevo.</span><span class="sxs-lookup"><span data-stu-id="08dd5-142">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="08dd5-143">Selecciona la función**Reset Location** (Restaurar ubicación).</span><span class="sxs-lookup"><span data-stu-id="08dd5-143">Select the **Reset Location** function.</span></span> <span data-ttu-id="08dd5-144">Por último, arrastra la marca de ejecución de salida de **On Button Pressed** (Al presionar un botón) a la marca de ejecución de entrada de **Reset Location** (Restablecer ubicación).</span><span class="sxs-lookup"><span data-stu-id="08dd5-144">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="08dd5-145">**Compila** y **guarda** el plano técnico ResetButton y, a continuación, vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="08dd5-145">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Llamar a la función Reset Location (Restablecer ubicación) desde On Button Pressed (Al presionar un botón)](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="08dd5-147">Arrastre **ResetButton** a la ventanilla y establezca su ubicación en **X = 50**, **Y =-25** y **Z = 10**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-147">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="08dd5-148">En **Default** (Valor predeterminado), establezca el valor de la variable **WhiteKing** en **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="08dd5-148">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![Definir la variable](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="08dd5-150">Ejecute la aplicación, mueva la pieza de ajedrez a una nueva ubicación y presione el botón grande rosa para ver la lógica de restablecimiento en acción.</span><span class="sxs-lookup"><span data-stu-id="08dd5-150">Run the app, move the chess piece to a new location, and press the big pink button to see the reset logic in action!</span></span>

<span data-ttu-id="08dd5-151">Ahora tiene una aplicación de realidad mixta con un tablero y una pieza de ajedrez con los que puede interactuar, así como un botón totalmente funcional que restablecerá la ubicación de la pieza.</span><span class="sxs-lookup"><span data-stu-id="08dd5-151">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="08dd5-152">Puede encontrar la aplicación completada hasta este momento en su repositorio de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="08dd5-152">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="08dd5-153">No dude en profundizar más allá de este tutorial y configurar el resto de las piezas de ajedrez de modo que se restablezca todo el tablero cuando se presione el botón.</span><span class="sxs-lookup"><span data-stu-id="08dd5-153">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="08dd5-155">Está listo para pasar a la sección final de este tutorial, donde aprenderá a empaquetar e implementar correctamente la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="08dd5-155">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

[<span data-ttu-id="08dd5-156">Sección siguiente: 6. Empaquetado y implementación en el dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="08dd5-156">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
