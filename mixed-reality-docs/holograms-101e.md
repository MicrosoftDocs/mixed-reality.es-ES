---
title: MR Basics 101E-completar proyecto con Emulator
description: Siga este tutorial de codificación con Unity, Visual Studio y el emulador de HoloLens para aprender los conceptos básicos de una aplicación holográfica.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, Academy, tutorial, emulador
ms.openlocfilehash: b1d8e1f3f272051bdd6f69ab88c3aef4f86f13ef
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434706"
---
>[!NOTE]
><span data-ttu-id="656a2-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="656a2-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="656a2-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="656a2-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="656a2-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="656a2-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="656a2-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="656a2-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="656a2-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="656a2-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="656a2-109">MR Basics 101E: proyecto completo con Emulator</span><span class="sxs-lookup"><span data-stu-id="656a2-109">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="656a2-110">Este tutorial le guiará a través de un proyecto completo, integrado en Unity, que muestra características básicas de Windows Mixed Reality en HoloLens, como [mirados](gaze-and-commit.md), [gestos](gaze-and-commit.md#composite-gestures), [entrada de voz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="656a2-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="656a2-111">El tutorial tardará aproximadamente 1 hora en completarse.</span><span class="sxs-lookup"><span data-stu-id="656a2-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="656a2-112">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="656a2-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="656a2-113">Recurso</span><span class="sxs-lookup"><span data-stu-id="656a2-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="656a2-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="656a2-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="656a2-115"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="656a2-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="656a2-116">MR Basics 101E: proyecto completo con Emulator</span><span class="sxs-lookup"><span data-stu-id="656a2-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="656a2-117">✔️</span><span class="sxs-lookup"><span data-stu-id="656a2-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="656a2-118">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="656a2-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="656a2-119">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="656a2-119">Prerequisites</span></span>

* <span data-ttu-id="656a2-120">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="656a2-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="656a2-121">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="656a2-121">Project files</span></span>

* <span data-ttu-id="656a2-122">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="656a2-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="656a2-123"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="656a2-123"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="656a2-124">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="656a2-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="656a2-125">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="656a2-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="656a2-126">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="656a2-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="656a2-127">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="656a2-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="656a2-128">Mantenga el nombre de la carpeta como **origami**.</span><span class="sxs-lookup"><span data-stu-id="656a2-128">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="656a2-129">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="656a2-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="656a2-130">Capítulo 1: mundo "Hololens"</span><span class="sxs-lookup"><span data-stu-id="656a2-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="656a2-131">En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="656a2-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="656a2-132">Objetivos</span><span class="sxs-lookup"><span data-stu-id="656a2-132">Objectives</span></span>

* <span data-ttu-id="656a2-133">Configure Unity para el desarrollo holográfica.</span><span class="sxs-lookup"><span data-stu-id="656a2-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="656a2-134">Cree un holograma.</span><span class="sxs-lookup"><span data-stu-id="656a2-134">Make a hologram.</span></span>
* <span data-ttu-id="656a2-135">Vea un holograma que haya realizado.</span><span class="sxs-lookup"><span data-stu-id="656a2-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="656a2-136">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="656a2-136">Instructions</span></span>

* <span data-ttu-id="656a2-137">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="656a2-137">Start Unity.</span></span>
* <span data-ttu-id="656a2-138">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="656a2-138">Select **Open**.</span></span>
* <span data-ttu-id="656a2-139">Escriba ubicación como la carpeta **origami** que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="656a2-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="656a2-140">Seleccione **origami** y haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="656a2-140">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="656a2-141">Guarde la nueva escena: **archivo** / **guardar la escena como**.</span><span class="sxs-lookup"><span data-stu-id="656a2-141">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="656a2-142">Asigne a la escena el nombre **origami** y haga clic en el botón **Guardar** .</span><span class="sxs-lookup"><span data-stu-id="656a2-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="656a2-143">Configuración de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="656a2-143">Setup the main camera</span></span>

* <span data-ttu-id="656a2-144">En el **Panel jerarquía**, seleccione **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="656a2-144">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="656a2-145">En el **Inspector** , establezca su posición de transformación en **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="656a2-145">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="656a2-146">Busque la propiedad **Borrar marcas** y cambie la lista desplegable de **SKYBOX** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="656a2-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="656a2-147">Haga clic en el campo **fondo** para abrir un selector de colores.</span><span class="sxs-lookup"><span data-stu-id="656a2-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="656a2-148">Establezca **R, G, B y** a en **0**.</span><span class="sxs-lookup"><span data-stu-id="656a2-148">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="656a2-149">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="656a2-149">Setup the scene</span></span>

* <span data-ttu-id="656a2-150">En el **Panel jerarquía**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="656a2-150">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="656a2-151">Haga clic con el botón derecho en el nuevo **GameObject** y seleccione Cambiar nombre.</span><span class="sxs-lookup"><span data-stu-id="656a2-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="656a2-152">Cambie el nombre de GameObject a **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="656a2-152">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="656a2-153">En la carpeta **hologramas** del **panel Proyecto**:</span><span class="sxs-lookup"><span data-stu-id="656a2-153">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="656a2-154">Arrastre **Stage** hasta la jerarquía para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="656a2-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="656a2-155">Arrastre **Sphere1** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="656a2-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="656a2-156">Arrastre **Sphere2** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="656a2-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="656a2-157">Haga clic con el botón secundario en el objeto de **luz direccional** en el **Panel jerarquía** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="656a2-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="656a2-158">En la carpeta **hologramas** , arrastre **Lights** hasta la raíz del **Panel de jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="656a2-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="656a2-159">En la **jerarquía**, seleccione el **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="656a2-159">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="656a2-160">En el **Inspector**, establezca la posición de la transformación en **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="656a2-160">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="656a2-161">Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="656a2-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="656a2-162">Debería ver los objetos origami en la ventana de vista previa.</span><span class="sxs-lookup"><span data-stu-id="656a2-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="656a2-163">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="656a2-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="656a2-164">Exportar el proyecto de Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="656a2-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="656a2-165">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="656a2-165">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="656a2-166">Seleccione **tienda Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="656a2-166">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="656a2-167">Establezca **SDK** en **universal 10** y **tipo de compilación** en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="656a2-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="656a2-168">Compruebe **los C# proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="656a2-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="656a2-169">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="656a2-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="656a2-170">Haga clic en **configuración del reproductor..** ..</span><span class="sxs-lookup"><span data-stu-id="656a2-170">Click **Player Settings...**.</span></span>
* <span data-ttu-id="656a2-171">En el panel Inspector, seleccione el logotipo de la **tienda Windows**.</span><span class="sxs-lookup"><span data-stu-id="656a2-171">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="656a2-172">A continuación, seleccione **configuración de publicación**.</span><span class="sxs-lookup"><span data-stu-id="656a2-172">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="656a2-173">En la sección **capacidades** , seleccione las capacidades **micrófono** y **SpatialPerception** .</span><span class="sxs-lookup"><span data-stu-id="656a2-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="656a2-174">De nuevo en la ventana Configuración de compilación, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="656a2-174">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="656a2-175">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="656a2-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="656a2-176">Haga clic en la carpeta de la **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="656a2-176">Single click the **App Folder**.</span></span>
* <span data-ttu-id="656a2-177">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="656a2-177">Press **Select Folder**.</span></span>
* <span data-ttu-id="656a2-178">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="656a2-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="656a2-179">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="656a2-179">Open the **App** folder.</span></span>
* <span data-ttu-id="656a2-180">Abra la **solución origami de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="656a2-180">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="656a2-181">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="656a2-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="656a2-182">Haga clic en la flecha situada junto al botón dispositivo y seleccione **emulador de HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="656a2-182">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="656a2-183">Haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="656a2-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="656a2-184">Después de algún tiempo, el emulador comenzará con el proyecto origami.</span><span class="sxs-lookup"><span data-stu-id="656a2-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="656a2-185">Al iniciar el [emulador](using-the-hololens-emulator.md)por primera vez, el emulador puede tardar hasta 15 minutos en iniciarse.</span><span class="sxs-lookup"><span data-stu-id="656a2-185">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="656a2-186">Una vez que se inicia, no lo cierre.</span><span class="sxs-lookup"><span data-stu-id="656a2-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="656a2-187">Capítulo 2: mira hacia abajo</span><span class="sxs-lookup"><span data-stu-id="656a2-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="656a2-188">En este capítulo, vamos a presentar la primera de las tres formas de interactuar con los hologramas: [miramos](gaze-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="656a2-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="656a2-189">Objetivos</span><span class="sxs-lookup"><span data-stu-id="656a2-189">Objectives</span></span>

* <span data-ttu-id="656a2-190">Visualice la mirada con un cursor de un mundo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="656a2-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="656a2-191">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="656a2-191">Instructions</span></span>

* <span data-ttu-id="656a2-192">Vuelva al proyecto de Unity y cierre la ventana de configuración de la compilación si aún está abierta.</span><span class="sxs-lookup"><span data-stu-id="656a2-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="656a2-193">Seleccione la carpeta **hologramas** en el **panel Proyecto**.</span><span class="sxs-lookup"><span data-stu-id="656a2-193">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="656a2-194">Arrastre el objeto **cursor** al **Panel jerarquía** en el nivel raíz.</span><span class="sxs-lookup"><span data-stu-id="656a2-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="656a2-195">Haga doble clic en el objeto **cursor** para examinarlo más detenidamente.</span><span class="sxs-lookup"><span data-stu-id="656a2-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="656a2-196">Haga clic con el botón secundario en la carpeta **scripts** en el panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="656a2-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="656a2-197">Haga clic en el submenú **crear** .</span><span class="sxs-lookup"><span data-stu-id="656a2-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="656a2-198">Seleccione  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="656a2-198">Select **C# Script**.</span></span>
* <span data-ttu-id="656a2-199">Asigne al script el nombre **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="656a2-199">Name the script **WorldCursor**.</span></span> <span data-ttu-id="656a2-200">Nota: el nombre distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="656a2-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="656a2-201">No es necesario agregar la extensión. cs.</span><span class="sxs-lookup"><span data-stu-id="656a2-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="656a2-202">Seleccione el objeto **cursor** en el **Panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="656a2-202">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="656a2-203">Arrastre y coloque el script **WorldCursor** en el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="656a2-203">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="656a2-204">Haga doble clic en el script **WorldCursor** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="656a2-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="656a2-205">Copie y pegue este código en **WorldCursor.CS** y **guarde todo**.</span><span class="sxs-lookup"><span data-stu-id="656a2-205">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="656a2-206">Vuelva a compilar la aplicación desde el **archivo > la configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="656a2-206">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="656a2-207">Vuelva a la solución de Visual Studio que se usó anteriormente para implementar en el emulador.</span><span class="sxs-lookup"><span data-stu-id="656a2-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="656a2-208">Seleccione "recargar todo" cuando se le solicite.</span><span class="sxs-lookup"><span data-stu-id="656a2-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="656a2-209">Haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="656a2-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="656a2-210">Use el controlador Xbox para buscar en torno a la escena.</span><span class="sxs-lookup"><span data-stu-id="656a2-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="656a2-211">Observe cómo interactúa el cursor con la forma de los objetos.</span><span class="sxs-lookup"><span data-stu-id="656a2-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="656a2-212">Capítulo 3: gestos</span><span class="sxs-lookup"><span data-stu-id="656a2-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="656a2-213">En este capítulo, se agregará compatibilidad con [gestos](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="656a2-213">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="656a2-214">Cuando el usuario selecciona una esfera de papel, haremos que la esfera se active al activar la gravedad mediante el motor físico de Unity.</span><span class="sxs-lookup"><span data-stu-id="656a2-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="656a2-215">Objetivos</span><span class="sxs-lookup"><span data-stu-id="656a2-215">Objectives</span></span>

* <span data-ttu-id="656a2-216">Controle los hologramas con el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="656a2-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="656a2-217">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="656a2-217">Instructions</span></span>

<span data-ttu-id="656a2-218">Comenzaremos por crear un script que pueda detectar el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="656a2-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="656a2-219">En la carpeta **scripts** , cree un script denominado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="656a2-219">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="656a2-220">Arrastre el script **GazeGestureManager** hasta el objeto **OrigamiCollection** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="656a2-221">Abra el script **GazeGestureManager** en Visual Studio y agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="656a2-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="656a2-222">Cree otro script en la carpeta scripts, esta vez con el nombre **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="656a2-222">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="656a2-223">Expanda el objeto **OrigamiCollection** en la vista de jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="656a2-224">Arrastre el script **SphereCommands** al objeto **Sphere1** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="656a2-225">Arrastre el script **SphereCommands** al objeto **Sphere2** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="656a2-226">Abra el script en Visual Studio para editarlo y reemplace el código predeterminado por este:</span><span class="sxs-lookup"><span data-stu-id="656a2-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="656a2-227">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="656a2-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="656a2-228">Buscar en la escena y centrar en uno de los esferas.</span><span class="sxs-lookup"><span data-stu-id="656a2-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="656a2-229">Presione el **botón a del controlador** Xbox o presione la barra espaciadora para simular el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="656a2-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="656a2-230">Capítulo 4: voz</span><span class="sxs-lookup"><span data-stu-id="656a2-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="656a2-231">En este capítulo, se agregará compatibilidad con dos [comandos de voz](voice-input.md): "RESET World" para devolver los esferas colocados a su ubicación original y "Drop Sphere" para que la esfera quede.</span><span class="sxs-lookup"><span data-stu-id="656a2-231">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="656a2-232">Objetivos</span><span class="sxs-lookup"><span data-stu-id="656a2-232">Objectives</span></span>

* <span data-ttu-id="656a2-233">Agregue comandos de voz que siempre escuchan en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="656a2-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="656a2-234">Cree un holograma que reaccione a un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="656a2-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="656a2-235">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="656a2-235">Instructions</span></span>

* <span data-ttu-id="656a2-236">En la carpeta **scripts** , cree un script denominado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="656a2-236">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="656a2-237">Arrastre el script **SpeechManager** hasta el objeto **OrigamiCollection** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="656a2-238">Abra el script **SpeechManager** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="656a2-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="656a2-239">Copie y pegue este código en **SpeechManager.CS** y **guarde todo**:</span><span class="sxs-lookup"><span data-stu-id="656a2-239">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="656a2-240">Abra el script **SphereCommands** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="656a2-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="656a2-241">Actualice el script para que se lea de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="656a2-241">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="656a2-242">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="656a2-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="656a2-243">El emulador admitirá el micrófono del equipo y responderá a su voz: ajuste la vista para que el cursor esté en uno de los esferas y Supongamos "esfera de colocación".</span><span class="sxs-lookup"><span data-stu-id="656a2-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="656a2-244">Por ejemplo, "**restablecer mundo**" para volver a colocarlos en sus posiciones iniciales.</span><span class="sxs-lookup"><span data-stu-id="656a2-244">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="656a2-245">Capítulo 5: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="656a2-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="656a2-246">En este capítulo, agregaremos música a la aplicación y, a continuación, desencadenaremos efectos sonoros en determinadas acciones.</span><span class="sxs-lookup"><span data-stu-id="656a2-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="656a2-247">Usaremos el [sonido espacial](spatial-sound.md) para proporcionar a los sonidos una ubicación específica en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="656a2-247">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="656a2-248">Objetivos</span><span class="sxs-lookup"><span data-stu-id="656a2-248">Objectives</span></span>

* <span data-ttu-id="656a2-249">Escuche los hologramas de su mundo.</span><span class="sxs-lookup"><span data-stu-id="656a2-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="656a2-250">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="656a2-250">Instructions</span></span>

* <span data-ttu-id="656a2-251">En la selección de Unity, en el menú superior, **edite > configuración del proyecto > audio**</span><span class="sxs-lookup"><span data-stu-id="656a2-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="656a2-252">Busque la configuración del **complemento de Spatializer** y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="656a2-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="656a2-253">En la carpeta **hologramas** , arrastre el objeto **ambiente** hasta el objeto **OrigamiCollection** en el panel de jerarquías.</span><span class="sxs-lookup"><span data-stu-id="656a2-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="656a2-254">Seleccione **OrigamiCollection** y busque el componente de **origen de audio** .</span><span class="sxs-lookup"><span data-stu-id="656a2-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="656a2-255">Cambie estas propiedades:</span><span class="sxs-lookup"><span data-stu-id="656a2-255">Change these properties:</span></span>
  * <span data-ttu-id="656a2-256">Compruebe la propiedad **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="656a2-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="656a2-257">Active la casilla **reproducir en activo**.</span><span class="sxs-lookup"><span data-stu-id="656a2-257">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="656a2-258">Cambie la **mezcla espacial** a **3D** arrastrando el control deslizante hasta la derecha.</span><span class="sxs-lookup"><span data-stu-id="656a2-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="656a2-259">Compruebe la propiedad **Loop** .</span><span class="sxs-lookup"><span data-stu-id="656a2-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="656a2-260">Expanda **configuración de sonido 3D**y escriba **0,1** para el **nivel de Doppler**.</span><span class="sxs-lookup"><span data-stu-id="656a2-260">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="656a2-261">Establezca **rolloff de volumen** en **rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="656a2-261">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="656a2-262">Establezca la **distancia máxima** en **20**.</span><span class="sxs-lookup"><span data-stu-id="656a2-262">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="656a2-263">En la carpeta **scripts** , cree un script denominado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="656a2-263">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="656a2-264">Arrastre **SphereSounds** a los objetos **Sphere1** y **Sphere2** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="656a2-265">Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guarde todo**.</span><span class="sxs-lookup"><span data-stu-id="656a2-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="656a2-266">Guarde el script y vuelva a Unity.</span><span class="sxs-lookup"><span data-stu-id="656a2-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="656a2-267">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="656a2-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="656a2-268">Use auriculares para conseguir el efecto completo y vaya más cerca y después de la fase para oír el cambio de los sonidos.</span><span class="sxs-lookup"><span data-stu-id="656a2-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="656a2-269">Capítulo 6: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="656a2-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="656a2-270">Ahora vamos a usar la [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real del mundo real.</span><span class="sxs-lookup"><span data-stu-id="656a2-270">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="656a2-271">Objetivos</span><span class="sxs-lookup"><span data-stu-id="656a2-271">Objectives</span></span>

* <span data-ttu-id="656a2-272">Traiga su mundo real al mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="656a2-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="656a2-273">Coloque los hologramas donde más le importan.</span><span class="sxs-lookup"><span data-stu-id="656a2-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="656a2-274">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="656a2-274">Instructions</span></span>

* <span data-ttu-id="656a2-275">Haga clic en la carpeta **hologramas** en el panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="656a2-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="656a2-276">Arrastre el recurso de **asignación espacial** a la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="656a2-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="656a2-277">Haga clic en el objeto de **asignación espacial** en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="656a2-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="656a2-278">En el **panel Inspector**, cambie las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="656a2-278">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="656a2-279">Active la casilla **dibujar mallas visuales** .</span><span class="sxs-lookup"><span data-stu-id="656a2-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="656a2-280">Busque **material de dibujo** y haga clic en el círculo de la derecha.</span><span class="sxs-lookup"><span data-stu-id="656a2-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="656a2-281">Escriba "**Wireframe**" en el campo de búsqueda de la parte superior.</span><span class="sxs-lookup"><span data-stu-id="656a2-281">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="656a2-282">Haga clic en el resultado y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="656a2-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="656a2-283">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="656a2-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="656a2-284">Cuando se ejecuta la aplicación, se representará en alambre una malla de una sala de reuniones del mundo real analizada previamente.</span><span class="sxs-lookup"><span data-stu-id="656a2-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="656a2-285">Vea cómo una esfera gradual se quedará fuera de la fase y en el suelo.</span><span class="sxs-lookup"><span data-stu-id="656a2-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="656a2-286">Ahora le mostraremos cómo trasladar el OrigamiCollection a una nueva ubicación:</span><span class="sxs-lookup"><span data-stu-id="656a2-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="656a2-287">En la carpeta **scripts** , cree un script denominado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="656a2-287">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="656a2-288">En la **jerarquía**, expanda **OrigamiCollection** y seleccione el objeto **Stage** .</span><span class="sxs-lookup"><span data-stu-id="656a2-288">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="656a2-289">Arrastre el script **TapToPlaceParent** hasta el objeto Stage.</span><span class="sxs-lookup"><span data-stu-id="656a2-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="656a2-290">Abra el script **TapToPlaceParent** en Visual Studio y actualícelo para que sea el siguiente:</span><span class="sxs-lookup"><span data-stu-id="656a2-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="656a2-291">Exportar, compilar e implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="656a2-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="656a2-292">Ahora debería poder colocar el juego en una ubicación específica Gazing en él, con el gesto de selección (**a** o barra espaciadora) y, a continuación, desplazarse a una nueva ubicación y volver a usar el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="656a2-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="656a2-293">Fin</span><span class="sxs-lookup"><span data-stu-id="656a2-293">The end</span></span>

<span data-ttu-id="656a2-294">Y este es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="656a2-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="656a2-295">Aprendió:</span><span class="sxs-lookup"><span data-stu-id="656a2-295">You learned:</span></span>

* <span data-ttu-id="656a2-296">Cómo crear una aplicación holográfica en Unity.</span><span class="sxs-lookup"><span data-stu-id="656a2-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="656a2-297">Cómo hacer uso de la mirada, el gesto, la voz, los sonidos y la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="656a2-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="656a2-298">Cómo compilar e implementar una aplicación con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="656a2-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="656a2-299">Ya está listo para empezar a crear sus propias aplicaciones holográficas.</span><span class="sxs-lookup"><span data-stu-id="656a2-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="656a2-300">Consulta también</span><span class="sxs-lookup"><span data-stu-id="656a2-300">See also</span></span>

* [<span data-ttu-id="656a2-301">MR Basics 101: proyecto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="656a2-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="656a2-302">Gaze</span><span class="sxs-lookup"><span data-stu-id="656a2-302">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="656a2-303">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="656a2-303">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="656a2-304">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="656a2-304">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="656a2-305">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="656a2-305">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="656a2-306">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="656a2-306">Spatial mapping</span></span>](spatial-mapping.md)
