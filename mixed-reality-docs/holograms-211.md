---
title: Entrada MR 211-gesto
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de gestos.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, tutorial, gesto
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522460"
---
>[!NOTE]
><span data-ttu-id="7259b-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="7259b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7259b-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7259b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7259b-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7259b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7259b-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="7259b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7259b-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7259b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7259b-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="7259b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="7259b-110">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="7259b-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="7259b-111">Los [gestos](gestures.md) convierten la intención del usuario en acción.</span><span class="sxs-lookup"><span data-stu-id="7259b-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="7259b-112">Con los gestos, los usuarios pueden interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="7259b-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="7259b-113">En este curso, aprenderá a realizar un seguimiento de las manos del usuario, a responder a la entrada del usuario y a enviar comentarios al usuario en función del estado y la ubicación de la mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="7259b-114">En los [conceptos básicos de MR 101](holograms-101.md), usamos un sencillo gesto de TAP de aire para interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="7259b-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="7259b-115">Ahora, pasaremos más allá del gesto de TAP de aire y exploraremos los nuevos conceptos para:</span><span class="sxs-lookup"><span data-stu-id="7259b-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="7259b-116">Detecta cuándo se realiza el seguimiento de la mano del usuario y proporciona comentarios al usuario.</span><span class="sxs-lookup"><span data-stu-id="7259b-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="7259b-117">Use un gesto de navegación para rotar los hologramas.</span><span class="sxs-lookup"><span data-stu-id="7259b-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="7259b-118">Proporcione comentarios cuando el usuario esté a punto de salir de la vista.</span><span class="sxs-lookup"><span data-stu-id="7259b-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="7259b-119">Use los eventos de manipulación para permitir que los usuarios muevan hologramas con sus manos.</span><span class="sxs-lookup"><span data-stu-id="7259b-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="7259b-120">En este curso, volveremos a visitar el explorador de **modelos**de proyectos de Unity, que hemos creado en la [entrada Mr 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="7259b-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="7259b-121">Nuestro amigo Astronaut está de regreso para ayudarnos en nuestra exploración de estos nuevos conceptos de gestos.</span><span class="sxs-lookup"><span data-stu-id="7259b-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="7259b-122">Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="7259b-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="7259b-123">Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="7259b-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="7259b-124">Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.</span><span class="sxs-lookup"><span data-stu-id="7259b-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="7259b-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="7259b-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7259b-126">Recurso</span><span class="sxs-lookup"><span data-stu-id="7259b-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7259b-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7259b-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7259b-128"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="7259b-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7259b-129">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="7259b-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="7259b-130">✔️</span><span class="sxs-lookup"><span data-stu-id="7259b-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7259b-131">✔️</span><span class="sxs-lookup"><span data-stu-id="7259b-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7259b-132">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="7259b-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7259b-133">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="7259b-133">Prerequisites</span></span>

* <span data-ttu-id="7259b-134">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.</span><span class="sxs-lookup"><span data-stu-id="7259b-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="7259b-135">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="7259b-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="7259b-136">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="7259b-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="7259b-137">Debe haber completado la [entrada MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="7259b-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="7259b-138">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="7259b-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="7259b-139">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="7259b-139">Project files</span></span>

* <span data-ttu-id="7259b-140">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="7259b-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="7259b-141"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="7259b-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="7259b-142">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="7259b-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="7259b-143">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="7259b-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="7259b-144">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="7259b-144">Errata and Notes</span></span>

* <span data-ttu-id="7259b-145">"Habilitar Solo mi código" debe estar deshabilitado *(* desactivado) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="7259b-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="7259b-146">Capítulo 0: configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="7259b-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="7259b-147">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="7259b-147">Instructions</span></span>

1. <span data-ttu-id="7259b-148">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="7259b-148">Start Unity.</span></span>
2. <span data-ttu-id="7259b-149">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="7259b-149">Select **Open**.</span></span>
3. <span data-ttu-id="7259b-150">Navegue hasta la carpeta de gestos que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="7259b-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="7259b-151">Busque y seleccione la carpeta de **Inicio**/del**Explorador de modelos** .</span><span class="sxs-lookup"><span data-stu-id="7259b-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="7259b-152">Haga clic en el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="7259b-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="7259b-153">En el panel **proyecto** , expanda la carpeta **escenas** .</span><span class="sxs-lookup"><span data-stu-id="7259b-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="7259b-154">Haga doble clic en **ModelExplorer** Scene para cargarlo en Unity.</span><span class="sxs-lookup"><span data-stu-id="7259b-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="7259b-155">Compilación</span><span class="sxs-lookup"><span data-stu-id="7259b-155">Building</span></span>

1. <span data-ttu-id="7259b-156">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="7259b-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="7259b-157">Si **Scenes/ModelExplorer** no aparece en **escenas en la compilación**, haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="7259b-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="7259b-158">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="7259b-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="7259b-159">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="7259b-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="7259b-160">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="7259b-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="7259b-161">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="7259b-161">Click **Build**.</span></span>
6. <span data-ttu-id="7259b-162">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="7259b-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="7259b-163">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="7259b-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="7259b-164">Presione **Seleccionar carpeta** y Unity comenzará a compilar el proyecto para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7259b-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="7259b-165">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="7259b-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="7259b-166">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="7259b-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="7259b-167">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7259b-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="7259b-168">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="7259b-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="7259b-169">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="7259b-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="7259b-170">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="7259b-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="7259b-171">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="7259b-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="7259b-172">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="7259b-172">Click **Select**.</span></span> <span data-ttu-id="7259b-173">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="7259b-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="7259b-174">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="7259b-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="7259b-175">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="7259b-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="7259b-176">Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.</span><span class="sxs-lookup"><span data-stu-id="7259b-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="7259b-177">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="7259b-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="7259b-178">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="7259b-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="7259b-179">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="7259b-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="7259b-180">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="7259b-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="7259b-181">Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="7259b-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="7259b-182">Es posible que observe algunos errores rojos en el panel de errores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7259b-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="7259b-183">Es seguro ignorarlos.</span><span class="sxs-lookup"><span data-stu-id="7259b-183">It is safe to ignore them.</span></span> <span data-ttu-id="7259b-184">Cambie al panel de salida para ver el progreso real de la compilación.</span><span class="sxs-lookup"><span data-stu-id="7259b-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="7259b-185">Los errores en el panel de salida requerirán que se realice una corrección (la mayoría de las veces se deben a un error en un script).</span><span class="sxs-lookup"><span data-stu-id="7259b-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="7259b-186">Capítulo 1: comentarios de la mano detectados</span><span class="sxs-lookup"><span data-stu-id="7259b-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="7259b-187">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7259b-187">Objectives</span></span>

* <span data-ttu-id="7259b-188">Suscríbase a los eventos de seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="7259b-189">Use los comentarios del cursor para mostrar a los usuarios Cuándo se realiza el seguimiento de una mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="7259b-190">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="7259b-190">Instructions</span></span>

* <span data-ttu-id="7259b-191">En el panel **jerarquía** , expanda el objeto **InputManager** .</span><span class="sxs-lookup"><span data-stu-id="7259b-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="7259b-192">Busque y seleccione el objeto **GesturesInput** .</span><span class="sxs-lookup"><span data-stu-id="7259b-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="7259b-193">El script **InteractionInputSource.CS** realiza estos pasos:</span><span class="sxs-lookup"><span data-stu-id="7259b-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="7259b-194">Se suscribe a los eventos InteractionSourceDetected y InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="7259b-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="7259b-195">Establece el estado de HandDetected.</span><span class="sxs-lookup"><span data-stu-id="7259b-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="7259b-196">Cancela la suscripción de los eventos InteractionSourceDetected y InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="7259b-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="7259b-197">A continuación, actualizaremos el cursor de la [entrada MR 210](holograms-210.md) a uno que muestra comentarios en función de las acciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="7259b-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="7259b-198">En el panel **jerarquía** , seleccione el objeto **cursor** y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="7259b-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="7259b-199">En el panel **proyecto** , busque **CursorWithFeedback** y arrástrelo al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="7259b-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="7259b-200">Haga clic en **InputManager** en el panel de **jerarquías** y, a continuación, arrastre el objeto **CursorWithFeedback** desde la **jerarquía** al campo **cursor** de **SimpleSinglePointerSelector**de InputManager, situado en la parte inferior de la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="7259b-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="7259b-201">Haga clic en **CursorWithFeedback** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="7259b-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="7259b-202">En el panel **Inspector** , expanda **datos de estado de cursor** en el script de cursor de **objeto** .</span><span class="sxs-lookup"><span data-stu-id="7259b-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="7259b-203">Los **datos de estado del cursor** funcionan de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="7259b-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="7259b-204">Cualquier estado **observado** significa que no se detecta ninguna mano y que el usuario simplemente está buscando.</span><span class="sxs-lookup"><span data-stu-id="7259b-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="7259b-205">Cualquier estado de **interacción** significa que se detecta una mano o un controlador.</span><span class="sxs-lookup"><span data-stu-id="7259b-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="7259b-206">Cualquier estado de **mantener el mouse** significa que el usuario está examinando un holograma.</span><span class="sxs-lookup"><span data-stu-id="7259b-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="7259b-207">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="7259b-207">Build and Deploy</span></span>

* <span data-ttu-id="7259b-208">En Unity, use la **configuración de compilación de > de archivos** para recompilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7259b-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="7259b-209">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="7259b-209">Open the **App** folder.</span></span>
* <span data-ttu-id="7259b-210">Si aún no está abierto, abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7259b-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="7259b-211">(Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "recargar todo" cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="7259b-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="7259b-212">En Visual Studio, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="7259b-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="7259b-213">Después de que la aplicación se implemente en HoloLens, descartará el fitbox con el gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="7259b-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="7259b-214">Mueva la mano a la vista y apunte el dedo del índice al cielo para iniciar el seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="7259b-215">Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="7259b-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="7259b-216">Observe cómo cambia el cursor cuando se detecta la mano y, a continuación, se pierde de la vista.</span><span class="sxs-lookup"><span data-stu-id="7259b-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="7259b-217">Si se encuentra en un casco envolvente, tendrá que conectar y desconectar el controlador.</span><span class="sxs-lookup"><span data-stu-id="7259b-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="7259b-218">Esta información es menos interesante en un dispositivo envolvente, ya que un controlador conectado siempre estará "disponible".</span><span class="sxs-lookup"><span data-stu-id="7259b-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="7259b-219">Capítulo 2: navegación</span><span class="sxs-lookup"><span data-stu-id="7259b-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="7259b-220">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7259b-220">Objectives</span></span>

* <span data-ttu-id="7259b-221">Use los eventos de gestos de navegación para rotar el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="7259b-222">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="7259b-222">Instructions</span></span>

<span data-ttu-id="7259b-223">Para usar los gestos de navegación en nuestra aplicación, vamos a editar **GestureAction.CS** para girar objetos cuando se produce el gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="7259b-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="7259b-224">Además, agregaremos comentarios al cursor para que se muestren cuando la navegación esté disponible.</span><span class="sxs-lookup"><span data-stu-id="7259b-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="7259b-225">En el panel **jerarquía** , expanda **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="7259b-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="7259b-226">En la carpeta hologramas, busque el recurso **ScrollFeedback** .</span><span class="sxs-lookup"><span data-stu-id="7259b-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="7259b-227">Arrastre y coloque el recurso prefabricado de **ScrollFeedback** en **CursorWithFeedback** GameObject en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="7259b-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="7259b-228">Haga clic en **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="7259b-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="7259b-229">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="7259b-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="7259b-230">En el menú, escriba en el cuadro de búsqueda **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="7259b-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="7259b-231">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-231">Select the search result.</span></span>
7. <span data-ttu-id="7259b-232">Arrastre y coloque el objeto **ScrollFeedback** de la **jerarquía** en la propiedad **desplazamiento de objeto de juego detectado** del componente **cursor feedback** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="7259b-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="7259b-233">En el panel **jerarquía** , seleccione el objeto **AstroMan** .</span><span class="sxs-lookup"><span data-stu-id="7259b-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="7259b-234">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="7259b-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="7259b-235">En el menú, escriba en la acción de **gestos**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="7259b-236">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-236">Select the search result.</span></span>

<span data-ttu-id="7259b-237">A continuación, Abra **GestureAction.CS** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7259b-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="7259b-238">En el ejercicio de codificación 2. c, edite el script para hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7259b-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="7259b-239">**Gire el objeto AstroMan** cada vez que se lleve a cabo un gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="7259b-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="7259b-240">Calcule el valor de **rotationFactor** para controlar la cantidad de giro aplicada al objeto.</span><span class="sxs-lookup"><span data-stu-id="7259b-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="7259b-241">**Gire el objeto** alrededor del eje y cuando el usuario mueva su mano a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="7259b-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="7259b-242">Complete los ejercicios de codificación 2. c en el script o reemplace el código por la solución completada que aparece a continuación:</span><span class="sxs-lookup"><span data-stu-id="7259b-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="7259b-243">Observará que los demás eventos de navegación ya se han rellenado con cierta información.</span><span class="sxs-lookup"><span data-stu-id="7259b-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="7259b-244">La GameObject se envía a la pila modal InputSystem's del kit de herramientas, por lo que el usuario no tiene que mantener el foco en el Astronaut una vez que se ha iniciado la rotación.</span><span class="sxs-lookup"><span data-stu-id="7259b-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="7259b-245">En consecuencia, se extrae el GameObject de la pila una vez que se completa el gesto.</span><span class="sxs-lookup"><span data-stu-id="7259b-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="7259b-246">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="7259b-246">Build and Deploy</span></span>

1. <span data-ttu-id="7259b-247">Vuelva a compilar la aplicación en Unity y, después, compile e implemente desde Visual Studio para ejecutarla en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7259b-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="7259b-248">Mira el Astronaut, dos flechas deben aparecer a cada lado del cursor.</span><span class="sxs-lookup"><span data-stu-id="7259b-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="7259b-249">Este nuevo visual indica que el Astronaut se puede girar.</span><span class="sxs-lookup"><span data-stu-id="7259b-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="7259b-250">Coloque la mano en la posición listo (el dedo índice apunta hacia el cielo) para que HoloLens empiece a realizar un seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="7259b-251">Para girar el Astronaut, baje el dedo del índice a una posición de pinch y, a continuación, mueva la mano hacia la izquierda o hacia la derecha para desencadenar el gesto de NavigationX.</span><span class="sxs-lookup"><span data-stu-id="7259b-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="7259b-252">Capítulo 3: orientación a mano</span><span class="sxs-lookup"><span data-stu-id="7259b-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="7259b-253">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7259b-253">Objectives</span></span>

* <span data-ttu-id="7259b-254">Use la puntuación de la **Guía de mano** para ayudar a predecir cuándo se perderá el seguimiento de manos.</span><span class="sxs-lookup"><span data-stu-id="7259b-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="7259b-255">Proporcione **comentarios sobre el cursor** para mostrar Cuándo el usuario está cerca del borde de la cámara de la vista.</span><span class="sxs-lookup"><span data-stu-id="7259b-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="7259b-256">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="7259b-256">Instructions</span></span>

1. <span data-ttu-id="7259b-257">En el panel **jerarquía** , seleccione el objeto **CursorWithFeedback** .</span><span class="sxs-lookup"><span data-stu-id="7259b-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="7259b-258">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="7259b-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="7259b-259">En el menú, escriba en la guía de **mano**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="7259b-260">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-260">Select the search result.</span></span>
4. <span data-ttu-id="7259b-261">En la carpeta **hologramas** del panel de **proyecto** , busque el recurso **HandGuidanceFeedback** .</span><span class="sxs-lookup"><span data-stu-id="7259b-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="7259b-262">Arrastre y coloque el recurso **HandGuidanceFeedback** en la propiedad **indicador de orientación a mano** del panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="7259b-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="7259b-263">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="7259b-263">Build and Deploy</span></span>

* <span data-ttu-id="7259b-264">Vuelva a compilar la aplicación en Unity y, después, compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7259b-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="7259b-265">Traiga su mano a la vista y eleve el dedo del índice para realizar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="7259b-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="7259b-266">Empiece a girar Astronaut con el gesto de navegación (acerque el dedo del índice y Thumb juntos).</span><span class="sxs-lookup"><span data-stu-id="7259b-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="7259b-267">Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="7259b-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="7259b-268">A medida que su mano esté cerca del borde del marco de gestos, debe aparecer una flecha junto al cursor para avisarle de que se perderá el seguimiento de la mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="7259b-269">La flecha indica la dirección a la que debe DESPLACESE para evitar que se pierda el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="7259b-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="7259b-270">Capítulo 4: manipulación</span><span class="sxs-lookup"><span data-stu-id="7259b-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="7259b-271">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7259b-271">Objectives</span></span>

* <span data-ttu-id="7259b-272">Use los eventos de manipulación para trasladar el Astronaut con las manos.</span><span class="sxs-lookup"><span data-stu-id="7259b-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="7259b-273">Proporcione comentarios sobre el cursor para que el usuario sepa cuándo se puede usar la manipulación.</span><span class="sxs-lookup"><span data-stu-id="7259b-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="7259b-274">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="7259b-274">Instructions</span></span>

<span data-ttu-id="7259b-275">GestureManager.cs y AstronautManager.cs nos permiten hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7259b-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="7259b-276">Use la palabra clave de voz "**Move Astronaut**" para habilitar los gestos de **manipulación** y "**rotar Astronaut**" para deshabilitarlos.</span><span class="sxs-lookup"><span data-stu-id="7259b-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="7259b-277">Cambie a responder al reconocedor de gestos de **manipulación**.</span><span class="sxs-lookup"><span data-stu-id="7259b-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="7259b-278">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="7259b-278">Let's get started.</span></span>

1. <span data-ttu-id="7259b-279">En el panel **jerarquía** , cree un nuevo GameObject vacío.</span><span class="sxs-lookup"><span data-stu-id="7259b-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="7259b-280">Asígnele el nombre "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="7259b-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="7259b-281">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="7259b-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="7259b-282">En el menú, escriba en el cuadro de búsqueda **Astronaut Manager**.</span><span class="sxs-lookup"><span data-stu-id="7259b-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="7259b-283">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-283">Select the search result.</span></span>
4. <span data-ttu-id="7259b-284">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="7259b-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="7259b-285">En el menú, escriba en el cuadro de búsqueda **origen de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="7259b-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="7259b-286">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-286">Select the search result.</span></span>

<span data-ttu-id="7259b-287">Ahora agregaremos los comandos de voz necesarios para controlar el estado de interacción de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="7259b-288">Expanda la sección **palabras clave** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="7259b-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="7259b-289">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="7259b-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="7259b-290">Escriba la palabra clave como **Move Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="7259b-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="7259b-291">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="7259b-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="7259b-292">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="7259b-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="7259b-293">Escriba la palabra clave como **rotar Astronaut**.</span><span class="sxs-lookup"><span data-stu-id="7259b-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="7259b-294">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="7259b-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="7259b-295">El código de controlador correspondiente se puede encontrar en **GestureAction.CS**, en el controlador **ISpeechHandler. OnSpeechKeywordRecognized** .</span><span class="sxs-lookup"><span data-stu-id="7259b-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Cómo configurar el origen de entrada de voz para el capítulo 4](images/holograms211-speech.png)

<span data-ttu-id="7259b-297">A continuación, configuraremos los comentarios de manipulación en el cursor.</span><span class="sxs-lookup"><span data-stu-id="7259b-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="7259b-298">En la carpeta **hologramas** del panel de **proyecto** , busque el recurso **PathingFeedback** .</span><span class="sxs-lookup"><span data-stu-id="7259b-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="7259b-299">Arrastre y coloque el recurso prefabricado **PathingFeedback** en el objeto **CursorWithFeedback** de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="7259b-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="7259b-300">En el panel **jerarquía** , haga clic en **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="7259b-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="7259b-301">Arrastre y coloque el objeto **PathingFeedback** de la **jerarquía** en la propiedad del **objeto de juego Thing detectado** del componente **cursor feedback** del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="7259b-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="7259b-302">Ahora debemos agregar código a **GestureAction.CS** para habilitar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7259b-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="7259b-303">Agregue código a la función **IManipulationHandler. OnManipulationUpdated** , que moverá el Astronaut cuando se detecte un gesto de **manipulación** .</span><span class="sxs-lookup"><span data-stu-id="7259b-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="7259b-304">Calcule el **Vector de movimiento** para determinar dónde se debe mover el Astronaut en función de la posición de la mano.</span><span class="sxs-lookup"><span data-stu-id="7259b-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="7259b-305">**Mueva** el Astronaut a la nueva posición.</span><span class="sxs-lookup"><span data-stu-id="7259b-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="7259b-306">Complete la codificación ejercicio 4. a en **GestureAction.CS**o use nuestra solución completada a continuación:</span><span class="sxs-lookup"><span data-stu-id="7259b-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="7259b-307">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="7259b-307">Build and Deploy</span></span>

* <span data-ttu-id="7259b-308">Recompile en Unity y, después, compile e implemente desde Visual Studio para ejecutar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7259b-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="7259b-309">Mueva la mano hacia delante de HoloLens y eleve el dedo del índice para que se pueda realizar el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="7259b-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="7259b-310">Centre el cursor sobre el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="7259b-311">Por ejemplo, "Move Astronaut" para trasladar Astronaut con un gesto de manipulación.</span><span class="sxs-lookup"><span data-stu-id="7259b-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="7259b-312">Deben aparecer cuatro flechas alrededor del cursor para indicar que el programa responderá ahora a los eventos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="7259b-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="7259b-313">Baje el dedo del índice hasta el pulgar y manténgalos reducidos juntos.</span><span class="sxs-lookup"><span data-stu-id="7259b-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="7259b-314">A medida que mueve la mano, el Astronaut se moverá también (esta es la manipulación).</span><span class="sxs-lookup"><span data-stu-id="7259b-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="7259b-315">Eleve el dedo del índice para dejar de manipular el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="7259b-316">Nota: Si no se indica "mover Astronaut" antes de mover la mano, se usará en su lugar el gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="7259b-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="7259b-317">Por ejemplo, "rotar Astronaut" para volver al estado Rotatable.</span><span class="sxs-lookup"><span data-stu-id="7259b-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="7259b-318">Capítulo 5: expansión del modelo</span><span class="sxs-lookup"><span data-stu-id="7259b-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="7259b-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7259b-319">Objectives</span></span>

* <span data-ttu-id="7259b-320">Expanda el modelo Astronaut en varias partes más pequeñas con las que el usuario pueda interactuar.</span><span class="sxs-lookup"><span data-stu-id="7259b-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="7259b-321">Mueva cada pieza individualmente mediante gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="7259b-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="7259b-322">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="7259b-322">Instructions</span></span>

<span data-ttu-id="7259b-323">En esta sección, se realizarán las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="7259b-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="7259b-324">Agregue una nueva palabra clave "**Expand Model**" para expandir el modelo Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="7259b-325">Agregue una nueva palabra clave "**RESET Model**" para devolver el modelo a su forma original.</span><span class="sxs-lookup"><span data-stu-id="7259b-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="7259b-326">Haremos esto agregando dos palabras clave más al origen de entrada de voz del capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="7259b-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="7259b-327">También mostraremos otra manera de controlar los eventos de reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="7259b-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="7259b-328">Haga clic en atrás en **AstronautManager** en el **Inspector** y expanda la sección **palabras clave** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="7259b-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="7259b-329">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="7259b-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="7259b-330">Escriba la palabra clave como **modelo de expansión**.</span><span class="sxs-lookup"><span data-stu-id="7259b-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="7259b-331">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="7259b-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="7259b-332">Haga clic **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="7259b-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="7259b-333">Escriba la palabra clave como **restablecer modelo**.</span><span class="sxs-lookup"><span data-stu-id="7259b-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="7259b-334">Si lo desea, no dude en agregar un método abreviado de teclado.</span><span class="sxs-lookup"><span data-stu-id="7259b-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="7259b-335">En el panel **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="7259b-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="7259b-336">En el menú, escriba en el cuadro de búsqueda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="7259b-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="7259b-337">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="7259b-337">Select the search result.</span></span>
8. <span data-ttu-id="7259b-338">Check **es el agente de escucha global**, ya que queremos que estos comandos funcionen independientemente de la GameObject a la que nos centramos.</span><span class="sxs-lookup"><span data-stu-id="7259b-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="7259b-339">Haga clic **+** en el botón y seleccione **expandir modelo** en la lista desplegable palabra clave.</span><span class="sxs-lookup"><span data-stu-id="7259b-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="7259b-340">Haga clic en en respuesta y arrastre el **AstronautManager** desde la **jerarquía** hasta el campo **ninguno (objeto).** **+**</span><span class="sxs-lookup"><span data-stu-id="7259b-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="7259b-341">Ahora, haga clic en la lista desplegable **no función** , seleccione **AstronautManager**y **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="7259b-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="7259b-342">Haga clic en el botón del **+** controlador de entrada de voz y seleccione **restablecer modelo** en la lista desplegable palabra clave.</span><span class="sxs-lookup"><span data-stu-id="7259b-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="7259b-343">Haga clic en en respuesta y arrastre el **AstronautManager** desde la **jerarquía** hasta el campo **ninguno (objeto).** **+**</span><span class="sxs-lookup"><span data-stu-id="7259b-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="7259b-344">Ahora, haga clic en la lista desplegable **no función** , seleccione **AstronautManager**y **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="7259b-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Cómo configurar el origen y el controlador de entrada de voz para el capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="7259b-346">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="7259b-346">Build and Deploy</span></span>

* <span data-ttu-id="7259b-347">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="7259b-347">Try it!</span></span> <span data-ttu-id="7259b-348">Compile e implemente la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7259b-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="7259b-349">Por ejemplo, **expanda modelo** para ver el modelo Astronaut expandido.</span><span class="sxs-lookup"><span data-stu-id="7259b-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="7259b-350">Use la **navegación** para girar partes individuales del palo de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="7259b-351">Por ejemplo, **mueva Astronaut** y, a continuación, use la **manipulación** para desplace partes individuales del palo de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="7259b-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="7259b-352">Por ejemplo, **gire Astronaut** para volver a girar las piezas.</span><span class="sxs-lookup"><span data-stu-id="7259b-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="7259b-353">Por ejemplo, **restablezca el modelo** para devolver el Astronaut a su forma original.</span><span class="sxs-lookup"><span data-stu-id="7259b-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="7259b-354">Fin</span><span class="sxs-lookup"><span data-stu-id="7259b-354">The End</span></span>

<span data-ttu-id="7259b-355">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="7259b-355">Congratulations!</span></span> <span data-ttu-id="7259b-356">Ya ha completado **la entrada Mr 211: Movimiento**.</span><span class="sxs-lookup"><span data-stu-id="7259b-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="7259b-357">Sabe cómo detectar y responder a los eventos de seguimiento, navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="7259b-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="7259b-358">Comprende la diferencia entre los gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="7259b-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="7259b-359">Sabe cómo cambiar el cursor para proporcionar comentarios visuales sobre cuándo se detecta una mano, Cuándo se va a perder una mano y cuándo un objeto admite distintas interacciones (navegación frente a manipulación).</span><span class="sxs-lookup"><span data-stu-id="7259b-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
