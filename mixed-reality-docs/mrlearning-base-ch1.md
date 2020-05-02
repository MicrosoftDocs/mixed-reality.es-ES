---
title: 'Tutoriales de introducción: 2. Inicialización de tu proyecto y primera aplicación'
description: Haz este curso para aprender a implementar el reconocimiento facial de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376212"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="a29c6-105">2. Inicialización de tu proyecto y primera aplicación</span><span class="sxs-lookup"><span data-stu-id="a29c6-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="a29c6-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="a29c6-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="a29c6-107">En este primero tutorial, obtendrás información sobre algunas de las funcionalidades que ofrece <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a>, empezarás tu primera aplicación para HoloLens 2 y la implementarás en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a29c6-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="a29c6-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a29c6-108">Objectives</span></span>

* <span data-ttu-id="a29c6-109">Configurar Unity para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="a29c6-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="a29c6-110">Importar recursos y configurar la escena</span><span class="sxs-lookup"><span data-stu-id="a29c6-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="a29c6-111">Ver la malla de asignación espacial, mallas de mano y el contador de velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="a29c6-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a29c6-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a29c6-112">Prerequisites</span></span>

* <span data-ttu-id="a29c6-113">Un equipo Windows 10 configurado con las [herramientas instaladas](install-the-tools.md) correctas</span><span class="sxs-lookup"><span data-stu-id="a29c6-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a29c6-114">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="a29c6-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a29c6-115">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="a29c6-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="a29c6-116">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="a29c6-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a29c6-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="a29c6-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a29c6-118">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="a29c6-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="a29c6-119">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a29c6-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="a29c6-120">Creación de un nuevo proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="a29c6-120">Create new Unity project</span></span>

<span data-ttu-id="a29c6-121">Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):</span><span class="sxs-lookup"><span data-stu-id="a29c6-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="a29c6-123">Selecciona la versión de Unity especificada en la sección [Requisitos previos](#prerequisites) anterior:</span><span class="sxs-lookup"><span data-stu-id="a29c6-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="a29c6-125">En la ventana Create a new project (Crear un proyecto nuevo):</span><span class="sxs-lookup"><span data-stu-id="a29c6-125">In the Create a new project window:</span></span>

* <span data-ttu-id="a29c6-126">Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.</span><span class="sxs-lookup"><span data-stu-id="a29c6-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="a29c6-127">Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_</span><span class="sxs-lookup"><span data-stu-id="a29c6-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="a29c6-128">Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="a29c6-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="a29c6-129">Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="a29c6-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="a29c6-131">Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="a29c6-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="a29c6-132">Unity se ve afectado por estos límites y puede producirse un error en la compilación si la ruta de acceso de un archivo tiene más de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="a29c6-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="a29c6-133">Por lo tanto, se recomienda encarecidamente almacenar el proyecto de Unity lo más cerca posible de la raíz de la unidad.</span><span class="sxs-lookup"><span data-stu-id="a29c6-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="a29c6-134">Espera a que Unity cree el proyecto:</span><span class="sxs-lookup"><span data-stu-id="a29c6-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="a29c6-136">Configuración del proyecto de Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a29c6-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="a29c6-137">En esta sección, se cambiará la plataforma de compilación y se habilitará la realidad virtual y la percepción espacial.</span><span class="sxs-lookup"><span data-stu-id="a29c6-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="a29c6-138">1. Cambiar la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="a29c6-138">1. Switch build platform</span></span>

<span data-ttu-id="a29c6-139">En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="a29c6-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="a29c6-141">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="a29c6-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="a29c6-143">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="a29c6-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="a29c6-145">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="a29c6-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="a29c6-147">2. Habilitar la realidad virtual</span><span class="sxs-lookup"><span data-stu-id="a29c6-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="a29c6-148">La opción de habilitar la realidad virtual también se aplica a los cascos de realidad mixta y realidad aumentada, ya que hace referencia a la habilitación de la visión estereoscópica (p. ej., la representación de imágenes diferentes para cada ojo).</span><span class="sxs-lookup"><span data-stu-id="a29c6-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="a29c6-149">En el menú de Unity, selecciona **Edit** (Editar)  > **Project Settings...** (Configuración del proyecto) para abrir la ventana de configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="a29c6-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="a29c6-151">En la ventana de configuración del proyecto, selecciona **Player** (Reproductor) > **XR Settings** (Configuración de XR) para expandir la configuración de XR:</span><span class="sxs-lookup"><span data-stu-id="a29c6-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="a29c6-153">En la configuración de XR, activa la casilla **Virtual Reality Supported** (Compatible con realidad virtual) para habilitar la realidad virtual y, a continuación, haz clic en el icono **+** y selecciona **Windows Mixed Reality** para agregar el SDK de Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="a29c6-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="a29c6-155">Espera a que Unity termine de agregar el SDK:</span><span class="sxs-lookup"><span data-stu-id="a29c6-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="a29c6-157">Cuando Unity haya terminado de agregar el SDK, optimiza la configuración de XR de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="a29c6-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="a29c6-158">Establece el valor **Depth Format** (Formato de profundidad) de Windows Mixed Reality en **16-bit depth** (Profundidad de 16 bits).</span><span class="sxs-lookup"><span data-stu-id="a29c6-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="a29c6-159">Activa la casilla **Enable Depth Sharing** (Habilitar el uso compartido de profundidad) de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a29c6-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="a29c6-160">Establece el valor **Rendering Mode\* (Modo de representación) estéreo**  en **Single Pass Instanced** (Instancia de paso único)</span><span class="sxs-lookup"><span data-stu-id="a29c6-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="a29c6-162">Para obtener más información sobre cómo optimizar Unity para Windows Mixed Reality, puedes consultar la página de ayuda [Configuración recomendada para Unity](recommended-settings-for-unity.md) en la documentación.</span><span class="sxs-lookup"><span data-stu-id="a29c6-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="a29c6-163">3. Habilitar la percepción espacial</span><span class="sxs-lookup"><span data-stu-id="a29c6-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="a29c6-164">La percepción espacial permite ver la malla de asignación espacial en dispositivos Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a29c6-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="a29c6-165">En la ventana de configuración del proyecto, selecciona **Player** (Reproductor) > **Publishing Settings** (Configuración de publicación) para expandir la configuración de publicación:</span><span class="sxs-lookup"><span data-stu-id="a29c6-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="a29c6-167">En la configuración de publicación, desplázate hacia abajo hasta la sección **Capabilities** (Funcionalidades) y activa la casilla **SpatialPerception**:</span><span class="sxs-lookup"><span data-stu-id="a29c6-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="a29c6-169">Cierra la ventana Project Settings (Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="a29c6-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="a29c6-170">Importación de recursos esenciales de TextMesh Pro</span><span class="sxs-lookup"><span data-stu-id="a29c6-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="a29c6-171">Importamos este paquete porque los elementos de la UI de Mixed Reality Toolkit lo requieren.</span><span class="sxs-lookup"><span data-stu-id="a29c6-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="a29c6-172">En el menú de Unity, selecciona **Window** (Ventana) > **TextMeshPro** > **Import TMP Essential Resources** (Importar recursos esenciales de TMP):</span><span class="sxs-lookup"><span data-stu-id="a29c6-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="a29c6-174">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="a29c6-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="a29c6-176">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a29c6-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="a29c6-177">Descarga el paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="a29c6-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="a29c6-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a29c6-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="a29c6-179">En el menú de Unity, selecciona **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):</span><span class="sxs-lookup"><span data-stu-id="a29c6-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="a29c6-181">En la ventana de importación de paquetes, selecciona el paquete **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** que descargaste y haz clic en el botón **Open** (Abrir):</span><span class="sxs-lookup"><span data-stu-id="a29c6-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="a29c6-183">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="a29c6-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="a29c6-185">Configuración del proyecto de Unity para Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a29c6-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="a29c6-186">Una vez importado el paquete, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="a29c6-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="a29c6-187">Si no aparece, se puede abrir seleccionando la opción **Mixed Reality Toolkit** > **Utilities** (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) en el menú de Unity.</span><span class="sxs-lookup"><span data-stu-id="a29c6-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="a29c6-189">En la ventana MRTK Project Configurator, expande la sección **Modify Configurations** (Modificar configuraciones), <u>desactiva</u> la casilla **Enable MSBuild for Unity** (Habilitar MSBuild para Unity), asegúrate de que todas las demás opciones están seleccionadas y haz clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="a29c6-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="a29c6-191">Es posible que MSBuild para Unity no admita todos los SDK que vas a usar y puede ser difícil de deshabilitar una vez que se haya habilitado.</span><span class="sxs-lookup"><span data-stu-id="a29c6-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="a29c6-192">Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="a29c6-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="a29c6-193">Configuración de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a29c6-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="a29c6-194">En el menú de Unity, selecciona **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar) para agregar Mixed Reality Toolkit a la escena actual:</span><span class="sxs-lookup"><span data-stu-id="a29c6-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="a29c6-196">Con el objeto MixedRealityToolkit seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, comprueba que el perfil de configuración de Mixed Reality Toolkit se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="a29c6-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="a29c6-198">Normalmente, se usa el perfil DefaultHoloLens2ConfigurationProfile para desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a29c6-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="a29c6-199">Sin embargo, para este tutorial, usarás DefaultMixedRealityToolkitConfigurationProfile y, a continuación, en el siguiente tutorial, [Crear la interfaz de usuario y configurar Mixed Reality Toolkit](mrlearning-base-ch2.md), cambiarás a DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="a29c6-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="a29c6-200">En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):</span><span class="sxs-lookup"><span data-stu-id="a29c6-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="a29c6-202">En la ventana Save Scene (Guardar escena), desplázate hasta la carpeta **Scenes** (Escenas) del proyecto, asígnale un nombre adecuado (por ejemplo, _GettingStarted_), y haz clic en el botón **Save** (Guardar) para guardar la escena:</span><span class="sxs-lookup"><span data-stu-id="a29c6-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="a29c6-204">Compilación de la aplicación para el dispositivo</span><span class="sxs-lookup"><span data-stu-id="a29c6-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="a29c6-205">1. Compilar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="a29c6-205">1. Build the Unity project</span></span>

<span data-ttu-id="a29c6-206">En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="a29c6-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="a29c6-207">En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):</span><span class="sxs-lookup"><span data-stu-id="a29c6-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="a29c6-209">En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="a29c6-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="a29c6-211">Espera a que Unity finalice el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="a29c6-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="a29c6-213">2. Compilar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="a29c6-213">2. Build and deploy the application</span></span>

<span data-ttu-id="a29c6-214">Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación.</span><span class="sxs-lookup"><span data-stu-id="a29c6-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="a29c6-215">Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="a29c6-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="a29c6-217">Si Visual Studio solicita que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la documentación [Instalación de herramientas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a29c6-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="a29c6-218">Configura Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM** y la opción **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="a29c6-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> <span data-ttu-id="a29c6-220">Si no ves Device (Dispositivo) como opción, puede que necesites cambiar el proyecto de inicio predeterminado del proyecto IC2Lpp al proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="a29c6-220">If you don't see Device as an option you may need to change the default start up project from the IC2Lpp project to your UWP Project.</span></span> <span data-ttu-id="a29c6-221">En el **Explorador de soluciones**, haz clic con el botón derecho en **yourprojectname (Windows Universal)** y selecciona **Establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="a29c6-221">In the **Solution Explorer**, right click on **yourprojectname (Universal Windows)** and select **Set as StartUp Project**.</span></span> 

<span data-ttu-id="a29c6-222">Conecta HoloLens 2 a tu equipo.</span><span class="sxs-lookup"><span data-stu-id="a29c6-222">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a29c6-223">Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="a29c6-223">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="a29c6-224">Ambos pasos pueden completarse siguiendo [estas instrucciones](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="a29c6-224">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="a29c6-225">El último paso consiste en compilar y realizar la implementación en el dispositivo seleccionando las opciones **Depurar** > **Iniciar sin depurar**:</span><span class="sxs-lookup"><span data-stu-id="a29c6-225">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="a29c6-227">Aunque en estas instrucciones se supone que vas a realizar la implementación a un dispositivo HoloLens 2, también puedes realizar la implementación en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o crear un [paquete de la aplicación para una instalación de prueba](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="a29c6-227">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="a29c6-228">Al seleccionar Iniciar sin depurar, la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que el depurador esté asociado ni que la información de depuración aparezca en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a29c6-228">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="a29c6-229">Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a29c6-229">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="a29c6-230">Para realizar una implementación en el dispositivo sin necesidad de que se inicie automáticamente la aplicación, puedes seleccionar Compilar > Implementar solución.</span><span class="sxs-lookup"><span data-stu-id="a29c6-230">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a29c6-231">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="a29c6-231">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="a29c6-232">Ya has implementado tu primera aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a29c6-232">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="a29c6-233">A medida que avances, deberías ver una malla de asignación espacial que cubre todas las superficies que HoloLens 2 ha percibido.</span><span class="sxs-lookup"><span data-stu-id="a29c6-233">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="a29c6-234">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento de manos, así como un contador de velocidad de fotogramas para supervisar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a29c6-234">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="a29c6-235">Estos son solo algunas de las partes fundamentales, incluidas de fábrica en Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="a29c6-235">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="a29c6-236">En los tutoriales siguientes, comenzarás a agregar más contenido e interactividad a la escena, para que puedas explorar por completo las funcionalidades de HoloLens 2 y Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="a29c6-236">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="a29c6-237">Es posible que veas el generador de perfiles de diagnóstico en la aplicación. Puedes activar y desactivar su visibilidad mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="a29c6-237">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="a29c6-238">Sin embargo, por lo general es recomendable mantener siempre visible el generador de perfiles durante el desarrollo para saber si los cambios a la aplicación pueden haber tenido un impacto en el rendimiento (por ejemplo, la aplicación HoloLens 2 debería [ejecutarse continuamente a 60 FPS](understanding-performance-for-mixed-reality.md)).</span><span class="sxs-lookup"><span data-stu-id="a29c6-238">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="a29c6-239">Tutorial siguiente: 3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a29c6-239">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
