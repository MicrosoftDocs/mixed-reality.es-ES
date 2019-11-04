---
title: Entrada de teclado en Unity
description: Unity proporciona la clase TouchScreenKeyboard para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: teclado, entrada, Unity, touchscreenkeyboard
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438553"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="f01b2-104">Entrada de teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="f01b2-104">Keyboard input in Unity</span></span>

<span data-ttu-id="f01b2-105">**Espacio de nombres:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="f01b2-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="f01b2-106">**Tipo**:  *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="f01b2-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="f01b2-107">Aunque HoloLens admite muchas formas de entrada, incluidos los teclados Bluetooth, la mayoría de las aplicaciones no puede suponer que todos los usuarios tendrán un teclado físico disponible.</span><span class="sxs-lookup"><span data-stu-id="f01b2-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="f01b2-108">Si la aplicación requiere una entrada de texto, se debe proporcionar alguna forma de teclado en pantalla.</span><span class="sxs-lookup"><span data-stu-id="f01b2-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="f01b2-109">Unity proporciona la clase *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* para aceptar la entrada de teclado cuando no hay ningún teclado físico disponible.</span><span class="sxs-lookup"><span data-stu-id="f01b2-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="f01b2-110">Comportamiento del teclado del sistema HoloLens en Unity</span><span class="sxs-lookup"><span data-stu-id="f01b2-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="f01b2-111">En HoloLens, el *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema.</span><span class="sxs-lookup"><span data-stu-id="f01b2-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="f01b2-112">El teclado en pantalla del sistema no se puede superponer sobre una vista volumétrica, por lo que Unity tiene que crear una vista XAML 2D secundaria para mostrar el teclado y volver a la vista volumétrica una vez que se ha enviado la entrada.</span><span class="sxs-lookup"><span data-stu-id="f01b2-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="f01b2-113">El flujo de usuario es similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="f01b2-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="f01b2-114">El usuario realiza una acción que hace que el código de la aplicación llame a *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f01b2-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="f01b2-115">La aplicación es responsable de pausar el estado de la aplicación antes de llamar a *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f01b2-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="f01b2-116">La aplicación puede finalizar antes de volver a cambiar a la vista volumétrica.</span><span class="sxs-lookup"><span data-stu-id="f01b2-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="f01b2-117">Unity cambia a una vista XAML 2D que se coloca automáticamente en el mundo.</span><span class="sxs-lookup"><span data-stu-id="f01b2-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="f01b2-118">El usuario escribe texto mediante el teclado del sistema y lo envía o cancela.</span><span class="sxs-lookup"><span data-stu-id="f01b2-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="f01b2-119">Unity vuelve a cambiar a la vista volumétrica</span><span class="sxs-lookup"><span data-stu-id="f01b2-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="f01b2-120">La aplicación es responsable de reanudar el estado de la aplicación cuando se realiza la *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f01b2-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="f01b2-121">El texto enviado está disponible en *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="f01b2-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="f01b2-122">Vistas del teclado disponibles</span><span class="sxs-lookup"><span data-stu-id="f01b2-122">Available keyboard views</span></span>

<span data-ttu-id="f01b2-123">Hay seis vistas de teclado diferentes disponibles:</span><span class="sxs-lookup"><span data-stu-id="f01b2-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="f01b2-124">Cuadro de texto de una sola línea</span><span class="sxs-lookup"><span data-stu-id="f01b2-124">Single-line textbox</span></span>
* <span data-ttu-id="f01b2-125">Cuadro de texto de una sola línea con título</span><span class="sxs-lookup"><span data-stu-id="f01b2-125">Single-line textbox with title</span></span>
* <span data-ttu-id="f01b2-126">Cuadro de texto de varias líneas</span><span class="sxs-lookup"><span data-stu-id="f01b2-126">Multi-line textbox</span></span>
* <span data-ttu-id="f01b2-127">Cuadro de texto de varias líneas con título</span><span class="sxs-lookup"><span data-stu-id="f01b2-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="f01b2-128">Cuadro de contraseña de una sola línea</span><span class="sxs-lookup"><span data-stu-id="f01b2-128">Single-line password box</span></span>
* <span data-ttu-id="f01b2-129">Cuadro de contraseña de una sola línea con título</span><span class="sxs-lookup"><span data-stu-id="f01b2-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="f01b2-130">Cómo habilitar el teclado del sistema en Unity</span><span class="sxs-lookup"><span data-stu-id="f01b2-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="f01b2-131">El teclado del sistema HoloLens solo está disponible para las aplicaciones de Unity que se exportan con el "tipo de compilación de UWP" establecido en "XAML".</span><span class="sxs-lookup"><span data-stu-id="f01b2-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="f01b2-132">Hay inconvenientes que debe realizar al elegir "XAML" como "tipo de compilación de UWP" sobre "D3D".</span><span class="sxs-lookup"><span data-stu-id="f01b2-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="f01b2-133">Si no está familiarizado con esos inconvenientes, puede que desee explorar una [solución de entrada alternativa](#alternative-keyboard-options) al teclado del sistema.</span><span class="sxs-lookup"><span data-stu-id="f01b2-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="f01b2-134">Abra el menú **archivo** y seleccione **configuración de compilación..** .</span><span class="sxs-lookup"><span data-stu-id="f01b2-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="f01b2-135">Asegúrese de que la **plataforma** esté establecida en **tienda Windows**, que el **SDK** esté establecido en **universal 10**y establezca el **tipo de compilación de UWP** en **XAML**.</span><span class="sxs-lookup"><span data-stu-id="f01b2-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="f01b2-136">En el cuadro de diálogo **configuración de compilación** , haga clic en el botón **configuración del reproductor...**</span><span class="sxs-lookup"><span data-stu-id="f01b2-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="f01b2-137">Seleccionar la **configuración de la pestaña de la tienda Windows**</span><span class="sxs-lookup"><span data-stu-id="f01b2-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="f01b2-138">Expandir el grupo **otras configuraciones**</span><span class="sxs-lookup"><span data-stu-id="f01b2-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="f01b2-139">En la sección **representación** , active la casilla **compatibilidad con realidad virtual** para agregar una nueva lista de **dispositivos de realidad virtual**</span><span class="sxs-lookup"><span data-stu-id="f01b2-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="f01b2-140">Asegúrese de que **Windows Holographic** aparece en la lista de SDK de realidad virtual</span><span class="sxs-lookup"><span data-stu-id="f01b2-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="f01b2-141">Si no marca la compilación como realidad virtual compatible con el dispositivo HoloLens, el proyecto se exportará como una aplicación XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="f01b2-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="f01b2-142">Uso del teclado del sistema en la aplicación de Unity</span><span class="sxs-lookup"><span data-stu-id="f01b2-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="f01b2-143">Declarar el teclado</span><span class="sxs-lookup"><span data-stu-id="f01b2-143">Declare the keyboard</span></span>

<span data-ttu-id="f01b2-144">En la clase, declare una variable para almacenar el *TouchScreenKeyboard* y una variable que contenga la cadena que devuelve el teclado.</span><span class="sxs-lookup"><span data-stu-id="f01b2-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="f01b2-145">Invocar el teclado</span><span class="sxs-lookup"><span data-stu-id="f01b2-145">Invoke the keyboard</span></span>

<span data-ttu-id="f01b2-146">Cuando se produce un evento que solicita una entrada de teclado, llame a una de estas funciones según el tipo de entrada que desee.</span><span class="sxs-lookup"><span data-stu-id="f01b2-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="f01b2-147">Tenga en cuenta que el título se especifica en el parámetro textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="f01b2-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="f01b2-148">Recuperar contenido con tipo</span><span class="sxs-lookup"><span data-stu-id="f01b2-148">Retrieve typed contents</span></span>

<span data-ttu-id="f01b2-149">En el bucle de actualización, compruebe si el teclado ha recibido una nueva entrada y almacénela para su uso en otra parte.</span><span class="sxs-lookup"><span data-stu-id="f01b2-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="f01b2-150">Opciones de teclado alternativas</span><span class="sxs-lookup"><span data-stu-id="f01b2-150">Alternative keyboard options</span></span>

<span data-ttu-id="f01b2-151">Sabemos que el desactivador de una vista volumétrica en una vista 2D no es la manera ideal de obtener entradas de texto del usuario.</span><span class="sxs-lookup"><span data-stu-id="f01b2-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="f01b2-152">Las alternativas actuales para aprovechar el teclado del sistema mediante Unity incluyen:</span><span class="sxs-lookup"><span data-stu-id="f01b2-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="f01b2-153">Usar el dictado de voz para la entrada (<b>Nota:</b> a menudo esto es propenso a errores para las palabras que no se encuentran en el Diccionario y no es adecuada para la entrada de contraseña)</span><span class="sxs-lookup"><span data-stu-id="f01b2-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="f01b2-154">Crear un teclado que funcione en la vista exclusiva de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="f01b2-154">Create a keyboard that works in your applications exclusive view</span></span>
