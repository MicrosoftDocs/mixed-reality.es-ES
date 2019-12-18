---
title: 'Tutoriales de audio espacial: 1. Agregar audio espacial al proyecto'
description: Agregue el complemento de Microsoft Spatializer a su proyecto de Unity para acceder a la descarga de hardware de HoloLens 2 HRTF.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182802"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="fbe3c-105">Incorporación de audio espacial al proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="fbe3c-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="fbe3c-106">Este es el tutioral de audio espacial para Unity en HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="fbe3c-107">Esta secuencia de tutorial muestra:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="fbe3c-108">Cómo usar la descarga de HRTF en HoloLens 2 en Unity</span><span class="sxs-lookup"><span data-stu-id="fbe3c-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="fbe3c-109">Cómo habilitar la reverberación al usar la descarga de HRTF</span><span class="sxs-lookup"><span data-stu-id="fbe3c-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="fbe3c-110">El [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutoriales.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="fbe3c-111">Para ver las recomendaciones sobre cuándo puede ser útil espaciales, consulte diseño de [sonido espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="fbe3c-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="fbe3c-112">Objetivos</span><span class="sxs-lookup"><span data-stu-id="fbe3c-112">Objectives</span></span>
<span data-ttu-id="fbe3c-113">En este primer capítulo, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="fbe3c-114">Creación de un proyecto de Unity e importación de MRTK</span><span class="sxs-lookup"><span data-stu-id="fbe3c-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="fbe3c-115">Importar el complemento de Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="fbe3c-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="fbe3c-116">Habilitación del complemento Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="fbe3c-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="fbe3c-117">Habilitación del audio espacial en la estación de trabajo de desarrollador</span><span class="sxs-lookup"><span data-stu-id="fbe3c-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="fbe3c-118">Creación de un proyecto y adición de NuGet para Unity</span><span class="sxs-lookup"><span data-stu-id="fbe3c-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="fbe3c-119">Comience con un proyecto de Unity vacío y, después, agregue y configure NuGet para Unity:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="fbe3c-120">Descargue la versión más reciente de [NuGetForUnity. unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="fbe3c-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="fbe3c-121">En la barra de menús de Unity, haga clic en **activos > importar paquete > paquete personalizado...** e instalar el paquete NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importar paquete personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="fbe3c-123">Agregar el paquete de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="fbe3c-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="fbe3c-124">La compatibilidad con Windows Mixed Reality en Unity 2019 y versiones posteriores se incluye en un paquete opcional.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="fbe3c-125">Para agregarlo al proyecto, abra el **Administrador de paquetes de > de ventana** desde la barra de menús de Unity:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menú del administrador de paquetes](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="fbe3c-127">A continuación, busque e instale el paquete de **Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="fbe3c-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![Ventana del administrador de paquetes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="fbe3c-129">Instalación de MRTK y Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="fbe3c-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="fbe3c-130">Con NuGet para Unity, instale los complementos de MRTK y Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="fbe3c-131">En la barra de menús de Unity, haga clic en **Nuget-> administrar paquetes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Administrar paquetes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="fbe3c-133">En el cuadro de **búsqueda** , escriba "Microsoft. MixedReality. Toolkit" e instale el paquete de MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation** .</span><span class="sxs-lookup"><span data-stu-id="fbe3c-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Paquete NuGet de MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="fbe3c-135">El [paquete NuGet de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tiene contexto y detalles adicionales.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="fbe3c-136">En el cuadro de **búsqueda** , escriba "Microsoft. SpatialAudio" e instale el paquete de Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity** .</span><span class="sxs-lookup"><span data-stu-id="fbe3c-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Complemento NuGet de Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="fbe3c-138">Configuración de MRTK en el proyecto</span><span class="sxs-lookup"><span data-stu-id="fbe3c-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="fbe3c-139">Para abrir la ventana Configuración de compilación, vaya a **archivo-> configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="fbe3c-140">Seleccione la _plataforma universal de Windows_ y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="fbe3c-141">Haga clic en **configuración del reproductor** en la **ventana compilar** para abrir las propiedades de **configuración del reproductor** en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="fbe3c-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="fbe3c-142">En **configuración de XR**, active la casilla **compatible con realidad virtual**</span><span class="sxs-lookup"><span data-stu-id="fbe3c-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="fbe3c-143">En **configuración de XR**, cambie el **modo de representación de estéreo** a instancia de **paso único**.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="fbe3c-144">En **configuración de publicación**, active la casilla **percepción espacial** en la sección **capacidades** .</span><span class="sxs-lookup"><span data-stu-id="fbe3c-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="fbe3c-145">En la barra de menús, haga clic en **Kit de herramientas de realidad mixta: > agregar a la escena y configurar.**</span><span class="sxs-lookup"><span data-stu-id="fbe3c-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="fbe3c-146">para agregar MRTK a la escena.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="fbe3c-147">Para obtener instrucciones adicionales, incluida la forma de compilar la aplicación e implementarla en HoloLens 2, consulte [el capítulo 1 del módulo de base de aprendizaje Mr](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="fbe3c-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="fbe3c-148">Habilitación del complemento Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="fbe3c-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="fbe3c-149">Habilite el complemento de **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="fbe3c-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="fbe3c-150">Abra **editar > configuración del proyecto-> audio**y cambie el **complemento Spatializer** a "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="fbe3c-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="fbe3c-151">La sección **audio** de la **configuración del proyecto** tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="fbe3c-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Configuración del proyecto que muestra el complemento spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="fbe3c-153">Habilitación del audio espacial en la estación de trabajo</span><span class="sxs-lookup"><span data-stu-id="fbe3c-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="fbe3c-154">En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="fbe3c-155">Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="fbe3c-156">Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **sonido espacial > Windows Sonic para auriculares**.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Configuración de audio espacial de escritorio](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="fbe3c-158">Esta configuración solo es necesaria si tiene previsto probar el proyecto en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fbe3c-159">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="fbe3c-159">Next steps</span></span>
<span data-ttu-id="fbe3c-160">Continúe con el [capítulo 2 del audio espacial de Unity](unity-spatial-audio-ch2.md) para enspatial los sonidos de interacción del botón.</span><span class="sxs-lookup"><span data-stu-id="fbe3c-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

