---
title: 'Tutoriales sobre las funcionalidades multiusuario: 2. Preparación de Unity para desarrollo'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031239"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="f2c93-105">2. Preparación de Unity para el desarrollo</span><span class="sxs-lookup"><span data-stu-id="f2c93-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="f2c93-106">En este tutorial, aprenderás a preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación de Mixed Reality Toolkit, la configuración de las opciones de compilación y la preparación de la escena.</span><span class="sxs-lookup"><span data-stu-id="f2c93-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="f2c93-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f2c93-107">Objectives</span></span>

* <span data-ttu-id="f2c93-108">Configurar Unity para el desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="f2c93-108">Configure Unity for application development</span></span>
* <span data-ttu-id="f2c93-109">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="f2c93-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="f2c93-110">Preparar la escena del proyecto</span><span class="sxs-lookup"><span data-stu-id="f2c93-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="f2c93-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="f2c93-111">Instructions</span></span>

1. <span data-ttu-id="f2c93-112">Haz clic [aquí](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) para descargar el paquete básico de Unity de Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="f2c93-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="f2c93-113">En Unity, haz clic en el menú Assets (Recursos) y selecciona Import Package (Importar paquete). A continuación, haz clic en Custom Package (Paquete personalizado).</span><span class="sxs-lookup"><span data-stu-id="f2c93-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="f2c93-115">Selecciona el paquete de Unity que acabas de descargar del vínculo proporcionado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="f2c93-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="f2c93-116">Cuando aparezca la ventana emergente de importación en Unity, haz clic en el botón Importar para empezar a importar el MRTK.</span><span class="sxs-lookup"><span data-stu-id="f2c93-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="f2c93-117">Esto puede tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="f2c93-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f2c93-119">El paquete descargado está en la carpeta local, donde has guardado el archivo.</span><span class="sxs-lookup"><span data-stu-id="f2c93-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="f2c93-120">La imagen anterior no indica dónde encontrarás el paquete.</span><span class="sxs-lookup"><span data-stu-id="f2c93-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="f2c93-121">Una vez importado el paquete, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK).</span><span class="sxs-lookup"><span data-stu-id="f2c93-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="f2c93-122">Si no aparece, se puede abrir seleccionando la opción Mixed Reality Toolkit > Utilities > Configure Unity Project (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) en el menú de Unity.</span><span class="sxs-lookup"><span data-stu-id="f2c93-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="f2c93-123">En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expande la sección Modify Configurations (Modificar configuraciones), desactiva la casilla Enable MSBuild for Unity (Habilitar MSBuild para Unity), asegúrate de que todas las demás opciones están seleccionadas y haz clic en el botón Apply (Aplicar) para aplicar la configuración.</span><span class="sxs-lookup"><span data-stu-id="f2c93-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="f2c93-125">Es posible que MSBuild para Unity no admita todos los SDK que vas a usar y puede ser difícil de deshabilitar una vez que se haya habilitado.</span><span class="sxs-lookup"><span data-stu-id="f2c93-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="f2c93-126">Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.</span><span class="sxs-lookup"><span data-stu-id="f2c93-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="f2c93-127">Crea una escena nueva.</span><span class="sxs-lookup"><span data-stu-id="f2c93-127">Create a new scene.</span></span> <span data-ttu-id="f2c93-128">Para hacerlo, haz clic en File (Archivo) y selecciona New Scene (Nueva escena).</span><span class="sxs-lookup"><span data-stu-id="f2c93-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="f2c93-129">Guárdala como HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="f2c93-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="f2c93-130">En Mixed Reality Toolkit, haz clic en Add to Scene (Agregar a escena) y Configure (Configurar).</span><span class="sxs-lookup"><span data-stu-id="f2c93-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="f2c93-132">Al acabar, selecciona Mixed-Reality Toolkit (MRTK) en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="f2c93-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="f2c93-133">En el panel del inspector, cambia el perfil de configuración de MRTK a DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="f2c93-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="f2c93-135">Selecciona Mixed-Reality Toolkit (MRTK) en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="f2c93-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="f2c93-136">En el panel del inspector, busca Mixed Reality Toolkit Script (Script de Mixed Reality Toolkit) y selecciona el botón "Copy & Customize" (Copiar y personalizar) como se muestra en la ilustración siguiente.</span><span class="sxs-lookup"><span data-stu-id="f2c93-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="f2c93-137">Después de esto, aparecerá un elemento emergente. Selecciona la opción Clone (Clonar) en el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="f2c93-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="f2c93-140">Desplázate hacia abajo y desactiva Enable Diagnostics system (Habilitar el sistema de diagnóstico) si quieres ocultar la ventana de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="f2c93-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="f2c93-141">Es recomendable mantener la ventana de diagnóstico habilitada durante el desarrollo de la aplicación para supervisar el rendimiento y, a continuación, deshabilitarla durante las demostraciones de producción o de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f2c93-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="f2c93-143">Para abrir la configuración de compilación, presiona Control + Mayús + B o ve a File -> Build Settings (Archivo -> Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="f2c93-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="f2c93-144">Ten en cuenta, actualmente, que el programa está definido en la plataforma independiente para PC, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="f2c93-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="f2c93-145">Para el desarrollo de HoloLens 2, define la Plataforma universal de Windows como plataforma.</span><span class="sxs-lookup"><span data-stu-id="f2c93-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="f2c93-146">Selecciónala y haz clic en Switch Platform (Cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="f2c93-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="f2c93-148">Al finalizar, haz clic en el cuadro denominado Add Open Scenes (Agregar escenas abiertas).</span><span class="sxs-lookup"><span data-stu-id="f2c93-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="f2c93-149">Ahora, ve al panel Inspector y asegúrate de que esté activada la casilla situada a la derecha de Virtual Reality Supported (Realidad virtual compatible), como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="f2c93-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="f2c93-150">Asegúrate también de que la casilla situada junto a Scenes (Escenas)/HLSharedProjectMain también esté activada, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="f2c93-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="f2c93-152">En la sección Publishing Settings (Configuración de publicación) del panel Inspector, desplázate hacia abajo hasta Capabilities (Funcionalidades) y asegúrate de que las siguientes casillas estén marcadas:</span><span class="sxs-lookup"><span data-stu-id="f2c93-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="f2c93-154">Importa los paquetes personalizados que se muestran:</span><span class="sxs-lookup"><span data-stu-id="f2c93-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="f2c93-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (versión 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="f2c93-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="f2c93-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f2c93-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="f2c93-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f2c93-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="f2c93-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="f2c93-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="f2c93-159">Para obtener un recordatorio sobre cómo configurar un proyecto de Unity para Azure Spatial Anchors, puedes consultar el tutorial [Introducción a Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1), que forma parte de la serie de tutoriales de [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1).</span><span class="sxs-lookup"><span data-stu-id="f2c93-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="f2c93-160">En el panel Proyecto, ve a la carpeta Prefabs.</span><span class="sxs-lookup"><span data-stu-id="f2c93-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="f2c93-161">En los pasos siguientes, se implementarán algunos objetos prefabricados a la escena.</span><span class="sxs-lookup"><span data-stu-id="f2c93-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="f2c93-162">En la carpeta Prefabs, haz clic y arrastra el objeto prefabricado DebugWindow a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="f2c93-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="f2c93-163">Al acabar, guarda el proyecto. Para hacerlo, haz clic en File (Archivo) y Save (Guardar) o presiona Control+S.</span><span class="sxs-lookup"><span data-stu-id="f2c93-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="f2c93-165">Puede que observes que aparece una ventana emergente al hacer clic en el objeto prefabricado, que te preguntará acerca de TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="f2c93-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="f2c93-166">Haz clic en Import TMP Essentials (Importar TMP Essentials), ya que se necesita.</span><span class="sxs-lookup"><span data-stu-id="f2c93-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="f2c93-167">Si aparece esta ventana emergente, es posible que tengas que eliminar el objeto prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.</span><span class="sxs-lookup"><span data-stu-id="f2c93-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="f2c93-169">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="f2c93-169">Congratulations</span></span>

<span data-ttu-id="f2c93-170">El proyecto de Unity ya está listo para Photon.</span><span class="sxs-lookup"><span data-stu-id="f2c93-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="f2c93-171">En los próximos tutoriales, nos basaremos en esta escena y nuestro proyecto de Unity para lograr una experiencia completa compartida.</span><span class="sxs-lookup"><span data-stu-id="f2c93-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="f2c93-172">[Tutorial siguiente: 3. Conexión de varios usuarios](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="f2c93-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
