---
title: 5. Adición de un botón y restablecimiento de la ubicación de las piezas
description: Parte 5 de un tutorial para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit.
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 77fe2b59db970a2ac4b531d69efec6794478f7d5
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519997"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="ad9bb-104">5. Adición de un botón y restablecimiento de la ubicación de las piezas</span><span class="sxs-lookup"><span data-stu-id="ad9bb-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="ad9bb-105">En esta sección se siguen mostrando las funcionalidades del complemento UX Tools de Mixed Reality Toolkit y se siguen compilando las características de la aplicación de ajedrez.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-105">This section continues demonstrating the capabilities of the Mixed Reality Toolkit UX Tools plugin and building out the features of your chess app.</span></span> <span data-ttu-id="ad9bb-106">Crearás una nueva función y aprenderás a obtener referencias a actores de tu nivel en un plano técnico.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-106">You’ll create a new function and learn how to get references to Actors from your Level into a Blueprint.</span></span>

## <a name="objectives"></a><span data-ttu-id="ad9bb-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ad9bb-107">Objectives</span></span>

* <span data-ttu-id="ad9bb-108">Agregar un botón al proyecto</span><span class="sxs-lookup"><span data-stu-id="ad9bb-108">Add a button to your project</span></span>
* <span data-ttu-id="ad9bb-109">Crear una nueva función “Reset Location” (Restablecer ubicación) que envíe un elemento de vuelta a su ubicación original</span><span class="sxs-lookup"><span data-stu-id="ad9bb-109">Create a new “Reset Location” function that sends a piece back to its original location</span></span>
* <span data-ttu-id="ad9bb-110">Configurar el botón para que desencadene la función recién creada cuando se presione</span><span class="sxs-lookup"><span data-stu-id="ad9bb-110">Hook the button up to trigger the newly created function when pressed</span></span>

## <a name="create-a-function-to-reset-location"></a><span data-ttu-id="ad9bb-111">Crear una función para restablecer la ubicación</span><span class="sxs-lookup"><span data-stu-id="ad9bb-111">Create a function to reset location</span></span>

1.  <span data-ttu-id="ad9bb-112">Abre **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-112">Open **WhiteKing**.</span></span> <span data-ttu-id="ad9bb-113">En el panel **My Blueprint** (Mi plano técnico), haz clic en el botón "+" situado junto a la sección **Functions** (Funciones) para crear una nueva función.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-113">In the **My Blueprint** panel, click the “+” button next to the **Functions** section to create a new function.</span></span> <span data-ttu-id="ad9bb-114">Asigna a esta función el nombre "Reset Location" (Restablecer ubicación).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-114">Name this function “Reset Location”.</span></span> 

2.  <span data-ttu-id="ad9bb-115">En el plano técnico **Reset Location** (Restablecer ubicación) que acabas de crear, arrastra la marca de ejecución y suéltala en cualquier punto de la cuadrícula de Blueprint para llamar a un nodo **SetActorRelativeTransform**.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-115">In your newly created **Reset Location** Blueprint, drag the execution pin and release anywhere on the Blueprint grid to call a **SetActorRelativeTransform** node.</span></span> <span data-ttu-id="ad9bb-116">Esta función define la transformación (ubicación, rotación y escala) de un actor en relación con su elemento principal.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="ad9bb-117">Usaremos esta función para restablecer la posición del rey en el tablero, incluso si la posición original del tablero ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-117">We’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> <span data-ttu-id="ad9bb-118">Crea un nodo **Make Transform** (Crear transformación) con la ubicación X = -26, Y = 4, Z = 0 y conéctalo a la entrada New Relative Transform (Nueva transformación relativa).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-118">Create a **Make Transform** node with Location X = -26, Y = 4, Z = 0, and connect it to the New Relative Transform input.</span></span> 

![Función Reset Location (Restablecer ubicación)](images/unreal-uxt/5-function.PNG)

3.  <span data-ttu-id="ad9bb-120">Compila y guarda **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-120">Compile and Save **WhiteKing**.</span></span> <span data-ttu-id="ad9bb-121">Vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-121">Return to the Main window.</span></span> 

## <a name="add-a-button"></a><span data-ttu-id="ad9bb-122">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="ad9bb-122">Add a button</span></span>

1.  <span data-ttu-id="ad9bb-123">En la carpeta **Blueprints**, crea un nuevo plano técnico como subclase de SimpleButton.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-123">In your **Blueprints** folder, create a new Blueprint that subclasses SimpleButton.</span></span> <span data-ttu-id="ad9bb-124">SimpleButton es un actor de plano técnico de botón 3D que se proporciona como parte del complemento UX Tools.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-124">SimpleButton is a 3D button Blueprint Actor that is provided as part of the UX Tools plugin.</span></span> <span data-ttu-id="ad9bb-125">Asigna a este botón el nombre "ResetButton" y haz doble clic para abrir el plano técnico.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-125">Name this button “ResetButton” and double click to open the Blueprint.</span></span> 

![Subclase del nuevo plano técnico de SimpleButton](images/unreal-uxt/5-subclass.PNG)

2.  <span data-ttu-id="ad9bb-127">En el panel **Components** (Componentes), haz clic en **PressableButton (Inherited)** .</span><span class="sxs-lookup"><span data-stu-id="ad9bb-127">In the **Components** panel, click on **PressableButton (Inherited)**.</span></span> <span data-ttu-id="ad9bb-128">En el panel de detalles, desplázate hasta la sección **Eventos**.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-128">In the Details panel, scroll until you see the **Events** section.</span></span> <span data-ttu-id="ad9bb-129">Haz clic en el botón verde con el signo más junto a **On Button Pressed** (Al presionar un botón). Esto agregará un nuevo evento **On Button Pressed** (Al presionar un botón) al gráfico de eventos, que se invocará cuando se presione el botón.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-129">Click the green plus button next to **On Button Pressed**- this will add an **On Button Pressed** event to the Event Graph, which will be called when the button is pressed.</span></span> <span data-ttu-id="ad9bb-130">Desde aquí, llamaremos a la función Reset Location (Restablecer ubicación) de WhiteKing.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-130">From here, we’ll want to call our WhiteKing’s Reset Location function.</span></span> <span data-ttu-id="ad9bb-131">Para ello, primero necesitamos obtener una referencia al actor de WhiteKing de nuestro nivel.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-131">To do this, we’ll first need to get a reference to the WhiteKing Actor in our Level.</span></span> 

3.  <span data-ttu-id="ad9bb-132">En el panel **My Blueprint**, busca la sección **Variables** y haz clic en el botón **+** para agregar una nueva variable.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-132">In the **My Blueprint** panel, find the **Variables** section and click the **+** button to add a new variable.</span></span> <span data-ttu-id="ad9bb-133">Asigna a esta variable el nombre "WhiteKing".</span><span class="sxs-lookup"><span data-stu-id="ad9bb-133">Name this variable “WhiteKing”.</span></span> <span data-ttu-id="ad9bb-134">En el panel de detalles, selecciona la lista desplegable situada junto a **Variable Type** (Tipo de variable), busca "WhiteKing" y selecciona **Object Reference** (Referencia de objetos).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-134">In the Details panel, select the dropdown next to **Variable Type**, search for “WhiteKing”, and select the **Object Reference**.</span></span> <span data-ttu-id="ad9bb-135">Por último, activa la casilla situada junto a **Instance Editable** (Instance editable).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-135">Finally, check the box next to **Instance Editable**.</span></span> <span data-ttu-id="ad9bb-136">Esto permitirá que la variable se defina desde el nivel principal.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-136">This will allow the variable to be set from the Main Level.</span></span> 

![Crear una variable](images/unreal-uxt/5-var.PNG)

4.  <span data-ttu-id="ad9bb-138">Arrastra la variable de WhiteKing desde **My Blueprint > Variables** (Mi plano técnico > Variables) hasta el gráfico de eventos de botón de restablecimiento.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-138">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph.</span></span> <span data-ttu-id="ad9bb-139">Elige **Get WhiteKing** (Obtener WhiteKing).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-139">Choose **Get WhiteKing**.</span></span> 

5.  <span data-ttu-id="ad9bb-140">Arrastra la marca de salida de WhiteKing y suéltala para colocar un nodo nuevo.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-140">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="ad9bb-141">Selecciona la función**Reset Location** (Restaurar ubicación).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-141">Select the **Reset Location** function.</span></span> <span data-ttu-id="ad9bb-142">Por último, arrastra la marca de ejecución de salida de **On Button Pressed** (Al presionar un botón) a la marca de ejecución de entrada de **Reset Location** (Restablecer ubicación).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-142">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="ad9bb-143">**Compila** y **guarda** el plano técnico ResetButton y, a continuación, vuelve a la ventana principal.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-143">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![Llamar a la función Reset Location (Restablecer ubicación) desde On Button Pressed (Al presionar un botón)](images/unreal-uxt/5-callresetloc.PNG)

6.  <span data-ttu-id="ad9bb-145">Arrastra **ResetButton** a la ventanilla y establece su ubicación en X = 50, Y =-25, Z = 10.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-145">Drag **ResetButton** into the viewport and set its location to X = 50, Y = -25, Z = 10.</span></span> <span data-ttu-id="ad9bb-146">En **Default** (Predeterminada), establece el valor de la variable WhiteKing en **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-146">Under **Default**, set the value of the WhiteKing variable to **WhiteKing**.</span></span>

![Definir la variable](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="ad9bb-148">Ahora tienes una aplicación de realidad mixta con un tablero y una pieza de ajedrez manipulables, así como un botón totalmente funcional que restablecerá la ubicación de la pieza cuando se presione.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-148">You now have a mixed reality app with a grabbable chess piece and board, as well as a fully functioning button that will reset the piece’s location when pressed.</span></span> <span data-ttu-id="ad9bb-149">La aplicación completada hasta este momento se puede encontrar en [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span><span class="sxs-lookup"><span data-stu-id="ad9bb-149">The completed app up to this point can be found on [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp).</span></span> <span data-ttu-id="ad9bb-150">No dudes en profundizar más allá de este tutorial y configurar el resto de las piezas de ajedrez de modo que se restablezca todo el tablero cuando el usuario presione el botón.</span><span class="sxs-lookup"><span data-stu-id="ad9bb-150">Feel free to go beyond this tutorial and set up the remainder of the chess pieces, so that the entire board is reset when the user presses the button.</span></span>

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

[<span data-ttu-id="ad9bb-152">Sección siguiente: 6. Empaquetado y implementación en el dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="ad9bb-152">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)