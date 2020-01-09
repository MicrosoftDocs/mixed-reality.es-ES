---
title: 'Tutoriales de funcionalidades para varios usuarios: 2. Preparar Unity para el desarrollo'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 6840bcc583fe3e42dcaa6f42e71098f4dbe76f4c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334314"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="07927-105">2. obtener Unity listo para el desarrollo</span><span class="sxs-lookup"><span data-stu-id="07927-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="07927-106">En este tutorial, obtendrá información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación del kit de herramientas de realidad mixta, la configuración de las opciones de compilación y la preparación de la escena.</span><span class="sxs-lookup"><span data-stu-id="07927-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="07927-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="07927-107">Objectives</span></span>

* <span data-ttu-id="07927-108">Configuración de Unity para el desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="07927-108">Configure Unity for application development</span></span>
* <span data-ttu-id="07927-109">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="07927-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="07927-110">Preparación de la escena del proyecto</span><span class="sxs-lookup"><span data-stu-id="07927-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="07927-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="07927-111">Instructions</span></span>

1. <span data-ttu-id="07927-112">Para descargar y guardar el paquete Mixed Reality Toolkit Foundation Unity, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="07927-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="07927-113">En Unity, haga clic en el menú activos y seleccione Importar paquete y, a continuación, haga clic en paquete personalizado.</span><span class="sxs-lookup"><span data-stu-id="07927-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="07927-115">Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="07927-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="07927-116">Una vez que aparezca la ventana emergente importar en Unity, haga clic en el botón importar para empezar a importar el MRTK.</span><span class="sxs-lookup"><span data-stu-id="07927-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="07927-117">Este proceso podría tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="07927-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="07927-119">El paquete descargado se encuentra en la carpeta local, donde se guardó el archivo.</span><span class="sxs-lookup"><span data-stu-id="07927-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="07927-120">La imagen anterior no indica dónde encontrará el paquete.</span><span class="sxs-lookup"><span data-stu-id="07927-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="07927-121">Cree una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="07927-121">Create a new scene.</span></span> <span data-ttu-id="07927-122">Para ello, haga clic en archivo y seleccione nueva escena ".</span><span class="sxs-lookup"><span data-stu-id="07927-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="07927-123">Guárdelo como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="07927-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="07927-124">Es posible que reciba un mensaje emergente similar a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="07927-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="07927-125">Por ahora, haga clic en no.</span><span class="sxs-lookup"><span data-stu-id="07927-125">For now, click No.</span></span>
    <span data-ttu-id="07927-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="07927-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="07927-127">En el kit de herramientas de realidad mixta, haga clic en Agregar a escena y configurar.</span><span class="sxs-lookup"><span data-stu-id="07927-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="07927-129">Una vez que haya finalizado, aparecerá un nuevo archivo de configuración que le dará la opción de personalizar el perfil.</span><span class="sxs-lookup"><span data-stu-id="07927-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="07927-131">Seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="07927-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="07927-132">En el panel Inspector, busque el script Mixed Reality Toolkit y presione el botón "copiar & personalizar" como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="07927-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="07927-133">Después de esto, aparecerá un pop en el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="07927-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="07927-136">Desplácese hacia abajo y desactive habilitar el sistema de diagnósticos si desea ocultar la ventana de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="07927-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="07927-137">Se recomienda mantener la ventana de diagnósticos habilitada durante el desarrollo de la aplicación para supervisar el rendimiento y, a continuación, deshabilitarla durante las demostraciones de producción o de aplicación.</span><span class="sxs-lookup"><span data-stu-id="07927-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="07927-139">Para abrir la configuración de compilación, presione Control + Mayús + B o vaya a archivo-> configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="07927-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="07927-140">Tenga en cuenta que el programa está establecido actualmente en la plataforma independiente PC, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="07927-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="07927-141">Para el desarrollo de HoloLens 2, establezca la plataforma que se va a Plataforma universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="07927-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="07927-142">Selecciónelo y haga clic en switch Platform (cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="07927-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="07927-144">Una vez que haya finalizado, haga clic en el cuadro denominado agregar escenas abiertas.</span><span class="sxs-lookup"><span data-stu-id="07927-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="07927-145">Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de realidad virtual (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="07927-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="07927-146">Asegúrese también de que la casilla situada junto a Scenes/HLSharedProjectMain también está activada, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="07927-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="07927-148">En la sección configuración de publicación del panel Inspector, desplácese hacia abajo hasta capacidades y asegúrese de que las siguientes casillas están marcadas como:</span><span class="sxs-lookup"><span data-stu-id="07927-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="07927-150">Importe los paquetes personalizados enumerados:</span><span class="sxs-lookup"><span data-stu-id="07927-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="07927-151">a.</span><span class="sxs-lookup"><span data-stu-id="07927-151">a.</span></span> [<span data-ttu-id="07927-152">Unity. HoloLens2. GettingStarted. tutoriales. Asset. 2.1.0.0. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="07927-152">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    <span data-ttu-id="07927-153">b.</span><span class="sxs-lookup"><span data-stu-id="07927-153">b.</span></span> [<span data-ttu-id="07927-154">Unity. HoloLens2. MultiUserCapabilities. tutoriales. Asset. 2.1.0.0. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="07927-154">Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    ><span data-ttu-id="07927-155">Si ha completado los [tutoriales de introducción](mrlearning-base-ch1.md), es posible que todavía tenga el paquete de Unity denominado _Unity. HoloLens2. gettingstarted. tutoriales. Asset. 2.1.0.0. unitypackage Tools_ almacenado en el equipo.</span><span class="sxs-lookup"><span data-stu-id="07927-155">If you have completed the [Getting started tutorials](mrlearning-base-ch1.md), you might still have the Unity package named _Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage_ stored on your computer.</span></span> <span data-ttu-id="07927-156">Si es así, puede omitir la descarga del recurso que se muestra en el paso a anterior.</span><span class="sxs-lookup"><span data-stu-id="07927-156">If so, you can skip downloading the asset listed in step a above.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="07927-158">En el panel Proyecto, vaya a la carpeta Prefabs.</span><span class="sxs-lookup"><span data-stu-id="07927-158">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="07927-159">En los pasos siguientes, se implementarán algunas Prefabs en la escena.</span><span class="sxs-lookup"><span data-stu-id="07927-159">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="07927-160">En la carpeta Prefabs, haga clic y arrastre la ventana de depuración recurso prefabricado a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="07927-160">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="07927-161">Una vez finalizado, guarde el proyecto haciendo clic en archivo, luego en guardar o presione Control + S.</span><span class="sxs-lookup"><span data-stu-id="07927-161">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="07927-163">Es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="07927-163">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="07927-164">Haga clic en importar TMP Essentials según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="07927-164">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="07927-165">Si aparece esta ventana emergente, es posible que tenga que eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.</span><span class="sxs-lookup"><span data-stu-id="07927-165">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="07927-167">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="07927-167">Congratulations</span></span>

<span data-ttu-id="07927-168">El proyecto de Unity ya está listo para Photon.</span><span class="sxs-lookup"><span data-stu-id="07927-168">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="07927-169">En los tutoriales venideros, se basará en esta escena y nuestro proyecto de Unity en una experiencia completa compartida.</span><span class="sxs-lookup"><span data-stu-id="07927-169">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="07927-170">[Siguiente tutorial: 3. conectar varios usuarios](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="07927-170">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
