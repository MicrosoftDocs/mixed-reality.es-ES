---
title: Entradas mediante teclado en Unity
description: Unity proporciona la clase TouchScreenKeyboard para aceptar la entrada de teclado cuando no hay disponible ningún teclado físico.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: unity de entrada, teclado, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605741"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="8f27c-104">Entradas mediante teclado en Unity</span><span class="sxs-lookup"><span data-stu-id="8f27c-104">Keyboard input in Unity</span></span>

<span data-ttu-id="8f27c-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="8f27c-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="8f27c-106">**Tipo**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="8f27c-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="8f27c-107">Mientras HoloLens admite muchos formatos de entrada, incluidos los teclados Bluetooth, la mayoría de las aplicaciones no puede suponer que todos los usuarios tendrán un teclado físico disponible.</span><span class="sxs-lookup"><span data-stu-id="8f27c-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="8f27c-108">Si la aplicación requiere una entrada de texto, se debe proporcionar algún tipo de teclado en pantalla.</span><span class="sxs-lookup"><span data-stu-id="8f27c-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="8f27c-109">Unity proporciona el *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* clase para aceptar la entrada de teclado cuando no hay disponible ningún teclado físico.</span><span class="sxs-lookup"><span data-stu-id="8f27c-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="8f27c-110">Comportamiento de teclado del sistema de HoloLens en Unity</span><span class="sxs-lookup"><span data-stu-id="8f27c-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="8f27c-111">En HoloLens, el *TouchScreenKeyboard* aprovecha el teclado en pantalla del sistema.</span><span class="sxs-lookup"><span data-stu-id="8f27c-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="8f27c-112">Teclado en pantalla del sistema no puede superponer sobre una vista volumétrica, por lo que Unity tiene que crear una vista XAML 2D secundaria para mostrar el teclado, a continuación, devolver a la vista volumétrica una vez que se ha enviado la entrada.</span><span class="sxs-lookup"><span data-stu-id="8f27c-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="8f27c-113">El flujo de usuario es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="8f27c-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="8f27c-114">El usuario realiza una acción haciendo que el código de aplicación llamar a *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="8f27c-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="8f27c-115">La aplicación es responsable de estado de la aplicación Pausando antes de llamar a *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="8f27c-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="8f27c-116">La aplicación puede finalizar antes de cambiar alguna vez a la vista volumétrica</span><span class="sxs-lookup"><span data-stu-id="8f27c-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="8f27c-117">Unity cambia a la vista XAML 2D que se encuentra ubicados automáticamente en el mundo</span><span class="sxs-lookup"><span data-stu-id="8f27c-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="8f27c-118">El usuario escribe texto mediante el teclado del sistema y envía o se cancela</span><span class="sxs-lookup"><span data-stu-id="8f27c-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="8f27c-119">Unity vuelve a cambiar a la vista volumétrica</span><span class="sxs-lookup"><span data-stu-id="8f27c-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="8f27c-120">La aplicación es responsable de reanudar la aplicación de estado cuando el *TouchScreenKeyboard* se realiza</span><span class="sxs-lookup"><span data-stu-id="8f27c-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="8f27c-121">Está disponible en el texto presentado el *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="8f27c-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="8f27c-122">Vistas de teclado disponibles</span><span class="sxs-lookup"><span data-stu-id="8f27c-122">Available keyboard views</span></span>

<span data-ttu-id="8f27c-123">Hay seis vistas diferentes de teclado disponibles:</span><span class="sxs-lookup"><span data-stu-id="8f27c-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="8f27c-124">Cuadro de texto multilínea</span><span class="sxs-lookup"><span data-stu-id="8f27c-124">Single-line textbox</span></span>
* <span data-ttu-id="8f27c-125">Cuadro de texto multilínea con título</span><span class="sxs-lookup"><span data-stu-id="8f27c-125">Single-line textbox with title</span></span>
* <span data-ttu-id="8f27c-126">Cuadro de texto multilínea</span><span class="sxs-lookup"><span data-stu-id="8f27c-126">Multi-line textbox</span></span>
* <span data-ttu-id="8f27c-127">Cuadro de texto de varias líneas con título</span><span class="sxs-lookup"><span data-stu-id="8f27c-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="8f27c-128">Cuadro de contraseña de la línea</span><span class="sxs-lookup"><span data-stu-id="8f27c-128">Single-line password box</span></span>
* <span data-ttu-id="8f27c-129">Cuadro de contraseña de la línea con título</span><span class="sxs-lookup"><span data-stu-id="8f27c-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="8f27c-130">Cómo habilitar el teclado del sistema en Unity</span><span class="sxs-lookup"><span data-stu-id="8f27c-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="8f27c-131">El teclado del sistema HoloLens solo está disponible para las aplicaciones de Unity que se exportan con el "UWP compilar tipo" establecido en "XAML".</span><span class="sxs-lookup"><span data-stu-id="8f27c-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="8f27c-132">Hay equilibrios que realizar cuando se elige "XAML" como el "tipo de generación de UWP" sobre "D3D".</span><span class="sxs-lookup"><span data-stu-id="8f27c-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="8f27c-133">Si no está familiarizado con estos inconvenientes, puede desear explorar un [solución de entrada alternativos](#alternative-keyboard-options) para el teclado del sistema.</span><span class="sxs-lookup"><span data-stu-id="8f27c-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="8f27c-134">Abra el **archivo** menú y seleccione **configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="8f27c-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="8f27c-135">Asegúrese del **plataforma** está establecido en **Windows Store**, el **SDK** está establecido en **10 Universal**y establezca el **el tipo de compilación para UWP**  a **XAML**.</span><span class="sxs-lookup"><span data-stu-id="8f27c-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="8f27c-136">En el **configuración de compilación** cuadro de diálogo, haga clic en el **configuración del Reproductor...**  botón</span><span class="sxs-lookup"><span data-stu-id="8f27c-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="8f27c-137">Seleccione el **configuración para Windows Store** ficha</span><span class="sxs-lookup"><span data-stu-id="8f27c-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="8f27c-138">Expanda el **otra configuración** grupo</span><span class="sxs-lookup"><span data-stu-id="8f27c-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="8f27c-139">En el **representación** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar un nuevo **dispositivos de realidad Virtual** lista</span><span class="sxs-lookup"><span data-stu-id="8f27c-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="8f27c-140">Asegúrese de **Windows Holographic** aparece en la lista de SDK de realidad Virtual</span><span class="sxs-lookup"><span data-stu-id="8f27c-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="8f27c-141">Si no marca la compilación como admite la realidad Virtual con el dispositivo HoloLens, exportará el proyecto como una aplicación XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="8f27c-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="8f27c-142">Usar el teclado del sistema en la aplicación de Unity</span><span class="sxs-lookup"><span data-stu-id="8f27c-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="8f27c-143">Declare el teclado</span><span class="sxs-lookup"><span data-stu-id="8f27c-143">Declare the keyboard</span></span>

<span data-ttu-id="8f27c-144">En la clase, declare una variable para almacenar el *TouchScreenKeyboard* y devuelve una variable que contenga la cadena en el teclado.</span><span class="sxs-lookup"><span data-stu-id="8f27c-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="8f27c-145">Invocar el teclado</span><span class="sxs-lookup"><span data-stu-id="8f27c-145">Invoke the keyboard</span></span>

<span data-ttu-id="8f27c-146">Cuando la solicitud de entrada de teclado produce un evento, llame a una de estas funciones según el tipo de entrada deseado.</span><span class="sxs-lookup"><span data-stu-id="8f27c-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="8f27c-147">Tenga en cuenta que el título se especifica en el parámetro textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="8f27c-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="8f27c-148">Recuperar contenido con tipo</span><span class="sxs-lookup"><span data-stu-id="8f27c-148">Retrieve typed contents</span></span>

<span data-ttu-id="8f27c-149">En el bucle de actualización, compruebe si el teclado recibió una entrada nueva y almacenarla para su uso en otro lugar.</span><span class="sxs-lookup"><span data-stu-id="8f27c-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="8f27c-150">Opciones de teclado alternativo</span><span class="sxs-lookup"><span data-stu-id="8f27c-150">Alternative keyboard options</span></span>

<span data-ttu-id="8f27c-151">Somos conscientes de que desactivando una vista en una vista 2D volumétrica no ideales para obtener la entrada de texto del usuario.</span><span class="sxs-lookup"><span data-stu-id="8f27c-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="8f27c-152">Las alternativas actuales a aprovechar el teclado del sistema a través de Unity incluyen:</span><span class="sxs-lookup"><span data-stu-id="8f27c-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="8f27c-153">Utilizando el dictado de voz de entrada (<b>Nota:</b> esto a menudo es propenso a errores no se encuentra en el diccionario de palabras y no es adecuado como entrada de contraseña)</span><span class="sxs-lookup"><span data-stu-id="8f27c-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="8f27c-154">Creación de un teclado que funciona en la vista exclusiva de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="8f27c-154">Create a keyboard that works in your applications exclusive view</span></span>
