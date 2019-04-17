---
title: Entrada MR 212 - voz
description: Siga este tutorial de programación con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial de voz
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598927"
---
>[!NOTE]
><span data-ttu-id="6de14-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="6de14-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="6de14-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6de14-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="6de14-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="6de14-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="6de14-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="6de14-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="6de14-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6de14-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="6de14-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="6de14-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-212-voice"></a><span data-ttu-id="6de14-110">Entrada MR 212: Voz</span><span class="sxs-lookup"><span data-stu-id="6de14-110">MR Input 212: Voice</span></span>

<span data-ttu-id="6de14-111">[Entrada de voz](voice-input.md) nos proporciona otra manera de interactuar con nuestra hologramas.</span><span class="sxs-lookup"><span data-stu-id="6de14-111">[Voice input](voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="6de14-112">Los comandos de voz funcionan de manera muy fácil y natural.</span><span class="sxs-lookup"><span data-stu-id="6de14-112">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="6de14-113">Diseñar los comandos de voz para que sean:</span><span class="sxs-lookup"><span data-stu-id="6de14-113">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="6de14-114">Natural</span><span class="sxs-lookup"><span data-stu-id="6de14-114">Natural</span></span>
* <span data-ttu-id="6de14-115">Fácil de recordar</span><span class="sxs-lookup"><span data-stu-id="6de14-115">Easy to remember</span></span>
* <span data-ttu-id="6de14-116">Contexto adecuado</span><span class="sxs-lookup"><span data-stu-id="6de14-116">Context appropriate</span></span>
* <span data-ttu-id="6de14-117">Suficientemente distintos de otras opciones en el mismo contexto</span><span class="sxs-lookup"><span data-stu-id="6de14-117">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="6de14-118">En [MR Fundamentos 101](holograms-101.md), hemos usado el KeywordRecognizer para generar dos comandos de voz simple.</span><span class="sxs-lookup"><span data-stu-id="6de14-118">In [MR Basics 101](holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="6de14-119">En MR 212 de entrada, crearemos profundizar más y obtenga información sobre cómo:</span><span class="sxs-lookup"><span data-stu-id="6de14-119">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="6de14-120">Comandos de voz de diseño que están optimizados para el motor de voz de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6de14-120">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="6de14-121">Hacer que al usuario sea consciente de voz en qué comandos están disponibles.</span><span class="sxs-lookup"><span data-stu-id="6de14-121">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="6de14-122">Confirmar que hemos oído comandos de voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="6de14-122">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="6de14-123">Comprenda qué es el usuario que indica que, mediante un módulo de reconocimiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="6de14-123">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="6de14-124">Utilice un reconocedor de gramática para escuchar comandos basados en un archivo de SRGS o especificación de gramática de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-124">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="6de14-125">En este curso, volveremos a Explorador de modelos, que se basa en [MR entrada 210](holograms-210.md) y [MR entrada 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="6de14-125">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="6de14-126">Los vídeos insertados en cada uno de los siguientes capítulos se guardó usando una versión anterior de Unity y el Kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6de14-126">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="6de14-127">Aunque las instrucciones paso a paso son actuales y precisas, puede ver las secuencias de comandos y los objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="6de14-127">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="6de14-128">Los vídeos permanecen incluidos para la posterioridad y porque se tratan los conceptos se siguen aplican.</span><span class="sxs-lookup"><span data-stu-id="6de14-128">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="6de14-129">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="6de14-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6de14-130">Curso</span><span class="sxs-lookup"><span data-stu-id="6de14-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="6de14-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6de14-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6de14-132"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="6de14-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="6de14-133">Entrada MR 212: Voz</span><span class="sxs-lookup"><span data-stu-id="6de14-133">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="6de14-134">✔️</span><span class="sxs-lookup"><span data-stu-id="6de14-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6de14-135">✔️</span><span class="sxs-lookup"><span data-stu-id="6de14-135">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="6de14-136">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="6de14-136">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6de14-137">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="6de14-137">Prerequisites</span></span>

* <span data-ttu-id="6de14-138">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6de14-138">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="6de14-139">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="6de14-139">Some basic C# programming ability.</span></span>
* <span data-ttu-id="6de14-140">Debe haber completado [MR Fundamentos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="6de14-140">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="6de14-141">Debe haber completado [MR entrada 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="6de14-141">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="6de14-142">Debe haber completado [MR entrada 211](holograms-211.md).</span><span class="sxs-lookup"><span data-stu-id="6de14-142">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="6de14-143">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="6de14-143">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="6de14-144">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="6de14-144">Project files</span></span>

* <span data-ttu-id="6de14-145">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="6de14-145">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="6de14-146">Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="6de14-146">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="6de14-147">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="6de14-147">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="6de14-148">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span><span class="sxs-lookup"><span data-stu-id="6de14-148">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="6de14-149">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="6de14-149">Errata and Notes</span></span>

* <span data-ttu-id="6de14-150">"Habilitar Solo mi código" debe deshabilitarse (*unchecked*) en Visual Studio en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="6de14-150">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="6de14-151">Programa de instalación de Unity</span><span class="sxs-lookup"><span data-stu-id="6de14-151">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="6de14-152">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="6de14-152">Instructions</span></span>

1. <span data-ttu-id="6de14-153">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="6de14-153">Start Unity.</span></span>
2. <span data-ttu-id="6de14-154">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="6de14-154">Select **Open**.</span></span>
3. <span data-ttu-id="6de14-155">Navegue hasta la **HolographicAcademy hologramas 212 voz** carpeta que anteriormente no archivados.</span><span class="sxs-lookup"><span data-stu-id="6de14-155">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="6de14-156">Busque y seleccione el **iniciando**/**el Explorador de modelos** carpeta.</span><span class="sxs-lookup"><span data-stu-id="6de14-156">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="6de14-157">Haga clic en el **Seleccionar carpeta** botón.</span><span class="sxs-lookup"><span data-stu-id="6de14-157">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="6de14-158">En el **proyecto** del panel, expanda el **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="6de14-158">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="6de14-159">Haga doble clic en **ModelExplorer** escena para cargarlo en Unity.</span><span class="sxs-lookup"><span data-stu-id="6de14-159">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="6de14-160">Compilación</span><span class="sxs-lookup"><span data-stu-id="6de14-160">Building</span></span>

1. <span data-ttu-id="6de14-161">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="6de14-161">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="6de14-162">Si **escenas/ModelExplorer** no aparece en **escenas en compilación**, haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="6de14-162">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="6de14-163">Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6de14-163">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="6de14-164">En caso contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="6de14-164">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="6de14-165">Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="6de14-165">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="6de14-166">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="6de14-166">Click **Build**.</span></span>
6. <span data-ttu-id="6de14-167">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="6de14-167">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="6de14-168">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="6de14-168">Single click the **App** folder.</span></span>
8. <span data-ttu-id="6de14-169">Presione **seleccionar la carpeta** y Unity empezará a compilar el proyecto de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6de14-169">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="6de14-170">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="6de14-170">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="6de14-171">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="6de14-171">Open the **App** folder.</span></span>
2. <span data-ttu-id="6de14-172">Abra el **ModelExplorer Visual Studio solución**.</span><span class="sxs-lookup"><span data-stu-id="6de14-172">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="6de14-173">Si la implementación en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="6de14-173">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="6de14-174">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="6de14-174">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="6de14-175">Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="6de14-175">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="6de14-176">Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**.</span><span class="sxs-lookup"><span data-stu-id="6de14-176">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="6de14-177">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="6de14-177">Click **Select**.</span></span> <span data-ttu-id="6de14-178">Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="6de14-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="6de14-179">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="6de14-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="6de14-180">Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="6de14-180">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="6de14-181">Cuando haya implementado la aplicación, descartar los **Fitbox** con un **seleccione gesto**.</span><span class="sxs-lookup"><span data-stu-id="6de14-181">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="6de14-182">Si la implementación en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="6de14-182">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="6de14-183">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="6de14-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="6de14-184">Asegúrese de que el destino de implementación se establece en **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="6de14-184">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="6de14-185">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="6de14-185">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="6de14-186">Cuando haya implementado la aplicación, descartar los **Fitbox** extrayendo el desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="6de14-186">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="6de14-187">Es posible que observe algunos errores rojo en el panel de errores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6de14-187">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="6de14-188">Es seguro pasarlos por alto.</span><span class="sxs-lookup"><span data-stu-id="6de14-188">It is safe to ignore them.</span></span> <span data-ttu-id="6de14-189">Progreso de la compilación conmutador al panel de salida para ver los costes reales.</span><span class="sxs-lookup"><span data-stu-id="6de14-189">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="6de14-190">Errores en el panel de salida, deberá realizar una corrección (la mayoría suelen deberse a un error en una secuencia de comandos).</span><span class="sxs-lookup"><span data-stu-id="6de14-190">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="6de14-191">Capítulo 1 - reconocimiento</span><span class="sxs-lookup"><span data-stu-id="6de14-191">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="6de14-192">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6de14-192">Objectives</span></span>

* <span data-ttu-id="6de14-193">Obtenga información sobre la **consejos** de diseño de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-193">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="6de14-194">Use **KeywordRecognizer** para agregar los comandos de voz en función de mirada.</span><span class="sxs-lookup"><span data-stu-id="6de14-194">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="6de14-195">Informar a los usuarios de comandos de voz con cursor **comentarios**.</span><span class="sxs-lookup"><span data-stu-id="6de14-195">Make users aware of voice commands using cursor **feedback**.</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="6de14-196">Diseño de comandos de voz</span><span class="sxs-lookup"><span data-stu-id="6de14-196">Voice Command Design</span></span>

<span data-ttu-id="6de14-197">En este capítulo, aprenderá sobre el diseño de los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-197">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="6de14-198">Al crear los comandos de voz:</span><span class="sxs-lookup"><span data-stu-id="6de14-198">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="6de14-199">DO</span><span class="sxs-lookup"><span data-stu-id="6de14-199">DO</span></span>

* <span data-ttu-id="6de14-200">Crear comandos concisos.</span><span class="sxs-lookup"><span data-stu-id="6de14-200">Create concise commands.</span></span> <span data-ttu-id="6de14-201">No quiere usar *"Reproducir el vídeo seleccionado"*, ya que ese comando no es conciso y olvidan fácilmente por el usuario.</span><span class="sxs-lookup"><span data-stu-id="6de14-201">You don't want to use *"Play the currently selected video"*, because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="6de14-202">En su lugar, debe usar: *"Reproducir vídeo"*, porque es conciso y tiene varios sílabas.</span><span class="sxs-lookup"><span data-stu-id="6de14-202">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="6de14-203">Usar un vocabulario simple.</span><span class="sxs-lookup"><span data-stu-id="6de14-203">Use a simple vocabulary.</span></span> <span data-ttu-id="6de14-204">Siempre intenta utilizar palabras y frases que resultan fáciles para el usuario detectar y recuerde comunes.</span><span class="sxs-lookup"><span data-stu-id="6de14-204">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="6de14-205">Por ejemplo, si la aplicación tiene un objeto de la nota que se podría mostrar u ocultar de la vista, no utilizaría el comando *"Mostrar panel"*, ya que "panel" es un término usado con poca frecuencia.</span><span class="sxs-lookup"><span data-stu-id="6de14-205">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"*, because "placard" is a rarely used term.</span></span> <span data-ttu-id="6de14-206">En su lugar, usaría el comando: *"Mostrar nota"*, para mostrar la nota de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6de14-206">Instead, you would use the command: *"Show Note"*, to reveal the note in your application.</span></span>
* <span data-ttu-id="6de14-207">Ser coherente.</span><span class="sxs-lookup"><span data-stu-id="6de14-207">Be consistent.</span></span> <span data-ttu-id="6de14-208">Los comandos de voz se deben mantener coherentes en toda la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6de14-208">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="6de14-209">Imagine que tiene dos escenas en la aplicación y ambos escenas contienen un botón para cerrar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6de14-209">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="6de14-210">Si la primera escena usa el comando *"Exit"* para desencadenar el botón, pero la segunda escena usara el comando *"Cerrar aplicación"*, a continuación, el usuario será bastante confundido.</span><span class="sxs-lookup"><span data-stu-id="6de14-210">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"*, then the user is going to get very confused.</span></span> <span data-ttu-id="6de14-211">Si la misma funcionalidad que se conserva entre varias escenas, debe usarse el mismo comando de voz para activarlo.</span><span class="sxs-lookup"><span data-stu-id="6de14-211">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="6de14-212">NO</span><span class="sxs-lookup"><span data-stu-id="6de14-212">DON'T</span></span>

* <span data-ttu-id="6de14-213">Use los comandos Sílaba único.</span><span class="sxs-lookup"><span data-stu-id="6de14-213">Use single syllable commands.</span></span> <span data-ttu-id="6de14-214">Por ejemplo, si está creando un comando de voz para reproducir un vídeo, debe evitar usar el comando simple *"Reproducir"*, tal y como es solo un único Sílaba y podrían perderse fácilmente por el sistema.</span><span class="sxs-lookup"><span data-stu-id="6de14-214">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"*, as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="6de14-215">En su lugar, debe usar: *"Reproducir vídeo"*, porque es conciso y tiene varios sílabas.</span><span class="sxs-lookup"><span data-stu-id="6de14-215">Instead, you should use: *"Play Video"*, because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="6de14-216">Use los comandos del sistema.</span><span class="sxs-lookup"><span data-stu-id="6de14-216">Use system commands.</span></span> <span data-ttu-id="6de14-217">El *"Select"* comando está reservado por el sistema para desencadenar un evento Tap para el objeto tiene el foco.</span><span class="sxs-lookup"><span data-stu-id="6de14-217">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="6de14-218">No volver a usar el *"Select"* comando en una palabra clave o frase, podrían no funcionar según lo esperado.</span><span class="sxs-lookup"><span data-stu-id="6de14-218">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="6de14-219">Por ejemplo, si el comando de la voz para seleccionar un cubo en la aplicación era *"Cubo seleccione"*, pero el usuario estaba mirando una esfera cuando dijeron que el comando, a continuación, se seleccionan la esfera en su lugar.</span><span class="sxs-lookup"><span data-stu-id="6de14-219">For example, if the voice command for selecting a cube in your application was *"Select cube"*, but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="6de14-220">Del mismo modo, comandos de la barra de aplicación son voz habilitada.</span><span class="sxs-lookup"><span data-stu-id="6de14-220">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="6de14-221">No use los siguientes comandos de voz en la vista de CoreWindow:</span><span class="sxs-lookup"><span data-stu-id="6de14-221">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="6de14-222">Volver</span><span class="sxs-lookup"><span data-stu-id="6de14-222">Go Back</span></span>
    2. <span data-ttu-id="6de14-223">Herramienta de desplazamiento</span><span class="sxs-lookup"><span data-stu-id="6de14-223">Scroll Tool</span></span>
    3. <span data-ttu-id="6de14-224">Herramienta de zoom</span><span class="sxs-lookup"><span data-stu-id="6de14-224">Zoom Tool</span></span>
    4. <span data-ttu-id="6de14-225">Herramienta de arrastrar</span><span class="sxs-lookup"><span data-stu-id="6de14-225">Drag Tool</span></span>
    5. <span data-ttu-id="6de14-226">Ajustar</span><span class="sxs-lookup"><span data-stu-id="6de14-226">Adjust</span></span>
    6. <span data-ttu-id="6de14-227">Eliminar</span><span class="sxs-lookup"><span data-stu-id="6de14-227">Remove</span></span>
* <span data-ttu-id="6de14-228">Use sonidos similares.</span><span class="sxs-lookup"><span data-stu-id="6de14-228">Use similar sounds.</span></span> <span data-ttu-id="6de14-229">Intente evitar el uso de comandos de voz una rima.</span><span class="sxs-lookup"><span data-stu-id="6de14-229">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="6de14-230">Si tiene una aplicación de la compra que admite *"Mostrar Store"* y *"Mostrar más"* de comandos, como voz, a continuación, tendrá que deshabilitar uno de los comandos, mientras que el otro está en uso.</span><span class="sxs-lookup"><span data-stu-id="6de14-230">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="6de14-231">Por ejemplo, podría usar la *"Mostrar Store"* botón para abrir el almacén y, a continuación, deshabilitar ese comando cuando se muestra el almacén para que la *"Mostrar más"* comando podría usarse para la exploración.</span><span class="sxs-lookup"><span data-stu-id="6de14-231">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="6de14-232">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="6de14-232">Instructions</span></span>

* <span data-ttu-id="6de14-233">En Unity **jerarquía** del panel, utilice la herramienta de búsqueda para encontrar el **holoComm_screen_mesh** objeto.</span><span class="sxs-lookup"><span data-stu-id="6de14-233">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="6de14-234">Haga doble clic en el **holoComm_screen_mesh** objeto para verlo en el **escena**.</span><span class="sxs-lookup"><span data-stu-id="6de14-234">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene**.</span></span> <span data-ttu-id="6de14-235">Se trata de inspección de los astronautas, que responderá a nuestros comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-235">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="6de14-236">En el **Inspector** panel, busque el **origen de entrada de voz (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="6de14-236">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="6de14-237">Expanda el **palabras clave** sección para ver el comando de voz admitidos: **Abra Communicator**.</span><span class="sxs-lookup"><span data-stu-id="6de14-237">Expand the **Keywords** section to see the supported voice command: **Open Communicator**.</span></span>
* <span data-ttu-id="6de14-238">Haga clic en el icono de engranaje a la derecha, a continuación, seleccione **editar Script**.</span><span class="sxs-lookup"><span data-stu-id="6de14-238">Click the cog to the right side, then select **Edit Script**.</span></span>
* <span data-ttu-id="6de14-239">Explorar **SpeechInputSource.cs** para conocer cómo utiliza el **KeywordRecognizer** para agregar los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-239">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="6de14-240">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="6de14-240">Build and Deploy</span></span>

* <span data-ttu-id="6de14-241">En Unity, utilice **archivo > configuración de compilación** para recompilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6de14-241">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="6de14-242">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="6de14-242">Open the **App** folder.</span></span>
* <span data-ttu-id="6de14-243">Abra el **ModelExplorer Visual Studio solución**.</span><span class="sxs-lookup"><span data-stu-id="6de14-243">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="6de14-244">(Si ya creado o implementado este proyecto en Visual Studio durante la instalación, a continuación, puede abrir esa instancia de VS y haga clic en 'Volver a cargar todo' cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="6de14-244">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="6de14-245">En Visual Studio, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="6de14-245">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="6de14-246">Después de la aplicación se implementa en el HoloLens, descartar el cuadro de ajuste utilizando el [pulsar en el aire](gestures.md#air-tap) gesto.</span><span class="sxs-lookup"><span data-stu-id="6de14-246">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](gestures.md#air-tap) gesture.</span></span>
* <span data-ttu-id="6de14-247">Mire la inspección de los astronautas.</span><span class="sxs-lookup"><span data-stu-id="6de14-247">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="6de14-248">Cuando el reloj tiene el foco, compruebe que el cursor cambia a un micrófono.</span><span class="sxs-lookup"><span data-stu-id="6de14-248">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="6de14-249">Esto proporciona comentarios que la aplicación está escuchando comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-249">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="6de14-250">Compruebe que aparece una información sobre herramientas en el reloj.</span><span class="sxs-lookup"><span data-stu-id="6de14-250">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="6de14-251">Esto ayuda a los usuarios descubrir el *"Communicator abierto"* comando.</span><span class="sxs-lookup"><span data-stu-id="6de14-251">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="6de14-252">Mientras gazing en la inspección, por ejemplo *"Abrir Communicator"* para abrir el panel de communicator.</span><span class="sxs-lookup"><span data-stu-id="6de14-252">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="6de14-253">Capítulo 2: confirmación</span><span class="sxs-lookup"><span data-stu-id="6de14-253">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="6de14-254">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6de14-254">Objectives</span></span>

* <span data-ttu-id="6de14-255">Grabar un mensaje mediante la entrada de micrófono.</span><span class="sxs-lookup"><span data-stu-id="6de14-255">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="6de14-256">Proporcionar comentarios al usuario que la aplicación está escuchando en su propia voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-256">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="6de14-257">El **micrófono** se debe declarar la funcionalidad para que una aplicación grabar desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="6de14-257">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="6de14-258">Esto se hace por usted ya MR 212 de entrada, pero Téngalo en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="6de14-258">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="6de14-259">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="6de14-259">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="6de14-260">Haga clic en la pestaña "Plataforma Universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="6de14-260">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="6de14-261">En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad</span><span class="sxs-lookup"><span data-stu-id="6de14-261">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="6de14-262">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="6de14-262">Instructions</span></span>

* <span data-ttu-id="6de14-263">En Unity **jerarquía** del panel, compruebe que la **holoComm_screen_mesh** objeto está seleccionado.</span><span class="sxs-lookup"><span data-stu-id="6de14-263">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="6de14-264">En el **Inspector** panel, busque el **astronautas inspección (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="6de14-264">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="6de14-265">Haga clic en el cubo pequeño y azul que se ha establecido como el valor de la **Communicator prefabricado** propiedad.</span><span class="sxs-lookup"><span data-stu-id="6de14-265">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="6de14-266">En el **proyecto** panel, el **Communicator** prefabricado ahora debería tener el foco.</span><span class="sxs-lookup"><span data-stu-id="6de14-266">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="6de14-267">Haga clic en el **Communicator** prefabricado en el **proyecto** panel para ver sus componentes en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="6de14-267">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector**.</span></span>
* <span data-ttu-id="6de14-268">Examine el **Manager micrófono (Script)** componente, esto nos permitirá grabar la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="6de14-268">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="6de14-269">Tenga en cuenta que el **Communicator** objeto tiene un **controlador de entrada de voz (Script)** componente para responder a la **enviar mensaje** comando.</span><span class="sxs-lookup"><span data-stu-id="6de14-269">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="6de14-270">Examine el **Communicator (Script)** componente y haga doble clic en el script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6de14-270">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="6de14-271">Communicator.cs es responsable de establecer los Estados del botón adecuado en el dispositivo de communicator.</span><span class="sxs-lookup"><span data-stu-id="6de14-271">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="6de14-272">Esto permitirá que los usuarios grabar un mensaje, reproducirlo y enviar el mensaje a los astronautas.</span><span class="sxs-lookup"><span data-stu-id="6de14-272">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="6de14-273">También iniciará y detendrá una forma de onda animado, para confirmar que el usuario que estaba oír su voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-273">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="6de14-274">En **Communicator.cs**, elimine las líneas siguientes (81 y 82) desde el **iniciar** método.</span><span class="sxs-lookup"><span data-stu-id="6de14-274">In **Communicator.cs**, delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="6de14-275">Esto permitirá que el botón 'Registro' en el communicator.</span><span class="sxs-lookup"><span data-stu-id="6de14-275">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="6de14-276">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="6de14-276">Build and Deploy</span></span>

* <span data-ttu-id="6de14-277">En Visual Studio, vuelva a compilar la aplicación e implemente en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6de14-277">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="6de14-278">Mire la inspección de los astronautas y diga *"Communicator abierto"* para mostrar el communicator.</span><span class="sxs-lookup"><span data-stu-id="6de14-278">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="6de14-279">Presione el **registro** botón (micrófono) para iniciar la grabación de un mensaje verbal para los astronautas.</span><span class="sxs-lookup"><span data-stu-id="6de14-279">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="6de14-280">Empiece a hablar y compruebe que se reproduce la animación de onda en el communicator, lo que proporciona comentarios al usuario que se oye la voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-280">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="6de14-281">Presione el **detener** botón (cuadrado izquierdo) y compruebe que la animación de wave deja de ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="6de14-281">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="6de14-282">Presione el **reproducir** botón (triángulo) para reproducir el mensaje registrado y escuche en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6de14-282">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="6de14-283">Presione el **detener** botón (corchete derecho) para detener la reproducción del mensaje registrado.</span><span class="sxs-lookup"><span data-stu-id="6de14-283">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="6de14-284">Por ejemplo *"Enviar mensaje"* para cerrar el communicator y recibir una respuesta de 'Mensaje recibido' de los astronautas.</span><span class="sxs-lookup"><span data-stu-id="6de14-284">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="6de14-285">Capítulo 3: descripción y el reconocimiento de dictado</span><span class="sxs-lookup"><span data-stu-id="6de14-285">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="6de14-286">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6de14-286">Objectives</span></span>

* <span data-ttu-id="6de14-287">Usar el reconocimiento de dictado para convertir la voz del usuario en texto.</span><span class="sxs-lookup"><span data-stu-id="6de14-287">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="6de14-288">Mostrar los resultados de hipótesis y finales de dictado del reconocedor en la communicator.</span><span class="sxs-lookup"><span data-stu-id="6de14-288">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="6de14-289">En este capítulo, vamos a usar el reconocimiento de dictado para crear un mensaje para los astronautas.</span><span class="sxs-lookup"><span data-stu-id="6de14-289">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="6de14-290">Al usar el reconocimiento de dictado, tenga en cuenta que:</span><span class="sxs-lookup"><span data-stu-id="6de14-290">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="6de14-291">Debe estar conectado a Wi-Fi para el reconocedor dictado funcione.</span><span class="sxs-lookup"><span data-stu-id="6de14-291">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="6de14-292">Se producen tiempos de espera tras un período de tiempo establecido.</span><span class="sxs-lookup"><span data-stu-id="6de14-292">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="6de14-293">Hay dos tiempos de espera a tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="6de14-293">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="6de14-294">Si el reconocedor se inicia y no oye ningún sonido para los primeros cinco segundos, lo hará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="6de14-294">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="6de14-295">Si el reconocedor ha dado un resultado pero, a continuación, oye silencio durante veinte segundos, lo hará el tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="6de14-295">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="6de14-296">Puede ejecutar un único tipo de reconocedor (palabra clave o dictado) a la vez.</span><span class="sxs-lookup"><span data-stu-id="6de14-296">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="6de14-297">El **micrófono** se debe declarar la funcionalidad para que una aplicación grabar desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="6de14-297">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="6de14-298">Esto se hace por usted ya MR 212 de entrada, pero Téngalo en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="6de14-298">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="6de14-299">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="6de14-299">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="6de14-300">Haga clic en la pestaña "Plataforma Universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="6de14-300">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="6de14-301">En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad</span><span class="sxs-lookup"><span data-stu-id="6de14-301">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="6de14-302">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="6de14-302">Instructions</span></span>

<span data-ttu-id="6de14-303">Vamos a editar **MicrophoneManager.cs** para usar el reconocimiento de dictado.</span><span class="sxs-lookup"><span data-stu-id="6de14-303">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="6de14-304">Esto es lo que vamos a agregar:</span><span class="sxs-lookup"><span data-stu-id="6de14-304">This is what we'll add:</span></span>

1. <span data-ttu-id="6de14-305">Cuando el **botón grabar** está presionado, vamos a **iniciar el DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="6de14-305">When the **Record button** is pressed, we'll **start the DictationRecognizer**.</span></span>
2. <span data-ttu-id="6de14-306">Mostrar el **hipótesis** de qué se entiende el DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="6de14-306">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="6de14-307">Fijar el **resultados** de qué se entiende el DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="6de14-307">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="6de14-308">Compruebe si los tiempos de espera de la DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="6de14-308">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="6de14-309">Cuando el **botón detener** está presionado, o que expire la sesión de mic, **detener el DictationRecognizer**.</span><span class="sxs-lookup"><span data-stu-id="6de14-309">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer**.</span></span>
6. <span data-ttu-id="6de14-310">Reinicie el **KeywordRecognizer**, que escuchará el **enviar mensaje** comando.</span><span class="sxs-lookup"><span data-stu-id="6de14-310">Restart the **KeywordRecognizer**, which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="6de14-311">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="6de14-311">Let's get started.</span></span> <span data-ttu-id="6de14-312">Completar todos los ejercicios de codificación para 3.a en **MicrophoneManager.cs**, o copie y pegue el código terminado se encuentra a continuación:</span><span class="sxs-lookup"><span data-stu-id="6de14-312">Complete all coding exercises for 3.a in **MicrophoneManager.cs**, or copy and paste the finished code found below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="6de14-313">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="6de14-313">Build and Deploy</span></span>

* <span data-ttu-id="6de14-314">Volver a generar en Visual Studio e implemente en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6de14-314">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="6de14-315">Descartar el cuadro de ajuste con un gesto de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="6de14-315">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="6de14-316">Mire la inspección de los astronautas y diga *"Communicator abierto"*.</span><span class="sxs-lookup"><span data-stu-id="6de14-316">Gaze at the astronaut's watch and say *"Open Communicator"*.</span></span>
* <span data-ttu-id="6de14-317">Seleccione el **registro** botón (micrófono) para registrar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="6de14-317">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="6de14-318">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="6de14-318">Start speaking.</span></span> <span data-ttu-id="6de14-319">El **módulo de reconocimiento de dictado** interpretará su voz y mostrar el texto hipotética en el communicator.</span><span class="sxs-lookup"><span data-stu-id="6de14-319">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="6de14-320">Intente decir *"Enviar mensaje"* mientras se graba un mensaje.</span><span class="sxs-lookup"><span data-stu-id="6de14-320">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="6de14-321">Tenga en cuenta que el **reconocedor de palabra clave** no responde porque el **módulo de reconocimiento de dictado** todavía está activa.</span><span class="sxs-lookup"><span data-stu-id="6de14-321">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="6de14-322">Dejar de hablar durante unos segundos.</span><span class="sxs-lookup"><span data-stu-id="6de14-322">Stop speaking for a few seconds.</span></span> <span data-ttu-id="6de14-323">Ver como el reconocimiento de dictado se completa su hipótesis y muestra el resultado final.</span><span class="sxs-lookup"><span data-stu-id="6de14-323">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="6de14-324">Empiece a hablar y, a continuación, hacer una pausa durante 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="6de14-324">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="6de14-325">Esto hará que el **módulo de reconocimiento de dictado** al tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="6de14-325">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="6de14-326">Tenga en cuenta que el **reconocedor de palabra clave** se vuelve a habilitar después del tiempo de espera anterior.</span><span class="sxs-lookup"><span data-stu-id="6de14-326">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="6de14-327">El communicator ahora responderá a los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-327">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="6de14-328">Por ejemplo *"Enviar mensaje"* para enviar el mensaje a los astronautas.</span><span class="sxs-lookup"><span data-stu-id="6de14-328">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="6de14-329">Capítulo 4: módulo de reconocimiento de gramática</span><span class="sxs-lookup"><span data-stu-id="6de14-329">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="6de14-330">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6de14-330">Objectives</span></span>

* <span data-ttu-id="6de14-331">Usar el reconocedor de gramática para reconocer la voz del usuario según un archivo de SRGS o especificación de gramática de reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-331">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="6de14-332">El **micrófono** se debe declarar la funcionalidad para que una aplicación grabar desde el micrófono.</span><span class="sxs-lookup"><span data-stu-id="6de14-332">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="6de14-333">Esto se hace por usted ya MR 212 de entrada, pero Téngalo en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="6de14-333">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="6de14-334">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="6de14-334">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="6de14-335">Haga clic en la pestaña "Plataforma Universal de Windows"</span><span class="sxs-lookup"><span data-stu-id="6de14-335">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="6de14-336">En la sección "Funcionalidades de publicación configuración >", compruebe el **micrófono** capacidad</span><span class="sxs-lookup"><span data-stu-id="6de14-336">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="6de14-337">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="6de14-337">Instructions</span></span>

1. <span data-ttu-id="6de14-338">En el **jerarquía** del panel, busque **Jetpack_Center** y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="6de14-338">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="6de14-339">Busque el **acción sean** secuencia de comandos en el **Inspector** panel.</span><span class="sxs-lookup"><span data-stu-id="6de14-339">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="6de14-340">Haga clic en el círculo pequeño a la derecha de la **objeto para etiquetas a lo largo de** campo.</span><span class="sxs-lookup"><span data-stu-id="6de14-340">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="6de14-341">En la ventana emergente, busque **SRGSToolbox** y selecciónela en la lista.</span><span class="sxs-lookup"><span data-stu-id="6de14-341">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="6de14-342">Eche un vistazo a la **SRGSColor.xml** de archivos en el **StreamingAssets** carpeta.</span><span class="sxs-lookup"><span data-stu-id="6de14-342">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
* <span data-ttu-id="6de14-343">La especificación de diseño SRGS puede encontrarse en el sitio Web de W3C [aquí](https://www.w3.org/TR/speech-grammar/).</span><span class="sxs-lookup"><span data-stu-id="6de14-343">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>
* <span data-ttu-id="6de14-344">En nuestro archivo SRGS, tenemos tres tipos de reglas:</span><span class="sxs-lookup"><span data-stu-id="6de14-344">In our SRGS file, we have three types of rules:</span></span>
  * <span data-ttu-id="6de14-345">Una regla que permite especificar un color de una lista de doce colores.</span><span class="sxs-lookup"><span data-stu-id="6de14-345">A rule which lets you say one color from a list of twelve colors.</span></span>
  * <span data-ttu-id="6de14-346">Tres reglas que realizan escuchas de una combinación de la regla de color y una de las tres formas.</span><span class="sxs-lookup"><span data-stu-id="6de14-346">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
  * <span data-ttu-id="6de14-347">La regla raíz, colorChooser, que realiza escuchas para cualquier combinación de las tres reglas "de color + forma".</span><span class="sxs-lookup"><span data-stu-id="6de14-347">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="6de14-348">Las formas se pueden decir en cualquier orden y en cualquier cantidad de solo uno a tres.</span><span class="sxs-lookup"><span data-stu-id="6de14-348">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="6de14-349">Esta es la única regla que escucha, como se especifica como la regla raíz en la parte superior del archivo en la inicial &lt;gramática&gt; etiqueta.</span><span class="sxs-lookup"><span data-stu-id="6de14-349">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="6de14-350">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="6de14-350">Build and Deploy</span></span>

* <span data-ttu-id="6de14-351">Vuelva a compilar la aplicación en Unity, a continuación, compile e implemente desde Visual Studio para probar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6de14-351">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="6de14-352">Descartar el cuadro de ajuste con un gesto de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="6de14-352">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="6de14-353">Mire jetpack del astronautas y realizar un gesto de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="6de14-353">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="6de14-354">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="6de14-354">Start speaking.</span></span> <span data-ttu-id="6de14-355">El **gramática reconocedor** interpretará su voz y cambiar los colores de las formas según el reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="6de14-355">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="6de14-356">Un comando de ejemplo es "círculo azul, amarillo cuadrado".</span><span class="sxs-lookup"><span data-stu-id="6de14-356">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="6de14-357">Realice otra gesto de pulsar en el aire para descartar el cuadro de herramientas.</span><span class="sxs-lookup"><span data-stu-id="6de14-357">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="6de14-358">Fin</span><span class="sxs-lookup"><span data-stu-id="6de14-358">The End</span></span>

<span data-ttu-id="6de14-359">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="6de14-359">Congratulations!</span></span> <span data-ttu-id="6de14-360">Ahora ha completado **MR entrada 212: Voz**.</span><span class="sxs-lookup"><span data-stu-id="6de14-360">You have now completed **MR Input 212: Voice**.</span></span>

* <span data-ttu-id="6de14-361">Conocer la denegación de servicio y los contras de los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-361">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="6de14-362">Se ha explicado cómo se emplea la información sobre herramientas que los usuarios sea consciente de los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-362">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="6de14-363">Se ha visto varios tipos de comentarios que se utiliza para confirmar que se ha oído la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="6de14-363">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="6de14-364">Saber cómo cambiar entre el reconocedor de palabra clave y el reconocimiento de dictado y forma en que estas dos características comprender e interpretan la voz.</span><span class="sxs-lookup"><span data-stu-id="6de14-364">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="6de14-365">Ha aprendido a utilizar un archivo SRGS y el reconocimiento de la gramática de reconocimiento de voz en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6de14-365">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>
