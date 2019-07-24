---
title: Entrada MR 212-voz
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522354"
---
>[!NOTE]
><span data-ttu-id="8c562-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="8c562-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8c562-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8c562-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8c562-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8c562-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8c562-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="8c562-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8c562-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8c562-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8c562-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="8c562-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="8c562-110">Entrada MR 212: Voz</span><span class="sxs-lookup"><span data-stu-id="8c562-110">MR Input 212: Voice</span></span>

<span data-ttu-id="8c562-111">La [entrada de voz](voice-input.md) nos proporciona otro método para interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8c562-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="8c562-112">Los comandos de voz funcionan de forma muy natural y sencilla.</span><span class="sxs-lookup"><span data-stu-id="8c562-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="8c562-113">Diseñe los comandos de voz para que estén:</span><span class="sxs-lookup"><span data-stu-id="8c562-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="8c562-114">Clásica</span><span class="sxs-lookup"><span data-stu-id="8c562-114">Natural</span></span>
* <span data-ttu-id="8c562-115">Fácil de recordar</span><span class="sxs-lookup"><span data-stu-id="8c562-115">Easy to remember</span></span>
* <span data-ttu-id="8c562-116">Contexto adecuado</span><span class="sxs-lookup"><span data-stu-id="8c562-116">Context appropriate</span></span>
* <span data-ttu-id="8c562-117">Lo suficientemente distinto de otras opciones en el mismo contexto</span><span class="sxs-lookup"><span data-stu-id="8c562-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="8c562-118">En los [conceptos básicos de MR 101](holograms-101.md), usamos KeywordRecognizer para crear dos sencillos comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="8c562-119">En la entrada MR 212, profundizaremos más en cómo:</span><span class="sxs-lookup"><span data-stu-id="8c562-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="8c562-120">Diseñe comandos de voz que estén optimizados para el motor de voz de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c562-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="8c562-121">Haga que el usuario tenga en cuenta qué comandos de voz están disponibles.</span><span class="sxs-lookup"><span data-stu-id="8c562-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="8c562-122">Confirme que hemos escuchado el comando de voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="8c562-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="8c562-123">Comprenda lo que está diciendo el usuario, mediante un reconocedor de dictado.</span><span class="sxs-lookup"><span data-stu-id="8c562-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="8c562-124">Use un reconocedor de gramática para escuchar comandos basados en un archivo SRGS o una especificación de gramática de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="8c562-125">En este curso, volveremos a visitar el explorador de modelos, que hemos creado en la [entrada mr 210](holograms-210.md) y la [entrada Mr 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="8c562-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="8c562-126">Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8c562-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="8c562-127">Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="8c562-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="8c562-128">Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.</span><span class="sxs-lookup"><span data-stu-id="8c562-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="8c562-129">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="8c562-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8c562-130">Recurso</span><span class="sxs-lookup"><span data-stu-id="8c562-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8c562-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8c562-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8c562-132"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="8c562-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8c562-133">Entrada MR 212: Voz</span><span class="sxs-lookup"><span data-stu-id="8c562-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c562-134">✔️</span><span class="sxs-lookup"><span data-stu-id="8c562-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8c562-135">✔️</span><span class="sxs-lookup"><span data-stu-id="8c562-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8c562-136">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="8c562-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8c562-137">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="8c562-137">Prerequisites</span></span>

* <span data-ttu-id="8c562-138">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.</span><span class="sxs-lookup"><span data-stu-id="8c562-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="8c562-139">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="8c562-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="8c562-140">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="8c562-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="8c562-141">Debe haber completado la [entrada MR 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="8c562-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="8c562-142">Debe haber completado la [entrada MR 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="8c562-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="8c562-143">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="8c562-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="8c562-144">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="8c562-144">Project files</span></span>

* <span data-ttu-id="8c562-145">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="8c562-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="8c562-146">Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="8c562-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="8c562-147">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="8c562-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="8c562-148">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="8c562-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="8c562-149">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="8c562-149">Errata and Notes</span></span>

* <span data-ttu-id="8c562-150">"Habilitar Solo mi código" debe estar deshabilitado *(* desactivado) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="8c562-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="8c562-151">Configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="8c562-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="8c562-152">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8c562-152">Instructions</span></span>

1. <span data-ttu-id="8c562-153">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="8c562-153">Start Unity.</span></span>
2. <span data-ttu-id="8c562-154">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="8c562-154">Select **Open**.</span></span>
3. <span data-ttu-id="8c562-155">Vaya a la carpeta **HolographicAcademy-hologramas-212-Voice** que previamente eliminó de archivado.</span><span class="sxs-lookup"><span data-stu-id="8c562-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="8c562-156">Busque y seleccione la carpeta de **Inicio**/del**Explorador de modelos** .</span><span class="sxs-lookup"><span data-stu-id="8c562-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="8c562-157">Haga clic en el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="8c562-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="8c562-158">En el panel **proyecto** , expanda la carpeta **escenas** .</span><span class="sxs-lookup"><span data-stu-id="8c562-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="8c562-159">Haga doble clic en **ModelExplorer** Scene para cargarlo en Unity.</span><span class="sxs-lookup"><span data-stu-id="8c562-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="8c562-160">Compilación</span><span class="sxs-lookup"><span data-stu-id="8c562-160">Building</span></span>

1. <span data-ttu-id="8c562-161">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="8c562-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="8c562-162">Si **Scenes/ModelExplorer** no aparece en **escenas en la compilación**, haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="8c562-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="8c562-163">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="8c562-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="8c562-164">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="8c562-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="8c562-165">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="8c562-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="8c562-166">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="8c562-166">Click **Build**.</span></span>
6. <span data-ttu-id="8c562-167">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="8c562-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="8c562-168">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8c562-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="8c562-169">Presione **Seleccionar carpeta** y Unity comenzará a compilar el proyecto para Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c562-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="8c562-170">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="8c562-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="8c562-171">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8c562-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="8c562-172">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8c562-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="8c562-173">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="8c562-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="8c562-174">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="8c562-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="8c562-175">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="8c562-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="8c562-176">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="8c562-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="8c562-177">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="8c562-177">Click **Select**.</span></span> <span data-ttu-id="8c562-178">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="8c562-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="8c562-179">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8c562-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="8c562-180">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="8c562-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="8c562-181">Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.</span><span class="sxs-lookup"><span data-stu-id="8c562-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="8c562-182">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="8c562-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="8c562-183">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="8c562-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="8c562-184">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="8c562-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="8c562-185">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8c562-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="8c562-186">Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="8c562-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="8c562-187">Es posible que observe algunos errores rojos en el panel de errores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c562-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="8c562-188">Es seguro ignorarlos.</span><span class="sxs-lookup"><span data-stu-id="8c562-188">It is safe to ignore them.</span></span> <span data-ttu-id="8c562-189">Cambie al panel de salida para ver el progreso real de la compilación.</span><span class="sxs-lookup"><span data-stu-id="8c562-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="8c562-190">Los errores en el panel de salida requerirán que se realice una corrección (la mayoría de las veces se deben a un error en un script).</span><span class="sxs-lookup"><span data-stu-id="8c562-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="8c562-191">Capítulo 1: reconocimiento</span><span class="sxs-lookup"><span data-stu-id="8c562-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="8c562-192">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8c562-192">Objectives</span></span>

* <span data-ttu-id="8c562-193">Obtenga información sobre las **dos y no** el diseño de los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="8c562-194">Use **KeywordRecognizer** para agregar comandos de voz basados en la mirada.</span><span class="sxs-lookup"><span data-stu-id="8c562-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="8c562-195">Hacer que los usuarios conozcan los comandos de voz mediante los **comentarios**del cursor.</span><span class="sxs-lookup"><span data-stu-id="8c562-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="8c562-196">Diseño de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="8c562-196">Voice Command Design</span></span>

<span data-ttu-id="8c562-197">En este capítulo, aprenderá a diseñar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="8c562-198">Al crear comandos de voz:</span><span class="sxs-lookup"><span data-stu-id="8c562-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="8c562-199">DO</span><span class="sxs-lookup"><span data-stu-id="8c562-199">DO</span></span>

* <span data-ttu-id="8c562-200">Cree comandos concisos.</span><span class="sxs-lookup"><span data-stu-id="8c562-200">Create concise commands.</span></span> <span data-ttu-id="8c562-201">No quiere usar *"reproducir el vídeo seleccionado actualmente"* , ya que ese comando no es conciso y el usuario lo olvidará fácilmente.</span><span class="sxs-lookup"><span data-stu-id="8c562-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="8c562-202">En su lugar, debe usar: *"Reproducir vídeo"* , ya que es conciso y tiene varias sílabas.</span><span class="sxs-lookup"><span data-stu-id="8c562-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="8c562-203">Usar un vocabulario sencillo.</span><span class="sxs-lookup"><span data-stu-id="8c562-203">Use a simple vocabulary.</span></span> <span data-ttu-id="8c562-204">Siempre intente usar palabras y frases comunes que resulten fáciles de detectar y recordar.</span><span class="sxs-lookup"><span data-stu-id="8c562-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="8c562-205">Por ejemplo, si la aplicación tenía un objeto de nota que se podría mostrar u ocultar en la vista, no usaría el comando *"show letrero"* , ya que "letrero" es un término que rara vez se usa.</span><span class="sxs-lookup"><span data-stu-id="8c562-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="8c562-206">En su lugar, usaría el comando: *"Mostrar nota"* para mostrar la nota en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8c562-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="8c562-207">Ser coherente.</span><span class="sxs-lookup"><span data-stu-id="8c562-207">Be consistent.</span></span> <span data-ttu-id="8c562-208">Los comandos de voz deben mantenerse coherentes en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8c562-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="8c562-209">Imagine que tiene dos escenas en la aplicación y ambas escenas contienen un botón para cerrar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8c562-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="8c562-210">Si la primera escena usó el comando *"salir"* para desencadenar el botón, pero la segunda escena usaba el comando *"cerrar aplicación"* , el usuario se quedará muy confundido.</span><span class="sxs-lookup"><span data-stu-id="8c562-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="8c562-211">Si la misma funcionalidad persiste en varias escenas, se debe usar el mismo comando de voz para desencadenarla.</span><span class="sxs-lookup"><span data-stu-id="8c562-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="8c562-212">NO</span><span class="sxs-lookup"><span data-stu-id="8c562-212">DON'T</span></span>

* <span data-ttu-id="8c562-213">Use los comandos de una sola sílaba.</span><span class="sxs-lookup"><span data-stu-id="8c562-213">Use single syllable commands.</span></span> <span data-ttu-id="8c562-214">Por ejemplo, si estuviera creando un comando de voz para reproducir un vídeo, debe evitar el uso del comando simple *"Play"* , ya que es una sola sílaba y el sistema puede perderlo fácilmente.</span><span class="sxs-lookup"><span data-stu-id="8c562-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="8c562-215">En su lugar, debe usar: *"Reproducir vídeo"* , ya que es conciso y tiene varias sílabas.</span><span class="sxs-lookup"><span data-stu-id="8c562-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="8c562-216">Usar comandos del sistema.</span><span class="sxs-lookup"><span data-stu-id="8c562-216">Use system commands.</span></span> <span data-ttu-id="8c562-217">El sistema reserva el comando *"Select"* para desencadenar un evento TAP para el objeto que tiene actualmente el foco.</span><span class="sxs-lookup"><span data-stu-id="8c562-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="8c562-218">No vuelva a usar el comando *"Select"* en una palabra clave o frase, ya que es posible que no funcione como se espera.</span><span class="sxs-lookup"><span data-stu-id="8c562-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="8c562-219">Por ejemplo, si el comando de voz para seleccionar un cubo en la aplicación fuera *"seleccionar cubo"* , pero el usuario estaba examinando una esfera cuando creó el comando, la esfera se seleccionaría en su lugar.</span><span class="sxs-lookup"><span data-stu-id="8c562-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="8c562-220">Igualmente, los comandos de la barra de la aplicación están habilitados para voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="8c562-221">No use los siguientes comandos de voz en la vista de CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="8c562-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="8c562-222">Volver</span><span class="sxs-lookup"><span data-stu-id="8c562-222">Go Back</span></span>
    2. <span data-ttu-id="8c562-223">Herramienta de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="8c562-223">Scroll Tool</span></span>
    3. <span data-ttu-id="8c562-224">Herramienta de zoom</span><span class="sxs-lookup"><span data-stu-id="8c562-224">Zoom Tool</span></span>
    4. <span data-ttu-id="8c562-225">Herramienta de arrastre</span><span class="sxs-lookup"><span data-stu-id="8c562-225">Drag Tool</span></span>
    5. <span data-ttu-id="8c562-226">Ajustar</span><span class="sxs-lookup"><span data-stu-id="8c562-226">Adjust</span></span>
    6. <span data-ttu-id="8c562-227">Eliminar</span><span class="sxs-lookup"><span data-stu-id="8c562-227">Remove</span></span>
* <span data-ttu-id="8c562-228">Usar sonidos similares.</span><span class="sxs-lookup"><span data-stu-id="8c562-228">Use similar sounds.</span></span> <span data-ttu-id="8c562-229">Intente evitar el uso de comandos de voz que Rhyme.</span><span class="sxs-lookup"><span data-stu-id="8c562-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="8c562-230">Si tiene una aplicación de compras que admitía *"Mostrar tienda"* y *"Mostrar más"* como comandos de voz, querrá deshabilitar uno de los comandos mientras el otro estaba en uso.</span><span class="sxs-lookup"><span data-stu-id="8c562-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="8c562-231">Por ejemplo, puede usar el botón *"Mostrar tienda"* para abrir el almacén y, a continuación, deshabilitar ese comando cuando se mostró el almacén para que el comando *"Mostrar más"* pueda usarse para la exploración.</span><span class="sxs-lookup"><span data-stu-id="8c562-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="8c562-232">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8c562-232">Instructions</span></span>

* <span data-ttu-id="8c562-233">En el panel  de jerarquías de Unity, use la herramienta de búsqueda para buscar el objeto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="8c562-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="8c562-234">Haga doble clic en el objeto **holoComm_screen_mesh** para verlo en la **escena**.</span><span class="sxs-lookup"><span data-stu-id="8c562-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="8c562-235">Esta es la inspección de Astronaut, que responderá a los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="8c562-236">En el panel **Inspector** , busque el componente de **origen de entrada de voz (Script)** .</span><span class="sxs-lookup"><span data-stu-id="8c562-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="8c562-237">Expanda la sección **palabras clave** para ver el comando de voz admitido: **Abra Communicator**.</span><span class="sxs-lookup"><span data-stu-id="8c562-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="8c562-238">Haga clic en engranaje en el lado derecho y, luego, seleccione **Editar script**.</span><span class="sxs-lookup"><span data-stu-id="8c562-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="8c562-239">Explore **SpeechInputSource.CS** para saber cómo usa **KeywordRecognizer** para agregar comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="8c562-240">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8c562-240">Build and Deploy</span></span>

* <span data-ttu-id="8c562-241">En Unity, use la **configuración de compilación de > de archivos** para recompilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8c562-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="8c562-242">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8c562-242">Open the **App** folder.</span></span>
* <span data-ttu-id="8c562-243">Abra la **solución ModelExplorer de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="8c562-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="8c562-244">(Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "recargar todo" cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="8c562-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="8c562-245">En Visual Studio, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8c562-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="8c562-246">Después de que la aplicación se implemente en HoloLens, descartará el cuadro de ajuste mediante el gesto [de punteo de aire](gestures.md#air-tap) .</span><span class="sxs-lookup"><span data-stu-id="8c562-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="8c562-247">Mira fijamente en la inspección de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8c562-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="8c562-248">Cuando el reloj tenga el foco, compruebe que el cursor cambia a un micrófono.</span><span class="sxs-lookup"><span data-stu-id="8c562-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="8c562-249">Esto proporciona comentarios que la aplicación está escuchando para los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="8c562-250">Compruebe que aparece una información sobre herramientas en el reloj.</span><span class="sxs-lookup"><span data-stu-id="8c562-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="8c562-251">Esto ayuda a los usuarios a detectar el comando *"abrir Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="8c562-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="8c562-252">Mientras Gazing en el reloj, Imagine *"abrir Communicator"* para abrir el panel de Communicator.</span><span class="sxs-lookup"><span data-stu-id="8c562-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="8c562-253">Capítulo 2: confirmación</span><span class="sxs-lookup"><span data-stu-id="8c562-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="8c562-254">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8c562-254">Objectives</span></span>

* <span data-ttu-id="8c562-255">Grabe un mensaje mediante la entrada de micrófono.</span><span class="sxs-lookup"><span data-stu-id="8c562-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="8c562-256">Enviar comentarios al usuario que la aplicación está escuchando en la voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="8c562-257">La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="8c562-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="8c562-258">Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="8c562-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="8c562-259">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="8c562-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="8c562-260">Haga clic en la pestaña "Plataforma universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="8c562-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="8c562-261">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="8c562-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="8c562-262">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8c562-262">Instructions</span></span>

* <span data-ttu-id="8c562-263">En el panel  de jerarquías de Unity, compruebe que está seleccionado el objeto **holoComm_screen_mesh** .</span><span class="sxs-lookup"><span data-stu-id="8c562-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="8c562-264">En el panel **Inspector** , busque el componente **Astronaut Watch (Script)** .</span><span class="sxs-lookup"><span data-stu-id="8c562-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="8c562-265">Haga clic en el pequeño cubo azul que se establece como el valor de la propiedad **Communicator recurso prefabricado** .</span><span class="sxs-lookup"><span data-stu-id="8c562-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="8c562-266">En el panel **proyecto** , el recurso prefabricado de **Communicator** debería tener ahora el foco.</span><span class="sxs-lookup"><span data-stu-id="8c562-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="8c562-267">Haga clic en **Communicator** recurso prefabricado en el panel **proyecto** para ver sus componentes en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="8c562-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="8c562-268">Fíjese en el componente **Administrador de micrófonos (Script)** , lo que nos permitirá grabar la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="8c562-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="8c562-269">Observe que el objeto **Communicator** tiene un componente de **controlador de entrada de voz (Script)** para responder al comando **send Message** .</span><span class="sxs-lookup"><span data-stu-id="8c562-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="8c562-270">Fíjese en el componente **Communicator (Script)** y haga doble clic en el script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c562-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="8c562-271">Communicator.cs es responsable de establecer los Estados de botón adecuados en el dispositivo Communicator.</span><span class="sxs-lookup"><span data-stu-id="8c562-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="8c562-272">Esto permitirá a los usuarios grabar un mensaje, reproducirlo y enviar el mensaje a Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8c562-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="8c562-273">También iniciará y detendrá un formulario de onda animada para confirmar al usuario que se ha escuchado su voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="8c562-274">En **Communicator.CS**, elimine las líneas siguientes (81 y 82) del método **Start** .</span><span class="sxs-lookup"><span data-stu-id="8c562-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="8c562-275">Esto habilitará el botón "registro" en Communicator.</span><span class="sxs-lookup"><span data-stu-id="8c562-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="8c562-276">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8c562-276">Build and Deploy</span></span>

* <span data-ttu-id="8c562-277">En Visual Studio, vuelva a compilar la aplicación e implementarla en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8c562-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="8c562-278">Mira la inspección de Astronaut y di *"abrir Communicator"* para mostrar el Communicator.</span><span class="sxs-lookup"><span data-stu-id="8c562-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="8c562-279">Presione el botón **grabar** (micrófono) para iniciar la grabación de un mensaje verbal para el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8c562-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="8c562-280">Empiece a hablar y compruebe que la animación de onda se reproduce en Communicator, que proporciona comentarios al usuario de que se oye su voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="8c562-281">Presione el botón **detener** (cuadrado izquierdo) y compruebe que la animación de onda deja de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="8c562-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="8c562-282">Presione el botón de **reproducción** (triángulo derecho) para reproducir el mensaje grabado y oír en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8c562-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="8c562-283">Presione el botón **detener** (cuadrado derecho) para detener la reproducción del mensaje grabado.</span><span class="sxs-lookup"><span data-stu-id="8c562-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="8c562-284">Por ejemplo, *"Enviar mensaje"* para cerrar Communicator y recibir una respuesta "mensaje recibido" de Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8c562-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="8c562-285">Capítulo 3: Descripción y el reconocedor de dictado</span><span class="sxs-lookup"><span data-stu-id="8c562-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="8c562-286">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8c562-286">Objectives</span></span>

* <span data-ttu-id="8c562-287">Use el reconocedor de dictado para convertir la voz del usuario en texto.</span><span class="sxs-lookup"><span data-stu-id="8c562-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="8c562-288">Mostrar los resultados teóricos y finales del reconocedor de dictado en Communicator.</span><span class="sxs-lookup"><span data-stu-id="8c562-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="8c562-289">En este capítulo, usaremos el reconocedor de dictado para crear un mensaje para el Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8c562-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="8c562-290">Al usar el reconocedor de dictado, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8c562-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="8c562-291">Debe estar conectado a la red Wi-Fi para que el reconocedor de dictado funcione.</span><span class="sxs-lookup"><span data-stu-id="8c562-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="8c562-292">Los tiempos de espera se producen después de un período de tiempo establecido.</span><span class="sxs-lookup"><span data-stu-id="8c562-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="8c562-293">Hay dos tiempos de espera que se deben tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="8c562-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="8c562-294">Si el reconocedor se inicia y no oye ningún audio durante los primeros cinco segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="8c562-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="8c562-295">Si el reconocedor ha dado un resultado pero oye el silencio durante veinte segundos, se agotará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="8c562-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="8c562-296">Solo se puede ejecutar un tipo de reconocedor (palabra clave o dictado) a la vez.</span><span class="sxs-lookup"><span data-stu-id="8c562-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="8c562-297">La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="8c562-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="8c562-298">Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="8c562-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="8c562-299">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="8c562-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="8c562-300">Haga clic en la pestaña "Plataforma universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="8c562-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="8c562-301">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="8c562-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="8c562-302">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8c562-302">Instructions</span></span>

<span data-ttu-id="8c562-303">Vamos a editar **MicrophoneManager.CS** para usar el reconocedor de dictado.</span><span class="sxs-lookup"><span data-stu-id="8c562-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="8c562-304">Esto es lo que agregaremos:</span><span class="sxs-lookup"><span data-stu-id="8c562-304">This is what we'll add:</span></span>

1. <span data-ttu-id="8c562-305">Cuando se presiona el **botón grabar** , se **inicia el DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="8c562-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="8c562-306">Mostrar la **hipótesis** de lo que DictationRecognizer entendió.</span><span class="sxs-lookup"><span data-stu-id="8c562-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="8c562-307">Bloquee los **resultados** de lo que DictationRecognizer entendió.</span><span class="sxs-lookup"><span data-stu-id="8c562-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="8c562-308">Compruebe los tiempos de espera de DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="8c562-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="8c562-309">Cuando se presiona el **botón detener** o se agota el tiempo de espera de la sesión MIC, **detenga el DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="8c562-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="8c562-310">Reinicie **KeywordRecognizer**, que escuchará el comando **send Message** .</span><span class="sxs-lookup"><span data-stu-id="8c562-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="8c562-311">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="8c562-311">Let's get started.</span></span> <span data-ttu-id="8c562-312">Complete todos los ejercicios de codificación de 3. a en **MicrophoneManager.CS**, o copie y pegue el código finalizado que se encuentra a continuación:</span><span class="sxs-lookup"><span data-stu-id="8c562-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="8c562-313">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8c562-313">Build and Deploy</span></span>

* <span data-ttu-id="8c562-314">Vuelva a compilar en Visual Studio e impleméntela en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8c562-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="8c562-315">Descartar el cuadro de ajuste con un gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="8c562-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="8c562-316">Mira el Astronaut y di *"abrir Communicator"* .</span><span class="sxs-lookup"><span data-stu-id="8c562-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="8c562-317">Seleccione el botón **grabar** (micrófono) para grabar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="8c562-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="8c562-318">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="8c562-318">Start speaking.</span></span> <span data-ttu-id="8c562-319">El  reconocedor de dictado interpretará su voz y mostrará el texto teórico en Communicator.</span><span class="sxs-lookup"><span data-stu-id="8c562-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="8c562-320">Intente decir *"Enviar mensaje"* mientras está grabando un mensaje.</span><span class="sxs-lookup"><span data-stu-id="8c562-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="8c562-321">Observe que el reconocedor de **palabras clave** no responde  porque el reconocedor de dictado todavía está activo.</span><span class="sxs-lookup"><span data-stu-id="8c562-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="8c562-322">Deje de hablar durante unos segundos.</span><span class="sxs-lookup"><span data-stu-id="8c562-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="8c562-323">Observe que el reconocedor de dictado completa su hipótesis y muestra el resultado final.</span><span class="sxs-lookup"><span data-stu-id="8c562-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="8c562-324">Empiece a hablar y, a continuación, PAUSE durante 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="8c562-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="8c562-325">Esto hará que el  reconocedor de dictado agote el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="8c562-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="8c562-326">Tenga en cuenta que el reconocedor de **palabras clave** se vuelve a habilitar después del tiempo de espera anterior.</span><span class="sxs-lookup"><span data-stu-id="8c562-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="8c562-327">Communicator responderá ahora a los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="8c562-328">Por ejemplo, *"Enviar mensaje"* para enviar el mensaje a Astronaut.</span><span class="sxs-lookup"><span data-stu-id="8c562-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="8c562-329">Capítulo 4: Reconocedor de gramática</span><span class="sxs-lookup"><span data-stu-id="8c562-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="8c562-330">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8c562-330">Objectives</span></span>

* <span data-ttu-id="8c562-331">Use el reconocedor de gramática para reconocer la voz del usuario de acuerdo con un archivo SRGS o una especificación de gramática de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="8c562-332">La capacidad del **micrófono** se debe declarar para que una aplicación se grabe desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="8c562-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="8c562-333">Esto se hace ya en la entrada MR 212, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="8c562-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="8c562-334">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="8c562-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="8c562-335">Haga clic en la pestaña "Plataforma universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="8c562-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="8c562-336">En la sección "configuración de publicación > funcionalidades", Compruebe la capacidad del **micrófono** .</span><span class="sxs-lookup"><span data-stu-id="8c562-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="8c562-337">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8c562-337">Instructions</span></span>

1. <span data-ttu-id="8c562-338">En el panel **jerarquía** , busque **Jetpack_Center** y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="8c562-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="8c562-339">Busque el script de **acción tagalong** en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="8c562-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="8c562-340">Haga clic en el círculo pequeño situado a la derecha del **objeto para etiquetar a lo largo** del campo.</span><span class="sxs-lookup"><span data-stu-id="8c562-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="8c562-341">En la ventana que aparece, busque **SRGSToolbox** y selecciónela en la lista.</span><span class="sxs-lookup"><span data-stu-id="8c562-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="8c562-342">Eche un vistazo al archivo **SRGSColor. XML** de la carpeta **StreamingAssets** .</span><span class="sxs-lookup"><span data-stu-id="8c562-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="8c562-343">Las especificaciones de diseño de SRGS se pueden encontrar [aquí](https://www.w3.org/TR/speech-grammar/)en el sitio web de W3C.</span><span class="sxs-lookup"><span data-stu-id="8c562-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="8c562-344">En nuestro archivo SRGS, tenemos tres tipos de reglas:</span><span class="sxs-lookup"><span data-stu-id="8c562-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="8c562-345">Una regla que le permite decir un color de una lista de doce colores.</span><span class="sxs-lookup"><span data-stu-id="8c562-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="8c562-346">Tres reglas que escuchan una combinación de la regla de color y una de las tres formas.</span><span class="sxs-lookup"><span data-stu-id="8c562-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="8c562-347">La regla raíz, colorChooser, que escucha cualquier combinación de las tres reglas de "color + forma".</span><span class="sxs-lookup"><span data-stu-id="8c562-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="8c562-348">Las formas se pueden decir en cualquier orden y en cualquier cantidad de solo de una a las tres.</span><span class="sxs-lookup"><span data-stu-id="8c562-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="8c562-349">Esta es la única regla que se escucha, ya que se especifica como la regla raíz en la parte superior del archivo en la etiqueta de &lt;gramática&gt; inicial.</span><span class="sxs-lookup"><span data-stu-id="8c562-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="8c562-350">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8c562-350">Build and Deploy</span></span>

* <span data-ttu-id="8c562-351">Vuelva a compilar la aplicación en Unity y luego compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c562-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="8c562-352">Descartar el cuadro de ajuste con un gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="8c562-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="8c562-353">Mira el jetpack del Astronaut y realiza un gesto de pulsación de aire.</span><span class="sxs-lookup"><span data-stu-id="8c562-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="8c562-354">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="8c562-354">Start speaking.</span></span> <span data-ttu-id="8c562-355">El reconocedor de **gramática** interpretará la voz y cambiará los colores de las formas en función del reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="8c562-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="8c562-356">Un comando de ejemplo es "círculo azul, cuadrado amarillo".</span><span class="sxs-lookup"><span data-stu-id="8c562-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="8c562-357">Realice otro gesto de punteo de aire para descartar el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="8c562-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="8c562-358">Fin</span><span class="sxs-lookup"><span data-stu-id="8c562-358">The End</span></span>

<span data-ttu-id="8c562-359">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="8c562-359">Congratulations!</span></span> <span data-ttu-id="8c562-360">Ya ha completado **la entrada Mr 212: Voz**.</span><span class="sxs-lookup"><span data-stu-id="8c562-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="8c562-361">Conoce las dos y no los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="8c562-362">Vio cómo se empleó la información sobre herramientas para que los usuarios conozcan los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="8c562-363">Vio varios tipos de comentarios usados para confirmar que se ha escuchado la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="8c562-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="8c562-364">Sabe cómo cambiar entre el reconocedor de palabras clave y el reconocedor de dictado y cómo estas dos características entienden e interpretan la voz.</span><span class="sxs-lookup"><span data-stu-id="8c562-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="8c562-365">Ha aprendido a usar un archivo SRGS y el reconocedor de gramática para el reconocimiento de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8c562-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
