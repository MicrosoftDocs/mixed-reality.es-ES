---
title: MR espacial 220-sonido espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de sonido espacial.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, sonido espacial
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526908"
---
>[!NOTE]
><span data-ttu-id="8e07b-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="8e07b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8e07b-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8e07b-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8e07b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8e07b-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="8e07b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8e07b-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8e07b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8e07b-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="8e07b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="8e07b-110">MR espacial 220: Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="8e07b-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="8e07b-111">El [sonido espacial](spatial-sound.md) respire la vida en los hologramas y les da presencia en nuestro mundo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="8e07b-112">Los hologramas se componen de luz y sonido, y si se pierde la visión de los hologramas, el sonido espacial puede ayudarle a encontrarlos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="8e07b-113">El sonido espacial no es como el sonido típico que se oíría en la radio, sino que se encuentra en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="8e07b-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="8e07b-114">Con el sonido espacial, puede hacer que los hologramas suenen como si estuvieran detrás, junto a usted o incluso en su cabeza.</span><span class="sxs-lookup"><span data-stu-id="8e07b-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="8e07b-115">En este curso, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8e07b-115">In this course, you will:</span></span>

* <span data-ttu-id="8e07b-116">Configure el entorno de desarrollo para usar el sonido espacial de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8e07b-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="8e07b-117">Use el sonido espacial para mejorar las interacciones.</span><span class="sxs-lookup"><span data-stu-id="8e07b-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="8e07b-118">Use el sonido espacial junto con la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="8e07b-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="8e07b-119">Comprenda las prácticas recomendadas de diseño y mezcla.</span><span class="sxs-lookup"><span data-stu-id="8e07b-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="8e07b-120">Use el sonido para mejorar los efectos especiales y poner al usuario en el mundo de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="8e07b-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="8e07b-121">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="8e07b-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8e07b-122">Recurso</span><span class="sxs-lookup"><span data-stu-id="8e07b-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8e07b-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8e07b-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8e07b-124"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="8e07b-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8e07b-125">MR espacial 220: Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="8e07b-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="8e07b-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8e07b-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8e07b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8e07b-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8e07b-128">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="8e07b-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8e07b-129">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="8e07b-129">Prerequisites</span></span>

* <span data-ttu-id="8e07b-130">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.</span><span class="sxs-lookup"><span data-stu-id="8e07b-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="8e07b-131">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="8e07b-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="8e07b-132">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="8e07b-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="8e07b-133">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="8e07b-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="8e07b-134">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="8e07b-134">Project files</span></span>

* <span data-ttu-id="8e07b-135">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="8e07b-136"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="8e07b-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="8e07b-137">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="8e07b-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="8e07b-138">Es posible que esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="8e07b-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="8e07b-139">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="8e07b-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="8e07b-140"> Es posible que esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="8e07b-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="8e07b-141">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="8e07b-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="8e07b-142"> Es posible que esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="8e07b-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="8e07b-143">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="8e07b-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="8e07b-144">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="8e07b-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="8e07b-145">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="8e07b-145">Errata and Notes</span></span>

* <span data-ttu-id="8e07b-146">"Habilitar Solo mi código" debe estar deshabilitado *(* desactivado) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="8e07b-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="8e07b-147">Capítulo 1: configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="8e07b-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="8e07b-148">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8e07b-148">Objectives</span></span>

* <span data-ttu-id="8e07b-149">Cambie la configuración de sonido de Unity para usar el sonido espacial de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8e07b-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="8e07b-150">Agregue un sonido 3D a un objeto en Unity.</span><span class="sxs-lookup"><span data-stu-id="8e07b-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="8e07b-151">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-151">Instructions</span></span>

* <span data-ttu-id="8e07b-152">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="8e07b-152">Start Unity.</span></span>
* <span data-ttu-id="8e07b-153">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-153">Select **Open**.</span></span>
* <span data-ttu-id="8e07b-154">Navegue hasta el escritorio y busque la carpeta que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="8e07b-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="8e07b-155">Haga clic en la carpeta **Starting\Decibel** y, a continuación, presione el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="8e07b-156">Espere a que el proyecto se cargue en Unity.</span><span class="sxs-lookup"><span data-stu-id="8e07b-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="8e07b-157">En el panel **proyecto** , Abra **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="8e07b-158">En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="8e07b-159">En el inspector, expanda **AudioSource** y observe que no hay ninguna casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="8e07b-160">De forma predeterminada, Unity no carga un complemento de spatializer.</span><span class="sxs-lookup"><span data-stu-id="8e07b-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="8e07b-161">En los pasos siguientes se habilitará el sonido espacial en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="8e07b-162">En el menú superior de Unity, vaya a **editar > configuración del proyecto > audio**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="8e07b-163">Busque la lista desplegable **complemento de Spatializer** y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="8e07b-164">En el panel **jerarquía** , seleccione **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="8e07b-165">En el panel **Inspector** , busque el componente de **origen de audio** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="8e07b-166">Active la casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="8e07b-167">Arrastre el control deslizante de **combinación espacial** hasta el modo **3D**o escriba **1** en el cuadro de edición.</span><span class="sxs-lookup"><span data-stu-id="8e07b-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="8e07b-168">Ahora se compilará el proyecto en Unity y se configurará la solución en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="8e07b-169">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="8e07b-170">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="8e07b-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="8e07b-171">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="8e07b-172">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="8e07b-173">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="8e07b-174">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="8e07b-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="8e07b-175">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-175">Click **Build**.</span></span>
7. <span data-ttu-id="8e07b-176">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="8e07b-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="8e07b-177">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="8e07b-178">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-178">Press **Select Folder**.</span></span>

<span data-ttu-id="8e07b-179">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="8e07b-180">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="8e07b-181">Abra la **solución de Visual Studio**de decibelios.</span><span class="sxs-lookup"><span data-stu-id="8e07b-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="8e07b-182">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="8e07b-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="8e07b-183">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="8e07b-184">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="8e07b-185">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="8e07b-186">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-186">Click **Select**.</span></span> <span data-ttu-id="8e07b-187">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="8e07b-188">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="8e07b-189">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span><span class="sxs-lookup"><span data-stu-id="8e07b-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="8e07b-190">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="8e07b-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="8e07b-191">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="8e07b-192">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="8e07b-193">En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="8e07b-194">Capítulo 2: sonido espacial e interacción</span><span class="sxs-lookup"><span data-stu-id="8e07b-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="8e07b-195">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8e07b-195">Objectives</span></span>

* <span data-ttu-id="8e07b-196">Mejore el realismo del holograma mediante el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="8e07b-197">Dirija la mirada del usuario con el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="8e07b-198">Proporcione comentarios de gestos mediante sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="8e07b-199">Parte 1: mejora del realismo</span><span class="sxs-lookup"><span data-stu-id="8e07b-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-200">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-200">Key Concepts</span></span>

* <span data-ttu-id="8e07b-201">Spatial los sonidos del holograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="8e07b-202">Los orígenes de sonido se deben colocar en una ubicación adecuada en el holograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="8e07b-203">La ubicación adecuada para el sonido dependerá del holograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="8e07b-204">Por ejemplo, si el holograma es humano, el origen de sonido debe estar situado cerca de la boca y no de los pies.</span><span class="sxs-lookup"><span data-stu-id="8e07b-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e07b-205">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-205">Instructions</span></span>

<span data-ttu-id="8e07b-206">Las instrucciones siguientes conectarán un sonido espacial a un holograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="8e07b-207">En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="8e07b-208">En el panel **Inspector** , en el **AudioSource**, haga clic en el círculo situado junto a **AudioClip** y seleccione el subdesplazamiento en el elemento emergente.</span><span class="sxs-lookup"><span data-stu-id="8e07b-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="8e07b-209">Haga clic en el círculo situado junto a **salida** y seleccione **SoundEffects** en el elemento emergente.</span><span class="sxs-lookup"><span data-stu-id="8e07b-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="8e07b-210">El proyecto de decibelios usa un componente **AudioMixer** de Unity para habilitar el ajuste de los niveles de sonido para grupos de sonidos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="8e07b-211">Al agrupar los sonidos de esta manera, se puede ajustar el volumen global mientras se mantiene el volumen relativo de cada sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="8e07b-212">En **AudioSource**, expanda **configuración de sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="8e07b-213">Establezca el **nivel de Doppler** en **0**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="8e07b-214">Si se establece el nivel de Doppler en cero, se deshabilitan los cambios de tono causados por el movimiento (el holograma o el usuario).</span><span class="sxs-lookup"><span data-stu-id="8e07b-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="8e07b-215">Un ejemplo clásico de Doppler es un coche con movimiento rápido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="8e07b-216">A medida que el coche se aproxima a un agente de escucha estacionario, aumenta el tono del motor.</span><span class="sxs-lookup"><span data-stu-id="8e07b-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="8e07b-217">Cuando pasa el agente de escucha, el paso disminuye con la distancia.</span><span class="sxs-lookup"><span data-stu-id="8e07b-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="8e07b-218">Parte 2: dirigir la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="8e07b-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-219">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-219">Key Concepts</span></span>

* <span data-ttu-id="8e07b-220">Use el sonido para llamar la atención a los hologramas importantes.</span><span class="sxs-lookup"><span data-stu-id="8e07b-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="8e07b-221">Los oídos le ayudarán a tener el aspecto de los ojos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="8e07b-222">El cerebro tiene algunas expectativas conocidas.</span><span class="sxs-lookup"><span data-stu-id="8e07b-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="8e07b-223">Un ejemplo de expectativas aprendidas es que las aves suelen estar por encima de los cabezales de los seres humanos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="8e07b-224">Si un usuario oye un sonido de pájaro, su reacción inicial es buscar.</span><span class="sxs-lookup"><span data-stu-id="8e07b-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="8e07b-225">Colocar un pájaro debajo del usuario puede conducir a que se dirija a la dirección correcta del sonido, pero no puede encontrar el holograma en función de la expectativa de necesidad de buscar.</span><span class="sxs-lookup"><span data-stu-id="8e07b-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e07b-226">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-226">Instructions</span></span>

<span data-ttu-id="8e07b-227">Las instrucciones siguientes permiten que P0LY se oculte por detrás, de modo que pueda usar el sonido para buscar el holograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="8e07b-228">En el panel **jerarquía** , seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="8e07b-229">En el panel **Inspector** , busque **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="8e07b-230">En **controlador de entrada de voz**, expanda **ocultar**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="8e07b-231">**No cambie ninguna función** a poliactions **. GoHide**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Palabra clave Ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="8e07b-233">Parte 3: comentarios de gestos</span><span class="sxs-lookup"><span data-stu-id="8e07b-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-234">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-234">Key Concepts</span></span>

* <span data-ttu-id="8e07b-235">Proporcionar al usuario la confirmación de gestos positivos mediante el sonido</span><span class="sxs-lookup"><span data-stu-id="8e07b-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="8e07b-236">No sobrecargar el exceso de sonido del usuario en el camino</span><span class="sxs-lookup"><span data-stu-id="8e07b-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="8e07b-237">Los sonidos sutiles funcionan mejor: no hagan la experiencia</span><span class="sxs-lookup"><span data-stu-id="8e07b-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e07b-238">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-238">Instructions</span></span>

* <span data-ttu-id="8e07b-239">En el panel **jerarquía** , expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8e07b-240">Expanda **EnergyHub** y seleccione **base**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="8e07b-241">En el panel **Inspector** , haga clic en **Agregar componente** y agregue el **controlador de sonido de gesto**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="8e07b-242">En **el controlador de sonido**de gestos, haga clic en el círculo situado junto a **navegación Inicio clip** y **navegación actualizado clip** y seleccione **RotateClick** en el elemento emergente para ambos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="8e07b-243">Haga doble clic en "GestureSoundHandler" para cargar en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="8e07b-244">El controlador de sonido de gestos realiza las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="8e07b-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="8e07b-245">Cree y configure un **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="8e07b-246">Coloque **AudioSource** en la ubicación de la **GameObject**adecuada.</span><span class="sxs-lookup"><span data-stu-id="8e07b-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="8e07b-247">Reproduce el **AudioClip** asociado con el gesto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="8e07b-248">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8e07b-248">Build and Deploy</span></span>

1. <span data-ttu-id="8e07b-249">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="8e07b-250">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-250">Click **Build**.</span></span>
3. <span data-ttu-id="8e07b-251">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="8e07b-252">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-252">Press **Select Folder**.</span></span>

<span data-ttu-id="8e07b-253">Compruebe que la barra de herramientas indica "release", "x86" o "x64" y "dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="8e07b-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="8e07b-254">Si no es así, se trata de la instancia de codificación de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="8e07b-255">Es posible que tenga que volver a abrir la solución desde la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8e07b-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="8e07b-256">Si se le solicita, vuelva a cargar los archivos de proyecto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="8e07b-257">Como antes, implemente desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="8e07b-258">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="8e07b-258">After the application is deployed:</span></span>

* <span data-ttu-id="8e07b-259">Observe cómo cambia el sonido a medida que se desplaza por P0LY.</span><span class="sxs-lookup"><span data-stu-id="8e07b-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="8e07b-260">Di *"ir a ocultar"* para que P0LY se mueva a una ubicación detrás.</span><span class="sxs-lookup"><span data-stu-id="8e07b-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="8e07b-261">Lo encuentra en el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-261">Find it by the sound.</span></span>
* <span data-ttu-id="8e07b-262">Mira la base de la central de energía.</span><span class="sxs-lookup"><span data-stu-id="8e07b-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="8e07b-263">Puntee y arrastre hacia la izquierda o hacia la derecha para girar el holograma y observe cómo el sonido que hace clic confirma el gesto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="8e07b-264">Nota: Hay un panel de texto que le etiquetará junto con usted.</span><span class="sxs-lookup"><span data-stu-id="8e07b-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="8e07b-265">Esto contendrá los comandos de voz disponibles que puede usar en este curso.</span><span class="sxs-lookup"><span data-stu-id="8e07b-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="8e07b-266">Capítulo 3: mapa espacial y de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="8e07b-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="8e07b-267">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8e07b-267">Objectives</span></span>

* <span data-ttu-id="8e07b-268">Confirme la interacción entre los hologramas y el mundo real mediante el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="8e07b-269">Tapaba sonido con el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="8e07b-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="8e07b-270">Parte 1: interacción del mundo físico</span><span class="sxs-lookup"><span data-stu-id="8e07b-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-271">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-271">Key Concepts</span></span>

* <span data-ttu-id="8e07b-272">Normalmente, los objetos físicos realizan un sonido al encontrar una superficie u otro objeto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="8e07b-273">Los sonidos deben ser el contexto adecuado dentro de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="8e07b-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="8e07b-274">Por ejemplo, el establecimiento de una copa en una tabla debe hacer un sonido más silencioso que colocar un Boulder en una pieza de metal.</span><span class="sxs-lookup"><span data-stu-id="8e07b-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e07b-275">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-275">Instructions</span></span>

* <span data-ttu-id="8e07b-276">En el panel **jerarquía** , expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8e07b-277">Expanda **EnergyHub**y seleccione **base**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="8e07b-278">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **puntear para colocar con el sonido y la acción**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="8e07b-279">En **puntear para colocar con el sonido y la acción**:</span><span class="sxs-lookup"><span data-stu-id="8e07b-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="8e07b-280">Active **colocar primario al pulsar**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="8e07b-281">Establezca el sonido de  **selección de ubicación** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="8e07b-282">Establezca **sonido de recogida** en **recogida**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="8e07b-283">Presione + en la parte inferior derecha, en la acción **de recogida** y **en la acción de selección de ubicación**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="8e07b-284">Arrastre EnergyHub desde la escena hasta los campos **ninguno (objeto)** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="8e07b-285">En **acción de recogida**, haga clic en **ninguna función** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="8e07b-286">En **acción de selección de ubicación**, haga clic en **ninguna función** -> **EnergyHubBase** -> **alseleccionar**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Puntee para colocar con el sonido y la acción](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="8e07b-288">Parte 2: oclusión de sonido</span><span class="sxs-lookup"><span data-stu-id="8e07b-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-289">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-289">Key Concepts</span></span>

* <span data-ttu-id="8e07b-290">El sonido, como Light, puede ser ocluidos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="8e07b-291">Un ejemplo clásico es un salón de concierto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-291">A classic example is a concert hall.</span></span> <span data-ttu-id="8e07b-292">Cuando un agente de escucha está fuera del salón y la puerta está cerrada, la música suena silenciada.</span><span class="sxs-lookup"><span data-stu-id="8e07b-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="8e07b-293">Normalmente, también hay una reducción del volumen.</span><span class="sxs-lookup"><span data-stu-id="8e07b-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="8e07b-294">Cuando se abre la puerta, se oye todo el espectro del sonido en el volumen real.</span><span class="sxs-lookup"><span data-stu-id="8e07b-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="8e07b-295">Los sonidos de alta frecuencia suelen absorber más que las bajas frecuencias.</span><span class="sxs-lookup"><span data-stu-id="8e07b-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e07b-296">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-296">Instructions</span></span>

* <span data-ttu-id="8e07b-297">En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="8e07b-298">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **emisor de audio**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="8e07b-299">La clase emisora de audio proporciona las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="8e07b-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="8e07b-300">Restaura cualquier cambio realizado en el volumen de **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="8e07b-301">Realiza una conexión **física. RaycastNonAlloc** desde la posición del usuario en la dirección del **GameObject** al que se adjunta el **AudioEmitter** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="8e07b-302">El método RaycastNonAlloc se usa como optimización del rendimiento para limitar las asignaciones y el número de resultados devueltos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="8e07b-303">Para cada **IAudioInfluencer** encontrada, llama al método **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="8e07b-304">Para cada **IAudioInfluencer** anterior que ya no se encuentre, llame al método **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="8e07b-305">Tenga en cuenta que AudioEmitter se actualiza en las escalas de tiempo humano, en lugar de en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="8e07b-306">Esto se hace porque los seres humanos generalmente no se mueven lo suficientemente rápido como para que el efecto tenga que actualizarse con más frecuencia que cada trimestre o mitad de segundo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="8e07b-307">Los hologramas que se destransportan rápidamente de una ubicación a otra pueden interrumpir el efecto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="8e07b-308">En el panel **jerarquía** , expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8e07b-309">Expanda **EnergyHub** y seleccione **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="8e07b-310">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="8e07b-311">En **audio Occluder**, establezca la **frecuencia límite** en **1500**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="8e07b-312">Esta configuración limita las frecuencias AudioSource a 1500 Hz y por debajo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="8e07b-313">Establezca el **paso de volumen** en **0,9**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="8e07b-314">Esta configuración reduce el volumen de AudioSource al 90% del nivel actual.</span><span class="sxs-lookup"><span data-stu-id="8e07b-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="8e07b-315">Audio Occluder implementa IAudioInfluencer para:</span><span class="sxs-lookup"><span data-stu-id="8e07b-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="8e07b-316">Aplicar un efecto de oclusión mediante un **AudioLowPassFilter** que se adjunta a la **AudioSource** administrada compre el **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="8e07b-317">Aplica la atenuación del volumen a AudioSource.</span><span class="sxs-lookup"><span data-stu-id="8e07b-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="8e07b-318">Deshabilita el efecto estableciendo una frecuencia de límite neutro y deshabilitando el filtro.</span><span class="sxs-lookup"><span data-stu-id="8e07b-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="8e07b-319">La frecuencia usada como neutra es de 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="8e07b-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="8e07b-320">Esta frecuencia se eligió debido a que está por encima de la frecuencia máxima nominal que puede ser oída por el oído humano, lo que no hace ningún impacto más perceptible en el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="8e07b-321">En el panel **jerarquía** , seleccione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="8e07b-322">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="8e07b-323">En **audio Occluder**, establezca la **frecuencia límite** en **750**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="8e07b-324">Cuando hay varios occluders en la ruta de acceso entre el usuario y el **AudioEmitter**, se aplica la frecuencia más baja al filtro.</span><span class="sxs-lookup"><span data-stu-id="8e07b-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="8e07b-325">Establezca el **paso de volumen** en **0,75**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="8e07b-326">Cuando hay varios occluders en la ruta de acceso entre el usuario y el **AudioEmitter**, el paso del volumen a través se aplica de forma aditiva.</span><span class="sxs-lookup"><span data-stu-id="8e07b-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="8e07b-327">En el panel **jerarquía** , seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="8e07b-328">En el panel **Inspector** , expanda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="8e07b-329">En **controlador de entrada de voz**, expanda **gastos de avance**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="8e07b-330">**No cambie ninguna función** a poliactions **. GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Palabra clave Gastos de avance](images/gocharge.png)

* <span data-ttu-id="8e07b-332">Amplíe **aquí**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="8e07b-333">**No cambie ninguna función** a poliactions **. Comeback**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Palabra clave Ven](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="8e07b-335">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8e07b-335">Build and Deploy</span></span>

* <span data-ttu-id="8e07b-336">Como antes, compile el proyecto en Unity e impleméntelo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="8e07b-337">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="8e07b-337">After the application is deployed:</span></span>

* <span data-ttu-id="8e07b-338">Por ejemplo, *"go CHARGE"* para que P0LY escriba el centro de energía.</span><span class="sxs-lookup"><span data-stu-id="8e07b-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="8e07b-339">Observe el cambio en el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-339">Note the change in the sound.</span></span> <span data-ttu-id="8e07b-340">Debe sonar silenciado y un poco más silencioso.</span><span class="sxs-lookup"><span data-stu-id="8e07b-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="8e07b-341">Si puede colocarse con una pared u otro objeto entre usted y el centro de energía, debe observar un mayor silenciamiento del sonido debido a la oclusión del mundo real.</span><span class="sxs-lookup"><span data-stu-id="8e07b-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="8e07b-342">Supongamos que *"viene aquí"* para que P0LY deje la central de energía y se coloque por delante.</span><span class="sxs-lookup"><span data-stu-id="8e07b-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="8e07b-343">Tenga en cuenta que la oclusión de sonido se quita una vez que P0LY sale del centro de energía.</span><span class="sxs-lookup"><span data-stu-id="8e07b-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="8e07b-344">Si todavía está escuchando oclusión, P0LY puede ser ocluidos en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="8e07b-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="8e07b-345">Intente cambiar para asegurarse de que tiene una línea de visión clara a P0LY.</span><span class="sxs-lookup"><span data-stu-id="8e07b-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="8e07b-346">Parte 3: modelos Room</span><span class="sxs-lookup"><span data-stu-id="8e07b-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-347">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-347">Key Concepts</span></span>

* <span data-ttu-id="8e07b-348">El tamaño del espacio proporciona colas de subliminal que contribuyen a la localización de sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="8e07b-349">Los modelos de sala se establecen por**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="8e07b-350">[MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona código para establecer el modelo de habitación.</span><span class="sxs-lookup"><span data-stu-id="8e07b-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="8e07b-351">En el caso de experiencias de realidad mixta, seleccione el modelo de salón que mejor se adapte al espacio real del mundo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="8e07b-352">Si va a crear un escenario de realidad virtual, seleccione el modelo de salón que mejor se adapte al entorno virtual.</span><span class="sxs-lookup"><span data-stu-id="8e07b-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="8e07b-353">Capítulo 4: diseño de sonido</span><span class="sxs-lookup"><span data-stu-id="8e07b-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="8e07b-354">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8e07b-354">Objectives</span></span>

* <span data-ttu-id="8e07b-355">Comprender las consideraciones para un diseño de sonido eficaz.</span><span class="sxs-lookup"><span data-stu-id="8e07b-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="8e07b-356">Obtenga información sobre las técnicas y las directrices de combinación.</span><span class="sxs-lookup"><span data-stu-id="8e07b-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="8e07b-357">Parte 1: diseño de la experiencia y el sonido</span><span class="sxs-lookup"><span data-stu-id="8e07b-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="8e07b-358">En esta sección se describen las consideraciones y directrices de diseño de la experiencia y el sonido clave.</span><span class="sxs-lookup"><span data-stu-id="8e07b-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="8e07b-359">Normalizar todos los sonidos</span><span class="sxs-lookup"><span data-stu-id="8e07b-359">Normalize all sounds</span></span>

<span data-ttu-id="8e07b-360">Esto evita la necesidad de que el código de caso especial ajuste los niveles de volumen por sonido, lo que puede llevar mucho tiempo y limita la capacidad de actualizar fácilmente los archivos de sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="8e07b-361">Diseño para una experiencia de untethered</span><span class="sxs-lookup"><span data-stu-id="8e07b-361">Design for an untethered experience</span></span>

<span data-ttu-id="8e07b-362">HoloLens es un equipo untethered Holographic totalmente contenido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="8e07b-363">Los usuarios pueden usar sus experiencias mientras se mueven.</span><span class="sxs-lookup"><span data-stu-id="8e07b-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="8e07b-364">Asegúrese de probar la combinación de audio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="8e07b-365">Emitir sonido desde ubicaciones lógicas en los hologramas</span><span class="sxs-lookup"><span data-stu-id="8e07b-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="8e07b-366">En el mundo real, un perro no se corteza de su cola y la voz de un hombre no proviene de sus pies.</span><span class="sxs-lookup"><span data-stu-id="8e07b-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="8e07b-367">Evite que los sonidos se emitan desde partes inesperadas de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="8e07b-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="8e07b-368">En el caso de los hologramas pequeños, es razonable tener una emisión de sonido desde el centro de la geometría.</span><span class="sxs-lookup"><span data-stu-id="8e07b-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="8e07b-369">Los sonidos conocidos son más localizables</span><span class="sxs-lookup"><span data-stu-id="8e07b-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="8e07b-370">La voz humana y la música son muy fáciles de localizar.</span><span class="sxs-lookup"><span data-stu-id="8e07b-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="8e07b-371">Si alguien llama a su nombre, puede determinar con precisión desde qué dirección se ha recibido la voz y desde dónde está.</span><span class="sxs-lookup"><span data-stu-id="8e07b-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="8e07b-372">Los sonidos cortos y desconocidos son más difíciles de localizar.</span><span class="sxs-lookup"><span data-stu-id="8e07b-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="8e07b-373">Cognizant de las expectativas de los usuarios</span><span class="sxs-lookup"><span data-stu-id="8e07b-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="8e07b-374">La experiencia de vida juega una parte en nuestra capacidad de identificar la ubicación de un sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="8e07b-375">Esta es una de las razones por las que la voz humana es especialmente fácil de localizar.</span><span class="sxs-lookup"><span data-stu-id="8e07b-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="8e07b-376">Es importante tener en cuenta las expectativas aprendidas del usuario al colocar los sonidos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="8e07b-377">Por ejemplo, cuando alguien oye una canción de pájaro, se suele buscar, ya que las aves tienden a estar por encima de la línea de visión (vuelo o en un árbol).</span><span class="sxs-lookup"><span data-stu-id="8e07b-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="8e07b-378">No es raro que un usuario Active la dirección correcta de un sonido, sino que mire en la dirección vertical equivocada y se confunda o frustraría cuando no pueda encontrar el holograma.</span><span class="sxs-lookup"><span data-stu-id="8e07b-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="8e07b-379">Evitar emisores ocultos</span><span class="sxs-lookup"><span data-stu-id="8e07b-379">Avoid hidden emitters</span></span>

<span data-ttu-id="8e07b-380">En el mundo real, si escuchamos un sonido, generalmente podemos identificar el objeto que emite el sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="8e07b-381">También debe tener el valor true en sus experiencias.</span><span class="sxs-lookup"><span data-stu-id="8e07b-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="8e07b-382">Puede ser muy difícil para los usuarios oír un sonido, saber desde dónde se origina el sonido y no puede ver un objeto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="8e07b-383">Existen algunas excepciones a esta directriz.</span><span class="sxs-lookup"><span data-stu-id="8e07b-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="8e07b-384">Por ejemplo, los sonidos ambientales como Crickets en un campo no deben ser visibles.</span><span class="sxs-lookup"><span data-stu-id="8e07b-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="8e07b-385">La experiencia de vida nos permite familiarizarse con el origen de estos sonidos sin necesidad de verlo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="8e07b-386">Parte 2: combinación de sonidos</span><span class="sxs-lookup"><span data-stu-id="8e07b-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="8e07b-387">Destine su combinación para el volumen del 70% en HoloLens</span><span class="sxs-lookup"><span data-stu-id="8e07b-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="8e07b-388">Las experiencias de realidad mixta permiten que los hologramas se vean en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="8e07b-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="8e07b-389">También deben permitir escuchar sonidos reales.</span><span class="sxs-lookup"><span data-stu-id="8e07b-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="8e07b-390">Un destino de volumen del 70% permite al usuario oír todo el mundo junto con el sonido de su experiencia.</span><span class="sxs-lookup"><span data-stu-id="8e07b-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="8e07b-391">HoloLens en 100% de volumen debe estar ahogado a los sonidos externos</span><span class="sxs-lookup"><span data-stu-id="8e07b-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="8e07b-392">Un nivel de volumen del 100% es similar a una experiencia de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="8e07b-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="8e07b-393">Visualmente, el usuario se transporta a un mundo diferente.</span><span class="sxs-lookup"><span data-stu-id="8e07b-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="8e07b-394">Lo mismo debe ser un verdadero audible.</span><span class="sxs-lookup"><span data-stu-id="8e07b-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="8e07b-395">Usar el AudioMixer de Unity para ajustar categorías de sonidos</span><span class="sxs-lookup"><span data-stu-id="8e07b-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="8e07b-396">Al diseñar la combinación, a menudo resulta útil crear categorías de sonido y tener la capacidad de aumentar o disminuir el volumen como una unidad.</span><span class="sxs-lookup"><span data-stu-id="8e07b-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="8e07b-397">De este modo, se conservan los niveles relativos de cada sonido a la vez que se habilitan los cambios rápidos y sencillos en la combinación global.</span><span class="sxs-lookup"><span data-stu-id="8e07b-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="8e07b-398">Entre las categorías comunes se incluyen: efectos sonoros, ambiente, voz y música de fondo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="8e07b-399">Mezcle los sonidos en función de la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="8e07b-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="8e07b-400">A menudo, puede resultar útil cambiar la combinación de sonidos de su experiencia en función de la ubicación de un usuario (o no).</span><span class="sxs-lookup"><span data-stu-id="8e07b-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="8e07b-401">Un uso común de esta técnica consiste en reducir el nivel de volumen de los hologramas que están fuera del marco holográfica para que el usuario pueda centrarse más fácilmente en la información que se encuentra delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="8e07b-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="8e07b-402">Otro uso es aumentar el volumen de un sonido para atraer la atención del usuario a un evento importante.</span><span class="sxs-lookup"><span data-stu-id="8e07b-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="8e07b-403">Crear la combinación</span><span class="sxs-lookup"><span data-stu-id="8e07b-403">Building your mix</span></span>

<span data-ttu-id="8e07b-404">Al compilar la combinación, se recomienda empezar con el audio de fondo de la experiencia y agregar capas basadas en importancia.</span><span class="sxs-lookup"><span data-stu-id="8e07b-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="8e07b-405">A menudo, esto da lugar a que cada capa sea más fuerte que la anterior.</span><span class="sxs-lookup"><span data-stu-id="8e07b-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="8e07b-406">Al imaginarse la combinación como un embudo invertido, con el menos importante (y los sonidos generalmente más silencioso) en la parte inferior, se recomienda estructurar la combinación similar al siguiente diagrama.</span><span class="sxs-lookup"><span data-stu-id="8e07b-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Estructura de combinación de sonidos](images/soundlevels.png)

<span data-ttu-id="8e07b-408">La voz es un escenario interesante.</span><span class="sxs-lookup"><span data-stu-id="8e07b-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="8e07b-409">En función de la experiencia que cree, puede que desee tener un sonido estéreo (no localizado) o crear un espacial de la voz.</span><span class="sxs-lookup"><span data-stu-id="8e07b-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="8e07b-410">Dos experiencias publicadas de Microsoft muestran excelentes ejemplos de cada escenario.</span><span class="sxs-lookup"><span data-stu-id="8e07b-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="8e07b-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voz de estéreo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="8e07b-412">Cuando el narrador describe la ubicación que se está viendo, el sonido es coherente y no varía en función de la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="8e07b-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="8e07b-413">Esto permite al narrador describir la escena sin tener que alejarse de los sonidos espaciales del entorno.</span><span class="sxs-lookup"><span data-stu-id="8e07b-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="8e07b-414">[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) emplea una voz espacial en forma de un detective.</span><span class="sxs-lookup"><span data-stu-id="8e07b-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="8e07b-415">La voz del detective se usa para ayudar a la atención del usuario a una pista importante como si hubiera un hombre real en el salón.</span><span class="sxs-lookup"><span data-stu-id="8e07b-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="8e07b-416">Esto permite una mayor sensación de inmersión en la experiencia de resolución del misterio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="8e07b-417">Parte 3: rendimiento</span><span class="sxs-lookup"><span data-stu-id="8e07b-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="8e07b-418">Uso de CPU</span><span class="sxs-lookup"><span data-stu-id="8e07b-418">CPU usage</span></span>

<span data-ttu-id="8e07b-419">Cuando se usa el sonido espacial, 10-12 emisores consumirán aproximadamente el 12% de la CPU.</span><span class="sxs-lookup"><span data-stu-id="8e07b-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="8e07b-420">Transmitir archivos de audio largos</span><span class="sxs-lookup"><span data-stu-id="8e07b-420">Stream long audio files</span></span>

<span data-ttu-id="8e07b-421">Los datos de audio pueden ser grandes, sobre todo en las tarifas de ejemplo comunes (44,1 y 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="8e07b-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="8e07b-422">Una regla general es que los archivos de audio de más de 5-10 segundos se deben transmitir para reducir el uso de memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8e07b-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="8e07b-423">En Unity, puede marcar un archivo de audio para el streaming en la configuración de importación del archivo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Configuración de importación de audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="8e07b-425">Capítulo 5: efectos especiales</span><span class="sxs-lookup"><span data-stu-id="8e07b-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="8e07b-426">Objetivos</span><span class="sxs-lookup"><span data-stu-id="8e07b-426">Objectives</span></span>

* <span data-ttu-id="8e07b-427">Agregue profundidad a "Magic Windows".</span><span class="sxs-lookup"><span data-stu-id="8e07b-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="8e07b-428">Traslade al usuario al mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="8e07b-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="8e07b-429">Ventanas mágicas</span><span class="sxs-lookup"><span data-stu-id="8e07b-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="8e07b-430">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="8e07b-430">Key Concepts</span></span>

* <span data-ttu-id="8e07b-431">La creación de vistas en un mundo oculto es visualmente atractiva.</span><span class="sxs-lookup"><span data-stu-id="8e07b-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="8e07b-432">Mejore el realismo agregando efectos de audio cuando un holograma o el usuario están cerca del mundo oculto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="8e07b-433">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="8e07b-433">Instructions</span></span>

* <span data-ttu-id="8e07b-434">En el panel **jerarquía** , expanda **HologramCollection** y seleccione el submundo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="8e07b-435">Expanda el **submundo** y seleccione **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="8e07b-436">En el panel **Inspector** , haga clic en **Agregar componente** y agregar **efecto de voz de usuario**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="8e07b-437">Se agregará un componente **AudioSource** a **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="8e07b-438">En **AudioSource**, establezca **salida** en **UserVoice (Mixer)** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="8e07b-439">Active la casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="8e07b-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="8e07b-440">Arrastre el control deslizante de **combinación espacial** hasta el modo **3D**o escriba **1** en el cuadro de edición.</span><span class="sxs-lookup"><span data-stu-id="8e07b-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="8e07b-441">Expanda **configuración de sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="8e07b-442">Establezca el **nivel de Doppler** en **0**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="8e07b-443">En **efecto de voz de usuario**, establezca **objeto primario** en el **mundo** de la escena.</span><span class="sxs-lookup"><span data-stu-id="8e07b-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="8e07b-444">Establezca la **distancia máxima** en **1**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="8e07b-445">El establecimiento de la **distancia máxima** indica al **usuario el efecto** de la forma en que el usuario debe estar al objeto primario antes de que se habilite el efecto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="8e07b-446">En **efecto de voz de usuario**, expanda **los parámetros de coro**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="8e07b-447">Establezca **profundidad** en **0,1**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="8e07b-448">Establezca **TAP 1 Volume**, **Pulse 2 Volume** y **Pulse 3 Volume** hasta **0,8**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="8e07b-449">Establezca el **volumen de sonido original** en **0,5**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="8e07b-450">La configuración anterior configura los parámetros del **AudioChorusFilter** de Unity que se usa para agregar riqueza a la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="8e07b-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="8e07b-451">En **efecto de voz de usuario**, expanda **parámetros de eco**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="8e07b-452">Establecer **retraso** en **300**</span><span class="sxs-lookup"><span data-stu-id="8e07b-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="8e07b-453">Establezca la **relación** de decadencia en **0,2**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="8e07b-454">Establezca el **volumen de sonido original** en **0**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="8e07b-455">La configuración anterior configura los parámetros del **AudioEchoFilter** de Unity que se usa para hacer que la voz del usuario se repita.</span><span class="sxs-lookup"><span data-stu-id="8e07b-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="8e07b-456">El script de efecto de la voz de usuario es responsable de:</span><span class="sxs-lookup"><span data-stu-id="8e07b-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="8e07b-457">Medir la distancia entre el usuario y el **GameObject** al que se adjunta el script.</span><span class="sxs-lookup"><span data-stu-id="8e07b-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="8e07b-458">Determinar si el usuario está orientado o no al **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="8e07b-459">El usuario debe estar orientado a GameObject, independientemente de la distancia, para que el efecto se habilite.</span><span class="sxs-lookup"><span data-stu-id="8e07b-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="8e07b-460">Aplicar y configurar **AudioChorusFilter** y **AudioEchoFilter** en **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="8e07b-461">Deshabilitar el efecto deshabilitando los filtros.</span><span class="sxs-lookup"><span data-stu-id="8e07b-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="8e07b-462">Efecto de voz de usuario usa el componente selector de flujo de MIC, de [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), para seleccionar el flujo de voz de alta calidad y enrutarlo al sistema de audio de Unity.</span><span class="sxs-lookup"><span data-stu-id="8e07b-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="8e07b-463">En el panel **jerarquía** , seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="8e07b-464">En el panel **Inspector** , expanda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="8e07b-465">En **controlador de entrada de voz**, expanda **Mostrar**el submundo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="8e07b-466">No cambie la **función** a **UnderworldBase. alhabilitar**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Palabra clave Mostrar el submundo](images/showunderworld.png)

* <span data-ttu-id="8e07b-468">Expanda **ocultar submundo**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="8e07b-469">No cambie la **función** a **UnderworldBase. deshabilito**.</span><span class="sxs-lookup"><span data-stu-id="8e07b-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Palabra clave Ocultar submundo](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="8e07b-471">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="8e07b-471">Build and Deploy</span></span>

* <span data-ttu-id="8e07b-472">Como antes, compile el proyecto en Unity e impleméntelo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e07b-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="8e07b-473">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="8e07b-473">After the application is deployed:</span></span>

* <span data-ttu-id="8e07b-474">Cara a una superficie (pared, piso, tabla) y decir *"Mostrar el mundo"* .</span><span class="sxs-lookup"><span data-stu-id="8e07b-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="8e07b-475">Se mostrará el submundo y se ocultarán todos los demás hologramas.</span><span class="sxs-lookup"><span data-stu-id="8e07b-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="8e07b-476">Si no ve el mundo, asegúrese de que se enfrenta a una superficie real.</span><span class="sxs-lookup"><span data-stu-id="8e07b-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="8e07b-477">Enfoque dentro de 1 medidor del holograma de submundo y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="8e07b-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="8e07b-478">Ahora hay efectos de audio aplicados a la voz.</span><span class="sxs-lookup"><span data-stu-id="8e07b-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="8e07b-479">Desactive el mundo y observe cómo ya no se aplica el efecto.</span><span class="sxs-lookup"><span data-stu-id="8e07b-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="8e07b-480">*"Oculte el mundo"* para ocultar el mundo.</span><span class="sxs-lookup"><span data-stu-id="8e07b-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="8e07b-481">El mundo se ocultará y los hologramas previamente ocultos volverán a aparecer.</span><span class="sxs-lookup"><span data-stu-id="8e07b-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="8e07b-482">Fin</span><span class="sxs-lookup"><span data-stu-id="8e07b-482">The End</span></span>

<span data-ttu-id="8e07b-483">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="8e07b-483">Congratulations!</span></span> <span data-ttu-id="8e07b-484">Ahora ha completado **el Mr espacial 220: Sonido**espacial.</span><span class="sxs-lookup"><span data-stu-id="8e07b-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="8e07b-485">Escuche el mundo y llévese sus experiencias con sonido.</span><span class="sxs-lookup"><span data-stu-id="8e07b-485">Listen to the world and bring your experiences to life with sound!</span></span>
