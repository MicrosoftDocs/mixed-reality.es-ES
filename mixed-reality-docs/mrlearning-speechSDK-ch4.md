---
title: 'Tutoriales de Azure Speech Services: 4. Configuración del propósito y la comprensión del lenguaje natural'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 9235452d9dce38e9d849821a694a5d4c710d8e87
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913322"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="4ca5d-105">4. configuración del propósito y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="4ca5d-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="4ca5d-106">En esta lección, exploraremos la característica de intención del servicio de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="4ca5d-107">La característica de intención nos permite equipar nuestra aplicación con comandos de voz con tecnología de AI, donde los usuarios pueden indicar comandos de voz no específicos y seguir teniendo la intención entendida por el sistema.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="4ca5d-108">En esta lección, se configurará nuestro portal de LUIS de Azure, se configurará nuestra intención/entidades/grabaciones, se publicará nuestro recurso de intención, se conectará la aplicación de Unity a nuestro recurso de intención y se realizará nuestra primera llamada de API de intención.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="4ca5d-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4ca5d-109">Objectives</span></span>

- <span data-ttu-id="4ca5d-110">Obtenga información sobre cómo configurar la intención y el lenguaje natural en nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="4ca5d-111">Aprenda a configurar el portal de LUIS de Azure</span><span class="sxs-lookup"><span data-stu-id="4ca5d-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="4ca5d-112">Aprenda a configurar la intención, las entidades y los grabaciones en Azure</span><span class="sxs-lookup"><span data-stu-id="4ca5d-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="4ca5d-113">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="4ca5d-113">Instructions</span></span>

1. <span data-ttu-id="4ca5d-114">Permitir que la máquina habilite el dictado para ello, vaya a configuración de Windows, seleccione "privacidad", "voz" y, finalmente, "entrada manuscrita & escribir" y Active servicios de voz y sugerencias de escritura.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="4ca5d-118">Inicie sesión en el [portal de Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="4ca5d-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="4ca5d-119">Una vez que haya iniciado sesión, haga clic en crear un recurso y busque "Language Understanding" y haga clic en entrar.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

    ![mrlearning-Speech-CH4-1-Step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="4ca5d-121">Haga clic en el botón **crear** para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-121">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="4ca5d-123">Asigne un **nombre**al recurso, por ejemplo, *Speech-SDK-Learning-Module*.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-123">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="4ca5d-124">En **suscripción**, seleccione *pago por* uso o *pista gratuita* si tiene una cuenta de prueba.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-124">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="4ca5d-125">A continuación, cree un nuevo **grupo de recursos** . para ello, haga clic en el vínculo **crear nuevo** , escriba un nombre, por ejemplo, *HoloLens-2-tutoriales-Resource-Group*y haga clic en el botón **Aceptar** .</span><span class="sxs-lookup"><span data-stu-id="4ca5d-125">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and clicking the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="4ca5d-127">Seleccione la **Ubicación de creación** y el **tiempo de ejecución**para este tutorial, use *(EE. UU.) oeste de EE. UU.*</span><span class="sxs-lookup"><span data-stu-id="4ca5d-127">Select your **Authoring location** and **Runtime location**, for the purpose of this tutorial, use *(US) West US*.</span></span> <span data-ttu-id="4ca5d-128">A continuación, elija *F0 (5 llamadas por segundo, 10.000 llamadas al mes)* para el plan de tarifa de **creación** y el **plan de tarifa en tiempo de ejecución**.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-128">Then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="4ca5d-129">Por último, haga clic en el botón **crear** para crear el recurso y el nuevo grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-129">Finally, click the **Create** button to create the resource as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-Step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="4ca5d-131">Después de hacer clic en el botón crear, tendrá que esperar a que se cree el servicio, lo que puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-131">After you click the Create button you will have to wait for the service to be created, this might take a few minute.</span></span>

5. <span data-ttu-id="4ca5d-132">Una vez completado el proceso de creación de recursos, verá el mensaje **se ha completado la implementación**.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-132">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-Step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="4ca5d-134">Con la misma cuenta de usuario, inicie sesión en el portal de [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) , seleccione su país y acepte los términos de uso.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-134">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="4ca5d-135">Al llegar al portal de Language Understanding, puede que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-135">Upon reaching the Language Understanding portal, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="4ca5d-136">Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la Página principal, para buscar y hacer clic en el botón "crear LUIS" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-136">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="4ca5d-137">Una vez que haya iniciado sesión, haga clic en mis aplicaciones (si no está en esa sección actualmente).</span><span class="sxs-lookup"><span data-stu-id="4ca5d-137">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="4ca5d-138">Después, puede hacer clic en crear nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-138">You can then click on Create new app.</span></span> <span data-ttu-id="4ca5d-139">Asigne a la nueva aplicación el nombre "módulo de aprendizaje de SDK de Speech".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-139">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="4ca5d-140">Agregue "Speech SDK Learning Module" al campo Descripción.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-140">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="4ca5d-141">A continuación, haga clic en "listo".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-141">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="4ca5d-144">Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la "referencia cultural" al idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-144">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="4ca5d-145">Haga clic en "compilar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-145">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="4ca5d-146">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en "crear nuevo intento" y asígnele el nombre "PressButton".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-146">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="4ca5d-148">Es importante usar los nombres de los intentos y las entidades que se usan en este tutorial, ya que la aplicación Lunarcom hará referencia a ellos por su nombre.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-148">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="4ca5d-149">Ahora debería tener 2 intenciones: "PressButton" y "none".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-149">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="4ca5d-150">En activos de la aplicación de la izquierda, seleccione "entidades", haga clic en "crear nueva entidad" y asígnele el nombre "acción" y mantenga el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-150">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="4ca5d-152">Vuelva a hacer clic en "crear nueva entidad" y asígnele el nombre "destino" y conserve también el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-152">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="4ca5d-154">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en el intento de "PressButton" que creó en el paso 10.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-154">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="4ca5d-156">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar valores de entidad".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-156">Click on the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="4ca5d-158">Haga clic en el "Escriba un ejemplo..."</span><span class="sxs-lookup"><span data-stu-id="4ca5d-158">Click on the “Enter an example…”</span></span> <span data-ttu-id="4ca5d-159">mytextbox.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-159">textbox.</span></span> <span data-ttu-id="4ca5d-160">A continuación, escriba el siguiente grabaciones:</span><span class="sxs-lookup"><span data-stu-id="4ca5d-160">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="4ca5d-162">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar nombres de entidad".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-162">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="4ca5d-164">Asegúrese de que cada uno de los 10 grabaciones tenga las siguientes etiquetas de entidad en los lugares siguientes en 1). al hacer clic en palabras que no están etiquetadas y, en el menú emergente, seleccionando "quitar etiqueta" y 2). al hacer clic en las palabras que deben etiquetarse y, en el menú emergente, seleccione la etiqueta adecuada.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-164">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="4ca5d-166">Ahora, para publicar el modelo, haga clic en "entrenar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-166">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="4ca5d-167">Después, una vez finalizado el procesamiento, haga clic en "probar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-167">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="4ca5d-169">Escriba en "seleccionar el botón de inicio" en el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-169">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="4ca5d-170">No hemos agregado "Select" como acción en ninguno de nuestros grabaciones, pero si hace clic en "inspeccionar", el modelo reconoció "Select" como entidad de acción.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-170">We did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="4ca5d-172">Ahora, haga clic en "publicar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-172">Now, click "publish" in the top right.</span></span> <span data-ttu-id="4ca5d-173">Asegúrese de que la lista desplegable indica "producción" y haga clic en "publicar" también en la ventana emergente.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-173">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="4ca5d-175">Una vez publicada, aparecerá una barra verde en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-175">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="4ca5d-176">Haga clic en la barra verde para ir a la página "administrar".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-176">Click on the green bar to be taken to the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="4ca5d-178">Haga clic en "claves y puntos de conexión" en "configuración de la aplicación" a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-178">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="4ca5d-179">A continuación, establezca la lista desplegable "publicar en" como "producción".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-179">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="4ca5d-180">Establezca la zona horaria para que coincida con la suya y active la casilla para incluir todas las puntuaciones de intención previstas.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-180">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="4ca5d-181">Por último, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-181">Lastly, Click on "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="4ca5d-183">Seleccione inquilino en la primera lista desplegable y seleccione "pago por uso" en el menú desplegable nombre de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-183">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="4ca5d-184">En el nombre del recurso LUIS, elija el recurso que se creó anteriormente en los pasos 1-5.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-184">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="4ca5d-185">A continuación, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-185">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="4ca5d-187">Asegúrese de copiar y guardar la dirección URL del punto de conexión asociada con el recurso que acaba de asignar para que sea fácilmente accesible para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-187">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="4ca5d-188">En el nombre del inquilino, coloque su corporación o el perfil que creó para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-188">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="4ca5d-189">Ahora, abra la nueva aplicación en Unity y seleccione el objeto de Lunarcom_Base de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-189">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="4ca5d-190">Haga clic en "Agregar componente" en el panel Inspector y busque y seleccione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="4ca5d-190">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="4ca5d-192">En el campo punto de conexión Luis de "LunarcomIntentRecognizer" en el panel Inspector, escriba la dirección URL del punto de conexión que guardó en el paso 22.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-192">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="4ca5d-194">En el componente "LunarcomOfflineRecognizer" del panel Inspector, asegúrese de que está seleccionado "Deshabilitar" para "SimulateOfflineMode"; de lo contrario, no funcionará la prueba del programa.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-194">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="4ca5d-195">Presione el botón reproducir en el editor de Unity y haga clic en el botón Rocket para iniciar el reconocimiento de intenciones.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-195">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="4ca5d-196">En la frase, haga clic en el botón iniciar Rocket.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-196">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="4ca5d-197">La aplicación reconoció la función deseada y activó el botón Rocket.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-197">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="4ca5d-199">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="4ca5d-199">Congratulations</span></span>

<span data-ttu-id="4ca5d-200">En esta lección, hemos aprendido a agregar comandos de voz con tecnología de AI.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-200">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="4ca5d-201">Ahora el programa puede reconocer la intención de los usuarios, incluso si no son comandos de voz precisos.</span><span class="sxs-lookup"><span data-stu-id="4ca5d-201">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>
