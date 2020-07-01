---
title: Sr Basics 100-Introducción a Unity
description: Aprenda a crear su primera aplicación básica "Hola a todos" de realidad mixta.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, inmersivo, VR, Mr, introducción, holograma, Academia, tutorial
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570309"
---
# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="6cce9-104">Aspectos básicos de realidad mixta (100): Introducción a Unity</span><span class="sxs-lookup"><span data-stu-id="6cce9-104">MR Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="6cce9-105">Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6cce9-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="6cce9-106">Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6cce9-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="6cce9-107">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6cce9-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="6cce9-108">Se mantendrán para que sigan funcionando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="6cce9-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="6cce9-109">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6cce9-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="6cce9-110">Este tutorial le guiará a través de la creación de una aplicación básica de realidad mixta compilada con Unity.</span><span class="sxs-lookup"><span data-stu-id="6cce9-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="6cce9-111">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="6cce9-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="6cce9-112">Curso</span><span class="sxs-lookup"><span data-stu-id="6cce9-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="6cce9-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="6cce9-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="6cce9-114"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="6cce9-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="6cce9-115">Aspectos básicos de realidad mixta (100): Introducción a Unity</span><span class="sxs-lookup"><span data-stu-id="6cce9-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="6cce9-116">✔️</span><span class="sxs-lookup"><span data-stu-id="6cce9-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="6cce9-117">✔️</span><span class="sxs-lookup"><span data-stu-id="6cce9-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="6cce9-118">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="6cce9-118">Prerequisites</span></span>

* <span data-ttu-id="6cce9-119">Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6cce9-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="6cce9-120">Capítulo 1: crear un nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="6cce9-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="6cce9-121">Para compilar una aplicación con Unity, primero debe crear un proyecto.</span><span class="sxs-lookup"><span data-stu-id="6cce9-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="6cce9-122">Este proyecto está organizado en algunas carpetas, lo más importante es la carpeta assets.</span><span class="sxs-lookup"><span data-stu-id="6cce9-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="6cce9-123">Se trata de la carpeta que contiene todos los recursos que se importan desde herramientas de creación de contenido digital como Maya, Max Cinema 4D o Photoshop, todo el código que se crea con Visual Studio o su editor de código favorito y cualquier número de archivos de contenido que Unity crea al crear escenas, animaciones y otros tipos de recursos de Unity en el editor.</span><span class="sxs-lookup"><span data-stu-id="6cce9-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="6cce9-124">Para compilar e implementar aplicaciones UWP, Unity puede exportar el proyecto como una solución de Visual Studio que contendrá todos los archivos de recursos y de código necesarios.</span><span class="sxs-lookup"><span data-stu-id="6cce9-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="6cce9-125">Iniciar Unity</span><span class="sxs-lookup"><span data-stu-id="6cce9-125">Start Unity</span></span>
2. <span data-ttu-id="6cce9-126">Seleccione **Nuevo paso**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-126">Select **New**</span></span>
3. <span data-ttu-id="6cce9-127">Escriba un nombre de proyecto (por ejemplo, "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="6cce9-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="6cce9-128">Escriba una ubicación para guardar el proyecto</span><span class="sxs-lookup"><span data-stu-id="6cce9-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="6cce9-129">Asegúrese de que la opción alternancia **3D** está seleccionada</span><span class="sxs-lookup"><span data-stu-id="6cce9-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="6cce9-130">Seleccione **crear proyecto** .</span><span class="sxs-lookup"><span data-stu-id="6cce9-130">Select **Create project**</span></span>

<span data-ttu-id="6cce9-131">Enhorabuena, todo está configurado para empezar a trabajar con las personalizaciones de realidad mixta ahora.</span><span class="sxs-lookup"><span data-stu-id="6cce9-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="6cce9-132">Capítulo 2: configuración de la cámara</span><span class="sxs-lookup"><span data-stu-id="6cce9-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="6cce9-133">La cámara principal de Unity controla el seguimiento de los cabezales y la representación de Stereoscopic.</span><span class="sxs-lookup"><span data-stu-id="6cce9-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="6cce9-134">Hay algunos cambios que se deben realizar en la cámara principal para usarlo con la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="6cce9-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="6cce9-135">Seleccionar archivo > nueva escena</span><span class="sxs-lookup"><span data-stu-id="6cce9-135">Select File > New Scene</span></span>

<span data-ttu-id="6cce9-136">En primer lugar, será más fácil diseñar la aplicación si imagina la posición inicial del usuario como (**X**: 0, **y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="6cce9-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="6cce9-137">Dado que la cámara principal está realizando el seguimiento del movimiento del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="6cce9-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="6cce9-138">Seleccionar **cámara principal** en el panel **jerarquía**</span><span class="sxs-lookup"><span data-stu-id="6cce9-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="6cce9-139">En el panel **Inspector** , busque el componente de **transformación** y cambie **la posición** de **(x**: 0, **y**: 1, **z**:-10) a (**x**: 0, **y**: 0, **z**: 0)</span><span class="sxs-lookup"><span data-stu-id="6cce9-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="6cce9-140">En segundo lugar, hay que pensar en el fondo de la cámara predeterminada.</span><span class="sxs-lookup"><span data-stu-id="6cce9-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="6cce9-141">**En el caso de las aplicaciones de HoloLens**, el mundo real debe aparecer detrás de todo lo que representa la cámara, no una textura SKYBOX.</span><span class="sxs-lookup"><span data-stu-id="6cce9-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="6cce9-142">Con la **cámara principal** aún seleccionada en el **Panel jerarquía** , busque el **componente cámara** en el panel **Inspector** y cambie la lista desplegable **Borrar marcas** de **SKYBOX** a **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="6cce9-143">Seleccione el selector de colores de **fondo** y cambie los valores **RGBA** a (0, 0, 0, 0)</span><span class="sxs-lookup"><span data-stu-id="6cce9-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="6cce9-144">**En el caso de las aplicaciones de realidad mixta destinadas a auriculares envolventes**, podemos usar la textura SKYBOX predeterminada que proporciona Unity.</span><span class="sxs-lookup"><span data-stu-id="6cce9-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="6cce9-145">Con la **cámara principal** aún seleccionada en el panel **jerarquía** , busque el componente **cámara** en el panel **Inspector** y mantenga la lista desplegable **Borrar marcas** en **SKYBOX**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="6cce9-146">En tercer lugar, permítanos considerar el plano de recorte cercano en Unity y evitar que los objetos se representen demasiado cerca de los ojos de los usuarios cuando un usuario se aproxime a un objeto o un objeto se aproxime a un usuario.</span><span class="sxs-lookup"><span data-stu-id="6cce9-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="6cce9-147">**En el caso de las aplicaciones de hololens**, el plano de recorte cercano se puede establecer en los contadores de 0,85 [recomendados de hololens](camera-in-unity.md#clip-planes) .</span><span class="sxs-lookup"><span data-stu-id="6cce9-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="6cce9-148">Con la **cámara principal** aún seleccionada en el **Panel jerarquía** , busque el componente **cámara** en el panel **Inspector** y cambie el campo **Near Clip plano** del valor predeterminado **0,3** a HoloLens recomendado **0,85**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="6cce9-149">**En el caso de las aplicaciones de realidad mixta destinadas a auriculares envolventes**, podemos usar la configuración predeterminada que proporciona Unity.</span><span class="sxs-lookup"><span data-stu-id="6cce9-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="6cce9-150">Con la **cámara principal** aún seleccionada en el panel de **jerarquías** , busque el componente de **cámara** en el panel **Inspector** y mantenga el campo de **plano de clip cercano** al valor predeterminado **0,3**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="6cce9-151">Por último, permítanos ahorrar nuestro progreso hasta ahora.</span><span class="sxs-lookup"><span data-stu-id="6cce9-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="6cce9-152">Para guardar los cambios de la escena, seleccione **archivo > guardar escena como**, asigne un nombre a la escena **principal**y seleccione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="6cce9-153">Capítulo 3: configuración del proyecto</span><span class="sxs-lookup"><span data-stu-id="6cce9-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="6cce9-154">En este capítulo, se establecerá una configuración de proyecto de Unity que nos ayude a dirigirse al SDK de Windows Holographic para el desarrollo.</span><span class="sxs-lookup"><span data-stu-id="6cce9-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="6cce9-155">También estableceremos algunos valores de calidad para nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="6cce9-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="6cce9-156">Por último, se asegurará de que los destinos de compilación estén establecidos en Plataforma universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="6cce9-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="6cce9-157">Configuración de rendimiento y calidad de Unity</span><span class="sxs-lookup"><span data-stu-id="6cce9-157">Unity performance and quality settings</span></span>

<span data-ttu-id="6cce9-158">**Configuración de calidad de Unity para HoloLens**</span><span class="sxs-lookup"><span data-stu-id="6cce9-158">**Unity quality settings for HoloLens**</span></span>

![Configuración de calidad de Unity para HoloLens](images/qualitysettings.png)

<span data-ttu-id="6cce9-160">Dado que mantener una velocidad de fotogramas elevada en HoloLens es tan importante, queremos que la configuración de calidad esté optimizada para un rendimiento más rápido.</span><span class="sxs-lookup"><span data-stu-id="6cce9-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="6cce9-161">Para obtener información más detallada sobre el rendimiento, [recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="6cce9-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="6cce9-162">Seleccione **editar > configuración del proyecto > calidad**</span><span class="sxs-lookup"><span data-stu-id="6cce9-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="6cce9-163">Seleccione la **lista desplegable** en el logotipo de **plataforma universal de Windows** y seleccione **muy baja**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low**.</span></span> <span data-ttu-id="6cce9-164">Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna Plataforma universal de Windows y una fila **muy baja** es verde.</span><span class="sxs-lookup"><span data-stu-id="6cce9-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="6cce9-165">En el **caso de las aplicaciones de realidad mixta destinadas a ocluidos**, puede dejar la configuración de calidad a sus valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="6cce9-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="6cce9-166">SDK de Windows 10 de destino</span><span class="sxs-lookup"><span data-stu-id="6cce9-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="6cce9-167">**SDK de Windows Holographic de destino**</span><span class="sxs-lookup"><span data-stu-id="6cce9-167">**Target Windows Holographic SDK**</span></span>

![SDK de Windows Holographic de destino](images/xrsettings.png)

<span data-ttu-id="6cce9-169">Necesitamos que Unity sepa que la aplicación que se está intentando exportar debe crear una [vista envolvente](app-views.md) en lugar de una vista 2D.</span><span class="sxs-lookup"><span data-stu-id="6cce9-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="6cce9-170">Para ello, se habilita la compatibilidad con la realidad virtual en Unity que tiene como destino el SDK de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6cce9-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="6cce9-171">Vaya a **editar > configuración del proyecto > Player**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="6cce9-172">En el **panel Inspector** de configuración del reproductor, seleccione el icono de **plataforma universal de Windows** .</span><span class="sxs-lookup"><span data-stu-id="6cce9-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="6cce9-173">Expanda el grupo **XR Settings** (Configuración de XR).</span><span class="sxs-lookup"><span data-stu-id="6cce9-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="6cce9-174">En la sección **representación** , active la casilla **compatibilidad con realidad virtual** para agregar una nueva lista de **SDK de realidad virtual** .</span><span class="sxs-lookup"><span data-stu-id="6cce9-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="6cce9-175">Compruebe que **Windows Mixed Reality** (Mixed Reality de Windows) aparece en la lista.</span><span class="sxs-lookup"><span data-stu-id="6cce9-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="6cce9-176">En caso contrario, seleccione el botón **+** situado en la parte inferior de la lista y elija **Windows Mixed Reality** (Mixed Reality de Windows).</span><span class="sxs-lookup"><span data-stu-id="6cce9-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="6cce9-177">Si no ve el icono de **plataforma universal de Windows** , asegúrese de que ha seleccionado plataforma universal de Windows compatibilidad con la compilación durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="6cce9-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="6cce9-178">Si no, es posible que deba volver a instalar Unity con la instalación correcta de Windows.</span><span class="sxs-lookup"><span data-stu-id="6cce9-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="6cce9-179">Trabajo maravilla en la obtención de la configuración del proyecto aplicada.</span><span class="sxs-lookup"><span data-stu-id="6cce9-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="6cce9-180">A continuación, vamos a agregar un holograma.</span><span class="sxs-lookup"><span data-stu-id="6cce9-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="6cce9-181">Capítulo 4: crear un cubo</span><span class="sxs-lookup"><span data-stu-id="6cce9-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="6cce9-182">La creación de un cubo en el proyecto de Unity es igual que crear cualquier otro objeto en Unity.</span><span class="sxs-lookup"><span data-stu-id="6cce9-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="6cce9-183">Colocar un cubo delante del usuario es fácil porque el sistema de coordenadas de Unity está asignado al mundo real, donde un medidor en Unity es aproximadamente un medidor del mundo real.</span><span class="sxs-lookup"><span data-stu-id="6cce9-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="6cce9-184">En la esquina superior izquierda del panel de **jerarquías** , seleccione la lista desplegable **crear** y elija **objeto 3D > cubo**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="6cce9-185">Seleccionar el **cubo** recién creado en el panel **jerarquía**</span><span class="sxs-lookup"><span data-stu-id="6cce9-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="6cce9-186">En el **Inspector** , busque el componente de **transformación** y cambie la **posición** a (**X**: 0, **y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="6cce9-186">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="6cce9-187">*Esto coloca los medidores del cubo 2 delante de la posición inicial del usuario.*</span><span class="sxs-lookup"><span data-stu-id="6cce9-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="6cce9-188">En el componente de **transformación** , cambie **rotación** a (**x**: 45 **, y**: 45, **z**: 45) y cambie la **escala** a (**x**: 0,25, **y**: 0,25, **z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="6cce9-188">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="6cce9-189">*Esto escala el cubo a 0,25 metros.*</span><span class="sxs-lookup"><span data-stu-id="6cce9-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="6cce9-190">Para guardar los cambios de la escena, seleccione **archivo > guardar escena**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-190">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="6cce9-191">Capítulo 5: comprobar en el dispositivo desde el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="6cce9-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="6cce9-192">Ahora que hemos creado el cubo, es el momento de realizar una comprobación rápida del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6cce9-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="6cce9-193">Puede hacerlo directamente desde el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="6cce9-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="6cce9-194">Instalación inicial</span><span class="sxs-lookup"><span data-stu-id="6cce9-194">Initial setup</span></span>

1. <span data-ttu-id="6cce9-195">En el equipo de desarrollo, en Unity, Abra **archivo >** ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="6cce9-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="6cce9-196">Cambie **plataforma** a **plataforma universal de Windows** y haga clic en **cambiar plataforma**</span><span class="sxs-lookup"><span data-stu-id="6cce9-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="6cce9-197">Para HoloLens, use Unity Remoting</span><span class="sxs-lookup"><span data-stu-id="6cce9-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="6cce9-198">En HoloLens, instale y ejecute el [reproductor de comunicación remota holográfica](holographic-remoting-player.md), disponible en la tienda Windows.</span><span class="sxs-lookup"><span data-stu-id="6cce9-198">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="6cce9-199">Inicie la aplicación en el dispositivo y se especificará un estado de espera y se mostrará la dirección IP del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6cce9-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="6cce9-200">Anote la dirección IP.</span><span class="sxs-lookup"><span data-stu-id="6cce9-200">Note down the IP.</span></span>
2. <span data-ttu-id="6cce9-201">Abra **Window > XR > la emulación holográfica**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-201">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="6cce9-202">Cambiar el **modo de emulación** de **ninguno** a **remoto a dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-202">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="6cce9-203">En **equipo remoto**, escriba la dirección IP de su HoloLens indicada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6cce9-203">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="6cce9-204">Haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-204">Click **Connect**.</span></span>
6. <span data-ttu-id="6cce9-205">Asegúrese de que el estado de la **conexión** cambia a verde **conectado**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-205">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="6cce9-206">Ahora puede hacer clic en **reproducir** en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="6cce9-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="6cce9-207">Ahora podrá ver el cubo en el dispositivo y en el editor.</span><span class="sxs-lookup"><span data-stu-id="6cce9-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="6cce9-208">Puede pausar, inspeccionar objetos y depurar del mismo modo que está ejecutando una aplicación en el editor, ya que esto es esencialmente lo que está ocurriendo, pero con vídeo, audio y entrada de dispositivo transmitidos entre la red entre el equipo host y el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6cce9-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="6cce9-209">Para otros auriculares compatibles con la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="6cce9-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="6cce9-210">Conecte los auriculares a su equipo de desarrollo con el cable USB y el cable de puerto de pantalla o HDMI.</span><span class="sxs-lookup"><span data-stu-id="6cce9-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="6cce9-211">Inicie el **portal de realidad mixta** y asegúrese de que ha completado la primera experiencia de ejecución.</span><span class="sxs-lookup"><span data-stu-id="6cce9-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="6cce9-212">Desde Unity, ahora puede hacer clic en el botón reproducir.</span><span class="sxs-lookup"><span data-stu-id="6cce9-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="6cce9-213">Ahora podrá ver la representación del cubo en el casco de la realidad mixta y en el editor.</span><span class="sxs-lookup"><span data-stu-id="6cce9-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="6cce9-214">Capítulo 6: compilar e implementar en el dispositivo desde Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6cce9-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="6cce9-215">Ahora estamos listos para compilar el proyecto en Visual Studio e implementarlo en nuestro dispositivo de destino.</span><span class="sxs-lookup"><span data-stu-id="6cce9-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="6cce9-216">Exportar a la solución de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6cce9-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="6cce9-217">Abra el **archivo > ventana Configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="6cce9-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="6cce9-218">Haga clic en **Agregar escenas abiertas** para agregar la escena.</span><span class="sxs-lookup"><span data-stu-id="6cce9-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="6cce9-219">Cambie **plataforma** a **plataforma universal de Windows** y haga clic en **cambiar plataforma**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
1. <span data-ttu-id="6cce9-220">En **plataforma universal de Windows** configuración, asegúrese de que el **SDK** es **universal 10**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10**.</span></span>
1. <span data-ttu-id="6cce9-221">En dispositivo de destino, deje en **cualquier dispositivo** para ocluidos muestra o cambie a **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
1. <span data-ttu-id="6cce9-222">El **tipo de compilación de UWP** debe ser **D3D**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-222">**UWP Build Type** should be **D3D**.</span></span>
1. <span data-ttu-id="6cce9-223">El **SDK de UWP** podría dejarse en la **versión más reciente instalada**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-223">**UWP SDK** could be left at **Latest installed**.</span></span>
1. <span data-ttu-id="6cce9-224">Haga clic en **Generar**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-224">Click **Build**.</span></span>
1. <span data-ttu-id="6cce9-225">En el explorador de archivos, haga clic en **nueva carpeta** y asigne el nombre **"app"** a la carpeta.</span><span class="sxs-lookup"><span data-stu-id="6cce9-225">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
1. <span data-ttu-id="6cce9-226">Con la carpeta de **aplicaciones** seleccionada, haga clic en el botón **Seleccionar carpeta** .</span><span class="sxs-lookup"><span data-stu-id="6cce9-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="6cce9-227">Cuando Unity termine de compilar, aparecerá una ventana del explorador de archivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="6cce9-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="6cce9-228">Abra la carpeta de la **aplicación** en el explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="6cce9-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="6cce9-229">Abra la solución de Visual Studio generada (MixedRealityIntroduction. sln en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="6cce9-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="6cce9-230">Compilar la solución de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6cce9-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="6cce9-231">Por último, se compilará la solución de Visual Studio exportada, se implementará y se probará en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6cce9-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="6cce9-232">Con la barra de herramientas superior de Visual Studio, cambie el destino de **Debug** a **Release** y de **ARM** a **x86**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="6cce9-233">Las instrucciones difieren en cuanto a la implementación en un dispositivo frente al emulador.</span><span class="sxs-lookup"><span data-stu-id="6cce9-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="6cce9-234">Siga las instrucciones que coincidan con la configuración.</span><span class="sxs-lookup"><span data-stu-id="6cce9-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="6cce9-235">Implementación en dispositivo de realidad mixta a través de Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="6cce9-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="6cce9-236">Haga clic en la flecha situada junto al botón **equipo local** y cambie el destino de implementación a **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="6cce9-237">Escriba la dirección IP del dispositivo de realidad mixta y cambie el **modo de autenticación** a universal (protocolo sin cifrar) para HoloLens y **Windows** para otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6cce9-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="6cce9-238">Haga clic en **Depurar > iniciar sin depurar**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-238">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="6cce9-239">**En el caso de HoloLens**, si esta es la primera vez que se implementa en el dispositivo, tendrá que emparejar [con Visual Studio](using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6cce9-239">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="6cce9-240">Implementación en dispositivo de realidad mixta a través de USB</span><span class="sxs-lookup"><span data-stu-id="6cce9-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="6cce9-241">Asegúrese de que el dispositivo está conectado a través del cable USB.</span><span class="sxs-lookup"><span data-stu-id="6cce9-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="6cce9-242">**Para HoloLens**, haga clic en la flecha situada junto al botón **equipo local** y cambie el destino de implementación a **dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-242">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="6cce9-243">**Para dirigirse a dispositivos ocluidos conectados al equipo**, mantenga la configuración en equipo local.</span><span class="sxs-lookup"><span data-stu-id="6cce9-243">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="6cce9-244">Asegúrese de que tiene el **portal de realidad mixta** en ejecución.</span><span class="sxs-lookup"><span data-stu-id="6cce9-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="6cce9-245">Haga clic en **Depurar > iniciar sin depurar**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-245">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="6cce9-246">Implementar en el emulador</span><span class="sxs-lookup"><span data-stu-id="6cce9-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="6cce9-247">Haga clic en la flecha situada junto al botón **dispositivo** y, en la lista desplegable, seleccione **emulador de HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="6cce9-248">Haga clic en **Depurar > iniciar sin depurar**.</span><span class="sxs-lookup"><span data-stu-id="6cce9-248">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="6cce9-249">Probar la aplicación</span><span class="sxs-lookup"><span data-stu-id="6cce9-249">Try out your app</span></span>

<span data-ttu-id="6cce9-250">Ahora que la aplicación está implementada, intente mover todo el cubo y observe que permanece en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="6cce9-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cce9-251">Consulte también</span><span class="sxs-lookup"><span data-stu-id="6cce9-251">See also</span></span>

* [<span data-ttu-id="6cce9-252">Introducción al desarrollo de Unity</span><span class="sxs-lookup"><span data-stu-id="6cce9-252">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="6cce9-253">Procedimientos recomendados para trabajar con Unity y Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6cce9-253">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="6cce9-254">Aspectos básicos de realidad mixta (101)</span><span class="sxs-lookup"><span data-stu-id="6cce9-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="6cce9-255">Aspectos básicos de realidad mixta (101E)</span><span class="sxs-lookup"><span data-stu-id="6cce9-255">MR Basics 101E</span></span>](holograms-101e.md)
