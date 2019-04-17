---
title: Conceptos básicos de MR 101E - proyecto completo con el emulador
description: Siga este tutorial con Unity, Visual Studio y el emulador de HoloLens para obtener información sobre los conceptos básicos de una aplicación holográfica de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, emulador tutorial, academy,
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599407"
---
>[!NOTE]
><span data-ttu-id="e18c3-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="e18c3-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e18c3-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="e18c3-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e18c3-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="e18c3-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e18c3-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="e18c3-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e18c3-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e18c3-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e18c3-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="e18c3-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="e18c3-110">Conceptos básicos de MR 101E: Proyecto completo con el emulador</span><span class="sxs-lookup"><span data-stu-id="e18c3-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="e18c3-111">Este tutorial le guiará a través de un proyecto completo, compilado en Unity, que muestra las características de Windows Mixed Reality principales en incluidos HoloLens [que mirar](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e18c3-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="e18c3-112">El tutorial tardará aproximadamente una hora en completarse.</span><span class="sxs-lookup"><span data-stu-id="e18c3-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="e18c3-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e18c3-114">Curso</span><span class="sxs-lookup"><span data-stu-id="e18c3-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e18c3-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e18c3-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e18c3-116"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="e18c3-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e18c3-117">Conceptos básicos de MR 101E: Proyecto completo con el emulador</span><span class="sxs-lookup"><span data-stu-id="e18c3-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="e18c3-118">✔️</span><span class="sxs-lookup"><span data-stu-id="e18c3-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e18c3-119">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="e18c3-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e18c3-120">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="e18c3-120">Prerequisites</span></span>

* <span data-ttu-id="e18c3-121">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="e18c3-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="e18c3-122">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="e18c3-122">Project files</span></span>

* <span data-ttu-id="e18c3-123">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="e18c3-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="e18c3-124"> Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="e18c3-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="e18c3-125">Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="e18c3-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="e18c3-126">Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="e18c3-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="e18c3-127">Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="e18c3-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="e18c3-128">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="e18c3-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="e18c3-129">Mantenga el nombre de carpeta **Origami**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="e18c3-130">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="e18c3-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="e18c3-131">Capítulo 1: "Holo" world</span><span class="sxs-lookup"><span data-stu-id="e18c3-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="e18c3-132">En este capítulo, crearemos nuestro primer proyecto de Unity y paso a través de la compilación de la instalación y proceso de implementación.</span><span class="sxs-lookup"><span data-stu-id="e18c3-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="e18c3-133">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-133">Objectives</span></span>

* <span data-ttu-id="e18c3-134">Configuración de Unity para desarrollo holográfica.</span><span class="sxs-lookup"><span data-stu-id="e18c3-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="e18c3-135">Realice un holograma.</span><span class="sxs-lookup"><span data-stu-id="e18c3-135">Make a hologram.</span></span>
* <span data-ttu-id="e18c3-136">Vea un holograma que haya realizado.</span><span class="sxs-lookup"><span data-stu-id="e18c3-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="e18c3-137">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="e18c3-137">Instructions</span></span>

* <span data-ttu-id="e18c3-138">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="e18c3-138">Start Unity.</span></span>
* <span data-ttu-id="e18c3-139">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-139">Select **Open**.</span></span>
* <span data-ttu-id="e18c3-140">Escriba la ubicación que el **Origami** carpeta que anteriormente no archivados.</span><span class="sxs-lookup"><span data-stu-id="e18c3-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="e18c3-141">Seleccione **Origami** y haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="e18c3-142">Guarde la nueva escena: **Archivo** / **Guardar escena como**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="e18c3-143">Nombre de la escena **Origami** y presione la **guardar** botón.</span><span class="sxs-lookup"><span data-stu-id="e18c3-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="e18c3-144">Programa de instalación de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="e18c3-144">Setup the main camera</span></span>

* <span data-ttu-id="e18c3-145">En el **jerarquía Panel**, seleccione **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="e18c3-146">En el **Inspector** establecer su posición de la transformación a **0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="e18c3-147">Buscar el **borrar las marcas** propiedad y cambie la lista desplegable de **Skybox** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="e18c3-148">Haga clic en el **en segundo plano** campo para abrir un selector de colores.</span><span class="sxs-lookup"><span data-stu-id="e18c3-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="e18c3-149">Establecer **R, G, B y A** a **0**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="e18c3-150">Programa de instalación de la escena</span><span class="sxs-lookup"><span data-stu-id="e18c3-150">Setup the scene</span></span>

* <span data-ttu-id="e18c3-151">En el **jerarquía Panel**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="e18c3-152">Haga clic en el nuevo **GameObject** y seleccione Cambiar nombre.</span><span class="sxs-lookup"><span data-stu-id="e18c3-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="e18c3-153">Cambiar el nombre de la GameObject a **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="e18c3-154">Desde el **hologramas** carpeta en el **Panel proyecto**:</span><span class="sxs-lookup"><span data-stu-id="e18c3-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="e18c3-155">Arrastre **fase** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="e18c3-156">Arrastre **Sphere1** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="e18c3-157">Arrastre **Sphere2** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="e18c3-158">Haga clic en el **luz direccional** objeto en el **jerarquía Panel** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="e18c3-159">Desde el **hologramas** carpeta, arrastre **luces** en la raíz de la **jerarquía Panel**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="e18c3-160">En el **jerarquía**, seleccione el **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="e18c3-161">En el **Inspector**, establezca la posición de la transformación en **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="e18c3-162">Presione el **reproducir** en Unity para obtener una vista previa de sus hologramas botón.</span><span class="sxs-lookup"><span data-stu-id="e18c3-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="e18c3-163">Debería ver los objetos de Origami en la ventana Vista previa.</span><span class="sxs-lookup"><span data-stu-id="e18c3-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="e18c3-164">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="e18c3-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="e18c3-165">Exporta el proyecto de Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e18c3-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="e18c3-166">En Seleccione Unity **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="e18c3-167">Seleccione **Windows Store** en el **plataforma** lista y haga clic en **Cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="e18c3-168">Establecer **SDK** a **10 Universal** y **tipo de compilación** a **D3D**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="e18c3-169">Comprobar **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="e18c3-170">Haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="e18c3-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="e18c3-171">Haga clic en **configuración del Reproductor...** .</span><span class="sxs-lookup"><span data-stu-id="e18c3-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="e18c3-172">En, seleccione el Panel Inspector el **logotipo de Windows Store**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="e18c3-173">A continuación, seleccione **configuración de publicación**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="e18c3-174">En el **capacidades** sección, seleccione el **micrófono** y **SpatialPerception** capacidades.</span><span class="sxs-lookup"><span data-stu-id="e18c3-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="e18c3-175">En la ventana de configuración de compilación, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="e18c3-176">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="e18c3-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="e18c3-177">Solo haga clic en el **carpeta aplicación**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="e18c3-178">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="e18c3-179">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="e18c3-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="e18c3-180">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="e18c3-180">Open the **App** folder.</span></span>
* <span data-ttu-id="e18c3-181">Abra el **solución de Visual Studio Origami**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="e18c3-182">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X86**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="e18c3-183">Haga clic en la flecha situada junto al botón del dispositivo y seleccione **emulador de HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="e18c3-184">Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="e18c3-185">Más tarde el emulador se inicia con el proyecto Origami.</span><span class="sxs-lookup"><span data-stu-id="e18c3-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="e18c3-186">Cuando se inicia en primer lugar el [emulador](using-the-hololens-emulator.md), puede tardar hasta 15 minutos para iniciar el emulador.</span><span class="sxs-lookup"><span data-stu-id="e18c3-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="e18c3-187">Una vez se inicia, no lo cierre.</span><span class="sxs-lookup"><span data-stu-id="e18c3-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="e18c3-188">Capítulo 2: mirada</span><span class="sxs-lookup"><span data-stu-id="e18c3-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="e18c3-189">En este capítulo, vamos a introducir la primera de estas tres maneras de interactuar con sus hologramas-- [que mirar](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="e18c3-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="e18c3-190">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-190">Objectives</span></span>

* <span data-ttu-id="e18c3-191">Visualice a su mirada mediante un cursor bloqueado por el mundo.</span><span class="sxs-lookup"><span data-stu-id="e18c3-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="e18c3-192">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="e18c3-192">Instructions</span></span>

* <span data-ttu-id="e18c3-193">Vuelva a su proyecto de Unity y cerrar la ventana de configuración de compilación si aún está abierta.</span><span class="sxs-lookup"><span data-stu-id="e18c3-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="e18c3-194">Seleccione el **hologramas** carpeta en el **panel proyecto**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="e18c3-195">Arrastre el **Cursor** objeto en el **panel jerarquía** en el nivel raíz.</span><span class="sxs-lookup"><span data-stu-id="e18c3-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="e18c3-196">Haga doble clic en el **Cursor** objeto vistazo más de cerca.</span><span class="sxs-lookup"><span data-stu-id="e18c3-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="e18c3-197">Haga doble clic en el **Scripts** carpeta en el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="e18c3-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="e18c3-198">Haga clic en el **crear** submenú.</span><span class="sxs-lookup"><span data-stu-id="e18c3-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="e18c3-199">Seleccione  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-199">Select **C# Script**.</span></span>
* <span data-ttu-id="e18c3-200">Nombre de la secuencia de comandos **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="e18c3-201">Nota: El nombre distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="e18c3-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="e18c3-202">No es necesario agregar la extensión. cs.</span><span class="sxs-lookup"><span data-stu-id="e18c3-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="e18c3-203">Seleccione el **Cursor** objeto en el **panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="e18c3-204">Arrastre y coloque el **WorldCursor** de script en el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="e18c3-205">Haga doble clic en el **WorldCursor** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e18c3-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="e18c3-206">Copie y pegue este código en **WorldCursor.cs** y **guardar todo**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="e18c3-207">Vuelva a compilar la aplicación de **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="e18c3-208">Vuelva a la solución de Visual Studio que anteriormente se usa para implementar en el emulador.</span><span class="sxs-lookup"><span data-stu-id="e18c3-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="e18c3-209">Seleccione "Volver a cargar todo" cuando se le solicite.</span><span class="sxs-lookup"><span data-stu-id="e18c3-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="e18c3-210">Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="e18c3-211">Usar el controlador de Xbox para buscar en torno a la escena.</span><span class="sxs-lookup"><span data-stu-id="e18c3-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="e18c3-212">Tenga en cuenta cómo interactúa el cursor con la forma de objetos.</span><span class="sxs-lookup"><span data-stu-id="e18c3-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="e18c3-213">Capítulo 3: gestos</span><span class="sxs-lookup"><span data-stu-id="e18c3-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="e18c3-214">En este capítulo, se agregará compatibilidad para [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="e18c3-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="e18c3-215">Cuando el usuario selecciona una esfera de papel, nos aseguraremos de hacer la esfera se dividen activando gravedad mediante el motor de leyes físicas de Unity.</span><span class="sxs-lookup"><span data-stu-id="e18c3-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="e18c3-216">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-216">Objectives</span></span>

* <span data-ttu-id="e18c3-217">Controlar las hologramas con el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="e18c3-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="e18c3-218">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="e18c3-218">Instructions</span></span>

<span data-ttu-id="e18c3-219">Comenzaremos por crear una secuencia de comandos que puede detectar el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="e18c3-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="e18c3-220">En el **Scripts** carpeta, cree un script denominado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="e18c3-221">Arrastre el **GazeGestureManager** de script en el **OrigamiCollection** objeto en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="e18c3-222">Abra el **GazeGestureManager** de script en Visual Studio y agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="e18c3-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="e18c3-223">Cree otra secuencia de comandos en la carpeta de Scripts, esta vez denominada **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="e18c3-224">Expanda el **OrigamiCollection** objeto en la vista de jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="e18c3-225">Arrastre el **SphereCommands** de script en el **Sphere1** objeto en el panel de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="e18c3-226">Arrastre el **SphereCommands** de script en el **Sphere2** objeto en el panel de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="e18c3-227">Abra el script en Visual Studio para editar y reemplace el código predeterminado con esto:</span><span class="sxs-lookup"><span data-stu-id="e18c3-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="e18c3-228">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e18c3-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="e18c3-229">Mire en torno a la escena y centrar en uno de los ámbitos.</span><span class="sxs-lookup"><span data-stu-id="e18c3-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="e18c3-230">Presione el **A** situado en el controlador de Xbox o presione la barra espaciadora para simular el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="e18c3-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="e18c3-231">Capítulo 4 - voz</span><span class="sxs-lookup"><span data-stu-id="e18c3-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="e18c3-232">En este capítulo, se agregará compatibilidad para dos [comandos de voz](voice-input.md): "Restablecer world" para devuelve las esferas colocarlo en su ubicación original y "Colocar sphere" para realizar la esfera se encuentran.</span><span class="sxs-lookup"><span data-stu-id="e18c3-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="e18c3-233">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-233">Objectives</span></span>

* <span data-ttu-id="e18c3-234">Agregar comandos de voz que siempre escuchan en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="e18c3-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="e18c3-235">Cree un holograma que reacciona a un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="e18c3-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="e18c3-236">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="e18c3-236">Instructions</span></span>

* <span data-ttu-id="e18c3-237">En el **Scripts** carpeta, cree un script denominado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="e18c3-238">Arrastre el **SpeechManager** de script en el **OrigamiCollection** objeto en la jerarquía</span><span class="sxs-lookup"><span data-stu-id="e18c3-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="e18c3-239">Abra el **SpeechManager** script en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e18c3-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="e18c3-240">Copie y pegue este código en **SpeechManager.cs** y **guardar todo**:</span><span class="sxs-lookup"><span data-stu-id="e18c3-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="e18c3-241">Abra el **SphereCommands** script en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e18c3-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="e18c3-242">Actualice el script para que quede como sigue:</span><span class="sxs-lookup"><span data-stu-id="e18c3-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="e18c3-243">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e18c3-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="e18c3-244">El emulador admitirá micrófono de su PC y responder a su voz: ajustar la vista de modo que el cursor está en uno de los ámbitos y diga "Drop esfera".</span><span class="sxs-lookup"><span data-stu-id="e18c3-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="e18c3-245">Por ejemplo "**restablecer World**" para llevarlas nuevamente a sus posiciones iniciales.</span><span class="sxs-lookup"><span data-stu-id="e18c3-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="e18c3-246">Capítulo 5: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="e18c3-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="e18c3-247">En este capítulo, se deberá agregar música a la aplicación y, a continuación, desencadenar efectos de sonido en determinadas acciones.</span><span class="sxs-lookup"><span data-stu-id="e18c3-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="e18c3-248">Vamos a usar [sonido espacial](spatial-sound.md) para proporcionar a los sonidos de una ubicación específica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="e18c3-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="e18c3-249">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-249">Objectives</span></span>

* <span data-ttu-id="e18c3-250">Escuche hologramas en el mundo.</span><span class="sxs-lookup"><span data-stu-id="e18c3-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="e18c3-251">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="e18c3-251">Instructions</span></span>

* <span data-ttu-id="e18c3-252">En el, en el menú superior seleccione Unity **Editar > configuración del proyecto > Audio**</span><span class="sxs-lookup"><span data-stu-id="e18c3-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="e18c3-253">Buscar el **espacial complemento** configuración y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="e18c3-254">Desde el **hologramas** carpeta, arrastre el **ambiente** objeto en el **OrigamiCollection** objeto en el Panel de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="e18c3-255">Seleccione **OrigamiCollection** y busque el **origen Audio** componente.</span><span class="sxs-lookup"><span data-stu-id="e18c3-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="e18c3-256">Cambiar estas propiedades:</span><span class="sxs-lookup"><span data-stu-id="e18c3-256">Change these properties:</span></span>
  * <span data-ttu-id="e18c3-257">Compruebe el **Spatialize** propiedad.</span><span class="sxs-lookup"><span data-stu-id="e18c3-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="e18c3-258">Compruebe el **reproducir en activo**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="e18c3-259">Cambio **Blend espacial** a **3D** arrastrando el control deslizante totalmente hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="e18c3-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="e18c3-260">Compruebe el **bucle** propiedad.</span><span class="sxs-lookup"><span data-stu-id="e18c3-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="e18c3-261">Expanda **configuración sonido 3D**y escriba **0,1** para **nivel Doppler**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="e18c3-262">Establecer **volumen atenuación** a **atenuación logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="e18c3-263">Establecer **distancia máxima** a **20**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="e18c3-264">En el **Scripts** carpeta, cree un script denominado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="e18c3-265">Arrastre **SphereSounds** a la **Sphere1** y **Sphere2** objetos de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="e18c3-266">Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guardar todo**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="e18c3-267">Guarde el script y volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="e18c3-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="e18c3-268">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e18c3-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="e18c3-269">Utilizar auriculares para obtener el efecto completo y mover más cercana y nada más lejos de la fase oír el sonido a cambiar.</span><span class="sxs-lookup"><span data-stu-id="e18c3-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="e18c3-270">Asignación de capítulo 6: espacial</span><span class="sxs-lookup"><span data-stu-id="e18c3-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="e18c3-271">Ahora vamos a usar [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="e18c3-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="e18c3-272">Objetivos</span><span class="sxs-lookup"><span data-stu-id="e18c3-272">Objectives</span></span>

* <span data-ttu-id="e18c3-273">Ponga el mundo real en el mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="e18c3-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="e18c3-274">Coloque sus hologramas donde más le interesen.</span><span class="sxs-lookup"><span data-stu-id="e18c3-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="e18c3-275">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="e18c3-275">Instructions</span></span>

* <span data-ttu-id="e18c3-276">Haga clic en el **hologramas** carpeta en el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="e18c3-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="e18c3-277">Arrastre el **asignación espacial** activo en la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="e18c3-278">Haga clic en el **asignación espacial** objeto en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="e18c3-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="e18c3-279">En el **panel Inspector**, cambie las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="e18c3-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="e18c3-280">Compruebe el **dibujar mallas Visual** cuadro.</span><span class="sxs-lookup"><span data-stu-id="e18c3-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="e18c3-281">Busque **dibujar Material** y haga clic en el círculo de la derecha.</span><span class="sxs-lookup"><span data-stu-id="e18c3-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="e18c3-282">Tipo de "**tramas de alambres**" en el campo de búsqueda en la parte superior.</span><span class="sxs-lookup"><span data-stu-id="e18c3-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="e18c3-283">Haga clic en el resultado y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="e18c3-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="e18c3-284">Exportar, compilar e implementar la aplicación en el emulador de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e18c3-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="e18c3-285">Cuando se ejecuta la aplicación, se representará una malla de una sala de estar previamente digitalizada reales en tramas de alambres.</span><span class="sxs-lookup"><span data-stu-id="e18c3-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="e18c3-286">Vea cómo una esfera gradual estarán fuera del escenario y en el suelo.</span><span class="sxs-lookup"><span data-stu-id="e18c3-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="e18c3-287">Ahora vamos a mostrarle cómo mover la OrigamiCollection a una nueva ubicación:</span><span class="sxs-lookup"><span data-stu-id="e18c3-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="e18c3-288">En el **Scripts** carpeta, cree un script denominado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="e18c3-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="e18c3-289">En el **jerarquía**, expanda el **OrigamiCollection** y seleccione el **fase** objeto.</span><span class="sxs-lookup"><span data-stu-id="e18c3-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="e18c3-290">Arrastre el **TapToPlaceParent** script en el objeto de fase.</span><span class="sxs-lookup"><span data-stu-id="e18c3-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="e18c3-291">Abra el **TapToPlaceParent** de script en Visual Studio y actualizarlo para que sea lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e18c3-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="e18c3-292">Exportar, compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e18c3-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="e18c3-293">Ahora ahora podrá colocar el juego en una ubicación específica mediante gazing en él, mediante el gesto de Select (**A** o la barra espaciadora) y, a continuación, pasar a una nueva ubicación y volver a usar el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="e18c3-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="e18c3-294">Fin</span><span class="sxs-lookup"><span data-stu-id="e18c3-294">The end</span></span>

<span data-ttu-id="e18c3-295">Y es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="e18c3-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="e18c3-296">Ha aprendido conceptos:</span><span class="sxs-lookup"><span data-stu-id="e18c3-296">You learned:</span></span>

* <span data-ttu-id="e18c3-297">Cómo crear una aplicación holográfica en Unity.</span><span class="sxs-lookup"><span data-stu-id="e18c3-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="e18c3-298">Cómo hacer que el uso de mirada, gestos, voz, sonidos y asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="e18c3-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="e18c3-299">Cómo compilar e implementar una aplicación mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e18c3-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="e18c3-300">Ahora está listo para comenzar a crear sus propias aplicaciones holográficas.</span><span class="sxs-lookup"><span data-stu-id="e18c3-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="e18c3-301">Vea también</span><span class="sxs-lookup"><span data-stu-id="e18c3-301">See also</span></span>

* [<span data-ttu-id="e18c3-302">Conceptos básicos de MR 101: Proyecto completo con el dispositivo</span><span class="sxs-lookup"><span data-stu-id="e18c3-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="e18c3-303">Gaze</span><span class="sxs-lookup"><span data-stu-id="e18c3-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="e18c3-304">Gestos</span><span class="sxs-lookup"><span data-stu-id="e18c3-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="e18c3-305">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="e18c3-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="e18c3-306">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="e18c3-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="e18c3-307">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="e18c3-307">Spatial mapping</span></span>](spatial-mapping.md)
