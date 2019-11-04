---
title: MR espacial 220-sonido espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de sonido espacial.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, sonido espacial
ms.openlocfilehash: a3fc054927d73cf9ac21f831caa4ec23875977bd
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434724"
---
>[!NOTE]
><span data-ttu-id="90e92-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="90e92-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="90e92-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="90e92-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="90e92-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="90e92-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="90e92-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="90e92-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="90e92-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="90e92-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="90e92-109">MR espacial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="90e92-109">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="90e92-110">El [sonido espacial](spatial-sound.md) respire la vida en los hologramas y les da presencia en nuestro mundo.</span><span class="sxs-lookup"><span data-stu-id="90e92-110">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="90e92-111">Los hologramas se componen de luz y sonido, y si se pierde la visión de los hologramas, el sonido espacial puede ayudarle a encontrarlos.</span><span class="sxs-lookup"><span data-stu-id="90e92-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="90e92-112">El sonido espacial no es como el sonido típico que se oíría en la radio, sino que se encuentra en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="90e92-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="90e92-113">Con el sonido espacial, puede hacer que los hologramas suenen como si estuvieran detrás, junto a usted o incluso en su cabeza.</span><span class="sxs-lookup"><span data-stu-id="90e92-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="90e92-114">En este curso, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="90e92-114">In this course, you will:</span></span>

* <span data-ttu-id="90e92-115">Configure el entorno de desarrollo para usar el sonido espacial de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="90e92-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="90e92-116">Use el sonido espacial para mejorar las interacciones.</span><span class="sxs-lookup"><span data-stu-id="90e92-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="90e92-117">Use el sonido espacial junto con la [asignación espacial](spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="90e92-117">Use Spatial Sound in conjunction with [Spatial Mapping](spatial-mapping.md).</span></span>
* <span data-ttu-id="90e92-118">Comprenda las prácticas recomendadas de diseño y mezcla.</span><span class="sxs-lookup"><span data-stu-id="90e92-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="90e92-119">Use el sonido para mejorar los efectos especiales y poner al usuario en el mundo de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="90e92-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="90e92-120">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="90e92-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="90e92-121">Recurso</span><span class="sxs-lookup"><span data-stu-id="90e92-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="90e92-122"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="90e92-122"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="90e92-123"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="90e92-123"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="90e92-124">MR espacial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="90e92-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="90e92-125">✔️</span><span class="sxs-lookup"><span data-stu-id="90e92-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="90e92-126">✔️</span><span class="sxs-lookup"><span data-stu-id="90e92-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="90e92-127">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="90e92-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="90e92-128">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="90e92-128">Prerequisites</span></span>

* <span data-ttu-id="90e92-129">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="90e92-129">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="90e92-130">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="90e92-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="90e92-131">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="90e92-131">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="90e92-132">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="90e92-132">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="90e92-133">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="90e92-133">Project files</span></span>

* <span data-ttu-id="90e92-134">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="90e92-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="90e92-135"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="90e92-135"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="90e92-136">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="90e92-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="90e92-137">Es posible que esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="90e92-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="90e92-138">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="90e92-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="90e92-139"> Es posible que esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="90e92-139"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="90e92-140">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="90e92-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="90e92-141"> Es posible que esta versión ya no esté actualizada.</span><span class="sxs-lookup"><span data-stu-id="90e92-141"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="90e92-142">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="90e92-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="90e92-143">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="90e92-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="90e92-144">Erratas y notas</span><span class="sxs-lookup"><span data-stu-id="90e92-144">Errata and Notes</span></span>

* <span data-ttu-id="90e92-145">"Habilitar Solo mi código" debe estar deshabilitado *(desactivado*) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="90e92-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="90e92-146">Capítulo 1: configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="90e92-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="90e92-147">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90e92-147">Objectives</span></span>

* <span data-ttu-id="90e92-148">Cambie la configuración de sonido de Unity para usar el sonido espacial de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="90e92-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="90e92-149">Agregue un sonido 3D a un objeto en Unity.</span><span class="sxs-lookup"><span data-stu-id="90e92-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="90e92-150">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-150">Instructions</span></span>

* <span data-ttu-id="90e92-151">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="90e92-151">Start Unity.</span></span>
* <span data-ttu-id="90e92-152">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="90e92-152">Select **Open**.</span></span>
* <span data-ttu-id="90e92-153">Navegue hasta el escritorio y busque la carpeta que ha eliminado previamente.</span><span class="sxs-lookup"><span data-stu-id="90e92-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="90e92-154">Haga clic en la carpeta **Starting\Decibel** y, a continuación, presione el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="90e92-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="90e92-155">Espere a que el proyecto se cargue en Unity.</span><span class="sxs-lookup"><span data-stu-id="90e92-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="90e92-156">En el panel **proyecto** , Abra **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="90e92-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="90e92-157">En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="90e92-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="90e92-158">En el inspector, expanda **AudioSource** y observe que no hay ninguna casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="90e92-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="90e92-159">De forma predeterminada, Unity no carga un complemento de spatializer.</span><span class="sxs-lookup"><span data-stu-id="90e92-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="90e92-160">En los pasos siguientes se habilitará el sonido espacial en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="90e92-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="90e92-161">En el menú superior de Unity, vaya a **editar > configuración del proyecto > audio**.</span><span class="sxs-lookup"><span data-stu-id="90e92-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="90e92-162">Busque la lista desplegable **complemento de Spatializer** y seleccione **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="90e92-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="90e92-163">En el panel **jerarquía** , seleccione **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="90e92-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="90e92-164">En el panel **Inspector** , busque el componente de **origen de audio** .</span><span class="sxs-lookup"><span data-stu-id="90e92-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="90e92-165">Active la casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="90e92-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="90e92-166">Arrastre el control deslizante de **combinación espacial** hasta el modo **3D**o escriba **1** en el cuadro de edición.</span><span class="sxs-lookup"><span data-stu-id="90e92-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="90e92-167">Ahora se compilará el proyecto en Unity y se configurará la solución en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e92-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="90e92-168">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="90e92-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="90e92-169">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="90e92-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="90e92-170">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="90e92-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="90e92-171">Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**.</span><span class="sxs-lookup"><span data-stu-id="90e92-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="90e92-172">De lo contrario, déjelo en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="90e92-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="90e92-173">Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).</span><span class="sxs-lookup"><span data-stu-id="90e92-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="90e92-174">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="90e92-174">Click **Build**.</span></span>
7. <span data-ttu-id="90e92-175">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="90e92-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="90e92-176">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="90e92-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="90e92-177">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="90e92-177">Press **Select Folder**.</span></span>

<span data-ttu-id="90e92-178">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="90e92-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="90e92-179">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="90e92-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="90e92-180">Abra la **solución de Visual Studio de decibelios**.</span><span class="sxs-lookup"><span data-stu-id="90e92-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="90e92-181">Si se implementa en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="90e92-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="90e92-182">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.</span><span class="sxs-lookup"><span data-stu-id="90e92-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="90e92-183">Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="90e92-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="90e92-184">Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="90e92-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="90e92-185">Haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="90e92-185">Click **Select**.</span></span> <span data-ttu-id="90e92-186">Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.</span><span class="sxs-lookup"><span data-stu-id="90e92-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="90e92-187">En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="90e92-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="90e92-188">Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="90e92-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="90e92-189">Si se implementa en un auricular envolvente:</span><span class="sxs-lookup"><span data-stu-id="90e92-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="90e92-190">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="90e92-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="90e92-191">Asegúrese de que el destino de implementación está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="90e92-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="90e92-192">En la barra de menús superior, haga clic en **depurar-> iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="90e92-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="90e92-193">Capítulo 2: sonido espacial e interacción</span><span class="sxs-lookup"><span data-stu-id="90e92-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="90e92-194">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90e92-194">Objectives</span></span>

* <span data-ttu-id="90e92-195">Mejore el realismo del holograma mediante el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="90e92-196">Dirija la mirada del usuario con el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="90e92-197">Proporcione comentarios de gestos mediante sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="90e92-198">Parte 1: mejora del realismo</span><span class="sxs-lookup"><span data-stu-id="90e92-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-199">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-199">Key Concepts</span></span>

* <span data-ttu-id="90e92-200">Spatial los sonidos del holograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="90e92-201">Los orígenes de sonido se deben colocar en una ubicación adecuada en el holograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="90e92-202">La ubicación adecuada para el sonido dependerá del holograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="90e92-203">Por ejemplo, si el holograma es humano, el origen de sonido debe estar situado cerca de la boca y no de los pies.</span><span class="sxs-lookup"><span data-stu-id="90e92-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="90e92-204">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-204">Instructions</span></span>

<span data-ttu-id="90e92-205">Las instrucciones siguientes conectarán un sonido espacial a un holograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="90e92-206">En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="90e92-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="90e92-207">En el panel **Inspector** , en el **AudioSource**, haga clic en el círculo situado junto a **AudioClip** y seleccione el **subdesplazamiento** en el elemento emergente.</span><span class="sxs-lookup"><span data-stu-id="90e92-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="90e92-208">Haga clic en el círculo situado junto a **salida** y seleccione **SoundEffects** en el elemento emergente.</span><span class="sxs-lookup"><span data-stu-id="90e92-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="90e92-209">El proyecto de decibelios usa un componente **AudioMixer** de Unity para habilitar el ajuste de los niveles de sonido para grupos de sonidos.</span><span class="sxs-lookup"><span data-stu-id="90e92-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="90e92-210">Al agrupar los sonidos de esta manera, se puede ajustar el volumen global mientras se mantiene el volumen relativo de cada sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="90e92-211">En **AudioSource**, expanda **configuración de sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="90e92-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="90e92-212">Establezca el **nivel de Doppler** en **0**.</span><span class="sxs-lookup"><span data-stu-id="90e92-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="90e92-213">Si se establece el nivel de Doppler en cero, se deshabilitan los cambios de tono causados por el movimiento (el holograma o el usuario).</span><span class="sxs-lookup"><span data-stu-id="90e92-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="90e92-214">Un ejemplo clásico de Doppler es un coche con movimiento rápido.</span><span class="sxs-lookup"><span data-stu-id="90e92-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="90e92-215">A medida que el coche se aproxima a un agente de escucha estacionario, aumenta el tono del motor.</span><span class="sxs-lookup"><span data-stu-id="90e92-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="90e92-216">Cuando pasa el agente de escucha, el paso disminuye con la distancia.</span><span class="sxs-lookup"><span data-stu-id="90e92-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="90e92-217">Parte 2: dirigir la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="90e92-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-218">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-218">Key Concepts</span></span>

* <span data-ttu-id="90e92-219">Use el sonido para llamar la atención a los hologramas importantes.</span><span class="sxs-lookup"><span data-stu-id="90e92-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="90e92-220">Los oídos le ayudarán a tener el aspecto de los ojos.</span><span class="sxs-lookup"><span data-stu-id="90e92-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="90e92-221">El cerebro tiene algunas expectativas conocidas.</span><span class="sxs-lookup"><span data-stu-id="90e92-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="90e92-222">Un ejemplo de expectativas aprendidas es que las aves suelen estar por encima de los cabezales de los seres humanos.</span><span class="sxs-lookup"><span data-stu-id="90e92-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="90e92-223">Si un usuario oye un sonido de pájaro, su reacción inicial es buscar.</span><span class="sxs-lookup"><span data-stu-id="90e92-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="90e92-224">Colocar un pájaro debajo del usuario puede conducir a que se dirija a la dirección correcta del sonido, pero no puede encontrar el holograma en función de la expectativa de necesidad de buscar.</span><span class="sxs-lookup"><span data-stu-id="90e92-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="90e92-225">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-225">Instructions</span></span>

<span data-ttu-id="90e92-226">Las instrucciones siguientes permiten que P0LY se oculte por detrás, de modo que pueda usar el sonido para buscar el holograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="90e92-227">En el panel **jerarquía** , seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="90e92-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="90e92-228">En el panel **Inspector** , busque **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="90e92-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="90e92-229">En **controlador de entrada de voz**, expanda **ocultar**.</span><span class="sxs-lookup"><span data-stu-id="90e92-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="90e92-230">**No cambie ninguna función** a **poliactions. GoHide**.</span><span class="sxs-lookup"><span data-stu-id="90e92-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Palabra clave: ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="90e92-232">Parte 3: comentarios de gestos</span><span class="sxs-lookup"><span data-stu-id="90e92-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-233">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-233">Key Concepts</span></span>

* <span data-ttu-id="90e92-234">Proporcionar al usuario la confirmación de gestos positivos mediante el sonido</span><span class="sxs-lookup"><span data-stu-id="90e92-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="90e92-235">No sobrecargar el exceso de sonido del usuario en el camino</span><span class="sxs-lookup"><span data-stu-id="90e92-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="90e92-236">Los sonidos sutiles funcionan mejor: no hagan la experiencia</span><span class="sxs-lookup"><span data-stu-id="90e92-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="90e92-237">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-237">Instructions</span></span>

* <span data-ttu-id="90e92-238">En el panel **jerarquía** , expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="90e92-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="90e92-239">Expanda **EnergyHub** y seleccione **base**.</span><span class="sxs-lookup"><span data-stu-id="90e92-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="90e92-240">En el panel **Inspector** , haga clic en **Agregar componente** y agregue el **controlador de sonido de gesto**.</span><span class="sxs-lookup"><span data-stu-id="90e92-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="90e92-241">En el **controlador de sonido de gestos**, haga clic en el círculo situado junto a **navegación Inicio clip** y **navegación actualizado clip** y seleccione **RotateClick** en el elemento emergente para ambos.</span><span class="sxs-lookup"><span data-stu-id="90e92-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="90e92-242">Haga doble clic en "GestureSoundHandler" para cargar en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e92-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="90e92-243">El controlador de sonido de gestos realiza las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="90e92-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="90e92-244">Cree y configure un **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="90e92-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="90e92-245">Coloque **AudioSource** en la ubicación de la **GameObject**adecuada.</span><span class="sxs-lookup"><span data-stu-id="90e92-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="90e92-246">Reproduce el **AudioClip** asociado con el gesto.</span><span class="sxs-lookup"><span data-stu-id="90e92-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="90e92-247">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="90e92-247">Build and Deploy</span></span>

1. <span data-ttu-id="90e92-248">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="90e92-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="90e92-249">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="90e92-249">Click **Build**.</span></span>
3. <span data-ttu-id="90e92-250">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="90e92-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="90e92-251">Presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="90e92-251">Press **Select Folder**.</span></span>

<span data-ttu-id="90e92-252">Compruebe que la barra de herramientas indica "release", "x86" o "x64" y "dispositivo remoto".</span><span class="sxs-lookup"><span data-stu-id="90e92-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="90e92-253">Si no es así, se trata de la instancia de codificación de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e92-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="90e92-254">Es posible que tenga que volver a abrir la solución desde la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="90e92-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="90e92-255">Si se le solicita, vuelva a cargar los archivos de proyecto.</span><span class="sxs-lookup"><span data-stu-id="90e92-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="90e92-256">Como antes, implemente desde Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e92-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="90e92-257">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="90e92-257">After the application is deployed:</span></span>

* <span data-ttu-id="90e92-258">Observe cómo cambia el sonido a medida que se desplaza por P0LY.</span><span class="sxs-lookup"><span data-stu-id="90e92-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="90e92-259">Di *"ir a ocultar"* para que P0LY se mueva a una ubicación detrás.</span><span class="sxs-lookup"><span data-stu-id="90e92-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="90e92-260">Lo encuentra en el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-260">Find it by the sound.</span></span>
* <span data-ttu-id="90e92-261">Mira la base de la central de energía.</span><span class="sxs-lookup"><span data-stu-id="90e92-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="90e92-262">Puntee y arrastre hacia la izquierda o hacia la derecha para girar el holograma y observe cómo el sonido que hace clic confirma el gesto.</span><span class="sxs-lookup"><span data-stu-id="90e92-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="90e92-263">Nota: hay un panel de texto que se etiquetará junto con usted.</span><span class="sxs-lookup"><span data-stu-id="90e92-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="90e92-264">Esto contendrá los comandos de voz disponibles que puede usar en este curso.</span><span class="sxs-lookup"><span data-stu-id="90e92-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="90e92-265">Capítulo 3: mapa espacial y de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="90e92-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="90e92-266">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90e92-266">Objectives</span></span>

* <span data-ttu-id="90e92-267">Confirme la interacción entre los hologramas y el mundo real mediante el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="90e92-268">Tapaba sonido con el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="90e92-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="90e92-269">Parte 1: interacción del mundo físico</span><span class="sxs-lookup"><span data-stu-id="90e92-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-270">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-270">Key Concepts</span></span>

* <span data-ttu-id="90e92-271">Normalmente, los objetos físicos realizan un sonido al encontrar una superficie u otro objeto.</span><span class="sxs-lookup"><span data-stu-id="90e92-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="90e92-272">Los sonidos deben ser el contexto adecuado dentro de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="90e92-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="90e92-273">Por ejemplo, el establecimiento de una copa en una tabla debe hacer un sonido más silencioso que colocar un Boulder en una pieza de metal.</span><span class="sxs-lookup"><span data-stu-id="90e92-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="90e92-274">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-274">Instructions</span></span>

* <span data-ttu-id="90e92-275">En el panel **jerarquía** , expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="90e92-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="90e92-276">Expanda **EnergyHub**y seleccione **base**.</span><span class="sxs-lookup"><span data-stu-id="90e92-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="90e92-277">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **puntear para colocar con el sonido y la acción**.</span><span class="sxs-lookup"><span data-stu-id="90e92-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="90e92-278">En **puntear para colocar con el sonido y la acción**:</span><span class="sxs-lookup"><span data-stu-id="90e92-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="90e92-279">Active **colocar primario al pulsar**.</span><span class="sxs-lookup"><span data-stu-id="90e92-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="90e92-280">Establezca el sonido de **selección de ubicación** .</span><span class="sxs-lookup"><span data-stu-id="90e92-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="90e92-281">Establezca **sonido de recogida** en **recogida**.</span><span class="sxs-lookup"><span data-stu-id="90e92-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="90e92-282">Presione + en la parte inferior derecha, en la acción **de recogida** y **en la acción de selección de ubicación**.</span><span class="sxs-lookup"><span data-stu-id="90e92-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="90e92-283">Arrastre EnergyHub desde la escena hasta los campos **ninguno (objeto)** .</span><span class="sxs-lookup"><span data-stu-id="90e92-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="90e92-284">En **acción de recogida**, haga clic en **ninguna función** -> **EnergyHubBase** -> **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="90e92-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="90e92-285">En **acción de selección de ubicación**, haga clic en **ninguna función** -> **EnergyHubBase** -> **alseleccionar**.</span><span class="sxs-lookup"><span data-stu-id="90e92-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Puntee para colocar con el sonido y la acción](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="90e92-287">Parte 2: oclusión de sonido</span><span class="sxs-lookup"><span data-stu-id="90e92-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-288">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-288">Key Concepts</span></span>

* <span data-ttu-id="90e92-289">El sonido, como Light, puede ser ocluidos.</span><span class="sxs-lookup"><span data-stu-id="90e92-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="90e92-290">Un ejemplo clásico es un salón de concierto.</span><span class="sxs-lookup"><span data-stu-id="90e92-290">A classic example is a concert hall.</span></span> <span data-ttu-id="90e92-291">Cuando un agente de escucha está fuera del salón y la puerta está cerrada, la música suena silenciada.</span><span class="sxs-lookup"><span data-stu-id="90e92-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="90e92-292">Normalmente, también hay una reducción del volumen.</span><span class="sxs-lookup"><span data-stu-id="90e92-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="90e92-293">Cuando se abre la puerta, se oye todo el espectro del sonido en el volumen real.</span><span class="sxs-lookup"><span data-stu-id="90e92-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="90e92-294">Los sonidos de alta frecuencia suelen absorber más que las bajas frecuencias.</span><span class="sxs-lookup"><span data-stu-id="90e92-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="90e92-295">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-295">Instructions</span></span>

* <span data-ttu-id="90e92-296">En el panel **jerarquía** , expanda **HologramCollection** y seleccione **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="90e92-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="90e92-297">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **emisor de audio**.</span><span class="sxs-lookup"><span data-stu-id="90e92-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="90e92-298">La clase emisora de audio proporciona las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="90e92-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="90e92-299">Restaura cualquier cambio realizado en el volumen de **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="90e92-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="90e92-300">Realiza una conexión **física. RaycastNonAlloc** desde la posición del usuario en la dirección del **GameObject** al que se adjunta el **AudioEmitter** .</span><span class="sxs-lookup"><span data-stu-id="90e92-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="90e92-301">El método RaycastNonAlloc se usa como optimización del rendimiento para limitar las asignaciones y el número de resultados devueltos.</span><span class="sxs-lookup"><span data-stu-id="90e92-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="90e92-302">Para cada **IAudioInfluencer** encontrada, llama al método **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="90e92-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="90e92-303">Para cada **IAudioInfluencer** anterior que ya no se encuentre, llame al método **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="90e92-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="90e92-304">Tenga en cuenta que AudioEmitter se actualiza en las escalas de tiempo humano, en lugar de en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="90e92-305">Esto se hace porque los seres humanos generalmente no se mueven lo suficientemente rápido como para que el efecto tenga que actualizarse con más frecuencia que cada trimestre o mitad de segundo.</span><span class="sxs-lookup"><span data-stu-id="90e92-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="90e92-306">Los hologramas que se destransportan rápidamente de una ubicación a otra pueden interrumpir el efecto.</span><span class="sxs-lookup"><span data-stu-id="90e92-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="90e92-307">En el panel **jerarquía** , expanda **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="90e92-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="90e92-308">Expanda **EnergyHub** y seleccione **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="90e92-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="90e92-309">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="90e92-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="90e92-310">En **audio Occluder**, establezca la **frecuencia límite** en **1500**.</span><span class="sxs-lookup"><span data-stu-id="90e92-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="90e92-311">Esta configuración limita las frecuencias AudioSource a 1500 Hz y por debajo.</span><span class="sxs-lookup"><span data-stu-id="90e92-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="90e92-312">Establezca el **paso de volumen** en **0,9**.</span><span class="sxs-lookup"><span data-stu-id="90e92-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="90e92-313">Esta configuración reduce el volumen de AudioSource al 90% del nivel actual.</span><span class="sxs-lookup"><span data-stu-id="90e92-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="90e92-314">Audio Occluder implementa IAudioInfluencer para:</span><span class="sxs-lookup"><span data-stu-id="90e92-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="90e92-315">Aplicar un efecto de oclusión mediante un **AudioLowPassFilter** que se adjunta a la **AudioSource** administrada compre el **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="90e92-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="90e92-316">Aplica la atenuación del volumen a AudioSource.</span><span class="sxs-lookup"><span data-stu-id="90e92-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="90e92-317">Deshabilita el efecto estableciendo una frecuencia de límite neutro y deshabilitando el filtro.</span><span class="sxs-lookup"><span data-stu-id="90e92-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="90e92-318">La frecuencia usada como neutra es de 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="90e92-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="90e92-319">Esta frecuencia se eligió debido a que está por encima de la frecuencia máxima nominal que puede ser oída por el oído humano, lo que no hace ningún impacto más perceptible en el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="90e92-320">En el panel **jerarquía** , seleccione **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="90e92-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="90e92-321">En el panel **Inspector** , haga clic en **Agregar componente** y agregue **audio Occluder**.</span><span class="sxs-lookup"><span data-stu-id="90e92-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="90e92-322">En **audio Occluder**, establezca la **frecuencia límite** en **750**.</span><span class="sxs-lookup"><span data-stu-id="90e92-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="90e92-323">Cuando hay varios occluders en la ruta de acceso entre el usuario y el **AudioEmitter**, se aplica la frecuencia más baja al filtro.</span><span class="sxs-lookup"><span data-stu-id="90e92-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="90e92-324">Establezca el **paso de volumen** en **0,75**.</span><span class="sxs-lookup"><span data-stu-id="90e92-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="90e92-325">Cuando hay varios occluders en la ruta de acceso entre el usuario y el **AudioEmitter**, el paso del volumen a través se aplica de forma aditiva.</span><span class="sxs-lookup"><span data-stu-id="90e92-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="90e92-326">En el panel **jerarquía** , seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="90e92-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="90e92-327">En el panel **Inspector** , expanda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="90e92-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="90e92-328">En **controlador de entrada de voz**, expanda **gastos de avance**.</span><span class="sxs-lookup"><span data-stu-id="90e92-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="90e92-329">**No cambie ninguna función** a **poliactions. GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="90e92-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Palabra clave: gastos de avance](images/gocharge.png)

* <span data-ttu-id="90e92-331">Amplíe **aquí**.</span><span class="sxs-lookup"><span data-stu-id="90e92-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="90e92-332">**No cambie ninguna función** a **poliactions. Comeback**.</span><span class="sxs-lookup"><span data-stu-id="90e92-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Palabra clave: viene aquí](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="90e92-334">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="90e92-334">Build and Deploy</span></span>

* <span data-ttu-id="90e92-335">Como antes, compile el proyecto en Unity e impleméntelo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e92-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="90e92-336">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="90e92-336">After the application is deployed:</span></span>

* <span data-ttu-id="90e92-337">Por ejemplo, *"go CHARGE"* para que P0LY escriba el centro de energía.</span><span class="sxs-lookup"><span data-stu-id="90e92-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="90e92-338">Observe el cambio en el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-338">Note the change in the sound.</span></span> <span data-ttu-id="90e92-339">Debe sonar silenciado y un poco más silencioso.</span><span class="sxs-lookup"><span data-stu-id="90e92-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="90e92-340">Si puede colocarse con una pared u otro objeto entre usted y el centro de energía, debe observar un mayor silenciamiento del sonido debido a la oclusión del mundo real.</span><span class="sxs-lookup"><span data-stu-id="90e92-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="90e92-341">Supongamos que *"viene aquí"* para que P0LY deje la central de energía y se coloque por delante.</span><span class="sxs-lookup"><span data-stu-id="90e92-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="90e92-342">Tenga en cuenta que la oclusión de sonido se quita una vez que P0LY sale del centro de energía.</span><span class="sxs-lookup"><span data-stu-id="90e92-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="90e92-343">Si todavía está escuchando oclusión, P0LY puede ser ocluidos en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="90e92-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="90e92-344">Intente cambiar para asegurarse de que tiene una línea de visión clara a P0LY.</span><span class="sxs-lookup"><span data-stu-id="90e92-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="90e92-345">Parte 3: modelos Room</span><span class="sxs-lookup"><span data-stu-id="90e92-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-346">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-346">Key Concepts</span></span>

* <span data-ttu-id="90e92-347">El tamaño del espacio proporciona colas de subliminal que contribuyen a la localización de sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="90e92-348">Los modelos de sala se establecen por**AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="90e92-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="90e92-349">[MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona código para establecer el modelo de habitación.</span><span class="sxs-lookup"><span data-stu-id="90e92-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="90e92-350">En el caso de experiencias de realidad mixta, seleccione el modelo de salón que mejor se adapte al espacio real del mundo.</span><span class="sxs-lookup"><span data-stu-id="90e92-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="90e92-351">Si va a crear un escenario de realidad virtual, seleccione el modelo de salón que mejor se adapte al entorno virtual.</span><span class="sxs-lookup"><span data-stu-id="90e92-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="90e92-352">Capítulo 4: diseño de sonido</span><span class="sxs-lookup"><span data-stu-id="90e92-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="90e92-353">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90e92-353">Objectives</span></span>

* <span data-ttu-id="90e92-354">Comprender las consideraciones para un diseño de sonido eficaz.</span><span class="sxs-lookup"><span data-stu-id="90e92-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="90e92-355">Obtenga información sobre las técnicas y las directrices de combinación.</span><span class="sxs-lookup"><span data-stu-id="90e92-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="90e92-356">Parte 1: diseño de la experiencia y el sonido</span><span class="sxs-lookup"><span data-stu-id="90e92-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="90e92-357">En esta sección se describen las consideraciones y directrices de diseño de la experiencia y el sonido clave.</span><span class="sxs-lookup"><span data-stu-id="90e92-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="90e92-358">Normalizar todos los sonidos</span><span class="sxs-lookup"><span data-stu-id="90e92-358">Normalize all sounds</span></span>

<span data-ttu-id="90e92-359">Esto evita la necesidad de que el código de caso especial ajuste los niveles de volumen por sonido, lo que puede llevar mucho tiempo y limita la capacidad de actualizar fácilmente los archivos de sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="90e92-360">Diseño para una experiencia de untethered</span><span class="sxs-lookup"><span data-stu-id="90e92-360">Design for an untethered experience</span></span>

<span data-ttu-id="90e92-361">HoloLens es un equipo untethered Holographic totalmente contenido.</span><span class="sxs-lookup"><span data-stu-id="90e92-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="90e92-362">Los usuarios pueden usar sus experiencias mientras se mueven.</span><span class="sxs-lookup"><span data-stu-id="90e92-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="90e92-363">Asegúrese de probar la combinación de audio.</span><span class="sxs-lookup"><span data-stu-id="90e92-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="90e92-364">Emitir sonido desde ubicaciones lógicas en los hologramas</span><span class="sxs-lookup"><span data-stu-id="90e92-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="90e92-365">En el mundo real, un perro no se corteza de su cola y la voz de un hombre no proviene de sus pies.</span><span class="sxs-lookup"><span data-stu-id="90e92-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="90e92-366">Evite que los sonidos se emitan desde partes inesperadas de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="90e92-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="90e92-367">En el caso de los hologramas pequeños, es razonable tener una emisión de sonido desde el centro de la geometría.</span><span class="sxs-lookup"><span data-stu-id="90e92-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="90e92-368">Los sonidos conocidos son más localizables</span><span class="sxs-lookup"><span data-stu-id="90e92-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="90e92-369">La voz humana y la música son muy fáciles de localizar.</span><span class="sxs-lookup"><span data-stu-id="90e92-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="90e92-370">Si alguien llama a su nombre, puede determinar con precisión desde qué dirección se ha recibido la voz y desde dónde está.</span><span class="sxs-lookup"><span data-stu-id="90e92-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="90e92-371">Los sonidos cortos y desconocidos son más difíciles de localizar.</span><span class="sxs-lookup"><span data-stu-id="90e92-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="90e92-372">Cognizant de las expectativas de los usuarios</span><span class="sxs-lookup"><span data-stu-id="90e92-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="90e92-373">La experiencia de vida juega una parte en nuestra capacidad de identificar la ubicación de un sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="90e92-374">Esta es una de las razones por las que la voz humana es especialmente fácil de localizar.</span><span class="sxs-lookup"><span data-stu-id="90e92-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="90e92-375">Es importante tener en cuenta las expectativas aprendidas del usuario al colocar los sonidos.</span><span class="sxs-lookup"><span data-stu-id="90e92-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="90e92-376">Por ejemplo, cuando alguien oye una canción de pájaro, se suele buscar, ya que las aves tienden a estar por encima de la línea de visión (vuelo o en un árbol).</span><span class="sxs-lookup"><span data-stu-id="90e92-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="90e92-377">No es raro que un usuario Active la dirección correcta de un sonido, sino que mire en la dirección vertical equivocada y se confunda o frustraría cuando no pueda encontrar el holograma.</span><span class="sxs-lookup"><span data-stu-id="90e92-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="90e92-378">Evitar emisores ocultos</span><span class="sxs-lookup"><span data-stu-id="90e92-378">Avoid hidden emitters</span></span>

<span data-ttu-id="90e92-379">En el mundo real, si escuchamos un sonido, generalmente podemos identificar el objeto que emite el sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="90e92-380">También debe tener el valor true en sus experiencias.</span><span class="sxs-lookup"><span data-stu-id="90e92-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="90e92-381">Puede ser muy difícil para los usuarios oír un sonido, saber desde dónde se origina el sonido y no puede ver un objeto.</span><span class="sxs-lookup"><span data-stu-id="90e92-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="90e92-382">Existen algunas excepciones a esta directriz.</span><span class="sxs-lookup"><span data-stu-id="90e92-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="90e92-383">Por ejemplo, los sonidos ambientales como Crickets en un campo no deben ser visibles.</span><span class="sxs-lookup"><span data-stu-id="90e92-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="90e92-384">La experiencia de vida nos permite familiarizarse con el origen de estos sonidos sin necesidad de verlo.</span><span class="sxs-lookup"><span data-stu-id="90e92-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="90e92-385">Parte 2: combinación de sonidos</span><span class="sxs-lookup"><span data-stu-id="90e92-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="90e92-386">Destine su combinación para el volumen del 70% en HoloLens</span><span class="sxs-lookup"><span data-stu-id="90e92-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="90e92-387">Las experiencias de realidad mixta permiten que los hologramas se vean en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="90e92-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="90e92-388">También deben permitir escuchar sonidos reales.</span><span class="sxs-lookup"><span data-stu-id="90e92-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="90e92-389">Un destino de volumen del 70% permite al usuario oír todo el mundo junto con el sonido de su experiencia.</span><span class="sxs-lookup"><span data-stu-id="90e92-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="90e92-390">HoloLens en 100% de volumen debe estar ahogado a los sonidos externos</span><span class="sxs-lookup"><span data-stu-id="90e92-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="90e92-391">Un nivel de volumen del 100% es similar a una experiencia de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="90e92-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="90e92-392">Visualmente, el usuario se transporta a un mundo diferente.</span><span class="sxs-lookup"><span data-stu-id="90e92-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="90e92-393">Lo mismo debe ser un verdadero audible.</span><span class="sxs-lookup"><span data-stu-id="90e92-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="90e92-394">Usar el AudioMixer de Unity para ajustar categorías de sonidos</span><span class="sxs-lookup"><span data-stu-id="90e92-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="90e92-395">Al diseñar la combinación, a menudo resulta útil crear categorías de sonido y tener la capacidad de aumentar o disminuir el volumen como una unidad.</span><span class="sxs-lookup"><span data-stu-id="90e92-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="90e92-396">De este modo, se conservan los niveles relativos de cada sonido a la vez que se habilitan los cambios rápidos y sencillos en la combinación global.</span><span class="sxs-lookup"><span data-stu-id="90e92-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="90e92-397">Entre las categorías comunes se incluyen: efectos sonoros, ambiente, voz y música de fondo.</span><span class="sxs-lookup"><span data-stu-id="90e92-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="90e92-398">Mezcle los sonidos en función de la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="90e92-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="90e92-399">A menudo, puede resultar útil cambiar la combinación de sonidos de su experiencia en función de la ubicación de un usuario (o no).</span><span class="sxs-lookup"><span data-stu-id="90e92-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="90e92-400">Un uso común de esta técnica consiste en reducir el nivel de volumen de los hologramas que están fuera del marco holográfica para que el usuario pueda centrarse más fácilmente en la información que se encuentra delante de ellos.</span><span class="sxs-lookup"><span data-stu-id="90e92-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="90e92-401">Otro uso es aumentar el volumen de un sonido para atraer la atención del usuario a un evento importante.</span><span class="sxs-lookup"><span data-stu-id="90e92-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="90e92-402">Crear la combinación</span><span class="sxs-lookup"><span data-stu-id="90e92-402">Building your mix</span></span>

<span data-ttu-id="90e92-403">Al compilar la combinación, se recomienda empezar con el audio de fondo de la experiencia y agregar capas basadas en importancia.</span><span class="sxs-lookup"><span data-stu-id="90e92-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="90e92-404">A menudo, esto da lugar a que cada capa sea más fuerte que la anterior.</span><span class="sxs-lookup"><span data-stu-id="90e92-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="90e92-405">Al imaginarse la combinación como un embudo invertido, con el menos importante (y los sonidos generalmente más silencioso) en la parte inferior, se recomienda estructurar la combinación similar al siguiente diagrama.</span><span class="sxs-lookup"><span data-stu-id="90e92-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Estructura de combinación de sonidos](images/soundlevels.png)

<span data-ttu-id="90e92-407">La voz es un escenario interesante.</span><span class="sxs-lookup"><span data-stu-id="90e92-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="90e92-408">En función de la experiencia que cree, puede que desee tener un sonido estéreo (no localizado) o crear un espacial de la voz.</span><span class="sxs-lookup"><span data-stu-id="90e92-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="90e92-409">Dos experiencias publicadas de Microsoft muestran excelentes ejemplos de cada escenario.</span><span class="sxs-lookup"><span data-stu-id="90e92-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="90e92-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voz de estéreo.</span><span class="sxs-lookup"><span data-stu-id="90e92-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="90e92-411">Cuando el narrador describe la ubicación que se está viendo, el sonido es coherente y no varía en función de la posición del usuario.</span><span class="sxs-lookup"><span data-stu-id="90e92-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="90e92-412">Esto permite al narrador describir la escena sin tener que alejarse de los sonidos espaciales del entorno.</span><span class="sxs-lookup"><span data-stu-id="90e92-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="90e92-413">[Fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) emplea una voz espacial en forma de un detective.</span><span class="sxs-lookup"><span data-stu-id="90e92-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="90e92-414">La voz del detective se usa para ayudar a la atención del usuario a una pista importante como si hubiera un hombre real en el salón.</span><span class="sxs-lookup"><span data-stu-id="90e92-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="90e92-415">Esto permite una mayor sensación de inmersión en la experiencia de resolución del misterio.</span><span class="sxs-lookup"><span data-stu-id="90e92-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="90e92-416">Parte 3: rendimiento</span><span class="sxs-lookup"><span data-stu-id="90e92-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="90e92-417">Uso de CPU</span><span class="sxs-lookup"><span data-stu-id="90e92-417">CPU usage</span></span>

<span data-ttu-id="90e92-418">Cuando se usa el sonido espacial, 10-12 emisores consumirán aproximadamente el 12% de la CPU.</span><span class="sxs-lookup"><span data-stu-id="90e92-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="90e92-419">Transmitir archivos de audio largos</span><span class="sxs-lookup"><span data-stu-id="90e92-419">Stream long audio files</span></span>

<span data-ttu-id="90e92-420">Los datos de audio pueden ser grandes, sobre todo en las tarifas de ejemplo comunes (44,1 y 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="90e92-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="90e92-421">Una regla general es que los archivos de audio de más de 5-10 segundos se deben transmitir para reducir el uso de memoria de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="90e92-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="90e92-422">En Unity, puede marcar un archivo de audio para el streaming en la configuración de importación del archivo.</span><span class="sxs-lookup"><span data-stu-id="90e92-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Configuración de importación de audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="90e92-424">Capítulo 5: efectos especiales</span><span class="sxs-lookup"><span data-stu-id="90e92-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="90e92-425">Objetivos</span><span class="sxs-lookup"><span data-stu-id="90e92-425">Objectives</span></span>

* <span data-ttu-id="90e92-426">Agregue profundidad a "Magic Windows".</span><span class="sxs-lookup"><span data-stu-id="90e92-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="90e92-427">Traslade al usuario al mundo virtual.</span><span class="sxs-lookup"><span data-stu-id="90e92-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="90e92-428">Ventanas mágicas</span><span class="sxs-lookup"><span data-stu-id="90e92-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="90e92-429">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="90e92-429">Key Concepts</span></span>

* <span data-ttu-id="90e92-430">La creación de vistas en un mundo oculto es visualmente atractiva.</span><span class="sxs-lookup"><span data-stu-id="90e92-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="90e92-431">Mejore el realismo agregando efectos de audio cuando un holograma o el usuario están cerca del mundo oculto.</span><span class="sxs-lookup"><span data-stu-id="90e92-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="90e92-432">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="90e92-432">Instructions</span></span>

* <span data-ttu-id="90e92-433">En el panel **jerarquía** , expanda **HologramCollection** y seleccione el **submundo**.</span><span class="sxs-lookup"><span data-stu-id="90e92-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="90e92-434">Expanda el **submundo** y seleccione **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="90e92-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="90e92-435">En el panel **Inspector** , haga clic en **Agregar componente** y agregar **efecto de voz de usuario**.</span><span class="sxs-lookup"><span data-stu-id="90e92-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="90e92-436">Se agregará un componente **AudioSource** a **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="90e92-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="90e92-437">En **AudioSource**, establezca **salida** en **UserVoice (Mixer)** .</span><span class="sxs-lookup"><span data-stu-id="90e92-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="90e92-438">Active la casilla **Spatial** .</span><span class="sxs-lookup"><span data-stu-id="90e92-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="90e92-439">Arrastre el control deslizante de **combinación espacial** hasta el modo **3D**o escriba **1** en el cuadro de edición.</span><span class="sxs-lookup"><span data-stu-id="90e92-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="90e92-440">Expanda **configuración de sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="90e92-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="90e92-441">Establezca el **nivel de Doppler** en **0**.</span><span class="sxs-lookup"><span data-stu-id="90e92-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="90e92-442">En **efecto de voz de usuario**, establezca **objeto primario** en el **mundo** de la escena.</span><span class="sxs-lookup"><span data-stu-id="90e92-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="90e92-443">Establezca la **distancia máxima** en **1**.</span><span class="sxs-lookup"><span data-stu-id="90e92-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="90e92-444">El establecimiento de la **distancia máxima** indica al **usuario el efecto** de la forma en que el usuario debe estar al objeto primario antes de que se habilite el efecto.</span><span class="sxs-lookup"><span data-stu-id="90e92-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="90e92-445">En **efecto de voz de usuario**, expanda **los parámetros de coro**.</span><span class="sxs-lookup"><span data-stu-id="90e92-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="90e92-446">Establezca **profundidad** en **0,1**.</span><span class="sxs-lookup"><span data-stu-id="90e92-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="90e92-447">Establezca **TAP 1 Volume**, **Pulse 2 Volume** y **Pulse 3 Volume** hasta **0,8**.</span><span class="sxs-lookup"><span data-stu-id="90e92-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="90e92-448">Establezca el **volumen de sonido original** en **0,5**.</span><span class="sxs-lookup"><span data-stu-id="90e92-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="90e92-449">La configuración anterior configura los parámetros del **AudioChorusFilter** de Unity que se usa para agregar riqueza a la voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="90e92-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="90e92-450">En **efecto de voz de usuario**, expanda **parámetros de eco**.</span><span class="sxs-lookup"><span data-stu-id="90e92-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="90e92-451">Establecer **retraso** en **300**</span><span class="sxs-lookup"><span data-stu-id="90e92-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="90e92-452">Establezca la **relación de decadencia** en **0,2**.</span><span class="sxs-lookup"><span data-stu-id="90e92-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="90e92-453">Establezca el **volumen de sonido original** en **0**.</span><span class="sxs-lookup"><span data-stu-id="90e92-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="90e92-454">La configuración anterior configura los parámetros del **AudioEchoFilter** de Unity que se usa para hacer que la voz del usuario se repita.</span><span class="sxs-lookup"><span data-stu-id="90e92-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="90e92-455">El script de efecto de la voz de usuario es responsable de:</span><span class="sxs-lookup"><span data-stu-id="90e92-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="90e92-456">Medir la distancia entre el usuario y el **GameObject** al que se adjunta el script.</span><span class="sxs-lookup"><span data-stu-id="90e92-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="90e92-457">Determinar si el usuario está orientado o no al **GameObject**.</span><span class="sxs-lookup"><span data-stu-id="90e92-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="90e92-458">El usuario debe estar orientado a GameObject, independientemente de la distancia, para que el efecto se habilite.</span><span class="sxs-lookup"><span data-stu-id="90e92-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="90e92-459">Aplicar y configurar **AudioChorusFilter** y **AudioEchoFilter** en **AudioSource**.</span><span class="sxs-lookup"><span data-stu-id="90e92-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="90e92-460">Deshabilitar el efecto deshabilitando los filtros.</span><span class="sxs-lookup"><span data-stu-id="90e92-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="90e92-461">Efecto de voz de usuario usa el componente selector de flujo de MIC, de [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), para seleccionar el flujo de voz de alta calidad y enrutarlo al sistema de audio de Unity.</span><span class="sxs-lookup"><span data-stu-id="90e92-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="90e92-462">En el panel **jerarquía** , seleccione **administradores**.</span><span class="sxs-lookup"><span data-stu-id="90e92-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="90e92-463">En el panel **Inspector** , expanda **controlador de entrada de voz**.</span><span class="sxs-lookup"><span data-stu-id="90e92-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="90e92-464">En **controlador de entrada de voz**, expanda **Mostrar el submundo**.</span><span class="sxs-lookup"><span data-stu-id="90e92-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="90e92-465">No cambie la **función** a **UnderworldBase. alhabilitar**.</span><span class="sxs-lookup"><span data-stu-id="90e92-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Palabra clave: mostrar el submundo](images/showunderworld.png)

* <span data-ttu-id="90e92-467">Expanda **ocultar submundo**.</span><span class="sxs-lookup"><span data-stu-id="90e92-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="90e92-468">No cambie la **función** a **UnderworldBase. deshabilito**.</span><span class="sxs-lookup"><span data-stu-id="90e92-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Palabra clave: ocultar el submundo](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="90e92-470">Compilación e implementación</span><span class="sxs-lookup"><span data-stu-id="90e92-470">Build and Deploy</span></span>

* <span data-ttu-id="90e92-471">Como antes, compile el proyecto en Unity e impleméntelo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e92-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="90e92-472">Una vez implementada la aplicación:</span><span class="sxs-lookup"><span data-stu-id="90e92-472">After the application is deployed:</span></span>

* <span data-ttu-id="90e92-473">Cara a una superficie (pared, piso, tabla) y decir *"Mostrar el mundo"* .</span><span class="sxs-lookup"><span data-stu-id="90e92-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="90e92-474">Se mostrará el submundo y se ocultarán todos los demás hologramas.</span><span class="sxs-lookup"><span data-stu-id="90e92-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="90e92-475">Si no ve el mundo, asegúrese de que se enfrenta a una superficie real.</span><span class="sxs-lookup"><span data-stu-id="90e92-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="90e92-476">Enfoque dentro de 1 medidor del holograma de submundo y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="90e92-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="90e92-477">Ahora hay efectos de audio aplicados a la voz.</span><span class="sxs-lookup"><span data-stu-id="90e92-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="90e92-478">Desactive el mundo y observe cómo ya no se aplica el efecto.</span><span class="sxs-lookup"><span data-stu-id="90e92-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="90e92-479">*"Oculte el mundo"* para ocultar el mundo.</span><span class="sxs-lookup"><span data-stu-id="90e92-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="90e92-480">El mundo se ocultará y los hologramas previamente ocultos volverán a aparecer.</span><span class="sxs-lookup"><span data-stu-id="90e92-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="90e92-481">Fin</span><span class="sxs-lookup"><span data-stu-id="90e92-481">The End</span></span>

<span data-ttu-id="90e92-482">Enhorabuena.</span><span class="sxs-lookup"><span data-stu-id="90e92-482">Congratulations!</span></span> <span data-ttu-id="90e92-483">Ahora ha completado el **Mr espacial 220: sonido espacial**.</span><span class="sxs-lookup"><span data-stu-id="90e92-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="90e92-484">Escuche el mundo y llévese sus experiencias con sonido.</span><span class="sxs-lookup"><span data-stu-id="90e92-484">Listen to the world and bring your experiences to life with sound!</span></span>
