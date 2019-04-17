---
title: El Sr. espacial 230 - asignación espacial
description: Siga este tutorial con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de asignación espacial de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, asignación espacial, reconstrucción expuesta, malla
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600927"
---
>[!NOTE]
><span data-ttu-id="da92b-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="da92b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="da92b-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="da92b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="da92b-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="da92b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="da92b-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="da92b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="da92b-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="da92b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="da92b-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="da92b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="da92b-110">MR 230 espacial: Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="da92b-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="da92b-111">[Asignación espacial](spatial-mapping.md) combina el mundo real y el mundo virtual juntos enseñanza hologramas sobre el entorno.</span><span class="sxs-lookup"><span data-stu-id="da92b-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="da92b-112">En el Sr. espacial 230 (apartado planetario del proyecto y disfrutará), obtendrá información sobre cómo:</span><span class="sxs-lookup"><span data-stu-id="da92b-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="da92b-113">Analizar los datos de entorno y la transferencia de la HoloLens a la máquina de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="da92b-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="da92b-114">Explore los sombreadores y obtenga información sobre cómo usarlas para visualizar el espacio.</span><span class="sxs-lookup"><span data-stu-id="da92b-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="da92b-115">Desglosar la malla del salón en planos simple mediante el procesamiento de la malla.</span><span class="sxs-lookup"><span data-stu-id="da92b-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="da92b-116">Vaya más allá de las técnicas de selección de ubicación que hemos aprendido en [MR Fundamentos 101](holograms-101.md)y proporcionar comentarios sobre dónde se puede colocar un holograma en el entorno.</span><span class="sxs-lookup"><span data-stu-id="da92b-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="da92b-117">Explore los efectos de oclusión, por lo que cuando su holograma está detrás de un objeto del mundo real, todavía puede ver con la visión de rayos x!</span><span class="sxs-lookup"><span data-stu-id="da92b-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="da92b-118">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="da92b-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="da92b-119">Curso</span><span class="sxs-lookup"><span data-stu-id="da92b-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="da92b-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="da92b-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="da92b-121"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="da92b-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="da92b-122">MR 230 espacial: Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="da92b-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="da92b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="da92b-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="da92b-124">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="da92b-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="da92b-125">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="da92b-125">Prerequisites</span></span>

* <span data-ttu-id="da92b-126">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="da92b-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="da92b-127">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="da92b-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="da92b-128">Debe haber completado [MR Fundamentos 101](holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="da92b-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="da92b-129">Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="da92b-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="da92b-130">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="da92b-130">Project files</span></span>

* <span data-ttu-id="da92b-131">Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) requerida por el proyecto.</span><span class="sxs-lookup"><span data-stu-id="da92b-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="da92b-132"> Requiere Unity 2017.2 o posterior.</span><span class="sxs-lookup"><span data-stu-id="da92b-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="da92b-133">Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span><span class="sxs-lookup"><span data-stu-id="da92b-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="da92b-134">Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span><span class="sxs-lookup"><span data-stu-id="da92b-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="da92b-135">Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span><span class="sxs-lookup"><span data-stu-id="da92b-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="da92b-136">Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="da92b-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="da92b-137">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span><span class="sxs-lookup"><span data-stu-id="da92b-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="da92b-138">Notas</span><span class="sxs-lookup"><span data-stu-id="da92b-138">Notes</span></span>

* <span data-ttu-id="da92b-139">"Habilitar Solo mi código" en Visual Studio debe estar deshabilitada (*unchecked*) en Herramientas > Opciones > depuración con el fin de alcanzar los puntos de interrupción en el código.</span><span class="sxs-lookup"><span data-stu-id="da92b-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="da92b-140">Programa de instalación de Unity</span><span class="sxs-lookup"><span data-stu-id="da92b-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="da92b-141">Iniciar **Unity**.</span><span class="sxs-lookup"><span data-stu-id="da92b-141">Start **Unity**.</span></span>
* <span data-ttu-id="da92b-142">Seleccione **New** para crear un nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="da92b-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="da92b-143">Denomine el proyecto **planetario y disfrutará**.</span><span class="sxs-lookup"><span data-stu-id="da92b-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="da92b-144">Compruebe que la **3D** está seleccionada.</span><span class="sxs-lookup"><span data-stu-id="da92b-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="da92b-145">Haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="da92b-145">Click **Create Project**.</span></span>
* <span data-ttu-id="da92b-146">Una vez que se inicia en Unity, vaya a **Editar > configuración del proyecto > Reproductor**.</span><span class="sxs-lookup"><span data-stu-id="da92b-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="da92b-147">En el **Inspector** panel, busque y seleccione el color verde **Windows Store** icono.</span><span class="sxs-lookup"><span data-stu-id="da92b-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="da92b-148">Expanda **otras configuraciones**.</span><span class="sxs-lookup"><span data-stu-id="da92b-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="da92b-149">En el **representación** sección, compruebe el **admite la realidad Virtual** opción.</span><span class="sxs-lookup"><span data-stu-id="da92b-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="da92b-150">Compruebe que **Windows Holographic** aparece en la lista de **SDK de realidad Virtual**.</span><span class="sxs-lookup"><span data-stu-id="da92b-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="da92b-151">Si no, seleccione el **+** situado en la parte inferior de la lista y elija **Windows Holographic**.</span><span class="sxs-lookup"><span data-stu-id="da92b-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="da92b-152">Expanda **configuración de publicación**.</span><span class="sxs-lookup"><span data-stu-id="da92b-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="da92b-153">En el **capacidades** sección, compruebe la configuración siguiente:</span><span class="sxs-lookup"><span data-stu-id="da92b-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="da92b-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="da92b-154">InternetClientServer</span></span>
    * <span data-ttu-id="da92b-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="da92b-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="da92b-156">Micrófono</span><span class="sxs-lookup"><span data-stu-id="da92b-156">Microphone</span></span>
    * <span data-ttu-id="da92b-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="da92b-157">SpatialPerception</span></span>
* <span data-ttu-id="da92b-158">Vaya a **Editar > configuración del proyecto > calidad**</span><span class="sxs-lookup"><span data-stu-id="da92b-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="da92b-159">En el **Inspector** panel, bajo el icono de Windows Store, seleccione la flecha de lista desplegable negra en la fila "Default" y cambie la configuración predeterminada para **Fastest**.</span><span class="sxs-lookup"><span data-stu-id="da92b-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Fastest**.</span></span>
* <span data-ttu-id="da92b-160">Vaya a **activos > Importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="da92b-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="da92b-161">Navegue hasta la **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** carpeta.</span><span class="sxs-lookup"><span data-stu-id="da92b-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="da92b-162">Haga clic en **Planetarium.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="da92b-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="da92b-163">Haga clic en **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="da92b-163">Click **Open**.</span></span>
* <span data-ttu-id="da92b-164">Un **Importar paquete de Unity** debe aparecer la ventana, haga clic en el **importación** botón.</span><span class="sxs-lookup"><span data-stu-id="da92b-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="da92b-165">Espere a que Unity importar todos los recursos que necesitamos para completar este proyecto.</span><span class="sxs-lookup"><span data-stu-id="da92b-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="da92b-166">En el **jerarquía** panel, elimine el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="da92b-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="da92b-167">En el **proyecto** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** carpeta, busque la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="da92b-168">Arrastre y coloque el **cámara principal** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="da92b-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="da92b-169">En el **jerarquía** panel, elimine el **luz direccional** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="da92b-170">En el **proyecto** panel, **hologramas** carpeta, busque la **Cursor** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="da92b-171">Arrastrar y colocar la **Cursor** prefabricado en el **jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="da92b-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="da92b-172">En el **jerarquía** panel, seleccione el **Cursor** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="da92b-173">En el **Inspector** del panel, haga clic en el **capa** hacia abajo y seleccione **capas editar...** .</span><span class="sxs-lookup"><span data-stu-id="da92b-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="da92b-174">Nombre **usuario capa 31** como "**SpatialMapping**".</span><span class="sxs-lookup"><span data-stu-id="da92b-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="da92b-175">Guarde la nueva escena: **Archivo > Guardar escena como...**</span><span class="sxs-lookup"><span data-stu-id="da92b-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="da92b-176">Haga clic en **nueva carpeta** y el nombre de la carpeta **escenas**.</span><span class="sxs-lookup"><span data-stu-id="da92b-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="da92b-177">Nombre del archivo "**planetario y disfrutará**" y guárdela en el **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="da92b-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="da92b-178">Capítulo 1: examen</span><span class="sxs-lookup"><span data-stu-id="da92b-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="da92b-179">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="da92b-179">**Objectives**</span></span>
* <span data-ttu-id="da92b-180">Obtenga información sobre la SurfaceObserver y cómo su impacto de la configuración de la experiencia y el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="da92b-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="da92b-181">Crear un salón de experiencia para recopilar las mallas de su sala de análisis.</span><span class="sxs-lookup"><span data-stu-id="da92b-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="da92b-182">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="da92b-182">**Instructions**</span></span>
* <span data-ttu-id="da92b-183">En el **proyecto** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** carpeta, busque la **SpatialMapping** prefabricado.</span><span class="sxs-lookup"><span data-stu-id="da92b-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="da92b-184">Arrastrar y colocar la **SpatialMapping** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="da92b-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="da92b-185">**Compilar e implementar (parte 1)**</span><span class="sxs-lookup"><span data-stu-id="da92b-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="da92b-186">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="da92b-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="da92b-187">Haga clic en **agregar escenas abierto** para agregar la **planetario y disfrutará** escena a la compilación.</span><span class="sxs-lookup"><span data-stu-id="da92b-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="da92b-188">Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="da92b-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="da92b-189">Establecer **SDK** a **10 Universal** y **tipo de compilación UWP** a **D3D**.</span><span class="sxs-lookup"><span data-stu-id="da92b-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="da92b-190">Comprobar **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="da92b-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="da92b-191">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="da92b-191">Click **Build**.</span></span>
* <span data-ttu-id="da92b-192">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="da92b-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="da92b-193">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="da92b-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="da92b-194">Presione el **Seleccionar carpeta** botón.</span><span class="sxs-lookup"><span data-stu-id="da92b-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="da92b-195">Cuando se hace Unity compilar, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="da92b-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="da92b-196">Haga doble clic en el **aplicación** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="da92b-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="da92b-197">Haga doble clic en **Planetarium.sln** para cargar el proyecto en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da92b-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="da92b-198">En Visual Studio, utilice la barra de herramientas superior para cambiar la configuración a **versión**.</span><span class="sxs-lookup"><span data-stu-id="da92b-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="da92b-199">Cambiar la plataforma a **x86**.</span><span class="sxs-lookup"><span data-stu-id="da92b-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="da92b-200">Haga clic en la flecha desplegable a la derecha de la «Máquina Local» y seleccione **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="da92b-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="da92b-201">Escriba [dirección IP de su dispositivo](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) en la dirección de campo y cambiar el modo de autenticación a **Universal (protocolo sin cifrar)**.</span><span class="sxs-lookup"><span data-stu-id="da92b-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="da92b-202">Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="da92b-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="da92b-203">Inspección del **salida** panel en Visual Studio para la compilación y el estado de la implementación.</span><span class="sxs-lookup"><span data-stu-id="da92b-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="da92b-204">Una vez que se ha implementado la aplicación, caminar alrededor de la sala.</span><span class="sxs-lookup"><span data-stu-id="da92b-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="da92b-205">Verá las superficies que lo rodea cubiertas por las mallas de tramas de alambres en blanco y negro.</span><span class="sxs-lookup"><span data-stu-id="da92b-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="da92b-206">Analizar respecto a su entorno.</span><span class="sxs-lookup"><span data-stu-id="da92b-206">Scan your surroundings.</span></span> <span data-ttu-id="da92b-207">No olvide mirar paredes, los límites máximos y los pisos.</span><span class="sxs-lookup"><span data-stu-id="da92b-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="da92b-208">**Compilar e implementar (parte 2)**</span><span class="sxs-lookup"><span data-stu-id="da92b-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="da92b-209">Ahora veamos cómo puede afectar la asignación espacial al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="da92b-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="da92b-210">En Unity, seleccione **Ventana > Profiler**.</span><span class="sxs-lookup"><span data-stu-id="da92b-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="da92b-211">Haga clic en **agregar Profiler > GPU**.</span><span class="sxs-lookup"><span data-stu-id="da92b-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="da92b-212">Haga clic en **Profiler Active > <Enter IP>** .</span><span class="sxs-lookup"><span data-stu-id="da92b-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="da92b-213">Escriba el **dirección IP** de su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="da92b-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="da92b-214">Haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="da92b-214">Click **Connect**.</span></span>
* <span data-ttu-id="da92b-215">Observe el número de milisegundos que tarda la GPU representar un fotograma.</span><span class="sxs-lookup"><span data-stu-id="da92b-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="da92b-216">Detener la aplicación se ejecute en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="da92b-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="da92b-217">Vuelva a Visual Studio y abra **SpatialMappingObserver.cs**.</span><span class="sxs-lookup"><span data-stu-id="da92b-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="da92b-218">La encontrará en la carpeta HoloToolkit\SpatialMapping del proyecto de ensamblado-CSharp (Windows Universal).</span><span class="sxs-lookup"><span data-stu-id="da92b-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="da92b-219">Buscar el **Awake()** funcione y agregue la siguiente línea de código: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="da92b-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="da92b-220">Volver a implementar el proyecto en el dispositivo y, a continuación, **volver a conectar el generador de perfiles**.</span><span class="sxs-lookup"><span data-stu-id="da92b-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="da92b-221">Observe el cambio en el número de milisegundos para representar un fotograma.</span><span class="sxs-lookup"><span data-stu-id="da92b-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="da92b-222">Detener la aplicación se ejecute en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="da92b-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="da92b-223">**Guardar y cargar en Unity**</span><span class="sxs-lookup"><span data-stu-id="da92b-223">**Save and load in Unity**</span></span>

<span data-ttu-id="da92b-224">Por último, vamos a guardar la malla de la sala y cargarlos en Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="da92b-225">Vuelva a Visual Studio y quitar el **TrianglesPerCubicMeter** línea que agregó en el **Awake()** función durante la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="da92b-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="da92b-226">Volver a implementar el proyecto en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="da92b-226">Redeploy the project to your device.</span></span> <span data-ttu-id="da92b-227">Nos debemos estar ejecutando con **500** triángulos por medidor cúbica.</span><span class="sxs-lookup"><span data-stu-id="da92b-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="da92b-228">Abra un explorador y escriba en su HoloLens IPAddress para navegar hasta el **Windows Device Portal**.</span><span class="sxs-lookup"><span data-stu-id="da92b-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="da92b-229">Seleccione el **vista 3D** opción en el panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="da92b-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="da92b-230">En **reconstrucción de superficie** seleccione la **actualización** botón.</span><span class="sxs-lookup"><span data-stu-id="da92b-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="da92b-231">Vea en las áreas que se han analizado en su HoloLens aparecen en la ventana de presentación.</span><span class="sxs-lookup"><span data-stu-id="da92b-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="da92b-232">Para guardar el examen de la sala, presione el **guardar** botón.</span><span class="sxs-lookup"><span data-stu-id="da92b-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="da92b-233">Abra su **descargas** carpeta para encontrar el modelo guardado sala **SRMesh.obj**.</span><span class="sxs-lookup"><span data-stu-id="da92b-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="da92b-234">Copia **SRMesh.obj** a la **activos** carpeta del proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="da92b-235">En Unity, seleccione el **SpatialMapping** objeto en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="da92b-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="da92b-236">Busque el **objeto observador de superficie (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="da92b-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="da92b-237">Haga clic en el círculo situado a la derecha de la **sala modelo** propiedad.</span><span class="sxs-lookup"><span data-stu-id="da92b-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="da92b-238">Busque y seleccione el **SRMesh** objeto y, a continuación, cierre la ventana.</span><span class="sxs-lookup"><span data-stu-id="da92b-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="da92b-239">Compruebe que la **sala modelo** propiedad en el **Inspector** panel ahora está configurado para **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="da92b-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="da92b-240">Presione el **reproducir** botón Entrar en modo de vista previa de Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="da92b-241">El componente SpatialMapping cargará las mallas del modelo guardado espacio para que pueda usar en Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="da92b-242">Cambie a **escena** vista para ver todo el modelo de sala muestra con el sombreador de tramas de alambres.</span><span class="sxs-lookup"><span data-stu-id="da92b-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="da92b-243">Presione el **reproducir** botón nuevo para salir del modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="da92b-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="da92b-244">**NOTA:** La próxima vez que especifique el modo de vista previa en Unity, cargará la malla de la sala guardado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="da92b-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="da92b-245">Capítulo 2: visualización</span><span class="sxs-lookup"><span data-stu-id="da92b-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="da92b-246">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="da92b-246">**Objectives**</span></span>
* <span data-ttu-id="da92b-247">Obtenga información sobre los conceptos básicos de los sombreadores.</span><span class="sxs-lookup"><span data-stu-id="da92b-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="da92b-248">Visualizar respecto a su entorno.</span><span class="sxs-lookup"><span data-stu-id="da92b-248">Visualize your surroundings.</span></span>

<span data-ttu-id="da92b-249">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="da92b-249">**Instructions**</span></span>
* <span data-ttu-id="da92b-250">En Unity **jerarquía** panel, seleccione el **SpatialMapping** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="da92b-251">En el **Inspector** panel, busque el **espacial Administrador de asignación (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="da92b-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="da92b-252">Haga clic en el círculo situado a la derecha de la **superficie Material** propiedad.</span><span class="sxs-lookup"><span data-stu-id="da92b-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="da92b-253">Busque y seleccione el **BlueLinesOnWalls** material y cerrar la ventana.</span><span class="sxs-lookup"><span data-stu-id="da92b-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="da92b-254">En el **proyecto** panel **sombreadores** carpeta, haga doble clic en **BlueLinesOnWalls** para abrir el sombreador en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da92b-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="da92b-255">Se trata de un píxel simple (vértice fragmentar) sombreador, que lleva a cabo las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="da92b-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="da92b-256">Convierte la ubicación de un vértice en espacio global.</span><span class="sxs-lookup"><span data-stu-id="da92b-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="da92b-257">Comprueba que el vértice 's normal para determinar si un píxel es vertical.</span><span class="sxs-lookup"><span data-stu-id="da92b-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="da92b-258">Establece el color del píxel para la representación.</span><span class="sxs-lookup"><span data-stu-id="da92b-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="da92b-259">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="da92b-259">**Build and Deploy**</span></span>
* <span data-ttu-id="da92b-260">Volver a Unity y presione **reproducir** entrar en modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="da92b-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="da92b-261">Las líneas azules se representará en todas las superficies verticales de la malla de espacio (que se cargan automáticamente desde nuestros datos guardados de análisis).</span><span class="sxs-lookup"><span data-stu-id="da92b-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="da92b-262">Cambie a la **escena** tab para ajustar la vista de la sala de reuniones y vea cómo aparece la malla en toda la sala de Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="da92b-263">En el **proyecto** panel, busque el **materiales** carpeta y seleccione el **BlueLinesOnWalls** material.</span><span class="sxs-lookup"><span data-stu-id="da92b-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="da92b-264">Modificar algunas propiedades y ver cómo aparecen los cambios en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="da92b-265">En el **Inspector** del panel, ajustar el **LineScale** valor para que las líneas aparezcan más gruesa o más estrecha.</span><span class="sxs-lookup"><span data-stu-id="da92b-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="da92b-266">En el **Inspector** del panel, ajustar el **LinesPerMeter** valor para cambiar el número de líneas que aparecen en cada muro.</span><span class="sxs-lookup"><span data-stu-id="da92b-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="da92b-267">Haga clic en **reproducir** nuevo para salir del modo de vista previa.</span><span class="sxs-lookup"><span data-stu-id="da92b-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="da92b-268">Compilar e implementar a la HoloLens y observe cómo aparece el sombreador de representación en superficies real.</span><span class="sxs-lookup"><span data-stu-id="da92b-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="da92b-269">Unity hace un gran trabajo de vista previa de materiales, pero siempre es una buena idea a la representación de desprotección en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="da92b-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="da92b-270">Capítulo 3: procesar</span><span class="sxs-lookup"><span data-stu-id="da92b-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="da92b-271">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="da92b-271">**Objectives**</span></span>
* <span data-ttu-id="da92b-272">Aprenda técnicas para procesar los datos de asignación espacial para su uso en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="da92b-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="da92b-273">Analizar los datos de asignación espacial para buscar planes y quitar triángulos.</span><span class="sxs-lookup"><span data-stu-id="da92b-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="da92b-274">Utilice planos para selección de ubicación holograma.</span><span class="sxs-lookup"><span data-stu-id="da92b-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="da92b-275">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="da92b-275">**Instructions**</span></span>
* <span data-ttu-id="da92b-276">En Unity **proyecto** panel, **hologramas** carpeta, busque la **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="da92b-277">Arrastrar y colocar la **SpatialProcessing** objeto en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="da92b-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="da92b-278">El recurso prefabricado SpatialProcessing incluye componentes para procesar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="da92b-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="da92b-279">**SurfaceMeshesToPlanes.cs** encontrará y generar planes según los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="da92b-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="da92b-280">Usaremos planos en nuestra aplicación para representar las paredes, pisos y los límites máximos.</span><span class="sxs-lookup"><span data-stu-id="da92b-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="da92b-281">También incluye este recurso prefabricado **RemoveSurfaceVertices.cs** que puede quitar los vértices de la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="da92b-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="da92b-282">Esto puede usarse para crear agujeros en la malla, o para quitar un exceso triángulos que ya no son necesarios (porque los planos pueden usarse en su lugar).</span><span class="sxs-lookup"><span data-stu-id="da92b-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="da92b-283">En Unity **proyecto** panel, **hologramas** carpeta, busque la **SpaceCollection** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="da92b-284">Arrastre y coloque el **SpaceCollection** objeto en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="da92b-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="da92b-285">En el **jerarquía** panel, seleccione el **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="da92b-286">En el **Inspector** panel, busque el **reproducir el Administrador de espacio (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="da92b-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="da92b-287">Haga doble clic en **PlaySpaceManager.cs** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da92b-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="da92b-288">PlaySpaceManager.cs contiene código específico de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="da92b-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="da92b-289">Se agregará funcionalidad a esta secuencia de comandos para habilitar el comportamiento siguiente:</span><span class="sxs-lookup"><span data-stu-id="da92b-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="da92b-290">Detener la recopilación de datos de asignación espacial después de que se supere el límite de tiempo de análisis (10 segundos).</span><span class="sxs-lookup"><span data-stu-id="da92b-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="da92b-291">Procesar los datos de asignación espacial:</span><span class="sxs-lookup"><span data-stu-id="da92b-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="da92b-292">Use SurfaceMeshesToPlanes para crear una representación más sencilla del mundo como planos (paredes, pisos, los límites máximos, etcetera).</span><span class="sxs-lookup"><span data-stu-id="da92b-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="da92b-293">Use RemoveSurfaceVertices para quitar los triángulos superficies que se encuentran dentro de los límites del plano.</span><span class="sxs-lookup"><span data-stu-id="da92b-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="da92b-294">Generar una colección de hologramas en el mundo y colocarlos en planos de piso y la pared cerca del usuario.</span><span class="sxs-lookup"><span data-stu-id="da92b-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="da92b-295">Completar los ejercicios de codificación marcados en PlaySpaceManager.cs o reemplazar la secuencia de comandos con la solución completa de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="da92b-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

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

<span data-ttu-id="da92b-296">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="da92b-296">**Build and Deploy**</span></span>
* <span data-ttu-id="da92b-297">Antes de implementar en el HoloLens, presione el **reproducir** botón en Unity para entrar en modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="da92b-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="da92b-298">Después de la malla de la sala se carga desde el archivo, espere 10 segundos antes de que comience el procesamiento en la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="da92b-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="da92b-299">Cuando se completa el procesamiento, planos aparecerá representar el suelo, paredes, ceiling, etcetera.</span><span class="sxs-lookup"><span data-stu-id="da92b-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="da92b-300">Después de todo de los aviones se han encontrado, debería ver un sistema solar aparecen en una tabla de piso cerca de la cámara.</span><span class="sxs-lookup"><span data-stu-id="da92b-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="da92b-301">Dos pósteres demasiado deben aparecer en las paredes cerca de la cámara.</span><span class="sxs-lookup"><span data-stu-id="da92b-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="da92b-302">Cambie a la **escena** pestaña si no puede verlas en **juego** modo.</span><span class="sxs-lookup"><span data-stu-id="da92b-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="da92b-303">Presione el **reproducir** botón nuevo para salir del modo de juego.</span><span class="sxs-lookup"><span data-stu-id="da92b-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="da92b-304">Compilar e implementar en el HoloLens, como de costumbre.</span><span class="sxs-lookup"><span data-stu-id="da92b-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="da92b-305">Espere a análisis y procesamiento de los datos de asignación espacial en completarse.</span><span class="sxs-lookup"><span data-stu-id="da92b-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="da92b-306">Una vez que vea aviones, intenta encontrar el sistema solar y pósters en el mundo.</span><span class="sxs-lookup"><span data-stu-id="da92b-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="da92b-307">Capítulo 4: selección de ubicación</span><span class="sxs-lookup"><span data-stu-id="da92b-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="da92b-308">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="da92b-308">**Objectives**</span></span>
* <span data-ttu-id="da92b-309">Determinar si un holograma caben en una superficie.</span><span class="sxs-lookup"><span data-stu-id="da92b-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="da92b-310">Proporcionar comentarios al usuario cuando un holograma puede o no cabe en una superficie.</span><span class="sxs-lookup"><span data-stu-id="da92b-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="da92b-311">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="da92b-311">**Instructions**</span></span>
* <span data-ttu-id="da92b-312">En Unity **jerarquía** panel, seleccione el **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="da92b-313">En el **Inspector** panel, busque el **mallas de superficie para aviones (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="da92b-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="da92b-314">Cambiar el **dibujar planos** propiedad **nada** para borrar la selección.</span><span class="sxs-lookup"><span data-stu-id="da92b-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="da92b-315">Cambiar el **dibujar planos** propiedad **pared**, de modo que solo los planos de pared se representará.</span><span class="sxs-lookup"><span data-stu-id="da92b-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="da92b-316">En el **proyecto** panel, **Scripts** carpeta, haga doble clic en **Placeable.cs** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da92b-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="da92b-317">El **Placeable** script ya está conectado con el cuadro de proyección y pósteres de los que se crean una vez finalizada la búsqueda de plano.</span><span class="sxs-lookup"><span data-stu-id="da92b-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="da92b-318">Todo lo que necesitamos hacer es eliminar los comentarios algo de código, y esta secuencia de comandos, logrará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="da92b-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="da92b-319">Determinar si un holograma caben en una superficie de detalles de las cuatro esquinas del cubo delimitador y el centro.</span><span class="sxs-lookup"><span data-stu-id="da92b-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="da92b-320">Comprobar para determinar si es lo suficientemente suave para el holograma vaciado estuvieron en normal de la superficie.</span><span class="sxs-lookup"><span data-stu-id="da92b-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="da92b-321">Representar el holograma para mostrar su tamaño real mientras se coloca un cubo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="da92b-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="da92b-322">Convertir una sombra el holograma para mostrar dónde se colocarán en el muro de piso en/subyacente.</span><span class="sxs-lookup"><span data-stu-id="da92b-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="da92b-323">Representar la sombra en rojo si el holograma no se puede colocar en la superficie o verde, si es posible.</span><span class="sxs-lookup"><span data-stu-id="da92b-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="da92b-324">Vuelva a orientar el holograma para alinearse con el tipo de superficie (horizontal o vertical) que tiene afinidad con.</span><span class="sxs-lookup"><span data-stu-id="da92b-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="da92b-325">Coloca sin problemas el holograma en la superficie seleccionada para evitar saltar o comportamiento de ajuste.</span><span class="sxs-lookup"><span data-stu-id="da92b-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="da92b-326">Quite todo el código en el ejercicio de codificación a continuación o usar esta solución completa en **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="da92b-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

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

<span data-ttu-id="da92b-327">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="da92b-327">**Build and Deploy**</span></span>
* <span data-ttu-id="da92b-328">Como antes, compile el proyecto e implemente en el HoloLens.</span><span class="sxs-lookup"><span data-stu-id="da92b-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="da92b-329">Espere a análisis y procesamiento de los datos de asignación espacial en completarse.</span><span class="sxs-lookup"><span data-stu-id="da92b-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="da92b-330">Cuando ve el sistema solar, mire debajo de la casilla de proyección y realizar un gesto de select para moverse por.</span><span class="sxs-lookup"><span data-stu-id="da92b-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="da92b-331">Mientras está seleccionado el cuadro de proyección, un cubo delimitador estará visible alrededor del cuadro de proyección.</span><span class="sxs-lookup"><span data-stu-id="da92b-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="da92b-332">Mover head para que mirar en una ubicación diferente en la sala.</span><span class="sxs-lookup"><span data-stu-id="da92b-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="da92b-333">El cuadro de proyección debe seguir a su mirada.</span><span class="sxs-lookup"><span data-stu-id="da92b-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="da92b-334">Cuando la sombra debajo del cuadro de proyección en color roja, no se puede colocar el holograma en que se muestran.</span><span class="sxs-lookup"><span data-stu-id="da92b-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="da92b-335">Cuando se vuelve verde la sombra debajo del cuadro de proyección, puede colocar el holograma realizando gesto seleccione otro.</span><span class="sxs-lookup"><span data-stu-id="da92b-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="da92b-336">Busque y seleccione uno de los pósteres holográficas en una pared para moverlo a una nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="da92b-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="da92b-337">Tenga en cuenta que no se puede colocar el póster en el suelo, ceiling, y que se mantiene correctamente orientado hacia cada pared al desplazarse por.</span><span class="sxs-lookup"><span data-stu-id="da92b-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="da92b-338">Capítulo 5: oclusión</span><span class="sxs-lookup"><span data-stu-id="da92b-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="da92b-339">**Objetivos**</span><span class="sxs-lookup"><span data-stu-id="da92b-339">**Objectives**</span></span>
* <span data-ttu-id="da92b-340">Determinar si un holograma se ocluyeron en la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="da92b-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="da92b-341">Aplicar técnicas de oclusión diferentes para lograr un divertido efecto.</span><span class="sxs-lookup"><span data-stu-id="da92b-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="da92b-342">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="da92b-342">**Instructions**</span></span>

<span data-ttu-id="da92b-343">En primer lugar, vamos a permitir la malla de asignación espacial a occlude otros hologramas sin occluding del mundo real:</span><span class="sxs-lookup"><span data-stu-id="da92b-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="da92b-344">En el **jerarquía** panel, seleccione el **SpatialProcessing** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="da92b-345">En el **Inspector** panel, busque el **reproducir el Administrador de espacio (Script)** componente.</span><span class="sxs-lookup"><span data-stu-id="da92b-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="da92b-346">Haga clic en el círculo situado a la derecha de la **Material secundario** propiedad.</span><span class="sxs-lookup"><span data-stu-id="da92b-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="da92b-347">Busque y seleccione el **oclusión** material y cerrar la ventana.</span><span class="sxs-lookup"><span data-stu-id="da92b-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="da92b-348">A continuación, vamos a agregar un comportamiento especial a la tierra, para que tenga un resaltado azul cada vez que se pasa a ser ocluido holograma otro (por ejemplo, el sol), o bien la malla de asignación espacial:</span><span class="sxs-lookup"><span data-stu-id="da92b-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="da92b-349">En el **proyecto** panel el **hologramas** carpeta, expanda la **SolarSystem** objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="da92b-350">Haga clic en **tierra**.</span><span class="sxs-lookup"><span data-stu-id="da92b-350">Click on **Earth**.</span></span>
* <span data-ttu-id="da92b-351">En el **Inspector** del panel, encontrará abundante material de la tierra (componente de la parte inferior).</span><span class="sxs-lookup"><span data-stu-id="da92b-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="da92b-352">En el **sombreador desplegable**, cambie el sombreador **personalizado > OcclusionRim**.</span><span class="sxs-lookup"><span data-stu-id="da92b-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="da92b-353">Esto representará un resaltado azul alrededor de la tierra cada vez que se ocluyeron en otro objeto.</span><span class="sxs-lookup"><span data-stu-id="da92b-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="da92b-354">Por último, vamos a habilitar un efecto de la visión de rayos x para planetas en nuestro sistema solar.</span><span class="sxs-lookup"><span data-stu-id="da92b-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="da92b-355">Tendremos que editar **PlanetOcclusion.cs** (que se encuentra en la carpeta Scripts\SolarSystem) con el fin de lograr lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="da92b-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="da92b-356">Determinar si un planeta se ocluyeron en la capa SpatialMapping (sala mallas y planos).</span><span class="sxs-lookup"><span data-stu-id="da92b-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="da92b-357">Mostrar la representación de tramas de alambres de un mundo cada vez que se ocluyeron en la capa SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="da92b-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="da92b-358">Ocultar la representación de tramas de alambres de un planeta cuando no está bloqueado por la capa de SpatialMapping.</span><span class="sxs-lookup"><span data-stu-id="da92b-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="da92b-359">Siga el ejercicio de codificación de PlanetOcclusion.cs, o utilice la siguiente solución:</span><span class="sxs-lookup"><span data-stu-id="da92b-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

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

<span data-ttu-id="da92b-360">**Compilación e implementación**</span><span class="sxs-lookup"><span data-stu-id="da92b-360">**Build and Deploy**</span></span>
* <span data-ttu-id="da92b-361">Compile e implemente la aplicación a HoloLens, como de costumbre.</span><span class="sxs-lookup"><span data-stu-id="da92b-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="da92b-362">Espere de análisis y procesamiento de los datos de asignación espacial que se complete (debería ver las líneas azules aparecen en las paredes).</span><span class="sxs-lookup"><span data-stu-id="da92b-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="da92b-363">Buscar y seleccione el cuadro de proyección solar del sistema y, a continuación, establezca el cuadro situado junto a una pared o detrás de un contador.</span><span class="sxs-lookup"><span data-stu-id="da92b-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="da92b-364">Puede ver la oclusión básica ocultándose tras las superficies del mismo nivel en el cuadro de póster o proyección.</span><span class="sxs-lookup"><span data-stu-id="da92b-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="da92b-365">Busque la tierra, debe haber un efecto de resaltado en azul cada vez que va detrás de otro holograma o la superficie.</span><span class="sxs-lookup"><span data-stu-id="da92b-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="da92b-366">Ver cómo mover los planetas detrás de la pared o en otras superficies en la sala.</span><span class="sxs-lookup"><span data-stu-id="da92b-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="da92b-367">¡Ahora tiene la visión de rayos x y puede ver sus esqueletos de tramas de alambres!</span><span class="sxs-lookup"><span data-stu-id="da92b-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="da92b-368">Fin</span><span class="sxs-lookup"><span data-stu-id="da92b-368">The End</span></span>

<span data-ttu-id="da92b-369">¡Enhorabuena!</span><span class="sxs-lookup"><span data-stu-id="da92b-369">Congratulations!</span></span> <span data-ttu-id="da92b-370">Ahora ha completado **MR espacial 230: Asignación espacial**.</span><span class="sxs-lookup"><span data-stu-id="da92b-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="da92b-371">Saber cómo analizar los datos de carga y el entorno de asignación espacial a Unity.</span><span class="sxs-lookup"><span data-stu-id="da92b-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="da92b-372">Comprender los conceptos básicos de los sombreadores y cómo se pueden usar los materiales para volver a visualizar el mundo.</span><span class="sxs-lookup"><span data-stu-id="da92b-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="da92b-373">Ha aprendido de nuevas técnicas de procesamiento para buscar los planos y quitarlo una malla de triángulos.</span><span class="sxs-lookup"><span data-stu-id="da92b-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="da92b-374">Podía mover y colocar hologramas en superficies que tenía sentido.</span><span class="sxs-lookup"><span data-stu-id="da92b-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="da92b-375">¡Ha experimentado técnicas diferentes oclusión y aprovecha la potencia de la visión de rayos x!</span><span class="sxs-lookup"><span data-stu-id="da92b-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
