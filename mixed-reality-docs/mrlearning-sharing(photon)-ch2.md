---
title: 'Tutoriales de funcionalidades para varios usuarios: 2. Preparar Unity para el desarrollo'
description: Complete este curso para aprender a implementar experiencias compartidas multiusuario en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 2bcec7e70949186c6e711120c36ee8649c006ec7
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553851"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="db806-105">2. obtener Unity listo para el desarrollo</span><span class="sxs-lookup"><span data-stu-id="db806-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="db806-106">En este tutorial, obtendrá información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación del kit de herramientas de realidad mixta, la configuración de las opciones de compilación y la preparación de la escena.</span><span class="sxs-lookup"><span data-stu-id="db806-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="db806-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="db806-107">Objectives</span></span>

* <span data-ttu-id="db806-108">Configuración de Unity para el desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="db806-108">Configure Unity for application development</span></span>
* <span data-ttu-id="db806-109">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="db806-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="db806-110">Preparación de la escena del proyecto</span><span class="sxs-lookup"><span data-stu-id="db806-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="db806-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="db806-111">Instructions</span></span>

1. <span data-ttu-id="db806-112">Para descargar y guardar el paquete Mixed Reality Toolkit Foundation Unity, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="db806-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="db806-113">En Unity, haga clic en el menú activos y seleccione Importar paquete y, a continuación, haga clic en paquete personalizado.</span><span class="sxs-lookup"><span data-stu-id="db806-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="db806-115">Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="db806-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="db806-116">Una vez que aparezca la ventana emergente importar en Unity, haga clic en el botón importar para empezar a importar el MRTK.</span><span class="sxs-lookup"><span data-stu-id="db806-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="db806-117">Esto puede tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="db806-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="db806-119">El paquete descargado se encuentra en la carpeta local, donde se guardó el archivo.</span><span class="sxs-lookup"><span data-stu-id="db806-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="db806-120">La imagen anterior no indica dónde encontrará el paquete.</span><span class="sxs-lookup"><span data-stu-id="db806-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="db806-121">Una vez importado el paquete, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="db806-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="db806-122">Si no es así, ábralo seleccionando el kit de herramientas de realidad mixta > Utilidades > configurar el proyecto de Unity en el menú de Unity.</span><span class="sxs-lookup"><span data-stu-id="db806-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="db806-123">En la ventana Configurator del proyecto de MRTK, expanda la sección modificar configuraciones, desactive la casilla habilitar MSBuild para Unity, asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón aplicar para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="db806-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="db806-125">Es posible que MSBuild para Unity no admita todos los SDK que vas a usar y puede ser difícil de deshabilitar una vez que se haya habilitado.</span><span class="sxs-lookup"><span data-stu-id="db806-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="db806-126">Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="db806-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="db806-127">Cree una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="db806-127">Create a new scene.</span></span> <span data-ttu-id="db806-128">Para ello, haga clic en archivo y seleccione nueva escena ".</span><span class="sxs-lookup"><span data-stu-id="db806-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="db806-129">Guárdelo como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="db806-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="db806-130">En el kit de herramientas de realidad mixta, haga clic en Agregar a escena y configurar.</span><span class="sxs-lookup"><span data-stu-id="db806-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="db806-132">Una vez que haya finalizado, seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="db806-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="db806-133">En el panel Inspector, cambie el perfil de configuración de MRTK a DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="db806-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="db806-135">Seleccione el kit de herramientas de realidad mixta (MRTK) de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="db806-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="db806-136">En el panel Inspector, busque el script Mixed Reality Toolkit y presione el botón "copiar & personalizar" como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="db806-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="db806-137">Después de esto, aparecerá un pop en el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="db806-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="db806-140">Desplácese hacia abajo y desactive habilitar el sistema de diagnósticos si desea ocultar la ventana de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="db806-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="db806-141">Se recomienda mantener la ventana de diagnósticos habilitada durante el desarrollo de la aplicación para supervisar el rendimiento y, a continuación, deshabilitarla durante las demostraciones de producción o de aplicación.</span><span class="sxs-lookup"><span data-stu-id="db806-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="db806-143">Para abrir la configuración de compilación, presione Control + Mayús + B o vaya a archivo-> configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="db806-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="db806-144">Tenga en cuenta que el programa está establecido actualmente en la plataforma independiente PC, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="db806-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="db806-145">Para el desarrollo de HoloLens 2, establezca la plataforma que se va a Plataforma universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="db806-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="db806-146">Selecciónelo y haga clic en switch Platform (cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="db806-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="db806-148">Una vez que haya finalizado, haga clic en el cuadro denominado agregar escenas abiertas.</span><span class="sxs-lookup"><span data-stu-id="db806-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="db806-149">Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de realidad virtual (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="db806-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="db806-150">Asegúrese también de que la casilla situada junto a Scenes/HLSharedProjectMain también está activada, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="db806-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="db806-152">En la sección configuración de publicación del panel Inspector, desplácese hacia abajo hasta capacidades y asegúrese de que las siguientes casillas están marcadas como:</span><span class="sxs-lookup"><span data-stu-id="db806-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="db806-154">Importe los paquetes personalizados enumerados:</span><span class="sxs-lookup"><span data-stu-id="db806-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="db806-155">[AzureSpatialAnchors. unitypackage Tools](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="db806-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="db806-156">MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.3.0.2. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="db806-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="db806-157">MRTK. HoloLens2. Unity. tutoriales. assets. AzureSpatialAnchors. 2.3.0.0. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="db806-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="db806-158">MRTK. HoloLens2. Unity. tutoriales. assets. MultiUserCapabilities. 2.1.0.1. unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="db806-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="db806-159">Para obtener un recordatorio sobre cómo configurar un proyecto de Unity para los anclajes espaciales de Azure, puede consultar el tutorial Introducción a los [anclajes espaciales de Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) , que forma parte de la serie de tutoriales de los [delimitadores espaciales de Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) .</span><span class="sxs-lookup"><span data-stu-id="db806-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="db806-160">En el panel Proyecto, vaya a la carpeta Prefabs.</span><span class="sxs-lookup"><span data-stu-id="db806-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="db806-161">En los pasos siguientes, se implementarán algunas Prefabs en la escena.</span><span class="sxs-lookup"><span data-stu-id="db806-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="db806-162">En la carpeta Prefabs, haga clic y arrastre la ventana de depuración recurso prefabricado a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="db806-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="db806-163">Una vez finalizado, guarde el proyecto haciendo clic en archivo, luego en guardar o presione Control + S.</span><span class="sxs-lookup"><span data-stu-id="db806-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="db806-165">Es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="db806-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="db806-166">Haga clic en importar TMP Essentials según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="db806-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="db806-167">Si aparece esta ventana emergente, es posible que tenga que eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.</span><span class="sxs-lookup"><span data-stu-id="db806-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="db806-169">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="db806-169">Congratulations</span></span>

<span data-ttu-id="db806-170">El proyecto de Unity ya está listo para Photon.</span><span class="sxs-lookup"><span data-stu-id="db806-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="db806-171">En los tutoriales venideros, se basará en esta escena y nuestro proyecto de Unity en una experiencia completa compartida.</span><span class="sxs-lookup"><span data-stu-id="db806-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="db806-172">[Siguiente tutorial: 3. conectar varios usuarios](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="db806-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
