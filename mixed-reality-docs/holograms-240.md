---
title: MR Sharing 240-varios dispositivos HoloLens
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre el uso compartido de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, uso compartido, redes, Academia, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522336"
---
>[!NOTE]
><span data-ttu-id="c3c22-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c3c22-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c3c22-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3c22-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c3c22-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="c3c22-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c3c22-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3c22-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c3c22-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="c3c22-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="c3c22-110">Uso compartido de MR 240: Varios dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="c3c22-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="c3c22-111">Los hologramas reciben la presencia en nuestro mundo a medida que avanzamos en el espacio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="c3c22-112">HoloLens mantiene los hologramas en su lugar mediante el uso de varios [sistemas de coordenadas](coordinate-systems.md) para realizar un seguimiento de la ubicación y la orientación de los objetos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="c3c22-113">Cuando compartimos estos sistemas de coordenadas entre dispositivos, podemos crear una experiencia compartida que nos permita participar en un mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="c3c22-114">En este tutorial, haremos lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c3c22-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="c3c22-115">Configurar una red para una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="c3c22-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="c3c22-116">Compartir hologramas en dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-117">Descubra otras personas en nuestro mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="c3c22-118">Cree una experiencia interactiva compartida donde pueda dirigirse a otros reproductores e iniciar proyectiles en ellos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="c3c22-119">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c3c22-120">Recurso</span><span class="sxs-lookup"><span data-stu-id="c3c22-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c3c22-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c3c22-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c3c22-122"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="c3c22-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c3c22-123">Uso compartido de MR 240: Varios dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="c3c22-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="c3c22-124">✔️</span><span class="sxs-lookup"><span data-stu-id="c3c22-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="c3c22-125">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="c3c22-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c3c22-126">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="c3c22-126">Prerequisites</span></span>

* <span data-ttu-id="c3c22-127">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md) correctas instaladas con acceso a Internet.</span><span class="sxs-lookup"><span data-stu-id="c3c22-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="c3c22-128">Al menos dos dispositivos HoloLens [configurados para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="c3c22-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="c3c22-129">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="c3c22-129">Project files</span></span>

* <span data-ttu-id="c3c22-130">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c3c22-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="c3c22-131">Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="c3c22-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="c3c22-132">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="c3c22-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="c3c22-133">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="c3c22-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="c3c22-134">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="c3c22-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="c3c22-135">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="c3c22-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="c3c22-136">Mantenga el nombre de la carpeta como **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="c3c22-137">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="c3c22-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="c3c22-138">Capítulo 1: Hololens World</span><span class="sxs-lookup"><span data-stu-id="c3c22-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="c3c22-139">En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="c3c22-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-140">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-140">Objectives</span></span>

* <span data-ttu-id="c3c22-141">Configure Unity para desarrollar aplicaciones holográficas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="c3c22-142">Vea su holograma.</span><span class="sxs-lookup"><span data-stu-id="c3c22-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-143">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-143">Instructions</span></span>

* <span data-ttu-id="c3c22-144">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="c3c22-144">Start Unity.</span></span>
* <span data-ttu-id="c3c22-145">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-145">Select **Open**.</span></span>
* <span data-ttu-id="c3c22-146">Escriba Location como la carpeta **SharedHolograms** que ha desarchivado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="c3c22-147">Seleccione **nombre del proyecto** y haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="c3c22-148">En la **jerarquía**, haga clic con el botón secundario en la **cámara principal** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="c3c22-149">En la carpeta **HoloToolkit-Sharing-240/Prefabs/cámara** , busque la **cámara principal** recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="c3c22-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="c3c22-150">Arrastre y coloque la **cámara principal** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="c3c22-151">En la **jerarquía**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="c3c22-152">Haga clic con el botón derecho en el nuevo **GameObject** y seleccione **cambiar nombre**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="c3c22-153">Cambie el nombre de GameObject a **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="c3c22-154">Seleccione el objeto **HologramCollection** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="c3c22-155">En el **Inspector** , establezca la posición de la **transformación** en: **X1 0, Y:-0,25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="c3c22-156">En la  carpeta hologramas del **panel Proyecto**, busque el recurso **EnergyHub** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="c3c22-157">Arrastre y coloque el objeto **EnergyHub** desde el **panel Proyecto** hasta la **jerarquía** como **elemento secundario de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="c3c22-158">Seleccione el **archivo > guardar la escena como...**</span><span class="sxs-lookup"><span data-stu-id="c3c22-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="c3c22-159">Asigne a la escena el nombre **SharedHolograms** y haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="c3c22-160">Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="c3c22-161">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="c3c22-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="c3c22-162">**Exportar el proyecto de Unity a Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="c3c22-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="c3c22-163">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="c3c22-164">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="c3c22-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="c3c22-165">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="c3c22-166">Establezca **SDK** en **universal 10**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="c3c22-167">Establezca **el dispositivo de destino** en **HoloLens** y el tipo de **compilación de UWP** en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="c3c22-168">Compruebe **los C# proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="c3c22-169">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-169">Click **Build**.</span></span>
* <span data-ttu-id="c3c22-170">En la ventana del explorador de archivos que aparece, cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="c3c22-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="c3c22-171">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="c3c22-172">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="c3c22-173">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="c3c22-174">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-174">Open the **App** folder.</span></span>
* <span data-ttu-id="c3c22-175">Abra **SharedHolograms. sln** para iniciar Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="c3c22-176">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="c3c22-177">Haga clic en la flecha desplegable situada junto a equipo local y seleccione **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="c3c22-178">Establezca la **Dirección** en el nombre o la dirección IP de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="c3c22-179">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas** o pregunte a Cortana **, ¿cuál es mi dirección IP? "** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="c3c22-180">Deje el **modo de autenticación** establecido en **universal**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="c3c22-181">Haga clic en **seleccionar**</span><span class="sxs-lookup"><span data-stu-id="c3c22-181">Click **Select**</span></span>
* <span data-ttu-id="c3c22-182">Haga clic en depurar **> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="c3c22-183">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="c3c22-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="c3c22-184">Pon en tu HoloLens y busca el holograma de EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3c22-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="c3c22-185">Capítulo 2: interacción</span><span class="sxs-lookup"><span data-stu-id="c3c22-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="c3c22-186">En este capítulo, Interactuaremos con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="c3c22-187">En primer lugar, vamos a agregar un cursor para visualizar nuestra [mirada](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="c3c22-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="c3c22-188">Después, agregaremos [gestos](gestures.md) y usaremos nuestra mano para colocar los hologramas en el espacio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-189">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-189">Objectives</span></span>

* <span data-ttu-id="c3c22-190">Use la entrada de fijamente para controlar un cursor.</span><span class="sxs-lookup"><span data-stu-id="c3c22-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="c3c22-191">Use la entrada de gestos para interactuar con los hologramas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-192">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-192">Instructions</span></span>

<span data-ttu-id="c3c22-193">**Gaze**</span><span class="sxs-lookup"><span data-stu-id="c3c22-193">**Gaze**</span></span>
* <span data-ttu-id="c3c22-194">En el **Panel jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3c22-195">En el **panel Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3c22-196">En el menú, escriba en el cuadro de búsqueda, **mira el administrador**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="c3c22-197">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-197">Select the search result.</span></span>
* <span data-ttu-id="c3c22-198">En la carpeta **HoloToolkit-Sharing-240\Prefabs\Input** , busque el recurso **cursor** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="c3c22-199">Arrastre y coloque el activo del **cursor** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="c3c22-200">**Hacia**</span><span class="sxs-lookup"><span data-stu-id="c3c22-200">**Gesture**</span></span>
* <span data-ttu-id="c3c22-201">En el **Panel jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3c22-202">Haga clic en **Agregar componente** y escriba **Administrador** de gestos en el campo de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="c3c22-203">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-203">Select the search result.</span></span>
* <span data-ttu-id="c3c22-204">En el **Panel jerarquía**, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="c3c22-205">Seleccione el objeto **EnergyHub** secundario.</span><span class="sxs-lookup"><span data-stu-id="c3c22-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="c3c22-206">En el **panel Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3c22-207">En el menú, escriba en la ubicación del **holograma**del cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="c3c22-208">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-208">Select the search result.</span></span>
* <span data-ttu-id="c3c22-209">Guarde la escena seleccionando **archivo > guardar escena**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="c3c22-210">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="c3c22-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3c22-211">Cree e implemente en HoloLens con las instrucciones del capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="c3c22-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="c3c22-212">Una vez que la aplicación se inicie en HoloLens, mueva el dedo y observe cómo el EnergyHub sigue su mirada.</span><span class="sxs-lookup"><span data-stu-id="c3c22-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="c3c22-213">Observe cómo aparece el cursor cuando mira el holograma y cambia a una luz puntual cuando no se Gazing en un holograma.</span><span class="sxs-lookup"><span data-stu-id="c3c22-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="c3c22-214">Realice una derivación aérea para colocar el holograma.</span><span class="sxs-lookup"><span data-stu-id="c3c22-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="c3c22-215">En este momento, en nuestro proyecto, solo puede colocar el holograma una vez (vuelva a implementarlo para intentarlo de nuevo).</span><span class="sxs-lookup"><span data-stu-id="c3c22-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="c3c22-216">Capítulo 3: coordenadas compartidas</span><span class="sxs-lookup"><span data-stu-id="c3c22-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="c3c22-217">Es divertido ver los hologramas e interactuar con ellos, pero vamos a continuar.</span><span class="sxs-lookup"><span data-stu-id="c3c22-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="c3c22-218">Configuraremos nuestra primera experiencia compartida: un holograma todo el mundo puede ver juntos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-219">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-219">Objectives</span></span>

* <span data-ttu-id="c3c22-220">Configurar una red para una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="c3c22-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="c3c22-221">Establezca un punto de referencia común.</span><span class="sxs-lookup"><span data-stu-id="c3c22-221">Establish a common reference point.</span></span>
* <span data-ttu-id="c3c22-222">Compartir sistemas de coordenadas entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="c3c22-223">Todos ven el mismo holograma.</span><span class="sxs-lookup"><span data-stu-id="c3c22-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="c3c22-224">Las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer** se deben declarar para que una aplicación se conecte al servidor de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="c3c22-225">Esto ya se hace en los hologramas 240, pero tenga esto en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="c3c22-226">En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".</span><span class="sxs-lookup"><span data-stu-id="c3c22-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="c3c22-227">Haga clic en la pestaña "tienda Windows"</span><span class="sxs-lookup"><span data-stu-id="c3c22-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="c3c22-228">En la sección "configuración de publicación > funcionalidades", Compruebe la funcionalidad de **InternetClientServer** y la capacidad de **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="c3c22-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-229">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-229">Instructions</span></span>

* <span data-ttu-id="c3c22-230">En el **panel Proyecto** , vaya a la carpeta **HoloToolkit-Sharing-240\Prefabs\Sharing** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="c3c22-231">Arrastre y coloque el recurso prefabricado de **uso compartido** en el **Panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="c3c22-232">A continuación, es necesario iniciar el servicio de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="c3c22-233">Solo **un equipo** en la experiencia compartida debe realizar este paso.</span><span class="sxs-lookup"><span data-stu-id="c3c22-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="c3c22-234">En Unity: en el menú de la parte superior, seleccione el **menú HoloToolkit-Sharing-240**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="c3c22-235">Seleccione el elemento **servicio de uso compartido de inicio** en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="c3c22-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="c3c22-236">Active la opción **red privada** y haga clic en **permitir el acceso** cuando aparezca el mensaje del firewall.</span><span class="sxs-lookup"><span data-stu-id="c3c22-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="c3c22-237">Anote la dirección IPv4 que se muestra en la ventana de la consola del servicio de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="c3c22-238">Se trata de la misma dirección IP que el equipo en el que se ejecuta el servicio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="c3c22-239">Siga el resto de las instrucciones en **todos los equipos** que se unirán a la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="c3c22-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="c3c22-240">En la **jerarquía**, seleccione el objeto de **uso compartido** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="c3c22-241">En el **Inspector**, en el componente de la **fase de uso compartido** , cambie la **dirección del servidor** de "localhost" a la dirección IPv4 del equipo que ejecuta SharingService. exe.</span><span class="sxs-lookup"><span data-stu-id="c3c22-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="c3c22-242">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3c22-243">En el **Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3c22-244">En el cuadro de búsqueda, escriba **Import Export Anchor Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="c3c22-245">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-245">Select the search result.</span></span>
* <span data-ttu-id="c3c22-246">En el **panel Proyecto** , vaya a  la carpeta scripts.</span><span class="sxs-lookup"><span data-stu-id="c3c22-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3c22-247">Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3c22-248">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="c3c22-249">De nuevo en Unity, seleccione el **HologramCollection** en el **Panel**de jerarquías.</span><span class="sxs-lookup"><span data-stu-id="c3c22-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="c3c22-250">En el **panel Inspector** , haga clic en el botón **Agregar componente** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="c3c22-251">En el menú, escriba en el cuadro de búsqueda **App State Manager**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="c3c22-252">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-252">Select the search result.</span></span>

<span data-ttu-id="c3c22-253">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="c3c22-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3c22-254">Compile el proyecto para los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-255">Designe un HoloLens en el que implementar primero.</span><span class="sxs-lookup"><span data-stu-id="c3c22-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="c3c22-256">Tendrá que esperar a que el delimitador se cargue en el servicio antes de poder colocar el EnergyHub (esto puede tardar ~ 30-60 segundos).</span><span class="sxs-lookup"><span data-stu-id="c3c22-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="c3c22-257">Hasta que se realice la carga, se omitirán los gestos de TAP.</span><span class="sxs-lookup"><span data-stu-id="c3c22-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="c3c22-258">Una vez colocada la EnergyHub, su ubicación se cargará en el servicio y, a continuación, podrá implementar en todos los demás dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-259">Cuando un nuevo HoloLens se une por primera vez a la sesión, es posible que la ubicación de EnergyHub no sea correcta en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c3c22-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="c3c22-260">Sin embargo, en cuanto se hayan descargado las ubicaciones de delimitador y EnergyHub desde el servicio, el EnergyHub debe saltar a la nueva ubicación compartida.</span><span class="sxs-lookup"><span data-stu-id="c3c22-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="c3c22-261">Si esto no ocurre en menos de 30-60 segundos, desplácese a la ubicación donde se encontraba HoloLens original al establecer el delimitador para recopilar más pistas de entorno.</span><span class="sxs-lookup"><span data-stu-id="c3c22-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="c3c22-262">Si la ubicación sigue sin bloquearse, vuelva a realizar la implementación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c3c22-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="c3c22-263">Cuando todos los dispositivos estén listos y ejecuten la aplicación, busque EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3c22-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="c3c22-264">¿Puede estar de acuerdo con la ubicación del holograma y la dirección en la que el texto está enfrente?</span><span class="sxs-lookup"><span data-stu-id="c3c22-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="c3c22-265">Capítulo 4: detección</span><span class="sxs-lookup"><span data-stu-id="c3c22-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="c3c22-266">Ahora todo el mundo puede ver el mismo holograma.</span><span class="sxs-lookup"><span data-stu-id="c3c22-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="c3c22-267">Ahora, vamos a ver a todos los demás conectados a nuestro mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="c3c22-268">En este capítulo, se tomará la ubicación principal y la rotación de todos los demás dispositivos HoloLens en la misma sesión de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="c3c22-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-269">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-269">Objectives</span></span>

* <span data-ttu-id="c3c22-270">Descubra entre sí en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="c3c22-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="c3c22-271">Elegir y compartir un avatar de reproductor.</span><span class="sxs-lookup"><span data-stu-id="c3c22-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="c3c22-272">Adjunte el avatar del jugador junto a los cabezales de todos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-273">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-273">Instructions</span></span>

* <span data-ttu-id="c3c22-274">En el **panel Proyecto** , vaya a  la carpeta hologramas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c3c22-275">Arrastre y coloque **PlayerAvatarStore** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="c3c22-276">En el **panel Proyecto** , vaya a  la carpeta scripts.</span><span class="sxs-lookup"><span data-stu-id="c3c22-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3c22-277">Haga doble clic en el script **AvatarSelector** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3c22-278">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="c3c22-279">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3c22-280">En el **Inspector** , haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c3c22-281">En el cuadro de búsqueda, escriba **Administrador del reproductor local**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="c3c22-282">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-282">Select the search result.</span></span>
* <span data-ttu-id="c3c22-283">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3c22-284">En el **Inspector** , haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c3c22-285">En el cuadro de búsqueda, escriba **Administrador**de reproductores remotos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="c3c22-286">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-286">Select the search result.</span></span>
* <span data-ttu-id="c3c22-287">Abra el script **HologramPlacement** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="c3c22-288">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="c3c22-289">Abra el script **AppStateManager** en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="c3c22-290">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="c3c22-291">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="c3c22-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="c3c22-292">Compile e implemente el proyecto en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-293">Cuando escuche un sonido de ping, busque el menú de selección de Avatar y seleccione un avatar con el gesto de punteo de aire.</span><span class="sxs-lookup"><span data-stu-id="c3c22-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="c3c22-294">Si no está mirando ningún holograma, la luz puntual alrededor del cursor girará un color diferente cuando HoloLens se comunique con el servicio: inicializando (púrpura oscuro), descargando el delimitador (verde), importando/exportando datos de ubicación (amarillo), cargar el delimitador (azul).</span><span class="sxs-lookup"><span data-stu-id="c3c22-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="c3c22-295">Si la luz de punto alrededor del cursor es el color predeterminado (púrpura claro), está listo para interactuar con otros jugadores en la sesión.</span><span class="sxs-lookup"><span data-stu-id="c3c22-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="c3c22-296">Mire otras personas conectadas a su espacio: en este caso, habrá un robot holográfica que se flota por encima de su hombro y imitando sus movimientos de cabeza.</span><span class="sxs-lookup"><span data-stu-id="c3c22-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="c3c22-297">Capítulo 5: selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="c3c22-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="c3c22-298">En este capítulo, haremos que el anclaje sea capaz de colocarse en superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="c3c22-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="c3c22-299">Usaremos coordenadas compartidas para colocar ese delimitador en el punto intermedio entre todos los usuarios conectados a la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="c3c22-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-300">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-300">Objectives</span></span>

* <span data-ttu-id="c3c22-301">Coloque los hologramas en el mapa espacial en función de la posición principal de los jugadores.</span><span class="sxs-lookup"><span data-stu-id="c3c22-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-302">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-302">Instructions</span></span>

* <span data-ttu-id="c3c22-303">En el **panel Proyecto** , vaya a  la carpeta hologramas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c3c22-304">Arrastre y coloque el recurso prefabricado de **CustomSpatialMapping** en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="c3c22-305">En el **panel Proyecto** , vaya a  la carpeta scripts.</span><span class="sxs-lookup"><span data-stu-id="c3c22-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3c22-306">Haga doble clic en el script **AppStateManager** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3c22-307">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="c3c22-308">En el **panel Proyecto** , vaya a  la carpeta scripts.</span><span class="sxs-lookup"><span data-stu-id="c3c22-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="c3c22-309">Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3c22-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="c3c22-310">Reemplace el contenido por el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="c3c22-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="c3c22-311">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="c3c22-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3c22-312">Compile e implemente el proyecto en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-313">Cuando la aplicación esté lista, destaque un círculo y observe cómo aparece EnergyHub en el centro de todos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="c3c22-314">Puntee para colocar el EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3c22-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="c3c22-315">Pruebe el comando de voz "restablecer destino" para elegir la copia de seguridad de EnergyHub y trabajar conjuntamente como un grupo para trasladar el holograma a una nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="c3c22-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="c3c22-316">Capítulo 6: física del mundo real</span><span class="sxs-lookup"><span data-stu-id="c3c22-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="c3c22-317">En este capítulo, vamos a agregar hologramas que rebotan las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="c3c22-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="c3c22-318">Vea el espacio lleno con proyectos que usted y sus amigos han lanzado.</span><span class="sxs-lookup"><span data-stu-id="c3c22-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-319">Objectives</span></span>

* <span data-ttu-id="c3c22-320">Inicie los proyectiles que rebotan las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="c3c22-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="c3c22-321">Comparta los proyectiles para que otros jugadores puedan verlos.</span><span class="sxs-lookup"><span data-stu-id="c3c22-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-322">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-322">Instructions</span></span>

* <span data-ttu-id="c3c22-323">En la **jerarquía** , seleccione el objeto **HologramCollection** .</span><span class="sxs-lookup"><span data-stu-id="c3c22-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="c3c22-324">En el **Inspector** , haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="c3c22-325">En el cuadro de búsqueda, escriba **selector de proyectil**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="c3c22-326">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-326">Select the search result.</span></span>

<span data-ttu-id="c3c22-327">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="c3c22-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3c22-328">Cree e implemente en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-329">Cuando la aplicación se ejecuta en todos los dispositivos, realice una derivación aérea para lanzar el proyectil en las superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="c3c22-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="c3c22-330">Vea lo que sucede cuando el proyectil entra en conflicto con el avatar de otro jugador.</span><span class="sxs-lookup"><span data-stu-id="c3c22-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="c3c22-331">Capítulo 7: final general</span><span class="sxs-lookup"><span data-stu-id="c3c22-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="c3c22-332">En este capítulo, se descubrirá un portal que solo se puede detectar con colaboración.</span><span class="sxs-lookup"><span data-stu-id="c3c22-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="c3c22-333">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c3c22-333">Objectives</span></span>

* <span data-ttu-id="c3c22-334">Trabaje de forma conjunta para iniciar suficientes proyectiles en el anclaje para descubrir un portal secreto.</span><span class="sxs-lookup"><span data-stu-id="c3c22-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="c3c22-335">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c3c22-335">Instructions</span></span>

* <span data-ttu-id="c3c22-336">En el **panel Proyecto** , vaya a  la carpeta hologramas.</span><span class="sxs-lookup"><span data-stu-id="c3c22-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="c3c22-337">Arrastre y coloque el  activo de submundo como **elemento secundario de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="c3c22-338">Con **HologramCollection** seleccionado, haga clic en el botón **Agregar componente** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="c3c22-339">En el menú, escriba en el cuadro de búsqueda **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="c3c22-340">Seleccione el resultado de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c3c22-340">Select the search result.</span></span>
* <span data-ttu-id="c3c22-341">Con **HologramCollection** seleccionado, en la **jerarquía** , arrastre el objeto **EnergyHub** hasta el campo de **destino** en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="c3c22-342">Con **HologramCollection** seleccionado, en la **jerarquía** , arrastre  el objeto de submundo al campo de submundo del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="c3c22-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="c3c22-343">**Implementación y disfrute**</span><span class="sxs-lookup"><span data-stu-id="c3c22-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="c3c22-344">Cree e implemente en sus dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3c22-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="c3c22-345">Cuando se haya iniciado la aplicación, colabore con el fin de lanzar proyectiles en el EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="c3c22-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="c3c22-346">Cuando aparezca el submundo, inicie los proyectiles en el mundo de los robots (golpee un robot tres veces para obtener una diversión adicional).</span><span class="sxs-lookup"><span data-stu-id="c3c22-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
