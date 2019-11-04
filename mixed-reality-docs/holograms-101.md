---
title: Sr Basics 101-proyecto completo con dispositivo
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los aspectos básicos de Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, Academy, tutorial
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434719"
---
>[!NOTE]
><span data-ttu-id="357c6-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="357c6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="357c6-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="357c6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="357c6-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="357c6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="357c6-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="357c6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="357c6-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="357c6-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="357c6-109">MR Basics 101: proyecto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="357c6-109">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="357c6-110">Este tutorial le guiará a través de un proyecto completo, integrado en Unity, que muestra características básicas de Windows Mixed Reality en HoloLens, como [mirados](gaze-and-commit.md), [gestos](gaze-and-commit.md#composite-gestures), [entrada de voz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md) . .</span><span class="sxs-lookup"><span data-stu-id="357c6-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="357c6-111">El tutorial tardará aproximadamente 1 hora en completarse.</span><span class="sxs-lookup"><span data-stu-id="357c6-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="357c6-112">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="357c6-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="357c6-113">Recurso</span><span class="sxs-lookup"><span data-stu-id="357c6-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="357c6-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="357c6-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="357c6-115"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="357c6-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="357c6-116">MR Basics 101: proyecto completo con dispositivo</span><span class="sxs-lookup"><span data-stu-id="357c6-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="357c6-117">✔️</span><span class="sxs-lookup"><span data-stu-id="357c6-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="357c6-118">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="357c6-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="357c6-119">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="357c6-119">Prerequisites</span></span>

* <span data-ttu-id="357c6-120">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="357c6-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="357c6-121">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="357c6-121">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="357c6-122">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="357c6-122">Project files</span></span>

* <span data-ttu-id="357c6-123">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="357c6-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="357c6-124"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="357c6-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="357c6-125">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="357c6-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="357c6-126">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="357c6-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="357c6-127">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="357c6-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="357c6-128">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="357c6-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="357c6-129">Mantenga el nombre de la carpeta como **origami**.</span><span class="sxs-lookup"><span data-stu-id="357c6-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="357c6-130">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="357c6-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="357c6-131">Capítulo 1: mundo "Hololens"</span><span class="sxs-lookup"><span data-stu-id="357c6-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="357c6-132">En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="357c6-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-133">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-133">Objectives</span></span>

* <span data-ttu-id="357c6-134">Configure Unity para el desarrollo holográfica.</span><span class="sxs-lookup"><span data-stu-id="357c6-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="357c6-135">Cree un holograma.</span><span class="sxs-lookup"><span data-stu-id="357c6-135">Make a hologram.</span></span>
* <span data-ttu-id="357c6-136">Vea un holograma que haya realizado.</span><span class="sxs-lookup"><span data-stu-id="357c6-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-137">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-137">Instructions</span></span>

* <span data-ttu-id="357c6-138">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="357c6-138">Start Unity.</span></span>
* <span data-ttu-id="357c6-139">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="357c6-139">Select **Open**.</span></span>
* <span data-ttu-id="357c6-140">Escriba ubicación como la carpeta **origami** que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="357c6-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="357c6-141">Seleccione **origami** y haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="357c6-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="357c6-142">Dado que el proyecto **origami** no contiene una escena, guarde la escena predeterminada vacía en un archivo nuevo con: **archivo** / **Guardar escena como**.</span><span class="sxs-lookup"><span data-stu-id="357c6-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="357c6-143">Asigne a la nueva escena el nombre **origami** y haga clic en el botón **Guardar** .</span><span class="sxs-lookup"><span data-stu-id="357c6-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="357c6-144">Configuración de la cámara virtual principal</span><span class="sxs-lookup"><span data-stu-id="357c6-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="357c6-145">En el **Panel jerarquía**, seleccione **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="357c6-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="357c6-146">En el **Inspector** , establezca su posición de transformación en **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="357c6-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="357c6-147">Busque la propiedad **Borrar marcas** y cambie la lista desplegable de **SKYBOX** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="357c6-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="357c6-148">Haga clic en el campo **fondo** para abrir un selector de colores.</span><span class="sxs-lookup"><span data-stu-id="357c6-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="357c6-149">Establezca **R, G, B y** a en **0**.</span><span class="sxs-lookup"><span data-stu-id="357c6-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="357c6-150">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="357c6-150">Setup the scene</span></span>

* <span data-ttu-id="357c6-151">En el **Panel jerarquía**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="357c6-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="357c6-152">Haga clic con el botón derecho en el nuevo **GameObject** y seleccione Cambiar nombre.</span><span class="sxs-lookup"><span data-stu-id="357c6-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="357c6-153">Cambie el nombre de GameObject a **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="357c6-154">En la carpeta **hologramas** del panel Proyecto (expanda activos y seleccione hologramas o haga doble clic en la carpeta hologramas en el panel Proyecto):</span><span class="sxs-lookup"><span data-stu-id="357c6-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="357c6-155">Arrastre **Stage** hasta la jerarquía para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="357c6-156">Arrastre **Sphere1** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="357c6-157">Arrastre **Sphere2** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="357c6-158">Haga clic con el botón secundario en el objeto de **luz direccional** en el **Panel jerarquía** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="357c6-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="357c6-159">En la carpeta **hologramas** , arrastre **Lights** hasta la raíz del **Panel de jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="357c6-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="357c6-160">En la **jerarquía**, seleccione el **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="357c6-161">En el **Inspector**, establezca la posición de la transformación en **0,-0,5, 2,0**.</span><span class="sxs-lookup"><span data-stu-id="357c6-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="357c6-162">Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="357c6-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="357c6-163">Debería ver los objetos origami en la ventana de vista previa.</span><span class="sxs-lookup"><span data-stu-id="357c6-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="357c6-164">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="357c6-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="357c6-165">Exportar el proyecto de Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="357c6-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="357c6-166">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="357c6-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="357c6-167">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="357c6-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="357c6-168">Establezca **SDK** en **universal 10** y **tipo de compilación** en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="357c6-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="357c6-169">Compruebe **los C# proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="357c6-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="357c6-170">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="357c6-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="357c6-171">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="357c6-171">Click **Build**.</span></span>
* <span data-ttu-id="357c6-172">En la ventana del explorador de archivos que aparece, cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="357c6-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="357c6-173">Haga clic en la carpeta de la **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="357c6-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="357c6-174">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="357c6-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="357c6-175">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="357c6-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="357c6-176">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="357c6-176">Open the **App** folder.</span></span>
* <span data-ttu-id="357c6-177">Abra (doble clic) **origami. sln**.</span><span class="sxs-lookup"><span data-stu-id="357c6-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="357c6-178">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="357c6-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="357c6-179">Haga clic en la flecha situada junto al botón dispositivo y seleccione **equipo remoto** para implementar a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="357c6-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="357c6-180">Establezca la **Dirección** en el nombre o la dirección IP de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="357c6-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="357c6-181">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas** o pregunte a Cortana **, ¿cuál es mi dirección IP? "** .</span><span class="sxs-lookup"><span data-stu-id="357c6-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="357c6-182">Si HoloLens está conectado a través de USB, puede seleccionar **dispositivo** para implementar a través de USB.</span><span class="sxs-lookup"><span data-stu-id="357c6-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="357c6-183">Deje el **modo de autenticación** establecido en **universal**.</span><span class="sxs-lookup"><span data-stu-id="357c6-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="357c6-184">Haga clic en **seleccionar**</span><span class="sxs-lookup"><span data-stu-id="357c6-184">Click **Select**</span></span>

* <span data-ttu-id="357c6-185">Haga clic en **Depurar > iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="357c6-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="357c6-186">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="357c6-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="357c6-187">Ahora se compilará el proyecto origami, se implementará en HoloLens y, a continuación, se ejecutará.</span><span class="sxs-lookup"><span data-stu-id="357c6-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="357c6-188">Pon en tu HoloLens y mira tu vista para ver los nuevos hologramas.</span><span class="sxs-lookup"><span data-stu-id="357c6-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="357c6-189">Capítulo 2: mira hacia abajo</span><span class="sxs-lookup"><span data-stu-id="357c6-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="357c6-190">En este capítulo, vamos a presentar la primera de las tres formas de interactuar con los hologramas: [miramos](gaze-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="357c6-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-191">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-191">Objectives</span></span>

* <span data-ttu-id="357c6-192">Visualice la mirada con un cursor de un mundo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="357c6-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-193">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-193">Instructions</span></span>

* <span data-ttu-id="357c6-194">Vuelva al proyecto de Unity y cierre la ventana de configuración de la compilación si aún está abierta.</span><span class="sxs-lookup"><span data-stu-id="357c6-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="357c6-195">Seleccione la carpeta **hologramas** en el **panel Proyecto**.</span><span class="sxs-lookup"><span data-stu-id="357c6-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="357c6-196">Arrastre el objeto **cursor** al **Panel jerarquía** en el nivel raíz.</span><span class="sxs-lookup"><span data-stu-id="357c6-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="357c6-197">Haga doble clic en el objeto **cursor** para examinarlo más detenidamente.</span><span class="sxs-lookup"><span data-stu-id="357c6-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="357c6-198">Haga clic con el botón secundario en la carpeta **scripts** en el panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="357c6-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="357c6-199">Haga clic en el submenú **crear** .</span><span class="sxs-lookup"><span data-stu-id="357c6-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="357c6-200">Seleccione  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="357c6-200">Select **C# Script**.</span></span>
* <span data-ttu-id="357c6-201">Asigne al script el nombre **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="357c6-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="357c6-202">Nota: el nombre distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="357c6-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="357c6-203">No es necesario agregar la extensión. cs.</span><span class="sxs-lookup"><span data-stu-id="357c6-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="357c6-204">Seleccione el objeto **cursor** en el **Panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="357c6-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="357c6-205">Arrastre y coloque el script **WorldCursor** en el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="357c6-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="357c6-206">Haga doble clic en el script **WorldCursor** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="357c6-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="357c6-207">Copie y pegue este código en **WorldCursor.CS** y **guarde todo**.</span><span class="sxs-lookup"><span data-stu-id="357c6-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="357c6-208">Vuelva a compilar la aplicación desde el **archivo > la configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="357c6-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="357c6-209">Vuelva a la solución de Visual Studio que se usó anteriormente para implementar en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="357c6-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="357c6-210">Seleccione "recargar todo" cuando se le solicite.</span><span class="sxs-lookup"><span data-stu-id="357c6-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="357c6-211">Haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="357c6-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="357c6-212">Ahora mire la escena y observe cómo interactúa el cursor con la forma de los objetos.</span><span class="sxs-lookup"><span data-stu-id="357c6-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="357c6-213">Capítulo 3: gestos</span><span class="sxs-lookup"><span data-stu-id="357c6-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="357c6-214">En este capítulo, se agregará compatibilidad con [gestos](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="357c6-214">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="357c6-215">Cuando el usuario selecciona una esfera de papel, haremos que la esfera se active al activar la gravedad mediante el motor físico de Unity.</span><span class="sxs-lookup"><span data-stu-id="357c6-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-216">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-216">Objectives</span></span>

* <span data-ttu-id="357c6-217">Controle los hologramas con el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="357c6-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-218">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-218">Instructions</span></span>

<span data-ttu-id="357c6-219">Comenzaremos por crear un script y luego puede detectar el gesto de selección.</span><span class="sxs-lookup"><span data-stu-id="357c6-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="357c6-220">En la carpeta **scripts** , cree un script denominado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="357c6-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="357c6-221">Arrastre el script **GazeGestureManager** hasta el objeto **OrigamiCollection** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="357c6-222">Abra el script **GazeGestureManager** en Visual Studio y agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="357c6-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="357c6-223">Cree otro script en la carpeta scripts, esta vez con el nombre **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="357c6-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="357c6-224">Expanda el objeto **OrigamiCollection** en la vista de jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="357c6-225">Arrastre el script **SphereCommands** al objeto **Sphere1** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="357c6-226">Arrastre el script **SphereCommands** al objeto **Sphere2** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="357c6-227">Abra el script en Visual Studio para editarlo y reemplace el código predeterminado por este:</span><span class="sxs-lookup"><span data-stu-id="357c6-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="357c6-228">Exporte, compile e implemente la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="357c6-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="357c6-229">Fíjese en uno de los esferas.</span><span class="sxs-lookup"><span data-stu-id="357c6-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="357c6-230">Realice el gesto seleccionar y observe la esfera que se coloca en la superficie siguiente.</span><span class="sxs-lookup"><span data-stu-id="357c6-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="357c6-231">Capítulo 4: voz</span><span class="sxs-lookup"><span data-stu-id="357c6-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="357c6-232">En este capítulo, se agregará compatibilidad con dos [comandos de voz](voice-input.md): "RESET World" para devolver los esferas quitados a su ubicación original y "Drop Sphere" para que la esfera quede.</span><span class="sxs-lookup"><span data-stu-id="357c6-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-233">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-233">Objectives</span></span>

* <span data-ttu-id="357c6-234">Agregue comandos de voz que siempre escuchan en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="357c6-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="357c6-235">Cree un holograma que reaccione a un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="357c6-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-236">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-236">Instructions</span></span>

* <span data-ttu-id="357c6-237">En la carpeta **scripts** , cree un script denominado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="357c6-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="357c6-238">Arrastre el script **SpeechManager** hasta el objeto **OrigamiCollection** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="357c6-239">Abra el script **SpeechManager** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="357c6-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="357c6-240">Copie y pegue este código en **SpeechManager.CS** y **guarde todo**:</span><span class="sxs-lookup"><span data-stu-id="357c6-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="357c6-241">Abra el script **SphereCommands** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="357c6-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="357c6-242">Actualice el script para que se lea de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="357c6-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="357c6-243">Exporte, compile e implemente la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="357c6-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="357c6-244">Fíjese en uno de los esferas y en "**colocar esfera**".</span><span class="sxs-lookup"><span data-stu-id="357c6-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="357c6-245">Por ejemplo, "**restablecer mundo**" para volver a colocarlos en sus posiciones iniciales.</span><span class="sxs-lookup"><span data-stu-id="357c6-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="357c6-246">Capítulo 5: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="357c6-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="357c6-247">En este capítulo, agregaremos música a la aplicación y, a continuación, desencadenaremos efectos sonoros en determinadas acciones.</span><span class="sxs-lookup"><span data-stu-id="357c6-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="357c6-248">Usaremos el [sonido espacial](spatial-sound.md) para proporcionar a los sonidos una ubicación específica en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="357c6-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-249">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-249">Objectives</span></span>

* <span data-ttu-id="357c6-250">Escuche los hologramas de su mundo.</span><span class="sxs-lookup"><span data-stu-id="357c6-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-251">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-251">Instructions</span></span>

* <span data-ttu-id="357c6-252">En Unity, seleccione en el menú superior **editar > configuración del proyecto > audio**</span><span class="sxs-lookup"><span data-stu-id="357c6-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="357c6-253">En el panel Inspector del lado derecho, busque la configuración del **complemento Spatializer** y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="357c6-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="357c6-254">En la carpeta **hologramas** del panel Proyecto, arrastre el objeto **ambiente** hasta el objeto **OrigamiCollection** en el panel jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="357c6-255">Seleccione **OrigamiCollection** y busque el componente **origen de audio** en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="357c6-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="357c6-256">Cambie estas propiedades:</span><span class="sxs-lookup"><span data-stu-id="357c6-256">Change these properties:</span></span>
  * <span data-ttu-id="357c6-257">Compruebe la propiedad **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="357c6-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="357c6-258">Active la casilla **reproducir en activo**.</span><span class="sxs-lookup"><span data-stu-id="357c6-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="357c6-259">Cambie la **mezcla espacial** a **3D** arrastrando el control deslizante hasta la derecha.</span><span class="sxs-lookup"><span data-stu-id="357c6-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="357c6-260">El valor debe cambiar de 0 a 1 cuando se mueve el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="357c6-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="357c6-261">Compruebe la propiedad **Loop** .</span><span class="sxs-lookup"><span data-stu-id="357c6-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="357c6-262">Expanda **configuración de sonido 3D**y escriba **0,1** para el **nivel de Doppler**.</span><span class="sxs-lookup"><span data-stu-id="357c6-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="357c6-263">Establezca **rolloff de volumen** en **rolloff logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="357c6-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="357c6-264">Establezca la **distancia máxima** en **20**.</span><span class="sxs-lookup"><span data-stu-id="357c6-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="357c6-265">En la carpeta **scripts** , cree un script denominado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="357c6-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="357c6-266">Arrastre y coloque **SphereSounds** en los objetos **Sphere1** y **Sphere2** de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="357c6-267">Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guarde todo**.</span><span class="sxs-lookup"><span data-stu-id="357c6-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="357c6-268">Guarde el script y vuelva a Unity.</span><span class="sxs-lookup"><span data-stu-id="357c6-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="357c6-269">Exporte, compile e implemente la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="357c6-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="357c6-270">Desplácese más cerca y más lejos de la fase y vuelva al lado para oír el cambio de los sonidos.</span><span class="sxs-lookup"><span data-stu-id="357c6-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="357c6-271">Capítulo 6: asignación espacial</span><span class="sxs-lookup"><span data-stu-id="357c6-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="357c6-272">Ahora vamos a usar la [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real del mundo real.</span><span class="sxs-lookup"><span data-stu-id="357c6-272">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-273">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-273">Objectives</span></span>

* <span data-ttu-id="357c6-274">Traiga su mundo real al mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="357c6-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="357c6-275">Coloque los hologramas donde más le importan.</span><span class="sxs-lookup"><span data-stu-id="357c6-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-276">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-276">Instructions</span></span>

* <span data-ttu-id="357c6-277">En Unity, haga clic en la carpeta **hologramas** en el panel Proyecto.</span><span class="sxs-lookup"><span data-stu-id="357c6-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="357c6-278">Arrastre el recurso de **asignación espacial** a la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="357c6-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="357c6-279">Haga clic en el objeto de **asignación espacial** en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="357c6-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="357c6-280">En el **panel Inspector**, cambie las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="357c6-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="357c6-281">Active la casilla **dibujar mallas visuales** .</span><span class="sxs-lookup"><span data-stu-id="357c6-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="357c6-282">Busque **material de dibujo** y haga clic en el círculo de la derecha.</span><span class="sxs-lookup"><span data-stu-id="357c6-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="357c6-283">Escriba "**Wireframe**" en el campo de búsqueda de la parte superior.</span><span class="sxs-lookup"><span data-stu-id="357c6-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="357c6-284">Haga clic en el resultado y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="357c6-284">Click on the result and then close the window.</span></span> <span data-ttu-id="357c6-285">Al hacerlo, el valor de Draw material debe establecerse en Wireframe.</span><span class="sxs-lookup"><span data-stu-id="357c6-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="357c6-286">Exporte, compile e implemente la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="357c6-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="357c6-287">Cuando se ejecuta la aplicación, una malla de alambres se superpone a su mundo real.</span><span class="sxs-lookup"><span data-stu-id="357c6-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="357c6-288">Vea cómo una esfera gradual se quedará fuera de la fase y en el suelo.</span><span class="sxs-lookup"><span data-stu-id="357c6-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="357c6-289">Ahora le mostraremos cómo trasladar el OrigamiCollection a una nueva ubicación:</span><span class="sxs-lookup"><span data-stu-id="357c6-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="357c6-290">En la carpeta **scripts** , cree un script denominado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="357c6-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="357c6-291">En la **jerarquía**, expanda **OrigamiCollection** y seleccione el objeto **Stage** .</span><span class="sxs-lookup"><span data-stu-id="357c6-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="357c6-292">Arrastre el script **TapToPlaceParent** hasta el objeto Stage.</span><span class="sxs-lookup"><span data-stu-id="357c6-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="357c6-293">Abra el script **TapToPlaceParent** en Visual Studio y actualícelo para que sea el siguiente:</span><span class="sxs-lookup"><span data-stu-id="357c6-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="357c6-294">Exportar, compilar e implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="357c6-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="357c6-295">Ahora debería poder colocar el juego en una ubicación específica Gazing en él, con el gesto seleccionar y, a continuación, pasar a una nueva ubicación y volver a usar el gesto seleccionar.</span><span class="sxs-lookup"><span data-stu-id="357c6-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="357c6-296">Capítulo 7: diversión de holográfica</span><span class="sxs-lookup"><span data-stu-id="357c6-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="357c6-297">Objetivos</span><span class="sxs-lookup"><span data-stu-id="357c6-297">Objectives</span></span>

* <span data-ttu-id="357c6-298">Revela la entrada a un mundo holográfica.</span><span class="sxs-lookup"><span data-stu-id="357c6-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="357c6-299">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="357c6-299">Instructions</span></span>

<span data-ttu-id="357c6-300">Ahora le mostraremos cómo descubrir el mundo holográfica:</span><span class="sxs-lookup"><span data-stu-id="357c6-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="357c6-301">En la carpeta **hologramas** del panel Proyecto:</span><span class="sxs-lookup"><span data-stu-id="357c6-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="357c6-302">Arrastre el **submundo** a la jerarquía para que sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="357c6-303">En la carpeta **scripts** , cree un script denominado **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="357c6-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="357c6-304">En la **jerarquía**, expanda **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="357c6-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="357c6-305">Expanda el objeto **fase** y seleccione el objeto de **destino** (ventilador azul).</span><span class="sxs-lookup"><span data-stu-id="357c6-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="357c6-306">Arrastre el script **HitTarget** al objeto de **destino** .</span><span class="sxs-lookup"><span data-stu-id="357c6-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="357c6-307">Abra el script **HitTarget** en Visual Studio y actualícelo para que sea el siguiente:</span><span class="sxs-lookup"><span data-stu-id="357c6-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="357c6-308">En Unity, seleccione el objeto de **destino** .</span><span class="sxs-lookup"><span data-stu-id="357c6-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="357c6-309">Ahora hay dos propiedades públicas visibles en el componente de **destino de aciertos** y necesitan hacer referencia a los objetos de nuestra escena:</span><span class="sxs-lookup"><span data-stu-id="357c6-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="357c6-310">Arrastre el **subámbito** del panel **jerarquía** a la propiedad **subworld** del componente **destino** de la visita.</span><span class="sxs-lookup"><span data-stu-id="357c6-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="357c6-311">Arrastre **fase** desde el panel **jerarquía** hasta el **objeto para ocultar** la propiedad en el componente de destino de la **visita** .</span><span class="sxs-lookup"><span data-stu-id="357c6-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="357c6-312">Exportar, compilar e implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="357c6-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="357c6-313">Coloque la colección origami en el plano inferior y, a continuación, use el gesto seleccionar para hacer una colocación de esfera.</span><span class="sxs-lookup"><span data-stu-id="357c6-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="357c6-314">Cuando la esfera alcanza el destino (ventilador azul), se producirá una explosión.</span><span class="sxs-lookup"><span data-stu-id="357c6-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="357c6-315">La colección se ocultará y aparecerá un hueco para el mundo.</span><span class="sxs-lookup"><span data-stu-id="357c6-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="357c6-316">Fin</span><span class="sxs-lookup"><span data-stu-id="357c6-316">The end</span></span>

<span data-ttu-id="357c6-317">Y este es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="357c6-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="357c6-318">Aprendió:</span><span class="sxs-lookup"><span data-stu-id="357c6-318">You learned:</span></span>

* <span data-ttu-id="357c6-319">Cómo crear una aplicación holográfica en Unity.</span><span class="sxs-lookup"><span data-stu-id="357c6-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="357c6-320">Cómo hacer uso de fijamente, gestos, voz, sonido y asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="357c6-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="357c6-321">Cómo compilar e implementar una aplicación con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="357c6-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="357c6-322">Ya está listo para empezar a crear su propia experiencia holográfica.</span><span class="sxs-lookup"><span data-stu-id="357c6-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="357c6-323">Consulta también</span><span class="sxs-lookup"><span data-stu-id="357c6-323">See also</span></span>

* [<span data-ttu-id="357c6-324">MR Basics 101E: proyecto completo con Emulator</span><span class="sxs-lookup"><span data-stu-id="357c6-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="357c6-325">Gaze</span><span class="sxs-lookup"><span data-stu-id="357c6-325">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="357c6-326">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="357c6-326">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="357c6-327">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="357c6-327">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="357c6-328">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="357c6-328">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="357c6-329">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="357c6-329">Spatial mapping</span></span>](spatial-mapping.md)
