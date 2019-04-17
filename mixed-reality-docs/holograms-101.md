---
title: Conceptos básicos de MR 101 - proyecto completo con el dispositivo
description: Siga este tutorial de programación con Unity, Visual Studio y HoloLens para obtener información sobre los conceptos básicos de Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: la realidad, Windows Mixed Reality, HoloLens, mixta holograma, academy, tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599358"
---
>[!NOTE]
><span data-ttu-id="d9d2f-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d9d2f-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d9d2f-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d9d2f-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d9d2f-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d9d2f-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="d9d2f-110">Conceptos básicos de MR 101: Proyecto completo con el dispositivo</span><span class="sxs-lookup"><span data-stu-id="d9d2f-110">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="d9d2f-111">Este tutorial le guiará a través de un proyecto completo, compilado en Unity, que muestra las características de Windows Mixed Reality principales en incluidos HoloLens [que mirar](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="d9d2f-112">El tutorial tardará aproximadamente una hora en completarse.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="d9d2f-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d9d2f-114">Curso</span><span class="sxs-lookup"><span data-stu-id="d9d2f-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d9d2f-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d9d2f-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d9d2f-116"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="d9d2f-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d9d2f-117">Conceptos básicos de MR 101: Proyecto completo con el dispositivo</span><span class="sxs-lookup"><span data-stu-id="d9d2f-117">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="d9d2f-118">✔️</span><span class="sxs-lookup"><span data-stu-id="d9d2f-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d9d2f-119">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="d9d2f-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d9d2f-120">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-120">Prerequisites</span></span>

* <span data-ttu-id="d9d2f-121">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="d9d2f-122">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-122">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="d9d2f-123">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="d9d2f-123">Project files</span></span>

* <span data-ttu-id="d9d2f-124">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-124">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="d9d2f-125"> Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-125"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="d9d2f-126">Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-126">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="d9d2f-127">Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-127">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="d9d2f-128">Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-128">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="d9d2f-129">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-129">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="d9d2f-130">Mantenga el nombre de carpeta **Origami**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-130">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="d9d2f-131">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-131">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="d9d2f-132">Capítulo 1: "Holo" world</span><span class="sxs-lookup"><span data-stu-id="d9d2f-132">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="d9d2f-133">En este capítulo, crearemos nuestro primer proyecto de Unity y paso a través de la compilación de la instalación y proceso de implementación.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-133">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-134">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-134">Objectives</span></span>

* <span data-ttu-id="d9d2f-135">Configuración de Unity para desarrollo holográfica.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-135">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="d9d2f-136">Realice un holograma.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-136">Make a hologram.</span></span>
* <span data-ttu-id="d9d2f-137">Vea un holograma que haya realizado.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-137">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-138">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-138">Instructions</span></span>

* <span data-ttu-id="d9d2f-139">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-139">Start Unity.</span></span>
* <span data-ttu-id="d9d2f-140">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-140">Select **Open**.</span></span>
* <span data-ttu-id="d9d2f-141">Escriba la ubicación que el **Origami** carpeta que anteriormente no archivados.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-141">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="d9d2f-142">Seleccione **Origami** y haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-142">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="d9d2f-143">Puesto que la **Origami** proyecto no contiene una escena, guarde la escena vacía de forma predeterminada un nuevo archivo con: **Archivo** / **Guardar escena como**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-143">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="d9d2f-144">Nombre de la nueva escena **Origami** y presione la **guardar** botón.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-144">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="d9d2f-145">Programa de instalación de la cámara virtual principal</span><span class="sxs-lookup"><span data-stu-id="d9d2f-145">Setup the main virtual camera</span></span>

* <span data-ttu-id="d9d2f-146">En el **jerarquía Panel**, seleccione **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-146">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="d9d2f-147">En el **Inspector** establecer su posición de la transformación a **0,0,0**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-147">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="d9d2f-148">Buscar el **borrar las marcas** propiedad y cambie la lista desplegable de **Skybox** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-148">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="d9d2f-149">Haga clic en el **en segundo plano** campo para abrir un selector de colores.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-149">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="d9d2f-150">Establecer **R, G, B y A** a **0**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-150">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="d9d2f-151">Programa de instalación de la escena</span><span class="sxs-lookup"><span data-stu-id="d9d2f-151">Setup the scene</span></span>

* <span data-ttu-id="d9d2f-152">En el **jerarquía Panel**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-152">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="d9d2f-153">Haga clic en el nuevo **GameObject** y seleccione Cambiar nombre.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-153">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="d9d2f-154">Cambiar el nombre de la GameObject a **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-154">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="d9d2f-155">Desde el **hologramas** carpeta en el Panel de proyecto (expanda activos y seleccione hologramas o haga doble clic en la carpeta hologramas en el Panel de proyecto):</span><span class="sxs-lookup"><span data-stu-id="d9d2f-155">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="d9d2f-156">Arrastre **fase** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-156">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="d9d2f-157">Arrastre **Sphere1** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-157">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="d9d2f-158">Arrastre **Sphere2** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-158">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="d9d2f-159">Haga clic en el **luz direccional** objeto en el **jerarquía Panel** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-159">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="d9d2f-160">Desde el **hologramas** carpeta, arrastre **luces** en la raíz de la **jerarquía Panel**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-160">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="d9d2f-161">En el **jerarquía**, seleccione el **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-161">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="d9d2f-162">En el **Inspector**, establezca la posición de la transformación en **0, -0,5, 2.0**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-162">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="d9d2f-163">Presione el **reproducir** en Unity para obtener una vista previa de sus hologramas botón.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-163">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="d9d2f-164">Debería ver los objetos de Origami en la ventana Vista previa.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-164">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="d9d2f-165">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-165">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="d9d2f-166">Exporta el proyecto de Unity a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9d2f-166">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="d9d2f-167">En Seleccione Unity **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-167">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="d9d2f-168">Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-168">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="d9d2f-169">Establecer **SDK** a **10 Universal** y **tipo de compilación** a **D3D**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-169">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="d9d2f-170">Comprobar **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-170">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="d9d2f-171">Haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-171">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="d9d2f-172">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-172">Click **Build**.</span></span>
* <span data-ttu-id="d9d2f-173">En la ventana del explorador de archivos que aparece, cree un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="d9d2f-173">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="d9d2f-174">Solo haga clic en el **carpeta aplicación**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-174">Single click the **App Folder**.</span></span>
* <span data-ttu-id="d9d2f-175">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-175">Press **Select Folder**.</span></span>
* <span data-ttu-id="d9d2f-176">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-176">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="d9d2f-177">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-177">Open the **App** folder.</span></span>
* <span data-ttu-id="d9d2f-178">Abrir (hacer doble clic) **Origami.sln**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-178">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="d9d2f-179">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X86**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-179">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="d9d2f-180">Haga clic en la flecha situada junto al botón del dispositivo y seleccione **máquina remota** para implementar a través de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-180">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="d9d2f-181">Establecer el **dirección** en el nombre o dirección IP de su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-181">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="d9d2f-182">Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas** o solicitar a Cortana **"Hola Cortana, ¿cuál es mi dirección IP?"**</span><span class="sxs-lookup"><span data-stu-id="d9d2f-182">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="d9d2f-183">Si el HoloLens está conectado a través de USB, puede seleccionar en su lugar **dispositivo** para implementar a través de USB.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-183">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="d9d2f-184">Deje el **modo de autenticación** establecido en **Universal**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-184">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="d9d2f-185">Haga clic en **seleccionar**</span><span class="sxs-lookup"><span data-stu-id="d9d2f-185">Click **Select**</span></span>

* <span data-ttu-id="d9d2f-186">Haga clic en **Depurar > Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-186">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="d9d2f-187">Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-187">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).</span></span>

* <span data-ttu-id="d9d2f-188">El proyecto Origami ahora crear, implementar en su HoloLens y, a continuación, ejecute.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-188">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="d9d2f-189">Colocar en su HoloLens y mire para ver sus nueva hologramas.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-189">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="d9d2f-190">Capítulo 2: mirada</span><span class="sxs-lookup"><span data-stu-id="d9d2f-190">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="d9d2f-191">En este capítulo, vamos a introducir la primera de estas tres maneras de interactuar con sus hologramas-- [que mirar](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-191">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-192">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-192">Objectives</span></span>

* <span data-ttu-id="d9d2f-193">Visualice a su mirada mediante un cursor bloqueado por el mundo.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-193">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-194">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-194">Instructions</span></span>

* <span data-ttu-id="d9d2f-195">Vuelva a su proyecto de Unity y cerrar la ventana de configuración de compilación si aún está abierta.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-195">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="d9d2f-196">Seleccione el **hologramas** carpeta en el **panel proyecto**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-196">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="d9d2f-197">Arrastre el **Cursor** objeto en el **panel jerarquía** en el nivel raíz.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-197">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="d9d2f-198">Haga doble clic en el **Cursor** objeto vistazo más de cerca.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-198">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="d9d2f-199">Haga doble clic en el **Scripts** carpeta en el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-199">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="d9d2f-200">Haga clic en el **crear** submenú.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-200">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="d9d2f-201">Seleccione  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-201">Select **C# Script**.</span></span>
* <span data-ttu-id="d9d2f-202">Nombre de la secuencia de comandos **WorldCursor**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-202">Name the script **WorldCursor**.</span></span> <span data-ttu-id="d9d2f-203">Nota: El nombre distingue mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-203">Note: The name is case-sensitive.</span></span> <span data-ttu-id="d9d2f-204">No es necesario agregar la extensión. cs.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-204">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="d9d2f-205">Seleccione el **Cursor** objeto en el **panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-205">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="d9d2f-206">Arrastre y coloque el **WorldCursor** de script en el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-206">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="d9d2f-207">Haga doble clic en el **WorldCursor** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-207">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d9d2f-208">Copie y pegue este código en **WorldCursor.cs** y **guardar todo**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-208">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="d9d2f-209">Vuelva a compilar la aplicación de **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-209">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="d9d2f-210">Vuelva a la solución de Visual Studio que anteriormente se usa para implementar en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-210">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="d9d2f-211">Seleccione "Volver a cargar todo" cuando se le solicite.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-211">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="d9d2f-212">Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-212">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="d9d2f-213">Ahora mire la escena y observe cómo interactúa el cursor con la forma de objetos.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-213">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="d9d2f-214">Capítulo 3: gestos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-214">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="d9d2f-215">En este capítulo, se agregará compatibilidad para [gestos](gestures.md).</span><span class="sxs-lookup"><span data-stu-id="d9d2f-215">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="d9d2f-216">Cuando el usuario selecciona una esfera de papel, nos aseguraremos de hacer la esfera se dividen activando gravedad mediante el motor de leyes físicas de Unity.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-216">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-217">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-217">Objectives</span></span>

* <span data-ttu-id="d9d2f-218">Controlar las hologramas con el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-218">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-219">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-219">Instructions</span></span>

<span data-ttu-id="d9d2f-220">Se comenzará creando una secuencia de comandos, a continuación, puede detectar el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-220">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="d9d2f-221">En el **Scripts** carpeta, cree un script denominado **GazeGestureManager**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-221">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="d9d2f-222">Arrastre el **GazeGestureManager** de script en el **OrigamiCollection** objeto en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-222">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="d9d2f-223">Abra el **GazeGestureManager** de script en Visual Studio y agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-223">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="d9d2f-224">Cree otra secuencia de comandos en la carpeta de Scripts, esta vez denominada **SphereCommands**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-224">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="d9d2f-225">Expanda el **OrigamiCollection** objeto en la vista de jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-225">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="d9d2f-226">Arrastre el **SphereCommands** de script en el **Sphere1** objeto en el panel de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-226">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="d9d2f-227">Arrastre el **SphereCommands** de script en el **Sphere2** objeto en el panel de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-227">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="d9d2f-228">Abra el script en Visual Studio para editar y reemplace el código predeterminado con esto:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-228">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="d9d2f-229">Exportar, compilar e implementar la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-229">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d9d2f-230">Examine una de las esferas.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-230">Look at one of the spheres.</span></span>
* <span data-ttu-id="d9d2f-231">Realice el gesto de select y observe cómo la esfera de colocar en la superficie de debajo.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-231">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="d9d2f-232">Capítulo 4 - voz</span><span class="sxs-lookup"><span data-stu-id="d9d2f-232">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="d9d2f-233">En este capítulo, se agregará compatibilidad para dos [comandos de voz](voice-input.md): "Restablecer world" para devolver las esferas colocarlo en su ubicación original y "Quitar esfera" para realizar la esfera se encuentran.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-233">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-234">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-234">Objectives</span></span>

* <span data-ttu-id="d9d2f-235">Agregar comandos de voz que siempre escuchan en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-235">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="d9d2f-236">Cree un holograma que reacciona a un comando de voz.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-236">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-237">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-237">Instructions</span></span>

* <span data-ttu-id="d9d2f-238">En el **Scripts** carpeta, cree un script denominado **SpeechManager**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-238">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="d9d2f-239">Arrastre el **SpeechManager** de script en el **OrigamiCollection** objeto en la jerarquía</span><span class="sxs-lookup"><span data-stu-id="d9d2f-239">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="d9d2f-240">Abra el **SpeechManager** script en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-240">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="d9d2f-241">Copie y pegue este código en **SpeechManager.cs** y **guardar todo**:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-241">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="d9d2f-242">Abra el **SphereCommands** script en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-242">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="d9d2f-243">Actualice el script para que quede como sigue:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-243">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="d9d2f-244">Exportar, compilar e implementar la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-244">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d9d2f-245">Examine una de las esferas y diga "**Drop esfera**".</span><span class="sxs-lookup"><span data-stu-id="d9d2f-245">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="d9d2f-246">Por ejemplo "**restablecer World**" para llevarlas nuevamente a sus posiciones iniciales.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-246">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="d9d2f-247">Capítulo 5: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="d9d2f-247">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="d9d2f-248">En este capítulo, se deberá agregar música a la aplicación y, a continuación, desencadenar efectos de sonido en determinadas acciones.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-248">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="d9d2f-249">Vamos a usar [sonido espacial](spatial-sound.md) para proporcionar a los sonidos de una ubicación específica en un espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-249">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-250">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-250">Objectives</span></span>

* <span data-ttu-id="d9d2f-251">Escuche hologramas en el mundo.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-251">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-252">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-252">Instructions</span></span>

* <span data-ttu-id="d9d2f-253">En el menú superior, seleccione Unity **Editar > configuración del proyecto > Audio**</span><span class="sxs-lookup"><span data-stu-id="d9d2f-253">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="d9d2f-254">En el Panel de Inspector en el lado derecho, busque el **espacial complemento** configuración y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-254">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="d9d2f-255">Desde el **hologramas** carpeta en el panel proyecto, arrastre el **ambiente** objeto en el **OrigamiCollection** objeto en el Panel de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-255">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="d9d2f-256">Seleccione **OrigamiCollection** y busque el **origen Audio** componente en el panel del Inspector.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-256">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="d9d2f-257">Cambiar estas propiedades:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-257">Change these properties:</span></span>
  * <span data-ttu-id="d9d2f-258">Compruebe el **Spatialize** propiedad.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-258">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="d9d2f-259">Compruebe el **reproducir en activo**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-259">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="d9d2f-260">Cambio **Blend espacial** a **3D** arrastrando el control deslizante totalmente hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-260">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="d9d2f-261">El valor debe cambiar de 0 a 1 cuando se mueve el control deslizante.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-261">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="d9d2f-262">Compruebe el **bucle** propiedad.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-262">Check the **Loop** property.</span></span>
  * <span data-ttu-id="d9d2f-263">Expanda **configuración sonido 3D**y escriba **0,1** para **nivel Doppler**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-263">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="d9d2f-264">Establecer **volumen atenuación** a **atenuación logarítmica**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-264">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="d9d2f-265">Establecer **distancia máxima** a **20**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-265">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="d9d2f-266">En el **Scripts** carpeta, cree un script denominado **SphereSounds**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-266">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="d9d2f-267">Arrastre y coloque **SphereSounds** a la **Sphere1** y **Sphere2** objetos de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-267">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="d9d2f-268">Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guardar todo**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-268">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="d9d2f-269">Guarde el script y volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-269">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="d9d2f-270">Exportar, compilar e implementar la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-270">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d9d2f-271">Mover más cercano y más lejos de la fase y activar lado a lado para que escuche los sonidos cambiar.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-271">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="d9d2f-272">Asignación de capítulo 6: espacial</span><span class="sxs-lookup"><span data-stu-id="d9d2f-272">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="d9d2f-273">Ahora vamos a usar [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-273">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-274">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-274">Objectives</span></span>

* <span data-ttu-id="d9d2f-275">Ponga el mundo real en el mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-275">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="d9d2f-276">Coloque sus hologramas donde más le interesen.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-276">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-277">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-277">Instructions</span></span>

* <span data-ttu-id="d9d2f-278">En Unity, haga clic en el **hologramas** carpeta en el panel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-278">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="d9d2f-279">Arrastre el **asignación espacial** activo en la raíz de la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-279">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="d9d2f-280">Haga clic en el **asignación espacial** objeto en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-280">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="d9d2f-281">En el **panel Inspector**, cambie las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-281">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="d9d2f-282">Compruebe el **dibujar mallas Visual** cuadro.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-282">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="d9d2f-283">Busque **dibujar Material** y haga clic en el círculo de la derecha.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-283">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="d9d2f-284">Tipo de "**tramas de alambres**" en el campo de búsqueda en la parte superior.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-284">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="d9d2f-285">Haga clic en el resultado y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-285">Click on the result and then close the window.</span></span> <span data-ttu-id="d9d2f-286">Al hacerlo, debe obtener o establecer el valor de dibujar Material en tramas de alambres.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-286">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="d9d2f-287">Exportar, compilar e implementar la aplicación en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-287">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="d9d2f-288">Cuando se ejecuta la aplicación, una malla de tramas de alambres superpondrán el mundo real.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-288">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="d9d2f-289">Vea cómo una esfera gradual estarán fuera del escenario y en el suelo.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-289">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="d9d2f-290">Ahora vamos a mostrarle cómo mover la OrigamiCollection a una nueva ubicación:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-290">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="d9d2f-291">En el **Scripts** carpeta, cree un script denominado **TapToPlaceParent**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-291">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="d9d2f-292">En el **jerarquía**, expanda el **OrigamiCollection** y seleccione el **fase** objeto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-292">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="d9d2f-293">Arrastre el **TapToPlaceParent** script en el objeto de fase.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-293">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="d9d2f-294">Abra el **TapToPlaceParent** de script en Visual Studio y actualizarlo para que sea lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-294">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="d9d2f-295">Exportar, compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-295">Export, build and deploy the app.</span></span>
* <span data-ttu-id="d9d2f-296">Ahora ya podrá colocar el juego en una ubicación específica mediante gazing en él, con el gesto de Select y, a continuación, mover a una nueva ubicación y volver a usar el gesto de Select.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-296">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="d9d2f-297">Capítulo 7 - divertido holográfica</span><span class="sxs-lookup"><span data-stu-id="d9d2f-297">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="d9d2f-298">Objetivos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-298">Objectives</span></span>

* <span data-ttu-id="d9d2f-299">Mostrar la entrada a un Underword holográfica.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-299">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="d9d2f-300">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="d9d2f-300">Instructions</span></span>

<span data-ttu-id="d9d2f-301">Ahora vamos a mostrarle cómo descubrir el Underword holográfica:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-301">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="d9d2f-302">Desde el **hologramas** carpeta en el Panel de proyecto:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-302">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="d9d2f-303">Arrastre **Underword** en la jerarquía sea un elemento secundario de **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-303">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="d9d2f-304">En el **Scripts** carpeta, cree un script denominado **HitTarget**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-304">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="d9d2f-305">En el **jerarquía**, expanda el **OrigamiCollection**.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-305">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="d9d2f-306">Expanda el **fase** de objetos y seleccione el **destino** (ventilador azul) del objeto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-306">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="d9d2f-307">Arrastre el **HitTarget** de script en el **destino** objeto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-307">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="d9d2f-308">Abra el **HitTarget** de script en Visual Studio y actualizarlo para que sea lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-308">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="d9d2f-309">En Unity, seleccione el **destino** objeto.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-309">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="d9d2f-310">Dos propiedades públicas son ahora visibles en el **aciertos destino** componente y la necesidad de los objetos de referencia de nuestra escena:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-310">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="d9d2f-311">Arrastre **Underword** desde el **jerarquía** panel a la **Underword** propiedad en el **aciertos destino** componente.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-311">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="d9d2f-312">Arrastre **fase** desde el **jerarquía** panel a la **objeto se va a ocultar** propiedad en el **aciertos destino** componente.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-312">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="d9d2f-313">Exportar, compile e implemente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-313">Export, build and deploy the app.</span></span>
* <span data-ttu-id="d9d2f-314">Coloque la colección de Origami en el suelo y, a continuación, usar el gesto de Select para realizar una esfera drop.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-314">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="d9d2f-315">Cuando la esfera alcanza el destino (ventilador azul), se producirá una explosión.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-315">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="d9d2f-316">La colección se ocultarán y aparecerá un "agujero" para el Underword.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-316">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="d9d2f-317">Fin</span><span class="sxs-lookup"><span data-stu-id="d9d2f-317">The end</span></span>

<span data-ttu-id="d9d2f-318">Y es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-318">And that's the end of this tutorial!</span></span>

<span data-ttu-id="d9d2f-319">Ha aprendido conceptos:</span><span class="sxs-lookup"><span data-stu-id="d9d2f-319">You learned:</span></span>

* <span data-ttu-id="d9d2f-320">Cómo crear una aplicación holográfica en Unity.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-320">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="d9d2f-321">Cómo hacer uso de mirada, gestos, voz, sonido y asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-321">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="d9d2f-322">Cómo compilar e implementar una aplicación mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-322">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="d9d2f-323">Ahora está listo para comenzar a crear su propia experiencia holográfica.</span><span class="sxs-lookup"><span data-stu-id="d9d2f-323">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d2f-324">Vea también</span><span class="sxs-lookup"><span data-stu-id="d9d2f-324">See also</span></span>

* [<span data-ttu-id="d9d2f-325">Conceptos básicos de MR 101E: Proyecto completo con el emulador</span><span class="sxs-lookup"><span data-stu-id="d9d2f-325">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="d9d2f-326">Gaze</span><span class="sxs-lookup"><span data-stu-id="d9d2f-326">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="d9d2f-327">Gestos</span><span class="sxs-lookup"><span data-stu-id="d9d2f-327">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="d9d2f-328">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="d9d2f-328">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="d9d2f-329">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="d9d2f-329">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="d9d2f-330">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="d9d2f-330">Spatial mapping</span></span>](spatial-mapping.md)
