---
title: MR Sharing 240-varios dispositivos HoloLens
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre el uso compartido de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, uso compartido, redes, Academia, tutorial
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434567"
---
>[!NOTE]
><span data-ttu-id="3ed7f-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3ed7f-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3ed7f-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3ed7f-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3ed7f-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="3ed7f-109">MR Sharing 240: varios dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="3ed7f-109">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="3ed7f-110">Los hologramas reciben la presencia en nuestro mundo a medida que avanzamos en el espacio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="3ed7f-111">HoloLens mantiene los hologramas en su lugar mediante el uso de varios [sistemas de coordenadas](coordinate-systems.md) para realizar un seguimiento de la ubicación y la orientación de los objetos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-111">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="3ed7f-112">Cuando compartimos estos sistemas de coordenadas entre dispositivos, podemos crear una experiencia compartida que nos permita participar en un mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="3ed7f-113">En este tutorial, haremos lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3ed7f-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="3ed7f-114">Configurar una red para una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="3ed7f-115">Compartir hologramas en dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-116">Descubra otras personas en nuestro mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="3ed7f-117">Cree una experiencia interactiva compartida donde pueda dirigirse a otros reproductores e iniciar proyectiles en ellos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="3ed7f-118">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3ed7f-119">Recurso</span><span class="sxs-lookup"><span data-stu-id="3ed7f-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3ed7f-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3ed7f-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3ed7f-121"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="3ed7f-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="3ed7f-122">MR Sharing 240: varios dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="3ed7f-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="3ed7f-123">✔️</span><span class="sxs-lookup"><span data-stu-id="3ed7f-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3ed7f-124">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="3ed7f-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3ed7f-125">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-125">Prerequisites</span></span>

* <span data-ttu-id="3ed7f-126">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md) con acceso a Internet.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="3ed7f-127">Al menos dos dispositivos HoloLens [configurados para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-127">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="3ed7f-128">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="3ed7f-128">Project files</span></span>

* <span data-ttu-id="3ed7f-129">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="3ed7f-130">Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="3ed7f-131">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="3ed7f-132">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="3ed7f-133">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="3ed7f-134">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="3ed7f-135">Mantenga el nombre de la carpeta como **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="3ed7f-136">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="3ed7f-137">Capítulo 1: Hololens World</span><span class="sxs-lookup"><span data-stu-id="3ed7f-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="3ed7f-138">En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-139">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-139">Objectives</span></span>

* <span data-ttu-id="3ed7f-140">Configure Unity para desarrollar aplicaciones holográficas.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="3ed7f-141">Vea su holograma.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-142">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-142">Instructions</span></span>

* <span data-ttu-id="3ed7f-143">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-143">Start Unity.</span></span>
* <span data-ttu-id="3ed7f-144">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-144">Select **Open**.</span></span>
* <span data-ttu-id="3ed7f-145">Escriba Location como la carpeta **SharedHolograms** que ha desarchivado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="3ed7f-146">Seleccione **nombre del proyecto** y haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="3ed7f-147">En la **jerarquía**, haga clic con el botón secundario en la **cámara principal** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="3ed7f-148">En la carpeta **HoloToolkit-Sharing-240/Prefabs/cámara** , busque la **cámara principal** recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="3ed7f-149">Arrastre y coloque la **cámara principal** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="3ed7f-150">En la **jerarquía**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="3ed7f-151">Haga clic con el botón derecho en el nuevo **GameObject** y seleccione **cambiar nombre**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="3ed7f-152">Cambie el nombre de GameObject a **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="3ed7f-153">Seleccione el objeto **HologramCollection** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="3ed7f-154">En el **Inspector** , establezca la posición de la **transformación** en: **X: 0, y:-0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="3ed7f-155">En la carpeta **hologramas** del **panel Proyecto**, busque el recurso **EnergyHub** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="3ed7f-156">Arrastre y coloque el objeto **EnergyHub** desde el **panel Proyecto** hasta la **jerarquía** como **elemento secundario de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="3ed7f-157">Seleccione el **archivo > guardar la escena como...**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="3ed7f-158">Asigne a la escena el nombre **SharedHolograms** y haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="3ed7f-159">Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="3ed7f-160">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="3ed7f-161">**Exportar el proyecto de Unity a Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="3ed7f-162">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="3ed7f-163">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="3ed7f-164">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="3ed7f-165">Establezca **SDK** en **universal 10**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="3ed7f-166">Establezca **el dispositivo de destino** en **HoloLens** y el tipo de **compilación de UWP** en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="3ed7f-167">Compruebe **los C# proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="3ed7f-168">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-168">Click **Build**.</span></span>
* <span data-ttu-id="3ed7f-169">En la ventana del explorador de archivos que aparece, cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="3ed7f-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="3ed7f-170">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="3ed7f-171">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="3ed7f-172">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="3ed7f-173">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-173">Open the **App** folder.</span></span>
* <span data-ttu-id="3ed7f-174">Abra **SharedHolograms. sln** para iniciar Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-175">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="3ed7f-176">Haga clic en la flecha desplegable situada junto a equipo local y seleccione **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="3ed7f-177">Establezca la **Dirección** en el nombre o la dirección IP de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="3ed7f-178">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas** o pregunte a Cortana **, ¿cuál es mi dirección IP? "** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="3ed7f-179">Deje el **modo de autenticación** establecido en **universal**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="3ed7f-180">Haga clic en **seleccionar**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-180">Click **Select**</span></span>
* <span data-ttu-id="3ed7f-181">Haga clic en **Depurar > iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="3ed7f-182">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="3ed7f-183">Pon en tu HoloLens y busca el holograma de EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="3ed7f-184">Capítulo 2: interacción</span><span class="sxs-lookup"><span data-stu-id="3ed7f-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="3ed7f-185">En este capítulo, Interactuaremos con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="3ed7f-186">En primer lugar, vamos a agregar un cursor para visualizar nuestra [mirada](gaze-and-commit.md).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-186">First, we'll add a cursor to visualize our [Gaze](gaze-and-commit.md).</span></span> <span data-ttu-id="3ed7f-187">Después, agregaremos [gestos](gaze-and-commit.md#composite-gestures) y usaremos nuestra mano para colocar los hologramas en el espacio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-187">Then, we'll add [Gestures](gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-188">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-188">Objectives</span></span>

* <span data-ttu-id="3ed7f-189">Use la entrada de fijamente para controlar un cursor.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="3ed7f-190">Use la entrada de gestos para interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-191">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-191">Instructions</span></span>

<span data-ttu-id="3ed7f-192">**Gaze**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-192">**Gaze**</span></span>

* <span data-ttu-id="3ed7f-193">En el **Panel jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3ed7f-194">En el **panel Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3ed7f-195">En el menú, escriba en el cuadro de búsqueda, **mira el administrador**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="3ed7f-196">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-196">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-197">En la carpeta **HoloToolkit-Sharing-240\Prefabs\Input** , busque el recurso **cursor** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="3ed7f-198">Arrastre y coloque el activo del **cursor** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="3ed7f-199">**Hacia**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-199">**Gesture**</span></span>

* <span data-ttu-id="3ed7f-200">En el **Panel jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3ed7f-201">Haga clic en **Agregar componente** y escriba **Administrador de gestos** en el campo de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="3ed7f-202">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-202">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-203">En el **Panel jerarquía**, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="3ed7f-204">Seleccione el objeto **EnergyHub** secundario.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="3ed7f-205">En el **panel Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3ed7f-206">En el menú, escriba en la ubicación del **holograma**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="3ed7f-207">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-207">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-208">Guarde la escena seleccionando **archivo > guardar escena**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="3ed7f-209">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3ed7f-210">Cree e implemente en HoloLens con las instrucciones del capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="3ed7f-211">Una vez que la aplicación se inicie en HoloLens, mueva el dedo y observe cómo el EnergyHub sigue su mirada.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="3ed7f-212">Observe cómo aparece el cursor cuando mira el holograma y cambia a una luz puntual cuando no se Gazing en un holograma.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="3ed7f-213">Realice una derivación aérea para colocar el holograma.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="3ed7f-214">En este momento, en nuestro proyecto, solo puede colocar el holograma una vez (vuelva a implementarlo para intentarlo de nuevo).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="3ed7f-215">Capítulo 3: coordenadas compartidas</span><span class="sxs-lookup"><span data-stu-id="3ed7f-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="3ed7f-216">Es divertido ver los hologramas e interactuar con ellos, pero vamos a continuar.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="3ed7f-217">Configuraremos nuestra primera experiencia compartida: un holograma todo el mundo puede ver juntos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-218">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-218">Objectives</span></span>

* <span data-ttu-id="3ed7f-219">Configurar una red para una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="3ed7f-220">Establezca un punto de referencia común.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-220">Establish a common reference point.</span></span>
* <span data-ttu-id="3ed7f-221">Compartir sistemas de coordenadas entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="3ed7f-222">Todos ven el mismo holograma.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="3ed7f-223">Las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer** se deben declarar para que una aplicación se conecte al servidor de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="3ed7f-224">Esto ya se hace en los hologramas 240, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="3ed7f-225">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="3ed7f-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="3ed7f-226">Haga clic en la pestaña "tienda Windows"</span><span class="sxs-lookup"><span data-stu-id="3ed7f-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="3ed7f-227">En la sección "configuración de publicación > funcionalidades", Compruebe la funcionalidad de **InternetClientServer** y la capacidad de **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-228">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-228">Instructions</span></span>

* <span data-ttu-id="3ed7f-229">En el **panel Proyecto** , vaya a la carpeta **HoloToolkit-Sharing-240\Prefabs\Sharing** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="3ed7f-230">Arrastre y coloque el recurso prefabricado de **uso compartido** en el **Panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="3ed7f-231">A continuación, es necesario iniciar el servicio de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="3ed7f-232">Solo **un equipo** en la experiencia compartida debe realizar este paso.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="3ed7f-233">En Unity: en el menú de la parte superior, seleccione el **menú HoloToolkit-Sharing-240**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="3ed7f-234">Seleccione el elemento **servicio de uso compartido de inicio** en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="3ed7f-235">Active la opción **red privada** y haga clic en **permitir el acceso** cuando aparezca el mensaje del firewall.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="3ed7f-236">Anote la dirección IPv4 que se muestra en la ventana de la consola del servicio de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="3ed7f-237">Se trata de la misma dirección IP que el equipo en el que se ejecuta el servicio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="3ed7f-238">Siga el resto de las instrucciones en **todos los equipos** que se unirán a la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="3ed7f-239">En la **jerarquía**, seleccione el objeto de **uso compartido** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="3ed7f-240">En el **Inspector**, en el componente de la **fase de uso compartido** , cambie la **dirección del servidor** de "localhost" a la dirección IPv4 del equipo que ejecuta SharingService. exe.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="3ed7f-241">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3ed7f-242">En el **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="3ed7f-243">En el cuadro de búsqueda, escriba **Import Export Anchor Manager**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="3ed7f-244">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-244">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-245">En el **panel Proyecto** , vaya a la carpeta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3ed7f-246">Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-247">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-247">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="3ed7f-248">De nuevo en Unity, seleccione el **HologramCollection** en el **Panel de jerarquías**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="3ed7f-249">En el **panel Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="3ed7f-250">En el menú, escriba en el cuadro de búsqueda **App State Manager**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="3ed7f-251">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-251">Select the search result.</span></span>

<span data-ttu-id="3ed7f-252">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3ed7f-253">Compile el proyecto para los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-254">Designe un HoloLens en el que implementar primero.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="3ed7f-255">Tendrá que esperar a que el delimitador se cargue en el servicio antes de poder colocar el EnergyHub (esto puede tardar ~ 30-60 segundos).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="3ed7f-256">Hasta que se realice la carga, se omitirán los gestos de TAP.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="3ed7f-257">Una vez colocada la EnergyHub, su ubicación se cargará en el servicio y, a continuación, podrá implementar en todos los demás dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-258">Cuando un nuevo HoloLens se une por primera vez a la sesión, es posible que la ubicación de EnergyHub no sea correcta en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="3ed7f-259">Sin embargo, en cuanto se hayan descargado las ubicaciones de delimitador y EnergyHub desde el servicio, el EnergyHub debe saltar a la nueva ubicación compartida.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="3ed7f-260">Si esto no ocurre en menos de 30-60 segundos, desplácese a la ubicación donde se encontraba HoloLens original al establecer el delimitador para recopilar más pistas de entorno.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="3ed7f-261">Si la ubicación sigue sin bloquearse, vuelva a realizar la implementación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="3ed7f-262">Cuando todos los dispositivos estén listos y ejecuten la aplicación, busque EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="3ed7f-263">¿Puede estar de acuerdo con la ubicación del holograma y la dirección en la que el texto está enfrente?</span><span class="sxs-lookup"><span data-stu-id="3ed7f-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="3ed7f-264">Capítulo 4: detección</span><span class="sxs-lookup"><span data-stu-id="3ed7f-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="3ed7f-265">Ahora todo el mundo puede ver el mismo holograma.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="3ed7f-266">Ahora, vamos a ver a todos los demás conectados a nuestro mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="3ed7f-267">En este capítulo, se tomará la ubicación principal y la rotación de todos los demás dispositivos HoloLens en la misma sesión de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-268">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-268">Objectives</span></span>

* <span data-ttu-id="3ed7f-269">Descubra entre sí en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="3ed7f-270">Elegir y compartir un avatar de reproductor.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="3ed7f-271">Adjunte el avatar del jugador junto a los cabezales de todos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-272">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-272">Instructions</span></span>

* <span data-ttu-id="3ed7f-273">En el **panel Proyecto** , vaya a la carpeta **hologramas** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3ed7f-274">Arrastre y coloque **PlayerAvatarStore** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="3ed7f-275">En el **panel Proyecto** , vaya a la carpeta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3ed7f-276">Haga doble clic en el script **AvatarSelector** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-277">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-277">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="3ed7f-278">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3ed7f-279">En el **Inspector** , haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3ed7f-280">En el cuadro de búsqueda, escriba **Administrador del reproductor local**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="3ed7f-281">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-281">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-282">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3ed7f-283">En el **Inspector** , haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3ed7f-284">En el cuadro de búsqueda, escriba **Administrador de reproductores remotos**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="3ed7f-285">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-285">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-286">Abra el script **HologramPlacement** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-287">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-287">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="3ed7f-288">Abra el script **AppStateManager** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-289">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-289">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="3ed7f-290">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="3ed7f-291">Compile e implemente el proyecto en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-292">Cuando escuche un sonido de ping, busque el menú de selección de Avatar y seleccione un avatar con el gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="3ed7f-293">Si no está mirando ningún holograma, la luz puntual alrededor del cursor girará un color diferente cuando HoloLens se comunique con el servicio: inicializando (púrpura oscuro), descargando el delimitador (verde), importando/exportando datos de ubicación (amarillo), cargar el delimitador (azul).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="3ed7f-294">Si la luz de punto alrededor del cursor es el color predeterminado (púrpura claro), está listo para interactuar con otros jugadores en la sesión.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="3ed7f-295">Mire otras personas conectadas a su espacio: en este caso, habrá un robot holográfica que se flota por encima de su hombro y imitando sus movimientos de cabeza.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="3ed7f-296">Capítulo 5: selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="3ed7f-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="3ed7f-297">En este capítulo, haremos que el anclaje sea capaz de colocarse en superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="3ed7f-298">Usaremos coordenadas compartidas para colocar ese delimitador en el punto intermedio entre todos los usuarios conectados a la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-299">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-299">Objectives</span></span>

* <span data-ttu-id="3ed7f-300">Coloque los hologramas en la malla de asignación espacial basada en la posición principal de los jugadores.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-301">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-301">Instructions</span></span>

* <span data-ttu-id="3ed7f-302">En el **panel Proyecto** , vaya a la carpeta **hologramas** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3ed7f-303">Arrastre y coloque el recurso prefabricado de **CustomSpatialMapping** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="3ed7f-304">En el **panel Proyecto** , vaya a la carpeta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3ed7f-305">Haga doble clic en el script **AppStateManager** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-306">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-306">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="3ed7f-307">En el **panel Proyecto** , vaya a la carpeta **scripts** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="3ed7f-308">Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="3ed7f-309">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-309">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="3ed7f-310">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3ed7f-311">Compile e implemente el proyecto en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-312">Cuando la aplicación esté lista, destaque un círculo y observe cómo aparece EnergyHub en el centro de todos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="3ed7f-313">Puntee para colocar el EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="3ed7f-314">Pruebe el comando de voz "restablecer destino" para elegir la copia de seguridad de EnergyHub y trabajar conjuntamente como un grupo para trasladar el holograma a una nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="3ed7f-315">Capítulo 6: física del mundo real</span><span class="sxs-lookup"><span data-stu-id="3ed7f-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="3ed7f-316">En este capítulo, vamos a agregar hologramas que rebotan las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="3ed7f-317">Vea el espacio lleno con proyectos que usted y sus amigos han lanzado.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-318">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-318">Objectives</span></span>

* <span data-ttu-id="3ed7f-319">Inicie los proyectiles que rebotan las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="3ed7f-320">Comparta los proyectiles para que otros jugadores puedan verlos.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-321">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-321">Instructions</span></span>

* <span data-ttu-id="3ed7f-322">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="3ed7f-323">En el **Inspector** , haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="3ed7f-324">En el cuadro de búsqueda, escriba **selector de proyectil**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="3ed7f-325">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-325">Select the search result.</span></span>

<span data-ttu-id="3ed7f-326">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3ed7f-327">Cree e implemente en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-328">Cuando la aplicación se ejecuta en todos los dispositivos, realice una derivación aérea para lanzar el proyectil en las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="3ed7f-329">Vea lo que sucede cuando el proyectil entra en conflicto con el avatar de otro jugador.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="3ed7f-330">Capítulo 7: final general</span><span class="sxs-lookup"><span data-stu-id="3ed7f-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="3ed7f-331">En este capítulo, se descubrirá un portal que solo se puede detectar con colaboración.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="3ed7f-332">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3ed7f-332">Objectives</span></span>

* <span data-ttu-id="3ed7f-333">Trabaje de forma conjunta para iniciar suficientes proyectiles en el anclaje para descubrir un portal secreto.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="3ed7f-334">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="3ed7f-334">Instructions</span></span>

* <span data-ttu-id="3ed7f-335">En el **panel Proyecto** , vaya a la carpeta **hologramas** .</span><span class="sxs-lookup"><span data-stu-id="3ed7f-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="3ed7f-336">Arrastre y coloque el activo de **submundo** como **elemento secundario de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="3ed7f-337">Con **HologramCollection** seleccionado, haga clic en el botón **Agregar componente** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="3ed7f-338">En el menú, escriba en el cuadro de búsqueda **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="3ed7f-339">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-339">Select the search result.</span></span>
* <span data-ttu-id="3ed7f-340">Con **HologramCollection** seleccionado, en la **jerarquía** , arrastre el objeto **EnergyHub** hasta el campo de **destino** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="3ed7f-341">Con **HologramCollection** seleccionado, en la **jerarquía** , arrastre el objeto de **submundo** al campo de **submundo** del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="3ed7f-342">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="3ed7f-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="3ed7f-343">Cree e implemente en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="3ed7f-344">Cuando se haya iniciado la aplicación, colabore con el fin de lanzar proyectiles en el EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="3ed7f-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="3ed7f-345">Cuando aparezca el submundo, inicie los proyectiles en el mundo de los robots (golpee un robot tres veces para obtener una diversión adicional).</span><span class="sxs-lookup"><span data-stu-id="3ed7f-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
