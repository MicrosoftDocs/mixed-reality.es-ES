---
title: Uso compartido de módulo para HoloLens 2 de aprendizaje de MR
description: Realice este curso para aprender a implementar varios usuarios experiencias compartidas dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327719"
---
# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="15534-104">**Cómo prepararse para el desarrollo de Unity**</span><span class="sxs-lookup"><span data-stu-id="15534-104">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="15534-105">En esta lección, se obtendrá información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, como importar el Kit de herramientas de realidad mixta, configuración de generación y preparación de la escena.</span><span class="sxs-lookup"><span data-stu-id="15534-105">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="15534-106">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="15534-106">Objectives:</span></span>

- <span data-ttu-id="15534-107">Configuración de Unity para desarrollo de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="15534-107">Configure Unity for app development</span></span>

- <span data-ttu-id="15534-108">Importación de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="15534-108">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="15534-109">Preparación de la escena de proyecto</span><span class="sxs-lookup"><span data-stu-id="15534-109">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="15534-110">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="15534-110">Instructions</span></span>

1. <span data-ttu-id="15534-111">Descargue y guarde el paquete de unity del Kit de herramientas de realidad mixta haciendo [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="15534-111">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span></span>
2. <span data-ttu-id="15534-112">En Unity, haga clic en el menú de recursos y seleccione "Importar paquete" y luego haga clic en "Paquete personalizado".</span><span class="sxs-lookup"><span data-stu-id="15534-112">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="15534-114">Seleccione el paquete de Unity que acaba de descargar desde el vínculo indicado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="15534-114">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="15534-115">Una vez que aparece la ventana emergente de importación en Unity, haga clic en el botón Importar para comenzar a importar.</span><span class="sxs-lookup"><span data-stu-id="15534-115">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="15534-116">Importar el MRTK puede tardar varios minutos.</span><span class="sxs-lookup"><span data-stu-id="15534-116">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="15534-118">Nota: El paquete descargado estará en la carpeta local donde ha guardado el archivo.</span><span class="sxs-lookup"><span data-stu-id="15534-118">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="15534-119">La imagen anterior no describe donde encontrará el paquete.</span><span class="sxs-lookup"><span data-stu-id="15534-119">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="15534-120">Cree una nueva escena (Esto se puede realizar haciendo clic en "file" y seleccione "nueva escena").</span><span class="sxs-lookup"><span data-stu-id="15534-120">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="15534-121">Guarde la escena como "HLSharedProjectMain."</span><span class="sxs-lookup"><span data-stu-id="15534-121">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="15534-122">Nota: puede recibir un mensaje emergente que tiene un aspecto similar a la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="15534-122">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="15534-123">Por ahora, simplemente haga clic en "no".</span><span class="sxs-lookup"><span data-stu-id="15534-123">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="15534-125">En "Mixed Reality Toolkit", haga clic en "Agregar a la escena y configurar".</span><span class="sxs-lookup"><span data-stu-id="15534-125">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="15534-127">Una vez completado, un nuevo archivo de configuración aparecerá, lo que le ofrece la opción de personalizar el perfil.</span><span class="sxs-lookup"><span data-stu-id="15534-127">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="15534-128">Haga clic en "copiar y personalizar".</span><span class="sxs-lookup"><span data-stu-id="15534-128">Click "copy and customize."</span></span>

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. <span data-ttu-id="15534-130">Desplácese hacia abajo y desactive la opción "Habilitar sistema de diagnóstico" Si desea ocultar la ventana de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="15534-130">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="15534-131">Se recomienda mantener la ventana diagnóstico habilitado durante el desarrollo de aplicaciones para supervisar el rendimiento y, si lo deshabilitan en las demostraciones de producción o la aplicación.</span><span class="sxs-lookup"><span data-stu-id="15534-131">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span>

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. <span data-ttu-id="15534-133">Abra la configuración de compilación, presione control + MAYÚS + B o vaya a archivo > configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="15534-133">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="15534-134">Tenga en cuenta que el programa está establecido actualmente en la plataforma "PC, Mac y Linux independiente".</span><span class="sxs-lookup"><span data-stu-id="15534-134">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="15534-135">Para el desarrollo de HoloLens 2, establezca la plataforma como "Plataforma Universal de Windows".</span><span class="sxs-lookup"><span data-stu-id="15534-135">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="15534-136">Selecciónelo y haga clic en "Cambiar plataforma".</span><span class="sxs-lookup"><span data-stu-id="15534-136">Select it and click "switch platform."</span></span>

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. <span data-ttu-id="15534-138">Una vez que haya terminado, haga clic en el cuadro que dice "Agregar escenas abiertos".</span><span class="sxs-lookup"><span data-stu-id="15534-138">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="15534-139">Ahora, vaya al panel de inspector y asegúrese de que la casilla situada a la derecha de "la realidad virtual admitida" (como se muestra en la imagen siguiente) está activada.</span><span class="sxs-lookup"><span data-stu-id="15534-139">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="15534-140">También asegúrese de que también se activa la casilla de verificación situada junto a "escenas/HLSharedProjectMain", tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="15534-140">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. <span data-ttu-id="15534-142">En la "configuración de publicación" sección en el panel inspector, desplácese a "Capacidades" y asegúrese de que se marcan las siguientes casillas:</span><span class="sxs-lookup"><span data-stu-id="15534-142">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>
    - <span data-ttu-id="15534-143">cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="15534-143">internet client</span></span>
       
       - <span data-ttu-id="15534-144">servidor de cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="15534-144">internet client server</span></span>
       
       - <span data-ttu-id="15534-145">servidor de cliente de red privada</span><span class="sxs-lookup"><span data-stu-id="15534-145">private network client server</span></span>
   
       - <span data-ttu-id="15534-146">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="15534-146">camera/webcam</span></span>

       - <span data-ttu-id="15534-147">Micrófono</span><span class="sxs-lookup"><span data-stu-id="15534-147">microphone</span></span>
   
   11. <span data-ttu-id="15534-148">Importe el paquete personalizado denominado "Lesson2", que puede descargarse aquí.</span><span class="sxs-lookup"><span data-stu-id="15534-148">Import the custom package called "Lesson2" which can be downloaded here.</span></span> <span data-ttu-id="15534-149">TODO: Proporcione el vínculo al paquete de recursos.</span><span class="sxs-lookup"><span data-stu-id="15534-149">TODO: Provide link to asset pack.</span></span>
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. <span data-ttu-id="15534-151">Ahora, en el panel de proyecto, vaya a la carpeta "prefabricados", puesto que en los pasos siguientes, va a implementar unos prefabricados en la escena.</span><span class="sxs-lookup"><span data-stu-id="15534-151">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="15534-152">En la carpeta "prefabricados", haga clic y arrastre el prefabricado verá, "DebugWindow" en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="15534-152">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="15534-153">Una vez terminado, guarde el proyecto (haga clic en archivo, a continuación, guardar, o presione CTRL + S)</span><span class="sxs-lookup"><span data-stu-id="15534-153">Once finished, save the project (click file, then save, or press control+S)</span></span>
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > <span data-ttu-id="15534-155">Nota: Puede que observe un elemento emergente aparece al hacer clic en el prefabricado verá, que le pide sobre Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="15534-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="15534-156">Haga clic en "Importar TMP Essentials" como será necesaria.</span><span class="sxs-lookup"><span data-stu-id="15534-156">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="15534-157">Si este elemento emergente aparece, es posible que deba eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.</span><span class="sxs-lookup"><span data-stu-id="15534-157">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="15534-159">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="15534-159">Congratulations</span></span>

<span data-ttu-id="15534-160">Ahora está listo para Photon el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="15534-160">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="15534-161">En las próximas lecciones, creamos esta escena y nuestro proyecto de Unity hacia una experiencia completa compartida.</span><span class="sxs-lookup"><span data-stu-id="15534-161">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="15534-162">[Siguiente lección: Sharing(Photon) lección 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="15534-162">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

