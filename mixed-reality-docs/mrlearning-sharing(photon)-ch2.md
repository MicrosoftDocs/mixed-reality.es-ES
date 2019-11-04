---
title: 'Tutoriales de funcionalidades para varios usuarios: 2. Preparar Unity para el desarrollo'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 5d8194e9a51bdb0ce32f345b4adfbfaf408c5396
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438383"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="074e9-105">2. obtener Unity listo para el desarrollo</span><span class="sxs-lookup"><span data-stu-id="074e9-105">2. Getting Unity ready for development</span></span> 


<span data-ttu-id="074e9-106">En este tutorial, obtendrá información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación del kit de herramientas de realidad mixta, la configuración de las opciones de compilación y la preparación de la escena.</span><span class="sxs-lookup"><span data-stu-id="074e9-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="074e9-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="074e9-107">Objectives</span></span>

- <span data-ttu-id="074e9-108">Configuración de Unity para el desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="074e9-108">Configure Unity for application development</span></span>

- <span data-ttu-id="074e9-109">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="074e9-109">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="074e9-110">Preparación de la escena del proyecto</span><span class="sxs-lookup"><span data-stu-id="074e9-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="074e9-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="074e9-111">Instructions</span></span>

1. <span data-ttu-id="074e9-112">Descargue y guarde el paquete de Unity del kit de herramientas de realidad mixta; para ello, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="074e9-112">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="074e9-113">En Unity, haga clic en el menú activos y seleccione Importar paquete y, a continuación, haga clic en paquete personalizado.</span><span class="sxs-lookup"><span data-stu-id="074e9-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="074e9-115">Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="074e9-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="074e9-116">Una vez que aparezca la ventana emergente importar en Unity, haga clic en el botón importar para empezar a importar el MRTK.</span><span class="sxs-lookup"><span data-stu-id="074e9-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="074e9-117">Esto puede tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="074e9-117">This may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="074e9-119">Nota: el paquete descargado se encuentra en la carpeta local, donde se guardó el archivo.</span><span class="sxs-lookup"><span data-stu-id="074e9-119">Note: The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="074e9-120">La imagen anterior no indica dónde encontrará el paquete.</span><span class="sxs-lookup"><span data-stu-id="074e9-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="074e9-121">Cree una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="074e9-121">Create a new scene.</span></span> <span data-ttu-id="074e9-122">Para ello, haga clic en archivo y seleccione nueva escena ".</span><span class="sxs-lookup"><span data-stu-id="074e9-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="074e9-123">Guárdelo como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="074e9-123">Save it as HLSharedProjectMain.</span></span>

> <span data-ttu-id="074e9-124">Nota: es posible que reciba un elemento emergente que tenga un aspecto similar a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="074e9-124">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="074e9-125">Por ahora, haga clic en no.</span><span class="sxs-lookup"><span data-stu-id="074e9-125">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="074e9-127">En el kit de herramientas de realidad mixta, haga clic en Agregar a escena y configurar.</span><span class="sxs-lookup"><span data-stu-id="074e9-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="074e9-129">Una vez que haya finalizado, aparecerá un nuevo archivo de configuración que le dará la opción de personalizar el perfil.</span><span class="sxs-lookup"><span data-stu-id="074e9-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="074e9-130">Haga clic en copiar y personalizar.</span><span class="sxs-lookup"><span data-stu-id="074e9-130">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="074e9-134">Desplácese hacia abajo y desactive habilitar el sistema de diagnósticos si desea ocultar la ventana de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="074e9-134">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="074e9-135">Se recomienda mantener la ventana de diagnósticos habilitada durante el desarrollo de la aplicación para supervisar el rendimiento y, a continuación, deshabilitarla durante las demostraciones de producción o de aplicación.</span><span class="sxs-lookup"><span data-stu-id="074e9-135">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="074e9-137">Para abrir la configuración de compilación, presione Control + Mayús + B o vaya a archivo-> configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="074e9-137">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="074e9-138">Tenga en cuenta que el programa está establecido actualmente en la plataforma independiente PC, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="074e9-138">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="074e9-139">Para el desarrollo de HoloLens 2, establezca la plataforma que se va a Plataforma universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="074e9-139">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="074e9-140">Selecciónelo y haga clic en switch Platform (cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="074e9-140">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="074e9-142">Una vez que haya finalizado, haga clic en el cuadro denominado agregar escenas abiertas.</span><span class="sxs-lookup"><span data-stu-id="074e9-142">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="074e9-143">Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de realidad virtual (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="074e9-143">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="074e9-144">Asegúrese también de que la casilla situada junto a Scenes/HLSharedProjectMain también está activada, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="074e9-144">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="074e9-146">En la sección configuración de publicación del panel Inspector, desplácese hacia abajo hasta capacidades y asegúrese de que las siguientes casillas están marcadas como:</span><span class="sxs-lookup"><span data-stu-id="074e9-146">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="074e9-148">Importe el paquete personalizado denominado SharingAssetCollection, que se puede descargar [aquí.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span><span class="sxs-lookup"><span data-stu-id="074e9-148">Import the custom package called SharingAssetCollection, which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="074e9-150">En el panel Proyecto, vaya a la carpeta Prefabs.</span><span class="sxs-lookup"><span data-stu-id="074e9-150">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="074e9-151">En los pasos siguientes, se implementarán algunas Prefabs en la escena.</span><span class="sxs-lookup"><span data-stu-id="074e9-151">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="074e9-152">En la carpeta Prefabs, haga clic y arrastre la ventana de depuración recurso prefabricado a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="074e9-152">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="074e9-153">Una vez finalizado, guarde el proyecto haciendo clic en archivo, luego en guardar o presione Control + S.</span><span class="sxs-lookup"><span data-stu-id="074e9-153">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="074e9-155">Nota: es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="074e9-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="074e9-156">Haga clic en importar TMP Essentials según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="074e9-156">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="074e9-157">Si aparece esta ventana emergente, es posible que tenga que eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.</span><span class="sxs-lookup"><span data-stu-id="074e9-157">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="074e9-159">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="074e9-159">Congratulations</span></span>

<span data-ttu-id="074e9-160">El proyecto de Unity ya está listo para Photon.</span><span class="sxs-lookup"><span data-stu-id="074e9-160">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="074e9-161">En los tutoriales venideros, se basará en esta escena y nuestro proyecto de Unity en una experiencia completa compartida.</span><span class="sxs-lookup"><span data-stu-id="074e9-161">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="074e9-162">[Siguiente tutorial: 3. conectar varios usuarios](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="074e9-162">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

