---
title: 'Módulo SpeechSDK de aprendizaje MR: reconocimiento de voz y transcripción'
description: Complete este curso para aprender a implementar el SDK de voz de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c1ca44ffcaa8dced988b829d9875ebe304f14a12
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460356"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="63370-104">1. Integración y uso del reconocimiento de voz y la transcripción</span><span class="sxs-lookup"><span data-stu-id="63370-104">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="63370-105">En este tutorial se crea una aplicación de realidad mixta que explora el uso de Azure Cognitive Services Speech SDK con HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63370-105">This tutorial creates a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="63370-106">Una vez finalizada esta serie de tutoriales, podrá usar el micrófono del dispositivo para transcribir voz en texto en tiempo real, traducir su voz en otros idiomas y aprovechar la característica de intención del SDK de Speech para comprender los comandos de voz con inteligencia artificial.</span><span class="sxs-lookup"><span data-stu-id="63370-106">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="63370-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="63370-107">Objectives</span></span>

- <span data-ttu-id="63370-108">Obtenga información sobre cómo integrar el SDK de voz de Azure en una aplicación de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63370-108">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="63370-109">Obtener información sobre cómo usar comandos de voz</span><span class="sxs-lookup"><span data-stu-id="63370-109">Learn how to use voice commands</span></span>
- <span data-ttu-id="63370-110">Aprenda a usar las funcionalidades de voz a texto</span><span class="sxs-lookup"><span data-stu-id="63370-110">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="63370-111">Instrucciones</span><span class="sxs-lookup"><span data-stu-id="63370-111">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="63370-112">Introducción</span><span class="sxs-lookup"><span data-stu-id="63370-112">Getting Started</span></span>

1. <span data-ttu-id="63370-113">Inicie Unity y cree un nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="63370-113">Start Unity, and create a new project.</span></span> <span data-ttu-id="63370-114">Escriba el nombre del proyecto de Speech SDK Learning Module.</span><span class="sxs-lookup"><span data-stu-id="63370-114">Enter the project name Speech SDK Learning Module.</span></span> <span data-ttu-id="63370-115">Elija una ubicación donde guardar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="63370-115">Choose a location for where to save your project.</span></span> <span data-ttu-id="63370-116">A continuación, haga clic en crear proyecto.</span><span class="sxs-lookup"><span data-stu-id="63370-116">Then click Create Project.</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="63370-118">Nota: Asegúrese de que la plantilla está establecida en 3D, tal como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="63370-118">Note: Ensure that the template is set to 3D, as shown in the image above.</span></span>

2. <span data-ttu-id="63370-119">Descargue el paquete de Unity del [Kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) y guárdelo en una carpeta de su equipo.</span><span class="sxs-lookup"><span data-stu-id="63370-119">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package, and save it to a folder on your PC.</span></span> <span data-ttu-id="63370-120">Importe el paquete en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="63370-120">Import the package into your Unity project.</span></span> <span data-ttu-id="63370-121">Para obtener instrucciones detalladas sobre cómo hacerlo, consulte la [Lección 1 del módulo base](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="63370-121">For detailed instructions on how to do this, please see [Base Module Lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="63370-122">Descargue e importe el [SDK de voz](https://aka.ms/csspeech/unitypackage) de Azure para el paquete de activos de Unity.</span><span class="sxs-lookup"><span data-stu-id="63370-122">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for the Unity asset package.</span></span> <span data-ttu-id="63370-123">Importe el paquete del SDK de Speech; para ello, haga clic en recursos, seleccione Importar paquete y, a continuación, seleccione paquete personalizado.</span><span class="sxs-lookup"><span data-stu-id="63370-123">Import the Speech SDK package by clicking on Assets, selecting Import package, then selecting Custom Package.</span></span> <span data-ttu-id="63370-124">Busque el paquete del SDK de Speech descargado anteriormente y ábralo para comenzar el proceso de importación.</span><span class="sxs-lookup"><span data-stu-id="63370-124">Find the Speech SDK package downloaded earlier, and open it to begin the importing process.</span></span> 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="63370-127">En la siguiente ventana emergente, haga clic en importar para iniciar la importación del paquete del SDK de Speech.</span><span class="sxs-lookup"><span data-stu-id="63370-127">In the next pop-up window, click Import to begin importing the Speech SDK package.</span></span> <span data-ttu-id="63370-128">Asegúrese de que todos los elementos se comprueban como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="63370-128">Ensure all items are checked as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. <span data-ttu-id="63370-130">Descargue el paquete de activos del módulo Speech SDK, también conocido como paquete Lunarcom haciendo clic en [este vínculo](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span><span class="sxs-lookup"><span data-stu-id="63370-130">Download the Speech SDK Module asset pack, also know as Lunarcom package by clicking on [this link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2).</span></span> <span data-ttu-id="63370-131">El paquete de recursos Lunarcom es una colección de recursos y scripts desarrollados para esta serie de lecciones con el fin de presentar un uso práctico del SDK de voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="63370-131">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="63370-132">Se trata de un terminal de comandos de voz que, en última instancia, se basará en la experiencia de ensamblado del módulo lunar desarrollada en el [tutorial del módulo base.](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="63370-132">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>

6. <span data-ttu-id="63370-133">Importe el paquete de recursos Lunarcom en el proyecto de Unity siguiendo unos pasos similares que se han llevado a cabo para importar el kit de herramientas de realidad mixta y el SDK de Speech.</span><span class="sxs-lookup"><span data-stu-id="63370-133">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="63370-134">Configure el kit de herramientas de realidad mixta (MRTK).</span><span class="sxs-lookup"><span data-stu-id="63370-134">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="63370-135">Para ello, haga clic en el panel del kit de herramientas de realidad mixta en la parte superior de la ventana y, a continuación, seleccione Agregar a escena y configurar.</span><span class="sxs-lookup"><span data-stu-id="63370-135">To do this, click on the Mixed Reality Toolkit panel in the top of your window, and then select Add to Scene and Configure.</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. <span data-ttu-id="63370-139">La escena ahora tiene varios elementos nuevos en ella desde MRTK.</span><span class="sxs-lookup"><span data-stu-id="63370-139">Your scene now has several new items in it from the MRTK.</span></span> <span data-ttu-id="63370-140">Guarde la escena en un nombre diferente; para ello, haga clic en "archivo", "guardar como" y asigne el nombre SpeechScene a la escena.</span><span class="sxs-lookup"><span data-stu-id="63370-140">Save your scene under a different name by clicking on "file," then "save as" and name your scene SpeechScene.</span></span> 

> <span data-ttu-id="63370-141">Nota: Si presiona reproducir en la escena después de agregar el MRTK al proyecto y no entra en el modo de reproducción, es posible que tenga que reiniciar Unity.</span><span class="sxs-lookup"><span data-stu-id="63370-141">Note: If you press Play on your scene after you add the MRTK to your project, and it doesn't enter play mode, you might need to restart Unity.</span></span> 

9. <span data-ttu-id="63370-142">Con el objeto MixedRealityToolkit seleccionado en la jerarquía, haga clic en copiar y personalizar en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="63370-142">With the MixedRealityToolkit object selected in your hierarchy, click Copy and Customize in the Inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="63370-144">También en el panel Inspector (con el objeto MixedRealityToolkit seleccionado en la jerarquía), deshabilite el sistema de diagnósticos desactivando la casilla situada a la derecha de habilitar el sistema de diagnósticos.</span><span class="sxs-lookup"><span data-stu-id="63370-144">Also in the Inspector panel (with the MixedRealityToolkit object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of Enable Diagnostics System.</span></span>

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. <span data-ttu-id="63370-146">Para habilitar los comandos de voz, seleccione el perfil de MRTK recién creado para personalizarlo.</span><span class="sxs-lookup"><span data-stu-id="63370-146">To enable voice commands, select the newly created MRTK profile to customize.</span></span> <span data-ttu-id="63370-147">En este tutorial, vamos a usar los comandos de voz de entrada para el reconocimiento de voz y la transcripción.</span><span class="sxs-lookup"><span data-stu-id="63370-147">In this tutorial, we are using the input speech commands for speech recognition and transcription.</span></span> <span data-ttu-id="63370-148">Permite clonar el perfil de entrada para realizar cambios en la configuración de voz.</span><span class="sxs-lookup"><span data-stu-id="63370-148">Lets clone the input profile to make changes to speech settings.</span></span>

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. <span data-ttu-id="63370-151">Una vez que se clona el perfil de entrada, vaya a comandos de voz y Clone los comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="63370-151">Once the input profile is cloned, go to speech commands and clone the speech commands.</span></span>

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. <span data-ttu-id="63370-154">Ahora, en comandos de voz, vaya a "configuración general" y establezca "iniciar comportamiento" en "Inicio manual".</span><span class="sxs-lookup"><span data-stu-id="63370-154">Now under speech commands, go to "General Settings" and set "Start Behavior" to "Manual Start"</span></span>

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. <span data-ttu-id="63370-156">En el panel Proyecto, expanda la carpeta Lunarcom y arrastre Lunarcom_Base recurso prefabricado a la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="63370-156">In the Project panel, expand the Lunarcom folder and drag the Lunarcom_Base prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. <span data-ttu-id="63370-158">Seleccione el objeto Lunarcom_Base en la jerarquía y asegúrese de que la posición está establecida en x = 0, y = 0 y z = 0, así como en la rotación establecida en x = 0, y = 0 y z = 0.</span><span class="sxs-lookup"><span data-stu-id="63370-158">Select the Lunarcom_Base object in your hierarchy, and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="63370-159">Establezca la escala en Read x = 0.008, y = 0.008 y z = 0,01.</span><span class="sxs-lookup"><span data-stu-id="63370-159">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. <span data-ttu-id="63370-161">Haga clic en Agregar componente y busque y seleccione LunarcomController.</span><span class="sxs-lookup"><span data-stu-id="63370-161">Click Add Component, and search for and select LunarcomController.</span></span> <span data-ttu-id="63370-162">Este script se incluye en el módulo de recursos Lunarcom que importó en el paso 6.</span><span class="sxs-lookup"><span data-stu-id="63370-162">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. <span data-ttu-id="63370-164">Para conectar la aplicación a Azure Cognitive Services, debe especificar una clave de suscripción (también conocida como clave de API) para el servicio de voz.</span><span class="sxs-lookup"><span data-stu-id="63370-164">To connect our applicaiton to Azure Cognitive Services, you must enter a subscription key (also known as an API Key), for the Speech Service.</span></span> <span data-ttu-id="63370-165">Siga las instrucciones que se indican [aquí](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) para obtener una clave de suscripción gratuita.</span><span class="sxs-lookup"><span data-stu-id="63370-165">Follow the instructions at [here](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="63370-166">Una vez que obtenga la clave de suscripción, escríbala en el campo clave de la API del servicio de voz del componente LunarcomController en el panel Inspector, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="63370-166">Once you obtain the subscription key, enter it into the Speech Service API Key field of the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

18. <span data-ttu-id="63370-167">Escriba la región que eligió al suscribirse a la clave de suscripción en el campo región del servicio de voz del componente LunarcomController del panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="63370-167">Enter the Region that you chose when you signed up for the subscription key into the Speech Service Region field of the LunarcomController component in the Inspector panel.</span></span> <span data-ttu-id="63370-168">Por ejemplo, para la región "oeste de EE. UU.", escriba "westus"</span><span class="sxs-lookup"><span data-stu-id="63370-168">For example, for the region "West US" type in "westus"</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. <span data-ttu-id="63370-170">En la jerarquía, expanda el objeto Lunarcom_Base haciendo clic en la flecha situada a su izquierda.</span><span class="sxs-lookup"><span data-stu-id="63370-170">In your hierarchy, expand the Lunarcom_Base object by clicking the arrow to the left of it.</span></span> <span data-ttu-id="63370-171">A continuación, haga lo mismo para su objeto secundario, "terminal, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="63370-171">Then do the same for its child object, "Terminal, as shown in the image below.</span></span>

20. <span data-ttu-id="63370-172">Mientras Lunarcom_Base está seleccionado, haga clic y arrastre Lunarcom Text desde la jerarquía hasta la ranura del texto de salida en el componente LunarcomController del panel Inspector, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="63370-172">While Lunarcom_Base is selected, click and drag Lunarcom Text from the hierarchy to the Output Text slot in the LunarcomController component in the Inspector panel as shown in the image below.</span></span>

21. <span data-ttu-id="63370-173">Haga lo mismo con el objeto terminal en la ranura de terminal y el objeto de luz de conexión con la ranura del controlador de luz de conexión.</span><span class="sxs-lookup"><span data-stu-id="63370-173">Do the same thing with the Terminal object into the Terminal slot and the Connection Light object to the Connection Light Controller slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. <span data-ttu-id="63370-175">Haga clic en la flecha situada junto a la sección botones de Lunarcom del script LunarcomController en el panel Inspector y cambie el tamaño a 3.</span><span class="sxs-lookup"><span data-stu-id="63370-175">Click the arrow next to the Lunarcom Buttons section of the LunarcomController script in the Inspector panel, and change the size to 3.</span></span> <span data-ttu-id="63370-176">Presione entrar o entrar.</span><span class="sxs-lookup"><span data-stu-id="63370-176">Press Enter or Return.</span></span> <span data-ttu-id="63370-177">Esto hace que aparezcan tres nuevos campos de elemento.</span><span class="sxs-lookup"><span data-stu-id="63370-177">This causes three new Element fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. <span data-ttu-id="63370-179">Para expandir los botones de Lunarcom, haga clic en la flecha situada junto a él en la jerarquía y, con el mismo proceso anterior, arrastre los GameObjects MIC, Satellite y Rocket a las referencias del elemento 0, 1 y 2, respectivamente, en el componente LunarcomController de la Panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="63370-179">Expand the Lunarcom Buttons by clicking the arrow next to it in your hierarchy, and using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references, respectively, in the LunarcomController component in the Inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. <span data-ttu-id="63370-181">Seleccione el objeto Lunarcom_Base "en la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="63370-181">Select the Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="63370-182">Haga clic en Agregar componente en el panel Inspector y busque y seleccione LunarcomWakeWordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="63370-182">Click Add Component in the inspector panel, and search for and select LunarcomWakeWordRecognizer.</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. <span data-ttu-id="63370-184">En la ranura de reactivación de la palabra, escriba activar terminal.</span><span class="sxs-lookup"><span data-stu-id="63370-184">In the Wake Word slot, type in Activate Terminal.</span></span> <span data-ttu-id="63370-185">En la casilla descartar palabra, escriba descartar terminal.</span><span class="sxs-lookup"><span data-stu-id="63370-185">In the Dismiss Word slot, type Dismiss Terminal.</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a><span data-ttu-id="63370-187">Compilación de la aplicación para el dispositivo</span><span class="sxs-lookup"><span data-stu-id="63370-187">Build your application to your device</span></span>

1. <span data-ttu-id="63370-188">Vuelva a abrir la ventana de configuración de compilación. para ello, vaya a archivo > configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="63370-188">Open the build settings window again by going to File>Build Settings.</span></span>

![Lesson1 Chapter5 paso 1](images/Lesson1Chapter5Step1.JPG)

2. <span data-ttu-id="63370-190">Comprueba que la escena que deseas probar está en la lista "Scenes in Build" (Escenas en compilación) haciendo clic en el botón "Add Open Scenes" (Agregar escenas abiertas).</span><span class="sxs-lookup"><span data-stu-id="63370-190">Ensure the scene you want to try is in the “Scenes in Build” list by clicking on the “Add Open Scenes” button.</span></span>

3. <span data-ttu-id="63370-191">Presiona el botón Build (Compilar) para comenzar el proceso de compilación.</span><span class="sxs-lookup"><span data-stu-id="63370-191">Press the Build button to begin the build process.</span></span>

![Lesson1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. <span data-ttu-id="63370-193">Crea y asigna un nombre a una nueva carpeta para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="63370-193">Create and name a new folder for your application.</span></span> <span data-ttu-id="63370-194">En la imagen siguiente, se ha creado una carpeta con el nombre "App" (Aplicación) para contener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="63370-194">In the image below, a folder with the name “App” was created to contain the application.</span></span> <span data-ttu-id="63370-195">Haz clic en "Select Folder" (Seleccionar carpeta) para empezar a compilar la carpeta recién creada.</span><span class="sxs-lookup"><span data-stu-id="63370-195">Click “Select Folder” to begin building to the newly created folder.</span></span> <span data-ttu-id="63370-196">Una vez finalizada la compilación, puedes cerrar la ventana "Build Settings" (Configuración de compilación) en Unity.</span><span class="sxs-lookup"><span data-stu-id="63370-196">After the build has completed, you may close the "Build Settings" window in Unity.</span></span> 

![Lesson1 Chapter5 Paso4](images/Lesson1Chapter5Step4.JPG)

> <span data-ttu-id="63370-198">Nota: Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar.</span><span class="sxs-lookup"><span data-stu-id="63370-198">NOTE: If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="63370-199">Si ves un error como "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)" [Error: CS0246 = No se encontró el nombre de tipo o de espacio de nombres "XX" (¿te falta una directiva de uso o una referencia de ensamblado?)", es posible que debas instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)]</span><span class="sxs-lookup"><span data-stu-id="63370-199">If you see an error such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)", then you may need to install [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)</span></span>

5. <span data-ttu-id="63370-200">Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear.</span><span class="sxs-lookup"><span data-stu-id="63370-200">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="63370-201">Haga doble clic en el archivo de solución ". sln" para abrir el archivo de solución en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63370-201">Double click on the “.sln” solution file to open the solution file in Visual Studio.</span></span>

> <span data-ttu-id="63370-202">Nota: Asegúrate de abrir la carpeta recién creada [es decir, la carpeta "App" (Aplicaciones), si ha seguido las convenciones de nomenclatura de los pasos anteriores], ya que habrá un archivo .sln con el mismo nombre fuera de esa carpeta que no debes confundir con el archivo .sln dentro de la carpeta de compilación.</span><span class="sxs-lookup"><span data-stu-id="63370-202">Note: Be sure to open the newly created folder (i.e., the "App" folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder that is not to be confused with the .sln file inside the build folder.</span></span> 

![Lección 1, capítulo 5, paso 5](images/Lesson1Chapter5Step5.JPG)

> <span data-ttu-id="63370-204">Nota: Si Visual Studio te pide que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de requisitos previos estén instalados, tal como se especifica en la [página "Instalación de las herramientas"](install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="63370-204">Note: If Visual Studio asks you to install new components, please take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

6. <span data-ttu-id="63370-205">Conecta HoloLens 2 a tu equipo con el cable USB.</span><span class="sxs-lookup"><span data-stu-id="63370-205">Plug your HoloLens 2 into your PC with the USB cable.</span></span> <span data-ttu-id="63370-206">Aunque en estas instrucciones de la lección se supone que vas a implementar una prueba con un dispositivo HoloLens 2, también puedes optar por realizar la implementación en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o decidir crear un [paquete de la aplicación para una transferencia local](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).</span><span class="sxs-lookup"><span data-stu-id="63370-206">While these lesson instructions assume you will be deploying a testing with a HoloLens 2 device, you may also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)</span></span>

7. <span data-ttu-id="63370-207">Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador.</span><span class="sxs-lookup"><span data-stu-id="63370-207">Before building to your device, ensure that the device is in Developer Mode.</span></span> <span data-ttu-id="63370-208">Si es la primera vez que estás realizando una implementación en HoloLens 2, Visual Studio puede pedirte que emparejes HoloLens 2 con un PIN.</span><span class="sxs-lookup"><span data-stu-id="63370-208">If this is your first time deploying to the HoloLens 2, Visual Studio may ask you to pair your HoloLens 2 with a pin.</span></span> <span data-ttu-id="63370-209">Sigue [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si tienes que habilitar el modo de desarrollador o emparejar con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63370-209">Please follow [these instructions](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) if you need to enable developer mode or pair with Visual Studio.</span></span>

8. <span data-ttu-id="63370-210">Configura Visual Studio para compilar HoloLens 2 seleccionando la configuración "Release" (Liberar) y la arquitectura "ARM".</span><span class="sxs-lookup"><span data-stu-id="63370-210">Configure Visual Studio for building to your HoloLens 2 by selecting the “Release” configuration and the “ARM” architecture.</span></span>

![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. <span data-ttu-id="63370-212">El último paso es compilar en el dispositivo seleccionando Depurar>Iniciar sin depurar.</span><span class="sxs-lookup"><span data-stu-id="63370-212">The final step is to build to your device by selecting Debug>Start without Debugging.</span></span> <span data-ttu-id="63370-213">Al seleccionar "Iniciar sin depurar", la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que la información de depuración aparezca en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63370-213">Selecting “Start without Debugging” will cause the application to immediately start on your device upon a successful build, but without Debugging information appearing in Visual Studio.</span></span> <span data-ttu-id="63370-214">Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación.</span><span class="sxs-lookup"><span data-stu-id="63370-214">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span> <span data-ttu-id="63370-215">También puedes seleccionar Compilar>Implementar solución para realizar una implementación en el dispositivo sin necesidad de que se reinicie automáticamente la aplicación.</span><span class="sxs-lookup"><span data-stu-id="63370-215">You may also select Build>Deploy Solution to deploy to your device without having the application automatically start.</span></span>

![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a><span data-ttu-id="63370-217">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="63370-217">Congratulations</span></span>

<span data-ttu-id="63370-218">Ha configurado el reconocimiento de voz en la aplicación, con la tecnología de Azure.</span><span class="sxs-lookup"><span data-stu-id="63370-218">You've set up voice recognition in your application, powered by Azure.</span></span> <span data-ttu-id="63370-219">Ejecute la aplicación para asegurarse de que todas las funciones y características funcionan correctamente.</span><span class="sxs-lookup"><span data-stu-id="63370-219">Run the application to ensure all functions and features are working properly.</span></span> <span data-ttu-id="63370-220">Empiece por decir la palabra de reactivación que escribió en el paso 22, activar terminal.</span><span class="sxs-lookup"><span data-stu-id="63370-220">Start with saying the wake word you typed in Step 22, Activate Terminal.</span></span> <span data-ttu-id="63370-221">Seleccione el botón micrófono para iniciar el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="63370-221">Select the Microphone button to start voice recognition.</span></span> <span data-ttu-id="63370-222">Empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="63370-222">Begin speaking.</span></span> <span data-ttu-id="63370-223">Verá las palabras transformadas en el terminal mientras habla.</span><span class="sxs-lookup"><span data-stu-id="63370-223">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="63370-224">Presione el botón micrófono una segunda vez para detener el reconocimiento de voz.</span><span class="sxs-lookup"><span data-stu-id="63370-224">Press the Microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="63370-225">Por ejemplo, descartar terminal para ocultar el terminal Lunarcom.</span><span class="sxs-lookup"><span data-stu-id="63370-225">Say Dismiss Terminal to hide the Lunarcom terminal.</span></span> <span data-ttu-id="63370-226">En la lección siguiente, veremos cómo cambiar dinámicamente al uso del reconocimiento de voz basado en dispositivos en situaciones en las que el SDK de voz de Azure no está disponible debido a que HoloLens 2 está sin conexión.</span><span class="sxs-lookup"><span data-stu-id="63370-226">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="63370-227">Siguiente tutorial: 2. Adición de un modo sin conexión para la traducción de voz a texto local</span><span class="sxs-lookup"><span data-stu-id="63370-227">Next tutorial: 2. Adding an offline mode for local speech-to-text translation</span></span>](mrlearning-speechSDK-ch2.md)

