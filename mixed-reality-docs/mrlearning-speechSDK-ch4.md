---
title: 'Tutoriales de Azure Speech Services: 4. Configuración del propósito y la comprensión del lenguaje natural'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 8805fa6410e882bce2f0fe8da780dfd5f794cc74
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554011"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="2782d-105">4. configuración del propósito y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="2782d-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="2782d-106">En esta lección, explorará la característica de intención del servicio de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="2782d-106">In this lesson, you will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="2782d-107">La característica de intención le permite equipar nuestra aplicación con comandos de voz con tecnología de inteligencia artificial, donde los usuarios pueden indicar comandos de voz no específicos y seguir teniendo la intención entendida por el sistema.</span><span class="sxs-lookup"><span data-stu-id="2782d-107">The Intent feature allows you to equip our application with AI-powered voice commands, where users can say non-specific voice commands and still have their intent understood by the system.</span></span> <span data-ttu-id="2782d-108">En esta lección, se configurará nuestro portal de LUIS de Azure, se configurará nuestra intención/entidades/grabaciones, se publicará nuestro recurso de intención, se conectará la aplicación de Unity a nuestro recurso de intención y se realizará nuestra primera llamada de API de intención.</span><span class="sxs-lookup"><span data-stu-id="2782d-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="2782d-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2782d-109">Objectives</span></span>

- <span data-ttu-id="2782d-110">Obtenga información sobre cómo configurar la intención y el lenguaje natural en nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="2782d-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="2782d-111">Aprenda a configurar el portal de LUIS de Azure</span><span class="sxs-lookup"><span data-stu-id="2782d-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="2782d-112">Aprenda a configurar la intención, las entidades y los grabaciones en Azure</span><span class="sxs-lookup"><span data-stu-id="2782d-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="2782d-113">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="2782d-113">Instructions</span></span>

1. <span data-ttu-id="2782d-114">Permita que el equipo habilite el dictado.</span><span class="sxs-lookup"><span data-stu-id="2782d-114">Allow your machine to enable Dictation.</span></span> <span data-ttu-id="2782d-115">Para ello, vaya a configuración de Windows, seleccione "privacidad", "voz", seguido de "entrada manuscrita & escribiendo" y active los servicios de voz y sugerencias de escritura.</span><span class="sxs-lookup"><span data-stu-id="2782d-115">To do this, go to Windows Settings, select "privacy," then "speech," followed by "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="2782d-119">Inicie sesión en el [portal de Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="2782d-119">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="2782d-120">Una vez que haya iniciado sesión, haga clic en crear un recurso, busque "Language Understanding" y haga clic en entrar.</span><span class="sxs-lookup"><span data-stu-id="2782d-120">Once you are logged in, click on Create a resource, search for "Language Understanding" and click Enter.</span></span>

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="2782d-122">Haga clic en el botón **crear** para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="2782d-122">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="2782d-124">Asigne un **nombre**al recurso, por ejemplo, *Speech-SDK-Learning-Module*.</span><span class="sxs-lookup"><span data-stu-id="2782d-124">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="2782d-125">En **suscripción**, seleccione *pago por* uso o *pista gratuita* si tiene una cuenta de prueba.</span><span class="sxs-lookup"><span data-stu-id="2782d-125">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="2782d-126">A continuación, cree un nuevo **grupo de recursos** . para ello, haga clic en el vínculo **crear nuevo** , escriba un nombre, por ejemplo, *HoloLens-2-tutoriales-Resource-Group*y haga clic en el botón **Aceptar** .</span><span class="sxs-lookup"><span data-stu-id="2782d-126">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and click the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="2782d-128">Seleccione la **Ubicación de creación** y la **ubicación en tiempo de ejecución**.</span><span class="sxs-lookup"><span data-stu-id="2782d-128">Select your **Authoring location** and **Runtime location**.</span></span> <span data-ttu-id="2782d-129">Para este tutorial, use *(EE. UU.) oeste de EE. UU.* y luego elija *F0 (5 llamadas por segundo, 10 000 llamadas al mes)* para el plan de tarifa de **creación** y el plan de tarifa **en tiempo de ejecución**.</span><span class="sxs-lookup"><span data-stu-id="2782d-129">For the purpose of this tutorial, use *(US) West US*, then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="2782d-130">Por último, haga clic en el botón **crear** para crear el recurso, así como el nuevo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="2782d-130">Finally, click the **Create** button to create the resource, as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-Step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="2782d-132">Después de hacer clic en el botón crear, tendrá que esperar a que se cree el servicio, lo que puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="2782d-132">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

5. <span data-ttu-id="2782d-133">Una vez completado el proceso de creación de recursos, verá el mensaje **se ha completado la implementación**.</span><span class="sxs-lookup"><span data-stu-id="2782d-133">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-Step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="2782d-135">Con la misma cuenta de usuario, inicie sesión en el portal de [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , seleccione su país y acepte los términos de uso.</span><span class="sxs-lookup"><span data-stu-id="2782d-135">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2782d-136">Al llegar al portal de Language Understanding, es posible que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="2782d-136">Upon reaching the Language Understanding portal, you may need to log in, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="2782d-137">Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la página de bienvenida para buscar y hacer clic en el botón "crear LUIS" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2782d-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the Welcome page to find and click the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="2782d-138">Una vez que haya iniciado sesión, haga clic en mis aplicaciones (si no está actualmente en esa sección).</span><span class="sxs-lookup"><span data-stu-id="2782d-138">Once logged in, click My Apps (if you are not currently in that section).</span></span> <span data-ttu-id="2782d-139">Después, puede hacer clic en crear nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="2782d-139">You can then click on Create new app.</span></span> <span data-ttu-id="2782d-140">Asigne a la nueva aplicación el nombre "módulo de aprendizaje de SDK de Speech".</span><span class="sxs-lookup"><span data-stu-id="2782d-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="2782d-141">Agregue "Speech SDK Learning Module" al campo Descripción.</span><span class="sxs-lookup"><span data-stu-id="2782d-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="2782d-142">A continuación, haga clic en "listo".</span><span class="sxs-lookup"><span data-stu-id="2782d-142">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="2782d-145">Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la "referencia cultural" al idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="2782d-145">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="2782d-146">Haga clic en "compilar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="2782d-146">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="2782d-147">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en "crear nuevo intento" y asígnele el nombre "PressButton".</span><span class="sxs-lookup"><span data-stu-id="2782d-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2782d-149">Es importante usar los nombres de los intentos y las entidades que se usan en este tutorial, ya que la aplicación Lunarcom hará referencia a ellos por su nombre.</span><span class="sxs-lookup"><span data-stu-id="2782d-149">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2782d-150">Ahora debería tener 2 intenciones: "PressButton" y "none".</span><span class="sxs-lookup"><span data-stu-id="2782d-150">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="2782d-151">En activos de la aplicación de la izquierda, seleccione "entidades", haga clic en "crear nueva entidad", asígnele el nombre "acción" y mantenga el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="2782d-151">Under App Assets on the left, select “Entities”, click “Create New Entity”, name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="2782d-153">Vuelva a hacer clic en "crear nueva entidad" y asígnele el nombre "destino".</span><span class="sxs-lookup"><span data-stu-id="2782d-153">Click “Create New Entity” again and name it “Target”.</span></span> <span data-ttu-id="2782d-154">CONSERVE también el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="2782d-154">Keep the Entity Type as “Simple”, as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="2782d-156">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en el intento de "PressButton" que creó en el paso 10.</span><span class="sxs-lookup"><span data-stu-id="2782d-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="2782d-158">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar valores de entidad".</span><span class="sxs-lookup"><span data-stu-id="2782d-158">Click the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="2782d-160">Haga clic en la "Escriba un ejemplo..."</span><span class="sxs-lookup"><span data-stu-id="2782d-160">Click the “Enter an example…”</span></span> <span data-ttu-id="2782d-161">.</span><span class="sxs-lookup"><span data-stu-id="2782d-161">textbox.</span></span> <span data-ttu-id="2782d-162">A continuación, escriba el siguiente grabaciones:</span><span class="sxs-lookup"><span data-stu-id="2782d-162">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="2782d-164">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar nombres de entidad".</span><span class="sxs-lookup"><span data-stu-id="2782d-164">Click the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="2782d-166">Asegúrese de que cada uno de los 10 grabaciones tenga las siguientes etiquetas de entidad en los lugares siguientes en 1). al hacer clic en palabras que no están etiquetadas y, en el menú emergente, seleccionando "quitar etiqueta" y 2). al hacer clic en las palabras que deben etiquetarse y, en el menú emergente, seleccione la etiqueta adecuada.</span><span class="sxs-lookup"><span data-stu-id="2782d-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="2782d-168">Ahora, para publicar el modelo, haga clic en "entrenar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="2782d-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="2782d-169">Después, una vez finalizado el procesamiento, haga clic en "probar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="2782d-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="2782d-171">Escriba en "seleccionar el botón de inicio" en el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="2782d-171">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2782d-172">No hemos agregado "Select" como acción en ninguno de nuestros grabaciones, pero si hace clic en "inspeccionar", el modelo reconoció "Select" como entidad de acción.</span><span class="sxs-lookup"><span data-stu-id="2782d-172">We did not add “select” as an action in any of our Utterances, but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="2782d-174">Haga clic en "publicar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="2782d-174">Click "publish" in the top right.</span></span> <span data-ttu-id="2782d-175">Asegúrese de que la lista desplegable indica "producción" y haga clic en "publicar" en el menú emergente.</span><span class="sxs-lookup"><span data-stu-id="2782d-175">Ensure the dropdown says “Production” and click "publish" on the popup, as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="2782d-177">Una vez publicada, aparecerá una barra verde en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="2782d-177">Once published, a green bar should appear at the top of the page.</span></span> <span data-ttu-id="2782d-178">Haga clic en la barra verde para ver la página "administrar".</span><span class="sxs-lookup"><span data-stu-id="2782d-178">Click the green bar to view the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="2782d-180">Haga clic en "claves y puntos de conexión" en "configuración de la aplicación" a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="2782d-180">Click "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="2782d-181">A continuación, establezca la lista desplegable "publicar en" como "producción".</span><span class="sxs-lookup"><span data-stu-id="2782d-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="2782d-182">Establezca la zona horaria para que coincida con la suya y active la casilla para incluir todas las puntuaciones de intención previstas.</span><span class="sxs-lookup"><span data-stu-id="2782d-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="2782d-183">Por último, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="2782d-183">Lastly, click "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="2782d-185">Seleccione inquilino en la primera lista desplegable y seleccione "pago por uso" en la lista desplegable nombre de suscripción.</span><span class="sxs-lookup"><span data-stu-id="2782d-185">Select tenant from the first dropdown and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="2782d-186">En el nombre del recurso LUIS, elija el recurso que se creó anteriormente en los pasos 1-5.</span><span class="sxs-lookup"><span data-stu-id="2782d-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="2782d-187">A continuación, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="2782d-187">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2782d-189">Asegúrese de copiar y guardar la dirección URL del punto de conexión asociada con el recurso que acaba de asignar para que sea fácilmente accesible para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="2782d-189">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2782d-190">En el nombre del inquilino, coloque su corporación o el perfil que creó para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="2782d-190">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="2782d-191">Ahora, abra la nueva aplicación en Unity y seleccione el objeto de Lunarcom_Base de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="2782d-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="2782d-192">Haga clic en "Agregar componente" en el panel Inspector y busque y seleccione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="2782d-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="2782d-194">En el campo punto de conexión Luis de "LunarcomIntentRecognizer" en el panel Inspector, escriba la dirección URL del punto de conexión que guardó en el paso 21.</span><span class="sxs-lookup"><span data-stu-id="2782d-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 21.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="2782d-196">En el componente "LunarcomOfflineRecognizer" del panel Inspector, asegúrese de que está seleccionado "Deshabilitar" para "SimulateOfflineMode"; de lo contrario, no funcionará la prueba del programa.</span><span class="sxs-lookup"><span data-stu-id="2782d-196">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="2782d-197">En la ventana de proyecto, navegue a los recursos > MRTK. Tutoriales. GettingStarted > Prefabs > carpeta RocketLauncher, arrastre el RocketLauncher_Complete recurso prefabricado a la ventana de jerarquía y colóquelo delante del objeto Lunarcom_Base.</span><span class="sxs-lookup"><span data-stu-id="2782d-197">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs > RocketLauncher folder, drag the RocketLauncher_Complete prefab into your Hierarchy window, and position it in front of the Lunarcom_Base object.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing01.png)

25. <span data-ttu-id="2782d-199">En la ventana jerarquía, seleccione el objeto Lunarcom_Base y busque el componente reconocedor de intención de Lunarcom (Script) y, a continuación, expanda el objeto de botón RocketLauncher_Complete > y asigne cada uno de los objetos de botón a los botones del selector lunar correspondientes. campo.</span><span class="sxs-lookup"><span data-stu-id="2782d-199">In the Hierarchy window, select the Lunarcom_Base object and locate the Lunarcom Intent Recognizer (Script) component, then expand the RocketLauncher_Complete > Button object and assign each of the button objects to the corresponding Lunar Launcher Buttons field.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im-missing02.png)

26. <span data-ttu-id="2782d-201">Presione el botón reproducir en el editor de Unity y haga clic en el botón Rocket para iniciar el reconocimiento de intenciones.</span><span class="sxs-lookup"><span data-stu-id="2782d-201">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="2782d-202">En la frase, haga clic en el botón iniciar Rocket.</span><span class="sxs-lookup"><span data-stu-id="2782d-202">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="2782d-203">La aplicación reconoció la función deseada y activó el botón Rocket.</span><span class="sxs-lookup"><span data-stu-id="2782d-203">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="2782d-205">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="2782d-205">Congratulations</span></span>

<span data-ttu-id="2782d-206">En esta lección ha aprendido a agregar comandos de voz con tecnología de AI.</span><span class="sxs-lookup"><span data-stu-id="2782d-206">In this lesson, you learned how to add AI-powered speech commands.</span></span> <span data-ttu-id="2782d-207">Ahora el programa puede reconocer la intención de los usuarios, incluso si no son comandos de voz precisos.</span><span class="sxs-lookup"><span data-stu-id="2782d-207">Now your program can recognize users' intent, even if they do not utter precise voice commands!</span></span>
