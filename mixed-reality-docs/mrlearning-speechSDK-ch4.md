---
title: 'Tutoriales de Azure Speech Services: 4. Configuración del propósito y la comprensión del lenguaje natural'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 5ca2df56eee3ae41d97de4e8b1e88a39d4d36718
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701951"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="1c60c-105">4. Configuración del propósito y la comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="1c60c-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="1c60c-106">En esta lección, exploraremos la característica de intención del servicio de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="1c60c-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="1c60c-107">La característica de intención nos permite equipar nuestra aplicación con comandos de voz con tecnología de AI, donde los usuarios pueden indicar comandos de voz no específicos y seguir teniendo la intención entendida por el sistema.</span><span class="sxs-lookup"><span data-stu-id="1c60c-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="1c60c-108">En esta lección, se configurará nuestro portal de LUIS de Azure, se configurará nuestra intención/entidades/grabaciones, se publicará nuestro recurso de intención, se conectará la aplicación de Unity a nuestro recurso de intención y se realizará nuestra primera llamada de API de intención.</span><span class="sxs-lookup"><span data-stu-id="1c60c-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="1c60c-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1c60c-109">Objectives</span></span>

- <span data-ttu-id="1c60c-110">Obtenga información sobre cómo configurar la intención y el lenguaje natural en nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="1c60c-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="1c60c-111">Aprenda a configurar el portal de LUIS de Azure</span><span class="sxs-lookup"><span data-stu-id="1c60c-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="1c60c-112">Aprenda a configurar la intención, las entidades y los grabaciones en Azure</span><span class="sxs-lookup"><span data-stu-id="1c60c-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="1c60c-113">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="1c60c-113">Instructions</span></span>
1. <span data-ttu-id="1c60c-114">Permitir que la máquina habilite el dictado para ello, vaya a configuración de Windows, seleccione "privacidad", "voz" y, finalmente, "entrada manuscrita & escribir" y Active servicios de voz y sugerencias de escritura.</span><span class="sxs-lookup"><span data-stu-id="1c60c-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="1c60c-118">Inicie sesión en el [portal de Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="1c60c-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="1c60c-119">Una vez que haya iniciado sesión, haga clic en crear un recurso y busque "Language Understanding" y haga clic en entrar.</span><span class="sxs-lookup"><span data-stu-id="1c60c-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="1c60c-121">Seleccione el botón crear para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1c60c-121">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="1c60c-122">Asigne al proyecto el nombre "Speech_SDK_Learning_Module" y seleccione "pago por uso".</span><span class="sxs-lookup"><span data-stu-id="1c60c-122">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="1c60c-125">Seleccione su región.</span><span class="sxs-lookup"><span data-stu-id="1c60c-125">Select your Region.</span></span>  <span data-ttu-id="1c60c-126">Para este tutorial, seleccione "(EE. UU.) oeste de EE. UU.".</span><span class="sxs-lookup"><span data-stu-id="1c60c-126">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="1c60c-127">A continuación, elija "F0" para el plan de tarifa.</span><span class="sxs-lookup"><span data-stu-id="1c60c-127">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="1c60c-128">Ahora haga clic en "crear" (que se encuentra en la esquina inferior izquierda) para crear el recurso.</span><span class="sxs-lookup"><span data-stu-id="1c60c-128">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="1c60c-129">Nota: una vez que haya hecho clic en "crear", tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="1c60c-129">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="1c60c-130">Una vez que se crea el recurso, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="1c60c-130">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="1c60c-131">Haga clic en esta notificación y seleccione "ir a recurso".</span><span class="sxs-lookup"><span data-stu-id="1c60c-131">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="1c60c-132">En la página "Inicio rápido" del servicio "LUIS API", navegue hasta el primer paso, tome las "teclas" y haga clic en "claves" (también puede conseguirlo haciendo clic en el hipervínculo azul "Keys", que se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="1c60c-132">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="1c60c-133">Esto revelará el servicio, "claves".</span><span class="sxs-lookup"><span data-stu-id="1c60c-133">This will reveal your service, "Keys."</span></span> <span data-ttu-id="1c60c-134">Guarde una copia de una de las claves para poder usarla más adelante en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1c60c-134">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="1c60c-136">De nuevo en la página "Inicio rápido" de la sección 2b, haga clic en "portal de Language Understanding" (que se muestra en la imagen anterior) para redirigirse a la página web que usará para crear el nuevo servicio, dentro de la aplicación LUIS.</span><span class="sxs-lookup"><span data-stu-id="1c60c-136">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="1c60c-137">Nota: Al llegar al "portal de Language Understanding", es posible que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="1c60c-137">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="1c60c-138">Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la Página principal, para buscar y hacer clic en el botón "crear LUIS" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1c60c-138">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="1c60c-139">Una vez que haya iniciado sesión, haga clic en mis aplicaciones (si no está en esa sección actualmente).</span><span class="sxs-lookup"><span data-stu-id="1c60c-139">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="1c60c-140">Después, puede hacer clic en crear nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="1c60c-140">You can then click on Create new app.</span></span> <span data-ttu-id="1c60c-141">Asigne a la nueva aplicación el nombre "módulo de aprendizaje de SDK de Speech".</span><span class="sxs-lookup"><span data-stu-id="1c60c-141">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="1c60c-142">Agregue "Speech SDK Learning Module" al campo Descripción.</span><span class="sxs-lookup"><span data-stu-id="1c60c-142">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="1c60c-143">A continuación, haga clic en "listo".</span><span class="sxs-lookup"><span data-stu-id="1c60c-143">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="1c60c-146">Tenga en cuenta Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la "referencia cultural" al idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="1c60c-146">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="1c60c-147">Haga clic en "compilar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="1c60c-147">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="1c60c-148">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en "crear nuevo intento" y asígnele el nombre "PressButton".</span><span class="sxs-lookup"><span data-stu-id="1c60c-148">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="1c60c-150">Nota: Es importante usar los nombres de los intentos y las entidades que se usan en este tutorial, ya que la aplicación Lunarcom hará referencia a ellos por su nombre.</span><span class="sxs-lookup"><span data-stu-id="1c60c-150">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="1c60c-151">Nota: ahora debe tener 2 intenciones: "PressButton" y "none".</span><span class="sxs-lookup"><span data-stu-id="1c60c-151">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="1c60c-152">En activos de la aplicación de la izquierda, seleccione "entidades", haga clic en "crear nueva entidad" y asígnele el nombre "acción" y mantenga el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="1c60c-152">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="1c60c-154">Vuelva a hacer clic en "crear nueva entidad" y asígnele el nombre "destino" y conserve también el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="1c60c-154">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="1c60c-156">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en el intento de "PressButton" que creó en el paso 10.</span><span class="sxs-lookup"><span data-stu-id="1c60c-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="1c60c-158">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar valores de entidad".</span><span class="sxs-lookup"><span data-stu-id="1c60c-158">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="1c60c-160">Haga clic en el "Escriba un ejemplo..."</span><span class="sxs-lookup"><span data-stu-id="1c60c-160">Click on the “Enter an example…”</span></span> <span data-ttu-id="1c60c-161">mytextbox.</span><span class="sxs-lookup"><span data-stu-id="1c60c-161">textbox.</span></span> <span data-ttu-id="1c60c-162">A continuación, escriba el siguiente grabaciones:</span><span class="sxs-lookup"><span data-stu-id="1c60c-162">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="1c60c-164">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar nombres de entidad".</span><span class="sxs-lookup"><span data-stu-id="1c60c-164">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="1c60c-166">Asegúrese de que cada uno de los 10 grabaciones tenga las siguientes etiquetas de entidad en los lugares siguientes en 1). al hacer clic en palabras que no están etiquetadas y, en el menú emergente, seleccionando "quitar etiqueta" y 2). al hacer clic en las palabras que deben etiquetarse y, en el menú emergente, seleccione la etiqueta adecuada.</span><span class="sxs-lookup"><span data-stu-id="1c60c-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="1c60c-168">Ahora, para publicar el modelo, haga clic en "entrenar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="1c60c-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="1c60c-169">Después, una vez finalizado el procesamiento, haga clic en "probar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="1c60c-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="1c60c-171">Escriba en "seleccionar el botón de inicio" en el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="1c60c-171">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="1c60c-172">Nota: no hemos agregado "Select" como acción en ninguno de nuestros grabaciones, pero si hace clic en "inspeccionar", el modelo reconoció "Select" como entidad de acción.</span><span class="sxs-lookup"><span data-stu-id="1c60c-172">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="1c60c-174">Ahora, haga clic en "publicar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="1c60c-174">Now, click "publish" in the top right.</span></span> <span data-ttu-id="1c60c-175">Asegúrese de que la lista desplegable indica "producción" y haga clic en "publicar" también en la ventana emergente.</span><span class="sxs-lookup"><span data-stu-id="1c60c-175">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="1c60c-177">Una vez publicada, aparecerá una barra verde en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="1c60c-177">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="1c60c-178">Haga clic en la barra verde para ir a la página "administrar".</span><span class="sxs-lookup"><span data-stu-id="1c60c-178">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="1c60c-180">Haga clic en "claves y puntos de conexión" en "configuración de la aplicación" a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="1c60c-180">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="1c60c-181">A continuación, establezca la lista desplegable "publicar en" como "producción".</span><span class="sxs-lookup"><span data-stu-id="1c60c-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="1c60c-182">Establezca la zona horaria para que coincida con la suya y active la casilla para incluir todas las puntuaciones de intención previstas.</span><span class="sxs-lookup"><span data-stu-id="1c60c-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="1c60c-183">Por último, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="1c60c-183">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="1c60c-185">Seleccione inquilino en la primera lista desplegable y seleccione "pago por uso" en el menú desplegable nombre de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="1c60c-185">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="1c60c-186">En el nombre del recurso LUIS, elija el recurso que se creó anteriormente en los pasos 1-5.</span><span class="sxs-lookup"><span data-stu-id="1c60c-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="1c60c-187">A continuación, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="1c60c-187">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="1c60c-189">Nota: Asegúrese de copiar y guardar la dirección URL del punto de conexión asociada con el recurso que acaba de asignar para que sea fácilmente accesible para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="1c60c-189">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="1c60c-190">Nota: En el nombre del inquilino, coloque su corporación o el perfil que creó para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="1c60c-190">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="1c60c-191">Ahora, abra la nueva aplicación en Unity y seleccione el objeto Lunarcom_Base en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="1c60c-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="1c60c-192">Haga clic en "Agregar componente" en el panel Inspector y busque y seleccione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="1c60c-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="1c60c-194">En el campo punto de conexión Luis de "LunarcomIntentRecognizer" en el panel Inspector, escriba la dirección URL del punto de conexión que guardó en el paso 22.</span><span class="sxs-lookup"><span data-stu-id="1c60c-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="1c60c-196">Nota: En el componente "LunarcomOfflineRecognizer" del panel Inspector, asegúrese de que está seleccionado "Deshabilitar" para "SimulateOfflineMode"; de lo contrario, no funcionará la prueba del programa.</span><span class="sxs-lookup"><span data-stu-id="1c60c-196">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="1c60c-197">Presione el botón reproducir en el editor de Unity y haga clic en el botón Rocket para iniciar el reconocimiento de intenciones.</span><span class="sxs-lookup"><span data-stu-id="1c60c-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="1c60c-198">En la frase, haga clic en el botón iniciar Rocket.</span><span class="sxs-lookup"><span data-stu-id="1c60c-198">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="1c60c-199">Nota: La aplicación reconoció la función deseada y activó el botón Rocket.</span><span class="sxs-lookup"><span data-stu-id="1c60c-199">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1c60c-201">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="1c60c-201">Congratulations</span></span>

<span data-ttu-id="1c60c-202">En esta lección, hemos aprendido a agregar comandos de voz con tecnología de AI.</span><span class="sxs-lookup"><span data-stu-id="1c60c-202">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="1c60c-203">Ahora el programa puede reconocer la intención de los usuarios, incluso si no son comandos de voz precisos.</span><span class="sxs-lookup"><span data-stu-id="1c60c-203">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

