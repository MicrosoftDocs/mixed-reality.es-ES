---
title: Módulo de ASA de aprendizaje MR Azure delimitador espacial en HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327292"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="c096f-104">Photon (corregirme si estoy equivocado)</span><span class="sxs-lookup"><span data-stu-id="c096f-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="c096f-105">En esta lección,</span><span class="sxs-lookup"><span data-stu-id="c096f-105">In this lesson,</span></span> 

<span data-ttu-id="c096f-106">Objetivos:</span><span class="sxs-lookup"><span data-stu-id="c096f-106">Objectives:</span></span>

* <span data-ttu-id="c096f-107">Obtenga información sobre cómo ___</span><span class="sxs-lookup"><span data-stu-id="c096f-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="c096f-108">Obtenga información sobre cómo ___</span><span class="sxs-lookup"><span data-stu-id="c096f-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="c096f-109">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="c096f-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="c096f-110">Configurar Photon</span><span class="sxs-lookup"><span data-stu-id="c096f-110">Setting Up Photon</span></span>

1. <span data-ttu-id="c096f-111">Configurar un [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) cuenta.</span><span class="sxs-lookup"><span data-stu-id="c096f-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="c096f-112">Esto constará de imputar su correo electrónico y realizar algunos pasos de comprobación.</span><span class="sxs-lookup"><span data-stu-id="c096f-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="c096f-114">Una vez que se registre, haga clic en el SDK.</span><span class="sxs-lookup"><span data-stu-id="c096f-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="c096f-115">Una vez que esté en esa página, haga clic en "servidor" y asegurarse de que dice, "alojado en sí mismo."</span><span class="sxs-lookup"><span data-stu-id="c096f-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="c096f-116">A continuación, desplácese hacia abajo y haga clic en "servidor" tal como se muestra en la segunda imagen abajo.</span><span class="sxs-lookup"><span data-stu-id="c096f-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="c096f-119">Esto hará que aparezca con la etiqueta, un cuadro de texto "me lees."</span><span class="sxs-lookup"><span data-stu-id="c096f-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="c096f-120">Continúe y leerlo.</span><span class="sxs-lookup"><span data-stu-id="c096f-120">Go ahead and read it.</span></span> <span data-ttu-id="c096f-121">Una vez finalizado, haga clic en el vínculo situado junto a "downloadSDK" para descargarla.</span><span class="sxs-lookup"><span data-stu-id="c096f-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="c096f-123">Haga doble clic en la carpeta una vez que termine la descarga.</span><span class="sxs-lookup"><span data-stu-id="c096f-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="c096f-124">Una vez que el Explorador de archivos abre revelar la carpeta del SDK, copie la carpeta del SDK.</span><span class="sxs-lookup"><span data-stu-id="c096f-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="c096f-125">El siguiente paso sería entrar en la unidad C: de windows y crear una nueva carpeta denominada "server".</span><span class="sxs-lookup"><span data-stu-id="c096f-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="c096f-127">Ahora abra la carpeta y pegue la carpeta del SDK que copió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c096f-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="c096f-129">Una vez que se ha completado, abra la carpeta del SDK y vaya a "implementar", a continuación, "bin_Win64", a continuación, haga doble clic en "control photon".</span><span class="sxs-lookup"><span data-stu-id="c096f-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="c096f-131">Nota: Si tiene alguna pregunta sobre la dirección IP o alguna otra pregunta similar, puede encontrar la mayor parte de su información en la barra de herramientas (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="c096f-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="c096f-133">Ahora que el servidor está configurado y se inicia, vuelva al sitio Web de Photon y haga clic en el icono del perfil (aplicar la conversión boxing en la imagen siguiente) y seleccione "las aplicaciones".</span><span class="sxs-lookup"><span data-stu-id="c096f-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="c096f-135">Crear un identificador de aplicación, haga clic en el botón "crear una nueva aplicación".</span><span class="sxs-lookup"><span data-stu-id="c096f-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="c096f-137">Seleccione "Ejecutar Photon" en el menú desplegable bajo "tipo photon".</span><span class="sxs-lookup"><span data-stu-id="c096f-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="c096f-138">A continuación, asígnele un nombre, (algo que recordaría).</span><span class="sxs-lookup"><span data-stu-id="c096f-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="c096f-139">En este ejemplo, se lo denominó "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="c096f-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="c096f-140">Una vez finalizado, haga clic en "crear".</span><span class="sxs-lookup"><span data-stu-id="c096f-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="c096f-142">Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="c096f-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="c096f-143">Haga clic en el identificador de aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="c096f-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="c096f-144">Pegar es en algún lugar que puede acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="c096f-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="c096f-146">Cree un nuevo proyecto de unity.</span><span class="sxs-lookup"><span data-stu-id="c096f-146">Create a new unity project.</span></span> <span data-ttu-id="c096f-147">Abra el centro de Unity y haga clic en "nuevo".</span><span class="sxs-lookup"><span data-stu-id="c096f-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="c096f-148">Asígnele el nombre "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="c096f-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="c096f-149">A continuación, haga clic en crear.</span><span class="sxs-lookup"><span data-stu-id="c096f-149">Then click create.</span></span> 

   > <span data-ttu-id="c096f-150">Nota: Esto puede tardar hasta 2 minutos en cargarse, según la velocidad del equipo.</span><span class="sxs-lookup"><span data-stu-id="c096f-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="c096f-152">Nota: elegir una ubicación para guardar el proyecto en el equipo cambiando la opción de "ubicación".</span><span class="sxs-lookup"><span data-stu-id="c096f-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="c096f-153">Guárdelo en un lugar recordará y acceder fácilmente a.</span><span class="sxs-lookup"><span data-stu-id="c096f-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="c096f-154">Cuando se cargue el proyecto, haga clic en el "almacén de activos".</span><span class="sxs-lookup"><span data-stu-id="c096f-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="c096f-155">A continuación, en el cuadro de búsqueda que se muestra en la imagen siguiente, escriba en "Juego de palabras" y seleccione el recurso "Photon 2 del juego de palabras libre".</span><span class="sxs-lookup"><span data-stu-id="c096f-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="c096f-157">¡Descargue e importe!</span><span class="sxs-lookup"><span data-stu-id="c096f-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="c096f-159">**Configurar el proyecto de Unity**</span><span class="sxs-lookup"><span data-stu-id="c096f-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="c096f-160">Descargue un nuevo recurso necesario para configurar Photon en Unity haciendo [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="c096f-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="c096f-161">En Unity, haga clic en el menú de recursos y seleccione "importar recursos" y luego haga clic en "recursos personalizados".</span><span class="sxs-lookup"><span data-stu-id="c096f-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="c096f-163">Seleccione el paquete de Unity que acaba de descargar desde el vínculo indicado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="c096f-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="c096f-164">Una vez que aparece el botón Importar en Unity, haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="c096f-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="c096f-166">Nota: donde descargó el paquete a será donde se encuentra.</span><span class="sxs-lookup"><span data-stu-id="c096f-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="c096f-167">La imagen anterior no describe donde encontrará el paquete.</span><span class="sxs-lookup"><span data-stu-id="c096f-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="c096f-168">Crear una nueva escena (Esto puede ser lleva a cabo mediante el control o comando + N o haciendo clic en "file" y seleccione "nueva escena.").</span><span class="sxs-lookup"><span data-stu-id="c096f-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="c096f-169">Guarde la escena como "HLSharedProjectMain."</span><span class="sxs-lookup"><span data-stu-id="c096f-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="c096f-170">Nota: puede recibir un mensaje emergente que tiene un aspecto similar a la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="c096f-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="c096f-171">Por ahora, simplemente haga clic en "no".</span><span class="sxs-lookup"><span data-stu-id="c096f-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="c096f-173">En "Mixed Reality Toolkit", haga clic en "Agregar a la escena y configurar".</span><span class="sxs-lookup"><span data-stu-id="c096f-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="c096f-175">Una vez completado, un nuevo archivo de configuración aparecerá, lo que le ofrece la opción de personalizar el perfil.</span><span class="sxs-lookup"><span data-stu-id="c096f-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="c096f-176">Haga clic en "copiar y personalizar".</span><span class="sxs-lookup"><span data-stu-id="c096f-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="c096f-178">Desplácese hacia abajo y desactive la opción "Habilitar sistema de diagnóstico".</span><span class="sxs-lookup"><span data-stu-id="c096f-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="c096f-179">Así resultará más fácil de configurar este proyecto.</span><span class="sxs-lookup"><span data-stu-id="c096f-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="c096f-181">Abra la configuración de compilación (control + MAYÚS + B).</span><span class="sxs-lookup"><span data-stu-id="c096f-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="c096f-182">Tenga en cuenta que el programa está establecido actualmente en la plataforma "PC, Mac y Linux independiente".</span><span class="sxs-lookup"><span data-stu-id="c096f-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="c096f-183">Para este proyecto, establezca la plataforma como "plataforma universal de windows".</span><span class="sxs-lookup"><span data-stu-id="c096f-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="c096f-184">Selecciónelo y haga clic en "Cambiar plataforma".</span><span class="sxs-lookup"><span data-stu-id="c096f-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="c096f-186">Una vez que haya terminado, haga clic en el cuadro que dice "Agregar escenas abiertos".</span><span class="sxs-lookup"><span data-stu-id="c096f-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="c096f-187">Ahora, vaya al panel de inspector y asegúrese de que la casilla situada a la derecha de "la realidad virtual admitida" (como se muestra en la imagen siguiente) está activada.</span><span class="sxs-lookup"><span data-stu-id="c096f-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="c096f-189">Nota: Asegúrese también de que la casilla de verificación situada junto a "escenas/HLSharedProjectMain" también se comprueba.</span><span class="sxs-lookup"><span data-stu-id="c096f-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="c096f-190">En la "configuración de publicación" en el panel del inspector desplácese hacia abajo hasta "capacidades" y asegúrese de que se marcan solo las siguientes casillas:</span><span class="sxs-lookup"><span data-stu-id="c096f-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="c096f-191">cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="c096f-191">internet client</span></span>
- <span data-ttu-id="c096f-192">servidor de cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="c096f-192">internet client server</span></span>
- <span data-ttu-id="c096f-193">servidor de cliente de red privada</span><span class="sxs-lookup"><span data-stu-id="c096f-193">private network client server</span></span>
- <span data-ttu-id="c096f-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="c096f-194">camera/webcam</span></span>
- <span data-ttu-id="c096f-195">Micrófono</span><span class="sxs-lookup"><span data-stu-id="c096f-195">microphone</span></span>

21. <span data-ttu-id="c096f-196">Al igual que el paso 12, el siguiente paso sería importar otro paquete personalizado denominado "Lesson2" que se puede descargar [aquí]. [lesson2.unitypackage vínculo va aquí] Importar ese paquete.</span><span class="sxs-lookup"><span data-stu-id="c096f-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="c096f-198">Ahora, en el panel de proyecto, vaya a la carpeta "prefabricados", puesto que en los pasos siguientes, va a implementar unos prefabricados en la escena.</span><span class="sxs-lookup"><span data-stu-id="c096f-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="c096f-199">En la carpeta "prefabricados", haga clic y arrastre el prefabricado verá, "DebugWindow" en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="c096f-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="c096f-200">Una vez terminado, guarde el proyecto (haga clic en archivo, a continuación, guarde o control + S)</span><span class="sxs-lookup"><span data-stu-id="c096f-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="c096f-202">Nota: Puede que observe un elemento emergente aparece al hacer clic en el prefabricado verá, que le pide sobre Essentials TMP.</span><span class="sxs-lookup"><span data-stu-id="c096f-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="c096f-203">Haga clic en "Importar TMP Essentials" como será necesaria.</span><span class="sxs-lookup"><span data-stu-id="c096f-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="c096f-205">**Conectar varios usuarios**</span><span class="sxs-lookup"><span data-stu-id="c096f-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="c096f-206">Como paso 22, en la carpeta "prefabricados" en el panel de proyecto, el siguiente paso es arrastrar y colocar el recurso prefabricado "NetworkLobby" a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="c096f-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="c096f-208">Cuando abra el recurso prefabricado primario, "NetworkLobby", debería ver a un elemento secundario prefabricado, "NetworkRoom".</span><span class="sxs-lookup"><span data-stu-id="c096f-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="c096f-209">Con él seleccionado, vaya al panel de inspector y haga clic en "Agregar el componente".</span><span class="sxs-lookup"><span data-stu-id="c096f-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="c096f-210">Busque "PhotonView" y agregue el componente.</span><span class="sxs-lookup"><span data-stu-id="c096f-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="c096f-212">Crear un nuevo objeto de juego vacío en la jerarquía (clic derecho en la jerarquía y seleccione 'empty').</span><span class="sxs-lookup"><span data-stu-id="c096f-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="c096f-213">Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y el nombre del objeto, "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="c096f-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="c096f-215">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="c096f-215">Congratulations</span></span>



