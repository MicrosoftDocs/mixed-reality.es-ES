---
title: Entrada MR 211-gesto
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de gestos.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, tutorial, gesto
ms.openlocfilehash: 694f51f1b56588e100d6d2676a8194d7e9936133
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559877"
---
>[!NOTE]
><span data-ttu-id="af748-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="af748-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="af748-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="af748-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="af748-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af748-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="af748-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="af748-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="af748-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af748-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="af748-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="af748-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="af748-110">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="af748-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="af748-111">Los [gestos](gestures.md) convierten la intención del usuario en acción.</span><span class="sxs-lookup"><span data-stu-id="af748-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="af748-112">Con los gestos, los usuarios pueden interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="af748-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="af748-113">En este curso, aprenderá a realizar un seguimiento de las manos del usuario, a responder a la entrada del usuario y a enviar comentarios al usuario en función del estado y la ubicación de la mano.</span><span class="sxs-lookup"><span data-stu-id="af748-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="af748-114">En los [conceptos básicos de MR 101](holograms-101.md), usamos un sencillo gesto de TAP de aire para interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="af748-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="af748-115">Ahora, pasaremos más allá del gesto de TAP de aire y exploraremos los nuevos conceptos para:</span><span class="sxs-lookup"><span data-stu-id="af748-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="af748-116">Detecta cuándo se realiza el seguimiento de la mano del usuario y proporciona comentarios al usuario.</span><span class="sxs-lookup"><span data-stu-id="af748-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="af748-117">Use un gesto de navegación para rotar los hologramas.</span><span class="sxs-lookup"><span data-stu-id="af748-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="af748-118">Proporcione comentarios cuando el usuario esté a punto de salir de la vista.</span><span class="sxs-lookup"><span data-stu-id="af748-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="af748-119">Use los eventos de manipulación para permitir que los usuarios muevan hologramas con sus manos.</span><span class="sxs-lookup"><span data-stu-id="af748-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="af748-120">En este curso, volveremos a visitar el explorador de **modelos**de proyectos de Unity, que hemos creado en la [entrada Mr 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="af748-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="af748-121">Nuestro amigo Astronaut está de regreso para ayudarnos en nuestra exploración de estos nuevos conceptos de gestos.</span><span class="sxs-lookup"><span data-stu-id="af748-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="af748-122">Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="af748-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="af748-123">Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="af748-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="af748-124">Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.</span><span class="sxs-lookup"><span data-stu-id="af748-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="af748-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="af748-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="af748-126">Recurso</span><span class="sxs-lookup"><span data-stu-id="af748-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="af748-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="af748-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="af748-128"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="af748-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="af748-129">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="af748-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="af748-130">✔️</span><span class="sxs-lookup"><span data-stu-id="af748-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="af748-131">✔️</span><span class="sxs-lookup"><span data-stu-id="af748-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="af748-132">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="af748-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="af748-133">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="af748-133">Prerequisites</span></span>

* <span data-ttu-id="af748-134">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.</span><span class="sxs-lookup"><span data-stu-id="af748-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="af748-135">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="af748-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="af748-136">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="af748-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="af748-137">Debe haber completado la [entrada MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="af748-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="af748-138">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="af748-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="af748-139">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="af748-139">Project files</span></span>

* <span data-ttu-id="af748-140">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="af748-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="af748-141"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="af748-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="af748-142">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="af748-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="af748-143">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="af748-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="af748-144">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="af748-144">Errata and Notes</span></span>

* <span data-ttu-id="af748-145">"Habilitar Solo mi código" debe estar deshabilitado(desactivado) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="af748-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="af748-146">Capítulo 0: configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="af748-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="af748-147">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="af748-147">Instructions</span></span>

1. <span data-ttu-id="af748-148">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="af748-148">Start Unity.</span></span>
2. <span data-ttu-id="af748-149">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="af748-149">Select **Open**.</span></span>
3. <span data-ttu-id="af748-150">Navegue hasta la carpeta de gestos que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="af748-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="af748-151">Busque y seleccione la carpeta de **Inicio**/del**Explorador de modelos** .</span><span class="sxs-lookup"><span data-stu-id="af748-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="af748-152">Haga clic en el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="af748-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="af748-153">En el panel **proyecto** , expanda la carpeta **escenas** .</span><span class="sxs-lookup"><span data-stu-id="af748-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="af748-154">Haga doble clic en **ModelExplorer** Scene para cargarlo en Unity.</span><span class="sxs-lookup"><span data-stu-id="af748-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="af748-155">Compilación</span><span class="sxs-lookup"><span data-stu-id="af748-155">Building</span></span>

1. <span data-ttu-id="af748-156">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="af748-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="af748-157">Si **Scenes/ModelExplorer** no aparece en **escenas en la compilación**, haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="af748-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="af748-158">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="af748-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="af748-159">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="af748-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="af748-160">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="af748-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="af748-161">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="af748-161">Click **Build**.</span></span>
6. <span data-ttu-id="af748-162">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="af748-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="af748-163">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="af748-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="af748-164">Presione **Seleccionar carpeta** y Unity comenzará a compilar el proyecto para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af748-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="af748-165">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="af748-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="af748-166">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="af748-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="af748-167">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="af748-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="af748-168">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="af748-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="af748-169">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="af748-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="af748-170">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="af748-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="af748-171">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="af748-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="af748-172">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="af748-172">Click **Select**.</span></span> <span data-ttu-id="af748-173">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="af748-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="af748-174">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="af748-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="af748-175">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="af748-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="af748-176">Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.</span><span class="sxs-lookup"><span data-stu-id="af748-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="af748-177">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="af748-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="af748-178">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="af748-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="af748-179">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="af748-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="af748-180">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="af748-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="af748-181">Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="af748-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="af748-182">Es posible que observe algunos errores rojos en el panel de errores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af748-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="af748-183">Es seguro ignorarlos.</span><span class="sxs-lookup"><span data-stu-id="af748-183">It is safe to ignore them.</span></span> <span data-ttu-id="af748-184">Cambie al panel de salida para ver el progreso real de la compilación.</span><span class="sxs-lookup"><span data-stu-id="af748-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="af748-185">Los errores en el panel de salida requerirán que se realice una corrección (la mayoría de las veces se deben a un error en un script).</span><span class="sxs-lookup"><span data-stu-id="af748-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="af748-186">Capítulo 1: comentarios de la mano detectados</span><span class="sxs-lookup"><span data-stu-id="af748-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="af748-187">Objetivos</span><span class="sxs-lookup"><span data-stu-id="af748-187">Objectives</span></span>

* <span data-ttu-id="af748-188">Suscríbase a los eventos de seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="af748-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="af748-189">Use los comentarios del cursor para mostrar a los usuarios Cuándo se realiza el seguimiento de una mano.</span><span class="sxs-lookup"><span data-stu-id="af748-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="af748-190">En HoloLens 2, las manos detectadas se activan siempre que las manos están visibles (no solo cuando se señala un dedo).</span><span class="sxs-lookup"><span data-stu-id="af748-190">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="af748-191">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="af748-191">Instructions</span></span>

* <span data-ttu-id="af748-192">En el panel **jerarquía** , expanda el objeto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="af748-192">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="af748-193">Busque y seleccione el objeto **GesturesInput** .</span><span class="sxs-lookup"><span data-stu-id="af748-193">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="af748-194">El script **InteractionInputSource.CS** realiza estos pasos:</span><span class="sxs-lookup"><span data-stu-id="af748-194">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="af748-195">Se suscribe a los eventos InteractionSourceDetected y InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="af748-195">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="af748-196">Establece el estado de HandDetected.</span><span class="sxs-lookup"><span data-stu-id="af748-196">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="af748-197">Cancela la suscripción de los eventos InteractionSourceDetected y InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="af748-197">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="af748-198">A continuación, actualizaremos el cursor de la [entrada MR 210](holograms-210.md) a uno que muestra comentarios en función de las acciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="af748-198">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="af748-199">En el panel **jerarquía** , seleccione el objeto **cursor** y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="af748-199">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="af748-200">En el panel **proyecto** , busque **CursorWithFeedback** y arrástrelo al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="af748-200">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="af748-201">Haga clic en **InputManager** en el panel de **jerarquías** y, a continuación, arrastre el objeto **CursorWithFeedback** desde la **jerarquía** al campo **cursor** de **SimpleSinglePointerSelector**de InputManager, situado en la parte inferior de la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="af748-201">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="af748-202">Haga clic en **CursorWithFeedback** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="af748-202">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="af748-203">En el panel **Inspector** , expanda **datos de estado de cursor** en el script de cursor de **objeto** .</span><span class="sxs-lookup"><span data-stu-id="af748-203">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="af748-204">Los **datos de estado del cursor** funcionan de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="af748-204">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="af748-205">Cualquier estado **observado** significa que no se detecta ninguna mano y que el usuario simplemente está buscando.</span><span class="sxs-lookup"><span data-stu-id="af748-205">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="af748-206">Cualquier estado de **interacción** significa que se detecta una mano o un controlador.</span><span class="sxs-lookup"><span data-stu-id="af748-206">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="af748-207">Cualquier estado de **mantener el mouse** significa que el usuario está examinando un holograma.</span><span class="sxs-lookup"><span data-stu-id="af748-207">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="af748-208">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="af748-208">Build and Deploy</span></span>

* <span data-ttu-id="af748-209">En Unity, use la **configuración de compilación de > de archivos** para recompilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="af748-209">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="af748-210">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="af748-210">Open the **App** folder.</span></span>
* <span data-ttu-id="af748-211">Si aún no está abierto, abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="af748-211">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="af748-212">(Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "recargar todo" cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="af748-212">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="af748-213">En Visual Studio, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="af748-213">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="af748-214">Después de que la aplicación se implemente en HoloLens, descartará el fitbox con el gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="af748-214">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="af748-215">Mueva la mano a la vista y apunte el dedo del índice al cielo para iniciar el seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="af748-215">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="af748-216">Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="af748-216">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="af748-217">Observe cómo cambia el cursor cuando se detecta la mano y, a continuación, se pierde de la vista.</span><span class="sxs-lookup"><span data-stu-id="af748-217">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="af748-218">Si se encuentra en un casco envolvente, tendrá que conectar y desconectar el controlador.</span><span class="sxs-lookup"><span data-stu-id="af748-218">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="af748-219">Esta información es menos interesante en un dispositivo envolvente, ya que un controlador conectado siempre estará "disponible".</span><span class="sxs-lookup"><span data-stu-id="af748-219">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="af748-220">Capítulo 2: navegación</span><span class="sxs-lookup"><span data-stu-id="af748-220">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="af748-221">Objetivos</span><span class="sxs-lookup"><span data-stu-id="af748-221">Objectives</span></span>

* <span data-ttu-id="af748-222">Use los eventos de gestos de navegación para rotar el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-222">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="af748-223">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="af748-223">Instructions</span></span>

<span data-ttu-id="af748-224">Para usar los gestos de navegación en nuestra aplicación, vamos a editar **GestureAction.CS** para girar objetos cuando se produce el gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="af748-224">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="af748-225">Además, agregaremos comentarios al cursor para que se muestren cuando la navegación esté disponible.</span><span class="sxs-lookup"><span data-stu-id="af748-225">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="af748-226">En el panel **jerarquía** , expanda **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="af748-226">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="af748-227">En la carpeta hologramas, busque el recurso **ScrollFeedback** .</span><span class="sxs-lookup"><span data-stu-id="af748-227">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="af748-228">Arrastre y coloque el recurso prefabricado de **ScrollFeedback** en **CursorWithFeedback** GameObject en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="af748-228">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="af748-229">Haga clic en **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="af748-229">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="af748-230">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="af748-230">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="af748-231">En el menú, escriba en el cuadro de búsqueda **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="af748-231">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="af748-232">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-232">Select the search result.</span></span>
7. <span data-ttu-id="af748-233">Arrastre y coloque el objeto **ScrollFeedback** de la **jerarquía** en la propiedad **desplazamiento de objeto de juego detectado** del componente **cursor feedback** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="af748-233">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="af748-234">En el panel **jerarquía** , seleccione el objeto **AstroMan** .</span><span class="sxs-lookup"><span data-stu-id="af748-234">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="af748-235">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="af748-235">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="af748-236">En el menú, escriba en la acción de **gestos**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-236">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="af748-237">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-237">Select the search result.</span></span>

<span data-ttu-id="af748-238">A continuación, Abra **GestureAction.CS** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="af748-238">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="af748-239">En el ejercicio de codificación 2. c, edite el script para hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="af748-239">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="af748-240">**Gire el objeto AstroMan** cada vez que se lleve a cabo un gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="af748-240">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="af748-241">Calcule el valor de **rotationFactor** para controlar la cantidad de giro aplicada al objeto.</span><span class="sxs-lookup"><span data-stu-id="af748-241">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="af748-242">**Gire el objeto** alrededor del eje y cuando el usuario mueva su mano a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="af748-242">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="af748-243">Complete los ejercicios de codificación 2. c en el script o reemplace el código por la solución completada que aparece a continuación:</span><span class="sxs-lookup"><span data-stu-id="af748-243">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="af748-244">Observará que los demás eventos de navegación ya se han rellenado con cierta información.</span><span class="sxs-lookup"><span data-stu-id="af748-244">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="af748-245">La GameObject se envía a la pila modal InputSystem's del kit de herramientas, por lo que el usuario no tiene que mantener el foco en el Astronaut una vez que se ha iniciado la rotación.</span><span class="sxs-lookup"><span data-stu-id="af748-245">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="af748-246">En consecuencia, se extrae el GameObject de la pila una vez que se completa el gesto.</span><span class="sxs-lookup"><span data-stu-id="af748-246">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="af748-247">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="af748-247">Build and Deploy</span></span>

1. <span data-ttu-id="af748-248">Vuelva a compilar la aplicación en Unity y, después, compile e implemente desde Visual Studio para ejecutarla en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="af748-248">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="af748-249">Mira el Astronaut, dos flechas deben aparecer a cada lado del cursor.</span><span class="sxs-lookup"><span data-stu-id="af748-249">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="af748-250">Este nuevo visual indica que el Astronaut se puede girar.</span><span class="sxs-lookup"><span data-stu-id="af748-250">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="af748-251">Coloque la mano en la posición listo (el dedo índice apunta hacia el cielo) para que HoloLens empiece a realizar un seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="af748-251">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="af748-252">Para girar el Astronaut, baje el dedo del índice a una posición de pinch y, a continuación, mueva la mano hacia la izquierda o hacia la derecha para desencadenar el gesto de NavigationX.</span><span class="sxs-lookup"><span data-stu-id="af748-252">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="af748-253">Capítulo 3: orientación a mano</span><span class="sxs-lookup"><span data-stu-id="af748-253">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="af748-254">Objetivos</span><span class="sxs-lookup"><span data-stu-id="af748-254">Objectives</span></span>

* <span data-ttu-id="af748-255">Use la puntuación de la **Guía de mano** para ayudar a predecir cuándo se perderá el seguimiento de manos.</span><span class="sxs-lookup"><span data-stu-id="af748-255">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="af748-256">Proporcione **comentarios sobre el cursor** para mostrar Cuándo el usuario está cerca del borde de la cámara de la vista.</span><span class="sxs-lookup"><span data-stu-id="af748-256">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="af748-257">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="af748-257">Instructions</span></span>

1. <span data-ttu-id="af748-258">En el panel **jerarquía** , seleccione el objeto **CursorWithFeedback** .</span><span class="sxs-lookup"><span data-stu-id="af748-258">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="af748-259">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="af748-259">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="af748-260">En el menú, escriba en la guía de **mano**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-260">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="af748-261">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-261">Select the search result.</span></span>
4. <span data-ttu-id="af748-262">En la carpeta **hologramas** del panel de **proyecto** , busque el recurso **HandGuidanceFeedback** .</span><span class="sxs-lookup"><span data-stu-id="af748-262">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="af748-263">Arrastre y coloque el recurso **HandGuidanceFeedback** en la propiedad **indicador de orientación a mano** del panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="af748-263">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="af748-264">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="af748-264">Build and Deploy</span></span>

* <span data-ttu-id="af748-265">Vuelva a compilar la aplicación en Unity y, después, compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="af748-265">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="af748-266">Traiga su mano a la vista y eleve el dedo del índice para realizar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="af748-266">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="af748-267">Empiece a girar Astronaut con el gesto de navegación (acerque el dedo del índice y Thumb juntos).</span><span class="sxs-lookup"><span data-stu-id="af748-267">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="af748-268">Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="af748-268">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="af748-269">A medida que su mano esté cerca del borde del marco de gestos, debe aparecer una flecha junto al cursor para avisarle de que se perderá el seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="af748-269">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="af748-270">La flecha indica la dirección a la que debe DESPLACESE para evitar que se pierda el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="af748-270">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="af748-271">Capítulo 4: manipulación</span><span class="sxs-lookup"><span data-stu-id="af748-271">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="af748-272">Objetivos</span><span class="sxs-lookup"><span data-stu-id="af748-272">Objectives</span></span>

* <span data-ttu-id="af748-273">Use los eventos de manipulación para trasladar el Astronaut con las manos.</span><span class="sxs-lookup"><span data-stu-id="af748-273">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="af748-274">Proporcione comentarios sobre el cursor para que el usuario sepa cuándo se puede usar la manipulación.</span><span class="sxs-lookup"><span data-stu-id="af748-274">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="af748-275">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="af748-275">Instructions</span></span>

<span data-ttu-id="af748-276">GestureManager.cs y AstronautManager.cs nos permiten hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="af748-276">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="af748-277">Use la palabra clave de voz "**Move Astronaut**" para habilitar los gestos de **manipulación** y "**rotar Astronaut**" para deshabilitarlos.</span><span class="sxs-lookup"><span data-stu-id="af748-277">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="af748-278">Cambie a responder al reconocedor de gestos de **manipulación**.</span><span class="sxs-lookup"><span data-stu-id="af748-278">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="af748-279">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="af748-279">Let's get started.</span></span>

1. <span data-ttu-id="af748-280">En el panel **jerarquía** , cree un nuevo GameObject vacío.</span><span class="sxs-lookup"><span data-stu-id="af748-280">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="af748-281">Asígnele el nombre "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="af748-281">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="af748-282">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="af748-282">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="af748-283">En el menú, escriba en el cuadro de búsqueda **Astronaut Manager**.</span><span class="sxs-lookup"><span data-stu-id="af748-283">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="af748-284">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-284">Select the search result.</span></span>
4. <span data-ttu-id="af748-285">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="af748-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="af748-286">En el menú, escriba en el cuadro de búsqueda **origen de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="af748-286">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="af748-287">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-287">Select the search result.</span></span>

<span data-ttu-id="af748-288">Ahora agregaremos los comandos de voz necesarios para controlar el estado de interacción de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-288">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="af748-289">Expanda la sección **palabras clave** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="af748-289">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="af748-290">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="af748-290">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="af748-291">Escriba la palabra clave como **Move Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="af748-291">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="af748-292">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="af748-292">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="af748-293">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="af748-293">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="af748-294">Escriba la palabra clave como **rotar Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="af748-294">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="af748-295">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="af748-295">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="af748-296">El código de controlador correspondiente se puede encontrar en **GestureAction.CS**, en el controlador **ISpeechHandler. OnSpeechKeywordRecognized** .</span><span class="sxs-lookup"><span data-stu-id="af748-296">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Cómo configurar el origen de entrada de voz para el capítulo 4](images/holograms211-speech.png)

<span data-ttu-id="af748-298">A continuación, configuraremos los comentarios de manipulación en el cursor.</span><span class="sxs-lookup"><span data-stu-id="af748-298">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="af748-299">En la carpeta **hologramas** del panel de **proyecto** , busque el recurso **PathingFeedback** .</span><span class="sxs-lookup"><span data-stu-id="af748-299">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="af748-300">Arrastre y coloque el recurso prefabricado **PathingFeedback** en el objeto **CursorWithFeedback** de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="af748-300">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="af748-301">En el panel **jerarquía** , haga clic en **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="af748-301">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="af748-302">Arrastre y coloque el objeto **PathingFeedback** de la **jerarquía** en la propiedad del **objeto de juego Thing detectado** del componente **cursor feedback** del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="af748-302">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="af748-303">Ahora debemos agregar código a **GestureAction.CS** para habilitar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="af748-303">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="af748-304">Agregue código a la función **IManipulationHandler. OnManipulationUpdated** , que moverá el Astronaut cuando se detecte un gesto de **manipulación** .</span><span class="sxs-lookup"><span data-stu-id="af748-304">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="af748-305">Calcule el **Vector de movimiento** para determinar dónde se debe mover el Astronaut en función de la posición de la mano.</span><span class="sxs-lookup"><span data-stu-id="af748-305">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="af748-306">**Mueva** el Astronaut a la nueva posición.</span><span class="sxs-lookup"><span data-stu-id="af748-306">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="af748-307">Complete la codificación ejercicio 4. a en **GestureAction.CS**o use nuestra solución completada a continuación:</span><span class="sxs-lookup"><span data-stu-id="af748-307">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="af748-308">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="af748-308">Build and Deploy</span></span>

* <span data-ttu-id="af748-309">Recompile en Unity y, después, compile e implemente desde Visual Studio para ejecutar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="af748-309">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="af748-310">Mueva la mano hacia delante de HoloLens y eleve el dedo del índice para que se pueda realizar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="af748-310">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="af748-311">Centre el cursor sobre el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-311">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="af748-312">Por ejemplo, "Move Astronaut" para trasladar Astronaut con un gesto de manipulación.</span><span class="sxs-lookup"><span data-stu-id="af748-312">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="af748-313">Deben aparecer cuatro flechas alrededor del cursor para indicar que el programa responderá ahora a los eventos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="af748-313">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="af748-314">Baje el dedo del índice hasta el pulgar y manténgalos reducidos juntos.</span><span class="sxs-lookup"><span data-stu-id="af748-314">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="af748-315">A medida que mueve la mano, el Astronaut se moverá también (esta es la manipulación).</span><span class="sxs-lookup"><span data-stu-id="af748-315">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="af748-316">Eleve el dedo del índice para dejar de manipular el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-316">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="af748-317">Nota: Si no se indica "mover Astronaut" antes de mover la mano, se usará en su lugar el gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="af748-317">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="af748-318">Por ejemplo, "rotar Astronaut" para volver al estado Rotatable.</span><span class="sxs-lookup"><span data-stu-id="af748-318">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="af748-319">Capítulo 5: expansión del modelo</span><span class="sxs-lookup"><span data-stu-id="af748-319">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="af748-320">Objetivos</span><span class="sxs-lookup"><span data-stu-id="af748-320">Objectives</span></span>

* <span data-ttu-id="af748-321">Expanda el modelo Astronaut en varias partes más pequeñas con las que el usuario pueda interactuar.</span><span class="sxs-lookup"><span data-stu-id="af748-321">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="af748-322">Mueva cada pieza individualmente mediante gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="af748-322">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="af748-323">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="af748-323">Instructions</span></span>

<span data-ttu-id="af748-324">En esta sección, se realizarán las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="af748-324">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="af748-325">Agregue una nueva palabra clave "**Expand Model**" para expandir el modelo Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-325">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="af748-326">Agregue una nueva palabra clave "**RESET Model**" para devolver el modelo a su forma original.</span><span class="sxs-lookup"><span data-stu-id="af748-326">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="af748-327">Haremos esto agregando dos palabras clave más al origen de entrada de voz del capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="af748-327">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="af748-328">También mostraremos otra manera de controlar los eventos de reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="af748-328">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="af748-329">Haga clic en atrás en **AstronautManager** en el **Inspector** y expanda la sección **palabras clave** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="af748-329">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="af748-330">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="af748-330">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="af748-331">Escriba la palabra clave como **modelo de expansión**.</span><span class="sxs-lookup"><span data-stu-id="af748-331">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="af748-332">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="af748-332">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="af748-333">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="af748-333">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="af748-334">Escriba la palabra clave como **restablecer modelo**.</span><span class="sxs-lookup"><span data-stu-id="af748-334">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="af748-335">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="af748-335">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="af748-336">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="af748-336">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="af748-337">En el menú, escriba en el cuadro de búsqueda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="af748-337">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="af748-338">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="af748-338">Select the search result.</span></span>
8. <span data-ttu-id="af748-339">Check **es el agente de escucha global**, ya que queremos que estos comandos funcionen independientemente de la GameObject a la que nos centramos.</span><span class="sxs-lookup"><span data-stu-id="af748-339">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="af748-340">Haga clic **+** en el botón y seleccione **expandir modelo** en la lista desplegable palabra clave.</span><span class="sxs-lookup"><span data-stu-id="af748-340">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="af748-341">Haga clic en en respuesta y arrastre el **AstronautManager** desde la **jerarquía** hasta el campo **ninguno (objeto).** **+**</span><span class="sxs-lookup"><span data-stu-id="af748-341">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="af748-342">Ahora, haga clic en la lista desplegable **no función** , seleccione **AstronautManager**y **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="af748-342">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="af748-343">Haga clic en el botón del **+** controlador de entrada de voz y seleccione **restablecer modelo** en la lista desplegable palabra clave.</span><span class="sxs-lookup"><span data-stu-id="af748-343">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="af748-344">Haga clic en en respuesta y arrastre el **AstronautManager** desde la **jerarquía** hasta el campo **ninguno (objeto).** **+**</span><span class="sxs-lookup"><span data-stu-id="af748-344">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="af748-345">Ahora, haga clic en la lista desplegable **no función** , seleccione **AstronautManager**y **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="af748-345">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Cómo configurar el origen y el controlador de entrada de voz para el capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="af748-347">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="af748-347">Build and Deploy</span></span>

* <span data-ttu-id="af748-348">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="af748-348">Try it!</span></span> <span data-ttu-id="af748-349">Compile e implemente la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="af748-349">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="af748-350">Por ejemplo, **expanda modelo** para ver el modelo Astronaut expandido.</span><span class="sxs-lookup"><span data-stu-id="af748-350">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="af748-351">Use la **navegación** para girar partes individuales del palo de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-351">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="af748-352">Por ejemplo, **mueva Astronaut** y, a continuación, use la **manipulación** para desplace partes individuales del palo de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="af748-352">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="af748-353">Por ejemplo, **gire Astronaut** para volver a girar las piezas.</span><span class="sxs-lookup"><span data-stu-id="af748-353">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="af748-354">Por ejemplo, **restablezca el modelo** para devolver el Astronaut a su forma original.</span><span class="sxs-lookup"><span data-stu-id="af748-354">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="af748-355">Fin</span><span class="sxs-lookup"><span data-stu-id="af748-355">The End</span></span>

<span data-ttu-id="af748-356">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="af748-356">Congratulations!</span></span> <span data-ttu-id="af748-357">Ya ha completado **la entrada Mr 211: Movimiento**.</span><span class="sxs-lookup"><span data-stu-id="af748-357">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="af748-358">Sabe cómo detectar y responder a los eventos de seguimiento, navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="af748-358">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="af748-359">Comprende la diferencia entre los gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="af748-359">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="af748-360">Sabe cómo cambiar el cursor para proporcionar comentarios visuales sobre cuándo se detecta una mano, Cuándo se va a perder una mano y cuándo un objeto admite distintas interacciones (navegación frente a manipulación).</span><span class="sxs-lookup"><span data-stu-id="af748-360">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
