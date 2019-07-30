---
title: Entrada MR 213
description: Siga este tutorial de codificación con Unity, Visual Studio y auriculares envolventes para aprender los detalles de los controladores de movimiento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, inmersivo, controlador de movimiento, Academia, tutorial
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516401"
---
>[!NOTE]
><span data-ttu-id="9c3c7-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9c3c7-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9c3c7-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9c3c7-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9c3c7-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9c3c7-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="9c3c7-110">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="9c3c7-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="9c3c7-111">Los controladores de movimiento del mundo de la realidad mixta agregan otro nivel de interactividad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="9c3c7-112">Con [los controladores de movimiento](motion-controllers.md), podemos interactuar directamente con los objetos de una manera más natural, de forma similar a las interacciones físicas en la vida real, lo que aumenta la inmersión y la alegría en la experiencia de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="9c3c7-113">En la entrada MR 213, exploraremos los eventos de entrada del controlador de movimiento mediante la creación de una sencilla experiencia de dibujo espacial.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="9c3c7-114">Con esta aplicación, los usuarios pueden pintar en un espacio tridimensional con varios tipos de pinceles y colores.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="9c3c7-115">Temas tratados en este tutorial</span><span class="sxs-lookup"><span data-stu-id="9c3c7-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="9c3c7-119">**Visualización del controlador**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-119">**Controller visualization**</span></span>|<span data-ttu-id="9c3c7-120">**Eventos de entrada del controlador**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-120">**Controller input events**</span></span>|<span data-ttu-id="9c3c7-121">**Controlador y interfaz de usuario personalizados**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="9c3c7-122">Aprenda a representar los modelos de control de movimiento en el modo de juego y el tiempo de ejecución de Unity.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="9c3c7-123">Comprenda los distintos tipos de eventos de botón y sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="9c3c7-124">Obtenga información sobre cómo superponer los elementos de la interfaz de usuario sobre el controlador o personalizarlos totalmente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="9c3c7-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9c3c7-126">Recurso</span><span class="sxs-lookup"><span data-stu-id="9c3c7-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9c3c7-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9c3c7-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9c3c7-128"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="9c3c7-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9c3c7-129">Entrada MR 213: Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="9c3c7-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="9c3c7-130">✔️</span><span class="sxs-lookup"><span data-stu-id="9c3c7-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9c3c7-131">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="9c3c7-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9c3c7-132">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-132">Prerequisites</span></span>

<span data-ttu-id="9c3c7-133">Consulte la lista de comprobación de instalación para los auriculares que se envolverán en [esta página](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="9c3c7-134">En este tutorial se requiere [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="9c3c7-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="9c3c7-135">Archivos de proyecto</span><span class="sxs-lookup"><span data-stu-id="9c3c7-135">Project files</span></span>

* <span data-ttu-id="9c3c7-136">[Descargue los archivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) requeridos por el proyecto y extraiga los archivos en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="9c3c7-137">Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/MixedReality213).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="9c3c7-138">Configuración de Unity</span><span class="sxs-lookup"><span data-stu-id="9c3c7-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="9c3c7-139">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-139">Objectives</span></span>

* <span data-ttu-id="9c3c7-140">Optimizar el desarrollo de Unity para Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9c3c7-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="9c3c7-141">Configuración de una cámara de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9c3c7-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="9c3c7-142">Entorno de instalación</span><span class="sxs-lookup"><span data-stu-id="9c3c7-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-143">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-143">Instructions</span></span>

* <span data-ttu-id="9c3c7-144">Inicia Unity.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-144">Start Unity.</span></span>
* <span data-ttu-id="9c3c7-145">Seleccione **abrir**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-145">Select **Open**.</span></span>
* <span data-ttu-id="9c3c7-146">Navegue hasta el escritorio y busque la carpeta **MixedReality213-Master** que ha desarchivado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="9c3c7-147">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="9c3c7-148">Una vez que Unity termine de cargar los archivos de proyecto, podrá ver el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="9c3c7-149">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="9c3c7-151">Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="9c3c7-152">Establecimiento del dispositivo de destino en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="9c3c7-153">Establecer el tipo de compilación en **D3D**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="9c3c7-154">Establecer SDK en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="9c3c7-155">Comprobación **de C# proyectos de Unity**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="9c3c7-156">Esto permite modificar archivos de script en el proyecto de Visual Studio sin volver a generar el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="9c3c7-157">Haga clic en **configuración del reproductor**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="9c3c7-158">En el panel **Inspector** , desplácese hacia abajo hasta la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="9c3c7-159">En configuración de XR, Active **realidad compatible**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="9c3c7-160">En SDK de realidad virtual, seleccione **Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="9c3c7-162">Cierre la ventana de **configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="9c3c7-163">Estructura del proyecto</span><span class="sxs-lookup"><span data-stu-id="9c3c7-163">Project structure</span></span>

<span data-ttu-id="9c3c7-164">En este tutorial se usa **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="9c3c7-165">Puede encontrar las versiones en [esta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="9c3c7-167">**Escenas completadas para su referencia**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="9c3c7-168">Encontrará dos escenas de Unity completadas en la carpeta Scenes.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="9c3c7-169">**MixedReality213**: Escena completada con un solo pincel</span><span class="sxs-lookup"><span data-stu-id="9c3c7-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="9c3c7-170">**MixedReality213Advanced**: Escena completada para diseño avanzado con varios pinceles</span><span class="sxs-lookup"><span data-stu-id="9c3c7-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="9c3c7-171">**Nueva configuración de escenas para el tutorial**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="9c3c7-172">En Unity, haga clic en **archivo > nueva escena** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="9c3c7-173">Eliminar la **cámara principal** y la **luz direccional**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="9c3c7-174">En el **panel Proyecto**, busque y arrastre el siguiente Prefabs al panel **jerarquía** :</span><span class="sxs-lookup"><span data-stu-id="9c3c7-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="9c3c7-175">Assets/HoloToolkit/INPUT/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="9c3c7-176">Activos/AppPrefabs/**entorno**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-176">Assets/AppPrefabs/**Environment**</span></span>

![Cámara y entorno](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="9c3c7-178">Hay dos Prefabs de cámara en el kit de herramientas de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="9c3c7-179">**MixedRealityCamera. recurso prefabricado**: Solo cámara</span><span class="sxs-lookup"><span data-stu-id="9c3c7-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="9c3c7-180">**MixedRealityCameraParent. recurso prefabricado**: Cámara + teleportabilidad + límite</span><span class="sxs-lookup"><span data-stu-id="9c3c7-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="9c3c7-181">En este tutorial, usaremos **MixedRealityCamera** sin la característica de teleportabilidad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="9c3c7-182">Por este motivo, hemos agregado recurso prefabricado de **entorno** sencillo, que contiene una planta básica para que el usuario sienta.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="9c3c7-183">Para obtener más información acerca de la teleportabilidad con **MixedRealityCameraParent**, consulte el artículo sobre el [diseño avanzado: teleportabilidad y Locomotion](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="9c3c7-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="9c3c7-184">**Configuración de SKYBOX**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-184">**Skybox setup**</span></span>
* <span data-ttu-id="9c3c7-185">Haga clic en **ventana > iluminación > configuración**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="9c3c7-186">Haga clic en el círculo en el lado derecho del **campo material de SKYBOX**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="9c3c7-187">Escriba "Gray" y seleccione **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="9c3c7-188">(Assets/AppPrefabs/support/Materials/SkyboxGray. MAT)</span><span class="sxs-lookup"><span data-stu-id="9c3c7-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Establecer SKYBOX](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="9c3c7-190">Active la opción **SKYBOX** para poder ver el degradado gris asignado SKYBOX</span><span class="sxs-lookup"><span data-stu-id="9c3c7-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Alternar opción SKYBOX](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="9c3c7-192">La escena con MixedRealityCamera, entorno y gris SKYBOX tendrá el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![Entorno de MixedReality213](images/mr213-environment-600px.jpg)
* <span data-ttu-id="9c3c7-194">Haga clic en **archivo > guardar escena como**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="9c3c7-195">**Guardar** la escena en la carpeta Scenes con cualquier nombre</span><span class="sxs-lookup"><span data-stu-id="9c3c7-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="9c3c7-196">Capítulo 1: visualización del controlador</span><span class="sxs-lookup"><span data-stu-id="9c3c7-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="9c3c7-197">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-197">Objectives</span></span>

* <span data-ttu-id="9c3c7-198">Aprenda a representar modelos de controlador de movimiento en el modo de juego de Unity y en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="9c3c7-199">Windows Mixed Reality proporciona un modelo de controlador animado para la visualización del controlador.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="9c3c7-200">Hay varios enfoques que puede realizar para la visualización del controlador en la aplicación:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="9c3c7-201">Predeterminado: uso del controlador predeterminado sin modificación</span><span class="sxs-lookup"><span data-stu-id="9c3c7-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="9c3c7-202">Híbrido: uso del controlador predeterminado, pero personalización de algunos de sus elementos o de la superposición de componentes de interfaz de usuario</span><span class="sxs-lookup"><span data-stu-id="9c3c7-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="9c3c7-203">Reemplazo: usar su propio modelo 3D personalizado para el controlador</span><span class="sxs-lookup"><span data-stu-id="9c3c7-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="9c3c7-204">En este capítulo, veremos los ejemplos de estas personalizaciones del controlador.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-205">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-205">Instructions</span></span>

* <span data-ttu-id="9c3c7-206">En el panel **proyecto** , escriba **MotionControllers** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="9c3c7-207">También puede encontrarlo en assets/HoloToolkit/INPUT/Prefabs/.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="9c3c7-208">Arrastre **MotionControllers** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-209">Haga clic en **MotionControllers** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="9c3c7-210">**MotionControllers recurso prefabricado**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="9c3c7-211">**MotionControllers** recurso prefabricado tiene un script **MotionControllerVisualizer** que proporciona las ranuras para los modelos de controladores alternativos.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="9c3c7-212">Si asigna sus propios modelos 3D personalizados, como una mano o un valor de espada, y activa la casilla "usar siempre el modelo alternativo de la izquierda o la derecha", se verán en lugar del modelo predeterminado.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="9c3c7-213">Usaremos esta ranura en el capítulo 4 para reemplazar el modelo de controlador por un pincel.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="9c3c7-215">**Las**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-215">**Instructions**</span></span>
* <span data-ttu-id="9c3c7-216">En el panel **Inspector** , haga doble clic en **MotionControllerVisualizer** script para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c3c7-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="9c3c7-217">**Script MotionControllerVisualizer**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="9c3c7-218">Las clases **MotionControllerVisualizer** y **MotionControllerInfo** proporcionan los medios para tener acceso a & modificar los modelos de controlador predeterminados.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="9c3c7-219">**MotionControllerVisualizer** se suscribe al evento **InteractionSourceDetected** de Unity y crea automáticamente instancias de los modelos de controlador cuando se encuentran.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="9c3c7-220">Los modelos de controlador se entregan según [la especificación glTF](https://github.com/KhronosGroup/glTF).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="9c3c7-221">Este formato se ha creado para proporcionar un formato común, a la vez que mejora el proceso que subyace a la transmisión y desempaquetado de recursos 3D.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="9c3c7-222">En este caso, es necesario recuperar y cargar los modelos de controlador en tiempo de ejecución, ya que queremos que la experiencia del usuario sea lo más fluida posible y no se garantice qué versión de los controladores de movimiento puede estar usando el usuario.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="9c3c7-223">Este curso, a través del kit de herramientas de la realidad mixta, usa una versión del [proyecto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)del Grupo Khronos.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="9c3c7-224">Una vez que se ha entregado el controlador, los scripts pueden usar **MotionControllerInfo** para buscar las transformaciones de elementos de controlador específicos para que puedan colocarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="9c3c7-225">En un capítulo posterior, se aprenderá a usar estos scripts para adjuntar elementos de interfaz de usuario a los controladores.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="9c3c7-226">*En algunos scripts, encontrará bloques de código con **#if. UNITY_EDITOR** o **UNITY_WSA**. Estos bloques de código solo se ejecutan en el tiempo de ejecución de UWP al implementar en Windows. Esto se debe a que el conjunto de API que usa el editor de Unity y el tiempo de ejecución de la aplicación para UWP son diferentes.*</span><span class="sxs-lookup"><span data-stu-id="9c3c7-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="9c3c7-227">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="9c3c7-228">Podrá ver la escena con controladores de movimiento en el casco.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="9c3c7-229">Puede ver animaciones detalladas para los clics de botón, el movimiento del stick analógico y el resaltado táctil de Touchpad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![Visualización predeterminada de MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="9c3c7-231">Capítulo 2: adjuntar elementos de la interfaz de usuario al controlador</span><span class="sxs-lookup"><span data-stu-id="9c3c7-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="9c3c7-232">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-232">Objectives</span></span>

* <span data-ttu-id="9c3c7-233">Más información sobre los elementos de los controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="9c3c7-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="9c3c7-234">Obtenga información acerca de cómo adjuntar objetos a partes específicas de los controladores</span><span class="sxs-lookup"><span data-stu-id="9c3c7-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="9c3c7-235">En este capítulo, aprenderá a agregar elementos de la interfaz de usuario al controlador, al que el usuario puede acceder y manipular fácilmente en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="9c3c7-236">También aprenderá a agregar una interfaz de usuario del selector de colores simple mediante la entrada del panel táctil.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-237">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-237">Instructions</span></span>

* <span data-ttu-id="9c3c7-238">En el panel **proyecto** , busque el script **MotionControllerInfo** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="9c3c7-239">En el resultado de la búsqueda, haga doble clic en **MotionControllerInfo** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="9c3c7-240">**Script MotionControllerInfo**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="9c3c7-241">El primer paso es elegir a qué elemento del controlador desea asociar la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="9c3c7-242">Estos elementos se definen en **ControllerElementEnum** en **MotionControllerInfo.CS**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="9c3c7-244">**Inicio**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-244">**Home**</span></span>
* <span data-ttu-id="9c3c7-245">**MENU**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-245">**Menu**</span></span>
* <span data-ttu-id="9c3c7-246">**Visión**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-246">**Grasp**</span></span>
* <span data-ttu-id="9c3c7-247">**Palanca**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-247">**Thumbstick**</span></span>
* <span data-ttu-id="9c3c7-248">**No**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-248">**Select**</span></span>
* <span data-ttu-id="9c3c7-249">**Panel táctil**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-249">**Touchpad**</span></span>
* <span data-ttu-id="9c3c7-250">**Pose de puntero** : este elemento representa la punta de la dirección de reenvío hacia delante del controlador.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="9c3c7-251">**Las**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-251">**Instructions**</span></span>
* <span data-ttu-id="9c3c7-252">En el panel **proyecto** , busque el script **AttachToController** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="9c3c7-253">En el resultado de la búsqueda, haga doble clic en **AttachToController** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="9c3c7-254">**Script AttachToController**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-254">**AttachToController script**</span></span>

<span data-ttu-id="9c3c7-255">El script **AttachToController** proporciona una manera sencilla de adjuntar cualquier objeto a un elemento y una manecilla de controlador especificados.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="9c3c7-256">En **AttachElementToController ()** ,</span><span class="sxs-lookup"><span data-stu-id="9c3c7-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="9c3c7-257">Comprobar la mano mediante **MotionControllerInfo. Handl**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="9c3c7-258">Obtiene un elemento específico del controlador mediante **MotionControllerInfo. TryGetElement ()**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="9c3c7-259">Después de recuperar la transformación del elemento del modelo del controlador, el objeto primario que se encuentra en él y establecer la posición local del objeto & la rotación en cero.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="9c3c7-260">La manera más sencilla de usar el script **AttachToController** es heredar de él, como hemos hecho en el caso de **ColorPickerWheel.**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="9c3c7-261">Simplemente invalide las funciones **OnAttachToController** y **OnDetatchFromController** para realizar la instalación o el desglose cuando el controlador se detecta o se desconecta.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="9c3c7-262">**Las**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-262">**Instructions**</span></span>
* <span data-ttu-id="9c3c7-263">En el panel **proyecto** , escriba en el cuadro de búsqueda **ColorPickerWheel**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="9c3c7-264">También puede encontrarlo en assets/AppPrefabs/.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="9c3c7-265">Arrastre **ColorPickerWheel** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-266">Haga clic en **ColorPickerWheel** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-267">En el panel **Inspector** , haga doble clic en **ColorPickerWheel** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel recurso prefabricado](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="9c3c7-269">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="9c3c7-270">Dado que **ColorPickerWheel** hereda **AttachToController**, muestra la **mano** y el **elemento** en el panel del **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="9c3c7-271">Vamos a asociar la interfaz de usuario al elemento Touchpad del controlador izquierdo.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="9c3c7-273">**ColorPickerWheel** invalida **OnAttachToController** y **OnDetatchFromController** para suscribirse al evento de entrada que se usará en el capítulo siguiente para la selección de color con entrada de Touchpad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="9c3c7-274">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="9c3c7-275">**Método alternativo para adjuntar objetos a los controladores**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="9c3c7-276">Se recomienda que los scripts hereden de **AttachToController** e invalide **OnAttachToController**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="9c3c7-277">Sin embargo, esto no siempre es posible.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-277">However, this may not always be possible.</span></span> <span data-ttu-id="9c3c7-278">Una alternativa es usarla como componente independiente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="9c3c7-279">Esto puede ser útil si desea adjuntar un recurso prefabricado existente a un controlador sin refactorizar los scripts.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="9c3c7-280">Basta con que la clase espere a que Isattached (se establezca en true antes de realizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="9c3c7-281">La manera más sencilla de hacerlo es usar una corutina para ' Start '.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="9c3c7-282">Capítulo 3: trabajar con la entrada de Touchpad</span><span class="sxs-lookup"><span data-stu-id="9c3c7-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="9c3c7-283">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-283">Objectives</span></span>

* <span data-ttu-id="9c3c7-284">Obtenga información sobre cómo obtener eventos de datos de entrada de Touchpad</span><span class="sxs-lookup"><span data-stu-id="9c3c7-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="9c3c7-285">Aprenda a usar la información de posición del eje Touchpad para la experiencia de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9c3c7-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-286">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-286">Instructions</span></span>

* <span data-ttu-id="9c3c7-287">En el panel **jerarquía** , haga clic en **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="9c3c7-288">En el panel **Inspector** , en **Animatior**, haga doble clic en **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="9c3c7-289">Podrá ver la pestaña animador abierta</span><span class="sxs-lookup"><span data-stu-id="9c3c7-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="9c3c7-290">**Mostrar u ocultar la interfaz de usuario con el controlador de animación de Unity**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="9c3c7-291">Para mostrar y ocultar la interfaz de usuario de **ColorPickerWheel** con la animación, usamos el [sistema de animación de Unity](https://docs.unity3d.com/Manual/AnimationOverview.html).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="9c3c7-292">Si se establece la propiedad **visible** de **ColorPickerWheel**en los desencadenadores true o false, se **muestran** y **ocultan** los desencadenadores de animación.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="9c3c7-293">Los parámetros de **Mostrar** y **ocultar** se definen en el controlador de animación **ColorPickerWheelController** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Controlador de animación de Unity](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="9c3c7-295">**Las**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-295">**Instructions**</span></span>
* <span data-ttu-id="9c3c7-296">En el panel **jerarquía** , seleccione **ColorPickerWheel** recurso prefabricado</span><span class="sxs-lookup"><span data-stu-id="9c3c7-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="9c3c7-297">En el panel **Inspector** , haga doble clic en **ColorPickerWheel** script para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c3c7-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="9c3c7-298">**Script ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="9c3c7-299">**ColorPickerWheel** se suscribe al evento **InteractionSourceUpdated** de Unity para escuchar eventos Touchpad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="9c3c7-300">En **InteractionSourceUpdated ()** , el script primero comprueba para asegurarse de que:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="9c3c7-301">es realmente un evento Touchpad (obj. state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="9c3c7-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="9c3c7-302">se origina desde el controlador izquierdo (obj. state. Source). **zurdo**)</span><span class="sxs-lookup"><span data-stu-id="9c3c7-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="9c3c7-303">Si ambos son true, la posición del panel táctil (obj. state. **touchpadPosition**) se asigna a **selectorPosition**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="9c3c7-304">En **Update ()** , en función de la propiedad **visible** , desencadena los desencadenadores Mostrar y ocultar animación en el componente de animación del selector de colores.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="9c3c7-305">En **Update ()** , **selectorPosition** se usa para convertir un rayo en el Colisionador de malla de la rueda de colores, que devuelve una posición UV.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="9c3c7-306">Esta posición se puede usar para buscar la coordenada de píxeles y el valor de color de la textura de la rueda de colores.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="9c3c7-307">Este valor es accesible para otros scripts a través de la propiedad **SelectedColor** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="9c3c7-309">Capítulo 4: invalidación del modelo de controlador</span><span class="sxs-lookup"><span data-stu-id="9c3c7-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="9c3c7-310">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-310">Objectives</span></span>

* <span data-ttu-id="9c3c7-311">Obtenga información sobre cómo invalidar el modelo de controlador con un modelo 3D personalizado.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="9c3c7-313">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-313">Instructions</span></span>

* <span data-ttu-id="9c3c7-314">Haga clic en **MotionControllers** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-315">Haga clic en el círculo en el lado derecho del campo **alternativo de controlador derecho** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="9c3c7-316">Escriba **"BrushController**" y seleccione recurso prefabricado en el resultado.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="9c3c7-317">Puede encontrarlo en assets/AppPrefabs/**BrushController**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="9c3c7-318">Comprobar **usar siempre el modelo derecho alternativo**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="9c3c7-320">No es necesario que **BrushController** recurso prefabricado esté incluido en el panel de jerarquías.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="9c3c7-321">Sin embargo, para desproteger sus componentes secundarios:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-321">However, to check out its child components:</span></span>
* <span data-ttu-id="9c3c7-322">En el panel **proyecto** , escriba **BrushController** y arrastre **BrushController** recurso prefabricado al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="9c3c7-324">Encontrará el componente de **información** en **BrushController**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="9c3c7-325">Usaremos su transformación para iniciar o detener las líneas de dibujo.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="9c3c7-326">Elimine el **BrushController** en el panel de **jerarquías** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-327">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="9c3c7-328">Podrá ver el modelo de pincel reemplazado por el controlador de movimiento de la derecha.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="9c3c7-329">Capítulo 5: pintar con seleccionar entrada</span><span class="sxs-lookup"><span data-stu-id="9c3c7-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="9c3c7-330">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-330">Objectives</span></span>

* <span data-ttu-id="9c3c7-331">Obtenga información sobre cómo usar el evento de botón Seleccionar para iniciar y detener un dibujo de línea</span><span class="sxs-lookup"><span data-stu-id="9c3c7-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-332">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-332">Instructions</span></span>

* <span data-ttu-id="9c3c7-333">Busque **BrushController** recurso prefabricado en el panel **proyecto** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="9c3c7-334">En el panel **Inspector** , haga doble clic en **BrushController** script para ver el código en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c3c7-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="9c3c7-335">**Script BrushController**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-335">**BrushController script**</span></span>

<span data-ttu-id="9c3c7-336">**BrushController** se suscribe a los eventos **InteractionSourcePressed** y **InteractionSourceReleased** de InteractionManager.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="9c3c7-337">Cuando se desencadena el evento **InteractionSourcePressed** , la propiedad **Draw** del pincel se establece en true. Cuando se desencadena el evento **InteractionSourceReleased** , la propiedad **Draw** del pincel se establece en false.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="9c3c7-338">Mientras **Draw** está establecido en true, el pincel generará puntos en una instancia de Unity **LineRenderer**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="9c3c7-339">Se mantiene una referencia a este recurso prefabricado en el campo **Stroke recurso prefabricado** del pincel.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="9c3c7-340">Para usar el color seleccionado actualmente en la interfaz de usuario de la rueda del selector de colores, **BrushController** debe tener una referencia al objeto **ColorPickerWheel** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="9c3c7-341">Dado que se crea una instancia de recurso prefabricado de **BrushController** en tiempo de ejecución como controlador de reemplazo, cualquier referencia a los objetos de la escena tendrá que establecerse en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="9c3c7-342">En este caso, usamos **GameObject. FindObjectOfType** para encontrar **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="9c3c7-343">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="9c3c7-344">Podrá dibujar las líneas y pintar con el botón seleccionar del controlador de la derecha.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="9c3c7-345">Capítulo 6: generación de objetos con selección de entrada</span><span class="sxs-lookup"><span data-stu-id="9c3c7-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="9c3c7-346">Objetivos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-346">Objectives</span></span>

* <span data-ttu-id="9c3c7-347">Obtenga información sobre cómo usar los eventos de entrada del botón seleccionar y agarre</span><span class="sxs-lookup"><span data-stu-id="9c3c7-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="9c3c7-348">Obtener información sobre cómo crear instancias de objetos</span><span class="sxs-lookup"><span data-stu-id="9c3c7-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-349">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-349">Instructions</span></span>

* <span data-ttu-id="9c3c7-350">En el panel **proyecto** , escriba **ObjectSpawner** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="9c3c7-351">También puede encontrarlo en assets/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="9c3c7-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="9c3c7-352">Arrastre **ObjectSpawner** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-353">Haga clic en **ObjectSpawner** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-354">**ObjectSpawner** tiene un campo denominado **origen de color**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="9c3c7-355">En el panel **jerarquía** , arrastre la referencia **ColorPickerWheel** a este campo.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![Inspector de generación de objetos](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="9c3c7-357">Haga clic en **ObjectSpawner** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-358">En el panel **Inspector** , haga doble clic en **ObjectSpawner** script para ver el código en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="9c3c7-359">**Script ObjectSpawner**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="9c3c7-360">El **ObjectSpawner** crea instancias de las copias de una malla primitiva (cubo, esfera, cilindro) en el espacio.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="9c3c7-361">Cuando se detecta un **InteractionSourcePressed** , comprueba la mano y si se trata de un evento **InteractionSourcePressType. agarre** o **InteractionSourcePressType. Select** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="9c3c7-362">Para un evento de **agarre** , incrementa el índice del tipo de malla actual (esfera, Cube, cylinder)</span><span class="sxs-lookup"><span data-stu-id="9c3c7-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="9c3c7-363">En el caso de un evento **Select** , en **SpawnObject ()** , se crea una instancia de un nuevo objeto, no primario y se publica en el mundo.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="9c3c7-364">**ObjectSpawner** usa **ColorPickerWheel** para establecer el color del material del objeto de presentación.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="9c3c7-365">A los objetos generados se les asigna una instancia de este material para conservar su color.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="9c3c7-366">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="9c3c7-367">Podrá cambiar los objetos con el botón de agarre y generar objetos con el botón seleccionar.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="9c3c7-368">Creación e implementación de una aplicación en el portal de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9c3c7-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="9c3c7-369">En Unity, seleccione **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="9c3c7-370">Haga clic en **Agregar escenas abiertas** para agregar la escena actual a las **escenas de la compilación**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="9c3c7-371">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-371">Click **Build**.</span></span>
* <span data-ttu-id="9c3c7-372">Cree una **nueva carpeta** denominada "app".</span><span class="sxs-lookup"><span data-stu-id="9c3c7-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="9c3c7-373">Haga clic en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="9c3c7-374">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="9c3c7-375">Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="9c3c7-376">Abra la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-376">Open the **App** folder.</span></span>
* <span data-ttu-id="9c3c7-377">Haga doble clic en el archivo de solución de Visual Studio **YourSceneName. sln** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="9c3c7-378">Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="9c3c7-379">Haga clic en la flecha desplegable situada junto al botón dispositivo y seleccione **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="9c3c7-380">Haga clic en depurar **-> iniciar sin** depurar en el menú o presione **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="9c3c7-381">Ahora la aplicación se crea e instala en el portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="9c3c7-382">Puede volver a iniciarlo a través del menú Inicio en el portal de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="9c3c7-383">Herramientas de pincel de diseño avanzadas con diseño radial</span><span class="sxs-lookup"><span data-stu-id="9c3c7-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="9c3c7-385">En este capítulo, obtendrá información sobre cómo reemplazar el modelo de controlador de movimiento predeterminado con una colección de herramientas de pincel personalizada.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="9c3c7-386">Como referencia, puede encontrar la escena completada **MixedReality213Advanced** en la carpeta Scenes.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-387">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-387">Instructions</span></span>

* <span data-ttu-id="9c3c7-388">En el panel **proyecto** , escriba **BrushSelector** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="9c3c7-389">También puede encontrarlo en assets/AppPrefabs/</span><span class="sxs-lookup"><span data-stu-id="9c3c7-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="9c3c7-390">Arrastre **BrushSelector** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-391">Para la organización, cree un GameObject vacío denominado brushes.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="9c3c7-392">Arrastre los siguientes Prefabs desde el panel **proyecto** a los **pinceles**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="9c3c7-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="9c3c7-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="9c3c7-395">Activos/AppPrefabs/**borrador**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="9c3c7-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="9c3c7-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="9c3c7-398">Activos/AppPrefabs/**lápiz**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-398">Assets/AppPrefabs/**Pencil**</span></span>

![Pinceles](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="9c3c7-400">Haga clic en **MotionControllers** recurso prefabricado en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="9c3c7-401">En el panel **Inspector** , desactive **usar modelo de derecho alternativo siempre** en el visualizador de **controlador de movimiento**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="9c3c7-402">En el panel **jerarquía** , haga clic en **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="9c3c7-403">**BrushSelector** tiene un campo denominado **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="9c3c7-404">En el panel **jerarquía** , arrastre el campo **ColorPickerWheel** al **ColorPicker** en el panel **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![Asignar ColorPickerWheel al selector de pincel](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="9c3c7-406">En el panel **jerarquía** , en **BrushSelector** recurso prefabricado, seleccione el objeto de **menú** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="9c3c7-407">En el panel **Inspector** , en el componente **LineObjectCollection** , abra la lista desplegable de la matriz de **objetos** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="9c3c7-408">Verá 6 ranuras vacías.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="9c3c7-409">En el panel **jerarquía** , arrastre cada uno de los Prefabs primarios bajo los **pinceles** GameObject a estas ranuras en cualquier orden.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="9c3c7-410">(Asegúrese de que está arrastrando el Prefabs de la escena, no el Prefabs en la carpeta del proyecto).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![Selector de pincel](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="9c3c7-412">**BrushSelector recurso prefabricado**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="9c3c7-413">Dado que **BrushSelector** hereda **AttachToController**, muestra las opciones de la **mano** y el **elemento** en el panel del **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="9c3c7-414">Hemos seleccionado **right** y **Pointing** para adjuntar herramientas de pincel al controlador de la derecha con dirección hacia delante.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="9c3c7-415">El **BrushSelector** hace uso de dos utilidades:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="9c3c7-416">**Ellipse**: se usa para generar puntos en el espacio a lo largo de una forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="9c3c7-417">**LineObjectCollection**: distribuye objetos usando los puntos generados por cualquier clase de línea (por ejemplo, elipse).</span><span class="sxs-lookup"><span data-stu-id="9c3c7-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="9c3c7-418">Esto es lo que vamos a usar para colocar los pinceles a lo largo de la forma de elipse.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="9c3c7-419">Cuando se combinan, estas utilidades se pueden usar para crear un menú radial.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="9c3c7-420">**Script LineObjectCollection**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="9c3c7-421">**LineObjectCollection** tiene controles para el tamaño, la posición y la rotación de objetos distribuidos a lo largo de su línea.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="9c3c7-422">Esto resulta útil para crear menús radiales como el selector de pincel.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="9c3c7-423">Para crear la apariencia de los pinceles que se escalan verticalmente desde cero a medida que se aproximan a la posición seleccionada del centro, los picos de la curva **ObjectScale** en el centro y en las cintas se desconectan en los bordes.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="9c3c7-424">**Script BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-424">**BrushSelector script**</span></span>

<span data-ttu-id="9c3c7-425">En el caso de **BrushSelector**, hemos elegido usar la animación de procedimientos.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="9c3c7-426">En primer lugar, el script **LineObjectCollection** distribuye los modelos de pincel en una elipse.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="9c3c7-427">Después, cada pincel es responsable de mantener su posición en la mano del usuario en función de su valor de **DisplayMode** , que cambia en función de la selección.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="9c3c7-428">Elegimos un enfoque de procedimiento debido a la alta probabilidad de que las transiciones de posición del pincel se interrumpan cuando el usuario selecciona pinceles.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="9c3c7-429">Las animaciones Mecanim pueden controlar las interrupciones correctamente, pero suelen ser más complicadas que una sencilla operación lerp.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="9c3c7-430">**BrushSelector** usa una combinación de ambos.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="9c3c7-431">Cuando se detecta la entrada del panel táctil, las opciones de pincel se vuelven visibles y se escalan verticalmente a lo largo del menú radial.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="9c3c7-432">Después de un período de tiempo de espera (que indica que el usuario ha realizado una selección), las opciones de pincel se vuelven a reducir de nuevo y solo se mantiene el pincel seleccionado.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="9c3c7-433">**Visualización de la entrada del panel táctil**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="9c3c7-434">Incluso en los casos en los que el modelo de controlador se ha reemplazado por completo, puede resultar útil Mostrar la entrada en las entradas del modelo original.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="9c3c7-435">Esto ayuda a realizar las acciones del usuario en realidad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="9c3c7-436">En el caso de **BrushSelector** , hemos optado por hacer que el Touchpad esté brevemente visible cuando se recibe la entrada.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="9c3c7-437">Para ello, se recupera el elemento Touchpad del controlador, se sustituye su material por un material personalizado y, después, se aplica un degradado al color de ese material en función de la última vez que se recibió la entrada Touchpad.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="9c3c7-438">**Selección de la herramienta pincel con entrada Touchpad**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="9c3c7-439">Cuando el selector de pincel detecta la entrada presionada del Touchpad, comprueba la posición de la entrada para determinar si estaba a la izquierda o a la derecha.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="9c3c7-440">**Grosor del trazo con selectPressedAmount**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="9c3c7-441">En lugar del evento **InteractionSourcePressType. Select** en **InteractionSourcePressed ()** , puede obtener el valor analógico de la cantidad presionada a través de **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="9c3c7-442">Este valor se puede recuperar en **InteractionSourceUpdated ()** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="9c3c7-443">**Script de borrador**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-443">**Eraser script**</span></span>

<span data-ttu-id="9c3c7-444">El borrador es un tipo especial de pincel que reemplaza la función **DrawOverTime ()** del **pincel**base.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="9c3c7-445">Mientras que Draw es true, el borrador comprueba si su sugerencia se corta con cualquier trazo de pincel existente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="9c3c7-446">Si lo hace, se agregan a una cola para que se reduzcan y se eliminen.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="9c3c7-447">Diseño avanzado: teleportabilidad y Locomotion</span><span class="sxs-lookup"><span data-stu-id="9c3c7-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="9c3c7-448">Si desea permitir que el usuario se mueva por la escena con la teleportabilidad mediante el Stick, use **MixedRealityCameraParent** en lugar de **MixedRealityCamera**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="9c3c7-449">También debe agregar **InputManager** y **DefaultCusor**.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="9c3c7-450">Dado que **MixedRealityCameraParent** ya incluye **MotionControllers** y el **límite** como componentes secundarios, debe quitar **MotionControllers** y recurso prefabricado de **entorno** existentes.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="9c3c7-451">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="9c3c7-451">Instructions</span></span>

* <span data-ttu-id="9c3c7-452">En el panel **jerarquía** , elimine **MixedRealityCamera**, **Environment** y **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="9c3c7-453">En el **panel Proyecto**, busque y arrastre el siguiente Prefabs al panel **jerarquía** :</span><span class="sxs-lookup"><span data-stu-id="9c3c7-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="9c3c7-454">Assets/AppPrefabs/INPUT/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="9c3c7-455">Assets/AppPrefabs/INPUT/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="9c3c7-456">Assets/AppPrefabs/INPUT/Prefabs/cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="9c3c7-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![Cámara principal de realidad mixta](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="9c3c7-458">En el panel **jerarquía** , haga clic en **Administrador de entrada** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="9c3c7-459">En el panel **Inspector** , desplácese hacia abajo hasta la sección **selector simple de puntero único** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="9c3c7-460">En el panel **jerarquía** , arrastre **DefaultCursor** al campo **cursor** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![Asignación de DefaultCursor](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="9c3c7-462">**Guarde** la escena y haga clic en el botón **reproducir** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="9c3c7-463">Podrá usar el stick analógico para girar izquierda/derecha o teletranspórtate.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="9c3c7-464">Fin</span><span class="sxs-lookup"><span data-stu-id="9c3c7-464">The end</span></span>

<span data-ttu-id="9c3c7-465">Y este es el final de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="9c3c7-466">Aprendió:</span><span class="sxs-lookup"><span data-stu-id="9c3c7-466">You learned:</span></span>
* <span data-ttu-id="9c3c7-467">Cómo trabajar con modelos de controlador de movimiento en el modo de juego y el tiempo de ejecución de Unity.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="9c3c7-468">Cómo usar diferentes tipos de eventos de botón y sus aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="9c3c7-469">Cómo superponer los elementos de la interfaz de usuario en la parte superior del controlador o personalizarlos totalmente.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="9c3c7-470">Ya está listo para empezar a crear su propia experiencia envolvente con los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="9c3c7-471">Escenas completadas</span><span class="sxs-lookup"><span data-stu-id="9c3c7-471">Completed scenes</span></span>

* <span data-ttu-id="9c3c7-472">En el panel del **proyecto** de Unity, haga clic en la carpeta **Scenes** .</span><span class="sxs-lookup"><span data-stu-id="9c3c7-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="9c3c7-473">Encontrará dos sceens **MixedReality213** y **MixedReality213Advanced**de Unity.</span><span class="sxs-lookup"><span data-stu-id="9c3c7-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="9c3c7-474">**MixedReality213**: Escena completada con un solo pincel</span><span class="sxs-lookup"><span data-stu-id="9c3c7-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="9c3c7-475">**MixedReality213Advanced**: Escena completada con varios pinceles en el ejemplo de la cantidad de imprenta del botón seleccionar</span><span class="sxs-lookup"><span data-stu-id="9c3c7-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="9c3c7-476">Vea también</span><span class="sxs-lookup"><span data-stu-id="9c3c7-476">See also</span></span>

* [<span data-ttu-id="9c3c7-477">MR 213 archivos de proyecto de entrada</span><span class="sxs-lookup"><span data-stu-id="9c3c7-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="9c3c7-478">Kit de herramientas de realidad mixta: escena de prueba de controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="9c3c7-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="9c3c7-479">Kit de herramientas de realidad mixta: mecánica de captación</span><span class="sxs-lookup"><span data-stu-id="9c3c7-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="9c3c7-480">Instrucciones de desarrollo de controlador de movimiento</span><span class="sxs-lookup"><span data-stu-id="9c3c7-480">Motion controller development guidelines</span></span>](motion-controllers.md)
