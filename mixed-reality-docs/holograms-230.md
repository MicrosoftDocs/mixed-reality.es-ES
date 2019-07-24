---
title: MR espacial 230-asignación espacial
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de asignación espacial.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academia, tutorial, asignación espacial, reconstrucción superficial, malla
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993560"
---
>[!NOTE]
><span data-ttu-id="a4987-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="a4987-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a4987-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a4987-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a4987-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a4987-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a4987-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="a4987-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a4987-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a4987-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a4987-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="a4987-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="a4987-110">MR espacial 230: Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="a4987-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="a4987-111">La [asignación espacial](spatial-mapping.md) combina el mundo real y el mundo virtual juntos mediante la enseñanza de hologramas sobre el entorno.</span><span class="sxs-lookup"><span data-stu-id="a4987-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="a4987-112">En MR Spatial 230 (Project Planetarium), veremos cómo:</span><span class="sxs-lookup"><span data-stu-id="a4987-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="a4987-113">Examinar el entorno y transferir los datos desde HoloLens a su equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="a4987-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="a4987-114">Explore los sombreadores y aprenda a usarlos para visualizar el espacio.</span><span class="sxs-lookup"><span data-stu-id="a4987-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="a4987-115">Divida la malla de la habitación en planos simples mediante el procesamiento de malla.</span><span class="sxs-lookup"><span data-stu-id="a4987-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="a4987-116">Vaya más allá de las técnicas de selección de ubicación que hemos aprendido en los [conceptos básicos de MR 101](holograms-101.md)y proporcione comentarios sobre dónde se puede colocar un holograma en el entorno.</span><span class="sxs-lookup"><span data-stu-id="a4987-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="a4987-117">Explore los efectos de la oclusión, de modo que cuando el holograma esté detrás de un objeto del mundo real, todavía puede verlo con la visión x-Ray.</span><span class="sxs-lookup"><span data-stu-id="a4987-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="a4987-118">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a4987-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a4987-119">Recurso</span><span class="sxs-lookup"><span data-stu-id="a4987-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a4987-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a4987-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a4987-121"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="a4987-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a4987-122">MR espacial 230: Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="a4987-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="a4987-123">✔️</span><span class="sxs-lookup"><span data-stu-id="a4987-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a4987-124">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="a4987-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a4987-125">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a4987-125">Prerequisites</span></span>

* <span data-ttu-id="a4987-126">Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.</span><span class="sxs-lookup"><span data-stu-id="a4987-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="a4987-127">Funcionalidad básica C# de programación.</span><span class="sxs-lookup"><span data-stu-id="a4987-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="a4987-128">Debe haber completado los [principios básicos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="a4987-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="a4987-129">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="a4987-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="a4987-130">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="a4987-130">Project files</span></span>

* <span data-ttu-id="a4987-131">Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) requeridos por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="a4987-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="a4987-132"> Requiere Unity 2017,2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a4987-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="a4987-133">Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="a4987-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="a4987-134">Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="a4987-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="a4987-135">Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="a4987-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="a4987-136">Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.</span><span class="sxs-lookup"><span data-stu-id="a4987-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="a4987-137">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="a4987-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="a4987-138">Notas</span><span class="sxs-lookup"><span data-stu-id="a4987-138">Notes</span></span>

* <span data-ttu-id="a4987-139">"Habilitar Solo mi código" en Visual Studio debe estar deshabilitado *(* desactivado) en herramientas > opciones > depuración para poder alcanzar puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="a4987-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="a4987-140">Configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="a4987-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="a4987-141">Inicie **Unity**.</span><span class="sxs-lookup"><span data-stu-id="a4987-141">Start **Unity**.</span></span>
* <span data-ttu-id="a4987-142">Seleccione **nuevo** para crear un nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="a4987-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="a4987-143">Asigne al proyecto el nombre **Planetarium**.</span><span class="sxs-lookup"><span data-stu-id="a4987-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="a4987-144">Compruebe que está seleccionada la opción **3D** .</span><span class="sxs-lookup"><span data-stu-id="a4987-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="a4987-145">Haz clic en **Create Project** (Crear proyecto).</span><span class="sxs-lookup"><span data-stu-id="a4987-145">Click **Create Project**.</span></span>
* <span data-ttu-id="a4987-146">Una vez que se inicia Unity, vaya a **editar > configuración del proyecto > Player**.</span><span class="sxs-lookup"><span data-stu-id="a4987-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="a4987-147">En el panel **Inspector** , busque y seleccione el icono verde de la **tienda Windows** .</span><span class="sxs-lookup"><span data-stu-id="a4987-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="a4987-148">Expanda **otros valores**.</span><span class="sxs-lookup"><span data-stu-id="a4987-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="a4987-149">En la sección **representación** , active la opción se **admite la realidad virtual** .</span><span class="sxs-lookup"><span data-stu-id="a4987-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="a4987-150">Compruebe que **Windows Holographic** aparece en la lista de **SDK de realidad virtual**.</span><span class="sxs-lookup"><span data-stu-id="a4987-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="a4987-151">Si no es así, **+** Seleccione el botón situado en la parte inferior de la lista y elija **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="a4987-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="a4987-152">Expanda **configuración de publicación**.</span><span class="sxs-lookup"><span data-stu-id="a4987-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="a4987-153">En la sección **capacidades** , Compruebe la siguiente configuración:</span><span class="sxs-lookup"><span data-stu-id="a4987-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="a4987-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="a4987-154">InternetClientServer</span></span>
    * <span data-ttu-id="a4987-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="a4987-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="a4987-156">Micrófono</span><span class="sxs-lookup"><span data-stu-id="a4987-156">Microphone</span></span>
    * <span data-ttu-id="a4987-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="a4987-157">SpatialPerception</span></span>
* <span data-ttu-id="a4987-158">Vaya a **editar > configuración del proyecto > calidad**</span><span class="sxs-lookup"><span data-stu-id="a4987-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="a4987-159">En el panel **Inspector** , bajo el icono de la tienda Windows, seleccione la flecha de lista desplegable negra situada debajo de la fila "predeterminada" y cambie la configuración predeterminada a **muy baja**.</span><span class="sxs-lookup"><span data-stu-id="a4987-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="a4987-160">Vaya a **activos > importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="a4987-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="a4987-161">Vaya a la carpeta **. ..\holographicacademy-holograms-230-SpatialMapping\Starting** .</span><span class="sxs-lookup"><span data-stu-id="a4987-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="a4987-162">Haga clic en **Planetarium. unitypackage Tools**.</span><span class="sxs-lookup"><span data-stu-id="a4987-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="a4987-163">Haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="a4987-163">Click **Open**.</span></span>
* <span data-ttu-id="a4987-164">Debe aparecer una ventana **importar paquete Unity** , haga clic en el botón **importar** .</span><span class="sxs-lookup"><span data-stu-id="a4987-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="a4987-165">Espere a que Unity importe todos los recursos que se van a necesitar para completar este proyecto.</span><span class="sxs-lookup"><span data-stu-id="a4987-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="a4987-166">En el panel **jerarquía** , elimine la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="a4987-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="a4987-167">En el panel **proyecto** , en la carpeta **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** , busque el objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="a4987-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="a4987-168">Arrastre y coloque la **cámara principal** recurso prefabricado en el  panel de jerarquías.</span><span class="sxs-lookup"><span data-stu-id="a4987-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="a4987-169">En el panel **jerarquía** , elimine el objeto de **luz direccional** .</span><span class="sxs-lookup"><span data-stu-id="a4987-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="a4987-170">En el panel **proyecto** , carpeta **hologramas** , busque el objeto **cursor** .</span><span class="sxs-lookup"><span data-stu-id="a4987-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="a4987-171">Arrastre & Coloque el **cursor** recurso prefabricado en la **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="a4987-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="a4987-172">En el panel **jerarquía** , seleccione el objeto **cursor** .</span><span class="sxs-lookup"><span data-stu-id="a4987-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="a4987-173">En el panel **Inspector** , haga clic en la lista desplegable **capa** y seleccione **Editar capas.**</span><span class="sxs-lookup"><span data-stu-id="a4987-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="a4987-174">Nombre de la **capa de usuario 31** como "**SpatialMapping**".</span><span class="sxs-lookup"><span data-stu-id="a4987-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="a4987-175">Guarde la nueva escena: **Archivo > guardar la escena como...**</span><span class="sxs-lookup"><span data-stu-id="a4987-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="a4987-176">Haga clic en **nueva carpeta** y asigne un nombre a la carpeta Scenes.</span><span class="sxs-lookup"><span data-stu-id="a4987-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="a4987-177">Asigne al archivo el nombre "**Planetarium**" y guárdelo en  la carpeta Scenes.</span><span class="sxs-lookup"><span data-stu-id="a4987-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="a4987-178">Capítulo 1: exploración</span><span class="sxs-lookup"><span data-stu-id="a4987-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="a4987-179">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="a4987-179">**Objectives**</span></span>
* <span data-ttu-id="a4987-180">Obtenga información sobre SurfaceObserver y cómo su configuración afecta a la experiencia y el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a4987-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="a4987-181">Cree una experiencia de detección de salones para recopilar las mallas de su habitación.</span><span class="sxs-lookup"><span data-stu-id="a4987-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="a4987-182">**Las**</span><span class="sxs-lookup"><span data-stu-id="a4987-182">**Instructions**</span></span>
* <span data-ttu-id="a4987-183">En la carpeta **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** del panel de **proyecto** , busque el **SpatialMapping** recurso prefabricado.</span><span class="sxs-lookup"><span data-stu-id="a4987-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="a4987-184">Arrastre & Coloque el recurso prefabricado de **SpatialMapping** en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="a4987-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="a4987-185">**Compilación e implementación (parte 1)**</span><span class="sxs-lookup"><span data-stu-id="a4987-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="a4987-186">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="a4987-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="a4987-187">Haga clic en **Agregar escenas abiertas** para agregar la escena **Planetarium** a la compilación.</span><span class="sxs-lookup"><span data-stu-id="a4987-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="a4987-188">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="a4987-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="a4987-189">Establezca el **tipo de compilación** **SDK** en **universal 10** y UWP en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="a4987-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="a4987-190">Compruebe **los C# proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="a4987-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="a4987-191">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="a4987-191">Click **Build**.</span></span>
* <span data-ttu-id="a4987-192">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="a4987-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="a4987-193">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="a4987-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="a4987-194">Presione el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="a4987-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="a4987-195">Cuando Unity termine de compilar, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="a4987-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="a4987-196">Haga doble clic en la carpeta de la **aplicación** para abrirla.</span><span class="sxs-lookup"><span data-stu-id="a4987-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="a4987-197">Haga doble clic en **Planetarium. sln** para cargar el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4987-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="a4987-198">En Visual Studio, use la barra de herramientas superior para cambiar la configuración a **Release**.</span><span class="sxs-lookup"><span data-stu-id="a4987-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="a4987-199">Cambie la plataforma a **x86**.</span><span class="sxs-lookup"><span data-stu-id="a4987-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="a4987-200">Haga clic en la flecha desplegable situada a la derecha de "equipo local" y seleccione **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="a4987-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="a4987-201">Escriba la [dirección IP del dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) en el campo Dirección y cambie el modo de autenticación a **universal (protocolo sin cifrar)** .</span><span class="sxs-lookup"><span data-stu-id="a4987-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="a4987-202">Haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="a4987-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="a4987-203">Vea el panel de **salida** en Visual Studio para ver el estado de compilación e implementación.</span><span class="sxs-lookup"><span data-stu-id="a4987-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="a4987-204">Una vez que la aplicación se haya implementado, desplazarse por la habitación.</span><span class="sxs-lookup"><span data-stu-id="a4987-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="a4987-205">Verá las superficies circundantes que se incluyen en mallas de alambres en blanco y negro.</span><span class="sxs-lookup"><span data-stu-id="a4987-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="a4987-206">Digitalice su entorno.</span><span class="sxs-lookup"><span data-stu-id="a4987-206">Scan your surroundings.</span></span> <span data-ttu-id="a4987-207">Asegúrese de mirar paredes, techos y suelos.</span><span class="sxs-lookup"><span data-stu-id="a4987-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="a4987-208">**Compilación e implementación (parte 2)**</span><span class="sxs-lookup"><span data-stu-id="a4987-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="a4987-209">Ahora vamos a explorar cómo la asignación espacial puede afectar al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a4987-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="a4987-210">En Unity, seleccione **Window > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="a4987-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="a4987-211">Haga clic en **Agregar generador de perfiles > GPU**.</span><span class="sxs-lookup"><span data-stu-id="a4987-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="a4987-212">Haga clic en **Active <Enter IP>Profiler >** .</span><span class="sxs-lookup"><span data-stu-id="a4987-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="a4987-213">Escriba la **dirección IP** de su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a4987-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="a4987-214">Haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="a4987-214">Click **Connect**.</span></span>
* <span data-ttu-id="a4987-215">Observe el número de milisegundos que tarda la GPU en representar un fotograma.</span><span class="sxs-lookup"><span data-stu-id="a4987-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="a4987-216">Detenga la ejecución de la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4987-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="a4987-217">Vuelva a Visual Studio y Abra **SpatialMappingObserver.CS**.</span><span class="sxs-lookup"><span data-stu-id="a4987-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="a4987-218">Lo encontrará en la carpeta HoloToolkit\SpatialMapping del proyecto Assembly-CSharp (universal Windows).</span><span class="sxs-lookup"><span data-stu-id="a4987-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="a4987-219">Busque la función Activate **()** y agregue la siguiente línea de código: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="a4987-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="a4987-220">Vuelva a implementar el proyecto en el dispositivo y, a continuación, vuelva a **conectar el generador de perfiles**.</span><span class="sxs-lookup"><span data-stu-id="a4987-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="a4987-221">Observe el cambio en el número de milisegundos para representar un fotograma.</span><span class="sxs-lookup"><span data-stu-id="a4987-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="a4987-222">Detenga la ejecución de la aplicación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4987-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="a4987-223">**Guardar y cargar en Unity**</span><span class="sxs-lookup"><span data-stu-id="a4987-223">**Save and load in Unity**</span></span>

<span data-ttu-id="a4987-224">Por último, vamos a guardar la malla de sala y cargarla en Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="a4987-225">Vuelva a Visual Studio y quite la línea **TrianglesPerCubicMeter** que agregó en la función Activate **()** en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="a4987-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="a4987-226">Vuelva a implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4987-226">Redeploy the project to your device.</span></span> <span data-ttu-id="a4987-227">Ahora deberíamos ejecutarse con triángulos **500** por metro cúbico.</span><span class="sxs-lookup"><span data-stu-id="a4987-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="a4987-228">Abra un explorador y escriba en la dirección IP de HoloLens para ir al **portal de dispositivos de Windows**.</span><span class="sxs-lookup"><span data-stu-id="a4987-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="a4987-229">Seleccione la opción **vista 3D** en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="a4987-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="a4987-230">En **reconstrucción superficial** , seleccione el botón **Actualizar** .</span><span class="sxs-lookup"><span data-stu-id="a4987-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="a4987-231">Observe que las áreas que ha examinado en HoloLens aparecen en la ventana de visualización.</span><span class="sxs-lookup"><span data-stu-id="a4987-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="a4987-232">Presione el botón **Guardar** para guardar el análisis de la habitación.</span><span class="sxs-lookup"><span data-stu-id="a4987-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="a4987-233">Abra la  carpeta downloads para buscar el modelo Room **SRMesh. obj**guardado.</span><span class="sxs-lookup"><span data-stu-id="a4987-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="a4987-234">Copie **SRMesh. obj** en la carpeta **assets** del proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="a4987-235">En Unity, seleccione el objeto **SpatialMapping** en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="a4987-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="a4987-236">Busque el componente de **observador de superficie de objeto (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a4987-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="a4987-237">Haga clic en el círculo situado a la derecha de la propiedad **modelo Room** .</span><span class="sxs-lookup"><span data-stu-id="a4987-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="a4987-238">Busque y seleccione el objeto **SRMesh** y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="a4987-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="a4987-239">Compruebe que la propiedad **modelo de habitación** del panel **Inspector** está ahora establecida en **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="a4987-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="a4987-240">Presione el botón **reproducir** para entrar en el modo de vista previa de Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="a4987-241">El componente SpatialMapping cargará las mallas del modelo de habitación guardado para que pueda usarlas en Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="a4987-242">Cambie a la vista **escena** para ver todo el modelo de habitación mostrado con el sombreador de tramas de alambres.</span><span class="sxs-lookup"><span data-stu-id="a4987-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="a4987-243">Vuelva a presionar el botón **reproducir** para salir del modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="a4987-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="a4987-244">**NOTA:** La próxima vez que escriba el modo de vista previa en Unity, se cargará la malla de habitación guardada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="a4987-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="a4987-245">Capítulo 2: visualización</span><span class="sxs-lookup"><span data-stu-id="a4987-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="a4987-246">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="a4987-246">**Objectives**</span></span>
* <span data-ttu-id="a4987-247">Conozca los aspectos básicos de los sombreadores.</span><span class="sxs-lookup"><span data-stu-id="a4987-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="a4987-248">Visualice su entorno.</span><span class="sxs-lookup"><span data-stu-id="a4987-248">Visualize your surroundings.</span></span>

<span data-ttu-id="a4987-249">**Las**</span><span class="sxs-lookup"><span data-stu-id="a4987-249">**Instructions**</span></span>
* <span data-ttu-id="a4987-250">En el panel  de jerarquías de Unity, seleccione el objeto **SpatialMapping** .</span><span class="sxs-lookup"><span data-stu-id="a4987-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="a4987-251">En el panel **Inspector** , busque el componente **Administrador de asignación espacial (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a4987-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="a4987-252">Haga clic en el círculo situado a la derecha de la propiedad material de la **superficie** .</span><span class="sxs-lookup"><span data-stu-id="a4987-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="a4987-253">Busque y seleccione el material **BlueLinesOnWalls** y cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="a4987-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="a4987-254">En la carpeta **sombreadores** del panel de **proyecto** , haga doble clic en **BlueLinesOnWalls** para abrir el sombreador en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4987-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="a4987-255">Se trata de un sombreador de píxeles sencillo (vértice a fragmento), que realiza las tareas siguientes:</span><span class="sxs-lookup"><span data-stu-id="a4987-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="a4987-256">Convierte la ubicación de un vértice en el espacio universal.</span><span class="sxs-lookup"><span data-stu-id="a4987-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="a4987-257">Comprueba la normal del vértice para determinar si un píxel es vertical.</span><span class="sxs-lookup"><span data-stu-id="a4987-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="a4987-258">Establece el color del píxel que se va a representar.</span><span class="sxs-lookup"><span data-stu-id="a4987-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="a4987-259">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="a4987-259">**Build and Deploy**</span></span>
* <span data-ttu-id="a4987-260">Vuelva a Unity y presione **reproducir** para entrar en el modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="a4987-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="a4987-261">Las líneas azules se representarán en todas las superficies verticales de la malla de habitación (que se cargan automáticamente a partir de los datos de exámenes guardados).</span><span class="sxs-lookup"><span data-stu-id="a4987-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="a4987-262">Cambie a la pestaña **escena** para ajustar la vista de la habitación y ver cómo aparece toda la malla de habitación en Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="a4987-263">En el panel **proyecto** , busque la carpeta **materiales** y seleccione el material **BlueLinesOnWalls** .</span><span class="sxs-lookup"><span data-stu-id="a4987-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="a4987-264">Modifique algunas propiedades y vea cómo aparecen los cambios en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="a4987-265">En el panel **Inspector** , ajuste el valor **LineScale** para que las líneas aparezcan más gruesas o más delgadas.</span><span class="sxs-lookup"><span data-stu-id="a4987-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="a4987-266">En el panel **Inspector** , ajuste el valor **LinesPerMeter** para cambiar el número de líneas que aparecen en cada muro.</span><span class="sxs-lookup"><span data-stu-id="a4987-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="a4987-267">Haga clic en **reproducir** de nuevo para salir del modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="a4987-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="a4987-268">Compile e implemente en HoloLens y observe cómo aparece la representación del sombreador en superficies reales.</span><span class="sxs-lookup"><span data-stu-id="a4987-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="a4987-269">Unity hace un gran trabajo de obtener una vista previa de los materiales, pero siempre es una buena idea desproteger la representación en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a4987-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="a4987-270">Capítulo 3: procesamiento</span><span class="sxs-lookup"><span data-stu-id="a4987-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="a4987-271">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="a4987-271">**Objectives**</span></span>
* <span data-ttu-id="a4987-272">Aprenda técnicas para procesar datos de asignación espacial para su uso en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a4987-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="a4987-273">Analizar datos de asignación espacial para buscar planos y Quitar triángulos.</span><span class="sxs-lookup"><span data-stu-id="a4987-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="a4987-274">Usar planos para la colocación de hologramas.</span><span class="sxs-lookup"><span data-stu-id="a4987-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="a4987-275">**Las**</span><span class="sxs-lookup"><span data-stu-id="a4987-275">**Instructions**</span></span>
* <span data-ttu-id="a4987-276">En el panel de **proyectos** de Unity, carpeta **hologramas** , busque el objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="a4987-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a4987-277">Arrastre & Coloque el objeto **SpatialProcessing** en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="a4987-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="a4987-278">SpatialProcessing recurso prefabricado incluye componentes para procesar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="a4987-279">**SurfaceMeshesToPlanes.CS** buscará y generará planos basados en los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="a4987-280">Usaremos planos en nuestra aplicación para representar paredes, suelos y techos.</span><span class="sxs-lookup"><span data-stu-id="a4987-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="a4987-281">Este recurso prefabricado también incluye **RemoveSurfaceVertices.CS** , que puede quitar vértices de la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="a4987-282">Se puede usar para crear huecos en la malla o para quitar los triángulos sobrantes que ya no son necesarios (porque en su lugar se pueden usar planos).</span><span class="sxs-lookup"><span data-stu-id="a4987-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="a4987-283">En el panel de **proyectos** de Unity, carpeta **hologramas** , busque el objeto **SpaceCollection** .</span><span class="sxs-lookup"><span data-stu-id="a4987-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="a4987-284">Arrastre y coloque el objeto **SpaceCollection** en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="a4987-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="a4987-285">En el panel **jerarquía** , seleccione el objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="a4987-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a4987-286">En el panel **Inspector** , busque el componente de **Administrador de espacio de reproducción (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a4987-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="a4987-287">Haga doble clic en **PlaySpaceManager.CS** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4987-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="a4987-288">PlaySpaceManager.cs contiene código específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a4987-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="a4987-289">Agregaremos funcionalidad a este script para habilitar el comportamiento siguiente:</span><span class="sxs-lookup"><span data-stu-id="a4987-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="a4987-290">Detener la recopilación de datos de asignación espacial después de superar el límite de tiempo de examen (10 segundos).</span><span class="sxs-lookup"><span data-stu-id="a4987-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="a4987-291">Procesar los datos de asignación espacial:</span><span class="sxs-lookup"><span data-stu-id="a4987-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="a4987-292">Use SurfaceMeshesToPlanes para crear una representación más sencilla del mundo como planos (paredes, suelos, techos, etc.).</span><span class="sxs-lookup"><span data-stu-id="a4987-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="a4987-293">Use RemoveSurfaceVertices para quitar los triángulos de superficie que se encuentran dentro de los límites del plano.</span><span class="sxs-lookup"><span data-stu-id="a4987-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="a4987-294">Generar una colección de hologramas en el mundo y colocarlos en planos murales y en planta cercanos al usuario.</span><span class="sxs-lookup"><span data-stu-id="a4987-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="a4987-295">Complete los ejercicios de codificación marcados en PlaySpaceManager.cs o reemplace el script por la solución terminada que aparece a continuación:</span><span class="sxs-lookup"><span data-stu-id="a4987-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="a4987-296">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="a4987-296">**Build and Deploy**</span></span>
* <span data-ttu-id="a4987-297">Antes de implementar en HoloLens, presione el botón **reproducir** en Unity para entrar en el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="a4987-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="a4987-298">Después de cargar la malla de sala desde el archivo, espere 10 segundos antes de que se inicie el procesamiento en la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="a4987-299">Una vez completado el procesamiento, aparecerán los planos para representar el suelo, las paredes, el límite superior, etc.</span><span class="sxs-lookup"><span data-stu-id="a4987-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="a4987-300">Una vez que se hayan encontrado todos los planos, debería ver que aparece un sistema solar en una tabla de piso cerca de la cámara.</span><span class="sxs-lookup"><span data-stu-id="a4987-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="a4987-301">También deberían aparecer dos pósteres en las paredes cerca de la cámara.</span><span class="sxs-lookup"><span data-stu-id="a4987-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="a4987-302">Cambie a la pestaña **escena** si no puede verla en el modo de **juego** .</span><span class="sxs-lookup"><span data-stu-id="a4987-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="a4987-303">Vuelva a presionar el botón **reproducir** para salir del modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="a4987-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="a4987-304">Compilar e implementar en HoloLens, como de costumbre.</span><span class="sxs-lookup"><span data-stu-id="a4987-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="a4987-305">Espere a que se complete el análisis y el procesamiento de los datos de la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="a4987-306">Una vez que vea los planos, intente encontrar el sistema solar y los pósteres de su mundo.</span><span class="sxs-lookup"><span data-stu-id="a4987-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="a4987-307">Capítulo 4: selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="a4987-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="a4987-308">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="a4987-308">**Objectives**</span></span>
* <span data-ttu-id="a4987-309">Determine si un holograma se ajustará en una superficie.</span><span class="sxs-lookup"><span data-stu-id="a4987-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="a4987-310">Proporcione comentarios al usuario cuando un holograma pueda o no quepa en una superficie.</span><span class="sxs-lookup"><span data-stu-id="a4987-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="a4987-311">**Las**</span><span class="sxs-lookup"><span data-stu-id="a4987-311">**Instructions**</span></span>
* <span data-ttu-id="a4987-312">En el panel  de jerarquías de Unity, seleccione el objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="a4987-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a4987-313">En el panel **Inspector** , busque el componente de mallas de **superficie en los planos (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a4987-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="a4987-314">Cambie la propiedad **Draw aviones** a **Nothing** para borrar la selección.</span><span class="sxs-lookup"><span data-stu-id="a4987-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="a4987-315">Cambie la propiedad **Draw aviones** a **Wall**para que solo se representen los planos de pared.</span><span class="sxs-lookup"><span data-stu-id="a4987-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="a4987-316">En el panel **proyecto** , en la carpeta **scripts** , haga doble clic en **placeable.CS** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4987-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="a4987-317">El script que se pueda **colocar** ya está adjunto a los pósters y al cuadro de proyección que se crearon una vez completada la búsqueda de planos.</span><span class="sxs-lookup"><span data-stu-id="a4987-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="a4987-318">Lo único que debemos hacer es quitar la marca de comentario de código y este script logrará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a4987-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="a4987-319">Determine si un holograma se ajustará en una superficie raycasting desde el centro y cuatro esquinas del cubo de límite.</span><span class="sxs-lookup"><span data-stu-id="a4987-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="a4987-320">Compruebe la superficie normal para determinar si es lo suficientemente suave para que el holograma permanezca en el vaciado.</span><span class="sxs-lookup"><span data-stu-id="a4987-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="a4987-321">Representa un cubo de límite alrededor del holograma para mostrar su tamaño real mientras se coloca.</span><span class="sxs-lookup"><span data-stu-id="a4987-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="a4987-322">Convierta una sombra debajo/detrás del holograma para mostrar dónde se colocará en el piso o la pared.</span><span class="sxs-lookup"><span data-stu-id="a4987-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="a4987-323">Representa la sombra en rojo si el holograma no se puede colocar en la superficie, o en verde, si es posible.</span><span class="sxs-lookup"><span data-stu-id="a4987-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="a4987-324">Vuelva a orientar el holograma para alinearlo con el tipo de superficie (vertical u horizontal) al que tiene afinidad.</span><span class="sxs-lookup"><span data-stu-id="a4987-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="a4987-325">Coloque suavemente el holograma en la superficie seleccionada para evitar saltar o ajustar el comportamiento.</span><span class="sxs-lookup"><span data-stu-id="a4987-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="a4987-326">Quite la marca de comentario de todo el código del ejercicio de codificación siguiente o use esta solución completada en **placeable.CS**:</span><span class="sxs-lookup"><span data-stu-id="a4987-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="a4987-327">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="a4987-327">**Build and Deploy**</span></span>
* <span data-ttu-id="a4987-328">Como antes, compile el proyecto e impleméntelo en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a4987-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="a4987-329">Espere a que se complete el análisis y el procesamiento de los datos de la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="a4987-330">Cuando vea el sistema solar, mira en el cuadro proyección siguiente y realiza un gesto de selección para moverlo.</span><span class="sxs-lookup"><span data-stu-id="a4987-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="a4987-331">Mientras se selecciona el cuadro proyección, un cubo de límite estará visible alrededor del cuadro de proyección.</span><span class="sxs-lookup"><span data-stu-id="a4987-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="a4987-332">Desplácese hacia mira en una ubicación diferente de la habitación.</span><span class="sxs-lookup"><span data-stu-id="a4987-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="a4987-333">El cuadro proyección debe seguir su mirada.</span><span class="sxs-lookup"><span data-stu-id="a4987-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="a4987-334">Cuando la sombra situada debajo del cuadro proyección se vuelve roja, no se puede colocar el holograma en esa superficie.</span><span class="sxs-lookup"><span data-stu-id="a4987-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="a4987-335">Cuando la sombra situada debajo del cuadro proyección se vuelve verde, puede colocar el holograma realizando otro gesto seleccionar.</span><span class="sxs-lookup"><span data-stu-id="a4987-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="a4987-336">Busque y seleccione uno de los pósteres holográficas en una pared para moverlo a una nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="a4987-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="a4987-337">Tenga en cuenta que no puede colocar el póster en el piso o el límite superior, y que permanece correctamente orientado a cada pared mientras se desplaza.</span><span class="sxs-lookup"><span data-stu-id="a4987-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="a4987-338">Capítulo 5: oclusión</span><span class="sxs-lookup"><span data-stu-id="a4987-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="a4987-339">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="a4987-339">**Objectives**</span></span>
* <span data-ttu-id="a4987-340">Determine si la malla de asignación espacial ocluidos un holograma.</span><span class="sxs-lookup"><span data-stu-id="a4987-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="a4987-341">Aplique distintas técnicas de oclusión para lograr un efecto divertido.</span><span class="sxs-lookup"><span data-stu-id="a4987-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="a4987-342">**Las**</span><span class="sxs-lookup"><span data-stu-id="a4987-342">**Instructions**</span></span>

<span data-ttu-id="a4987-343">En primer lugar, vamos a permitir que la malla de asignación espacial tapaba otros hologramas sin occluding el mundo real:</span><span class="sxs-lookup"><span data-stu-id="a4987-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="a4987-344">En el panel **jerarquía** , seleccione el objeto **SpatialProcessing** .</span><span class="sxs-lookup"><span data-stu-id="a4987-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="a4987-345">En el panel **Inspector** , busque el componente de **Administrador de espacio de reproducción (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a4987-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="a4987-346">Haga clic en el círculo situado a la derecha de la propiedad **material secundario** .</span><span class="sxs-lookup"><span data-stu-id="a4987-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="a4987-347">Busque y seleccione el material de **oclusión** y cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="a4987-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="a4987-348">A continuación, vamos a agregar un comportamiento especial a la tierra, de modo que tenga un resaltado azul cada vez que se ocluidos por otro holograma (por ejemplo, el sol) o por la malla de asignación espacial:</span><span class="sxs-lookup"><span data-stu-id="a4987-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="a4987-349">En el panel **proyecto** , en la carpeta **hologramas** , expanda el objeto **SolarSystem** .</span><span class="sxs-lookup"><span data-stu-id="a4987-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="a4987-350">Haga clic en **tierra**.</span><span class="sxs-lookup"><span data-stu-id="a4987-350">Click on **Earth**.</span></span>
* <span data-ttu-id="a4987-351">En el panel **Inspector** , busque el material de la tierra (componente inferior).</span><span class="sxs-lookup"><span data-stu-id="a4987-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="a4987-352">En el **menú desplegable**del sombreador, cambie el sombreador a **personalizado > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="a4987-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="a4987-353">Esto representará un resaltado azul alrededor de tierra siempre que se ocluidos por otro objeto.</span><span class="sxs-lookup"><span data-stu-id="a4987-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="a4987-354">Por último, vamos a habilitar un efecto x-Ray Vision para los planetas de nuestro sistema solar.</span><span class="sxs-lookup"><span data-stu-id="a4987-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="a4987-355">Tendremos que editar **PlanetOcclusion.CS** (que se encuentra en la carpeta Scripts\SolarSystem) para lograr lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a4987-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="a4987-356">Determinar si el nivel de SpatialMapping (mallas y planos de la habitación) ocluidos un planeta.</span><span class="sxs-lookup"><span data-stu-id="a4987-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="a4987-357">Muestra la representación en alambre de un planeta siempre que se ocluidos por el nivel de SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="a4987-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="a4987-358">Oculte la representación en alambre de un planeta cuando no esté bloqueada por el nivel SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="a4987-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="a4987-359">Siga el ejercicio de codificación de PlanetOcclusion.cs o use la siguiente solución:</span><span class="sxs-lookup"><span data-stu-id="a4987-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="a4987-360">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="a4987-360">**Build and Deploy**</span></span>
* <span data-ttu-id="a4987-361">Compile e implemente la aplicación en HoloLens, como de costumbre.</span><span class="sxs-lookup"><span data-stu-id="a4987-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="a4987-362">Espere a que se completen el análisis y el procesamiento de los datos de la asignación espacial (debe ver que aparecen líneas azules en las paredes).</span><span class="sxs-lookup"><span data-stu-id="a4987-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="a4987-363">Busque y seleccione el cuadro proyección del sistema solar y, a continuación, establezca el cuadro junto a una pared o detrás de un contador.</span><span class="sxs-lookup"><span data-stu-id="a4987-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="a4987-364">Para ver la oclusión básica, oculte las superficies detrás del mismo nivel en el póster o en el cuadro de proyección.</span><span class="sxs-lookup"><span data-stu-id="a4987-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="a4987-365">Busque la tierra; debe haber un efecto de resaltado azul cada vez que se encuentre detrás de otro holograma o superficie.</span><span class="sxs-lookup"><span data-stu-id="a4987-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="a4987-366">Observe que los planetas se mueven detrás de la pared u otras superficies de la habitación.</span><span class="sxs-lookup"><span data-stu-id="a4987-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="a4987-367">Ahora tiene una visión de rayos x y puede ver sus esqueletos de alambres.</span><span class="sxs-lookup"><span data-stu-id="a4987-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="a4987-368">Fin</span><span class="sxs-lookup"><span data-stu-id="a4987-368">The End</span></span>

<span data-ttu-id="a4987-369">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="a4987-369">Congratulations!</span></span> <span data-ttu-id="a4987-370">Ahora ha completado **el Mr espacial 230: Asignación**espacial.</span><span class="sxs-lookup"><span data-stu-id="a4987-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="a4987-371">Sabe cómo analizar el entorno y cargar datos de asignación espacial en Unity.</span><span class="sxs-lookup"><span data-stu-id="a4987-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="a4987-372">Comprende los aspectos básicos de los sombreadores y cómo se pueden usar los materiales para volver a visualizar el mundo.</span><span class="sxs-lookup"><span data-stu-id="a4987-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="a4987-373">Ha aprendido las nuevas técnicas de procesamiento para buscar planos y Quitar triángulos de una malla.</span><span class="sxs-lookup"><span data-stu-id="a4987-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="a4987-374">Puede trasladar y colocar hologramas en superficies que tengan sentido.</span><span class="sxs-lookup"><span data-stu-id="a4987-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="a4987-375">Ha experimentado diferentes técnicas de oclusión y ha aprovechado la potencia de la visión de rayos x.</span><span class="sxs-lookup"><span data-stu-id="a4987-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
