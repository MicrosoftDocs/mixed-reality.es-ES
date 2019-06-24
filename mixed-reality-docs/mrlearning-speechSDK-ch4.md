## <a name="lesson-4"></a><span data-ttu-id="9fdbe-101">Lección 4</span><span class="sxs-lookup"><span data-stu-id="9fdbe-101">Lesson 4</span></span>

<span data-ttu-id="9fdbe-102">En el capítulo 4, exploramos la característica de intención de servicios de voz.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="9fdbe-103">Se configurará nuestro LUIS Azure Portal, nuestra intención/entidades y declaraciones de instalación, publicar nuestro recurso intención, conectar nuestra aplicación de Unity a nuestro recurso intención y realizar nuestra primera llamada de API de intención.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="9fdbe-104">Permitir que la máquina para permitir dictado, para ello, vaya a la configuración de Windows, seleccionar "privacy", a continuación, "voz" y, por último, "tinta & escribiendo" y activar los servicios de voz y escritura de sugerencias.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="9fdbe-108">Nota: para obtener información sobre cómo hacer esto en un Macbook/Mac, haga clic en [aquí](linkgoeshere).</span><span class="sxs-lookup"><span data-stu-id="9fdbe-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="9fdbe-109">Inicie sesión en el [Portal Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="9fdbe-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="9fdbe-110">Una vez que haya iniciado sesión, haga clic en crear un recurso y busque "Comprensión del lenguaje" y haga clic en ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="9fdbe-112">Seleccione el botón Crear, para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="9fdbe-113">Nombre del proyecto "Speech_SDK_Learning_Module" y seleccione "Pago por uso."</span><span class="sxs-lookup"><span data-stu-id="9fdbe-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="9fdbe-116">Seleccione su región.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-116">Select your Region.</span></span>  <span data-ttu-id="9fdbe-117">Para este tutorial, seleccione "(Estados Unidos) West US".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="9fdbe-118">A continuación, elija "F0" para el plan de tarifa.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="9fdbe-119">Ahora haga clic en "crear" (que se encuentra en la esquina inferior izquierda) para crear el recurso.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="9fdbe-120">Nota: una vez que ha hecho clic en "crear", tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="9fdbe-121">Una vez creado el recurso, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="9fdbe-122">Haga clic en esta notificación y seleccione "Vaya al recurso".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="9fdbe-123">En la página "Inicio rápido" del servicio "LUIS API", navegue hasta el primer paso, obtener las "claves" y haga clic en "claves" (también puede lograr esto, haga clic en el hipervínculo azul "claves", que se muestra en la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="9fdbe-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="9fdbe-124">Esto revelará su servicio, "Claves".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="9fdbe-125">Guardar una copia de una de las claves para que pueda usarlo más adelante en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="9fdbe-127">En la página "Inicio rápido" en la sección 2b, haga clic en "Portal de Language Understanding" (se muestra en la imagen anterior) para redirigir a la página Web que usará para crear su nuevo servicio dentro de la aplicación de LUIS.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="9fdbe-128">Nota: Cuando se alcanza "Portal de Language Understanding", es posible que debe iniciar sesión, si no está ya, con las mismas credenciales que el portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="9fdbe-129">Si se trata de la primera vez que usa a LUIS, deberá desplácese hacia abajo hasta la parte inferior de la página de bienvenida, para buscar y haga clic en el botón de la aplicación "Crear LUIS".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="9fdbe-130">Una vez iniciada la sesión, haga clic en mis aplicaciones (si no estás en esa sección actualmente).</span><span class="sxs-lookup"><span data-stu-id="9fdbe-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="9fdbe-131">A continuación, puede hacer clic en Crear nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-131">You can then click on Create new app.</span></span> <span data-ttu-id="9fdbe-132">Nombre de la nueva aplicación "Módulo de aprendizaje de Speech SDK".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="9fdbe-133">Agregue "Módulo de aprendizaje de Speech SDK" en el campo de descripción.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="9fdbe-134">A continuación, haga clic en "listo".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="9fdbe-137">Nota: Si la aplicación se debía para entender un idioma distinto del inglés, debe cambiar el "Culture" para el idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="9fdbe-138">Haga clic en "Build" que se encuentra en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="9fdbe-139">En recursos de aplicación de la izquierda, seleccione "Intenciones", a continuación, haga clic en "Crear nuevo intento" y denomínelo "PressButton."</span><span class="sxs-lookup"><span data-stu-id="9fdbe-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="9fdbe-141">Nota: es importante para los nombres de intenciones y entidades que se usa en este tutorial, dado que la aplicación Lunarcom hará referencia ellos por su nombre.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="9fdbe-142">Para otros proyectos, las convenciones de nomenclatura pueden ser todo lo que desee.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="9fdbe-143">Nota: ahora debe tener 2 intenciones - "PressButton" y "None".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="9fdbe-144">En los recursos de la aplicación de la izquierda, seleccione "Entidades" y haga clic en "Crear nueva entidad" y asígnele el nombre "Action" y mantenga el tipo de entidad como "Simple".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="9fdbe-146">Haga clic en "Crear nueva entidad" nuevo y asígnele el nombre "Target" y mantener así el tipo de entidad como "Simple".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="9fdbe-148">En los recursos de la aplicación de la izquierda, seleccione "Intenciones", a continuación, haga clic en su intención de "PressButton" que creó en el paso 10.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="9fdbe-150">Haga clic en la lista desplegable "Ver opciones" de la derecha y seleccione "Mostrar valores de entidad".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="9fdbe-152">Haga clic en el "Escriba un ejemplo..."</span><span class="sxs-lookup"><span data-stu-id="9fdbe-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="9fdbe-153">cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-153">textbox.</span></span> <span data-ttu-id="9fdbe-154">A continuación, escriba las siguientes declaraciones:</span><span class="sxs-lookup"><span data-stu-id="9fdbe-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="9fdbe-156">Haga clic en la lista desplegable "Ver opciones" de la derecha y seleccione "Mostrar los nombres de entidad".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="9fdbe-158">Asegúrese de que cada uno de los 10 grabaciones de voz tienen las siguientes etiquetas de entidad en los lugares siguientes en 1.) al hacer clic en las palabras que están etiquetadas incorrectamente y, en el menú emergente, seleccione "quitar la etiqueta" y 2.) al hacer clic en las palabras que deben estar indicadas y, en el menú emergente, seleccione la etiqueta adecuada.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="9fdbe-160">Ahora, para publicar el modelo, haga clic en "Train" en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="9fdbe-161">A continuación, una vez que haya terminado el procesamiento, haga clic en "Test" en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="9fdbe-163">Escriba en "seleccionar el botón de inicio" en el cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="9fdbe-164">Nota: no agregamos "select" como una acción en cualquiera de nuestras declaraciones - pero si hace clic en "Inspeccionar", el modelo reconoce "select" como una entidad de la acción.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="9fdbe-166">Ahora, haga clic en "publicar" en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="9fdbe-167">Asegúrese de que la lista desplegable dice "Producción" y haga clic en "publicar" en la ventana emergente también.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="9fdbe-169">Una vez publicado, debe aparecer una barra verde en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="9fdbe-170">Haga clic en la barra de color verde para ir a la página "Administrar".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="9fdbe-172">Haga clic en "Claves y los puntos de conexión" en "Configuración de aplicación" a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="9fdbe-173">A continuación, establezca la lista desplegable "Publish To" como "Producción".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="9fdbe-174">Establezca la zona horaria para que coincida con el suyo y Active la casilla para incluir todas las puntuaciones previstas de intención.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="9fdbe-175">Por último, haga clic en "Asignar recursos".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="9fdbe-177">Seleccione el inquilino de la primera lista desplegable y seleccione "Pago por uso" en la lista desplegable Nombre de la suscripción.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="9fdbe-178">En nombre de recurso de LUIS, elija el recurso que se crearon anteriormente en los pasos 1-5.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="9fdbe-179">A continuación, haga clic en "Asignar recursos".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="9fdbe-181">Nota: asegúrese de copiar y guardar la dirección URL del extremo asociado al recurso asignamos simplemente para que sea fácilmente accesible para la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="9fdbe-182">Nota: para el nombre del inquilino, incluya su corporación o el perfil que ha creado para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="9fdbe-183">Ahora, abra la nueva aplicación en Unity y seleccione el objeto Lunarcom_Base en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="9fdbe-184">Haga clic en "Agregar componente" en el panel de inspector y busque y seleccione "LunarcomIntentRecognizer."</span><span class="sxs-lookup"><span data-stu-id="9fdbe-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="9fdbe-186">En el campo de Luis Endpoint de "LunarcomIntentRecognizer" en el panel del inspector, escriba la dirección URL del extremo que guardó en el paso 22.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="9fdbe-188">Nota: En el componente "LunarcomOfflineRecognizer" en el panel del inspector, asegúrese de que "Deshabilitar" esté seleccionada para "SimulateOfflineMode" en caso contrario, probando el programa no funcionará.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="9fdbe-189">Presione el botón Reproducir en el Editor de Unity y haga clic en el botón de cohete para iniciar el reconocimiento de intenciones mediante.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="9fdbe-190">Auténtica la frase "Seleccione el botón de cohete de inicio".</span><span class="sxs-lookup"><span data-stu-id="9fdbe-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="9fdbe-191">Nota: La aplicación reconoce la función deseada y activa el botón rocket.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9fdbe-193">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="9fdbe-193">Congratulations</span></span>

<span data-ttu-id="9fdbe-194">¡Oficialmente, ha aprendido cómo agregar comandos de voz desde el programa de speech SDK!</span><span class="sxs-lookup"><span data-stu-id="9fdbe-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="9fdbe-195">Ahora su programa pueda reconocer los comandos de voz de todos los tipos de variantes.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="9fdbe-196">Comenzar a probarlo y divertirse un poco con ella.</span><span class="sxs-lookup"><span data-stu-id="9fdbe-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="9fdbe-197">Siguiente lección: Speech SDK lección 5</span><span class="sxs-lookup"><span data-stu-id="9fdbe-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

