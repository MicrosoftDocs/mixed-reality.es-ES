---
title: MR compartir 240 - varios dispositivos HoloLens
description: Siga este tutorial con Unity, Visual Studio y HoloLens para conocer los detalles de uso compartido hologramas de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, compartir, redes, academy, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601388"
---
>[!NOTE]
><span data-ttu-id="cfced-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="cfced-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="cfced-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="cfced-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="cfced-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="cfced-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="cfced-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="cfced-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="cfced-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cfced-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="cfced-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="cfced-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="cfced-110">MR 240 de uso compartido: Varios dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="cfced-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="cfced-111">Hologramas tienen presencia en nuestro mundo al permanecer en su lugar conforme se mueve en el espacio.</span><span class="sxs-lookup"><span data-stu-id="cfced-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="cfced-112">HoloLens mantiene hologramas en su lugar utilizando varios [sistemas de coordenadas](coordinate-systems.md) para realizar un seguimiento de la ubicación y la orientación de objetos.</span><span class="sxs-lookup"><span data-stu-id="cfced-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="cfced-113">Cuando se comparten entre los dispositivos de estos sistemas de coordenadas, podemos crear una experiencia compartida que nos permite tomar parte en un mundo holográfico compartido.</span><span class="sxs-lookup"><span data-stu-id="cfced-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="cfced-114">En este tutorial, se hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfced-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="cfced-115">Configurar una red para una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="cfced-116">Compartir hologramas en todos los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="cfced-117">Descubra otras personas de nuestro mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="cfced-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="cfced-118">Cree una experiencia interactiva compartida donde puede tener como destino otros jugadores - e iniciar los proyectiles a ellos.</span><span class="sxs-lookup"><span data-stu-id="cfced-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="cfced-119">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="cfced-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="cfced-120">Curso</span><span class="sxs-lookup"><span data-stu-id="cfced-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="cfced-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="cfced-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="cfced-122"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="cfced-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="cfced-123">MR 240 de uso compartido: Varios dispositivos HoloLens</span><span class="sxs-lookup"><span data-stu-id="cfced-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="cfced-124">✔️</span><span class="sxs-lookup"><span data-stu-id="cfced-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="cfced-125">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="cfced-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="cfced-126">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="cfced-126">Prerequisites</span></span>

* <span data-ttu-id="cfced-127">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md) con acceso a Internet.</span><span class="sxs-lookup"><span data-stu-id="cfced-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="cfced-128">Al menos dos dispositivos HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="cfced-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="cfced-129">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="cfced-129">Project files</span></span>

* <span data-ttu-id="cfced-130">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="cfced-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="cfced-131">Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="cfced-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="cfced-132">Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span><span class="sxs-lookup"><span data-stu-id="cfced-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="cfced-133">Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span><span class="sxs-lookup"><span data-stu-id="cfced-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="cfced-134">Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span><span class="sxs-lookup"><span data-stu-id="cfced-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="cfced-135">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="cfced-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="cfced-136">Mantenga el nombre de carpeta **SharedHolograms**.</span><span class="sxs-lookup"><span data-stu-id="cfced-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="cfced-137">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span><span class="sxs-lookup"><span data-stu-id="cfced-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="cfced-138">Capítulo 1: Holo World</span><span class="sxs-lookup"><span data-stu-id="cfced-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="cfced-139">En este capítulo, crearemos nuestro primer proyecto de Unity y paso a través de la compilación de la instalación y proceso de implementación.</span><span class="sxs-lookup"><span data-stu-id="cfced-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-140">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-140">Objectives</span></span>

* <span data-ttu-id="cfced-141">La instalación de Unity para desarrollar aplicaciones holográficas.</span><span class="sxs-lookup"><span data-stu-id="cfced-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="cfced-142">¡Vea su holograma!</span><span class="sxs-lookup"><span data-stu-id="cfced-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-143">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-143">Instructions</span></span>

* <span data-ttu-id="cfced-144">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="cfced-144">Start Unity.</span></span>
* <span data-ttu-id="cfced-145">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="cfced-145">Select **Open**.</span></span>
* <span data-ttu-id="cfced-146">Escriba la ubicación que el **SharedHolograms** carpetas que anteriormente sin archivar.</span><span class="sxs-lookup"><span data-stu-id="cfced-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="cfced-147">Seleccione **nombre del proyecto** y haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="cfced-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="cfced-148">En el **jerarquía**, haga clic en el **cámara principal** y seleccione **eliminar**.</span><span class="sxs-lookup"><span data-stu-id="cfced-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="cfced-149">En el **HoloToolkit-uso compartido-240/prefabricados/cámara** carpeta, busque la **cámara principal** prefabricado.</span><span class="sxs-lookup"><span data-stu-id="cfced-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="cfced-150">Arrastre y coloque el **cámara principal** en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="cfced-151">En el **jerarquía**, haga clic en **crear** y **crear vacío**.</span><span class="sxs-lookup"><span data-stu-id="cfced-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="cfced-152">Haga clic en el nuevo **GameObject** y seleccione **cambiar el nombre**.</span><span class="sxs-lookup"><span data-stu-id="cfced-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="cfced-153">Cambiar el nombre de la GameObject a **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="cfced-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="cfced-154">Seleccione el **HologramCollection** objeto en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="cfced-155">En el **Inspector** establecer el **transformar posición** para: **X: 0, Y: -0.25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="cfced-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="cfced-156">En el **hologramas** carpeta en el **panel proyecto**, busque el **EnergyHub** activo.</span><span class="sxs-lookup"><span data-stu-id="cfced-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="cfced-157">Arrastre y coloque el **EnergyHub** objeto desde el **panel proyecto** a la **jerarquía** como un **secundarios de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="cfced-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="cfced-158">Seleccione **archivo > Guardar escena como...**</span><span class="sxs-lookup"><span data-stu-id="cfced-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="cfced-159">Nombre de la escena **SharedHolograms** y haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="cfced-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="cfced-160">Presione el **reproducir** en Unity para obtener una vista previa de sus hologramas botón.</span><span class="sxs-lookup"><span data-stu-id="cfced-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="cfced-161">Presione **reproducir** una segunda vez para detener el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="cfced-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="cfced-162">**Exporta el proyecto de Unity a Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="cfced-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="cfced-163">En Seleccione Unity **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="cfced-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="cfced-164">Haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="cfced-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="cfced-165">Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="cfced-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="cfced-166">Establecer **SDK** a **10 Universal**.</span><span class="sxs-lookup"><span data-stu-id="cfced-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="cfced-167">Establecer **dispositivo de destino** a **HoloLens** y **el tipo de compilación UWP** a **D3D**.</span><span class="sxs-lookup"><span data-stu-id="cfced-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="cfced-168">Comprobar **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="cfced-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="cfced-169">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="cfced-169">Click **Build**.</span></span>
* <span data-ttu-id="cfced-170">En la ventana del explorador de archivos que aparece, cree un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="cfced-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="cfced-171">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="cfced-172">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="cfced-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="cfced-173">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="cfced-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="cfced-174">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-174">Open the **App** folder.</span></span>
* <span data-ttu-id="cfced-175">Abra **SharedHolograms.sln** para iniciar Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="cfced-176">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X86**.</span><span class="sxs-lookup"><span data-stu-id="cfced-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="cfced-177">Haga clic en la flecha desplegable situada junto a la máquina Local y seleccione **dispositivo remoto**.</span><span class="sxs-lookup"><span data-stu-id="cfced-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="cfced-178">Establecer el **dirección** en el nombre o dirección IP de su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="cfced-179">Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas** o solicitar a Cortana **"Hola Cortana, ¿cuál es mi dirección IP?"**</span><span class="sxs-lookup"><span data-stu-id="cfced-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="cfced-180">Deje el **modo de autenticación** establecido en **Universal**.</span><span class="sxs-lookup"><span data-stu-id="cfced-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="cfced-181">Haga clic en **seleccionar**</span><span class="sxs-lookup"><span data-stu-id="cfced-181">Click **Select**</span></span>
* <span data-ttu-id="cfced-182">Haga clic en **Depurar > Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="cfced-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="cfced-183">Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span><span class="sxs-lookup"><span data-stu-id="cfced-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="cfced-184">Colocar en su HoloLens y busque el holograma EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="cfced-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="cfced-185">Capítulo 2: interacción</span><span class="sxs-lookup"><span data-stu-id="cfced-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="cfced-186">En este capítulo, interactuamos con nuestros hologramas.</span><span class="sxs-lookup"><span data-stu-id="cfced-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="cfced-187">En primer lugar, vamos a agregar un cursor para visualizar nuestro [que mirar](gaze.md).</span><span class="sxs-lookup"><span data-stu-id="cfced-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="cfced-188">A continuación, agregaremos [gestos](gestures.md) y use nuestra mano para colocar nuestros hologramas en el espacio.</span><span class="sxs-lookup"><span data-stu-id="cfced-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-189">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-189">Objectives</span></span>

* <span data-ttu-id="cfced-190">Utilice la mirada de entrada para controlar un cursor.</span><span class="sxs-lookup"><span data-stu-id="cfced-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="cfced-191">Utilice el gesto de entrada para interactuar con hologramas.</span><span class="sxs-lookup"><span data-stu-id="cfced-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-192">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-192">Instructions</span></span>

<span data-ttu-id="cfced-193">**Gaze**</span><span class="sxs-lookup"><span data-stu-id="cfced-193">**Gaze**</span></span>
* <span data-ttu-id="cfced-194">En el **panel jerarquía** seleccione la **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="cfced-195">En el **panel Inspector** haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="cfced-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="cfced-196">En el menú, escriba en el cuadro de búsqueda **que mirar Manager**.</span><span class="sxs-lookup"><span data-stu-id="cfced-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="cfced-197">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-197">Select the search result.</span></span>
* <span data-ttu-id="cfced-198">En el **240\Prefabs\Input compartir HoloToolkit** carpeta, busque la **Cursor** activo.</span><span class="sxs-lookup"><span data-stu-id="cfced-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="cfced-199">Arrastre y coloque el **Cursor** activo hasta la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="cfced-200">**Gesto**</span><span class="sxs-lookup"><span data-stu-id="cfced-200">**Gesture**</span></span>
* <span data-ttu-id="cfced-201">En el **panel jerarquía** seleccione la **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="cfced-202">Haga clic en **Agregar componente** y tipo **gesto Manager** en el campo de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="cfced-203">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-203">Select the search result.</span></span>
* <span data-ttu-id="cfced-204">En el **panel jerarquía**, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="cfced-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="cfced-205">Seleccione el elemento secundario **EnergyHub** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="cfced-206">En el **panel Inspector** haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="cfced-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="cfced-207">En el menú, escriba en el cuadro de búsqueda **holograma colocación**.</span><span class="sxs-lookup"><span data-stu-id="cfced-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="cfced-208">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-208">Select the search result.</span></span>
* <span data-ttu-id="cfced-209">Guarde la escena seleccionando **archivo > Guardar escena**.</span><span class="sxs-lookup"><span data-stu-id="cfced-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="cfced-210">**Implementar y disfrute**</span><span class="sxs-lookup"><span data-stu-id="cfced-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="cfced-211">Compilar e implementar en su HoloLens, siguiendo las instrucciones del capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="cfced-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="cfced-212">Una vez que inicie la aplicación en su HoloLens, mover la cabeza y observe cómo la EnergyHub sigue a su mirada.</span><span class="sxs-lookup"><span data-stu-id="cfced-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="cfced-213">Observe cómo el cursor aparece cuando visita el holograma y cambia a una luz puntual cuando no gazing en un holograma.</span><span class="sxs-lookup"><span data-stu-id="cfced-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="cfced-214">Realizar una derivación de aire para colocar el holograma.</span><span class="sxs-lookup"><span data-stu-id="cfced-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="cfced-215">En este momento en el proyecto, puede colocar solo una vez el holograma (vuelva a intentarlo).</span><span class="sxs-lookup"><span data-stu-id="cfced-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="cfced-216">Coordina el capítulo 3: compartidos</span><span class="sxs-lookup"><span data-stu-id="cfced-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="cfced-217">Es divertido ver e interactuar con hologramas, pero vayamos más lejos.</span><span class="sxs-lookup"><span data-stu-id="cfced-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="cfced-218">Configuraremos nuestra primera experiencia compartido - un holograma todos pueden ver juntos.</span><span class="sxs-lookup"><span data-stu-id="cfced-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-219">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-219">Objectives</span></span>

* <span data-ttu-id="cfced-220">Configurar una red para una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="cfced-221">Establecer un punto de referencia común.</span><span class="sxs-lookup"><span data-stu-id="cfced-221">Establish a common reference point.</span></span>
* <span data-ttu-id="cfced-222">Compartir sistemas de coordenadas en los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="cfced-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="cfced-223">¡Todos los usuarios ven el mismo holograma!</span><span class="sxs-lookup"><span data-stu-id="cfced-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="cfced-224">El **InternetClientServer** y **PrivateNetworkClientServer** capacidades se deben declarar para que una aplicación se conecte al servidor de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="cfced-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="cfced-225">Esto se hace por usted ya hologramas 240, pero Téngalo en cuenta para sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="cfced-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="cfced-226">En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"</span><span class="sxs-lookup"><span data-stu-id="cfced-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="cfced-227">Haga clic en la pestaña "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="cfced-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="cfced-228">En la sección "Funcionalidades de publicación configuración >", compruebe el **InternetClientServer** capacidad y la **PrivateNetworkClientServer** capacidad</span><span class="sxs-lookup"><span data-stu-id="cfced-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-229">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-229">Instructions</span></span>

* <span data-ttu-id="cfced-230">En el **panel proyecto** vaya a la **240\Prefabs\Sharing compartir HoloToolkit** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="cfced-231">Arrastre y coloque el **compartir** prefabricado en el **panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="cfced-232">A continuación, se debe iniciar el servicio de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="cfced-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="cfced-233">Solo **un PC** en el recurso compartido experimentar debe realizar este paso.</span><span class="sxs-lookup"><span data-stu-id="cfced-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="cfced-234">En Unity: en el menú de la mano de la parte superior, seleccione el **240 compartir HoloToolkit menú**.</span><span class="sxs-lookup"><span data-stu-id="cfced-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="cfced-235">Seleccione el **iniciar el servicio de uso compartido** elemento en la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="cfced-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="cfced-236">Compruebe el **red privada** opción y haga clic en **permitir el acceso a** cuando aparezca el símbolo del sistema del servidor de seguridad.</span><span class="sxs-lookup"><span data-stu-id="cfced-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="cfced-237">Anote la dirección IPv4 que se muestran en la ventana de consola de servicio de uso compartido.</span><span class="sxs-lookup"><span data-stu-id="cfced-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="cfced-238">Se trata de la misma dirección IP que la máquina que se ejecuta en el servicio.</span><span class="sxs-lookup"><span data-stu-id="cfced-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="cfced-239">Siga el resto de las instrucciones **todos los equipos** que unirá la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="cfced-240">En el **jerarquía**, seleccione el **compartir** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="cfced-241">En el **Inspector**, en el **compartir fase** componente, cambie la **dirección del servidor** desde 'localhost' a la dirección IPv4 de la máquina que ejecuta SharingService.exe.</span><span class="sxs-lookup"><span data-stu-id="cfced-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="cfced-242">En el **jerarquía** seleccione la **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="cfced-243">En el **Inspector** haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="cfced-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="cfced-244">En el cuadro de búsqueda, escriba **Administrador de anclaje de exportación de importación**.</span><span class="sxs-lookup"><span data-stu-id="cfced-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="cfced-245">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-245">Select the search result.</span></span>
* <span data-ttu-id="cfced-246">En el **panel proyecto** vaya a la **Scripts** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="cfced-247">Haga doble clic en el **HologramPlacement** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="cfced-248">Reemplace el contenido con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfced-248">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="cfced-249">En Unity, seleccione el **HologramCollection** en el **panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="cfced-250">En el **panel Inspector** haga clic en el **Agregar componente** botón.</span><span class="sxs-lookup"><span data-stu-id="cfced-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="cfced-251">En el menú, escriba en el cuadro de búsqueda **Administrador de estado de la aplicación**.</span><span class="sxs-lookup"><span data-stu-id="cfced-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="cfced-252">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-252">Select the search result.</span></span>

<span data-ttu-id="cfced-253">**Implementar y disfrute**</span><span class="sxs-lookup"><span data-stu-id="cfced-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="cfced-254">Compile el proyecto para los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="cfced-255">Designar uno HoloLens para implementar en primer lugar.</span><span class="sxs-lookup"><span data-stu-id="cfced-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="cfced-256">Deberá esperar el delimitador que se cargará en el servicio para poder poner el EnergyHub (este proceso puede tardar aproximadamente entre 30 y 60 segundos).</span><span class="sxs-lookup"><span data-stu-id="cfced-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="cfced-257">Hasta que se realiza la carga, se omitirán los gestos de tap.</span><span class="sxs-lookup"><span data-stu-id="cfced-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="cfced-258">Después de que se ha colocado el EnergyHub, su ubicación se cargarán en el servicio y, a continuación, puede implementar en todos los demás dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="cfced-259">Cuando un nuevo HoloLens en primer lugar une a la sesión, la ubicación de la EnergyHub no sea correcta en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cfced-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="cfced-260">Sin embargo, tan pronto como el delimitador y EnergyHub ubicaciones se han descargado desde el servicio, el EnergyHub debería saltar a la nueva ubicación compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="cfced-261">Si esto no sucede dentro de ~ 30 y 60 segundos, recorrer en la que se encontraba el HoloLens original cuando se establece el delimitador para recopilar más pistas de entorno.</span><span class="sxs-lookup"><span data-stu-id="cfced-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="cfced-262">Si no bloquea la ubicación todavía, volver a implementar en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cfced-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="cfced-263">Cuando los dispositivos están listos y ejecuta la aplicación, busque el EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="cfced-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="cfced-264">¿Puede que todos acuerden ubicación del holograma y en qué dirección mira el texto?</span><span class="sxs-lookup"><span data-stu-id="cfced-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="cfced-265">Capítulo 4: detección</span><span class="sxs-lookup"><span data-stu-id="cfced-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="cfced-266">¡Ahora todo el mundo puede ver el mismo holograma!</span><span class="sxs-lookup"><span data-stu-id="cfced-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="cfced-267">Ahora vamos a ver todos los usuarios conectados else en nuestro mundo holográfica compartido.</span><span class="sxs-lookup"><span data-stu-id="cfced-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="cfced-268">En este capítulo, se tomará la ubicación principal y la rotación de todos los demás dispositivos HoloLens en la misma sesión de uso compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-269">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-269">Objectives</span></span>

* <span data-ttu-id="cfced-270">Descubrirse entre ellos en nuestra experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="cfced-271">Seleccionar y compartir un avatar del Reproductor.</span><span class="sxs-lookup"><span data-stu-id="cfced-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="cfced-272">Adjunte el avatar del Reproductor junto a la mente de todos.</span><span class="sxs-lookup"><span data-stu-id="cfced-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-273">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-273">Instructions</span></span>

* <span data-ttu-id="cfced-274">En el **panel proyecto** vaya a la **hologramas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="cfced-275">Arrastre y coloque el **PlayerAvatarStore** en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="cfced-276">En el **panel proyecto** vaya a la **Scripts** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="cfced-277">Haga doble clic en el **AvatarSelector** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="cfced-278">Reemplace el contenido con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfced-278">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="cfced-279">En el **jerarquía** seleccione la **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="cfced-280">En el **Inspector** haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="cfced-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="cfced-281">En el cuadro de búsqueda, escriba **Local Reproductor Manager**.</span><span class="sxs-lookup"><span data-stu-id="cfced-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="cfced-282">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-282">Select the search result.</span></span>
* <span data-ttu-id="cfced-283">En el **jerarquía** seleccione la **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="cfced-284">En el **Inspector** haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="cfced-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="cfced-285">En el cuadro de búsqueda, escriba **remoto Reproductor Manager**.</span><span class="sxs-lookup"><span data-stu-id="cfced-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="cfced-286">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-286">Select the search result.</span></span>
* <span data-ttu-id="cfced-287">Abra el **HologramPlacement** script en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="cfced-288">Reemplace el contenido con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfced-288">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="cfced-289">Abra el **AppStateManager** script en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="cfced-290">Reemplace el contenido con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfced-290">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="cfced-291">**Implementar y disfrute**</span><span class="sxs-lookup"><span data-stu-id="cfced-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="cfced-292">Compilar e implementar el proyecto a los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="cfced-293">Cuando oye un sonido haciendo ping, el menú de selección de avatar de buscar y seleccionar un avatar con el gesto de pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="cfced-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="cfced-294">Si no ve ningún hologramas, el punto de luz en torno al cursor activará un color diferente cuando su HoloLens se comunican con el servicio: Inicializando (violeta oscuro), que descarga el delimitador (verde), importar o exportar datos de ubicación (amarillo), Cargando el delimitador (azul).</span><span class="sxs-lookup"><span data-stu-id="cfced-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="cfced-295">Si el punto de luz en torno a su cursor es el color predeterminado (púrpura claro), a continuación, está listo para interactuar con otros jugadores en la sesión.</span><span class="sxs-lookup"><span data-stu-id="cfced-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="cfced-296">Mirar otras personas conectadas a su espacio - habrá un robot holográfico flotando encima de su hombro y mediante la imitación de sus movimientos principales!</span><span class="sxs-lookup"><span data-stu-id="cfced-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="cfced-297">Capítulo 5: selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="cfced-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="cfced-298">En este capítulo, nos aseguraremos de hacer el delimitador que se pueden colocar en superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="cfced-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="cfced-299">Vamos a usar coordenadas compartidas para colocar ese delimitador en el punto medio entre todos los usuarios conectados a la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="cfced-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-300">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-300">Objectives</span></span>

* <span data-ttu-id="cfced-301">Colocar hologramas en el mapa espacial en función de posición principales de jugadores.</span><span class="sxs-lookup"><span data-stu-id="cfced-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-302">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-302">Instructions</span></span>

* <span data-ttu-id="cfced-303">En el **panel proyecto** vaya a la **hologramas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="cfced-304">Arrastre y coloque el **CustomSpatialMapping** prefabricado hasta el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="cfced-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="cfced-305">En el **panel proyecto** vaya a la **Scripts** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="cfced-306">Haga doble clic en el **AppStateManager** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="cfced-307">Reemplace el contenido con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfced-307">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="cfced-308">En el **panel proyecto** vaya a la **Scripts** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="cfced-309">Haga doble clic en el **HologramPlacement** script para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cfced-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="cfced-310">Reemplace el contenido con el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="cfced-310">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="cfced-311">**Implementar y disfrute**</span><span class="sxs-lookup"><span data-stu-id="cfced-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="cfced-312">Compilar e implementar el proyecto a los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="cfced-313">Cuando la aplicación esté lista y todo ello en un círculo, tenga en cuenta cómo el EnergyHub aparece en el centro de todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="cfced-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="cfced-314">Pulse para colocar el EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="cfced-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="cfced-315">Pruebe el comando de voz de restablecimiento de destino para seleccionar el EnergyHub copia de seguridad y trabajar juntos como un grupo para mover el holograma a una nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="cfced-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="cfced-316">Capítulo 6: físicas reales</span><span class="sxs-lookup"><span data-stu-id="cfced-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="cfced-317">En este capítulo, vamos a agregar hologramas que reboten en superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="cfced-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="cfced-318">¡Ver el espacio se llene con proyectos iniciados por usted y sus amigos!</span><span class="sxs-lookup"><span data-stu-id="cfced-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-319">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-319">Objectives</span></span>

* <span data-ttu-id="cfced-320">Inicie los proyectiles que reboten en superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="cfced-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="cfced-321">Comparta los proyectiles para que otros jugadores pueden verlos.</span><span class="sxs-lookup"><span data-stu-id="cfced-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-322">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-322">Instructions</span></span>

* <span data-ttu-id="cfced-323">En el **jerarquía** seleccione la **HologramCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="cfced-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="cfced-324">En el **Inspector** haga clic en **Agregar componente**.</span><span class="sxs-lookup"><span data-stu-id="cfced-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="cfced-325">En el cuadro de búsqueda, escriba **proyectil iniciador**.</span><span class="sxs-lookup"><span data-stu-id="cfced-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="cfced-326">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-326">Select the search result.</span></span>

<span data-ttu-id="cfced-327">**Implementar y disfrute**</span><span class="sxs-lookup"><span data-stu-id="cfced-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="cfced-328">Compilar e implementar en los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="cfced-329">Cuando se ejecuta la aplicación en todos los dispositivos, realice una derivación de aire para iniciar proyectil en superficies del mundo real.</span><span class="sxs-lookup"><span data-stu-id="cfced-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="cfced-330">¡Vea lo que sucede cuando su proyectil entra en conflicto con el avatar del otro reproductor!</span><span class="sxs-lookup"><span data-stu-id="cfced-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="cfced-331">Capítulo 7 - gran objetivo</span><span class="sxs-lookup"><span data-stu-id="cfced-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="cfced-332">En este capítulo, se podrá revelar un portal que solo se puede detectar con la colaboración.</span><span class="sxs-lookup"><span data-stu-id="cfced-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="cfced-333">Objetivos</span><span class="sxs-lookup"><span data-stu-id="cfced-333">Objectives</span></span>

* <span data-ttu-id="cfced-334">Funcionan conjuntamente para iniciar suficiente proyectiles en el delimitador para revelar un secreto portal!</span><span class="sxs-lookup"><span data-stu-id="cfced-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="cfced-335">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="cfced-335">Instructions</span></span>

* <span data-ttu-id="cfced-336">En el **panel proyecto** vaya a la **hologramas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="cfced-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="cfced-337">Arrastre y coloque el **Underword** activo como un **secundarios de HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="cfced-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="cfced-338">Con **HologramCollection** seleccionado, haga clic en el **Agregar componente** situado en la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="cfced-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="cfced-339">En el menú, escriba en el cuadro de búsqueda **ExplodeTarget**.</span><span class="sxs-lookup"><span data-stu-id="cfced-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="cfced-340">Seleccione el resultado de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="cfced-340">Select the search result.</span></span>
* <span data-ttu-id="cfced-341">Con **HologramCollection** seleccionado desde la **jerarquía** arrastrar el **EnergyHub** de objeto para el **destino** campo el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="cfced-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="cfced-342">Con **HologramCollection** seleccionado desde la **jerarquía** arrastrar el **Underword** de objeto para el **Underword** campo el  **Inspector de**.</span><span class="sxs-lookup"><span data-stu-id="cfced-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="cfced-343">**Implementar y disfrute**</span><span class="sxs-lookup"><span data-stu-id="cfced-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="cfced-344">Compilar e implementar en los dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cfced-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="cfced-345">Cuando se inicia la aplicación, colaborar para iniciar los proyectiles a lo EnergyHub.</span><span class="sxs-lookup"><span data-stu-id="cfced-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="cfced-346">Cuando aparezca el Underword, inicie proyectiles a robots Underword (acierto un robot tres veces por diversión adicional).</span><span class="sxs-lookup"><span data-stu-id="cfced-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
