---
title: 'Tutoriales de introducción: 2. Inicialización de su proyecto e implementación de su primera aplicación'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 4f72f70b9eaac159f7d9231e61f23d18d708d0c7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306276"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="96b44-105">2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="96b44-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="96b44-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="96b44-106">Overview</span></span>

<span data-ttu-id="96b44-107">En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK.</span><span class="sxs-lookup"><span data-stu-id="96b44-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="96b44-108">También le guiará a través de la configuración, la compilación y la implementación de la escena de ejemplo básica de Unity desde Visual Studio a HoloLens 2 o el emulador.</span><span class="sxs-lookup"><span data-stu-id="96b44-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="96b44-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="96b44-109">Objectives</span></span>

* <span data-ttu-id="96b44-110">Aprender a configurar Unity para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="96b44-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="96b44-111">Aprender a compilar e implementar la aplicación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="96b44-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="96b44-112">Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="96b44-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="96b44-113">Creación del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="96b44-113">Creating the Unity project</span></span>

<span data-ttu-id="96b44-114">Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):</span><span class="sxs-lookup"><span data-stu-id="96b44-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="96b44-116">En el desplegable, seleccione la **versión** de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="96b44-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="96b44-118">Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.</span><span class="sxs-lookup"><span data-stu-id="96b44-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="96b44-119">En la ventana Create a new project (Crear un proyecto nuevo):</span><span class="sxs-lookup"><span data-stu-id="96b44-119">In the Create a new project window:</span></span>

* <span data-ttu-id="96b44-120">Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.</span><span class="sxs-lookup"><span data-stu-id="96b44-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="96b44-121">Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_</span><span class="sxs-lookup"><span data-stu-id="96b44-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="96b44-122">Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.</span><span class="sxs-lookup"><span data-stu-id="96b44-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="96b44-123">Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="96b44-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="96b44-125">Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="96b44-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="96b44-126">Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.</span><span class="sxs-lookup"><span data-stu-id="96b44-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="96b44-127">Espera a que Unity cree el proyecto:</span><span class="sxs-lookup"><span data-stu-id="96b44-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="96b44-129">Cambio de la plataforma de compilación</span><span class="sxs-lookup"><span data-stu-id="96b44-129">Switching the build platform</span></span>

<span data-ttu-id="96b44-130">En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="96b44-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="96b44-132">En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):</span><span class="sxs-lookup"><span data-stu-id="96b44-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="96b44-134">Espera a que Unity termine de cambiar la plataforma:</span><span class="sxs-lookup"><span data-stu-id="96b44-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="96b44-136">Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:</span><span class="sxs-lookup"><span data-stu-id="96b44-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="96b44-138">Importación de los recursos esenciales de TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="96b44-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="96b44-139">En el menú de Unity, seleccione **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Ventana > TextMeshPro > Importar recursos esenciales de TMP) para abrir la ventana Import Unity Package (Importar paquete de Unity):</span><span class="sxs-lookup"><span data-stu-id="96b44-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="96b44-141">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="96b44-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="96b44-143">Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="96b44-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="96b44-144">Puede omitir este paso si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="96b44-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="96b44-145">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="96b44-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="96b44-146">Descarga el paquete personalizado de Unity:</span><span class="sxs-lookup"><span data-stu-id="96b44-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="96b44-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="96b44-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="96b44-148">En el menú de Unity, selecciona **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):</span><span class="sxs-lookup"><span data-stu-id="96b44-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="96b44-150">En la ventana Import package... (Importar paquete...), seleccione el paquete **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** que descargó y haga clic en el botón **Open** (Abrir):</span><span class="sxs-lookup"><span data-stu-id="96b44-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="96b44-152">En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:</span><span class="sxs-lookup"><span data-stu-id="96b44-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="96b44-154">Configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="96b44-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="96b44-155">1. Aplicación de la configuración del configurador del proyecto de MRTK</span><span class="sxs-lookup"><span data-stu-id="96b44-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="96b44-156">Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="96b44-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="96b44-157">Si no es así, abra la ventana Configurator (Configurador); para ello, vaya al menú de Unity y seleccione **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):</span><span class="sxs-lookup"><span data-stu-id="96b44-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="96b44-159">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expanda la sección **Modify Configurations (Modificar configuraciones)** , asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="96b44-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="96b44-161">2. Configuración de valores adicionales del proyecto</span><span class="sxs-lookup"><span data-stu-id="96b44-161">2. Configure additional project settings</span></span>

<span data-ttu-id="96b44-162">En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:</span><span class="sxs-lookup"><span data-stu-id="96b44-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="96b44-164">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR), haga clic en el icono **+** y seleccione Windows Mixed Reality para agregar el SDK de Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="96b44-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="96b44-166">Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK).</span><span class="sxs-lookup"><span data-stu-id="96b44-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="96b44-167">Si no es así, use el menú de Unity para abrirla.</span><span class="sxs-lookup"><span data-stu-id="96b44-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="96b44-168">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="96b44-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="96b44-170">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):</span><span class="sxs-lookup"><span data-stu-id="96b44-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="96b44-172">En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:</span><span class="sxs-lookup"><span data-stu-id="96b44-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="96b44-174">"Package name" es el identificador único para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="96b44-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="96b44-175">Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="96b44-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="96b44-176">"Product Name" es el nombre que se muestra en el menú Inicio de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="96b44-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="96b44-177">Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.</span><span class="sxs-lookup"><span data-stu-id="96b44-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="96b44-178">Creación y configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="96b44-178">Creating and configuring the scene</span></span>

<span data-ttu-id="96b44-179">En el menú de Unity, seleccione **File** > **New Scene** (Archivo > Nueva escena) para crear una nueva escena:</span><span class="sxs-lookup"><span data-stu-id="96b44-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="96b44-181">En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar...) para agregar MRTK a la escena actual:</span><span class="sxs-lookup"><span data-stu-id="96b44-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="96b44-183">Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, compruebe que el perfil de configuración **MixedRealityToolkit** se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="96b44-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="96b44-185">Normalmente, se usa el perfil DefaultHoloLens2ConfigurationProfile para desarrollar para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="96b44-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="96b44-186">Sin embargo, para este tutorial, usará DefaultMixedRealityToolkitConfigurationProfile y, a continuación, en el siguiente tutorial, [Configuración de los perfiles de MRTK](mr-learning-base-03.md), cambiará a DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="96b44-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="96b44-187">En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):</span><span class="sxs-lookup"><span data-stu-id="96b44-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="96b44-189">En la ventana Save Scene (Guardar escena), desplázate hasta la carpeta **Scenes** (Escenas) del proyecto, asígnale un nombre adecuado (por ejemplo, _GettingStarted_), y haz clic en el botón **Save** (Guardar) para guardar la escena:</span><span class="sxs-lookup"><span data-stu-id="96b44-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="96b44-191">Compilación de la aplicación a HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="96b44-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="96b44-192">1. Compilar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="96b44-192">1. Build the Unity project</span></span>

<span data-ttu-id="96b44-193">En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="96b44-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="96b44-194">En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):</span><span class="sxs-lookup"><span data-stu-id="96b44-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="96b44-196">En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="96b44-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="96b44-198">Espera a que Unity finalice el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="96b44-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="96b44-200">2. Compilar e implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="96b44-200">2. Build and deploy the application</span></span>

<span data-ttu-id="96b44-201">Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación.</span><span class="sxs-lookup"><span data-stu-id="96b44-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="96b44-202">Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="96b44-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="96b44-204">Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="96b44-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="96b44-205">Configure Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino:</span><span class="sxs-lookup"><span data-stu-id="96b44-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="96b44-207">Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.</span><span class="sxs-lookup"><span data-stu-id="96b44-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="96b44-208">En el caso de HoloLens, normalmente se compilará para la arquitectura ARM.</span><span class="sxs-lookup"><span data-stu-id="96b44-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="96b44-209">Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96b44-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="96b44-210">La solución recomendada es compilar para ARM64.</span><span class="sxs-lookup"><span data-stu-id="96b44-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="96b44-211">Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).</span><span class="sxs-lookup"><span data-stu-id="96b44-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="96b44-212">Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="96b44-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="96b44-213">Para ello, en el Explorador de soluciones, haga clic con el botón derecho en NombreDelProyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.</span><span class="sxs-lookup"><span data-stu-id="96b44-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="96b44-214">Conecte su HoloLens al equipo y, a continuación, seleccione **Depurar** > **Iniciar sin depurar** para compilar e realizar la implementación en el dispositivo:</span><span class="sxs-lookup"><span data-stu-id="96b44-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="96b44-216">Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="96b44-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="96b44-217">Ambos pasos pueden completarse siguiendo [estas instrucciones](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="96b44-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="96b44-218">También puede realizar la implementación en el [emulador de HoloLens](using-the-hololens-emulator.md) o crear un [paquete de aplicación](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.</span><span class="sxs-lookup"><span data-stu-id="96b44-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="96b44-219">Al usar Iniciar sin depurar, la aplicación se inicia automáticamente en el dispositivo sin el depurador de Visual Studio adjunto.</span><span class="sxs-lookup"><span data-stu-id="96b44-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="96b44-220">Seleccione **Compilar > Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="96b44-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="96b44-221">Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico).</span><span class="sxs-lookup"><span data-stu-id="96b44-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="96b44-222">Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="96b44-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="96b44-223">Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="96b44-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="96b44-224">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="96b44-224">Congratulations</span></span>

<span data-ttu-id="96b44-225">Ya ha implementado su primera aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="96b44-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="96b44-226">A medida que avance, debería ver una malla de asignación espacial que cubre todas las superficies que HoloLens ha percibido.</span><span class="sxs-lookup"><span data-stu-id="96b44-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="96b44-227">Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="96b44-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="96b44-228">Estas características son solo algunas partes fundamentales incluidas en MRTK.</span><span class="sxs-lookup"><span data-stu-id="96b44-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="96b44-229">En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.</span><span class="sxs-lookup"><span data-stu-id="96b44-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="96b44-230">Tutorial siguiente: 3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="96b44-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
