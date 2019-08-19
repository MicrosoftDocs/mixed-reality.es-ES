---
title: MR Basics 101E-completar proyecto con Emulator
description: Siga este tutorial de codificación con Unity, Visual Studio y el emulador de HoloLens para aprender los conceptos básicos de una aplicación holográfica.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, Academy, tutorial, emulador
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522321"
---
>[!NOTE]
><span data-ttu-id="1efb1-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="1efb1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1efb1-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1efb1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1efb1-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1efb1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1efb1-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="1efb1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1efb1-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1efb1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1efb1-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="1efb1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="1efb1-110">101E de datos básicos de MR: Proyecto completo con el emulador</span><span class="sxs-lookup"><span data-stu-id="1efb1-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="1efb1-111">Este tutorial le guiará a través de un proyecto completo, integrado en Unity, que muestra características básicas de Windows Mixed Reality en HoloLens, como [miradas](gaze.md), [gestos](gestures.md), [entrada de voz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="1efb1-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="1efb1-112">El tutorial tardará aproximadamente 1 hora en completarse.</span><span class="sxs-lookup"><span data-stu-id="1efb1-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="1efb1-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1efb1-114">Recurso</span><span class="sxs-lookup"><span data-stu-id="1efb1-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1efb1-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1efb1-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1efb1-116"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="1efb1-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1efb1-117">101E de datos básicos de MR: Proyecto completo con el emulador</span><span class="sxs-lookup"><span data-stu-id="1efb1-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="1efb1-118">✔️</span><span class="sxs-lookup"><span data-stu-id="1efb1-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1efb1-119">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="1efb1-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1efb1-120">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1efb1-120">Prerequisites</span></span>

* <span data-ttu-id="1efb1-121">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.</span><span class="sxs-lookup"><span data-stu-id="1efb1-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="1efb1-122">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="1efb1-122">Project files</span></span>

* <span data-ttu-id="1efb1-123">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1efb1-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="1efb1-124"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="1efb1-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="1efb1-125">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="1efb1-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="1efb1-126">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="1efb1-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="1efb1-127">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="1efb1-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="1efb1-128">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="1efb1-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="1efb1-129">Mantenga el nombre de la carpeta como **origami**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="1efb1-130">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="1efb1-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="1efb1-131">Capítulo 1: mundo "Hololens"</span><span class="sxs-lookup"><span data-stu-id="1efb1-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="1efb1-132">En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="1efb1-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="1efb1-133">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-133">Objectives</span></span>

* <span data-ttu-id="1efb1-134">Configure Unity para el desarrollo holográfica.</span><span class="sxs-lookup"><span data-stu-id="1efb1-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="1efb1-135">Cree un holograma.</span><span class="sxs-lookup"><span data-stu-id="1efb1-135">Make a hologram.</span></span>
* <span data-ttu-id="1efb1-136">Vea un holograma que haya realizado.</span><span class="sxs-lookup"><span data-stu-id="1efb1-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="1efb1-137">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1efb1-137">Instructions</span></span>

* <span data-ttu-id="1efb1-138">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="1efb1-138">Start Unity.</span></span>
* <span data-ttu-id="1efb1-139">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-139">Select **Open**.</span></span>
* <span data-ttu-id="1efb1-140">Escriba ubicación como la carpeta **origami** que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="1efb1-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="1efb1-141">Seleccione **origami** y haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="1efb1-142">Guarde la nueva escena:Archivo / :**Guardar escena como**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="1efb1-143">Asigne a la escena el nombre **origami** y haga clic en el botón **Guardar** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="1efb1-144">Configuración de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="1efb1-144">Setup the main camera</span></span>

* <span data-ttu-id="1efb1-145">En el **Panel jerarquía**, seleccione **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="1efb1-146">En el **Inspector** , establezca su posición de transformación en **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="1efb1-147">Busque la propiedad **Borrar marcas** y cambie la lista desplegable de **SKYBOX** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="1efb1-148">Haga clic en el campo **fondo** para abrir un selector de colores.</span><span class="sxs-lookup"><span data-stu-id="1efb1-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="1efb1-149">Establezca **R, G, B y** a en **0**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="1efb1-150">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="1efb1-150">Setup the scene</span></span>

* <span data-ttu-id="1efb1-151">En el **Panel jerarquía**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="1efb1-152">Haga clic con el botón derecho en el nuevo **GameObject** y seleccione Cambiar nombre.</span><span class="sxs-lookup"><span data-stu-id="1efb1-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="1efb1-153">Cambie el nombre de GameObject a **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="1efb1-154">En la carpeta hologramas del **panel Proyecto**:</span><span class="sxs-lookup"><span data-stu-id="1efb1-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="1efb1-155">Arrastre **Stage** hasta la jerarquía para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="1efb1-156">Arrastre **Sphere1** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="1efb1-157">Arrastre **Sphere2** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="1efb1-158">Haga clic con el botón secundario en el objeto de **luz direccional** en el **Panel jerarquía** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="1efb1-159">En la carpeta hologramas, arrastre **Lights** hasta la raíz del **Panel de jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="1efb1-160">En la **jerarquía**, seleccione el **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="1efb1-161">En el **Inspector**, establezca la posición de la transformación en **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="1efb1-162">Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="1efb1-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="1efb1-163">Debería ver los objetos origami en la ventana de vista previa.</span><span class="sxs-lookup"><span data-stu-id="1efb1-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="1efb1-164">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="1efb1-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="1efb1-165">Exportar el proyecto de Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1efb1-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="1efb1-166">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="1efb1-167">Seleccione **tienda Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="1efb1-168">Establezca **SDK** en **universal 10** y **tipo de compilación** en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="1efb1-169">Compruebe **los C# proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="1efb1-170">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="1efb1-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="1efb1-171">Haga clic en **configuración del reproductor..** ..</span><span class="sxs-lookup"><span data-stu-id="1efb1-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="1efb1-172">En el panel Inspector, seleccione el logotipo de la **tienda Windows**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="1efb1-173">A continuación, seleccione **configuración de publicación**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="1efb1-174">En la sección **capacidades** , seleccione las capacidades **micrófono** y **SpatialPerception** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="1efb1-175">De nuevo en la ventana Configuración de compilación, haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="1efb1-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="1efb1-176">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="1efb1-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="1efb1-177">Haga clic en la carpeta de la **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="1efb1-178">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="1efb1-179">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="1efb1-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="1efb1-180">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-180">Open the **App** folder.</span></span>
* <span data-ttu-id="1efb1-181">Abra la **solución origami de Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="1efb1-182">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="1efb1-183">Haga clic en la flecha situada junto al botón dispositivo y seleccione **emulador de HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="1efb1-184">Haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="1efb1-185">Después de algún tiempo, el emulador comenzará con el proyecto origami.</span><span class="sxs-lookup"><span data-stu-id="1efb1-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="1efb1-186">Al iniciar el [emulador](using-the-hololens-emulator.md)por primera vez, el emulador puede tardar hasta 15 minutos en iniciarse.</span><span class="sxs-lookup"><span data-stu-id="1efb1-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="1efb1-187">Una vez que se inicia, no lo cierre.</span><span class="sxs-lookup"><span data-stu-id="1efb1-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="1efb1-188">Capítulo 2: mira hacia abajo</span><span class="sxs-lookup"><span data-stu-id="1efb1-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="1efb1-189">En este capítulo, vamos a presentar la primera de las tres formas de interactuar con los hologramas: [mirada](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="1efb1-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="1efb1-190">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-190">Objectives</span></span>

* <span data-ttu-id="1efb1-191">Visualice la mirada con un cursor de un mundo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="1efb1-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="1efb1-192">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1efb1-192">Instructions</span></span>

* <span data-ttu-id="1efb1-193">Vuelva al proyecto de Unity y cierre la ventana de configuración de la compilación si aún está abierta.</span><span class="sxs-lookup"><span data-stu-id="1efb1-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="1efb1-194">Seleccione la carpeta hologramas en el **panel Proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="1efb1-195">Arrastre el objeto **cursor** al **Panel jerarquía** en el nivel raíz.</span><span class="sxs-lookup"><span data-stu-id="1efb1-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="1efb1-196">Haga doble clic en el objeto **cursor** para examinarlo más detenidamente.</span><span class="sxs-lookup"><span data-stu-id="1efb1-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="1efb1-197">Haga clic con el botón secundario en la carpeta scripts en el panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="1efb1-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="1efb1-198">Haga clic en el submenú **crear** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="1efb1-199">Seleccione  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-199">Select **C# Script**.</span></span>
* <span data-ttu-id="1efb1-200">Asigne al script el nombre **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="1efb1-201">Nota: El nombre distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="1efb1-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="1efb1-202">No es necesario agregar la extensión. cs.</span><span class="sxs-lookup"><span data-stu-id="1efb1-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="1efb1-203">Seleccione el objeto **cursor** en el **Panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="1efb1-204">Arrastre y coloque el script **WorldCursor** en el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="1efb1-205">Haga doble clic en el script **WorldCursor** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1efb1-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="1efb1-206">Copie y pegue este código en **WorldCursor.CS** y **guarde todo**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="1efb1-207">Vuelva a compilar la aplicación desde el **archivo > la configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="1efb1-208">Vuelva a la solución de Visual Studio que se usó anteriormente para implementar en el emulador.</span><span class="sxs-lookup"><span data-stu-id="1efb1-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="1efb1-209">Seleccione "recargar todo" cuando se le solicite.</span><span class="sxs-lookup"><span data-stu-id="1efb1-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="1efb1-210">Haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="1efb1-211">Use el controlador Xbox para buscar en torno a la escena.</span><span class="sxs-lookup"><span data-stu-id="1efb1-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="1efb1-212">Observe cómo interactúa el cursor con la forma de los objetos.</span><span class="sxs-lookup"><span data-stu-id="1efb1-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="1efb1-213">Capítulo 3: gestos</span><span class="sxs-lookup"><span data-stu-id="1efb1-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="1efb1-214">En este capítulo, se agregará compatibilidad con [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="1efb1-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="1efb1-215">Cuando el usuario selecciona una esfera de papel, haremos que la esfera se active al activar la gravedad mediante el motor físico de Unity.</span><span class="sxs-lookup"><span data-stu-id="1efb1-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="1efb1-216">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-216">Objectives</span></span>

* <span data-ttu-id="1efb1-217">Controle los hologramas con el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="1efb1-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="1efb1-218">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1efb1-218">Instructions</span></span>

<span data-ttu-id="1efb1-219">Comenzaremos por crear un script que pueda detectar el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="1efb1-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="1efb1-220">En la carpeta scripts, cree un script denominado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="1efb1-221">Arrastre el script **GazeGestureManager** hasta el objeto **OrigamiCollection** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="1efb1-222">Abra el script **GazeGestureManager** en Visual Studio y agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="1efb1-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="1efb1-223">Cree otro script en la carpeta scripts, esta vez con el nombre **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="1efb1-224">Expanda el objeto **OrigamiCollection** en la vista de jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="1efb1-225">Arrastre el script **SphereCommands** al objeto **Sphere1** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="1efb1-226">Arrastre el script **SphereCommands** al objeto **Sphere2** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="1efb1-227">Abra el script en Visual Studio para editarlo y reemplace el código predeterminado por este:</span><span class="sxs-lookup"><span data-stu-id="1efb1-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="1efb1-228">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1efb1-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="1efb1-229">Buscar en la escena y centrar en uno de los esferas.</span><span class="sxs-lookup"><span data-stu-id="1efb1-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="1efb1-230">Presione el **botón a** del controlador Xbox o presione la barra espaciadora para simular el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="1efb1-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="1efb1-231">Capítulo 4: voz</span><span class="sxs-lookup"><span data-stu-id="1efb1-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="1efb1-232">En este capítulo, se agregará compatibilidad con dos [comandos de voz](voice-input.md): "RESET World" para devolver los esferas quitados a su ubicación original y "Drop Sphere" para que la esfera quede.</span><span class="sxs-lookup"><span data-stu-id="1efb1-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="1efb1-233">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-233">Objectives</span></span>

* <span data-ttu-id="1efb1-234">Agregue comandos de voz que siempre escuchan en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="1efb1-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="1efb1-235">Cree un holograma que reaccione a un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="1efb1-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="1efb1-236">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1efb1-236">Instructions</span></span>

* <span data-ttu-id="1efb1-237">En la carpeta scripts, cree un script denominado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="1efb1-238">Arrastre el script **SpeechManager** hasta el objeto **OrigamiCollection** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="1efb1-239">Abra el script **SpeechManager** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1efb1-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="1efb1-240">Copie y pegue este código en **SpeechManager.CS** y **guarde todo**:</span><span class="sxs-lookup"><span data-stu-id="1efb1-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="1efb1-241">Abra el script **SphereCommands** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1efb1-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="1efb1-242">Actualice el script para que se lea de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="1efb1-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="1efb1-243">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1efb1-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="1efb1-244">El emulador admitirá el micrófono del equipo y responderá a su voz: ajuste la vista para que el cursor esté en uno de los esferas y Supongamos "esfera de colocación".</span><span class="sxs-lookup"><span data-stu-id="1efb1-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="1efb1-245">Por ejemplo, "**restablecer mundo**" para volver a colocarlos en sus posiciones iniciales.</span><span class="sxs-lookup"><span data-stu-id="1efb1-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="1efb1-246">Capítulo 5: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="1efb1-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="1efb1-247">En este capítulo, agregaremos música a la aplicación y, a continuación, desencadenaremos efectos sonoros en determinadas acciones.</span><span class="sxs-lookup"><span data-stu-id="1efb1-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="1efb1-248">Usaremos el [sonido espacial](spatial-sound.md) para proporcionar a los sonidos una ubicación específica en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="1efb1-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="1efb1-249">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-249">Objectives</span></span>

* <span data-ttu-id="1efb1-250">Escuche los hologramas de su mundo.</span><span class="sxs-lookup"><span data-stu-id="1efb1-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="1efb1-251">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1efb1-251">Instructions</span></span>

* <span data-ttu-id="1efb1-252">En la selección de Unity, en el menú superior, **edite > configuración del proyecto > audio**</span><span class="sxs-lookup"><span data-stu-id="1efb1-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="1efb1-253">Busque la configuración del **complemento de Spatializer** y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="1efb1-254">En la carpeta hologramas, arrastre el objeto **ambiente** hasta el objeto **OrigamiCollection** en el panel de jerarquías.</span><span class="sxs-lookup"><span data-stu-id="1efb1-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="1efb1-255">Seleccione **OrigamiCollection** y busque el componente de **origen de audio** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="1efb1-256">Cambie estas propiedades:</span><span class="sxs-lookup"><span data-stu-id="1efb1-256">Change these properties:</span></span>
  * <span data-ttu-id="1efb1-257">Compruebe la propiedad **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="1efb1-258">Active la casilla **reproducir en activo**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="1efb1-259">Cambie la **mezcla espacial** a **3D** arrastrando el control deslizante hasta la derecha.</span><span class="sxs-lookup"><span data-stu-id="1efb1-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="1efb1-260">Compruebe la propiedad **Loop** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="1efb1-261">Expanda **configuración de sonido 3D**y escriba **0,1** para el **nivel de Doppler**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="1efb1-262">Establezca **rolloff de volumen** en **rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="1efb1-263">Establezca la **distancia máxima** en **20**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="1efb1-264">En la carpeta scripts, cree un script denominado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="1efb1-265">Arrastre **SphereSounds** a los objetos **Sphere1** y **Sphere2** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="1efb1-266">Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guarde todo**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="1efb1-267">Guarde el script y vuelva a Unity.</span><span class="sxs-lookup"><span data-stu-id="1efb1-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="1efb1-268">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1efb1-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="1efb1-269">Use auriculares para conseguir el efecto completo y vaya más cerca y después de la fase para oír el cambio de los sonidos.</span><span class="sxs-lookup"><span data-stu-id="1efb1-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="1efb1-270">Capítulo 6: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="1efb1-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="1efb1-271">Ahora vamos a usar la [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real del mundo real.</span><span class="sxs-lookup"><span data-stu-id="1efb1-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="1efb1-272">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1efb1-272">Objectives</span></span>

* <span data-ttu-id="1efb1-273">Traiga su mundo real al mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="1efb1-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="1efb1-274">Coloque los hologramas donde más le importan.</span><span class="sxs-lookup"><span data-stu-id="1efb1-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="1efb1-275">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1efb1-275">Instructions</span></span>

* <span data-ttu-id="1efb1-276">Haga clic en la carpeta hologramas en el panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="1efb1-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="1efb1-277">Arrastre el recurso de **asignación espacial** a la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="1efb1-278">Haga clic en el objeto de **asignación espacial** en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1efb1-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="1efb1-279">En el **panel Inspector**, cambie las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="1efb1-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="1efb1-280">Active la casilla **dibujar mallas visuales** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="1efb1-281">Busque **material de dibujo** y haga clic en el círculo de la derecha.</span><span class="sxs-lookup"><span data-stu-id="1efb1-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="1efb1-282">Escriba "**Wireframe**" en el campo de búsqueda de la parte superior.</span><span class="sxs-lookup"><span data-stu-id="1efb1-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="1efb1-283">Haga clic en el resultado y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="1efb1-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="1efb1-284">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1efb1-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="1efb1-285">Cuando se ejecuta la aplicación, se representará en alambre una malla de una sala de reuniones del mundo real analizada previamente.</span><span class="sxs-lookup"><span data-stu-id="1efb1-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="1efb1-286">Vea cómo una esfera gradual se quedará fuera de la fase y en el suelo.</span><span class="sxs-lookup"><span data-stu-id="1efb1-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="1efb1-287">Ahora le mostraremos cómo trasladar el OrigamiCollection a una nueva ubicación:</span><span class="sxs-lookup"><span data-stu-id="1efb1-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="1efb1-288">En la carpeta scripts, cree un script denominado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="1efb1-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="1efb1-289">En la **jerarquía**, expanda **OrigamiCollection** y seleccione el objeto **Stage** .</span><span class="sxs-lookup"><span data-stu-id="1efb1-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="1efb1-290">Arrastre el script **TapToPlaceParent** hasta el objeto Stage.</span><span class="sxs-lookup"><span data-stu-id="1efb1-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="1efb1-291">Abra el script **TapToPlaceParent** en Visual Studio y actualícelo para que sea el siguiente:</span><span class="sxs-lookup"><span data-stu-id="1efb1-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="1efb1-292">Exportar, compilar e implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1efb1-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="1efb1-293">Ahora debería poder colocar el juego en una ubicación específica Gazing en él, con el gesto de selección (**a** o barra espaciadora) y, a continuación, desplazarse a una nueva ubicación y volver a usar el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="1efb1-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="1efb1-294">Fin</span><span class="sxs-lookup"><span data-stu-id="1efb1-294">The end</span></span>

<span data-ttu-id="1efb1-295">Y este es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="1efb1-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="1efb1-296">Aprendió:</span><span class="sxs-lookup"><span data-stu-id="1efb1-296">You learned:</span></span>

* <span data-ttu-id="1efb1-297">Cómo crear una aplicación holográfica en Unity.</span><span class="sxs-lookup"><span data-stu-id="1efb1-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="1efb1-298">Cómo hacer uso de la mirada, el gesto, la voz, los sonidos y la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="1efb1-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="1efb1-299">Cómo compilar e implementar una aplicación con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1efb1-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="1efb1-300">Ya está listo para empezar a crear sus propias aplicaciones holográficas.</span><span class="sxs-lookup"><span data-stu-id="1efb1-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="1efb1-301">Vea también</span><span class="sxs-lookup"><span data-stu-id="1efb1-301">See also</span></span>

* [<span data-ttu-id="1efb1-302">MR Basics 101: proyecto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="1efb1-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="1efb1-303">Gaze</span><span class="sxs-lookup"><span data-stu-id="1efb1-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="1efb1-304">Gestos</span><span class="sxs-lookup"><span data-stu-id="1efb1-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="1efb1-305">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="1efb1-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="1efb1-306">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="1efb1-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="1efb1-307">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="1efb1-307">Spatial mapping</span></span>](spatial-mapping.md)
