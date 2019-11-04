---
title: Entrada MR 212-voz
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, voz
ms.openlocfilehash: 9db503ea4c7db9a3eb272ad9663024ca3a407dda
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434600"
---
>[!NOTE]
><span data-ttu-id="d77d8-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="d77d8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d77d8-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d77d8-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d77d8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d77d8-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="d77d8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d77d8-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d77d8-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="d77d8-109">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="d77d8-109">MR Input 212: Voice</span></span>

<span data-ttu-id="d77d8-110">La [entrada de voz](voice-input.md) nos proporciona otro método para interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="d77d8-110">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="d77d8-111">Los comandos de voz funcionan de forma muy natural y sencilla.</span><span class="sxs-lookup"><span data-stu-id="d77d8-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="d77d8-112">Diseñe los comandos de voz para que estén:</span><span class="sxs-lookup"><span data-stu-id="d77d8-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="d77d8-113">Clásica</span><span class="sxs-lookup"><span data-stu-id="d77d8-113">Natural</span></span>
* <span data-ttu-id="d77d8-114">Fácil de recordar</span><span class="sxs-lookup"><span data-stu-id="d77d8-114">Easy to remember</span></span>
* <span data-ttu-id="d77d8-115">Contexto adecuado</span><span class="sxs-lookup"><span data-stu-id="d77d8-115">Context appropriate</span></span>
* <span data-ttu-id="d77d8-116">Lo suficientemente distinto de otras opciones en el mismo contexto</span><span class="sxs-lookup"><span data-stu-id="d77d8-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="d77d8-117">En los [conceptos básicos de MR 101](holograms-101.md), usamos KeywordRecognizer para crear dos sencillos comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-117">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="d77d8-118">En la entrada MR 212, profundizaremos más en cómo:</span><span class="sxs-lookup"><span data-stu-id="d77d8-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="d77d8-119">Diseñe comandos de voz que estén optimizados para el motor de voz de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d77d8-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="d77d8-120">Haga que el usuario tenga en cuenta qué comandos de voz están disponibles.</span><span class="sxs-lookup"><span data-stu-id="d77d8-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="d77d8-121">Confirme que hemos escuchado el comando de voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="d77d8-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="d77d8-122">Comprenda lo que está diciendo el usuario, mediante un reconocedor de dictado.</span><span class="sxs-lookup"><span data-stu-id="d77d8-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="d77d8-123">Use un reconocedor de gramática para escuchar comandos basados en un archivo SRGS o una especificación de gramática de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="d77d8-124">En este curso, volveremos a visitar el explorador de modelos, que hemos creado en la [entrada mr 210](holograms-210.md) y la [entrada Mr 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="d77d8-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="d77d8-125">Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d77d8-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d77d8-126">Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="d77d8-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="d77d8-127">Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="d77d8-128">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="d77d8-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d77d8-129">Recurso</span><span class="sxs-lookup"><span data-stu-id="d77d8-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d77d8-130"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d77d8-130"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d77d8-131"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="d77d8-131"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d77d8-132">Entrada MR 212: voz</span><span class="sxs-lookup"><span data-stu-id="d77d8-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="d77d8-133">✔️</span><span class="sxs-lookup"><span data-stu-id="d77d8-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d77d8-134">✔️</span><span class="sxs-lookup"><span data-stu-id="d77d8-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d77d8-135">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="d77d8-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d77d8-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="d77d8-136">Prerequisites</span></span>

* <span data-ttu-id="d77d8-137">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d77d8-137">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="d77d8-138">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="d77d8-139">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="d77d8-139">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="d77d8-140">Debe haber completado la [entrada MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="d77d8-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="d77d8-141">Debe haber completado la [entrada MR 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="d77d8-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="d77d8-142">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="d77d8-142">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="d77d8-143">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="d77d8-143">Project files</span></span>

* <span data-ttu-id="d77d8-144">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d77d8-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="d77d8-145">Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="d77d8-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="d77d8-146">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="d77d8-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="d77d8-147">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="d77d8-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="d77d8-148">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="d77d8-148">Errata and Notes</span></span>

* <span data-ttu-id="d77d8-149">"Habilitar Solo mi código" debe estar deshabilitado *(desactivado*) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="d77d8-149">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="d77d8-150">Configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="d77d8-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="d77d8-151">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d77d8-151">Instructions</span></span>

1. <span data-ttu-id="d77d8-152">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="d77d8-152">Start Unity.</span></span>
2. <span data-ttu-id="d77d8-153">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-153">Select **Open**.</span></span>
3. <span data-ttu-id="d77d8-154">Vaya a la carpeta **HolographicAcademy-hologramas-212-Voice** que previamente eliminó de archivado.</span><span class="sxs-lookup"><span data-stu-id="d77d8-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="d77d8-155">Busque y seleccione la carpeta **inicio**/**Explorador de modelos** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="d77d8-156">Haga clic en el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="d77d8-157">En el panel **proyecto** , expanda la carpeta **escenas** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="d77d8-158">Haga doble clic en **ModelExplorer** Scene para cargarlo en Unity.</span><span class="sxs-lookup"><span data-stu-id="d77d8-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="d77d8-159">Compilación</span><span class="sxs-lookup"><span data-stu-id="d77d8-159">Building</span></span>

1. <span data-ttu-id="d77d8-160">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-160">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="d77d8-161">Si **Scenes/ModelExplorer** no aparece en **escenas en la compilación**, haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="d77d8-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="d77d8-162">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="d77d8-163">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-163">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="d77d8-164">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="d77d8-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="d77d8-165">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-165">Click **Build**.</span></span>
6. <span data-ttu-id="d77d8-166">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="d77d8-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="d77d8-167">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="d77d8-168">Presione **Seleccionar carpeta** y Unity comenzará a compilar el proyecto para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d77d8-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="d77d8-169">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="d77d8-170">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="d77d8-171">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-171">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="d77d8-172">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="d77d8-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="d77d8-173">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="d77d8-174">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="d77d8-175">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="d77d8-176">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-176">Click **Select**.</span></span> <span data-ttu-id="d77d8-177">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="d77d8-178">En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="d77d8-179">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="d77d8-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="d77d8-180">Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="d77d8-181">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="d77d8-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="d77d8-182">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="d77d8-183">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-183">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="d77d8-184">En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="d77d8-185">Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="d77d8-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="d77d8-186">Es posible que observe algunos errores rojos en el panel de errores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d77d8-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="d77d8-187">Es seguro ignorarlos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-187">It is safe to ignore them.</span></span> <span data-ttu-id="d77d8-188">Cambie al panel de salida para ver el progreso real de la compilación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="d77d8-189">Los errores en el panel de salida requerirán que se realice una corrección (la mayoría de las veces se deben a un error en un script).</span><span class="sxs-lookup"><span data-stu-id="d77d8-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="d77d8-190">Capítulo 1: reconocimiento</span><span class="sxs-lookup"><span data-stu-id="d77d8-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="d77d8-191">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d77d8-191">Objectives</span></span>

* <span data-ttu-id="d77d8-192">Obtenga información sobre las **dos y no** el diseño de los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="d77d8-193">Use **KeywordRecognizer** para agregar comandos de voz basados en la mirada.</span><span class="sxs-lookup"><span data-stu-id="d77d8-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="d77d8-194">Hacer que los usuarios conozcan los comandos de voz mediante los **comentarios**del cursor.</span><span class="sxs-lookup"><span data-stu-id="d77d8-194">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="d77d8-195">Diseño de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="d77d8-195">Voice Command Design</span></span>

<span data-ttu-id="d77d8-196">En este capítulo, aprenderá a diseñar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="d77d8-197">Al crear comandos de voz:</span><span class="sxs-lookup"><span data-stu-id="d77d8-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="d77d8-198">DO</span><span class="sxs-lookup"><span data-stu-id="d77d8-198">DO</span></span>

* <span data-ttu-id="d77d8-199">Cree comandos concisos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-199">Create concise commands.</span></span> <span data-ttu-id="d77d8-200">No quiere usar *"reproducir el vídeo seleccionado actualmente"* , ya que ese comando no es conciso y el usuario lo olvidará fácilmente.</span><span class="sxs-lookup"><span data-stu-id="d77d8-200">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="d77d8-201">En su lugar, debe usar: *"reproducir vídeo"* , ya que es conciso y tiene varias sílabas.</span><span class="sxs-lookup"><span data-stu-id="d77d8-201">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="d77d8-202">Usar un vocabulario sencillo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-202">Use a simple vocabulary.</span></span> <span data-ttu-id="d77d8-203">Siempre intente usar palabras y frases comunes que resulten fáciles de detectar y recordar.</span><span class="sxs-lookup"><span data-stu-id="d77d8-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="d77d8-204">Por ejemplo, si la aplicación tenía un objeto de nota que se podría mostrar u ocultar en la vista, no usaría el comando *"show letrero"* , ya que "letrero" es un término que rara vez se usa.</span><span class="sxs-lookup"><span data-stu-id="d77d8-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="d77d8-205">En su lugar, usaría el comando: *"show Note"* para mostrar la nota en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-205">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="d77d8-206">Ser coherente.</span><span class="sxs-lookup"><span data-stu-id="d77d8-206">Be consistent.</span></span> <span data-ttu-id="d77d8-207">Los comandos de voz deben mantenerse coherentes en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="d77d8-208">Imagine que tiene dos escenas en la aplicación y ambas escenas contienen un botón para cerrar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="d77d8-209">Si la primera escena usó el comando *"salir"* para desencadenar el botón, pero la segunda escena usaba el comando *"cerrar aplicación"* , el usuario se quedará muy confundido.</span><span class="sxs-lookup"><span data-stu-id="d77d8-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="d77d8-210">Si la misma funcionalidad persiste en varias escenas, se debe usar el mismo comando de voz para desencadenarla.</span><span class="sxs-lookup"><span data-stu-id="d77d8-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="d77d8-211">No</span><span class="sxs-lookup"><span data-stu-id="d77d8-211">DON'T</span></span>

* <span data-ttu-id="d77d8-212">Use los comandos de una sola sílaba.</span><span class="sxs-lookup"><span data-stu-id="d77d8-212">Use single syllable commands.</span></span> <span data-ttu-id="d77d8-213">Por ejemplo, si estuviera creando un comando de voz para reproducir un vídeo, debe evitar el uso del comando simple *"Play"* , ya que es una sola sílaba y el sistema puede perderlo fácilmente.</span><span class="sxs-lookup"><span data-stu-id="d77d8-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="d77d8-214">En su lugar, debe usar: *"reproducir vídeo"* , ya que es conciso y tiene varias sílabas.</span><span class="sxs-lookup"><span data-stu-id="d77d8-214">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="d77d8-215">Usar comandos del sistema.</span><span class="sxs-lookup"><span data-stu-id="d77d8-215">Use system commands.</span></span> <span data-ttu-id="d77d8-216">El sistema reserva el comando *"Select"* para desencadenar un evento TAP para el objeto que tiene actualmente el foco.</span><span class="sxs-lookup"><span data-stu-id="d77d8-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="d77d8-217">No vuelva a usar el comando *"Select"* en una palabra clave o frase, ya que es posible que no funcione como se espera.</span><span class="sxs-lookup"><span data-stu-id="d77d8-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="d77d8-218">Por ejemplo, si el comando de voz para seleccionar un cubo en la aplicación fuera *"seleccionar cubo"* , pero el usuario estaba examinando una esfera cuando creó el comando, la esfera se seleccionaría en su lugar.</span><span class="sxs-lookup"><span data-stu-id="d77d8-218">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="d77d8-219">Igualmente, los comandos de la barra de la aplicación están habilitados para voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="d77d8-220">No use los siguientes comandos de voz en la vista de CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="d77d8-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="d77d8-221">Volver</span><span class="sxs-lookup"><span data-stu-id="d77d8-221">Go Back</span></span>
    2. <span data-ttu-id="d77d8-222">Herramienta de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="d77d8-222">Scroll Tool</span></span>
    3. <span data-ttu-id="d77d8-223">Herramienta de zoom</span><span class="sxs-lookup"><span data-stu-id="d77d8-223">Zoom Tool</span></span>
    4. <span data-ttu-id="d77d8-224">Herramienta de arrastre</span><span class="sxs-lookup"><span data-stu-id="d77d8-224">Drag Tool</span></span>
    5. <span data-ttu-id="d77d8-225">Ajustar</span><span class="sxs-lookup"><span data-stu-id="d77d8-225">Adjust</span></span>
    6. <span data-ttu-id="d77d8-226">Eliminar</span><span class="sxs-lookup"><span data-stu-id="d77d8-226">Remove</span></span>
* <span data-ttu-id="d77d8-227">Usar sonidos similares.</span><span class="sxs-lookup"><span data-stu-id="d77d8-227">Use similar sounds.</span></span> <span data-ttu-id="d77d8-228">Intente evitar el uso de comandos de voz que Rhyme.</span><span class="sxs-lookup"><span data-stu-id="d77d8-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="d77d8-229">Si tiene una aplicación de compras que admitía *"Mostrar tienda"* y *"Mostrar más"* como comandos de voz, querrá deshabilitar uno de los comandos mientras el otro estaba en uso.</span><span class="sxs-lookup"><span data-stu-id="d77d8-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="d77d8-230">Por ejemplo, puede usar el botón *"Mostrar tienda"* para abrir el almacén y, a continuación, deshabilitar ese comando cuando se mostró el almacén para que el comando *"Mostrar más"* pueda usarse para la exploración.</span><span class="sxs-lookup"><span data-stu-id="d77d8-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="d77d8-231">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d77d8-231">Instructions</span></span>

* <span data-ttu-id="d77d8-232">En el panel de **jerarquías** de Unity, use la herramienta de búsqueda para buscar el objeto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="d77d8-233">Haga doble clic en el objeto **holoComm_screen_mesh** para verlo en la **escena**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="d77d8-234">Esta es la inspección de Astronaut, que responderá a los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="d77d8-235">En el panel **Inspector** , busque el componente de **origen de entrada de voz (Script)** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="d77d8-236">Expanda la sección **palabras clave** para ver el comando de voz admitido: **Open Communicator**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="d77d8-237">Haga clic en engranaje en el lado derecho y, luego, seleccione **Editar script**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-237">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="d77d8-238">Explore **SpeechInputSource.CS** para saber cómo usa **KeywordRecognizer** para agregar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="d77d8-239">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="d77d8-239">Build and Deploy</span></span>

* <span data-ttu-id="d77d8-240">En Unity, use la **configuración de compilación de > de archivos** para recompilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="d77d8-241">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-241">Open the **App** folder.</span></span>
* <span data-ttu-id="d77d8-242">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-242">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="d77d8-243">(Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "recargar todo" cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="d77d8-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="d77d8-244">En Visual Studio, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="d77d8-245">Después de que la aplicación se implemente en HoloLens, descartará el cuadro de ajuste mediante el gesto [de punteo de aire](gaze-and-commit.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="d77d8-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="d77d8-246">Mira fijamente en la inspección de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d77d8-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="d77d8-247">Cuando el reloj tenga el foco, compruebe que el cursor cambia a un micrófono.</span><span class="sxs-lookup"><span data-stu-id="d77d8-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="d77d8-248">Esto proporciona comentarios que la aplicación está escuchando para los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="d77d8-249">Compruebe que aparece una información sobre herramientas en el reloj.</span><span class="sxs-lookup"><span data-stu-id="d77d8-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="d77d8-250">Esto ayuda a los usuarios a detectar el comando *"abrir Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="d77d8-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="d77d8-251">Mientras Gazing en el reloj, Imagine *"abrir Communicator"* para abrir el panel de Communicator.</span><span class="sxs-lookup"><span data-stu-id="d77d8-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="d77d8-252">Capítulo 2: confirmación</span><span class="sxs-lookup"><span data-stu-id="d77d8-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="d77d8-253">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d77d8-253">Objectives</span></span>

* <span data-ttu-id="d77d8-254">Grabe un mensaje mediante la entrada de micrófono.</span><span class="sxs-lookup"><span data-stu-id="d77d8-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="d77d8-255">Enviar comentarios al usuario que la aplicación está escuchando en la voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="d77d8-256">La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="d77d8-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="d77d8-257">Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="d77d8-258">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="d77d8-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d77d8-259">Haga clic en la pestaña "Plataforma universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="d77d8-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="d77d8-260">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d77d8-261">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d77d8-261">Instructions</span></span>

* <span data-ttu-id="d77d8-262">En el panel de **jerarquías** de Unity, compruebe que está seleccionado el objeto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="d77d8-263">En el panel **Inspector** , busque el componente **Astronaut Watch (Script)** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="d77d8-264">Haga clic en el pequeño cubo azul que se establece como el valor de la propiedad **Communicator recurso prefabricado** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="d77d8-265">En el panel **proyecto** , el recurso prefabricado de **Communicator** debería tener ahora el foco.</span><span class="sxs-lookup"><span data-stu-id="d77d8-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="d77d8-266">Haga clic en **Communicator** recurso prefabricado en el panel **proyecto** para ver sus componentes en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="d77d8-267">Fíjese en el componente **Administrador de micrófonos (Script)** , lo que nos permitirá grabar la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="d77d8-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="d77d8-268">Observe que el objeto **Communicator** tiene un componente de **controlador de entrada de voz (Script)** para responder al comando **send Message** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="d77d8-269">Fíjese en el componente **Communicator (Script)** y haga doble clic en el script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d77d8-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="d77d8-270">Communicator.cs es responsable de establecer los Estados de botón adecuados en el dispositivo Communicator.</span><span class="sxs-lookup"><span data-stu-id="d77d8-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="d77d8-271">Esto permitirá a los usuarios grabar un mensaje, reproducirlo y enviar el mensaje a Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d77d8-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="d77d8-272">También iniciará y detendrá un formulario de onda animada para confirmar al usuario que se ha escuchado su voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="d77d8-273">En **Communicator.CS**, elimine las líneas siguientes (81 y 82) del método **Start** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-273">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="d77d8-274">Esto habilitará el botón "registro" en Communicator.</span><span class="sxs-lookup"><span data-stu-id="d77d8-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="d77d8-275">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="d77d8-275">Build and Deploy</span></span>

* <span data-ttu-id="d77d8-276">En Visual Studio, vuelva a compilar la aplicación e implementarla en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="d77d8-277">Mira la inspección de Astronaut y di *"abrir Communicator"* para mostrar el Communicator.</span><span class="sxs-lookup"><span data-stu-id="d77d8-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="d77d8-278">Presione el botón **grabar** (micrófono) para iniciar la grabación de un mensaje verbal para el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d77d8-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="d77d8-279">Empiece a hablar y compruebe que la animación de onda se reproduce en Communicator, que proporciona comentarios al usuario de que se oye su voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="d77d8-280">Presione el botón **detener** (cuadrado izquierdo) y compruebe que la animación de onda deja de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="d77d8-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="d77d8-281">Presione el botón de **reproducción** (triángulo derecho) para reproducir el mensaje grabado y oír en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="d77d8-282">Presione el botón **detener** (cuadrado derecho) para detener la reproducción del mensaje grabado.</span><span class="sxs-lookup"><span data-stu-id="d77d8-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="d77d8-283">Por ejemplo, *"Enviar mensaje"* para cerrar Communicator y recibir una respuesta "mensaje recibido" de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d77d8-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="d77d8-284">Capítulo 3: Descripción y el reconocedor de dictado</span><span class="sxs-lookup"><span data-stu-id="d77d8-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="d77d8-285">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d77d8-285">Objectives</span></span>

* <span data-ttu-id="d77d8-286">Use el reconocedor de dictado para convertir la voz del usuario en texto.</span><span class="sxs-lookup"><span data-stu-id="d77d8-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="d77d8-287">Mostrar los resultados teóricos y finales del reconocedor de dictado en Communicator.</span><span class="sxs-lookup"><span data-stu-id="d77d8-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="d77d8-288">En este capítulo, usaremos el reconocedor de dictado para crear un mensaje para el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d77d8-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="d77d8-289">Al usar el reconocedor de dictado, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d77d8-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="d77d8-290">Debe estar conectado a la red Wi-Fi para que el reconocedor de dictado funcione.</span><span class="sxs-lookup"><span data-stu-id="d77d8-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="d77d8-291">Los tiempos de espera se producen después de un período de tiempo establecido.</span><span class="sxs-lookup"><span data-stu-id="d77d8-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="d77d8-292">Hay dos tiempos de espera que se deben tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="d77d8-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="d77d8-293">Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="d77d8-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="d77d8-294">Si el reconocedor ha dado un resultado pero oye el silencio durante veinte segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="d77d8-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="d77d8-295">Solo se puede ejecutar un tipo de reconocedor (palabra clave o dictado) a la vez.</span><span class="sxs-lookup"><span data-stu-id="d77d8-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="d77d8-296">La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="d77d8-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="d77d8-297">Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="d77d8-298">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="d77d8-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d77d8-299">Haga clic en la pestaña "Plataforma universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="d77d8-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="d77d8-300">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d77d8-301">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d77d8-301">Instructions</span></span>

<span data-ttu-id="d77d8-302">Vamos a editar **MicrophoneManager.CS** para usar el reconocedor de dictado.</span><span class="sxs-lookup"><span data-stu-id="d77d8-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="d77d8-303">Esto es lo que agregaremos:</span><span class="sxs-lookup"><span data-stu-id="d77d8-303">This is what we'll add:</span></span>

1. <span data-ttu-id="d77d8-304">Cuando se presiona el **botón grabar** , se **inicia el DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-304">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="d77d8-305">Mostrar la **hipótesis** de lo que DictationRecognizer entendió.</span><span class="sxs-lookup"><span data-stu-id="d77d8-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="d77d8-306">Bloquee los **resultados** de lo que DictationRecognizer entendió.</span><span class="sxs-lookup"><span data-stu-id="d77d8-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="d77d8-307">Compruebe los tiempos de espera de DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="d77d8-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="d77d8-308">Cuando se presiona el **botón detener** o se agota el tiempo de espera de la sesión MIC, **detenga el DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="d77d8-309">Reinicie **KeywordRecognizer**, que escuchará el comando **send Message** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-309">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="d77d8-310">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-310">Let's get started.</span></span> <span data-ttu-id="d77d8-311">Complete todos los ejercicios de codificación de 3. a en **MicrophoneManager.CS**, o copie y pegue el código finalizado que se encuentra a continuación:</span><span class="sxs-lookup"><span data-stu-id="d77d8-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="d77d8-312">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="d77d8-312">Build and Deploy</span></span>

* <span data-ttu-id="d77d8-313">Vuelva a compilar en Visual Studio e impleméntela en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="d77d8-314">Descartar el cuadro de ajuste con un gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="d77d8-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="d77d8-315">Mira el Astronaut y di *"abrir Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="d77d8-315">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="d77d8-316">Seleccione el botón **grabar** (micrófono) para grabar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="d77d8-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="d77d8-317">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="d77d8-317">Start speaking.</span></span> <span data-ttu-id="d77d8-318">El **reconocedor de dictado** interpretará su voz y mostrará el texto teórico en Communicator.</span><span class="sxs-lookup"><span data-stu-id="d77d8-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="d77d8-319">Intente decir *"Enviar mensaje"* mientras está grabando un mensaje.</span><span class="sxs-lookup"><span data-stu-id="d77d8-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="d77d8-320">Observe que el **reconocedor de palabras clave** no responde porque el **reconocedor de dictado** todavía está activo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="d77d8-321">Deje de hablar durante unos segundos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="d77d8-322">Observe que el reconocedor de dictado completa su hipótesis y muestra el resultado final.</span><span class="sxs-lookup"><span data-stu-id="d77d8-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="d77d8-323">Empiece a hablar y, a continuación, PAUSE durante 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="d77d8-324">Esto hará que el **reconocedor de dictado** agote el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="d77d8-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="d77d8-325">Tenga en cuenta que el **reconocedor de palabras clave** se vuelve a habilitar después del tiempo de espera anterior.</span><span class="sxs-lookup"><span data-stu-id="d77d8-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="d77d8-326">Communicator responderá ahora a los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="d77d8-327">Por ejemplo, *"Enviar mensaje"* para enviar el mensaje a Astronaut.</span><span class="sxs-lookup"><span data-stu-id="d77d8-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="d77d8-328">Capítulo 4: Reconocedor de gramática</span><span class="sxs-lookup"><span data-stu-id="d77d8-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="d77d8-329">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d77d8-329">Objectives</span></span>

* <span data-ttu-id="d77d8-330">Use el reconocedor de gramática para reconocer la voz del usuario de acuerdo con un archivo SRGS o una especificación de gramática de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="d77d8-331">La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="d77d8-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="d77d8-332">Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="d77d8-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="d77d8-333">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="d77d8-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d77d8-334">Haga clic en la pestaña "Plataforma universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="d77d8-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="d77d8-335">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d77d8-336">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d77d8-336">Instructions</span></span>

1. <span data-ttu-id="d77d8-337">En el panel **jerarquía** , busque **Jetpack_Center** y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="d77d8-338">Busque el script de **acción tagalong** en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="d77d8-339">Haga clic en el círculo pequeño situado a la derecha del **objeto para etiquetar a lo largo** del campo.</span><span class="sxs-lookup"><span data-stu-id="d77d8-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="d77d8-340">En la ventana que aparece, busque **SRGSToolbox** y selecciónela en la lista.</span><span class="sxs-lookup"><span data-stu-id="d77d8-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="d77d8-341">Eche un vistazo al archivo **SRGSColor. XML** de la carpeta **StreamingAssets** .</span><span class="sxs-lookup"><span data-stu-id="d77d8-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="d77d8-342">Las especificaciones de diseño de SRGS se pueden encontrar [aquí](https://www.w3.org/TR/speech-grammar/)en el sitio web de W3C.</span><span class="sxs-lookup"><span data-stu-id="d77d8-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="d77d8-343">En nuestro archivo SRGS, tenemos tres tipos de reglas:</span><span class="sxs-lookup"><span data-stu-id="d77d8-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="d77d8-344">Una regla que le permite decir un color de una lista de doce colores.</span><span class="sxs-lookup"><span data-stu-id="d77d8-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="d77d8-345">Tres reglas que escuchan una combinación de la regla de color y una de las tres formas.</span><span class="sxs-lookup"><span data-stu-id="d77d8-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="d77d8-346">La regla raíz, colorChooser, que escucha cualquier combinación de las tres reglas de "color + forma".</span><span class="sxs-lookup"><span data-stu-id="d77d8-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="d77d8-347">Las formas se pueden decir en cualquier orden y en cualquier cantidad de solo de una a las tres.</span><span class="sxs-lookup"><span data-stu-id="d77d8-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="d77d8-348">Esta es la única regla que se escucha, ya que se especifica como la regla raíz en la parte superior del archivo en la etiqueta inicial &lt;gramática&gt;.</span><span class="sxs-lookup"><span data-stu-id="d77d8-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="d77d8-349">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="d77d8-349">Build and Deploy</span></span>

* <span data-ttu-id="d77d8-350">Vuelva a compilar la aplicación en Unity y luego compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d77d8-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="d77d8-351">Descartar el cuadro de ajuste con un gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="d77d8-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="d77d8-352">Mira el jetpack del Astronaut y realiza un gesto de pulsación de aire.</span><span class="sxs-lookup"><span data-stu-id="d77d8-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="d77d8-353">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="d77d8-353">Start speaking.</span></span> <span data-ttu-id="d77d8-354">El **reconocedor de gramática** interpretará la voz y cambiará los colores de las formas en función del reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="d77d8-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="d77d8-355">Un comando de ejemplo es "círculo azul, cuadrado amarillo".</span><span class="sxs-lookup"><span data-stu-id="d77d8-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="d77d8-356">Realice otro gesto de punteo de aire para descartar el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="d77d8-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="d77d8-357">Fin</span><span class="sxs-lookup"><span data-stu-id="d77d8-357">The End</span></span>

<span data-ttu-id="d77d8-358">Enhorabuena.</span><span class="sxs-lookup"><span data-stu-id="d77d8-358">Congratulations!</span></span> <span data-ttu-id="d77d8-359">Ahora ha completado la **entrada MR 212: Voice**.</span><span class="sxs-lookup"><span data-stu-id="d77d8-359">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="d77d8-360">Conoce las dos y no los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="d77d8-361">Vio cómo se empleó la información sobre herramientas para que los usuarios conozcan los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="d77d8-362">Vio varios tipos de comentarios usados para confirmar que se ha escuchado la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="d77d8-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="d77d8-363">Sabe cómo cambiar entre el reconocedor de palabras clave y el reconocedor de dictado y cómo estas dos características entienden e interpretan la voz.</span><span class="sxs-lookup"><span data-stu-id="d77d8-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="d77d8-364">Ha aprendido a usar un archivo SRGS y el reconocedor de gramática para el reconocimiento de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d77d8-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
