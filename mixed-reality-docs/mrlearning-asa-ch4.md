---
title: MR Learning ASA Module Azure Spatial delimitador de HoloLens 2
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437794"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="754d7-104">Photon (corregir si soy mal)</span><span class="sxs-lookup"><span data-stu-id="754d7-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="754d7-105">En esta lección,</span><span class="sxs-lookup"><span data-stu-id="754d7-105">In this lesson,</span></span> 

<span data-ttu-id="754d7-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="754d7-106">Objectives:</span></span>

* <span data-ttu-id="754d7-107">Obtener información sobre cómo _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="754d7-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="754d7-108">Obtener información sobre cómo _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="754d7-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="754d7-109">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="754d7-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="754d7-110">Configuración de Photon</span><span class="sxs-lookup"><span data-stu-id="754d7-110">Setting Up Photon</span></span>

1. <span data-ttu-id="754d7-111">Configure una cuenta de [Photon](https://dashboard.photonengine.com//Account/SignUp) .</span><span class="sxs-lookup"><span data-stu-id="754d7-111">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="754d7-112">Esto consistirá en imputar el correo electrónico y seguir algunos pasos de comprobación.</span><span class="sxs-lookup"><span data-stu-id="754d7-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="754d7-114">Una vez que se haya registrado, haga clic en SDK.</span><span class="sxs-lookup"><span data-stu-id="754d7-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="754d7-115">Una vez que esté en esa página, haga clic en "servidor" y asegúrese de que dice "autohospedado".</span><span class="sxs-lookup"><span data-stu-id="754d7-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="754d7-116">A continuación, desplácese hacia abajo y haga clic en "servidor" como se muestra en la segunda imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="754d7-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="754d7-119">Esto hará que un cuadro de texto aparezca etiquetado como "Léame".</span><span class="sxs-lookup"><span data-stu-id="754d7-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="754d7-120">Siga leyendo.</span><span class="sxs-lookup"><span data-stu-id="754d7-120">Go ahead and read it.</span></span> <span data-ttu-id="754d7-121">Una vez finalizado, haga clic en el vínculo situado junto a "downloadSDK" para descargarlo.</span><span class="sxs-lookup"><span data-stu-id="754d7-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="754d7-123">Haga doble clic en la carpeta una vez finalizada la descarga.</span><span class="sxs-lookup"><span data-stu-id="754d7-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="754d7-124">Cuando el explorador de archivos se abra y revele la carpeta del SDK, copie la carpeta del SDK.</span><span class="sxs-lookup"><span data-stu-id="754d7-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="754d7-125">El siguiente paso consiste en ir a la unidad C: de Windows y crear una nueva carpeta denominada "Server".</span><span class="sxs-lookup"><span data-stu-id="754d7-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="754d7-127">Ahora, abra la carpeta y pegue la carpeta del SDK que copió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="754d7-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="754d7-129">Una vez que se haya completado, abra la carpeta SDK, vaya a "deploy", "bin_Win64" y haga doble clic en "Photon control".</span><span class="sxs-lookup"><span data-stu-id="754d7-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="754d7-131">Nota: Si tiene alguna pregunta sobre la dirección IP o cualquier otra pregunta similar, puede encontrar la mayor parte de la información en la barra de herramientas (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="754d7-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="754d7-133">Ahora que el servidor está configurado e iniciado, vuelva al sitio web de Photon y haga clic en el icono de perfil (con la conversión boxing de la imagen siguiente) y seleccione "Your Applications".</span><span class="sxs-lookup"><span data-stu-id="754d7-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="754d7-135">Cree un identificador de aplicación haciendo clic en el botón "crear una nueva aplicación".</span><span class="sxs-lookup"><span data-stu-id="754d7-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="754d7-137">Seleccione "Photon ejecutar" en el menú desplegable en "tipo de Photon".</span><span class="sxs-lookup"><span data-stu-id="754d7-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="754d7-138">A continuación, asígnele un nombre (algo que recordaría).</span><span class="sxs-lookup"><span data-stu-id="754d7-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="754d7-139">En este ejemplo, se denomina "HoloLensPhotonProject".</span><span class="sxs-lookup"><span data-stu-id="754d7-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="754d7-140">Una vez finalizado, haga clic en "crear".</span><span class="sxs-lookup"><span data-stu-id="754d7-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="754d7-142">Una vez hecho esto, vuelva a la página de aplicaciones y debería ver algo parecido a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="754d7-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="754d7-143">Haga clic en el identificador de la aplicación y cópielo.</span><span class="sxs-lookup"><span data-stu-id="754d7-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="754d7-144">Pegar es un lugar en el que se puede acceder fácilmente.</span><span class="sxs-lookup"><span data-stu-id="754d7-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="754d7-146">Cree un nuevo proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="754d7-146">Create a new unity project.</span></span> <span data-ttu-id="754d7-147">Abra Unity Hub y haga clic en "nuevo".</span><span class="sxs-lookup"><span data-stu-id="754d7-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="754d7-148">Asígnele el nombre "HLSharingProject".</span><span class="sxs-lookup"><span data-stu-id="754d7-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="754d7-149">A continuación, haga clic en crear.</span><span class="sxs-lookup"><span data-stu-id="754d7-149">Then click create.</span></span> 

   > <span data-ttu-id="754d7-150">Nota: esto puede tardar hasta 2 minutos en cargarse, en función de la velocidad del equipo.</span><span class="sxs-lookup"><span data-stu-id="754d7-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="754d7-152">Nota: elija un lugar para guardar el proyecto en el equipo; para ello, cambie la opción "ubicación".</span><span class="sxs-lookup"><span data-stu-id="754d7-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="754d7-153">Guárdelo en un lugar que recuerde y que tenga fácil acceso a.</span><span class="sxs-lookup"><span data-stu-id="754d7-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="754d7-154">Una vez que se cargue el proyecto, haga clic en el "almacén de activos".</span><span class="sxs-lookup"><span data-stu-id="754d7-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="754d7-155">A continuación, en el cuadro de búsqueda que aparece en la imagen siguiente, escriba "BURDO" y seleccione el recurso "Photon BURDO-2 FREE".</span><span class="sxs-lookup"><span data-stu-id="754d7-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="754d7-157">Descargar e importar</span><span class="sxs-lookup"><span data-stu-id="754d7-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="754d7-159">**Configuración del proyecto de Unity**</span><span class="sxs-lookup"><span data-stu-id="754d7-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="754d7-160">Descargue un nuevo recurso necesario para configurar Photon en Unity. para ello, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="754d7-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="754d7-161">En Unity, haga clic en el menú activos y seleccione "importar recursos" y, a continuación, haga clic en "activos personalizados".</span><span class="sxs-lookup"><span data-stu-id="754d7-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="754d7-163">Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="754d7-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="754d7-164">Cuando aparezca el botón importar en Unity, haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="754d7-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="754d7-166">Nota: dondequiera que haya descargado el paquete, será donde lo encuentre.</span><span class="sxs-lookup"><span data-stu-id="754d7-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="754d7-167">La imagen anterior no indica dónde encontrará el paquete.</span><span class="sxs-lookup"><span data-stu-id="754d7-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="754d7-168">Cree una nueva escena (esto puede hacerse mediante control/comando + N o haciendo clic en "archivo" y seleccionando "nueva escena").</span><span class="sxs-lookup"><span data-stu-id="754d7-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="754d7-169">Guarde la escena como "HLSharedProjectMain".</span><span class="sxs-lookup"><span data-stu-id="754d7-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="754d7-170">Nota: es posible que reciba un elemento emergente que tenga un aspecto similar a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="754d7-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="754d7-171">Por ahora, solo tiene que hacer clic en "no".</span><span class="sxs-lookup"><span data-stu-id="754d7-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="754d7-173">En "kit de herramientas de realidad mixta", haga clic en "Agregar a la escena y configurar".</span><span class="sxs-lookup"><span data-stu-id="754d7-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="754d7-175">Una vez que haya finalizado, aparecerá un nuevo archivo de configuración que le proporcionará la opción de personalizar el perfil.</span><span class="sxs-lookup"><span data-stu-id="754d7-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="754d7-176">Haga clic en "copiar y personalizar".</span><span class="sxs-lookup"><span data-stu-id="754d7-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="754d7-178">Desplácese hacia abajo y desactive "habilitar el sistema de diagnóstico".</span><span class="sxs-lookup"><span data-stu-id="754d7-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="754d7-179">Esto facilitará la configuración de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="754d7-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="754d7-181">Abra la configuración de compilación (Control + Mayús + B).</span><span class="sxs-lookup"><span data-stu-id="754d7-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="754d7-182">Tenga en cuenta que el programa está establecido actualmente en la plataforma "PC, Mac y Linux standalone".</span><span class="sxs-lookup"><span data-stu-id="754d7-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="754d7-183">Para este proyecto, establezca la plataforma en "plataforma universal de Windows".</span><span class="sxs-lookup"><span data-stu-id="754d7-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="754d7-184">Selecciónelo y haga clic en "cambiar plataforma".</span><span class="sxs-lookup"><span data-stu-id="754d7-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="754d7-186">Una vez que haya finalizado, haga clic en el cuadro que indica "agregar escenas abiertas".</span><span class="sxs-lookup"><span data-stu-id="754d7-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="754d7-187">Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de "realidad virtual compatible" (como se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="754d7-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="754d7-189">Nota: Asegúrese también de que la casilla situada junto a "Scenes/HLSharedProjectMain" también está activada.</span><span class="sxs-lookup"><span data-stu-id="754d7-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="754d7-190">En "configuración de publicación" en el panel de inspectores, desplácese hacia abajo hasta "capacidades" y asegúrese de que solo están marcadas las siguientes casillas:</span><span class="sxs-lookup"><span data-stu-id="754d7-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="754d7-191">cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="754d7-191">internet client</span></span>
- <span data-ttu-id="754d7-192">servidor de cliente de Internet</span><span class="sxs-lookup"><span data-stu-id="754d7-192">internet client server</span></span>
- <span data-ttu-id="754d7-193">servidor cliente de red privada</span><span class="sxs-lookup"><span data-stu-id="754d7-193">private network client server</span></span>
- <span data-ttu-id="754d7-194">cámara o cámara web</span><span class="sxs-lookup"><span data-stu-id="754d7-194">camera/webcam</span></span>
- <span data-ttu-id="754d7-195">micrófono</span><span class="sxs-lookup"><span data-stu-id="754d7-195">microphone</span></span>

21. <span data-ttu-id="754d7-196">Al igual que el paso 12, el paso siguiente sería importar otro paquete personalizado llamado "Lesson2", que se puede descargar [aquí.] [lesson2. unitypackage Tools vínculo va aquí] Importe ese paquete.</span><span class="sxs-lookup"><span data-stu-id="754d7-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="754d7-198">Ahora, en el panel Proyecto, vaya a la carpeta "Prefabs", ya que en los próximos pasos va a implementar algunos Prefabs en la escena.</span><span class="sxs-lookup"><span data-stu-id="754d7-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="754d7-199">En la carpeta "Prefabs", haga clic y arrastre recurso prefabricado "DebugWindow" a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="754d7-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="754d7-200">Cuando haya terminado, guarde el proyecto (haga clic en archivo, después en guardar o en control + S).</span><span class="sxs-lookup"><span data-stu-id="754d7-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="754d7-202">Nota: es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials.</span><span class="sxs-lookup"><span data-stu-id="754d7-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="754d7-203">Haga clic en "importar TMP Essentials", ya que se necesitarán.</span><span class="sxs-lookup"><span data-stu-id="754d7-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="754d7-205">**Conexión de varios usuarios**</span><span class="sxs-lookup"><span data-stu-id="754d7-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="754d7-206">Al igual que en el paso 22, en la carpeta "Prefabs" del panel Proyecto, el paso siguiente consiste en arrastrar y colocar el NetworkLobby "recurso prefabricado" en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="754d7-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="754d7-208">Al abrir el recurso prefabricado primario, "NetworkLobby", debería ver un recurso prefabricado secundario, "NetworkRoom".</span><span class="sxs-lookup"><span data-stu-id="754d7-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="754d7-209">Con esta opción seleccionada, vaya al panel Inspector y haga clic en "Agregar componente".</span><span class="sxs-lookup"><span data-stu-id="754d7-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="754d7-210">Busque "PhotonView" y agregue el componente.</span><span class="sxs-lookup"><span data-stu-id="754d7-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="754d7-212">Cree un nuevo objeto de juego vacío en la jerarquía (haga clic con el botón derecho en la jerarquía y seleccione "vacío").</span><span class="sxs-lookup"><span data-stu-id="754d7-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="754d7-213">Asegúrese de que la posición está establecida en x = 0, y = 0, z = 0 y asigne al objeto el nombre "PhotonUser".</span><span class="sxs-lookup"><span data-stu-id="754d7-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="754d7-215">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="754d7-215">Congratulations</span></span>



