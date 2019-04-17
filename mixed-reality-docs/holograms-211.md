---
title: Entrada MR 211 - gesto
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, movimiento
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605399"
---
>[!NOTE]
><span data-ttu-id="0770d-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="0770d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0770d-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="0770d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0770d-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="0770d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0770d-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="0770d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0770d-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0770d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0770d-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="0770d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="0770d-110">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="0770d-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="0770d-111">[Los gestos](gestures.md) convertir la intención del usuario en acción.</span><span class="sxs-lookup"><span data-stu-id="0770d-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="0770d-112">Con los gestos, los usuarios pueden interactuar con hologramas.</span><span class="sxs-lookup"><span data-stu-id="0770d-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="0770d-113">En este curso, se obtendrá información sobre cómo realizar un seguimiento de las manos del usuario, responder a entradas del usuario, y ofrecer comentarios al usuario por lado estado y la ubicación.</span><span class="sxs-lookup"><span data-stu-id="0770d-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="0770d-114">En [MR Fundamentos 101](holograms-101.md), usamos un gesto de pulsar de aire simple para interactuar con nuestra hologramas.</span><span class="sxs-lookup"><span data-stu-id="0770d-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="0770d-115">Ahora, podrá ir más allá del gesto de pulsar en el aire y explorar conceptos nuevos que:</span><span class="sxs-lookup"><span data-stu-id="0770d-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="0770d-116">Detectar cuándo se está realizando un seguimiento de la mano del usuario y proporcionar comentarios al usuario.</span><span class="sxs-lookup"><span data-stu-id="0770d-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="0770d-117">Usar un gesto de exploración se va a girar nuestro hologramas.</span><span class="sxs-lookup"><span data-stu-id="0770d-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="0770d-118">Proporcionar comentarios al manual del usuario que se va a dejar fuera de la vista.</span><span class="sxs-lookup"><span data-stu-id="0770d-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="0770d-119">Usar eventos de manipulación para permitir que los usuarios se desplacen hologramas con sus manos.</span><span class="sxs-lookup"><span data-stu-id="0770d-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="0770d-120">En este curso, volveremos a proyecto Unity **el Explorador de modelos**, que se basa [MR entrada 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="0770d-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="0770d-121">Es nuestro amigo astronautas a ayudarnos en nuestra exploración de estos nuevos conceptos de gesto.</span><span class="sxs-lookup"><span data-stu-id="0770d-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0770d-122">Los vídeos insertados en cada uno de los siguientes capítulos se guardó usando una versión anterior de Unity y el Kit de herramientas de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="0770d-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0770d-123">Aunque las instrucciones paso a paso son actuales y precisas, puede ver las secuencias de comandos y los objetos visuales en los vídeos correspondientes que no están actualizados.</span><span class="sxs-lookup"><span data-stu-id="0770d-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="0770d-124">Los vídeos permanecen incluidos para la posterioridad y porque se tratan los conceptos se siguen aplican.</span><span class="sxs-lookup"><span data-stu-id="0770d-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="0770d-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0770d-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0770d-126">Curso</span><span class="sxs-lookup"><span data-stu-id="0770d-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0770d-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0770d-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0770d-128"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="0770d-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0770d-129">Entrada MR 211: Gesto</span><span class="sxs-lookup"><span data-stu-id="0770d-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="0770d-130">✔️</span><span class="sxs-lookup"><span data-stu-id="0770d-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0770d-131">✔️</span><span class="sxs-lookup"><span data-stu-id="0770d-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0770d-132">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="0770d-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0770d-133">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="0770d-133">Prerequisites</span></span>

* <span data-ttu-id="0770d-134">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0770d-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="0770d-135">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="0770d-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="0770d-136">Debe haber completado [MR Fundamentos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="0770d-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="0770d-137">Debe haber completado [MR entrada 210](holograms-210.md).</span><span class="sxs-lookup"><span data-stu-id="0770d-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="0770d-138">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="0770d-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0770d-139">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="0770d-139">Project files</span></span>

* <span data-ttu-id="0770d-140">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="0770d-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="0770d-141"> Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="0770d-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="0770d-142">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="0770d-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="0770d-143">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span><span class="sxs-lookup"><span data-stu-id="0770d-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="0770d-144">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="0770d-144">Errata and Notes</span></span>

* <span data-ttu-id="0770d-145">"Habilitar Solo mi código" debe deshabilitarse (*unchecked*) en Visual Studio en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="0770d-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="0770d-146">Capítulo 0: instalación de Unity</span><span class="sxs-lookup"><span data-stu-id="0770d-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="0770d-147">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0770d-147">Instructions</span></span>

1. <span data-ttu-id="0770d-148">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="0770d-148">Start Unity.</span></span>
2. <span data-ttu-id="0770d-149">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="0770d-149">Select **Open**.</span></span>
3. <span data-ttu-id="0770d-150">Navegue hasta la **gesto** carpeta que anteriormente no archivados.</span><span class="sxs-lookup"><span data-stu-id="0770d-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="0770d-151">Busque y seleccione el **iniciando**/**el Explorador de modelos** carpeta.</span><span class="sxs-lookup"><span data-stu-id="0770d-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="0770d-152">Haga clic en el **Seleccionar carpeta** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="0770d-153">En el **proyecto** del panel, expanda el **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="0770d-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="0770d-154">Haga doble clic en **ModelExplorer** escena para cargarlo en Unity.</span><span class="sxs-lookup"><span data-stu-id="0770d-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="0770d-155">Compilación</span><span class="sxs-lookup"><span data-stu-id="0770d-155">Building</span></span>

1. <span data-ttu-id="0770d-156">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="0770d-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="0770d-157">Si **escenas/ModelExplorer** no aparece en **escenas en compilación**, haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="0770d-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="0770d-158">Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0770d-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="0770d-159">En caso contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="0770d-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="0770d-160">Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="0770d-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="0770d-161">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="0770d-161">Click **Build**.</span></span>
6. <span data-ttu-id="0770d-162">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="0770d-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="0770d-163">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="0770d-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="0770d-164">Presione **seleccionar la carpeta** y Unity empezará a compilar el proyecto de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0770d-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="0770d-165">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="0770d-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="0770d-166">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="0770d-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="0770d-167">Abra el **ModelExplorer Visual Studio solución**.</span><span class="sxs-lookup"><span data-stu-id="0770d-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="0770d-168">Si la implementación en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="0770d-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="0770d-169">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="0770d-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="0770d-170">Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="0770d-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="0770d-171">Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**.</span><span class="sxs-lookup"><span data-stu-id="0770d-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="0770d-172">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="0770d-172">Click **Select**.</span></span> <span data-ttu-id="0770d-173">Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="0770d-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="0770d-174">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0770d-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0770d-175">Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="0770d-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="0770d-176">Cuando haya implementado la aplicación, descartar los **Fitbox** con un **seleccione gesto**.</span><span class="sxs-lookup"><span data-stu-id="0770d-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="0770d-177">Si la implementación en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="0770d-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="0770d-178">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="0770d-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="0770d-179">Asegúrese de que el destino de implementación se establece en **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="0770d-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="0770d-180">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0770d-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="0770d-181">Cuando haya implementado la aplicación, descartar los **Fitbox** extrayendo el desencadenador en un controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0770d-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="0770d-182">Es posible que observe algunos errores rojo en el panel de errores de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0770d-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="0770d-183">Es seguro pasarlos por alto.</span><span class="sxs-lookup"><span data-stu-id="0770d-183">It is safe to ignore them.</span></span> <span data-ttu-id="0770d-184">Progreso de la compilación conmutador al panel de salida para ver los costes reales.</span><span class="sxs-lookup"><span data-stu-id="0770d-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="0770d-185">Errores en el panel de salida, deberá realizar una corrección (la mayoría suelen deberse a un error en una secuencia de comandos).</span><span class="sxs-lookup"><span data-stu-id="0770d-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="0770d-186">Capítulo 1: comentarios de mano detectado</span><span class="sxs-lookup"><span data-stu-id="0770d-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="0770d-187">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0770d-187">Objectives</span></span>

* <span data-ttu-id="0770d-188">Suscribirse para entregar eventos de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="0770d-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="0770d-189">Use la información del cursor para mostrar a los usuarios cuando se está realizando un seguimiento de una mano.</span><span class="sxs-lookup"><span data-stu-id="0770d-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="0770d-190">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0770d-190">Instructions</span></span>

* <span data-ttu-id="0770d-191">En el **jerarquía** del panel, expanda el **InputManager** objeto.</span><span class="sxs-lookup"><span data-stu-id="0770d-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="0770d-192">Busque y seleccione el **GesturesInput** objeto.</span><span class="sxs-lookup"><span data-stu-id="0770d-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="0770d-193">El **InteractionInputSource.cs** script sigue estos pasos:</span><span class="sxs-lookup"><span data-stu-id="0770d-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="0770d-194">Se suscribe a los eventos InteractionSourceDetected y InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="0770d-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="0770d-195">Establece el estado HandDetected.</span><span class="sxs-lookup"><span data-stu-id="0770d-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="0770d-196">Cancela la suscripción de los eventos InteractionSourceDetected y InteractionSourceLost.</span><span class="sxs-lookup"><span data-stu-id="0770d-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="0770d-197">A continuación, se actualizará el cursor de [MR entrada 210](holograms-210.md) en uno que se muestran comentarios dependiendo de las acciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="0770d-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="0770d-198">En el **jerarquía** panel, seleccione el **Cursor** objeto y elimínelo.</span><span class="sxs-lookup"><span data-stu-id="0770d-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="0770d-199">En el **proyecto** del panel, busque **CursorWithFeedback** y arrástrelo el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="0770d-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="0770d-200">Haga clic en **InputManager** en el **jerarquía** panel, a continuación, arrastre el **CursorWithFeedback** objeto desde el **jerarquía** en el Del InputManager **SimpleSinglePointerSelector**del **Cursor** campo, en la parte inferior de la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="0770d-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="0770d-201">Haga clic en el **CursorWithFeedback** en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="0770d-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="0770d-202">En el **Inspector** del panel, expanda **datos de estado del Cursor** en el **objeto Cursor** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="0770d-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="0770d-203">El **datos de estado del Cursor** funciona como esto:</span><span class="sxs-lookup"><span data-stu-id="0770d-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="0770d-204">Cualquier **observación** estado significa que no se detecta ningún mano y el usuario simplemente está mirando.</span><span class="sxs-lookup"><span data-stu-id="0770d-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="0770d-205">Cualquier **Interact** estado significa que se detecte una mano o el controlador.</span><span class="sxs-lookup"><span data-stu-id="0770d-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="0770d-206">Cualquier **mantenga el mouse** estado significa que el usuario está viendo un holograma.</span><span class="sxs-lookup"><span data-stu-id="0770d-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0770d-207">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="0770d-207">Build and Deploy</span></span>

* <span data-ttu-id="0770d-208">En Unity, utilice **archivo > configuración de compilación** para recompilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0770d-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="0770d-209">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="0770d-209">Open the **App** folder.</span></span>
* <span data-ttu-id="0770d-210">Si aún no está abierto, abra el **solución de Visual Studio ModelExplorer**.</span><span class="sxs-lookup"><span data-stu-id="0770d-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="0770d-211">(Si ya creado o implementado este proyecto en Visual Studio durante la instalación, a continuación, puede abrir esa instancia de VS y haga clic en 'Volver a cargar todo' cuando se le solicite).</span><span class="sxs-lookup"><span data-stu-id="0770d-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="0770d-212">En Visual Studio, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="0770d-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0770d-213">Después de la aplicación se implementa en el HoloLens, descarte la fitbox con el gesto de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="0770d-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="0770d-214">Mover la mano en la vista y seleccione el dedo índice el cielo para iniciar el seguimiento de mano.</span><span class="sxs-lookup"><span data-stu-id="0770d-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="0770d-215">Mover la mano izquierda, derecha, arriba y abajo.</span><span class="sxs-lookup"><span data-stu-id="0770d-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="0770d-216">Vea cómo el cursor cambia cuando se detecta y, a continuación, se pierde de vista de la mano.</span><span class="sxs-lookup"><span data-stu-id="0770d-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="0770d-217">Si se encuentra en un auricular envolvente, tendrá que conectar y desconectar el controlador.</span><span class="sxs-lookup"><span data-stu-id="0770d-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="0770d-218">Estos comentarios se vuelve menos interesantes en un dispositivo envolvente, como un controlador conectado siempre será "disponible".</span><span class="sxs-lookup"><span data-stu-id="0770d-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="0770d-219">Capítulo 2: navegación</span><span class="sxs-lookup"><span data-stu-id="0770d-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="0770d-220">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0770d-220">Objectives</span></span>

* <span data-ttu-id="0770d-221">Use los eventos de gestos de navegación para rotar a los astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="0770d-222">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0770d-222">Instructions</span></span>

<span data-ttu-id="0770d-223">Para usar gestos de navegación en nuestra aplicación, vamos a editar **GestureAction.cs** girar objetos cuando se produce el gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="0770d-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="0770d-224">Además, vamos a agregar comentarios al cursor para mostrar cuando la navegación está disponible.</span><span class="sxs-lookup"><span data-stu-id="0770d-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="0770d-225">En el **jerarquía** del panel, expanda **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0770d-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="0770d-226">En el **hologramas** carpeta, busque la **ScrollFeedback** activo.</span><span class="sxs-lookup"><span data-stu-id="0770d-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="0770d-227">Arrastre y coloque el **ScrollFeedback** prefabricado hasta el **CursorWithFeedback** GameObject en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="0770d-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="0770d-228">Haga clic en **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0770d-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="0770d-229">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="0770d-230">En el menú, escriba en el cuadro de búsqueda **CursorFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0770d-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="0770d-231">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0770d-231">Select the search result.</span></span>
7. <span data-ttu-id="0770d-232">Arrastrar y colocar el **ScrollFeedback** objeto desde el **jerarquía** en el **objeto de juego de desplazamiento detectado** propiedad en el **comentarios del Cursor**componente en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="0770d-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="0770d-233">En el **jerarquía** panel, seleccione el **AstroMan** objeto.</span><span class="sxs-lookup"><span data-stu-id="0770d-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="0770d-234">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="0770d-235">En el menú, escriba en el cuadro de búsqueda **acción de gesto**.</span><span class="sxs-lookup"><span data-stu-id="0770d-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="0770d-236">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0770d-236">Select the search result.</span></span>

<span data-ttu-id="0770d-237">A continuación, abra **GestureAction.cs** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0770d-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="0770d-238">En la codificación ejercicio 2.c, edite la secuencia de comandos para hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0770d-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="0770d-239">**Girar el AstroMan** objeto cada vez que se realiza un gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="0770d-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="0770d-240">Calcular la **rotationFactor** para controlar la cantidad de giro que se aplican al objeto.</span><span class="sxs-lookup"><span data-stu-id="0770d-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="0770d-241">**Girar el objeto** alrededor del eje y cuando el usuario mueve la mano izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="0770d-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="0770d-242">Codificación completa ejercita 2.c en la secuencia de comandos o reemplace el código con la solución completa a continuación:</span><span class="sxs-lookup"><span data-stu-id="0770d-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="0770d-243">Observará que los otros eventos de exploración ya se rellenan con alguna información.</span><span class="sxs-lookup"><span data-stu-id="0770d-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="0770d-244">Insertamos el GameObject en el Kit de herramientas pila modal del InputSystem, por lo que el usuario no tiene que mantener el foco en los astronautas una vez comenzada la rotación.</span><span class="sxs-lookup"><span data-stu-id="0770d-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="0770d-245">En consecuencia, se extraiga el GameObject la pila una vez completado el gesto.</span><span class="sxs-lookup"><span data-stu-id="0770d-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0770d-246">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="0770d-246">Build and Deploy</span></span>

1. <span data-ttu-id="0770d-247">Vuelva a compilar la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para ejecutarlo en el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0770d-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="0770d-248">Mire los astronautas, dos flechas deben aparecer en cualquier lado del cursor.</span><span class="sxs-lookup"><span data-stu-id="0770d-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="0770d-249">Este nuevo objeto visual indica que se pueden girar los astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="0770d-250">Coloque la mano en la posición lista (dedo de índice apuntado hacia el cielo) por lo que el HoloLens iniciará el seguimiento de su mano.</span><span class="sxs-lookup"><span data-stu-id="0770d-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="0770d-251">Para rotar a los astronautas, reducir el dedo índice a una posición pinch y, a continuación, mueva la mano izquierda o derecha para desencadenar el gesto NavigationX.</span><span class="sxs-lookup"><span data-stu-id="0770d-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="0770d-252">Capítulo 3: Guía de mano</span><span class="sxs-lookup"><span data-stu-id="0770d-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="0770d-253">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0770d-253">Objectives</span></span>

* <span data-ttu-id="0770d-254">Use **entregar puntuación orientación** para ayudar a predecir cuándo se perderá mano de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="0770d-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="0770d-255">Proporcionar **comentarios en el cursor** para mostrar cuando se acerque a la perimetral de la cámara de vista de la mano del usuario.</span><span class="sxs-lookup"><span data-stu-id="0770d-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="0770d-256">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0770d-256">Instructions</span></span>

1. <span data-ttu-id="0770d-257">En el **jerarquía** panel, seleccione el **CursorWithFeedback** objeto.</span><span class="sxs-lookup"><span data-stu-id="0770d-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="0770d-258">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="0770d-259">En el menú, escriba en el cuadro de búsqueda **mano orientación**.</span><span class="sxs-lookup"><span data-stu-id="0770d-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="0770d-260">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0770d-260">Select the search result.</span></span>
4. <span data-ttu-id="0770d-261">En el **proyecto** panel **hologramas** carpeta, busque la **HandGuidanceFeedback** activo.</span><span class="sxs-lookup"><span data-stu-id="0770d-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="0770d-262">Arrastre y coloque el **HandGuidanceFeedback** activo en el **mano orientación indicador** propiedad en el **Inspector** panel.</span><span class="sxs-lookup"><span data-stu-id="0770d-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="0770d-263">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="0770d-263">Build and Deploy</span></span>

* <span data-ttu-id="0770d-264">Vuelva a compilar la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para probar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0770d-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="0770d-265">Trae la mano a la vista y generar el dedo índice que se realiza el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="0770d-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="0770d-266">Iniciar la rotación de los astronautas con los gestos de navegación (acercar el dedo índice y thumb juntos).</span><span class="sxs-lookup"><span data-stu-id="0770d-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="0770d-267">Mover la mano izquierda, derecha, arriba y abajo.</span><span class="sxs-lookup"><span data-stu-id="0770d-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="0770d-268">Como la mano acerque el borde del marco de movimiento, aparecerá una flecha junto al cursor para avisarle de esa mano de seguimiento se perderá.</span><span class="sxs-lookup"><span data-stu-id="0770d-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="0770d-269">La flecha indica la dirección para mover la mano con el fin de evitar que el seguimiento que se pierdan.</span><span class="sxs-lookup"><span data-stu-id="0770d-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="0770d-270">Capítulo 4: manipulación</span><span class="sxs-lookup"><span data-stu-id="0770d-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="0770d-271">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0770d-271">Objectives</span></span>

* <span data-ttu-id="0770d-272">Usar eventos de manipulación para mover a los astronautas con las manos.</span><span class="sxs-lookup"><span data-stu-id="0770d-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="0770d-273">Proporcionar comentarios sobre el cursor para informar al usuario cuando se puede usar la manipulación.</span><span class="sxs-lookup"><span data-stu-id="0770d-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="0770d-274">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0770d-274">Instructions</span></span>

<span data-ttu-id="0770d-275">GestureManager.cs y AstronautManager.cs nos permitirá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0770d-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="0770d-276">Use la palabra clave de voz "**mover astronautas**" para habilitar **manipulación** gestos y "**girar astronautas**" para deshabilitarlos.</span><span class="sxs-lookup"><span data-stu-id="0770d-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="0770d-277">Se va a responder a la **reconocedor de gestos de manipulación**.</span><span class="sxs-lookup"><span data-stu-id="0770d-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="0770d-278">Empecemos.</span><span class="sxs-lookup"><span data-stu-id="0770d-278">Let's get started.</span></span>

1. <span data-ttu-id="0770d-279">En el **jerarquía** panel, cree un nuevo GameObject vacío.</span><span class="sxs-lookup"><span data-stu-id="0770d-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="0770d-280">Asígnele el nombre "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="0770d-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="0770d-281">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="0770d-282">En el menú, escriba en el cuadro de búsqueda **astronautas Manager**.</span><span class="sxs-lookup"><span data-stu-id="0770d-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="0770d-283">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0770d-283">Select the search result.</span></span>
4. <span data-ttu-id="0770d-284">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="0770d-285">En el menú, escriba en el cuadro de búsqueda **origen de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="0770d-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="0770d-286">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0770d-286">Select the search result.</span></span>

<span data-ttu-id="0770d-287">Ahora vamos a agregar los comandos de voz para controlar el estado de interacción de los astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="0770d-288">Expanda el **palabras clave** sección la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="0770d-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="0770d-289">Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="0770d-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="0770d-290">Escriba la palabra clave como **mover astronautas**.</span><span class="sxs-lookup"><span data-stu-id="0770d-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="0770d-291">No dude en Agregar un acceso directo de la clave si así lo desea.</span><span class="sxs-lookup"><span data-stu-id="0770d-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="0770d-292">Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="0770d-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="0770d-293">Escriba la palabra clave como **girar astronautas**.</span><span class="sxs-lookup"><span data-stu-id="0770d-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="0770d-294">No dude en Agregar un acceso directo de la clave si así lo desea.</span><span class="sxs-lookup"><span data-stu-id="0770d-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="0770d-295">El código del controlador correspondiente puede encontrarse en **GestureAction.cs**, en el **ISpeechHandler.OnSpeechKeywordRecognized** controlador.</span><span class="sxs-lookup"><span data-stu-id="0770d-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![Cómo configurar el origen de entrada de voz de capítulo 4](images/holograms211-speech.png)

<span data-ttu-id="0770d-297">A continuación, configuramos los comentarios de la manipulación en el cursor.</span><span class="sxs-lookup"><span data-stu-id="0770d-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="0770d-298">En el **proyecto** panel **hologramas** carpeta, busque la **PathingFeedback** activo.</span><span class="sxs-lookup"><span data-stu-id="0770d-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="0770d-299">Arrastre y coloque el **PathingFeedback** prefabricado hasta el **CursorWithFeedback** objeto en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="0770d-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="0770d-300">En el **jerarquía** del panel, haga clic en **CursorWithFeedback**.</span><span class="sxs-lookup"><span data-stu-id="0770d-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="0770d-301">Arrastre y coloque el **PathingFeedback** objeto desde el **jerarquía** en el **objeto de juego detectado rutas** propiedad en el **comentarios del Cursor**componente en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="0770d-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="0770d-302">Ahora tenemos que agregar código a **GestureAction.cs** para habilitar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0770d-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="0770d-303">Agregue código a la **IManipulationHandler.OnManipulationUpdated** función, lo que se moverá los astronautas cuando un **manipulación** se detecta el gesto.</span><span class="sxs-lookup"><span data-stu-id="0770d-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="0770d-304">Calcular la **vector de movimiento** determinar dónde se deben mover los astronautas a mano posición basada.</span><span class="sxs-lookup"><span data-stu-id="0770d-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="0770d-305">**Mover** los astronautas a la nueva posición.</span><span class="sxs-lookup"><span data-stu-id="0770d-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="0770d-306">Codificación completa ejercicio 4.a en **GestureAction.cs**, o usar nuestra solución completa a continuación:</span><span class="sxs-lookup"><span data-stu-id="0770d-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="0770d-307">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="0770d-307">Build and Deploy</span></span>

* <span data-ttu-id="0770d-308">Volver a generar en Unity y, a continuación, compile e implemente desde Visual Studio para ejecutar la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0770d-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="0770d-309">Mover la mano delante el HoloLens y generar el dedo índice para que puede realizar un seguimiento.</span><span class="sxs-lookup"><span data-stu-id="0770d-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="0770d-310">Centrar el cursor a través de los astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="0770d-311">Supongamos que mover astronautas para mover a los astronautas con un gesto de manipulación.</span><span class="sxs-lookup"><span data-stu-id="0770d-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="0770d-312">Deberían aparecer la cuatro flechas alrededor del cursor para indicar que el programa ahora responderán a eventos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="0770d-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="0770d-313">Disminuya el dedo índice hasta el pulgar y mantenerlos pellizcados juntos.</span><span class="sxs-lookup"><span data-stu-id="0770d-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="0770d-314">Al mover la mano alrededor, los astronautas moverá demasiado (es decir, manipulación).</span><span class="sxs-lookup"><span data-stu-id="0770d-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="0770d-315">Elevar el dedo índice para dejar de manipular a los astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="0770d-316">Nota: Si no dice a 'Mover astronautas' antes de mover la mano, los gestos de navegación se usará en su lugar.</span><span class="sxs-lookup"><span data-stu-id="0770d-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="0770d-317">Supongamos que girar astronautas para volver al estado giratorias.</span><span class="sxs-lookup"><span data-stu-id="0770d-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="0770d-318">Capítulo 5: expansión de modelo</span><span class="sxs-lookup"><span data-stu-id="0770d-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="0770d-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0770d-319">Objectives</span></span>

* <span data-ttu-id="0770d-320">Expanda el modelo astronautas en varios, fragmentos más pequeños que el usuario puede interactuar con.</span><span class="sxs-lookup"><span data-stu-id="0770d-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="0770d-321">Mover cada pieza individualmente con gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="0770d-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="0770d-322">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="0770d-322">Instructions</span></span>

<span data-ttu-id="0770d-323">En esta sección, se llevará a cabo las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="0770d-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="0770d-324">Agregar una nueva palabra clave "**expanda modelo**" para expandir el modelo astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="0770d-325">Agregar una nueva palabra clave "**restablecer modelo**" para devolver el modelo a su forma original.</span><span class="sxs-lookup"><span data-stu-id="0770d-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="0770d-326">Haremos esto mediante la adición de dos más palabras clave para el origen de entrada de voz en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="0770d-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="0770d-327">También le mostraré otra manera de controlar los eventos de reconocimiento.</span><span class="sxs-lookup"><span data-stu-id="0770d-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="0770d-328">Haga clic en nuevo en **AstronautManager** en el **Inspector** y expanda el **palabras clave** sección la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="0770d-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="0770d-329">Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="0770d-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="0770d-330">Escriba la palabra clave como **expandir modelo**.</span><span class="sxs-lookup"><span data-stu-id="0770d-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="0770d-331">No dude en Agregar un acceso directo de la clave si así lo desea.</span><span class="sxs-lookup"><span data-stu-id="0770d-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="0770d-332">Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.</span><span class="sxs-lookup"><span data-stu-id="0770d-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="0770d-333">Escriba la palabra clave como **restablecer modelo**.</span><span class="sxs-lookup"><span data-stu-id="0770d-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="0770d-334">No dude en Agregar un acceso directo de la clave si así lo desea.</span><span class="sxs-lookup"><span data-stu-id="0770d-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="0770d-335">En el **Inspector** del panel, haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="0770d-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="0770d-336">En el menú, escriba en el cuadro de búsqueda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="0770d-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="0770d-337">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="0770d-337">Select the search result.</span></span>
8. <span data-ttu-id="0770d-338">Comprobar **es Global escucha**, puesto que deseamos que estos comandos para trabajar sin tener en cuenta el GameObject nos centraremos.</span><span class="sxs-lookup"><span data-stu-id="0770d-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="0770d-339">Haga clic en el **+** y seleccione **expanda modelo** en la lista desplegable de la palabra clave.</span><span class="sxs-lookup"><span data-stu-id="0770d-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="0770d-340">Haga clic en el **+** en respuesta y arrastre el **AstronautManager** desde el **jerarquía** en el **None (objeto)** campo.</span><span class="sxs-lookup"><span data-stu-id="0770d-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="0770d-341">Ahora, haga clic en el **sin función** lista desplegable, seleccione **AstronautManager**, a continuación, **ExpandModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="0770d-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="0770d-342">Haga clic en el controlador de entrada de voz **+** y seleccione **restablecer modelo** en la lista desplegable de la palabra clave.</span><span class="sxs-lookup"><span data-stu-id="0770d-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="0770d-343">Haga clic en el **+** en respuesta y arrastre el **AstronautManager** desde el **jerarquía** en el **None (objeto)** campo.</span><span class="sxs-lookup"><span data-stu-id="0770d-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="0770d-344">Ahora, haga clic en el **sin función** lista desplegable, seleccione **AstronautManager**, a continuación, **ResetModelCommand**.</span><span class="sxs-lookup"><span data-stu-id="0770d-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![Cómo configurar el origen de entrada de voz y el controlador de capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="0770d-346">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="0770d-346">Build and Deploy</span></span>

* <span data-ttu-id="0770d-347">Pruébalo.</span><span class="sxs-lookup"><span data-stu-id="0770d-347">Try it!</span></span> <span data-ttu-id="0770d-348">Compilar e implementar la aplicación en el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0770d-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="0770d-349">Por ejemplo **expanda modelo** para ver el modelo astronautas expandida.</span><span class="sxs-lookup"><span data-stu-id="0770d-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="0770d-350">Use **navegación** para girar las partes individuales del palo astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="0770d-351">Por ejemplo **mover astronautas** y, a continuación, usar **manipulación** para mover partes individuales del palo astronautas.</span><span class="sxs-lookup"><span data-stu-id="0770d-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="0770d-352">Por ejemplo **girar astronautas** para girar las piezas de nuevo.</span><span class="sxs-lookup"><span data-stu-id="0770d-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="0770d-353">Por ejemplo **restablecer modelo** para devolver los astronautas a su forma original.</span><span class="sxs-lookup"><span data-stu-id="0770d-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="0770d-354">Fin</span><span class="sxs-lookup"><span data-stu-id="0770d-354">The End</span></span>

<span data-ttu-id="0770d-355">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="0770d-355">Congratulations!</span></span> <span data-ttu-id="0770d-356">Ahora ha completado **MR 211 de entrada: Gesto**.</span><span class="sxs-lookup"><span data-stu-id="0770d-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="0770d-357">Sepa cómo detectar y responder a mano los eventos de seguimiento, la navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="0770d-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="0770d-358">Comprender la diferencia entre los gestos de navegación y manipulación.</span><span class="sxs-lookup"><span data-stu-id="0770d-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="0770d-359">Saber cómo cambiar el cursor para proporcionar comentarios visuales cuando se detecta una mano, cuando se perderá una mano y cuando un objeto es compatible con diferentes interacciones (manipulación de vs de navegación).</span><span class="sxs-lookup"><span data-stu-id="0770d-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
