---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485785"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="a5c12-104">4. Configuración del propósito y la comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="a5c12-104">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="a5c12-105">En esta lección, exploraremos la característica de intención del servicio de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="a5c12-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="a5c12-106">La característica de intención nos permite equipar nuestra aplicación con comandos de voz con tecnología de AI, donde los usuarios pueden indicar comandos de voz no específicos y seguir teniendo la intención entendida por el sistema.</span><span class="sxs-lookup"><span data-stu-id="a5c12-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="a5c12-107">En esta lección, se configurará nuestro portal de LUIS de Azure, se configurará nuestra intención/entidades/grabaciones, se publicará nuestro recurso de intención, se conectará la aplicación de Unity a nuestro recurso de intención y se realizará nuestra primera llamada de API de intención.</span><span class="sxs-lookup"><span data-stu-id="a5c12-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="a5c12-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a5c12-108">Objectives</span></span>

- <span data-ttu-id="a5c12-109">Obtenga información sobre cómo configurar la intención y el lenguaje natural en nuestra aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5c12-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="a5c12-110">Aprenda a configurar el portal de LUIS de Azure</span><span class="sxs-lookup"><span data-stu-id="a5c12-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="a5c12-111">Aprenda a configurar la intención, las entidades y los grabaciones en Azure</span><span class="sxs-lookup"><span data-stu-id="a5c12-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="a5c12-112">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="a5c12-112">Instructions</span></span>
1. <span data-ttu-id="a5c12-113">Permitir que la máquina habilite el dictado para ello, vaya a configuración de Windows, seleccione "privacidad", "voz" y, finalmente, "entrada manuscrita & escribir" y Active servicios de voz y sugerencias de escritura.</span><span class="sxs-lookup"><span data-stu-id="a5c12-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="a5c12-117">Inicie sesión en el [portal de Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="a5c12-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="a5c12-118">Una vez que haya iniciado sesión, haga clic en crear un recurso y busque "Language Understanding" y haga clic en entrar.</span><span class="sxs-lookup"><span data-stu-id="a5c12-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="a5c12-120">Seleccione el botón crear para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="a5c12-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="a5c12-121">Asigne al proyecto el nombre "Speech_SDK_Learning_Module" y seleccione "pago por uso".</span><span class="sxs-lookup"><span data-stu-id="a5c12-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="a5c12-124">Seleccione su región.</span><span class="sxs-lookup"><span data-stu-id="a5c12-124">Select your Region.</span></span>  <span data-ttu-id="a5c12-125">Para este tutorial, seleccione "(EE. UU.) oeste de EE. UU.".</span><span class="sxs-lookup"><span data-stu-id="a5c12-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="a5c12-126">A continuación, elija "F0" para el plan de tarifa.</span><span class="sxs-lookup"><span data-stu-id="a5c12-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="a5c12-127">Ahora haga clic en "crear" (que se encuentra en la esquina inferior izquierda) para crear el recurso.</span><span class="sxs-lookup"><span data-stu-id="a5c12-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="a5c12-128">Nota: una vez que haya hecho clic en "crear", tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="a5c12-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="a5c12-129">Una vez que se crea el recurso, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="a5c12-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="a5c12-130">Haga clic en esta notificación y seleccione "ir a recurso".</span><span class="sxs-lookup"><span data-stu-id="a5c12-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="a5c12-131">En la página "Inicio rápido" del servicio "LUIS API", navegue hasta el primer paso, tome las "teclas" y haga clic en "claves" (también puede conseguirlo haciendo clic en el hipervínculo azul "Keys", que se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="a5c12-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="a5c12-132">Esto revelará el servicio, "claves".</span><span class="sxs-lookup"><span data-stu-id="a5c12-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="a5c12-133">Guarde una copia de una de las claves para poder usarla más adelante en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5c12-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="a5c12-135">De nuevo en la página "Inicio rápido" de la sección 2b, haga clic en "portal de Language Understanding" (que se muestra en la imagen anterior) para redirigirse a la página web que usará para crear el nuevo servicio, dentro de la aplicación LUIS.</span><span class="sxs-lookup"><span data-stu-id="a5c12-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="a5c12-136">Nota: Al llegar al "portal de Language Understanding", es posible que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="a5c12-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="a5c12-137">Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la Página principal, para buscar y hacer clic en el botón "crear LUIS" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5c12-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="a5c12-138">Una vez que haya iniciado sesión, haga clic en mis aplicaciones (si no está en esa sección actualmente).</span><span class="sxs-lookup"><span data-stu-id="a5c12-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="a5c12-139">Después, puede hacer clic en crear nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5c12-139">You can then click on Create new app.</span></span> <span data-ttu-id="a5c12-140">Asigne a la nueva aplicación el nombre "módulo de aprendizaje de SDK de Speech".</span><span class="sxs-lookup"><span data-stu-id="a5c12-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="a5c12-141">Agregue "Speech SDK Learning Module" al campo Descripción.</span><span class="sxs-lookup"><span data-stu-id="a5c12-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="a5c12-142">A continuación, haga clic en "listo".</span><span class="sxs-lookup"><span data-stu-id="a5c12-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="a5c12-145">Tenga en cuenta Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la "referencia cultural" al idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="a5c12-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="a5c12-146">Haga clic en "compilar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="a5c12-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="a5c12-147">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en "crear nuevo intento" y asígnele el nombre "PressButton".</span><span class="sxs-lookup"><span data-stu-id="a5c12-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="a5c12-149">Nota: Es importante usar los nombres de los intentos y las entidades que se usan en este tutorial, ya que la aplicación Lunarcom hará referencia a ellos por su nombre.</span><span class="sxs-lookup"><span data-stu-id="a5c12-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="a5c12-150">Nota: ahora debe tener 2 intenciones: "PressButton" y "none".</span><span class="sxs-lookup"><span data-stu-id="a5c12-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="a5c12-151">En activos de la aplicación de la izquierda, seleccione "entidades", haga clic en "crear nueva entidad" y asígnele el nombre "acción" y mantenga el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="a5c12-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="a5c12-153">Vuelva a hacer clic en "crear nueva entidad" y asígnele el nombre "destino" y conserve también el tipo de entidad como "simple".</span><span class="sxs-lookup"><span data-stu-id="a5c12-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="a5c12-155">En recursos de la aplicación a la izquierda, seleccione "intentos" y, a continuación, haga clic en el intento de "PressButton" que creó en el paso 10.</span><span class="sxs-lookup"><span data-stu-id="a5c12-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="a5c12-157">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar valores de entidad".</span><span class="sxs-lookup"><span data-stu-id="a5c12-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="a5c12-159">Haga clic en el "Escriba un ejemplo..."</span><span class="sxs-lookup"><span data-stu-id="a5c12-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="a5c12-160">mytextbox.</span><span class="sxs-lookup"><span data-stu-id="a5c12-160">textbox.</span></span> <span data-ttu-id="a5c12-161">A continuación, escriba el siguiente grabaciones:</span><span class="sxs-lookup"><span data-stu-id="a5c12-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="a5c12-163">Haga clic en la lista desplegable "ver opciones" de la derecha y seleccione "Mostrar nombres de entidad".</span><span class="sxs-lookup"><span data-stu-id="a5c12-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="a5c12-165">Asegúrese de que cada uno de los 10 grabaciones tenga las siguientes etiquetas de entidad en los lugares siguientes en 1). al hacer clic en palabras que no están etiquetadas y, en el menú emergente, seleccionando "quitar etiqueta" y 2). al hacer clic en las palabras que deben etiquetarse y, en el menú emergente, seleccione la etiqueta adecuada.</span><span class="sxs-lookup"><span data-stu-id="a5c12-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="a5c12-167">Ahora, para publicar el modelo, haga clic en "entrenar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="a5c12-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="a5c12-168">Después, una vez finalizado el procesamiento, haga clic en "probar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="a5c12-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="a5c12-170">Escriba en "seleccionar el botón de inicio" en el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="a5c12-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="a5c12-171">Nota: no hemos agregado "Select" como acción en ninguno de nuestros grabaciones, pero si hace clic en "inspeccionar", el modelo reconoció "Select" como entidad de acción.</span><span class="sxs-lookup"><span data-stu-id="a5c12-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="a5c12-173">Ahora, haga clic en "publicar" en la parte superior derecha.</span><span class="sxs-lookup"><span data-stu-id="a5c12-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="a5c12-174">Asegúrese de que la lista desplegable indica "producción" y haga clic en "publicar" también en la ventana emergente.</span><span class="sxs-lookup"><span data-stu-id="a5c12-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="a5c12-176">Una vez publicada, aparecerá una barra verde en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="a5c12-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="a5c12-177">Haga clic en la barra verde para ir a la página "administrar".</span><span class="sxs-lookup"><span data-stu-id="a5c12-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="a5c12-179">Haga clic en "claves y puntos de conexión" en "configuración de la aplicación" a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="a5c12-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="a5c12-180">A continuación, establezca la lista desplegable "publicar en" como "producción".</span><span class="sxs-lookup"><span data-stu-id="a5c12-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="a5c12-181">Establezca la zona horaria para que coincida con la suya y active la casilla para incluir todas las puntuaciones de intención previstas.</span><span class="sxs-lookup"><span data-stu-id="a5c12-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="a5c12-182">Por último, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="a5c12-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="a5c12-184">Seleccione inquilino en la primera lista desplegable y seleccione "pago por uso" en el menú desplegable nombre de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="a5c12-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="a5c12-185">En el nombre del recurso LUIS, elija el recurso que se creó anteriormente en los pasos 1-5.</span><span class="sxs-lookup"><span data-stu-id="a5c12-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="a5c12-186">A continuación, haga clic en "asignar recurso".</span><span class="sxs-lookup"><span data-stu-id="a5c12-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="a5c12-188">Nota: Asegúrese de copiar y guardar la dirección URL del punto de conexión asociada con el recurso que acaba de asignar para que sea fácilmente accesible para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="a5c12-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="a5c12-189">Nota: En el nombre del inquilino, coloque su corporación o el perfil que creó para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5c12-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="a5c12-190">Ahora, abra la nueva aplicación en Unity y seleccione el objeto Lunarcom_Base en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="a5c12-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="a5c12-191">Haga clic en "Agregar componente" en el panel Inspector y busque y seleccione "LunarcomIntentRecognizer".</span><span class="sxs-lookup"><span data-stu-id="a5c12-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="a5c12-193">En el campo punto de conexión Luis de "LunarcomIntentRecognizer" en el panel Inspector, escriba la dirección URL del punto de conexión que guardó en el paso 22.</span><span class="sxs-lookup"><span data-stu-id="a5c12-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="a5c12-195">Nota: En el componente "LunarcomOfflineRecognizer" del panel Inspector, asegúrese de que está seleccionado "Deshabilitar" para "SimulateOfflineMode"; de lo contrario, no funcionará la prueba del programa.</span><span class="sxs-lookup"><span data-stu-id="a5c12-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="a5c12-196">Presione el botón reproducir en el editor de Unity y haga clic en el botón Rocket para iniciar el reconocimiento de intenciones.</span><span class="sxs-lookup"><span data-stu-id="a5c12-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="a5c12-197">En la frase, haga clic en el botón iniciar Rocket.</span><span class="sxs-lookup"><span data-stu-id="a5c12-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="a5c12-198">Nota: La aplicación reconoció la función deseada y activó el botón Rocket.</span><span class="sxs-lookup"><span data-stu-id="a5c12-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a5c12-200">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="a5c12-200">Congratulations</span></span>

<span data-ttu-id="a5c12-201">En esta lección, hemos aprendido a agregar comandos de voz con tecnología de AI.</span><span class="sxs-lookup"><span data-stu-id="a5c12-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="a5c12-202">Ahora el programa puede reconocer la intención de los usuarios, incluso si no son comandos de voz precisos.</span><span class="sxs-lookup"><span data-stu-id="a5c12-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

