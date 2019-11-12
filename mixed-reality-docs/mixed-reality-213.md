---
title: Entrada MR 213
description: Siga este tutorial de codificación con Unity, Visual Studio y auriculares envolventes para aprender los detalles de los controladores de movimiento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, inmersivo, controlador de movimiento, Academia, tutorial
ms.openlocfilehash: 273d1bf384d588ab24bfe29e30f299b7a41fe541
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926817"
---
>[!NOTE]
><span data-ttu-id="b8b79-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b8b79-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b8b79-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b8b79-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b8b79-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b8b79-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="b8b79-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b8b79-108">Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b8b79-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="b8b79-109">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="b8b79-109">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="b8b79-110">Los controladores de movimiento del mundo de la realidad mixta agregan otro nivel de interactividad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-110">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="b8b79-111">Con [los controladores de movimiento](motion-controllers.md), podemos interactuar directamente con los objetos de una manera más natural, de forma similar a las interacciones físicas en la vida real, lo que aumenta la inmersión y la alegría en la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b8b79-111">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="b8b79-112">En la entrada MR 213, exploraremos los eventos de entrada del controlador de movimiento mediante la creación de una sencilla experiencia de dibujo espacial.</span><span class="sxs-lookup"><span data-stu-id="b8b79-112">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="b8b79-113">Con esta aplicación, los usuarios pueden pintar en un espacio tridimensional con varios tipos de pinceles y colores.</span><span class="sxs-lookup"><span data-stu-id="b8b79-113">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="b8b79-114">Temas tratados en este tutorial</span><span class="sxs-lookup"><span data-stu-id="b8b79-114">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="b8b79-118">**Visualización del controlador**</span><span class="sxs-lookup"><span data-stu-id="b8b79-118">**Controller visualization**</span></span>|<span data-ttu-id="b8b79-119">**Eventos de entrada del controlador**</span><span class="sxs-lookup"><span data-stu-id="b8b79-119">**Controller input events**</span></span>|<span data-ttu-id="b8b79-120">**Controlador y interfaz de usuario personalizados**</span><span class="sxs-lookup"><span data-stu-id="b8b79-120">**Custom controller and UI**</span></span>|
|<span data-ttu-id="b8b79-121">Aprenda a representar los modelos de control de movimiento en el modo de juego y el tiempo de ejecución de Unity.</span><span class="sxs-lookup"><span data-stu-id="b8b79-121">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="b8b79-122">Comprenda los distintos tipos de eventos de botón y sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b8b79-122">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="b8b79-123">Obtenga información sobre cómo superponer los elementos de la interfaz de usuario sobre el controlador o personalizarlos totalmente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-123">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="b8b79-124">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b8b79-125">Recurso</span><span class="sxs-lookup"><span data-stu-id="b8b79-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b8b79-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b8b79-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b8b79-127"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="b8b79-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b8b79-128">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="b8b79-128">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="b8b79-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b8b79-129">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="b8b79-130">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="b8b79-130">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="b8b79-131">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b8b79-131">Prerequisites</span></span>

<span data-ttu-id="b8b79-132">Consulte la lista de comprobación de instalación para los auriculares que se envolverán en [esta página](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b8b79-132">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="b8b79-133">En este tutorial se requiere [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="b8b79-133">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="b8b79-134">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="b8b79-134">Project files</span></span>

* <span data-ttu-id="b8b79-135">[Descargue los archivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) requeridos por el proyecto y extraiga los archivos en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="b8b79-135">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="b8b79-136">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="b8b79-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="b8b79-137">Configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="b8b79-137">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="b8b79-138">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-138">Objectives</span></span>

* <span data-ttu-id="b8b79-139">Optimizar el desarrollo de Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b8b79-139">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="b8b79-140">Configuración de una cámara de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b8b79-140">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="b8b79-141">Entorno de instalación</span><span class="sxs-lookup"><span data-stu-id="b8b79-141">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-142">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-142">Instructions</span></span>

* <span data-ttu-id="b8b79-143">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="b8b79-143">Start Unity.</span></span>
* <span data-ttu-id="b8b79-144">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-144">Select **Open**.</span></span>
* <span data-ttu-id="b8b79-145">Navegue hasta el escritorio y busque la carpeta **MixedReality213-Master** que ha desarchivado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-145">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="b8b79-146">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-146">Click **Select Folder**.</span></span>
* <span data-ttu-id="b8b79-147">Una vez que Unity termine de cargar los archivos de proyecto, podrá ver el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="b8b79-147">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="b8b79-148">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-148">In Unity, select **File > Build Settings**.</span></span>

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* <span data-ttu-id="b8b79-150">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-150">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="b8b79-151">Establecimiento del dispositivo de destino en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="b8b79-151">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="b8b79-152">Establecer el tipo de compilación en **D3D**</span><span class="sxs-lookup"><span data-stu-id="b8b79-152">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="b8b79-153">Establecer SDK en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="b8b79-153">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="b8b79-154">Comprobación **de C# proyectos de Unity**</span><span class="sxs-lookup"><span data-stu-id="b8b79-154">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="b8b79-155">Esto permite modificar archivos de script en el proyecto de Visual Studio sin volver a generar el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="b8b79-155">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="b8b79-156">Haga clic en **configuración del reproductor**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-156">Click **Player Settings**.</span></span>
* <span data-ttu-id="b8b79-157">En el panel **Inspector** , desplácese hacia abajo hasta la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="b8b79-157">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="b8b79-158">En configuración de XR, Active **realidad compatible**</span><span class="sxs-lookup"><span data-stu-id="b8b79-158">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="b8b79-159">En SDK de realidad virtual, seleccione **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-159">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* <span data-ttu-id="b8b79-161">Cierre la ventana de **configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-161">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="b8b79-162">Estructura del proyecto</span><span class="sxs-lookup"><span data-stu-id="b8b79-162">Project structure</span></span>

<span data-ttu-id="b8b79-163">En este tutorial se usa **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-163">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="b8b79-164">Puede encontrar las versiones en [esta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="b8b79-164">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="b8b79-166">**Escenas completadas para su referencia**</span><span class="sxs-lookup"><span data-stu-id="b8b79-166">**Completed scenes for your reference**</span></span>

* <span data-ttu-id="b8b79-167">Encontrará dos escenas de Unity completadas en la carpeta **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-167">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="b8b79-168">**MixedReality213**: escena completada con un solo pincel</span><span class="sxs-lookup"><span data-stu-id="b8b79-168">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="b8b79-169">**MixedReality213Advanced**: escena completada para diseño avanzado con varios pinceles</span><span class="sxs-lookup"><span data-stu-id="b8b79-169">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="b8b79-170">**Nueva configuración de escenas para el tutorial**</span><span class="sxs-lookup"><span data-stu-id="b8b79-170">**New Scene setup for the tutorial**</span></span>

* <span data-ttu-id="b8b79-171">En Unity, haga clic en **archivo > nueva escena** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-171">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="b8b79-172">Eliminar la **cámara principal** y la **luz direccional**</span><span class="sxs-lookup"><span data-stu-id="b8b79-172">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="b8b79-173">En el **panel Proyecto**, busque y arrastre el siguiente Prefabs al panel **jerarquía** :</span><span class="sxs-lookup"><span data-stu-id="b8b79-173">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="b8b79-174">Assets/HoloToolkit/INPUT/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="b8b79-174">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="b8b79-175">Activos/AppPrefabs/**entorno**</span><span class="sxs-lookup"><span data-stu-id="b8b79-175">Assets/AppPrefabs/**Environment**</span></span>

    ![Cámara y entorno](images/mr213-cameraenvironment-300px.jpg)

* <span data-ttu-id="b8b79-177">Hay dos Prefabs de cámara en el kit de herramientas de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="b8b79-177">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="b8b79-178">**MixedRealityCamera. recurso prefabricado**: solo cámara</span><span class="sxs-lookup"><span data-stu-id="b8b79-178">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="b8b79-179">**MixedRealityCameraParent. recurso prefabricado**: cámara + teleportabilidad + límite</span><span class="sxs-lookup"><span data-stu-id="b8b79-179">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="b8b79-180">En este tutorial, usaremos **MixedRealityCamera** sin la característica de teleportabilidad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-180">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="b8b79-181">Por este motivo, hemos agregado recurso prefabricado de **entorno** sencillo, que contiene una planta básica para que el usuario sienta.</span><span class="sxs-lookup"><span data-stu-id="b8b79-181">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="b8b79-182">Para obtener más información acerca de la teleportabilidad con **MixedRealityCameraParent**, consulte el artículo sobre el [diseño avanzado: teleportabilidad y Locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="b8b79-182">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="b8b79-183">**Configuración de SKYBOX**</span><span class="sxs-lookup"><span data-stu-id="b8b79-183">**Skybox setup**</span></span>

* <span data-ttu-id="b8b79-184">Haga clic en **ventana > iluminación > configuración**</span><span class="sxs-lookup"><span data-stu-id="b8b79-184">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="b8b79-185">Haga clic en el círculo en el lado derecho del **campo material de SKYBOX**</span><span class="sxs-lookup"><span data-stu-id="b8b79-185">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="b8b79-186">Escriba "Gray" y seleccione **SkyboxGray** (assets/AppPrefabs/support/Materials/SkyboxGray. MAT)</span><span class="sxs-lookup"><span data-stu-id="b8b79-186">Type in ‘gray’ and select **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

    ![Establecer SKYBOX](images/mr123-skyboxsetting-400px.jpg)

* <span data-ttu-id="b8b79-188">Active la opción **SKYBOX** para poder ver el degradado gris asignado SKYBOX</span><span class="sxs-lookup"><span data-stu-id="b8b79-188">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

    ![Alternar opción SKYBOX](images/mr213-skyboxcheck-400px.jpg)

* <span data-ttu-id="b8b79-190">La escena con MixedRealityCamera, entorno y gris SKYBOX tendrá el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="b8b79-190">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

    ![Entorno de MixedReality213](images/mr213-environment-600px.jpg)

* <span data-ttu-id="b8b79-192">Haga clic en **archivo > guardar escena como**</span><span class="sxs-lookup"><span data-stu-id="b8b79-192">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="b8b79-193">**Guardar** la escena en la carpeta Scenes con cualquier nombre</span><span class="sxs-lookup"><span data-stu-id="b8b79-193">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="b8b79-194">Capítulo 1: visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="b8b79-194">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="b8b79-195">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-195">Objectives</span></span>

* <span data-ttu-id="b8b79-196">Aprenda a representar modelos de controlador de movimiento en el modo de juego de Unity y en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b8b79-196">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="b8b79-197">Windows Mixed Reality proporciona un modelo de controlador animado para la visualización del controlador.</span><span class="sxs-lookup"><span data-stu-id="b8b79-197">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="b8b79-198">Hay varios enfoques que puede realizar para la visualización del controlador en la aplicación:</span><span class="sxs-lookup"><span data-stu-id="b8b79-198">There are several approaches you can take for controller visualization in your app:</span></span>

* <span data-ttu-id="b8b79-199">Predeterminado: uso del controlador predeterminado sin modificación</span><span class="sxs-lookup"><span data-stu-id="b8b79-199">Default - Using default controller without modification</span></span>
* <span data-ttu-id="b8b79-200">Híbrido: uso del controlador predeterminado, pero personalización de algunos de sus elementos o de la superposición de componentes de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="b8b79-200">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="b8b79-201">Reemplazo: usar su propio modelo 3D personalizado para el controlador</span><span class="sxs-lookup"><span data-stu-id="b8b79-201">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="b8b79-202">En este capítulo, veremos los ejemplos de estas personalizaciones del controlador.</span><span class="sxs-lookup"><span data-stu-id="b8b79-202">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-203">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-203">Instructions</span></span>

* <span data-ttu-id="b8b79-204">En el panel **proyecto** , escriba **MotionControllers** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="b8b79-204">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="b8b79-205">También puede encontrarlo en assets/HoloToolkit/INPUT/Prefabs/.</span><span class="sxs-lookup"><span data-stu-id="b8b79-205">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="b8b79-206">Arrastre **MotionControllers** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-206">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-207">Haga clic en **MotionControllers** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-207">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="b8b79-208">**MotionControllers recurso prefabricado**</span><span class="sxs-lookup"><span data-stu-id="b8b79-208">**MotionControllers prefab**</span></span>

<span data-ttu-id="b8b79-209">**MotionControllers** recurso prefabricado tiene un script **MotionControllerVisualizer** que proporciona las ranuras para los modelos de controladores alternativos.</span><span class="sxs-lookup"><span data-stu-id="b8b79-209">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="b8b79-210">Si asigna sus propios modelos 3D personalizados, como una mano o un valor de espada, y activa la casilla "usar siempre el modelo alternativo de la izquierda o la derecha", se verán en lugar del modelo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="b8b79-210">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="b8b79-211">Usaremos esta ranura en el capítulo 4 para reemplazar el modelo de controlador por un pincel.</span><span class="sxs-lookup"><span data-stu-id="b8b79-211">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="b8b79-213">**Las**</span><span class="sxs-lookup"><span data-stu-id="b8b79-213">**Instructions**</span></span>

* <span data-ttu-id="b8b79-214">En el panel **Inspector** , haga doble clic en **MotionControllerVisualizer** script para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8b79-214">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="b8b79-215">**Script MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="b8b79-215">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="b8b79-216">Las clases **MotionControllerVisualizer** y **MotionControllerInfo** proporcionan los medios para tener acceso a & modificar los modelos de controlador predeterminados.</span><span class="sxs-lookup"><span data-stu-id="b8b79-216">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="b8b79-217">**MotionControllerVisualizer** se suscribe al evento **InteractionSourceDetected** de Unity y crea automáticamente instancias de los modelos de controlador cuando se encuentran.</span><span class="sxs-lookup"><span data-stu-id="b8b79-217">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="b8b79-218">Los modelos de controlador se entregan según [la especificación glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="b8b79-218">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="b8b79-219">Este formato se ha creado para proporcionar un formato común, a la vez que mejora el proceso que subyace a la transmisión y desempaquetado de recursos 3D.</span><span class="sxs-lookup"><span data-stu-id="b8b79-219">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="b8b79-220">En este caso, es necesario recuperar y cargar los modelos de controlador en tiempo de ejecución, ya que queremos que la experiencia del usuario sea lo más fluida posible y no se garantice qué versión de los controladores de movimiento puede estar usando el usuario.</span><span class="sxs-lookup"><span data-stu-id="b8b79-220">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="b8b79-221">Este curso, a través del kit de herramientas de la realidad mixta, usa una versión del [proyecto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)del Grupo Khronos.</span><span class="sxs-lookup"><span data-stu-id="b8b79-221">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="b8b79-222">Una vez que se ha entregado el controlador, los scripts pueden usar **MotionControllerInfo** para buscar las transformaciones de elementos de controlador específicos para que puedan colocarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-222">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="b8b79-223">En un capítulo posterior, se aprenderá a usar estos scripts para adjuntar elementos de interfaz de usuario a los controladores.</span><span class="sxs-lookup"><span data-stu-id="b8b79-223">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="b8b79-224">*En algunos scripts, encontrará bloques de código con **#if. UNITY_EDITOR** o **UNITY_WSA**. Estos bloques de código solo se ejecutan en el tiempo de ejecución de UWP al implementar en Windows. Esto se debe a que el conjunto de API que usa el editor de Unity y el tiempo de ejecución de la aplicación para UWP son diferentes.*</span><span class="sxs-lookup"><span data-stu-id="b8b79-224">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>

* <span data-ttu-id="b8b79-225">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-225">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="b8b79-226">Podrá ver la escena con controladores de movimiento en el casco.</span><span class="sxs-lookup"><span data-stu-id="b8b79-226">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="b8b79-227">Puede ver animaciones detalladas para los clics de botón, el movimiento del stick analógico y el resaltado táctil de Touchpad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-227">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller valor predeterminado de visualización](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="b8b79-229">Capítulo 2: adjuntar elementos de la interfaz de usuario al controlador</span><span class="sxs-lookup"><span data-stu-id="b8b79-229">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="b8b79-230">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-230">Objectives</span></span>

* <span data-ttu-id="b8b79-231">Más información sobre los elementos de los controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="b8b79-231">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="b8b79-232">Obtenga información acerca de cómo adjuntar objetos a partes específicas de los controladores</span><span class="sxs-lookup"><span data-stu-id="b8b79-232">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="b8b79-233">En este capítulo, aprenderá a agregar elementos de la interfaz de usuario al controlador, al que el usuario puede acceder y manipular fácilmente en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="b8b79-233">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="b8b79-234">También aprenderá a agregar una interfaz de usuario del selector de colores simple mediante la entrada del panel táctil.</span><span class="sxs-lookup"><span data-stu-id="b8b79-234">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-235">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-235">Instructions</span></span>

* <span data-ttu-id="b8b79-236">En el panel **proyecto** , busque el script **MotionControllerInfo** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-236">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="b8b79-237">En el resultado de la búsqueda, haga doble clic en **MotionControllerInfo** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8b79-237">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="b8b79-238">**Script MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="b8b79-238">**MotionControllerInfo script**</span></span>

<span data-ttu-id="b8b79-239">El primer paso es elegir a qué elemento del controlador desea asociar la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="b8b79-239">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="b8b79-240">Estos elementos se definen en **ControllerElementEnum** en **MotionControllerInfo.CS**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-240">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* <span data-ttu-id="b8b79-242">**Inicio**</span><span class="sxs-lookup"><span data-stu-id="b8b79-242">**Home**</span></span>
* <span data-ttu-id="b8b79-243">**MENU**</span><span class="sxs-lookup"><span data-stu-id="b8b79-243">**Menu**</span></span>
* <span data-ttu-id="b8b79-244">**Visión**</span><span class="sxs-lookup"><span data-stu-id="b8b79-244">**Grasp**</span></span>
* <span data-ttu-id="b8b79-245">**Palanca**</span><span class="sxs-lookup"><span data-stu-id="b8b79-245">**Thumbstick**</span></span>
* <span data-ttu-id="b8b79-246">**No**</span><span class="sxs-lookup"><span data-stu-id="b8b79-246">**Select**</span></span>
* <span data-ttu-id="b8b79-247">**Panel táctil**</span><span class="sxs-lookup"><span data-stu-id="b8b79-247">**Touchpad**</span></span>
* <span data-ttu-id="b8b79-248">**Pose de puntero** : este elemento representa la punta de la dirección de reenvío hacia delante del controlador.</span><span class="sxs-lookup"><span data-stu-id="b8b79-248">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="b8b79-249">**Las**</span><span class="sxs-lookup"><span data-stu-id="b8b79-249">**Instructions**</span></span>

* <span data-ttu-id="b8b79-250">En el panel **proyecto** , busque el script **AttachToController** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-250">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="b8b79-251">En el resultado de la búsqueda, haga doble clic en **AttachToController** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8b79-251">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="b8b79-252">**Script AttachToController**</span><span class="sxs-lookup"><span data-stu-id="b8b79-252">**AttachToController script**</span></span>

<span data-ttu-id="b8b79-253">El script **AttachToController** proporciona una manera sencilla de adjuntar cualquier objeto a un elemento y una manecilla de controlador especificados.</span><span class="sxs-lookup"><span data-stu-id="b8b79-253">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="b8b79-254">En **AttachElementToController ()** ,</span><span class="sxs-lookup"><span data-stu-id="b8b79-254">In **AttachElementToController()**,</span></span>

* <span data-ttu-id="b8b79-255">Comprobar la mano mediante **MotionControllerInfo. Handl**</span><span class="sxs-lookup"><span data-stu-id="b8b79-255">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="b8b79-256">Obtiene un elemento específico del controlador mediante **MotionControllerInfo. TryGetElement ()**</span><span class="sxs-lookup"><span data-stu-id="b8b79-256">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="b8b79-257">Después de recuperar la transformación del elemento del modelo del controlador, el objeto primario que se encuentra en él y establecer la posición local del objeto & la rotación en cero.</span><span class="sxs-lookup"><span data-stu-id="b8b79-257">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="b8b79-258">La manera más sencilla de usar el script **AttachToController** es heredar de él, como hemos hecho en el caso de **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="b8b79-258">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="b8b79-259">Simplemente invalide las funciones **OnAttachToController** y **OnDetachFromController** para realizar la instalación o el desglose cuando el controlador se detecta o se desconecta.</span><span class="sxs-lookup"><span data-stu-id="b8b79-259">Simply override the **OnAttachToController** and **OnDetachFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="b8b79-260">**Las**</span><span class="sxs-lookup"><span data-stu-id="b8b79-260">**Instructions**</span></span>

* <span data-ttu-id="b8b79-261">En el panel **proyecto** , escriba en el cuadro de búsqueda **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-261">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="b8b79-262">También puede encontrarlo en assets/AppPrefabs/.</span><span class="sxs-lookup"><span data-stu-id="b8b79-262">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="b8b79-263">Arrastre **ColorPickerWheel** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-263">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-264">Haga clic en **ColorPickerWheel** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-264">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-265">En el panel **Inspector** , haga doble clic en **ColorPickerWheel** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8b79-265">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel recurso prefabricado](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="b8b79-267">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="b8b79-267">**ColorPickerWheel script**</span></span>

<span data-ttu-id="b8b79-268">Dado que **ColorPickerWheel** hereda **AttachToController**, muestra la **mano** y el **elemento** en el panel del **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-268">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="b8b79-269">Vamos a asociar la interfaz de usuario al elemento Touchpad del controlador izquierdo.</span><span class="sxs-lookup"><span data-stu-id="b8b79-269">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="b8b79-271">**ColorPickerWheel** invalida **OnAttachToController** y **OnDetachFromController** para suscribirse al evento de entrada que se usará en el capítulo siguiente para la selección de color con entrada de Touchpad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-271">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetachFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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

* <span data-ttu-id="b8b79-272">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-272">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="b8b79-273">**Método alternativo para adjuntar objetos a los controladores**</span><span class="sxs-lookup"><span data-stu-id="b8b79-273">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="b8b79-274">Se recomienda que los scripts hereden de **AttachToController** e invalide **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-274">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="b8b79-275">Sin embargo, esto no siempre es posible.</span><span class="sxs-lookup"><span data-stu-id="b8b79-275">However, this may not always be possible.</span></span> <span data-ttu-id="b8b79-276">Una alternativa es usarla como componente independiente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-276">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="b8b79-277">Esto puede ser útil si desea adjuntar un recurso prefabricado existente a un controlador sin refactorizar los scripts.</span><span class="sxs-lookup"><span data-stu-id="b8b79-277">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="b8b79-278">Basta con que la clase espere a que Isattached (se establezca en true antes de realizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="b8b79-278">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="b8b79-279">La manera más sencilla de hacerlo es usar una corutina para ' Start '.</span><span class="sxs-lookup"><span data-stu-id="b8b79-279">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="b8b79-280">Capítulo 3: trabajar con la entrada de Touchpad</span><span class="sxs-lookup"><span data-stu-id="b8b79-280">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="b8b79-281">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-281">Objectives</span></span>

* <span data-ttu-id="b8b79-282">Obtenga información sobre cómo obtener eventos de datos de entrada de Touchpad</span><span class="sxs-lookup"><span data-stu-id="b8b79-282">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="b8b79-283">Aprenda a usar la información de posición del eje Touchpad para la experiencia de la aplicación</span><span class="sxs-lookup"><span data-stu-id="b8b79-283">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-284">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-284">Instructions</span></span>

* <span data-ttu-id="b8b79-285">En el panel **jerarquía** , haga clic en **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="b8b79-285">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="b8b79-286">En el panel **Inspector** , en **animación**, haga doble clic en **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="b8b79-286">In the **Inspector** panel, under **Animator**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="b8b79-287">Podrá ver la pestaña **animador** abierta</span><span class="sxs-lookup"><span data-stu-id="b8b79-287">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="b8b79-288">**Mostrar u ocultar la interfaz de usuario con el controlador de animación de Unity**</span><span class="sxs-lookup"><span data-stu-id="b8b79-288">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="b8b79-289">Para mostrar y ocultar la interfaz de usuario de **ColorPickerWheel** con la animación, usamos el [sistema de animación de Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="b8b79-289">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="b8b79-290">Si se establece la propiedad **visible** de **ColorPickerWheel**en los desencadenadores true o false, se **muestran** y **ocultan** los desencadenadores de animación.</span><span class="sxs-lookup"><span data-stu-id="b8b79-290">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="b8b79-291">Los parámetros de **Mostrar** y **ocultar** se definen en el controlador de animación **ColorPickerWheelController** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-291">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controlador de animación de Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="b8b79-293">**Las**</span><span class="sxs-lookup"><span data-stu-id="b8b79-293">**Instructions**</span></span>

* <span data-ttu-id="b8b79-294">En el panel **jerarquía** , seleccione **ColorPickerWheel** recurso prefabricado</span><span class="sxs-lookup"><span data-stu-id="b8b79-294">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="b8b79-295">En el panel **Inspector** , haga doble clic en **ColorPickerWheel** script para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8b79-295">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="b8b79-296">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="b8b79-296">**ColorPickerWheel script**</span></span>

<span data-ttu-id="b8b79-297">**ColorPickerWheel** se suscribe al evento **InteractionSourceUpdated** de Unity para escuchar eventos Touchpad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-297">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="b8b79-298">En **InteractionSourceUpdated ()** , el script primero comprueba para asegurarse de que:</span><span class="sxs-lookup"><span data-stu-id="b8b79-298">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>

* <span data-ttu-id="b8b79-299">es realmente un evento Touchpad (obj. state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="b8b79-299">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="b8b79-300">se origina desde el controlador izquierdo (obj. state. Source). **zurdo**)</span><span class="sxs-lookup"><span data-stu-id="b8b79-300">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="b8b79-301">Si ambos son true, la posición del panel táctil (obj. state. **touchpadPosition**) se asigna a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-301">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="b8b79-302">En **Update ()** , en función de la propiedad **visible** , desencadena los desencadenadores Mostrar y ocultar animación en el componente de animación del selector de colores.</span><span class="sxs-lookup"><span data-stu-id="b8b79-302">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="b8b79-303">En **Update ()** , **selectorPosition** se usa para convertir un rayo en el Colisionador de malla de la rueda de colores, que devuelve una posición UV.</span><span class="sxs-lookup"><span data-stu-id="b8b79-303">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="b8b79-304">Esta posición se puede usar para buscar la coordenada de píxeles y el valor de color de la textura de la rueda de colores.</span><span class="sxs-lookup"><span data-stu-id="b8b79-304">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="b8b79-305">Este valor es accesible para otros scripts a través de la propiedad **SelectedColor** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-305">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![Rueda del selector de colores raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="b8b79-307">Capítulo 4: invalidación del modelo de controlador</span><span class="sxs-lookup"><span data-stu-id="b8b79-307">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="b8b79-308">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-308">Objectives</span></span>

* <span data-ttu-id="b8b79-309">Obtenga información sobre cómo invalidar el modelo de controlador con un modelo 3D personalizado.</span><span class="sxs-lookup"><span data-stu-id="b8b79-309">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="b8b79-311">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-311">Instructions</span></span>

* <span data-ttu-id="b8b79-312">Haga clic en **MotionControllers** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-312">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-313">Haga clic en el círculo en el lado derecho del campo **alternativo de controlador derecho** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-313">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="b8b79-314">Escriba **"BrushController**" y seleccione recurso prefabricado en el resultado.</span><span class="sxs-lookup"><span data-stu-id="b8b79-314">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="b8b79-315">Puede encontrarlo en assets/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-315">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="b8b79-316">Comprobar **usar siempre el modelo derecho alternativo**</span><span class="sxs-lookup"><span data-stu-id="b8b79-316">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="b8b79-318">No es necesario que **BrushController** recurso prefabricado esté incluido en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-318">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="b8b79-319">Sin embargo, para desproteger sus componentes secundarios:</span><span class="sxs-lookup"><span data-stu-id="b8b79-319">However, to check out its child components:</span></span>

* <span data-ttu-id="b8b79-320">En el panel **proyecto** , escriba **BrushController** y arrastre **BrushController** recurso prefabricado al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-320">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="b8b79-322">Encontrará el componente de **información** en **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-322">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="b8b79-323">Usaremos su transformación para iniciar o detener las líneas de dibujo.</span><span class="sxs-lookup"><span data-stu-id="b8b79-323">We will use its transform to start/stop drawing lines.</span></span>

* <span data-ttu-id="b8b79-324">Elimine el **BrushController** en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-324">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-325">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-325">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="b8b79-326">Podrá ver el modelo de pincel reemplazado por el controlador de movimiento de la derecha.</span><span class="sxs-lookup"><span data-stu-id="b8b79-326">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="b8b79-327">Capítulo 5: pintar con seleccionar entrada</span><span class="sxs-lookup"><span data-stu-id="b8b79-327">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="b8b79-328">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-328">Objectives</span></span>

* <span data-ttu-id="b8b79-329">Obtenga información sobre cómo usar el evento de botón Seleccionar para iniciar y detener un dibujo de línea</span><span class="sxs-lookup"><span data-stu-id="b8b79-329">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-330">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-330">Instructions</span></span>

* <span data-ttu-id="b8b79-331">Busque **BrushController** recurso prefabricado en el panel **proyecto** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-331">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="b8b79-332">En el panel **Inspector** , haga doble clic en **BrushController** script para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8b79-332">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="b8b79-333">**Script BrushController**</span><span class="sxs-lookup"><span data-stu-id="b8b79-333">**BrushController script**</span></span>

<span data-ttu-id="b8b79-334">**BrushController** se suscribe a los eventos **InteractionSourcePressed** y **InteractionSourceReleased** de InteractionManager.</span><span class="sxs-lookup"><span data-stu-id="b8b79-334">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="b8b79-335">Cuando se desencadena el evento **InteractionSourcePressed** , la propiedad **Draw** del pincel se establece en true. Cuando se desencadena el evento **InteractionSourceReleased** , la propiedad **Draw** del pincel se establece en false.</span><span class="sxs-lookup"><span data-stu-id="b8b79-335">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="b8b79-336">Mientras **Draw** está establecido en true, el pincel generará puntos en una instancia de Unity **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-336">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="b8b79-337">Se mantiene una referencia a este recurso prefabricado en el campo **Stroke recurso prefabricado** del pincel.</span><span class="sxs-lookup"><span data-stu-id="b8b79-337">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="b8b79-338">Para usar el color seleccionado actualmente en la interfaz de usuario de la rueda del selector de colores, **BrushController** debe tener una referencia al objeto **ColorPickerWheel** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-338">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="b8b79-339">Dado que se crea una instancia de recurso prefabricado de **BrushController** en tiempo de ejecución como controlador de reemplazo, cualquier referencia a los objetos de la escena tendrá que establecerse en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="b8b79-339">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="b8b79-340">En este caso, usamos **GameObject. FindObjectOfType** para encontrar **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="b8b79-340">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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

* <span data-ttu-id="b8b79-341">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-341">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="b8b79-342">Podrá dibujar las líneas y pintar con el botón seleccionar del controlador de la derecha.</span><span class="sxs-lookup"><span data-stu-id="b8b79-342">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="b8b79-343">Capítulo 6: generación de objetos con selección de entrada</span><span class="sxs-lookup"><span data-stu-id="b8b79-343">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="b8b79-344">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b8b79-344">Objectives</span></span>

* <span data-ttu-id="b8b79-345">Obtenga información sobre cómo usar los eventos de entrada del botón seleccionar y agarre</span><span class="sxs-lookup"><span data-stu-id="b8b79-345">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="b8b79-346">Obtener información sobre cómo crear instancias de objetos</span><span class="sxs-lookup"><span data-stu-id="b8b79-346">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-347">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-347">Instructions</span></span>

* <span data-ttu-id="b8b79-348">En el panel **proyecto** , escriba **ObjectSpawner** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="b8b79-348">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="b8b79-349">También puede encontrarlo en assets/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="b8b79-349">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="b8b79-350">Arrastre **ObjectSpawner** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-350">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-351">Haga clic en **ObjectSpawner** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-351">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-352">**ObjectSpawner** tiene un campo denominado **origen de color**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-352">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="b8b79-353">En el panel **jerarquía** , arrastre la referencia **ColorPickerWheel** a este campo.</span><span class="sxs-lookup"><span data-stu-id="b8b79-353">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

    ![Inspector de generación de objetos](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* <span data-ttu-id="b8b79-355">Haga clic en **ObjectSpawner** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-355">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-356">En el panel **Inspector** , haga doble clic en **ObjectSpawner** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8b79-356">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="b8b79-357">**Script ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="b8b79-357">**ObjectSpawner script**</span></span>

<span data-ttu-id="b8b79-358">El **ObjectSpawner** crea instancias de las copias de una malla primitiva (cubo, esfera, cilindro) en el espacio.</span><span class="sxs-lookup"><span data-stu-id="b8b79-358">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="b8b79-359">Cuando se detecta un **InteractionSourcePressed** , comprueba la mano y si se trata de un evento **InteractionSourcePressType. agarre** o **InteractionSourcePressType. Select** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-359">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="b8b79-360">Para un evento de **agarre** , incrementa el índice del tipo de malla actual (esfera, Cube, cylinder)</span><span class="sxs-lookup"><span data-stu-id="b8b79-360">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="b8b79-361">En el caso de un evento **Select** , en **SpawnObject ()** , se crea una instancia de un nuevo objeto, no primario y se publica en el mundo.</span><span class="sxs-lookup"><span data-stu-id="b8b79-361">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="b8b79-362">**ObjectSpawner** usa **ColorPickerWheel** para establecer el color del material del objeto de presentación.</span><span class="sxs-lookup"><span data-stu-id="b8b79-362">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="b8b79-363">A los objetos generados se les asigna una instancia de este material para conservar su color.</span><span class="sxs-lookup"><span data-stu-id="b8b79-363">Spawned objects are given an instance of this material so they will retain their color.</span></span>

* <span data-ttu-id="b8b79-364">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-364">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="b8b79-365">Podrá cambiar los objetos con el botón de agarre y generar objetos con el botón seleccionar.</span><span class="sxs-lookup"><span data-stu-id="b8b79-365">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="b8b79-366">Creación e implementación de una aplicación en el portal de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b8b79-366">Build and deploy app to Mixed Reality Portal</span></span>

* <span data-ttu-id="b8b79-367">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-367">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="b8b79-368">Haga clic en **Agregar escenas abiertas** para agregar la escena actual a las **escenas de la compilación**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-368">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="b8b79-369">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-369">Click **Build**.</span></span>
* <span data-ttu-id="b8b79-370">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="b8b79-370">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="b8b79-371">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-371">Single click the **App** folder.</span></span>
* <span data-ttu-id="b8b79-372">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-372">Click **Select Folder**.</span></span>
* <span data-ttu-id="b8b79-373">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="b8b79-373">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="b8b79-374">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-374">Open the **App** folder.</span></span>
* <span data-ttu-id="b8b79-375">Haga doble clic en el archivo de solución de Visual Studio **YourSceneName. sln** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-375">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="b8b79-376">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-376">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="b8b79-377">Haga clic en la flecha desplegable situada junto al botón dispositivo y seleccione **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-377">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="b8b79-378">Haga clic en **depurar-> iniciar sin depurar** en el menú o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-378">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="b8b79-379">Ahora la aplicación se crea e instala en el portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b8b79-379">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="b8b79-380">Puede volver a iniciarlo a través del menú Inicio en el portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b8b79-380">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="b8b79-381">Herramientas de pincel de diseño avanzadas con diseño radial</span><span class="sxs-lookup"><span data-stu-id="b8b79-381">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="b8b79-383">En este capítulo, obtendrá información sobre cómo reemplazar el modelo de controlador de movimiento predeterminado con una colección de herramientas de pincel personalizada.</span><span class="sxs-lookup"><span data-stu-id="b8b79-383">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="b8b79-384">Como referencia, puede encontrar la escena completada **MixedReality213Advanced** en la carpeta **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-384">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-385">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-385">Instructions</span></span>

* <span data-ttu-id="b8b79-386">En el panel **proyecto** , escriba **BrushSelector** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="b8b79-386">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="b8b79-387">También puede encontrarlo en assets/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="b8b79-387">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="b8b79-388">Arrastre **BrushSelector** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-388">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-389">Para la organización, cree un GameObject vacío denominado **brushes** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-389">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="b8b79-390">Arrastre los siguientes Prefabs desde el panel **proyecto** a los **pinceles**</span><span class="sxs-lookup"><span data-stu-id="b8b79-390">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="b8b79-391">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="b8b79-391">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="b8b79-392">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="b8b79-392">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="b8b79-393">Activos/AppPrefabs/**borrador**</span><span class="sxs-lookup"><span data-stu-id="b8b79-393">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="b8b79-394">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="b8b79-394">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="b8b79-395">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="b8b79-395">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="b8b79-396">Activos/AppPrefabs/**lápiz**</span><span class="sxs-lookup"><span data-stu-id="b8b79-396">Assets/AppPrefabs/**Pencil**</span></span>

    ![Pinceles](images/mixedreality213-brushes-250px.png)

* <span data-ttu-id="b8b79-398">Haga clic en **MotionControllers** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-398">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="b8b79-399">En el panel **Inspector** , desactive **usar modelo de derecho alternativo siempre** en el **visualizador de controlador de movimiento**</span><span class="sxs-lookup"><span data-stu-id="b8b79-399">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="b8b79-400">En el panel **jerarquía** , haga clic en **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="b8b79-400">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="b8b79-401">**BrushSelector** tiene un campo denominado **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="b8b79-401">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="b8b79-402">En el panel **jerarquía** , arrastre el campo **ColorPickerWheel** al **ColorPicker** en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-402">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

    ![Asignar ColorPickerWheel al selector de pincel](images/mr213-brushselector-500px.jpg)

* <span data-ttu-id="b8b79-404">En el panel **jerarquía** , en **BrushSelector** recurso prefabricado, seleccione el objeto de **menú** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-404">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="b8b79-405">En el panel **Inspector** , en el componente **LineObjectCollection** , abra la lista desplegable de la matriz de **objetos** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-405">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="b8b79-406">Verá 6 ranuras vacías.</span><span class="sxs-lookup"><span data-stu-id="b8b79-406">You will see 6 empty slots.</span></span>
* <span data-ttu-id="b8b79-407">En el panel **jerarquía** , arrastre cada uno de los Prefabs primarios bajo los **pinceles** GameObject a estas ranuras en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="b8b79-407">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="b8b79-408">(Asegúrese de que está arrastrando el Prefabs de la escena, no el Prefabs en la carpeta del proyecto).</span><span class="sxs-lookup"><span data-stu-id="b8b79-408">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Selector de pincel](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="b8b79-410">**BrushSelector recurso prefabricado**</span><span class="sxs-lookup"><span data-stu-id="b8b79-410">**BrushSelector prefab**</span></span>

<span data-ttu-id="b8b79-411">Dado que **BrushSelector** hereda **AttachToController**, muestra las opciones de la **mano** y el **elemento** en el panel del **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-411">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="b8b79-412">Hemos seleccionado **right** y **Pointing** para adjuntar herramientas de pincel al controlador de la derecha con dirección hacia delante.</span><span class="sxs-lookup"><span data-stu-id="b8b79-412">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="b8b79-413">El **BrushSelector** hace uso de dos utilidades:</span><span class="sxs-lookup"><span data-stu-id="b8b79-413">The **BrushSelector** makes use of two utilities:</span></span>

* <span data-ttu-id="b8b79-414">**Ellipse**: se usa para generar puntos en el espacio a lo largo de una forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="b8b79-414">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="b8b79-415">**LineObjectCollection**: distribuye objetos usando los puntos generados por cualquier clase de línea (por ejemplo, elipse).</span><span class="sxs-lookup"><span data-stu-id="b8b79-415">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="b8b79-416">Esto es lo que vamos a usar para colocar los pinceles a lo largo de la forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="b8b79-416">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="b8b79-417">Cuando se combinan, estas utilidades se pueden usar para crear un menú radial.</span><span class="sxs-lookup"><span data-stu-id="b8b79-417">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="b8b79-418">**Script LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="b8b79-418">**LineObjectCollection script**</span></span>

<span data-ttu-id="b8b79-419">**LineObjectCollection** tiene controles para el tamaño, la posición y la rotación de objetos distribuidos a lo largo de su línea.</span><span class="sxs-lookup"><span data-stu-id="b8b79-419">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="b8b79-420">Esto resulta útil para crear menús radiales como el selector de pincel.</span><span class="sxs-lookup"><span data-stu-id="b8b79-420">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="b8b79-421">Para crear la apariencia de los pinceles que se escalan verticalmente desde cero a medida que se aproximan a la posición seleccionada del centro, los picos de la curva **ObjectScale** en el centro y en las cintas se desconectan en los bordes.</span><span class="sxs-lookup"><span data-stu-id="b8b79-421">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="b8b79-422">**Script BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="b8b79-422">**BrushSelector script**</span></span>

<span data-ttu-id="b8b79-423">En el caso de **BrushSelector**, hemos elegido usar la animación de procedimientos.</span><span class="sxs-lookup"><span data-stu-id="b8b79-423">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="b8b79-424">En primer lugar, el script **LineObjectCollection** distribuye los modelos de pincel en una elipse.</span><span class="sxs-lookup"><span data-stu-id="b8b79-424">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="b8b79-425">Después, cada pincel es responsable de mantener su posición en la mano del usuario en función de su valor de **DisplayMode** , que cambia en función de la selección.</span><span class="sxs-lookup"><span data-stu-id="b8b79-425">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="b8b79-426">Elegimos un enfoque de procedimiento debido a la alta probabilidad de que las transiciones de posición del pincel se interrumpan cuando el usuario selecciona pinceles.</span><span class="sxs-lookup"><span data-stu-id="b8b79-426">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="b8b79-427">Las animaciones Mecanim pueden controlar las interrupciones correctamente, pero suelen ser más complicadas que una sencilla operación lerp.</span><span class="sxs-lookup"><span data-stu-id="b8b79-427">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="b8b79-428">**BrushSelector** usa una combinación de ambos.</span><span class="sxs-lookup"><span data-stu-id="b8b79-428">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="b8b79-429">Cuando se detecta la entrada del panel táctil, las opciones de pincel se vuelven visibles y se escalan verticalmente a lo largo del menú radial.</span><span class="sxs-lookup"><span data-stu-id="b8b79-429">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="b8b79-430">Después de un período de tiempo de espera (que indica que el usuario ha realizado una selección), las opciones de pincel se vuelven a reducir de nuevo y solo se mantiene el pincel seleccionado.</span><span class="sxs-lookup"><span data-stu-id="b8b79-430">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="b8b79-431">**Visualización de la entrada del panel táctil**</span><span class="sxs-lookup"><span data-stu-id="b8b79-431">**Visualizing touchpad input**</span></span>

<span data-ttu-id="b8b79-432">Incluso en los casos en los que el modelo de controlador se ha reemplazado por completo, puede resultar útil Mostrar la entrada en las entradas del modelo original.</span><span class="sxs-lookup"><span data-stu-id="b8b79-432">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="b8b79-433">Esto ayuda a realizar las acciones del usuario en realidad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-433">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="b8b79-434">En el caso de **BrushSelector** , hemos optado por hacer que el Touchpad esté brevemente visible cuando se recibe la entrada.</span><span class="sxs-lookup"><span data-stu-id="b8b79-434">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="b8b79-435">Para ello, se recupera el elemento Touchpad del controlador, se sustituye su material por un material personalizado y, después, se aplica un degradado al color de ese material en función de la última vez que se recibió la entrada Touchpad.</span><span class="sxs-lookup"><span data-stu-id="b8b79-435">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="b8b79-436">**Selección de la herramienta pincel con entrada Touchpad**</span><span class="sxs-lookup"><span data-stu-id="b8b79-436">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="b8b79-437">Cuando el selector de pincel detecta la entrada presionada del Touchpad, comprueba la posición de la entrada para determinar si estaba a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="b8b79-437">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="b8b79-438">**Grosor del trazo con selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="b8b79-438">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="b8b79-439">En lugar del evento **InteractionSourcePressType. Select** en **InteractionSourcePressed ()** , puede obtener el valor analógico de la cantidad presionada a través de **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-439">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="b8b79-440">Este valor se puede recuperar en **InteractionSourceUpdated ()** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-440">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="b8b79-441">**Script de borrador**</span><span class="sxs-lookup"><span data-stu-id="b8b79-441">**Eraser script**</span></span>

<span data-ttu-id="b8b79-442">El **borrador** es un tipo especial de pincel que reemplaza la función **DrawOverTime ()** del **pincel**base.</span><span class="sxs-lookup"><span data-stu-id="b8b79-442">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="b8b79-443">Mientras que Draw es true, el borrador comprueba si su sugerencia se corta con cualquier trazo de pincel existente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-443">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="b8b79-444">Si lo hace, se agregan a una cola para que se reduzcan y se eliminen.</span><span class="sxs-lookup"><span data-stu-id="b8b79-444">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="b8b79-445">Diseño avanzado: teleportabilidad y Locomotion</span><span class="sxs-lookup"><span data-stu-id="b8b79-445">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="b8b79-446">Si desea permitir que el usuario se mueva por la escena con la teleportabilidad mediante el Stick, use **MixedRealityCameraParent** en lugar de **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-446">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="b8b79-447">También debe agregar **InputManager** y **DefaultCursor**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-447">You also need to add **InputManager** and **DefaultCursor**.</span></span> <span data-ttu-id="b8b79-448">Dado que **MixedRealityCameraParent** ya incluye **MotionControllers** y el **límite** como componentes secundarios, debe quitar **MotionControllers** y recurso prefabricado de **entorno** existentes.</span><span class="sxs-lookup"><span data-stu-id="b8b79-448">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="b8b79-449">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="b8b79-449">Instructions</span></span>

* <span data-ttu-id="b8b79-450">En el panel **jerarquía** , elimine **MixedRealityCamera**, **Environment** y **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="b8b79-450">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="b8b79-451">En el **panel Proyecto**, busque y arrastre el siguiente Prefabs al panel **jerarquía** :</span><span class="sxs-lookup"><span data-stu-id="b8b79-451">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="b8b79-452">Assets/AppPrefabs/INPUT/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="b8b79-452">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="b8b79-453">Assets/AppPrefabs/INPUT/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="b8b79-453">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="b8b79-454">Assets/AppPrefabs/INPUT/Prefabs/cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="b8b79-454">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

    ![Cámara principal de realidad mixta](images/mr213-cameraparent-300px.png)

* <span data-ttu-id="b8b79-456">En el panel **jerarquía** , haga clic en **Administrador de entrada** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-456">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="b8b79-457">En el panel **Inspector** , desplácese hacia abajo hasta la sección **selector simple de puntero único** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-457">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="b8b79-458">En el panel **jerarquía** , arrastre **DefaultCursor** al campo **cursor** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-458">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

    ![Asignación de DefaultCursor](images/mr213-defaultcursor-500px.png)

* <span data-ttu-id="b8b79-460">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-460">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="b8b79-461">Podrá usar el stick analógico para girar izquierda/derecha o teletranspórtate.</span><span class="sxs-lookup"><span data-stu-id="b8b79-461">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="b8b79-462">Fin</span><span class="sxs-lookup"><span data-stu-id="b8b79-462">The end</span></span>

<span data-ttu-id="b8b79-463">Y este es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="b8b79-463">And that's the end of this tutorial!</span></span> <span data-ttu-id="b8b79-464">Aprendió:</span><span class="sxs-lookup"><span data-stu-id="b8b79-464">You learned:</span></span>

* <span data-ttu-id="b8b79-465">Cómo trabajar con modelos de controlador de movimiento en el modo de juego y el tiempo de ejecución de Unity.</span><span class="sxs-lookup"><span data-stu-id="b8b79-465">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="b8b79-466">Cómo usar diferentes tipos de eventos de botón y sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b8b79-466">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="b8b79-467">Cómo superponer los elementos de la interfaz de usuario en la parte superior del controlador o personalizarlos totalmente.</span><span class="sxs-lookup"><span data-stu-id="b8b79-467">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="b8b79-468">Ya está listo para empezar a crear su propia experiencia envolvente con los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="b8b79-468">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="b8b79-469">Escenas completadas</span><span class="sxs-lookup"><span data-stu-id="b8b79-469">Completed scenes</span></span>

* <span data-ttu-id="b8b79-470">En el panel del **proyecto** de Unity, haga clic en la carpeta **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="b8b79-470">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="b8b79-471">Encontrará dos escenas de Unity **MixedReality213** y **MixedReality213Advanced**.</span><span class="sxs-lookup"><span data-stu-id="b8b79-471">You will find two Unity scenes **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="b8b79-472">**MixedReality213**: escena completada con un solo pincel</span><span class="sxs-lookup"><span data-stu-id="b8b79-472">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="b8b79-473">**MixedReality213Advanced**: escena completada con varios pinceles en el ejemplo de la cantidad de imprenta del botón seleccionar</span><span class="sxs-lookup"><span data-stu-id="b8b79-473">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="b8b79-474">Consulta también</span><span class="sxs-lookup"><span data-stu-id="b8b79-474">See also</span></span>

* [<span data-ttu-id="b8b79-475">MR 213 archivos de proyecto de entrada</span><span class="sxs-lookup"><span data-stu-id="b8b79-475">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="b8b79-476">Kit de herramientas de realidad mixta: escena de prueba de controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="b8b79-476">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="b8b79-477">Kit de herramientas de realidad mixta: mecánica de captación</span><span class="sxs-lookup"><span data-stu-id="b8b79-477">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="b8b79-478">Instrucciones de desarrollo de controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="b8b79-478">Motion controller development guidelines</span></span>](motion-controllers.md)
