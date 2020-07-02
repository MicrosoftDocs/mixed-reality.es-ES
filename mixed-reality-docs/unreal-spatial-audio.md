---
title: Audio espacial en Unreal
description: Información general del complemento de audio espacial para Unreal Engine.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446816"
---
# <a name="spatial-audio-in-unreal"></a><span data-ttu-id="6e510-104">Audio espacial en Unreal</span><span class="sxs-lookup"><span data-stu-id="6e510-104">Spatial Audio in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6e510-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="6e510-105">Overview</span></span>

<span data-ttu-id="6e510-106">A diferencia de la visión, los seres humanos escuchan el sonido envolvente en 360 grados.</span><span class="sxs-lookup"><span data-stu-id="6e510-106">Unlike vision, humans hear in 360 degree surround sound.</span></span> <span data-ttu-id="6e510-107">El sonido espacial emula el funcionamiento de la audición humana y proporciona las indicaciones necesarias para identificar las ubicaciones del sonido en el espacio real.</span><span class="sxs-lookup"><span data-stu-id="6e510-107">Spatial sound emulates how human hearing works, providing the cues needed to identify sound locations in world-space.</span></span> <span data-ttu-id="6e510-108">Al agregar sonido espacial en las aplicaciones de realidad mixta, mejora el nivel de inmersión de la experiencia de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="6e510-108">When you add spatial sound in your mixed reality applications, you're enhancing the level of immersion your users experience.</span></span>  

<span data-ttu-id="6e510-109">El procesamiento de sonido espacial de alta calidad es complejo, por lo que HoloLens 2 incluye hardware dedicado para procesar esos objetos de sonido.</span><span class="sxs-lookup"><span data-stu-id="6e510-109">High quality spatial sound processing is complex, so the HoloLens 2 comes with dedicated hardware for processing those sound objects.</span></span>  <span data-ttu-id="6e510-110">Para poder acceder a este soporte de procesamiento de hardware, debe instalar el complemento **MicrosoftSpatialSound** en su proyecto de Unreal.</span><span class="sxs-lookup"><span data-stu-id="6e510-110">Before you can access this hardware processing support, you'll need to install the **MicrosoftSpatialSound** plugin in your Unreal project.</span></span> <span data-ttu-id="6e510-111">Este artículo le guiará a través de la instalación y configuración de ese complemento y le indicará recursos más detallados para usar el sonido espacial en Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="6e510-111">This article will walk you through the installation and configuration of that plugin and point you towards more in-depth resources for using spatial sound in the Unreal engine.</span></span> 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a><span data-ttu-id="6e510-112">Instalación del complemento de sonido espacial de Microsoft</span><span class="sxs-lookup"><span data-stu-id="6e510-112">Installing the Microsoft Spatial Sound plugin</span></span> 

<span data-ttu-id="6e510-113">El primer paso para agregar sonido espacial a su proyecto es instalar el complemento de sonido espacial de Microsoft, que puede buscar de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6e510-113">The first step to adding spatial sound to your project is installing the Microsoft Spatial Sound plugin, which you can find by:</span></span> 

1. <span data-ttu-id="6e510-114">Haga clic en **Editar > Complementos** y busque **MicrosoftSpatialSound** en el cuadro de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="6e510-114">Clicking **Edit > Plugins** and searching for **MicrosoftSpatialSound** in the search box.</span></span> 
2. <span data-ttu-id="6e510-115">Active la casilla **Habilitado** en el complemento **MicrosoftSpatialSound**.</span><span class="sxs-lookup"><span data-stu-id="6e510-115">Selecting the **Enabled** checkbox in the **MicrosoftSpatialSound** plugin.</span></span> 
3. <span data-ttu-id="6e510-116">Reinicie el editor de Unreal mediante la opción **Reiniciar ahora** desde la página de complementos.</span><span class="sxs-lookup"><span data-stu-id="6e510-116">Restarting the Unreal Editor by selecting **Restart Now** from the plugins page.</span></span> 

> [!NOTE]
> <span data-ttu-id="6e510-117">Si todavía no lo ha hecho, deberá instalar los complementos de **Microsoft Windows Mixed Reality** y **HoloLens** siguiendo las instrucciones de la sección **[Inicialización del proyecto](unreal-uxt-ch2.md)** de nuestra serie de tutoriales de Unreal.</span><span class="sxs-lookup"><span data-stu-id="6e510-117">If you haven't already, you'll need to install the **Microsoft Windows Mixed Reality** and **HoloLens** plugins by following the instructions in the **[Initializing your project](unreal-uxt-ch2.md)** section of our Unreal tutorial series.</span></span>

![Complemento de audio espacial de Unreal](images/unreal-spatial-audio-img-01.png)

<span data-ttu-id="6e510-119">Cuando se reinicia el editor, el proyecto ya está preparado.</span><span class="sxs-lookup"><span data-stu-id="6e510-119">Once the editor restarts, your project is all set!</span></span>


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a><span data-ttu-id="6e510-120">Configuración del complemento de espacialización para la plataforma HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6e510-120">Setting the spatialization plugin for HoloLens 2 platform</span></span>
<span data-ttu-id="6e510-121">La configuración del complemento de espacialización se realiza por plataforma.</span><span class="sxs-lookup"><span data-stu-id="6e510-121">Configuring the spatialization plugin is done on a per-platform basis.</span></span>  <span data-ttu-id="6e510-122">Puede habilitar el complemento de sonido espacial de Microsoft para HoloLens 2 de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6e510-122">You can enable the Microsoft Spatial Sound plugin for the HoloLens 2 by:</span></span>
1. <span data-ttu-id="6e510-123">Seleccione **Edit > Projects Settings** (Editar > Configuración del proyecto), desplácese a **Platforms** (Plataformas) y haga clic en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="6e510-123">Selecting **Edit > Project Settings**, scrolling to **Platforms** and clicking **HoloLens**.</span></span>
2. <span data-ttu-id="6e510-124">Expanda las propiedades **Audio** y establezca el campo **Spatialization Plugin** (Complemento de la espacialización) en **Microsoft Spatial Sound** (Sonido espacial de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="6e510-124">Expanding the **Audio** properties and setting the **Spatialization Plugin** field to **Microsoft Spatial Sound**.</span></span>

![Complemento de espacialización para la plataforma HoloLens](images/unreal-spatial-audio-img-02.png)

<span data-ttu-id="6e510-126">Si va a obtener una vista previa de la aplicación en el editor de Unreal en un equipo de escritorio, deberá repetir los pasos anteriores para la plataforma **Windows**:</span><span class="sxs-lookup"><span data-stu-id="6e510-126">If you're going to be previewing your application in the Unreal editor on a desktop PC, you'll need to repeat the above steps for the **Windows** platform:</span></span>

![Complemento de espacialización para la plataforma Windows](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a><span data-ttu-id="6e510-128">Habilitación del audio espacial en la estación de trabajo</span><span class="sxs-lookup"><span data-stu-id="6e510-128">Enabling spatial audio on your workstation</span></span>
<span data-ttu-id="6e510-129">El audio espacial está deshabilitado de forma predeterminada en las versiones de escritorio de Windows.</span><span class="sxs-lookup"><span data-stu-id="6e510-129">Spatial audio is disabled by default on desktop versions of Windows.</span></span> <span data-ttu-id="6e510-130">Puede habilitarlo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6e510-130">You can enable it by:</span></span>
* <span data-ttu-id="6e510-131">Haga clic con el botón derecho en el icono de **volumen** de la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="6e510-131">Right-clicking on the **volume** icon in the task bar.</span></span> 
    + <span data-ttu-id="6e510-132">Elija **Sonido espacial > Windows Sonic para auriculares** para obtener la mejor representación de lo que escuchará en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6e510-132">Choose **Spatial sound -> Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

![Complemento de espacialización](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
><span data-ttu-id="6e510-134">Esta opción solo es necesaria si tiene previsto probar el proyecto en el editor de Unreal.</span><span class="sxs-lookup"><span data-stu-id="6e510-134">This setting is only required if you plan to test your project in the Unreal editor.</span></span>

## <a name="creating-attenuation-objects"></a><span data-ttu-id="6e510-135">Creación de objetos de atenuación</span><span class="sxs-lookup"><span data-stu-id="6e510-135">Creating Attenuation objects</span></span>
<span data-ttu-id="6e510-136">Después de instalar y configurar los complementos necesarios:</span><span class="sxs-lookup"><span data-stu-id="6e510-136">After you've installed and configured the necessary plugins:</span></span>
1. <span data-ttu-id="6e510-137">Busque un actor de **Ambient Sound** (Sonido ambiental) actor en la ventana **Place Actors** (Colocar actores) y arrástrelo a la ventana **Scene** (Escena).</span><span class="sxs-lookup"><span data-stu-id="6e510-137">Search for an **Ambient Sound** actor in the **Place Actors** window and drag it into the **Scene** window.</span></span>

![Adición de un actor de sonido ambiental](images/unreal-spatial-audio-img-07.png)

2. <span data-ttu-id="6e510-139">Convierta el actor de **Ambient Sound** (Sonido ambiental) en un elemento secundario de un elemento visual de la escena.</span><span class="sxs-lookup"><span data-stu-id="6e510-139">Make the **Ambient Sound** actor a child of a visual element in your scene.</span></span> 
    * <span data-ttu-id="6e510-140">Un actor de sonido ambiental no tiene ninguna representación visual de forma predeterminada, por lo que solo oirá un sonido de su posición en la escena.</span><span class="sxs-lookup"><span data-stu-id="6e510-140">An Ambient Sound actor doesn't have any visual representation by default, so you'll only hear a sound from its position in the scene.</span></span> <span data-ttu-id="6e510-141">Al adjuntarlo a un elemento visual, el actor se muestra y se mueve como cualquier otro recurso.</span><span class="sxs-lookup"><span data-stu-id="6e510-141">Attaching it to a visual element let's you see and move the actor like any other asset.</span></span>

3.  <span data-ttu-id="6e510-142">Haga clic con el botón derecho en **Content Browser** (Explorador de contenido) y seleccione **Create Advanced Asset -> Sounds -> Sound Attenuation** (Crear recurso avanzado -> Sonidos -> Atenuación de sonido):</span><span class="sxs-lookup"><span data-stu-id="6e510-142">Right-click on the **Content Browser** and selecting **Create Advanced Asset -> Sounds -> Sound Attenuation**:</span></span>

![Creación de un recurso de atenuación de sonido](images/unreal-spatial-audio-img-06.png)

4. <span data-ttu-id="6e510-144">Haga clic con el botón derecho en el recurso **Sound Attenuation** (Atenuación de sonido) en la ventana **Content Browser** (Explorador de contenido) y seleccione la opción **Edit** (Editar) para abrir la ventana de propiedades.</span><span class="sxs-lookup"><span data-stu-id="6e510-144">Right-click on the **Sound Attenuation** asset in the **Content Browser** window and select the **Edit** option to bring up the properties window.</span></span>
    * <span data-ttu-id="6e510-145">Cambie el valor de **Spatialization Method** (Método de espacialización) a **Binaural**.</span><span class="sxs-lookup"><span data-stu-id="6e510-145">Switch the **Spatialization Method** to **Binaural**.</span></span>

![Establecimiento del método de espacialización](images/unreal-spatial-audio-img-03.png)

5. <span data-ttu-id="6e510-147">Seleccione el actor de **Ambient Sound** (Sonido ambiental) y desplácese hacia abajo hasta la sección **Attenuation** (Atenuación) del panel **Details** (Detalles).</span><span class="sxs-lookup"><span data-stu-id="6e510-147">Select the **Ambient Sound** actor and scroll down to the **Attenuation** section in the **Details** panel.</span></span> 
    * <span data-ttu-id="6e510-148">Establezca la propiedad **Attenuation Settings** (Configuración de atenuación) en el recurso de **Sound Attenuation** (Atenuación de sonido) que creó.</span><span class="sxs-lookup"><span data-stu-id="6e510-148">Set the **Attenuation Settings** property to the **Sound Attenuation** asset you created.</span></span>

![Establecimiento de la configuración de atenuación](images/unreal-spatial-audio-img-08.png)

6. <span data-ttu-id="6e510-150">Establezca la opción de **Sound Asset** (Recurso de sonido) que desea asociar al actor de sonido ambiental mediante la actualización de la propiedad **Sound** (Sonido) de dicho actor para especificar el archivo SoundAsset que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="6e510-150">Set the **Sound Asset** you want to attach to the Ambient Sound actor by updating the **Sound** property of the Ambient Sound actor to specify the SoundAsset file to use.</span></span>

![Establecimiento del recurso de sonido](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> <span data-ttu-id="6e510-152">El archivo SoundAsset debe ser monoaural para que se pueda espacializar con el complemento de sonido espacial de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6e510-152">The SoundAsset file needs to be mono to be spatialized with the Microsoft Spatial Sound plug-in.</span></span> <span data-ttu-id="6e510-153">Para buscar las propiedades del archivo de sonido, puede mantener el puntero sobre el recurso en la ventana Content Browser (Explorador de contenido), tal como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="6e510-153">You can find the sound file properties by hovering over the asset in the Content Browser window as shown in the screenshot below.</span></span>

![Nuevo recurso de atenuación de sonido](images/unreal-spatial-audio-img-10.png)

<span data-ttu-id="6e510-155">Una vez configurado todo esto, el sonido ambiental se puede espacializar con el soporte de descarga de hardware dedicado en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6e510-155">Once all of this is configured the ambient sound can be spatialized using the dedicated hardware offload support on HoloLens 2.</span></span>

## <a name="configuring-objects-for-spatialization"></a><span data-ttu-id="6e510-156">Configuración de objetos para la espacialización</span><span class="sxs-lookup"><span data-stu-id="6e510-156">Configuring objects for spatialization</span></span>
<span data-ttu-id="6e510-157">Trabajar con audio espacial significa responsabilizarse de administrar el comportamiento del sonido en un entorno virtual.</span><span class="sxs-lookup"><span data-stu-id="6e510-157">Working with spatial audio means you're in charge of managing how sound behaves in a virtual environment.</span></span> <span data-ttu-id="6e510-158">El enfoque principal es crear objetos de sonido que parezcan más altos cuando el usuario esté cerca y más silenciosos cuando el usuario esté lejos.</span><span class="sxs-lookup"><span data-stu-id="6e510-158">Your main focus is creating sound objects that appear louder when the user is close, and quieter when the user is far away.</span></span> <span data-ttu-id="6e510-159">Esto se conoce como atenuación de sonido y hace que los sonidos se oigan como si estuvieran en una posición fija.</span><span class="sxs-lookup"><span data-stu-id="6e510-159">This is referred to as sound attenuation, making sounds appear as if they are positioned in a fixed spot.</span></span>

<span data-ttu-id="6e510-160">Todos los objetos de atenuación tienen valores modificables de:</span><span class="sxs-lookup"><span data-stu-id="6e510-160">All attenuation objects come with modifiable settings for:</span></span>
* <span data-ttu-id="6e510-161">Distancia</span><span class="sxs-lookup"><span data-stu-id="6e510-161">Distance</span></span>
* <span data-ttu-id="6e510-162">Espacialización</span><span class="sxs-lookup"><span data-stu-id="6e510-162">Spatialization</span></span>
* <span data-ttu-id="6e510-163">Absorción de aire</span><span class="sxs-lookup"><span data-stu-id="6e510-163">Air Absorption</span></span>
* <span data-ttu-id="6e510-164">Foco del agente de escucha</span><span class="sxs-lookup"><span data-stu-id="6e510-164">Listener Focus</span></span>
* <span data-ttu-id="6e510-165">Envío de reverberación</span><span class="sxs-lookup"><span data-stu-id="6e510-165">Reverb Send</span></span>
* <span data-ttu-id="6e510-166">Oclusión</span><span class="sxs-lookup"><span data-stu-id="6e510-166">Occlusion</span></span>

<span data-ttu-id="6e510-167">La [atenuación de sonido en Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) tiene detalles e información específica de la implementación en cada uno de estos temas.</span><span class="sxs-lookup"><span data-stu-id="6e510-167">[Sound attenuation in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) has details and implementation specifics on each of these topics.</span></span>


## <a name="see-also"></a><span data-ttu-id="6e510-168">Consulta también</span><span class="sxs-lookup"><span data-stu-id="6e510-168">See also</span></span>
* [<span data-ttu-id="6e510-169">Sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6e510-169">Spatial Sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [<span data-ttu-id="6e510-170">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6e510-170">Spatial Sound Design</span></span>](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [<span data-ttu-id="6e510-171">MR Spatial 220: sonido espacial</span><span class="sxs-lookup"><span data-stu-id="6e510-171">MR Spatial 220: Spatial sound</span></span>](https://docs.microsoft.com/windows/mixed-reality/holograms-220)