---
title: Entrada MR 213
description: Siga este tutorial de programación con Unity, Visual Studio e inmersivos para conocer los detalles de los controladores de movimiento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, unity mixedrealitytoolkit, envolvente, controlador, academy, tutorial de movimiento
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605704"
---
>[!NOTE]
><span data-ttu-id="1eb63-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="1eb63-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1eb63-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1eb63-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="1eb63-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1eb63-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="1eb63-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1eb63-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1eb63-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1eb63-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="1eb63-110">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="1eb63-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="1eb63-111">Controladores de movimiento en el mundo de realidad mixta agregan otro nivel de interactividad.</span><span class="sxs-lookup"><span data-stu-id="1eb63-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="1eb63-112">Con [controladores de movimiento](motion-controllers.md), podemos interactuar con objetos de una manera más natural, similar a nuestras interacciones físicas en la vida real, aumentar inmersión directamente y Deleite a su experiencia de aplicación.</span><span class="sxs-lookup"><span data-stu-id="1eb63-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="1eb63-113">En MR 213 de entrada, exploraremos los eventos de entrada del controlador de movimiento mediante la creación de una experiencia simple pintura espacial.</span><span class="sxs-lookup"><span data-stu-id="1eb63-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="1eb63-114">Con esta aplicación, los usuarios pueden pintar en un espacio tridimensional con diversos tipos de pinceles y colores.</span><span class="sxs-lookup"><span data-stu-id="1eb63-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="1eb63-115">Temas tratados en este tutorial</span><span class="sxs-lookup"><span data-stu-id="1eb63-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![Topic2 MixedReality213](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="1eb63-119">**Visualización de controlador**</span><span class="sxs-lookup"><span data-stu-id="1eb63-119">**Controller visualization**</span></span>|<span data-ttu-id="1eb63-120">**Eventos de entrada del controlador**</span><span class="sxs-lookup"><span data-stu-id="1eb63-120">**Controller input events**</span></span>|<span data-ttu-id="1eb63-121">**Interfaz de usuario y dispositivo personalizado**</span><span class="sxs-lookup"><span data-stu-id="1eb63-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="1eb63-122">Obtenga información sobre cómo representar modelos de controlador de movimiento en modo de juego de Unity y en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1eb63-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="1eb63-123">Comprender los distintos tipos de eventos de botón y sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1eb63-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="1eb63-124">Obtenga información sobre los elementos de interfaz de usuario en la parte superior del controlador de superposición o personalizarlo completamente.</span><span class="sxs-lookup"><span data-stu-id="1eb63-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="1eb63-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1eb63-126">Curso</span><span class="sxs-lookup"><span data-stu-id="1eb63-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1eb63-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1eb63-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1eb63-128"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="1eb63-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1eb63-129">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="1eb63-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="1eb63-130">✔️</span><span class="sxs-lookup"><span data-stu-id="1eb63-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1eb63-131">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="1eb63-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1eb63-132">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1eb63-132">Prerequisites</span></span>

<span data-ttu-id="1eb63-133">Consulte la lista de comprobación de instalación para inmersivos en [esta página](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1eb63-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="1eb63-134">Este tutorial requiere [2017.2.1p2 de Unity](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="1eb63-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="1eb63-135">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="1eb63-135">Project files</span></span>

* <span data-ttu-id="1eb63-136">[Descargar los archivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) requerida por el proyecto y extraiga los archivos en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="1eb63-137">Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="1eb63-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="1eb63-138">Programa de instalación de Unity</span><span class="sxs-lookup"><span data-stu-id="1eb63-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="1eb63-139">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-139">Objectives</span></span>

* <span data-ttu-id="1eb63-140">Optimizar el desarrollo de Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1eb63-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="1eb63-141">Configuración de la cámara de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1eb63-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="1eb63-142">Configuración del entorno</span><span class="sxs-lookup"><span data-stu-id="1eb63-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-143">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-143">Instructions</span></span>

* <span data-ttu-id="1eb63-144">Inicie Unity.</span><span class="sxs-lookup"><span data-stu-id="1eb63-144">Start Unity.</span></span>
* <span data-ttu-id="1eb63-145">Seleccione **abierto**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-145">Select **Open**.</span></span>
* <span data-ttu-id="1eb63-146">Vaya al escritorio y buscar el **MixedReality213-master** carpetas que anteriormente sin archivar.</span><span class="sxs-lookup"><span data-stu-id="1eb63-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="1eb63-147">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="1eb63-148">Una vez que Unity termina de cargar archivos de proyecto, podrá ver el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1eb63-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="1eb63-149">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="1eb63-151">Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="1eb63-152">Establezca el dispositivo de destino en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="1eb63-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="1eb63-153">Establece el tipo de compilación en **D3D**</span><span class="sxs-lookup"><span data-stu-id="1eb63-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="1eb63-154">Establece el SDK **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="1eb63-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="1eb63-155">Comprobar **Unity C# proyectos**</span><span class="sxs-lookup"><span data-stu-id="1eb63-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="1eb63-156">Esto permite que modificar los archivos de script en el proyecto de Visual Studio sin volver a generar el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1eb63-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="1eb63-157">Haga clic en **configuración del Reproductor**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="1eb63-158">En el **Inspector** panel, desplácese hacia abajo hasta la parte inferior</span><span class="sxs-lookup"><span data-stu-id="1eb63-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="1eb63-159">En la configuración de XR, comprobar **compatibles de realidad Virtual**</span><span class="sxs-lookup"><span data-stu-id="1eb63-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="1eb63-160">En el SDK de realidad Virtual, seleccione **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="1eb63-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="1eb63-162">Cerrar **configuración de compilación** ventana.</span><span class="sxs-lookup"><span data-stu-id="1eb63-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="1eb63-163">Estructura del proyecto</span><span class="sxs-lookup"><span data-stu-id="1eb63-163">Project structure</span></span>

<span data-ttu-id="1eb63-164">Este tutorial se usa  **[Kit de herramientas de realidad mixta - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="1eb63-165">Puede encontrar las versiones en [esta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="1eb63-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="1eb63-167">**Completado escenas para su referencia**</span><span class="sxs-lookup"><span data-stu-id="1eb63-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="1eb63-168">Encontrará dos escenas Unity completadas en **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="1eb63-169">**MixedReality213**: Escena completado con el único pincel</span><span class="sxs-lookup"><span data-stu-id="1eb63-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="1eb63-170">**MixedReality213Advanced**: Completar la escena para diseño avanzado con varios pinceles</span><span class="sxs-lookup"><span data-stu-id="1eb63-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="1eb63-171">**Nueva configuración de la escena para el tutorial**</span><span class="sxs-lookup"><span data-stu-id="1eb63-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="1eb63-172">En Unity, haga clic en **archivo > nueva escena**</span><span class="sxs-lookup"><span data-stu-id="1eb63-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="1eb63-173">Eliminar **cámara principal** y **luz direccional**</span><span class="sxs-lookup"><span data-stu-id="1eb63-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="1eb63-174">Desde el **panel proyecto**, busque y arrastre el prefabricados siguientes en el **jerarquía** panel:</span><span class="sxs-lookup"><span data-stu-id="1eb63-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="1eb63-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="1eb63-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="1eb63-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="1eb63-176">Assets/AppPrefabs/**Environment**</span></span>

![Cámara y entorno](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="1eb63-178">Hay dos prefabricados de cámara en el Kit de herramientas de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="1eb63-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="1eb63-179">**MixedRealityCamera.prefab**: Solo la cámara</span><span class="sxs-lookup"><span data-stu-id="1eb63-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="1eb63-180">**MixedRealityCameraParent.prefab**: Cámara Teleportation + límites</span><span class="sxs-lookup"><span data-stu-id="1eb63-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="1eb63-181">En este tutorial, usaremos **MixedRealityCamera** sin teleportation característica.</span><span class="sxs-lookup"><span data-stu-id="1eb63-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="1eb63-182">Por este motivo, hemos agregado simple **entorno** prefabricado que contiene un piso básico para que el usuario sienta toma de tierra.</span><span class="sxs-lookup"><span data-stu-id="1eb63-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="1eb63-183">Para obtener más información sobre la teleportation con **MixedRealityCameraParent**, consulte [avanzado diseño - Teleportation y desplazamiento](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="1eb63-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="1eb63-184">**Programa de instalación skybox**</span><span class="sxs-lookup"><span data-stu-id="1eb63-184">**Skybox setup**</span></span>
* <span data-ttu-id="1eb63-185">Haga clic en **Ventana > iluminación > configuración**</span><span class="sxs-lookup"><span data-stu-id="1eb63-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="1eb63-186">Haga clic en el círculo en el lado derecho de la **campo Skybox Material**</span><span class="sxs-lookup"><span data-stu-id="1eb63-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="1eb63-187">Escriba "gray" y seleccione **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="1eb63-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="1eb63-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="1eb63-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Establecer skybox](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="1eb63-190">Comprobar **Skybox** opción para poder ver asignado skybox degradado gris</span><span class="sxs-lookup"><span data-stu-id="1eb63-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Opción de alternancia skybox](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="1eb63-192">La escena con MixedRealityCamera, entorno y skybox gris tendrá un aspecto similar al siguiente.</span><span class="sxs-lookup"><span data-stu-id="1eb63-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![Entorno MixedReality213](images/mr213-environment-600px.jpg)
* <span data-ttu-id="1eb63-194">Haga clic en **archivo > Guardar escena como**</span><span class="sxs-lookup"><span data-stu-id="1eb63-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="1eb63-195">**Guardar** la escena en la carpeta de escenas con cualquier nombre</span><span class="sxs-lookup"><span data-stu-id="1eb63-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="1eb63-196">Capítulo 1: visualización de controlador</span><span class="sxs-lookup"><span data-stu-id="1eb63-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="1eb63-197">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-197">Objectives</span></span>

* <span data-ttu-id="1eb63-198">Obtenga información sobre cómo representar los modelos en modo de juego de Unity y en tiempo de ejecución de controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="1eb63-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="1eb63-199">Windows Mixed Reality proporciona un modelo de controlador animado para la visualización del controlador.</span><span class="sxs-lookup"><span data-stu-id="1eb63-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="1eb63-200">Hay varios enfoques que puede emplear para la visualización del controlador en la aplicación:</span><span class="sxs-lookup"><span data-stu-id="1eb63-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="1eb63-201">Valor predeterminado: mediante el controlador predeterminado sin modificaciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="1eb63-202">Hybrid - utilizando el controlador de forma predeterminada, pero personalizar algunas de sus elementos o superposición de componentes de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="1eb63-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="1eb63-203">Reemplazo - mediante su propio personalizar un modelo 3D para el controlador</span><span class="sxs-lookup"><span data-stu-id="1eb63-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="1eb63-204">En este capítulo, aprendemos sobre los ejemplos de estas personalizaciones del controlador.</span><span class="sxs-lookup"><span data-stu-id="1eb63-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-205">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-205">Instructions</span></span>

* <span data-ttu-id="1eb63-206">En el **proyecto** del panel, escriba **MotionControllers** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="1eb63-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="1eb63-207">También puede encontrarlo en activos/HoloToolkit/entrada/prefabricados /.</span><span class="sxs-lookup"><span data-stu-id="1eb63-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="1eb63-208">Arrastre el **MotionControllers** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-209">Haga clic en el **MotionControllers** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="1eb63-210">**MotionControllers prefabricado**</span><span class="sxs-lookup"><span data-stu-id="1eb63-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="1eb63-211">**MotionControllers** prefabricado tiene un **MotionControllerVisualizer** secuencia de comandos que proporciona las ranuras para los modelos de controlador alternativo.</span><span class="sxs-lookup"><span data-stu-id="1eb63-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="1eb63-212">Si asigna sus propios modelos 3D personalizados como una mano o un filo y compruebe 'Siempre uso alternativo izquierda/derecha Model', los verá en lugar del modelo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="1eb63-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="1eb63-213">Usaremos esta ranura en el capítulo 4 para reemplazar el modelo de controlador con un pincel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="1eb63-215">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="1eb63-215">**Instructions**</span></span>
* <span data-ttu-id="1eb63-216">En el **Inspector** del panel, haga doble clic en **MotionControllerVisualizer** secuencia de comandos para ver el código de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1eb63-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="1eb63-217">**Secuencia de comandos MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="1eb63-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="1eb63-218">El **MotionControllerVisualizer** y **MotionControllerInfo** clases proporcionan los medios para tener acceso y modificar los modelos del controlador predeterminado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="1eb63-219">**MotionControllerVisualizer** se suscribe a Unity **InteractionSourceDetected** eventos y automáticamente crea instancias de los modelos de controlador cuando se encuentran.</span><span class="sxs-lookup"><span data-stu-id="1eb63-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="1eb63-220">Los modelos de controlador se entregan según [la especificación glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="1eb63-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="1eb63-221">Este formato se ha creado para proporcionar un formato común, al tiempo que mejora el proceso detrás de transmisión y desempaquetar los recursos en 3D.</span><span class="sxs-lookup"><span data-stu-id="1eb63-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="1eb63-222">En este caso, se debe recuperar y cargar los modelos de controlador en tiempo de ejecución, como queremos que el usuario experimente lo más fácilmente posible, y no se garantiza la versión de los controladores de movimiento del usuario puede estar usando.</span><span class="sxs-lookup"><span data-stu-id="1eb63-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="1eb63-223">Este curso, mediante el Kit de herramientas de realidad mixta, usa una versión del grupo Khronos [UnityGLTF proyecto](https://github.com/KhronosGroup/UnityGLTF).</span><span class="sxs-lookup"><span data-stu-id="1eb63-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="1eb63-224">Una vez que se ha entregado el controlador, pueden utilizar secuencias de comandos **MotionControllerInfo** para buscar las transformaciones de los elementos de un controlador específico, por lo que pueden colocarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="1eb63-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="1eb63-225">En un capítulo posterior, se obtendrá información sobre cómo usar estas secuencias de comandos para asociar elementos de interfaz de usuario a los controladores.</span><span class="sxs-lookup"><span data-stu-id="1eb63-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="1eb63-226">*En algunos scripts, encontrará bloques de código con **#if! UNITY_EDITOR** o **UNITY_WSA**. Estos bloques de código se ejecutan solo en el tiempo de ejecución UWP al implementar en Windows. Esto es porque el conjunto de API usados por el editor de Unity y el tiempo de ejecución de la aplicación para UWP son diferentes.*</span><span class="sxs-lookup"><span data-stu-id="1eb63-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="1eb63-227">**Guardar** la escena y haga clic en el **reproducir** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="1eb63-228">Podrá ver la escena con los controladores de movimiento de los auriculares.</span><span class="sxs-lookup"><span data-stu-id="1eb63-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="1eb63-229">Puede ver animaciones detalladas para los clics de botón, el movimiento de tecla de navegación y panel táctil táctil resaltado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller visualización predeterminada](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="1eb63-231">Capítulo 2: asociar elementos de interfaz de usuario para el controlador</span><span class="sxs-lookup"><span data-stu-id="1eb63-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="1eb63-232">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-232">Objectives</span></span>

* <span data-ttu-id="1eb63-233">Obtenga información acerca de los elementos de los controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="1eb63-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="1eb63-234">Obtenga información sobre cómo asociar los objetos a partes específicas de los controladores</span><span class="sxs-lookup"><span data-stu-id="1eb63-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="1eb63-235">En este capítulo, obtendrá información sobre cómo agregar elementos de la interfaz de usuario para el controlador que el usuario puede tener acceso fácilmente y manipular en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="1eb63-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="1eb63-236">También aprenderá a agregar un selector de colores simple mediante el panel táctil de entrada de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="1eb63-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-237">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-237">Instructions</span></span>

* <span data-ttu-id="1eb63-238">En el **proyecto** del panel, buscar **MotionControllerInfo** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="1eb63-239">Los resultados de búsqueda, haga doble clic en **MotionControllerInfo** secuencia de comandos para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="1eb63-240">**Secuencia de comandos MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="1eb63-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="1eb63-241">El primer paso es elegir qué elemento del controlador que desee asociar a la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="1eb63-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="1eb63-242">Estos elementos se definen en **ControllerElementEnum** en **MotionControllerInfo.cs**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="1eb63-244">**Página principal**</span><span class="sxs-lookup"><span data-stu-id="1eb63-244">**Home**</span></span>
* <span data-ttu-id="1eb63-245">**Menú**</span><span class="sxs-lookup"><span data-stu-id="1eb63-245">**Menu**</span></span>
* <span data-ttu-id="1eb63-246">**Grasp**</span><span class="sxs-lookup"><span data-stu-id="1eb63-246">**Grasp**</span></span>
* <span data-ttu-id="1eb63-247">**Tecla de navegación**</span><span class="sxs-lookup"><span data-stu-id="1eb63-247">**Thumbstick**</span></span>
* <span data-ttu-id="1eb63-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="1eb63-248">**Select**</span></span>
* <span data-ttu-id="1eb63-249">**Panel táctil**</span><span class="sxs-lookup"><span data-stu-id="1eb63-249">**Touchpad**</span></span>
* <span data-ttu-id="1eb63-250">**Postura señalador** : este elemento representa la punta del controlador que señala hacia delante.</span><span class="sxs-lookup"><span data-stu-id="1eb63-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="1eb63-251">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="1eb63-251">**Instructions**</span></span>
* <span data-ttu-id="1eb63-252">En el **proyecto** del panel, buscar **AttachToController** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="1eb63-253">Los resultados de búsqueda, haga doble clic en **AttachToController** secuencia de comandos para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="1eb63-254">**Secuencia de comandos AttachToController**</span><span class="sxs-lookup"><span data-stu-id="1eb63-254">**AttachToController script**</span></span>

<span data-ttu-id="1eb63-255">El **AttachToController** script proporciona una manera sencilla para asociar todos los objetos a un lateralidad del controlador especificado y el elemento.</span><span class="sxs-lookup"><span data-stu-id="1eb63-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="1eb63-256">En **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="1eb63-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="1eb63-257">Compruebe con diestro o zurdo **MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="1eb63-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="1eb63-258">Obtener un elemento específico del controlador mediante **MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="1eb63-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="1eb63-259">Después de recuperar el elemento transformar desde el modelo de controlador primario, el objeto situado debajo de él y rotación o la posición local del objeto se establece en cero.</span><span class="sxs-lookup"><span data-stu-id="1eb63-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="1eb63-260">La manera más sencilla de usar **AttachToController** script es heredar de él, como hemos hecho en el caso de **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="1eb63-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="1eb63-261">Simplemente reemplace el **OnAttachToController** y **OnDetatchFromController** funciones para realizar la instalación / desglose cuando el controlador se ha detectado o desconectado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="1eb63-262">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="1eb63-262">**Instructions**</span></span>
* <span data-ttu-id="1eb63-263">En el **proyecto** del panel, escriba en el cuadro de búsqueda **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="1eb63-264">También puede encontrarlo en activos/AppPrefabs /.</span><span class="sxs-lookup"><span data-stu-id="1eb63-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="1eb63-265">Arrastre **ColorPickerWheel** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-266">Haga clic en el **ColorPickerWheel** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-267">En el **Inspector** del panel, haga doble clic en **ColorPickerWheel** secuencia de comandos para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefabricado](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="1eb63-269">**Secuencia de comandos ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="1eb63-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="1eb63-270">Puesto que **ColorPickerWheel** hereda **AttachToController**, muestra **diestro o zurdo** y **elemento** en el  **Inspector de** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="1eb63-271">Se adjuntará la interfaz de usuario para el elemento de panel táctil en el controlador de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="1eb63-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Secuencia de comandos ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="1eb63-273">**ColorPickerWheel** invalida la **OnAttachToController** y **OnDetatchFromController** para suscribirse al evento de entrada que se usará en el capítulo siguiente para la selección de color con panel táctil de entrada.</span><span class="sxs-lookup"><span data-stu-id="1eb63-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="1eb63-274">**Guardar** la escena y haga clic en el **reproducir** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="1eb63-275">**Método alternativo para asociar los objetos a los controladores**</span><span class="sxs-lookup"><span data-stu-id="1eb63-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="1eb63-276">Se recomienda que las secuencias de comandos heredan **AttachToController** e invalidar **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="1eb63-277">Sin embargo, esto no sea siempre posible.</span><span class="sxs-lookup"><span data-stu-id="1eb63-277">However, this may not always be possible.</span></span> <span data-ttu-id="1eb63-278">Una alternativa es usarlo como un componente independiente.</span><span class="sxs-lookup"><span data-stu-id="1eb63-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="1eb63-279">Esto puede ser útil cuando desee adjuntar un prefabricado existente a un controlador sin refactorizar las secuencias de comandos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="1eb63-280">Simplemente haga que su clase esperar IsAttached para establecerse en true antes de realizar ninguna configuración.</span><span class="sxs-lookup"><span data-stu-id="1eb63-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="1eb63-281">La manera más sencilla de hacerlo es mediante una corrutina de 'Start'.</span><span class="sxs-lookup"><span data-stu-id="1eb63-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="1eb63-282">Capítulo 3: trabajar con la entrada del teclado táctil</span><span class="sxs-lookup"><span data-stu-id="1eb63-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="1eb63-283">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-283">Objectives</span></span>

* <span data-ttu-id="1eb63-284">Obtenga información sobre cómo obtener eventos de datos de entrada de teclado táctil</span><span class="sxs-lookup"><span data-stu-id="1eb63-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="1eb63-285">Aprenda a usar la información de posición del eje de panel táctil para su experiencia de aplicación</span><span class="sxs-lookup"><span data-stu-id="1eb63-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-286">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-286">Instructions</span></span>

* <span data-ttu-id="1eb63-287">En el **jerarquía** del panel, haga clic en **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="1eb63-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="1eb63-288">En el **Inspector** panel **Animatior**, haga doble clic en **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="1eb63-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="1eb63-289">Podrá ver **animador** pestaña abierto</span><span class="sxs-lookup"><span data-stu-id="1eb63-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="1eb63-290">**Mostrar u ocultar la interfaz de usuario con el controlador de animación de Unity**</span><span class="sxs-lookup"><span data-stu-id="1eb63-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="1eb63-291">Para mostrar y ocultar el **ColorPickerWheel** la interfaz de usuario con la animación, estamos usando [sistema de animación de Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="1eb63-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="1eb63-292">Establecer el **ColorPickerWheel**del **Visible** propiedad en true o false desencadenadores **mostrar** y **ocultar** desencadenadores de animación.</span><span class="sxs-lookup"><span data-stu-id="1eb63-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="1eb63-293">**Mostrar** y **ocultar** parámetros se definen en el **ColorPickerWheelController** controlador de animación.</span><span class="sxs-lookup"><span data-stu-id="1eb63-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controlador de animación de Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="1eb63-295">**Instrucciones**</span><span class="sxs-lookup"><span data-stu-id="1eb63-295">**Instructions**</span></span>
* <span data-ttu-id="1eb63-296">En el **jerarquía** panel, seleccione **ColorPickerWheel** prefabricado</span><span class="sxs-lookup"><span data-stu-id="1eb63-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="1eb63-297">En el **Inspector** del panel, haga doble clic en **ColorPickerWheel** secuencia de comandos para ver el código de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1eb63-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="1eb63-298">**Secuencia de comandos ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="1eb63-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="1eb63-299">**ColorPickerWheel** se suscribe a Unity **InteractionSourceUpdated** eventos para escuchar eventos de teclado táctil.</span><span class="sxs-lookup"><span data-stu-id="1eb63-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="1eb63-300">En **InteractionSourceUpdated()**, la secuencia de comandos comprueba primero para asegurarse de que:</span><span class="sxs-lookup"><span data-stu-id="1eb63-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="1eb63-301">es realmente un evento de teclado táctil (obj.state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="1eb63-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="1eb63-302">se origina desde el controlador izquierdo (obj.state.source. **diestro o zurdo**)</span><span class="sxs-lookup"><span data-stu-id="1eb63-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="1eb63-303">Si se cumplen, coloque el panel táctil (obj.state. **touchpadPosition**) se asigna a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="1eb63-304">En **Update()**, en función de **visible** propiedad, desencadena mostrar y ocultar los desencadenadores de animación en el componente de Animador del selector de colores</span><span class="sxs-lookup"><span data-stu-id="1eb63-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="1eb63-305">En **Update()**, **selectorPosition** se utiliza para convertir un rayo en colisionador de malla de la rueda de colores, que devuelve la posición de UV.</span><span class="sxs-lookup"><span data-stu-id="1eb63-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="1eb63-306">Esta posición, a continuación, puede usarse para buscar las coordenadas de píxel y el valor de textura de la rueda de colores de color.</span><span class="sxs-lookup"><span data-stu-id="1eb63-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="1eb63-307">Este valor es accesible para otros scripts a través de la **SelectedColor** propiedad.</span><span class="sxs-lookup"><span data-stu-id="1eb63-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Detalles de rueda del selector de color](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="1eb63-309">Capítulo 4: reemplazar el modelo de controlador</span><span class="sxs-lookup"><span data-stu-id="1eb63-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="1eb63-310">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-310">Objectives</span></span>

* <span data-ttu-id="1eb63-311">Obtenga información sobre cómo invalidar el modelo de controlador con un modelo 3D personalizado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="1eb63-313">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-313">Instructions</span></span>

* <span data-ttu-id="1eb63-314">Haga clic en **MotionControllers** en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-315">Haga clic en el círculo en el lado derecho de la **alternativo controlador derecho** campo.</span><span class="sxs-lookup"><span data-stu-id="1eb63-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="1eb63-316">Escriba en **' BrushController**' y seleccione el prefabricado verá en el resultado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="1eb63-317">Puede encontrarlo en activos/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="1eb63-318">Comprobar **Use siempre el modelo adecuado alternativo**</span><span class="sxs-lookup"><span data-stu-id="1eb63-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="1eb63-320">El **BrushController** prefabricado no tiene que incluirse en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="1eb63-321">Sin embargo, para desproteger sus componentes secundarios:</span><span class="sxs-lookup"><span data-stu-id="1eb63-321">However, to check out its child components:</span></span>
* <span data-ttu-id="1eb63-322">En el **proyecto** del panel, escriba en **BrushController** y arrastre **BrushController** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="1eb63-324">Encontrará el **sugerencia** componente en **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="1eb63-325">Usaremos su transformación para dibujar líneas de inicio y detención.</span><span class="sxs-lookup"><span data-stu-id="1eb63-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="1eb63-326">Eliminar el **BrushController** desde el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-327">**Guardar** la escena y haga clic en el **reproducir** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="1eb63-328">Podrá ver que el modelo de pincel reemplazado el controlador de movimiento derecho.</span><span class="sxs-lookup"><span data-stu-id="1eb63-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="1eb63-329">Capítulo 5: pintar con seleccione entrada</span><span class="sxs-lookup"><span data-stu-id="1eb63-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="1eb63-330">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-330">Objectives</span></span>

* <span data-ttu-id="1eb63-331">Obtenga información sobre cómo usar el evento de botón de selección para iniciar y detener un dibujo de línea</span><span class="sxs-lookup"><span data-stu-id="1eb63-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-332">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-332">Instructions</span></span>

* <span data-ttu-id="1eb63-333">Búsqueda **BrushController** prefabricado en el **proyecto** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="1eb63-334">En el **Inspector** del panel, haga doble clic en **BrushController** secuencia de comandos para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1eb63-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="1eb63-335">**Secuencia de comandos BrushController**</span><span class="sxs-lookup"><span data-stu-id="1eb63-335">**BrushController script**</span></span>

<span data-ttu-id="1eb63-336">**BrushController** se suscribe a la InteractionManager **InteractionSourcePressed** y **InteractionSourceReleased** eventos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="1eb63-337">Cuando **InteractionSourcePressed** se desencadena el evento, el pincel **dibujar** propiedad está establecida en true; cuando **InteractionSourceReleased** se desencadena el evento, el pincel **Dibujar** propiedad está establecida en false.</span><span class="sxs-lookup"><span data-stu-id="1eb63-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="1eb63-338">Mientras **dibujar** está establecido en true, el pincel que se generan los puntos en un Unity con instancias **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="1eb63-339">Una referencia a este recurso prefabricado se mantiene en el pincel **trazo prefabricado** campo.</span><span class="sxs-lookup"><span data-stu-id="1eb63-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="1eb63-340">Para usar el color seleccionado actualmente de la rueda de selector de colores de la interfaz de usuario, **BrushController** debe tener una referencia a la **ColorPickerWheel** objeto.</span><span class="sxs-lookup"><span data-stu-id="1eb63-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="1eb63-341">Dado que el **BrushController** prefabricado se crea una instancia en tiempo de ejecución como un controlador de reemplazo, tendrán todas las referencias a objetos de la escena debe establecerse en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1eb63-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="1eb63-342">En este caso usamos **GameObject.FindObjectOfType** para localizar el **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="1eb63-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="1eb63-343">**Guardar** la escena y haga clic en el **reproducir** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="1eb63-344">Podrá volver a dibujar las líneas y pintar con el botón de selección en el controlador derecho.</span><span class="sxs-lookup"><span data-stu-id="1eb63-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="1eb63-345">Capítulo 6: al generar el objeto con selección de entrada</span><span class="sxs-lookup"><span data-stu-id="1eb63-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="1eb63-346">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1eb63-346">Objectives</span></span>

* <span data-ttu-id="1eb63-347">Obtenga información sobre cómo usar Select y entender los eventos de entrada de botón</span><span class="sxs-lookup"><span data-stu-id="1eb63-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="1eb63-348">Obtenga información sobre cómo crear instancias de objetos</span><span class="sxs-lookup"><span data-stu-id="1eb63-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-349">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-349">Instructions</span></span>

* <span data-ttu-id="1eb63-350">En el **proyecto** del panel, escriba **ObjectSpawner** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="1eb63-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="1eb63-351">También puede encontrarlo en activos/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="1eb63-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="1eb63-352">Arrastre el **ObjectSpawner** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-353">Haga clic en **ObjectSpawner** en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-354">**ObjectSpawner** tiene un campo denominado **Color origen**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="1eb63-355">Desde el **jerarquía** del panel, arrastre el **ColorPickerWheel** referencia en este campo.</span><span class="sxs-lookup"><span data-stu-id="1eb63-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Objeto Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="1eb63-357">Haga clic en el **ObjectSpawner** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-358">En el **Inspector** del panel, haga doble clic en **ObjectSpawner** secuencia de comandos para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="1eb63-359">**Secuencia de comandos ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="1eb63-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="1eb63-360">El **ObjectSpawner** crea una instancia de copias de una malla primitiva (cubo, esfera, cilindro) en el espacio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="1eb63-361">Cuando un **InteractionSourcePressed** se detecta comprueba la situación y, si es un **InteractionSourcePressType.Grasp** o **InteractionSourcePressType.Select** evento.</span><span class="sxs-lookup"><span data-stu-id="1eb63-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="1eb63-362">Para un **sujete** eventos, incrementa el índice del tipo actual de malla (esfera, cubo, cilindro)</span><span class="sxs-lookup"><span data-stu-id="1eb63-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="1eb63-363">Para un **seleccione** eventos, en **SpawnObject()**, un nuevo objeto se ha creado una instancia, sin principal y se lanzan en el mundo.</span><span class="sxs-lookup"><span data-stu-id="1eb63-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="1eb63-364">El **ObjectSpawner** usa el **ColorPickerWheel** para establecer el color del material del objeto de visualización.</span><span class="sxs-lookup"><span data-stu-id="1eb63-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="1eb63-365">Objetos generados se dada una instancia de este material, por lo que conservarán su color.</span><span class="sxs-lookup"><span data-stu-id="1eb63-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="1eb63-366">**Guardar** la escena y haga clic en el **reproducir** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="1eb63-367">Podrá cambiar los objetos con el botón de comprensión y generar objetos con el botón de selección.</span><span class="sxs-lookup"><span data-stu-id="1eb63-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="1eb63-368">Compilar e implementar la aplicación portal de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1eb63-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="1eb63-369">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="1eb63-370">Haga clic en **agregar escenas abierto** para agregar la escena actual para el **escenas en compilación**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="1eb63-371">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-371">Click **Build**.</span></span>
* <span data-ttu-id="1eb63-372">Crear un **nueva carpeta** denominada "Aplicación".</span><span class="sxs-lookup"><span data-stu-id="1eb63-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="1eb63-373">Solo haga clic en el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="1eb63-374">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="1eb63-375">Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="1eb63-376">Abra el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-376">Open the **App** folder.</span></span>
* <span data-ttu-id="1eb63-377">Haga doble clic en **YourSceneName.sln** el archivo de solución de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1eb63-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="1eb63-378">Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X64**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="1eb63-379">Haga clic en la flecha desplegable situada junto al botón del dispositivo y seleccione **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="1eb63-380">Haga clic en **Depurar -> Iniciar sin depurar** en el menú o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="1eb63-381">Ahora la aplicación se compila e instalada en el Portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="1eb63-382">Puede iniciar otra vez a través del menú Inicio en el Portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="1eb63-383">Diseño avanzado - herramientas de pincel con diseño radial</span><span class="sxs-lookup"><span data-stu-id="1eb63-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 principal](images/mr213-main-600px.jpg)

<span data-ttu-id="1eb63-385">En este capítulo, obtendrá información sobre cómo reemplazar el modelo de controlador de movimiento predeterminado con una colección de la herramienta pincel personalizado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="1eb63-386">Como referencia, puede encontrar la escena completa **MixedReality213Advanced** en **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-387">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-387">Instructions</span></span>

* <span data-ttu-id="1eb63-388">En el **proyecto** del panel, escriba **BrushSelector** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="1eb63-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="1eb63-389">También puede encontrarlo en activos/AppPrefabs /</span><span class="sxs-lookup"><span data-stu-id="1eb63-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="1eb63-390">Arrastre el **BrushSelector** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-391">Para la organización, cree un GameObject vacío denominado **pinceles**</span><span class="sxs-lookup"><span data-stu-id="1eb63-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="1eb63-392">Arrastre las siguientes prefabricados desde el **proyecto** en el panel **pinceles**</span><span class="sxs-lookup"><span data-stu-id="1eb63-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="1eb63-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="1eb63-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="1eb63-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="1eb63-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="1eb63-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="1eb63-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="1eb63-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="1eb63-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="1eb63-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="1eb63-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="1eb63-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="1eb63-398">Assets/AppPrefabs/**Pencil**</span></span>

![Pinceles](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="1eb63-400">Haga clic en **MotionControllers** prefabricado en el **jerarquía** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="1eb63-401">En el **Inspector** del panel, desactive la opción **siempre uso alternativo derecha modelo** en el **visualizador del controlador de movimiento**</span><span class="sxs-lookup"><span data-stu-id="1eb63-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="1eb63-402">En el **jerarquía** del panel, haga clic en **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="1eb63-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="1eb63-403">**BrushSelector** tiene un campo denominado **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="1eb63-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="1eb63-404">Desde el **jerarquía** del panel, arrastre el **ColorPickerWheel** en **ColorPicker** campo el **Inspector** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Asignar ColorPickerWheel al Selector de pincel](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="1eb63-406">En el **jerarquía** panel **BrushSelector** prefabricado, seleccione el **menú** objeto.</span><span class="sxs-lookup"><span data-stu-id="1eb63-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="1eb63-407">En el **Inspector** panel, en el **LineObjectCollection** componente, abra el **objetos** lista desplegable de la matriz.</span><span class="sxs-lookup"><span data-stu-id="1eb63-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="1eb63-408">Verá 6 ranuras vacías.</span><span class="sxs-lookup"><span data-stu-id="1eb63-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="1eb63-409">Desde el **jerarquía** del panel, arrastre cada uno de los prefabricados su elemento primarios en el **pinceles** GameObject en estas ranuras en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="1eb63-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="1eb63-410">(Asegúrese de que está arrastrando el prefabricados desde la escena, no el prefabricados en la carpeta del proyecto).</span><span class="sxs-lookup"><span data-stu-id="1eb63-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Selector de pincel](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="1eb63-412">**BrushSelector prefabricado**</span><span class="sxs-lookup"><span data-stu-id="1eb63-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="1eb63-413">Puesto que la **BrushSelector** hereda **AttachToController**, muestra **diestro o zurdo** y **elemento** opciones en el  **Inspector de** panel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="1eb63-414">Hemos seleccionado **derecha** y **señalando suponer** para adjuntar las herramientas de pincel para el controlador derecho hacia delante.</span><span class="sxs-lookup"><span data-stu-id="1eb63-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="1eb63-415">El **BrushSelector** hace uso de dos utilidades:</span><span class="sxs-lookup"><span data-stu-id="1eb63-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="1eb63-416">**Elipse**: usado para generar puntos en el espacio a lo largo de una forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="1eb63-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="1eb63-417">**LineObjectCollection**: distribuye objetos utilizando los puntos de generados por cualquier clase de línea (por ejemplo, la elipse).</span><span class="sxs-lookup"><span data-stu-id="1eb63-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="1eb63-418">Esto es lo que vamos a usar para colocar nuestros pinceles a lo largo de la forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="1eb63-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="1eb63-419">Cuando se combinan, estas utilidades se pueden usar para crear un menú radial.</span><span class="sxs-lookup"><span data-stu-id="1eb63-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="1eb63-420">**Secuencia de comandos LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="1eb63-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="1eb63-421">**LineObjectCollection** tiene controles para el tamaño, posición y giro de objetos distribuidos a lo largo de su línea.</span><span class="sxs-lookup"><span data-stu-id="1eb63-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="1eb63-422">Esto es útil para crear menús radiales, como el selector de pincel.</span><span class="sxs-lookup"><span data-stu-id="1eb63-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="1eb63-423">Para crear la apariencia de los pinceles esa escala nada, como se aproximen a la posición central seleccionado, el **ObjectScale** curva picos en el centro y cirios en los bordes.</span><span class="sxs-lookup"><span data-stu-id="1eb63-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="1eb63-424">**Secuencia de comandos BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="1eb63-424">**BrushSelector script**</span></span>

<span data-ttu-id="1eb63-425">En el caso de los **BrushSelector**, hemos elegido usar animación procedimientos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="1eb63-426">En primer lugar, los modelos de pincel se distribuyen en una elipse por la **LineObjectCollection** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="1eb63-427">A continuación, cada pincel es responsable de mantener su posición en la mano del usuario según sus **DisplayMode** valor, que cambia en función de la selección.</span><span class="sxs-lookup"><span data-stu-id="1eb63-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="1eb63-428">Nos decidimos por un enfoque de procedimiento porque la probabilidad alta de las transiciones de posición del pincel que se interrumpa, ya que el usuario selecciona pinceles.</span><span class="sxs-lookup"><span data-stu-id="1eb63-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="1eb63-429">Mecanim animaciones pueden controlar las interrupciones de forma correcta, pero suele ser más complicado que una simple operación Lerp.</span><span class="sxs-lookup"><span data-stu-id="1eb63-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="1eb63-430">**BrushSelector** usa una combinación de ambos.</span><span class="sxs-lookup"><span data-stu-id="1eb63-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="1eb63-431">Cuando se detecte una entrada de teclado táctil, opciones de pincel se hacen visibles y escalar verticalmente a lo largo del menú radial.</span><span class="sxs-lookup"><span data-stu-id="1eb63-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="1eb63-432">Tras un período de tiempo de espera (que indica que el usuario ha realizado una selección) el pincel las opciones de escala hacia abajo de nuevo, dejando sólo el pincel seleccionado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="1eb63-433">**Visualización de entrada de teclado táctil**</span><span class="sxs-lookup"><span data-stu-id="1eb63-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="1eb63-434">Incluso en casos donde el modelo de controlador se ha reemplazado por completo, puede ser útil mostrar la entrada en las entradas del modelo original.</span><span class="sxs-lookup"><span data-stu-id="1eb63-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="1eb63-435">Esto ayuda a hacer que las acciones del usuario en realidad.</span><span class="sxs-lookup"><span data-stu-id="1eb63-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="1eb63-436">Para el **BrushSelector** hemos decidido que el panel táctil brevemente visible cuando se recibe la entrada.</span><span class="sxs-lookup"><span data-stu-id="1eb63-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="1eb63-437">Para hacerlo, recuperando el elemento de panel táctil desde el controlador, reemplazando su material con un material personalizado, a continuación, aplicar un degradado de color de ese material según el último panel táctil de tiempo se ha recibido la entrada.</span><span class="sxs-lookup"><span data-stu-id="1eb63-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="1eb63-438">**Selección de herramientas de pincel con la entrada del teclado táctil**</span><span class="sxs-lookup"><span data-stu-id="1eb63-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="1eb63-439">Cuando el selector de pincel detecta una entrada presionado del teclado táctil, comprueba la posición de la entrada para determinar si fue a la izquierda o derecha.</span><span class="sxs-lookup"><span data-stu-id="1eb63-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="1eb63-440">**Grosor del trazo con selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="1eb63-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="1eb63-441">En lugar de la **InteractionSourcePressType.Select** eventos en el **InteractionSourcePressed()**, puede obtener el valor de la cantidad presionado a través de analógico **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="1eb63-442">Este valor se puede recuperar en **InteractionSourceUpdated()**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="1eb63-443">**Script de borrador**</span><span class="sxs-lookup"><span data-stu-id="1eb63-443">**Eraser script**</span></span>

<span data-ttu-id="1eb63-444">**Borrador** es un tipo especial de pincel que invalida la base de **pincel**del **DrawOverTime()** función.</span><span class="sxs-lookup"><span data-stu-id="1eb63-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="1eb63-445">Aunque Draw es true, el borrador comprueba si su sugerencia tiene una intersección con los trazos existentes.</span><span class="sxs-lookup"><span data-stu-id="1eb63-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="1eb63-446">Si es así, se agregan a una cola se puede reducir hacia abajo y eliminar.</span><span class="sxs-lookup"><span data-stu-id="1eb63-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="1eb63-447">Diseño avanzado - Teleportation y desplazamiento</span><span class="sxs-lookup"><span data-stu-id="1eb63-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="1eb63-448">Si desea permitir al usuario moverse por la escena con teleportation mediante la tecla de navegación, utilice **MixedRealityCameraParent** en lugar de **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="1eb63-449">También deberá agregar **InputManager** y **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="1eb63-450">Puesto que **MixedRealityCameraParent** ya incluye **MotionControllers** y **límite** como componentes secundarios, debe quitar las existentes  **MotionControllers** y **entorno** prefabricado.</span><span class="sxs-lookup"><span data-stu-id="1eb63-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="1eb63-451">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1eb63-451">Instructions</span></span>

* <span data-ttu-id="1eb63-452">En el **jerarquía** del panel, eliminar **MixedRealityCamera**, **entorno** y **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="1eb63-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="1eb63-453">Desde el **panel proyecto**, busque y arrastre el prefabricados siguientes en el **jerarquía** panel:</span><span class="sxs-lookup"><span data-stu-id="1eb63-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="1eb63-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="1eb63-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="1eb63-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="1eb63-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="1eb63-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="1eb63-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Realidad mixta cámara primaria](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="1eb63-458">En el **jerarquía** del panel, haga clic en **Administrador de entrada**</span><span class="sxs-lookup"><span data-stu-id="1eb63-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="1eb63-459">En el **Inspector** del panel, desplácese hacia abajo hasta la **Selector Simple de puntero único** sección</span><span class="sxs-lookup"><span data-stu-id="1eb63-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="1eb63-460">Desde el **jerarquía** del panel, arrastre **DefaultCursor** en **Cursor** campo</span><span class="sxs-lookup"><span data-stu-id="1eb63-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Asignación de DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="1eb63-462">**Guardar** la escena y haga clic en el **reproducir** botón.</span><span class="sxs-lookup"><span data-stu-id="1eb63-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="1eb63-463">Podrá usar la tecla de navegación para girar izquierda/derecha o teleport.</span><span class="sxs-lookup"><span data-stu-id="1eb63-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="1eb63-464">Fin</span><span class="sxs-lookup"><span data-stu-id="1eb63-464">The end</span></span>

<span data-ttu-id="1eb63-465">Y es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="1eb63-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="1eb63-466">Ha aprendido conceptos:</span><span class="sxs-lookup"><span data-stu-id="1eb63-466">You learned:</span></span>
* <span data-ttu-id="1eb63-467">Cómo trabajar con modelos de controlador de movimiento en el modo de juego Unity y en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1eb63-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="1eb63-468">Cómo usar diferentes tipos de eventos de botón y sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1eb63-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="1eb63-469">Cómo los elementos de interfaz de usuario en la parte superior del controlador de superposición o personalizarlo completamente.</span><span class="sxs-lookup"><span data-stu-id="1eb63-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="1eb63-470">Ahora está listo para comenzar a crear su propia experiencia envolvente con controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="1eb63-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="1eb63-471">Segundo plano completada</span><span class="sxs-lookup"><span data-stu-id="1eb63-471">Completed scenes</span></span>

* <span data-ttu-id="1eb63-472">En Unity **proyecto** panel, haga clic en el **escenas** carpeta.</span><span class="sxs-lookup"><span data-stu-id="1eb63-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="1eb63-473">Encontrará dos sceens Unity **MixedReality213** y **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="1eb63-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="1eb63-474">**MixedReality213**: Escena completado con el único pincel</span><span class="sxs-lookup"><span data-stu-id="1eb63-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="1eb63-475">**MixedReality213Advanced**: Escena completada con varios pincel con el ejemplo de cantidad presione del botón de selección</span><span class="sxs-lookup"><span data-stu-id="1eb63-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="1eb63-476">Vea también</span><span class="sxs-lookup"><span data-stu-id="1eb63-476">See also</span></span>

* [<span data-ttu-id="1eb63-477">Archivos de proyecto MR 213 de entrada</span><span class="sxs-lookup"><span data-stu-id="1eb63-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="1eb63-478">Kit de herramientas de realidad mixta - escena de la prueba del controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="1eb63-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="1eb63-479">Kit de herramientas de realidad mixta - mecánica de arrastre</span><span class="sxs-lookup"><span data-stu-id="1eb63-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="1eb63-480">Instrucciones de desarrollo del controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="1eb63-480">Motion controller development guidelines</span></span>](motion-controllers.md)
