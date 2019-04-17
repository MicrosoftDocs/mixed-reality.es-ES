---
title: El Sr. espacial 220 - sonido espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de sonido espaciales.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, sonido espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599017"
---
>[!NOTE]
><span data-ttu-id="4daab-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="4daab-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4daab-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4daab-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4daab-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="4daab-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4daab-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="4daab-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4daab-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4daab-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4daab-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="4daab-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="4daab-110">MR 220 espacial: Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="4daab-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="4daab-111">[Sonido espacial](spatial-sound.md) breathes vida en hologramas y les da presencia en nuestro mundo.</span><span class="sxs-lookup"><span data-stu-id="4daab-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="4daab-112">Hologramas se componen de luz y sonido, y si resulta que pasar por alto las hologramas, espacial sonido puede ayudarle a encontrarlas.</span><span class="sxs-lookup"><span data-stu-id="4daab-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="4daab-113">Sonido espacial no es como el sonido típico que desea escuchar en el radio, es el sonido que se coloca en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="4daab-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="4daab-114">Con sonido espacial, puede realizar hologramas sonido que están detrás de usted, a su lado o incluso en la cabeza!</span><span class="sxs-lookup"><span data-stu-id="4daab-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="4daab-115">En este curso, aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="4daab-115">In this course, you will:</span></span>

* <span data-ttu-id="4daab-116">Configurar el entorno de desarrollo para utilizar Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="4daab-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="4daab-117">Usar un sonido espacial para mejorar las interacciones.</span><span class="sxs-lookup"><span data-stu-id="4daab-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="4daab-118">Usar un sonido espacial junto con la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="4daab-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="4daab-119">Comprender el diseño del sonido y mezclando los procedimientos recomendados.</span><span class="sxs-lookup"><span data-stu-id="4daab-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="4daab-120">Usar un sonido para mejorar los efectos especiales y conducir al usuario en el mundo de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="4daab-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="4daab-121">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="4daab-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4daab-122">Curso</span><span class="sxs-lookup"><span data-stu-id="4daab-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4daab-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4daab-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4daab-124"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="4daab-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="4daab-125">MR 220 espacial: Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="4daab-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="4daab-126">✔️</span><span class="sxs-lookup"><span data-stu-id="4daab-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4daab-127">✔️</span><span class="sxs-lookup"><span data-stu-id="4daab-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="4daab-128">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="4daab-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4daab-129">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="4daab-129">Prerequisites</span></span>

* <span data-ttu-id="4daab-130">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="4daab-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="4daab-131">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="4daab-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="4daab-132">Debe haber completado [MR Fundamentos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="4daab-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="4daab-133">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="4daab-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="4daab-134">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="4daab-134">Project files</span></span>

* <span data-ttu-id="4daab-135">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4daab-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="4daab-136"> Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="4daab-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="4daab-137">Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="4daab-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="4daab-138">Esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="4daab-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="4daab-139">Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="4daab-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="4daab-140"> Esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="4daab-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="4daab-141">Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="4daab-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="4daab-142"> Esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="4daab-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="4daab-143">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="4daab-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="4daab-144">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="4daab-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="4daab-145">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="4daab-145">Errata and Notes</span></span>

* <span data-ttu-id="4daab-146">"Habilitar Solo mi código" debe deshabilitarse (*unchecked*) en Visual Studio en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="4daab-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="4daab-147">Capítulo 1: instalación de Unity</span><span class="sxs-lookup"><span data-stu-id="4daab-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="4daab-148">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4daab-148">Objectives</span></span>

* <span data-ttu-id="4daab-149">Cambiar la configuración de sonido de Unity para usar Microsoft Spatial Sound.</span><span class="sxs-lookup"><span data-stu-id="4daab-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="4daab-150">Agregar sonido 3D a un objeto en Unity.</span><span class="sxs-lookup"><span data-stu-id="4daab-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="4daab-151">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-151">Instructions</span></span>

* <span data-ttu-id="4daab-152">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="4daab-152">Start Unity.</span></span>
* <span data-ttu-id="4daab-153">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="4daab-153">Select **Open**.</span></span>
* <span data-ttu-id="4daab-154">Vaya al escritorio y busque la carpeta se archivados previamente sin.</span><span class="sxs-lookup"><span data-stu-id="4daab-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="4daab-155">Haga clic en el **Starting\Decibel** carpeta y, a continuación, presione el **Seleccionar carpeta** botón.</span><span class="sxs-lookup"><span data-stu-id="4daab-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="4daab-156">Espere a que el proyecto se carga en Unity.</span><span class="sxs-lookup"><span data-stu-id="4daab-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="4daab-157">En el **proyecto** panel abierto **Scenes\Decibel.unity**.</span><span class="sxs-lookup"><span data-stu-id="4daab-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="4daab-158">En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="4daab-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="4daab-159">En el Inspector de, expanda **AudioSource** y tenga en cuenta que no hay ningún **Spatialize** casilla de verificación.</span><span class="sxs-lookup"><span data-stu-id="4daab-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="4daab-160">De forma predeterminada, Unity no carga un complemento espacial.</span><span class="sxs-lookup"><span data-stu-id="4daab-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="4daab-161">Los pasos siguientes permitirán espacial sonido en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4daab-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="4daab-162">En el menú superior de Unity, vaya a **Editar > configuración del proyecto > Audio**.</span><span class="sxs-lookup"><span data-stu-id="4daab-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="4daab-163">Buscar el **espacial complemento** lista desplegable y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="4daab-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="4daab-164">En el **jerarquía** panel, seleccione **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="4daab-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="4daab-165">En el **Inspector** panel, busque el **origen Audio** componente.</span><span class="sxs-lookup"><span data-stu-id="4daab-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="4daab-166">Compruebe el **Spatialize** casilla de verificación.</span><span class="sxs-lookup"><span data-stu-id="4daab-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="4daab-167">Arrastre el **Blend espacial** control deslizante hasta **3D**, o escriba **1** en el cuadro de edición.</span><span class="sxs-lookup"><span data-stu-id="4daab-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="4daab-168">Ahora cree el proyecto en Unity y configurar la solución en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daab-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="4daab-169">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="4daab-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="4daab-170">Haga clic en **agregar escenas abierto** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="4daab-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="4daab-171">Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="4daab-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="4daab-172">Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="4daab-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="4daab-173">En caso contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="4daab-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="4daab-174">Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="4daab-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="4daab-175">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="4daab-175">Click **Build**.</span></span>
7. <span data-ttu-id="4daab-176">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="4daab-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="4daab-177">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="4daab-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="4daab-178">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="4daab-178">Press **Select Folder**.</span></span>

<span data-ttu-id="4daab-179">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="4daab-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="4daab-180">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="4daab-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="4daab-181">Abra el **solución de Visual Studio de decibelios**.</span><span class="sxs-lookup"><span data-stu-id="4daab-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="4daab-182">Si la implementación en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="4daab-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="4daab-183">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.</span><span class="sxs-lookup"><span data-stu-id="4daab-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="4daab-184">Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="4daab-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="4daab-185">Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**.</span><span class="sxs-lookup"><span data-stu-id="4daab-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="4daab-186">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="4daab-186">Click **Select**.</span></span> <span data-ttu-id="4daab-187">Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="4daab-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="4daab-188">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="4daab-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="4daab-189">Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="4daab-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="4daab-190">Si la implementación en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="4daab-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="4daab-191">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.</span><span class="sxs-lookup"><span data-stu-id="4daab-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="4daab-192">Asegúrese de que el destino de implementación se establece en **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="4daab-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="4daab-193">En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="4daab-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="4daab-194">Capítulo 2: sonido espacial e interacción</span><span class="sxs-lookup"><span data-stu-id="4daab-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="4daab-195">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4daab-195">Objectives</span></span>

* <span data-ttu-id="4daab-196">Mejore el realismo holograma mediante sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="4daab-197">Dirigir la mirada del usuario mediante sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="4daab-198">Proporcionar comentarios de gesto mediante sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="4daab-199">Parte 1: si quiere mejorar</span><span class="sxs-lookup"><span data-stu-id="4daab-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-200">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-200">Key Concepts</span></span>

* <span data-ttu-id="4daab-201">Spatialize sonidos holograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="4daab-202">Orígenes de sonido deben colocarse en una ubicación adecuada en el holograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="4daab-203">La ubicación adecuada para el sonido va a depender del holograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="4daab-204">Por ejemplo, si el holograma es de una persona, el origen de sonido debe encontrarse cerca de la boca y no los pies.</span><span class="sxs-lookup"><span data-stu-id="4daab-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="4daab-205">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-205">Instructions</span></span>

<span data-ttu-id="4daab-206">Las siguientes instrucciones asociará un sonido spatialized un holograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="4daab-207">En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="4daab-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="4daab-208">En el **Inspector** panel el **AudioSource**, haga clic en el círculo junto a **AudioClip** y seleccione **PolyHover** desde el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="4daab-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="4daab-209">Haga clic en el círculo junto a **salida** y seleccione **efectos de sonido** desde el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="4daab-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="4daab-210">Proyecto decibelios usa un Unity **AudioMixer** componente para habilitar el ajuste de los niveles de sonido para grupos de sonidos.</span><span class="sxs-lookup"><span data-stu-id="4daab-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="4daab-211">Por agrupación sonidos de este modo, se puede ajustar el volumen global al tiempo que mantiene el volumen relativo de cada sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="4daab-212">En el **AudioSource**, expanda **configuración sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="4daab-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="4daab-213">Establecer **Doppler nivel** a **0**.</span><span class="sxs-lookup"><span data-stu-id="4daab-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="4daab-214">Establecer nivel Doppler a cero los deshabilita cambios de timbre causados por el movimiento (ya sea el holograma o del usuario).</span><span class="sxs-lookup"><span data-stu-id="4daab-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="4daab-215">Un ejemplo clásico de Doppler es un automóvil de avance rápido.</span><span class="sxs-lookup"><span data-stu-id="4daab-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="4daab-216">Como el vehículo aproxima a un agente de escucha inmóvil, aumenta el tono del motor.</span><span class="sxs-lookup"><span data-stu-id="4daab-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="4daab-217">Cuando pasa el agente de escucha, el tono disminuye con la distancia.</span><span class="sxs-lookup"><span data-stu-id="4daab-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="4daab-218">Parte 2: dirigir la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="4daab-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-219">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-219">Key Concepts</span></span>

* <span data-ttu-id="4daab-220">Usar un sonido para llamar la atención sobre hologramas importante.</span><span class="sxs-lookup"><span data-stu-id="4daab-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="4daab-221">Las orejas ayudarán a dirigir donde deben buscar los ojos.</span><span class="sxs-lookup"><span data-stu-id="4daab-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="4daab-222">El cerebro tiene ciertas expectativas aprendidos.</span><span class="sxs-lookup"><span data-stu-id="4daab-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="4daab-223">Un ejemplo de expectativas aprendidos es que generalmente son pájaros por encima de los cabezales de los seres humanos.</span><span class="sxs-lookup"><span data-stu-id="4daab-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="4daab-224">Si un usuario oye un sonido de pájaro, su reacción inicial es buscar.</span><span class="sxs-lookup"><span data-stu-id="4daab-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="4daab-225">Colocación de una vista de pájaro a continuación el usuario puede dar lugar a ellos orientado a la dirección correcta de sonido, pero no puede encontrar el holograma según la expectativa de que se necesitan buscar.</span><span class="sxs-lookup"><span data-stu-id="4daab-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="4daab-226">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-226">Instructions</span></span>

<span data-ttu-id="4daab-227">Las instrucciones siguientes permiten P0LY ocultar detrás, para que pueda usar sonido para localizar el holograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="4daab-228">En el **jerarquía** panel, seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="4daab-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="4daab-229">En el **Inspector** panel, busque **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="4daab-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="4daab-230">En **controlador de entrada de voz**, expanda **vaya ocultar**.</span><span class="sxs-lookup"><span data-stu-id="4daab-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="4daab-231">Cambio **ninguna función** a **PolyActions.GoHide**.</span><span class="sxs-lookup"><span data-stu-id="4daab-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![palabra clave: Ocultar vaya](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="4daab-233">Parte 3: comentarios de gestos</span><span class="sxs-lookup"><span data-stu-id="4daab-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-234">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-234">Key Concepts</span></span>

* <span data-ttu-id="4daab-235">Proporcione al usuario confirmación positivo gesto con sonido</span><span class="sxs-lookup"><span data-stu-id="4daab-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="4daab-236">No se sobrecargará el usuario - get sonidos demasiado altos de la manera</span><span class="sxs-lookup"><span data-stu-id="4daab-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="4daab-237">Sonidos sutiles funcionan mejor - no hagan la experiencia</span><span class="sxs-lookup"><span data-stu-id="4daab-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="4daab-238">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-238">Instructions</span></span>

* <span data-ttu-id="4daab-239">En el **jerarquía** del panel, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="4daab-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="4daab-240">Expanda **EnergyHub** y seleccione **Base**.</span><span class="sxs-lookup"><span data-stu-id="4daab-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="4daab-241">En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **controlador de gestos sonido**.</span><span class="sxs-lookup"><span data-stu-id="4daab-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="4daab-242">En **controlador de gestos sonido**, haga clic en el círculo junto a **navegación iniciado Clip** y **navegación actualizado Clip** y seleccione **RotateClick**desde la ventana emergente para ambos.</span><span class="sxs-lookup"><span data-stu-id="4daab-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="4daab-243">Haga doble clic en "GestureSoundHandler" para cargar en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daab-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="4daab-244">Controlador de gestos sonido realiza las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="4daab-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="4daab-245">Crear y configurar un **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="4daab-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="4daab-246">Colocar el **AudioSource** en la ubicación de la correspondiente **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="4daab-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="4daab-247">Reproduce el **AudioClip** relacionadas con el gesto.</span><span class="sxs-lookup"><span data-stu-id="4daab-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="4daab-248">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="4daab-248">Build and Deploy</span></span>

1. <span data-ttu-id="4daab-249">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="4daab-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="4daab-250">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="4daab-250">Click **Build**.</span></span>
3. <span data-ttu-id="4daab-251">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="4daab-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="4daab-252">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="4daab-252">Press **Select Folder**.</span></span>

<span data-ttu-id="4daab-253">Compruebe que la barra de herramientas dice "Release", "x 86" o "x64" y "Dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="4daab-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="4daab-254">Si no es así, se trata de la instancia de codificación de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daab-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="4daab-255">Es posible que deba volver a abrir la solución desde la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4daab-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="4daab-256">Si se le solicite, vuelva a cargar los archivos del proyecto.</span><span class="sxs-lookup"><span data-stu-id="4daab-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="4daab-257">Como antes, la implementación desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daab-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="4daab-258">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="4daab-258">After the application is deployed:</span></span>

* <span data-ttu-id="4daab-259">Observe cómo el sonido cambia al desplazarse por P0LY.</span><span class="sxs-lookup"><span data-stu-id="4daab-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="4daab-260">Por ejemplo *"Ocultar vaya"* realizar P0LY mover a una ubicación que tiene detrás.</span><span class="sxs-lookup"><span data-stu-id="4daab-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="4daab-261">Encontrarlo si el sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-261">Find it by the sound.</span></span>
* <span data-ttu-id="4daab-262">Mire la base del concentrador de energía.</span><span class="sxs-lookup"><span data-stu-id="4daab-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="4daab-263">Pulse y arrastre izquierda o derecha para girar el holograma y observe cómo el sonido de clic confirma el gesto.</span><span class="sxs-lookup"><span data-stu-id="4daab-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="4daab-264">Nota: Hay un panel de texto que se va a tag-along con usted.</span><span class="sxs-lookup"><span data-stu-id="4daab-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="4daab-265">Contiene los comandos de voz disponibles que puede usar a lo largo de este curso.</span><span class="sxs-lookup"><span data-stu-id="4daab-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="4daab-266">Capítulo 3: asignación espacial de sonido y espacial</span><span class="sxs-lookup"><span data-stu-id="4daab-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="4daab-267">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4daab-267">Objectives</span></span>

* <span data-ttu-id="4daab-268">Confirme la interacción entre hologramas y el mundo real mediante sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="4daab-269">Occlude sonido con el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="4daab-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="4daab-270">Parte 1: interacción del mundo físico</span><span class="sxs-lookup"><span data-stu-id="4daab-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-271">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-271">Key Concepts</span></span>

* <span data-ttu-id="4daab-272">Los objetos físicos generalmente emita un sonido al encontrar una superficie u otro objeto.</span><span class="sxs-lookup"><span data-stu-id="4daab-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="4daab-273">Sonidos deben ser el contexto adecuado dentro de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="4daab-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="4daab-274">Por ejemplo, al definir una taza de una tabla, debe realizar un sonido y más suave que quitar un boulder en una parte del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="4daab-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="4daab-275">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-275">Instructions</span></span>

* <span data-ttu-id="4daab-276">En el **jerarquía** del panel, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="4daab-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="4daab-277">Expanda **EnergyHub**, seleccione **Base**.</span><span class="sxs-lookup"><span data-stu-id="4daab-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="4daab-278">En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **acción y puntee en lugar de a con sonido**.</span><span class="sxs-lookup"><span data-stu-id="4daab-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="4daab-279">En **pulse al lugar con la acción y sonido**:</span><span class="sxs-lookup"><span data-stu-id="4daab-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="4daab-280">Comprobar **colocar primario al pulsar**.</span><span class="sxs-lookup"><span data-stu-id="4daab-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="4daab-281">Establecer **colocación sonido** a **lugar**.</span><span class="sxs-lookup"><span data-stu-id="4daab-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="4daab-282">Establecer **Pickup sonido** a **Pickup**.</span><span class="sxs-lookup"><span data-stu-id="4daab-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="4daab-283">Presione el signo + de la parte inferior derecha bajo **Pickup acción** y **en acción de selección de ubicación**.</span><span class="sxs-lookup"><span data-stu-id="4daab-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="4daab-284">Arrastre EnergyHub desde la escena en el **None (objeto)** campos.</span><span class="sxs-lookup"><span data-stu-id="4daab-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="4daab-285">En **Pickup acción**, haga clic en **sin función** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="4daab-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="4daab-286">En **en acción de selección de ubicación**, haga clic en **sin función** -> **EnergyHubBase** -> **OnSelect**.</span><span class="sxs-lookup"><span data-stu-id="4daab-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Pulse en lugar de con la acción y sonido](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="4daab-288">Parte 2: oclusión de sonido</span><span class="sxs-lookup"><span data-stu-id="4daab-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-289">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-289">Key Concepts</span></span>

* <span data-ttu-id="4daab-290">Sonido, al igual que la luz, puede ser ocluido.</span><span class="sxs-lookup"><span data-stu-id="4daab-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="4daab-291">Un ejemplo clásico es una sala de conciertos.</span><span class="sxs-lookup"><span data-stu-id="4daab-291">A classic example is a concert hall.</span></span> <span data-ttu-id="4daab-292">Cuando un agente de escucha es permanente fuera del pasillo y la puerta se cierra, los sonidos de música atenuarse.</span><span class="sxs-lookup"><span data-stu-id="4daab-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="4daab-293">Normalmente, también es una reducción del volumen.</span><span class="sxs-lookup"><span data-stu-id="4daab-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="4daab-294">Cuando se abre la puerta, todo el espectro de sonido se escucha en el volumen real.</span><span class="sxs-lookup"><span data-stu-id="4daab-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="4daab-295">Sonidos de alta frecuencia generalmente absorbe más de las frecuencias bajas.</span><span class="sxs-lookup"><span data-stu-id="4daab-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="4daab-296">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-296">Instructions</span></span>

* <span data-ttu-id="4daab-297">En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="4daab-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="4daab-298">En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **Audio emisor**.</span><span class="sxs-lookup"><span data-stu-id="4daab-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="4daab-299">La clase emisora Audio proporciona las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="4daab-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="4daab-300">Restaura los cambios en el volumen de la **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="4daab-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="4daab-301">Realiza una **Physics.RaycastNonAlloc** desde la posición del usuario en la dirección de la **GameObject** a la que el **AudioEmitter** está conectado.</span><span class="sxs-lookup"><span data-stu-id="4daab-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="4daab-302">El método RaycastNonAlloc se utiliza como una optimización del rendimiento para limitar las asignaciones, así como el número de resultados devueltos.</span><span class="sxs-lookup"><span data-stu-id="4daab-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="4daab-303">Para cada **IAudioInfluencer** encontrado, llama a la **ApplyEffect** método.</span><span class="sxs-lookup"><span data-stu-id="4daab-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="4daab-304">Para cada uno anterior **IAudioInfluencer** es decir, ya no se ha encontrado, llamada la **RemoveEffect** método.</span><span class="sxs-lookup"><span data-stu-id="4daab-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="4daab-305">Tenga en cuenta que AudioEmitter se actualiza en escalas de tiempo humano, en contraposición a en un fotograma a fotograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="4daab-306">Esto se hace porque los seres humanos generalmente no se mueven lo suficientemente rápido para que el efecto a deben actualizarse con más frecuencia que cada trimestre o medio segundo.</span><span class="sxs-lookup"><span data-stu-id="4daab-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="4daab-307">Hologramas ese teleport rápidamente desde una ubicación a otra puede interrumpir la ilusión.</span><span class="sxs-lookup"><span data-stu-id="4daab-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="4daab-308">En el **jerarquía** del panel, expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="4daab-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="4daab-309">Expanda **EnergyHub** y seleccione **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="4daab-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="4daab-310">En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **Occluder Audio**.</span><span class="sxs-lookup"><span data-stu-id="4daab-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="4daab-311">En **Audio Occluder**, establezca **límite de frecuencia** a **1500**.</span><span class="sxs-lookup"><span data-stu-id="4daab-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="4daab-312">Esta configuración limita las frecuencias AudioSource a 1500 Hz y anteriores.</span><span class="sxs-lookup"><span data-stu-id="4daab-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="4daab-313">Establecer **volumen pasar** a **0.9**.</span><span class="sxs-lookup"><span data-stu-id="4daab-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="4daab-314">Esta configuración reduce el volumen de la AudioSource al 90% de su nivel actual.</span><span class="sxs-lookup"><span data-stu-id="4daab-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="4daab-315">Audio Occluder implementa IAudioInfluencer para:</span><span class="sxs-lookup"><span data-stu-id="4daab-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="4daab-316">Aplicar un efecto de oclusión utilizando un **AudioLowPassFilter** que se asocia a la **AudioSource** administrado comprar el **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="4daab-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="4daab-317">Aplica la atenuación de volumen a la AudioSource.</span><span class="sxs-lookup"><span data-stu-id="4daab-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="4daab-318">Deshabilita el efecto de establecer una frecuencia de corte neutra y deshabilitando el filtro.</span><span class="sxs-lookup"><span data-stu-id="4daab-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="4daab-319">La frecuencia usada como neutro es 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="4daab-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="4daab-320">Se ha elegido esta frecuencia debido a que está por encima de la frecuencia máxima nominal que pueda ser escuchada por el oído humano, no realizar ningún impacto perceptible en el sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="4daab-321">En el **jerarquía** panel, seleccione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="4daab-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="4daab-322">En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **Occluder Audio**.</span><span class="sxs-lookup"><span data-stu-id="4daab-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="4daab-323">En **Audio Occluder**, establezca **límite de frecuencia** a **750**.</span><span class="sxs-lookup"><span data-stu-id="4daab-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="4daab-324">Cuando varios occluders se encuentran en la ruta de acceso entre el usuario y la **AudioEmitter**, la frecuencia mínima se aplica el filtro.</span><span class="sxs-lookup"><span data-stu-id="4daab-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="4daab-325">Establecer **volumen pasar** a **0,75**.</span><span class="sxs-lookup"><span data-stu-id="4daab-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="4daab-326">Cuando varios occluders se encuentran en la ruta de acceso entre el usuario y la **AudioEmitter**, se aplica el paso de volumen a través de aditivamente.</span><span class="sxs-lookup"><span data-stu-id="4daab-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="4daab-327">En el **jerarquía** panel, seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="4daab-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="4daab-328">En el **Inspector** del panel, expanda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="4daab-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="4daab-329">En **controlador de entrada de voz**, expanda **cargo vaya**.</span><span class="sxs-lookup"><span data-stu-id="4daab-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="4daab-330">Cambio **ninguna función** a **PolyActions.GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="4daab-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![palabra clave: Vaya a cargo](images/gocharge.png)

* <span data-ttu-id="4daab-332">Expanda **aquí**.</span><span class="sxs-lookup"><span data-stu-id="4daab-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="4daab-333">Cambio **ninguna función** a **PolyActions.ComeBack**.</span><span class="sxs-lookup"><span data-stu-id="4daab-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![palabra clave: Ven aca](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="4daab-335">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="4daab-335">Build and Deploy</span></span>

* <span data-ttu-id="4daab-336">Como antes, compile el proyecto de Unity e implemente en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daab-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="4daab-337">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="4daab-337">After the application is deployed:</span></span>

* <span data-ttu-id="4daab-338">Por ejemplo *"Cargo por ir"* para que P0LY entrar en el centro de energía.</span><span class="sxs-lookup"><span data-stu-id="4daab-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="4daab-339">Tenga en cuenta el cambio en el sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-339">Note the change in the sound.</span></span> <span data-ttu-id="4daab-340">Debe parecer un poco más silencioso y estropeados.</span><span class="sxs-lookup"><span data-stu-id="4daab-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="4daab-341">Si es posible colocar manualmente con una pared u otro objeto entre usted y el centro de energía, debe observar un muffling adicional del sonido debido a la ocultación de todo el mundo real.</span><span class="sxs-lookup"><span data-stu-id="4daab-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="4daab-342">Por ejemplo *"Proceden aquí"* tener P0LY deje el concentrador de energía y colocarse delante de usted.</span><span class="sxs-lookup"><span data-stu-id="4daab-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="4daab-343">Tenga en cuenta que se ha quitado la ocultación de sonido cuando P0LY se cierra el concentrador de energía.</span><span class="sxs-lookup"><span data-stu-id="4daab-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="4daab-344">Si sigues siendo oclusión de audición, P0LY es posible que se ocluyeron en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="4daab-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="4daab-345">Intente mover para asegurarse de que tiene un claro ejemplo de línea de visión a P0LY.</span><span class="sxs-lookup"><span data-stu-id="4daab-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="4daab-346">Parte 3: modelos de sala</span><span class="sxs-lookup"><span data-stu-id="4daab-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-347">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-347">Key Concepts</span></span>

* <span data-ttu-id="4daab-348">El tamaño del espacio proporciona colas subliminales que contribuyen a la localización de sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="4daab-349">Los modelos de la sala se establecen por-**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="4daab-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="4daab-350">El [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona código para establecer el modelo de espacio.</span><span class="sxs-lookup"><span data-stu-id="4daab-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="4daab-351">Para la experiencia de realidad mixta, seleccione el modelo de espacio que mejor se ajusta el espacio del mundo real.</span><span class="sxs-lookup"><span data-stu-id="4daab-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="4daab-352">Si va a crear un escenario de realidad Virtual, seleccione el modelo de espacio que se adapte el entorno virtual.</span><span class="sxs-lookup"><span data-stu-id="4daab-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="4daab-353">Capítulo 4: diseño de sonido</span><span class="sxs-lookup"><span data-stu-id="4daab-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="4daab-354">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4daab-354">Objectives</span></span>

* <span data-ttu-id="4daab-355">Conocer las consideraciones de diseño eficaz de sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="4daab-356">Obtenga información sobre las directrices y técnicas de mezcla.</span><span class="sxs-lookup"><span data-stu-id="4daab-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="4daab-357">Parte 1: diseño de la experiencia y sonido</span><span class="sxs-lookup"><span data-stu-id="4daab-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="4daab-358">Esta sección describe directrices y consideraciones de diseño de experiencia y sonido clave de.</span><span class="sxs-lookup"><span data-stu-id="4daab-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="4daab-359">Normalizar todos los sonidos</span><span class="sxs-lookup"><span data-stu-id="4daab-359">Normalize all sounds</span></span>

<span data-ttu-id="4daab-360">Esto evita la necesidad de código de casos especial ajustar los niveles de volumen por sonido, que puede llevar mucho tiempo y limita la capacidad para actualizar fácilmente los archivos de sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="4daab-361">Diseño para una experiencia sin restricción</span><span class="sxs-lookup"><span data-stu-id="4daab-361">Design for an untethered experience</span></span>

<span data-ttu-id="4daab-362">HoloLens es un equipo completamente independiente, sin restricción holográfico.</span><span class="sxs-lookup"><span data-stu-id="4daab-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="4daab-363">Los usuarios pueden y usará sus experiencias al mover.</span><span class="sxs-lookup"><span data-stu-id="4daab-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="4daab-364">No olvide probar la mezcla de audio recorriendo alrededor.</span><span class="sxs-lookup"><span data-stu-id="4daab-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="4daab-365">Emitir sonidos desde ubicaciones lógicas en sus hologramas</span><span class="sxs-lookup"><span data-stu-id="4daab-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="4daab-366">En el mundo real, un perro no corteza de su cola y voz de una persona no proceden de sus pies.</span><span class="sxs-lookup"><span data-stu-id="4daab-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="4daab-367">Evitar la que emisión de los sonidos de inesperado partes de sus hologramas.</span><span class="sxs-lookup"><span data-stu-id="4daab-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="4daab-368">Para hologramas pequeño, es razonable tener sonido emitir desde el centro de la geometría.</span><span class="sxs-lookup"><span data-stu-id="4daab-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="4daab-369">Suena familiar es más localizable</span><span class="sxs-lookup"><span data-stu-id="4daab-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="4daab-370">La voz humana y la música son muy fáciles de localizar.</span><span class="sxs-lookup"><span data-stu-id="4daab-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="4daab-371">Si alguien llama a su nombre, es capaz de manera muy precisa determinar de qué dirección proviene de la voz y de cómo lejos.</span><span class="sxs-lookup"><span data-stu-id="4daab-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="4daab-372">Sonidos cortos y desconocidas son más difíciles de localizar.</span><span class="sxs-lookup"><span data-stu-id="4daab-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="4daab-373">Estar al corriente de las expectativas del usuario</span><span class="sxs-lookup"><span data-stu-id="4daab-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="4daab-374">Experiencia de vida juega un papel en nuestra capacidad para identificar la ubicación de un sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="4daab-375">Se trata de uno de los motivos por qué la voz humana es especialmente fácil de localizar.</span><span class="sxs-lookup"><span data-stu-id="4daab-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="4daab-376">Es importante tener en cuenta las expectativas de los usuarios aprendidos al colocar los sonidos.</span><span class="sxs-lookup"><span data-stu-id="4daab-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="4daab-377">Por ejemplo, cuando alguien oye una canción de la vista de pájaro generalmente parecen, como pájaros tienden a estar por encima de la línea de visión (volando o en un árbol).</span><span class="sxs-lookup"><span data-stu-id="4daab-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="4daab-378">No es raro que un usuario activar en la dirección correcta de un sonido, pero buscar en la dirección equivocada vertical y dejarán de estar confundirse o frustrados cuando se ha podido encontrar el holograma.</span><span class="sxs-lookup"><span data-stu-id="4daab-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="4daab-379">Evite los emisores ocultos</span><span class="sxs-lookup"><span data-stu-id="4daab-379">Avoid hidden emitters</span></span>

<span data-ttu-id="4daab-380">En el mundo real, si recibimos un sonido, podemos identificar por lo general el objeto que emite el sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="4daab-381">Esto también debe contener true en sus experiencias.</span><span class="sxs-lookup"><span data-stu-id="4daab-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="4daab-382">Puede ser muy desconcertar a los usuarios para oír un sonido, sabe de dónde se origina el sonido y podrá ver un objeto.</span><span class="sxs-lookup"><span data-stu-id="4daab-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="4daab-383">Existen algunas excepciones a esta directriz.</span><span class="sxs-lookup"><span data-stu-id="4daab-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="4daab-384">Por ejemplo, los sonidos ambientales como Bates de cricket en un campo no debe visibles.</span><span class="sxs-lookup"><span data-stu-id="4daab-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="4daab-385">Experiencia de vida nos da la familiaridad con el origen de estos sonidos sin necesidad de verlo.</span><span class="sxs-lookup"><span data-stu-id="4daab-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="4daab-386">Parte 2: mezcla de sonido</span><span class="sxs-lookup"><span data-stu-id="4daab-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="4daab-387">Destino de la combinación adecuada para el volumen de un 70% en el HoloLens</span><span class="sxs-lookup"><span data-stu-id="4daab-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="4daab-388">Experiencias de realidad mixtas permiten hologramas para verse en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="4daab-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="4daab-389">También deben permitir sonidos del mundo real se oye hablar mucho.</span><span class="sxs-lookup"><span data-stu-id="4daab-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="4daab-390">Un destino de un 70% del volumen permite al usuario escuchar el mundo en torno a ellas, junto con el sonido de su experiencia.</span><span class="sxs-lookup"><span data-stu-id="4daab-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="4daab-391">HoloLens en 100% del volumen deben ahogar los sonidos externos</span><span class="sxs-lookup"><span data-stu-id="4daab-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="4daab-392">Un nivel de volumen del 100% es semejante a una experiencia de realidad Virtual.</span><span class="sxs-lookup"><span data-stu-id="4daab-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="4daab-393">Visualmente, el usuario se transporta a un mundo diferente.</span><span class="sxs-lookup"><span data-stu-id="4daab-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="4daab-394">La misma debe cumplirse audible.</span><span class="sxs-lookup"><span data-stu-id="4daab-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="4daab-395">Utilice el AudioMixer Unity para ajustar las categorías de sonidos</span><span class="sxs-lookup"><span data-stu-id="4daab-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="4daab-396">Al diseñar la combinación, a menudo resulta útil crear categorías de sonido y tiene la posibilidad de aumentar o reducir su volumen como una unidad.</span><span class="sxs-lookup"><span data-stu-id="4daab-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="4daab-397">Esto conserva los niveles relativos de cada sonido y se permiten cambios rápidos y sencillo a la combinación global.</span><span class="sxs-lookup"><span data-stu-id="4daab-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="4daab-398">Incluyen categorías comunes; efectos de sonido de ambiente, voz superpuesta y música de fondo.</span><span class="sxs-lookup"><span data-stu-id="4daab-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="4daab-399">Combinación de sonidos según la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="4daab-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="4daab-400">A menudo puede ser útil cambiar la combinación de sonidos en su experiencia en función de dónde un usuario es (o no) busca.</span><span class="sxs-lookup"><span data-stu-id="4daab-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="4daab-401">Un uso común de esta técnica son reducir el nivel de volumen para hologramas que se encuentran fuera del marco holográfica para que sea más fácil para el usuario para centrarse en la información frente a ellas.</span><span class="sxs-lookup"><span data-stu-id="4daab-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="4daab-402">Otro uso es aumentar el volumen de un sonido para atraer la atención del usuario a un evento importante.</span><span class="sxs-lookup"><span data-stu-id="4daab-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="4daab-403">Creación de la combinación</span><span class="sxs-lookup"><span data-stu-id="4daab-403">Building your mix</span></span>

<span data-ttu-id="4daab-404">Al compilar la combinación, se recomienda comenzar con audio de fondo de su experiencia y agregar capas basadas en importancia.</span><span class="sxs-lookup"><span data-stu-id="4daab-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="4daab-405">A menudo, esto da como resultado de cada capa que se va a aumentar el volumen que el anterior.</span><span class="sxs-lookup"><span data-stu-id="4daab-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="4daab-406">Uno se imagina la combinación como un embudo invertido, con menos importante (y por lo general los sonidos) en la parte inferior, se recomienda para estructurar la combinación similar al siguiente diagrama.</span><span class="sxs-lookup"><span data-stu-id="4daab-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Estructura de la combinación de sonido](images/soundlevels.png)

<span data-ttu-id="4daab-408">Voz superpuesta es un escenario interesante.</span><span class="sxs-lookup"><span data-stu-id="4daab-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="4daab-409">Basándose en la experiencia que se va a crear es posible que desee tener un sonido estéreo (no localizado) o spatialize su voz superpuesta.</span><span class="sxs-lookup"><span data-stu-id="4daab-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="4daab-410">Publicado por Microsoft dos experiencias de ilustrar excelente ejemplos de cada escenario.</span><span class="sxs-lookup"><span data-stu-id="4daab-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="4daab-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voz estéreo a través.</span><span class="sxs-lookup"><span data-stu-id="4daab-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="4daab-412">Cuando el Narrador que describe la ubicación que se va a ver, el sonido es coherente y no varían en función de la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="4daab-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="4daab-413">Esto permite que el Narrador describir la escena sin toma de los sonidos spatialized del entorno.</span><span class="sxs-lookup"><span data-stu-id="4daab-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="4daab-414">[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utiliza una voz spatialized sobre en forma de un detective.</span><span class="sxs-lookup"><span data-stu-id="4daab-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="4daab-415">Voz del detective se usa para ayudar a que la atención del usuario a una importante pista como si fuera un humanos real en la sala.</span><span class="sxs-lookup"><span data-stu-id="4daab-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="4daab-416">Esto permite una mayor sensación de inmersión en la experiencia para resolver el misterio.</span><span class="sxs-lookup"><span data-stu-id="4daab-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="4daab-417">Parte 3: rendimiento</span><span class="sxs-lookup"><span data-stu-id="4daab-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="4daab-418">Uso de CPU</span><span class="sxs-lookup"><span data-stu-id="4daab-418">CPU usage</span></span>

<span data-ttu-id="4daab-419">Al usar sonido espacial, 10-12 emisores consumirá aproximadamente un 12% de la CPU.</span><span class="sxs-lookup"><span data-stu-id="4daab-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="4daab-420">Archivos de sonido de larga duración Stream</span><span class="sxs-lookup"><span data-stu-id="4daab-420">Stream long audio files</span></span>

<span data-ttu-id="4daab-421">Datos de audio pueden ser grandes, especialmente a velocidades de muestreo comunes (48 y 44,1 kHz).</span><span class="sxs-lookup"><span data-stu-id="4daab-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="4daab-422">Por regla general es que se deben transmitir archivos de audio más de 5 a 10 segundos para reducir el uso de memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4daab-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="4daab-423">En Unity, puede marcar un archivo de audio para el streaming en importar la configuración del archivo.</span><span class="sxs-lookup"><span data-stu-id="4daab-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Configuración de importación de audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="4daab-425">Capítulo 5: efectos especiales</span><span class="sxs-lookup"><span data-stu-id="4daab-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="4daab-426">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4daab-426">Objectives</span></span>

* <span data-ttu-id="4daab-427">Agregar profundidad a "Magic Windows".</span><span class="sxs-lookup"><span data-stu-id="4daab-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="4daab-428">Poner el usuario en el mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="4daab-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="4daab-429">Windows mágica</span><span class="sxs-lookup"><span data-stu-id="4daab-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="4daab-430">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="4daab-430">Key Concepts</span></span>

* <span data-ttu-id="4daab-431">Creación de vistas en un mundo oculto, es visualmente atractiva.</span><span class="sxs-lookup"><span data-stu-id="4daab-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="4daab-432">Mejore el realismo mediante la adición de efectos de audio cuando el usuario o un holograma es casi del mundo oculto.</span><span class="sxs-lookup"><span data-stu-id="4daab-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="4daab-433">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4daab-433">Instructions</span></span>

* <span data-ttu-id="4daab-434">En el **jerarquía** del panel, expanda **HologramCollection** y seleccione **Underword**.</span><span class="sxs-lookup"><span data-stu-id="4daab-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="4daab-435">Expanda **Underword** y seleccione **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="4daab-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="4daab-436">En el **Inspector** del panel, haga clic en **Agregar componente** y agregue **efecto de voz del usuario**.</span><span class="sxs-lookup"><span data-stu-id="4daab-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="4daab-437">Un **AudioSource** componente se agregará a **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="4daab-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="4daab-438">En **AudioSource**, establezca **salida** a **UserVoice (Mixer)**.</span><span class="sxs-lookup"><span data-stu-id="4daab-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="4daab-439">Compruebe el **Spatialize** casilla de verificación.</span><span class="sxs-lookup"><span data-stu-id="4daab-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="4daab-440">Arrastre el **Blend espacial** control deslizante hasta **3D**, o escriba **1** en el cuadro de edición.</span><span class="sxs-lookup"><span data-stu-id="4daab-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="4daab-441">Expanda **configuración de sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="4daab-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="4daab-442">Establecer **Doppler nivel** a **0**.</span><span class="sxs-lookup"><span data-stu-id="4daab-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="4daab-443">En **efecto de voz del usuario**, establezca **objeto primario** a la **Underword** desde la escena.</span><span class="sxs-lookup"><span data-stu-id="4daab-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="4daab-444">Establecer **distancia máxima** a **1**.</span><span class="sxs-lookup"><span data-stu-id="4daab-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="4daab-445">Establecer **distancia máxima** indica **efecto de voz del usuario** cómo cerrar el usuario debe ser para el objeto primario antes de que el efecto está habilitado.</span><span class="sxs-lookup"><span data-stu-id="4daab-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="4daab-446">En **efecto de voz del usuario**, expanda **coro parámetros**.</span><span class="sxs-lookup"><span data-stu-id="4daab-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="4daab-447">Establecer **profundidad** a **0,1**.</span><span class="sxs-lookup"><span data-stu-id="4daab-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="4daab-448">Establecer **pulse 1 volumen**, **pulse 2 volumen** y **pulse volumen 3** a **0.8**.</span><span class="sxs-lookup"><span data-stu-id="4daab-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="4daab-449">Establecer **volumen del sonido Original** a **0,5**.</span><span class="sxs-lookup"><span data-stu-id="4daab-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="4daab-450">La configuración anterior configura los parámetros de la unidad **AudioChorusFilter** usa para agregar la riqueza a la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="4daab-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="4daab-451">En **efecto de voz del usuario**, expanda **Echo parámetros**.</span><span class="sxs-lookup"><span data-stu-id="4daab-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="4daab-452">Establecer **retraso** a **300**</span><span class="sxs-lookup"><span data-stu-id="4daab-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="4daab-453">Establecer **decaer proporción** a **0.2**.</span><span class="sxs-lookup"><span data-stu-id="4daab-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="4daab-454">Establecer **volumen del sonido Original** a **0**.</span><span class="sxs-lookup"><span data-stu-id="4daab-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="4daab-455">La configuración anterior configura los parámetros de la unidad **AudioEchoFilter** usa para hacer que la voz del usuario se van a reflejar.</span><span class="sxs-lookup"><span data-stu-id="4daab-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="4daab-456">La secuencia de comandos de efecto de voz del usuario es responsable de:</span><span class="sxs-lookup"><span data-stu-id="4daab-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="4daab-457">Medir la distancia entre el usuario y la **GameObject** al que está adjunta la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="4daab-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="4daab-458">Determinar si el usuario es accesible desde el **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="4daab-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="4daab-459">El usuario debe ser accesible desde GameObject, independientemente de la distancia del efecto que se habilite.</span><span class="sxs-lookup"><span data-stu-id="4daab-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="4daab-460">Aplicar y configurar un **AudioChorusFilter** y un **AudioEchoFilter** a la **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="4daab-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="4daab-461">Deshabilitar el efecto de deshabilitar los filtros.</span><span class="sxs-lookup"><span data-stu-id="4daab-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="4daab-462">Efecto de voz del usuario utiliza el componente de Mic Stream Selector, desde el [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)para seleccionar la secuencia de voz de alta calidad y enrutarlo en el sistema de audio de Unity.</span><span class="sxs-lookup"><span data-stu-id="4daab-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="4daab-463">En el **jerarquía** panel, seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="4daab-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="4daab-464">En el **Inspector** del panel, expanda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="4daab-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="4daab-465">En **controlador de entrada de voz**, expanda **Underword mostrar**.</span><span class="sxs-lookup"><span data-stu-id="4daab-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="4daab-466">Cambio **ninguna función** a **UnderworldBase.OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="4daab-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![palabra clave: Mostrar Underword](images/showunderworld.png)

* <span data-ttu-id="4daab-468">Expanda **ocultar Underword**.</span><span class="sxs-lookup"><span data-stu-id="4daab-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="4daab-469">Cambio **ninguna función** a **UnderworldBase.OnDisable**.</span><span class="sxs-lookup"><span data-stu-id="4daab-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![palabra clave: Ocultar Underword](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="4daab-471">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="4daab-471">Build and Deploy</span></span>

* <span data-ttu-id="4daab-472">Como antes, compile el proyecto de Unity e implemente en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4daab-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="4daab-473">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="4daab-473">After the application is deployed:</span></span>

* <span data-ttu-id="4daab-474">Se enfrentan a una superficie (pared, floor, tabla) y say *"Mostrar Underword"*.</span><span class="sxs-lookup"><span data-stu-id="4daab-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="4daab-475">Se mostrará el Underword y todos los demás hologramas estará oculto.</span><span class="sxs-lookup"><span data-stu-id="4daab-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="4daab-476">Si no ve el Underword, asegúrese de que se enfrentan a una superficie del mundo real.</span><span class="sxs-lookup"><span data-stu-id="4daab-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="4daab-477">Enfoque de menos de 1 metro del holograma Underword y comience a hablar.</span><span class="sxs-lookup"><span data-stu-id="4daab-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="4daab-478">Ahora hay efectos de audio aplicados a su voz.</span><span class="sxs-lookup"><span data-stu-id="4daab-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="4daab-479">Aleje el Underword y observe cómo ya no se aplica el efecto.</span><span class="sxs-lookup"><span data-stu-id="4daab-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="4daab-480">Por ejemplo *"Ocultar Underword"* para ocultar el Underword.</span><span class="sxs-lookup"><span data-stu-id="4daab-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="4daab-481">Se ocultará el Underword y volverá a aparecer la hologramas estaban ocultos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4daab-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="4daab-482">Fin</span><span class="sxs-lookup"><span data-stu-id="4daab-482">The End</span></span>

<span data-ttu-id="4daab-483">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="4daab-483">Congratulations!</span></span> <span data-ttu-id="4daab-484">Ahora ha completado **220 espacial MR: Sonido espacial**.</span><span class="sxs-lookup"><span data-stu-id="4daab-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="4daab-485">Escuchar a todo el mundo y traiga sus experiencias cobren vida con sonido.</span><span class="sxs-lookup"><span data-stu-id="4daab-485">Listen to the world and bring your experiences to life with sound!</span></span>
