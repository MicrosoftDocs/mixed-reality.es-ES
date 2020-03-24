---
title: 'Tutoriales de los servicios de voz de Azure: 4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028427"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="ed26a-105">4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural</span><span class="sxs-lookup"><span data-stu-id="ed26a-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="ed26a-106">En este tutorial, explorarás el reconocimiento de la intención del servicio Voz de Azure.</span><span class="sxs-lookup"><span data-stu-id="ed26a-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="ed26a-107">El reconocimiento de la intención te permite equipar nuestra aplicación con comandos de voz con tecnología de IA que permite a los usuarios indicar comandos de voz no específicos y conseguir, igualmente, que les entienda el sistema.</span><span class="sxs-lookup"><span data-stu-id="ed26a-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="ed26a-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ed26a-108">Objectives</span></span>

* <span data-ttu-id="ed26a-109">Aprender a configurar la intención, las entidades y las expresiones en el portal de LUIS</span><span class="sxs-lookup"><span data-stu-id="ed26a-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="ed26a-110">Aprender a implementar la comprensión del lenguaje natural y la intención en nuestra aplicación</span><span class="sxs-lookup"><span data-stu-id="ed26a-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ed26a-111">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="ed26a-111">Preparing the scene</span></span>

<span data-ttu-id="ed26a-112">En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Intent Recognizer (Script)** (Reconocimiento de la intención de Lunarcom [script]):</span><span class="sxs-lookup"><span data-stu-id="ed26a-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="ed26a-114">En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > Objetos prefabricados > RocketLauncher), arrastra el objeto prefabricado**RocketLauncher_Complete** a la ventana Hierarchy (Jerarquía) y, a continuación, colócalo en una ubicación adecuada; por ejemplo, delante de la cámara:</span><span class="sxs-lookup"><span data-stu-id="ed26a-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="ed26a-115">Transforma el valor de **Position** (Posición) X = 0, Y = 0,4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="ed26a-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="ed26a-116">Transforma el valor de **Rotation** (Giro) X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="ed26a-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="ed26a-118">En la ventana Hierarchy (Jerarquía), selecciona de nuevo el objeto **Lunarcom**, expande el objeto **RocketLauncher_Complete** > **Button** (Botón) y asigna cada uno de los objetos secundarios del objeto **Buttons** (Botones) al campo **Lunar Launcher Buttons** (Botones del lanzacohetes lunar):</span><span class="sxs-lookup"><span data-stu-id="ed26a-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="ed26a-120">Creación del recurso de Azure Language Understanding</span><span class="sxs-lookup"><span data-stu-id="ed26a-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="ed26a-121">En esta sección, crearás un recurso de predicción de Azure para la aplicación de Language Understanding Intelligent Service (LUIS) que crearás en la próxima sección.</span><span class="sxs-lookup"><span data-stu-id="ed26a-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="ed26a-122">Inicia sesión en <a href="https://portal.azure.com" target="_blank">Azure</a> y haz clic en **Crear un recurso**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="ed26a-123">A continuación, busca y selecciona **Language Understanding**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-123">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="ed26a-125">Haz clic en el botón **Crear** para crear una instancia de este servicio:</span><span class="sxs-lookup"><span data-stu-id="ed26a-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="ed26a-127">En la página Crear, haz clic en la opción **Predicción** y escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="ed26a-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="ed26a-128">En **Suscripción**, selecciona **Free Trail** (Prueba gratuita) si tienes una suscripción de prueba. De lo contrario, selecciona una de las otras suscripciones.</span><span class="sxs-lookup"><span data-stu-id="ed26a-128">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="ed26a-129">Para **Grupo de recursos**, haz clic en el vínculo **Crear nuevo**, escribe un nombre adecuado; por ejemplo, *MRKT-Tutorials* y, a continuación, haz clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-129">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="ed26a-131">En el momento de redactar este documento, no es necesario crear un recurso de creación porque se generará automáticamente una clave de prueba de creación en LUIS cuando crees Language Understanding Intelligent Service (LUIS) en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="ed26a-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="ed26a-132">Si ya tienes otro grupo de recursos adecuado en tu cuenta de Azure; por ejemplo, si completaste el tutorial de [Azure Spatial Anchors](mrlearning-asa-ch1.md), puedes usar este grupo de recursos en lugar de crear uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="ed26a-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mrlearning-asa-ch1.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="ed26a-133">Mientras sigues en la página Crear, escribe los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="ed26a-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="ed26a-134">En **Nombre**, escribe un nombre adecuado para el servicio; por ejemplo, *MRTK-tutoriales-AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="ed26a-134">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="ed26a-135">Para **Ubicación de la predicción**, elige una ubicación cercana a la ubicación física de los usuarios de la aplicación; por ejemplo,  *(EE. UU.) Oeste de EE. UU.*</span><span class="sxs-lookup"><span data-stu-id="ed26a-135">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="ed26a-136">Para **Plan de tarifa de predicción**, para los fines de este tutorial, selecciona **F0 (5 llamadas por segundo, 10 000 llamadas al mes)** .</span><span class="sxs-lookup"><span data-stu-id="ed26a-136">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="ed26a-138">A continuación, ve a la pestaña **Revisar y crear**, revisa los detalles y haz clic en el botón **Crear**, situado en la parte inferior de la página, para crear el recurso, así como el nuevo grupo de recursos, si configuraste alguno para su creación:</span><span class="sxs-lookup"><span data-stu-id="ed26a-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="ed26a-140">Después de hacer clic en el botón Crear, tendrás que esperar a que se cree el servicio, lo que puede tardar unos minutos.</span><span class="sxs-lookup"><span data-stu-id="ed26a-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="ed26a-141">Una vez completado el proceso de creación de recursos, se mostrará el mensaje **Se completó la implementación**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-141">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="ed26a-143">Creación de Language Understanding Intelligent Service (LUIS)</span><span class="sxs-lookup"><span data-stu-id="ed26a-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="ed26a-144">En esta sección, crearás una aplicación de LUIS, configurarás y entrenarás su modelo de predicción y lo conectará al recurso de predicción de Azure que creaste en el paso anterior.</span><span class="sxs-lookup"><span data-stu-id="ed26a-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="ed26a-145">En concreto, crearás una intención: si el usuario dice que se debe realizar una acción, la aplicación desencadenará el evento Interactable.OnClick() en uno de los tres botones rojos de la escena, dependiendo del botón al que haga referencia el usuario.</span><span class="sxs-lookup"><span data-stu-id="ed26a-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="ed26a-146">Por ejemplo, si el usuario dice **go ahead and launch the rocket** (adelante, lanza el cohete), la aplicación predecirá que **adelante** significa que se debe realizar alguna **acción** y que el evento Interactable.OnClick() de **destino** está en el botón **launch** (lanzar).</span><span class="sxs-lookup"><span data-stu-id="ed26a-146">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="ed26a-147">Los principales pasos que debes seguir para lograrlo son:</span><span class="sxs-lookup"><span data-stu-id="ed26a-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ed26a-148">Crear una aplicación de LUIS</span><span class="sxs-lookup"><span data-stu-id="ed26a-148">Create a LUIS app</span></span>
2. <span data-ttu-id="ed26a-149">Crear intenciones</span><span class="sxs-lookup"><span data-stu-id="ed26a-149">Create intents</span></span>
3. <span data-ttu-id="ed26a-150">Crear expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="ed26a-150">Create example utterances</span></span>
4. <span data-ttu-id="ed26a-151">Crear entidades</span><span class="sxs-lookup"><span data-stu-id="ed26a-151">Create entities</span></span>
5. <span data-ttu-id="ed26a-152">Asignar entidades a las expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="ed26a-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="ed26a-153">Entrenar, probar y publicar la aplicación</span><span class="sxs-lookup"><span data-stu-id="ed26a-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="ed26a-154">Asignar un recurso de predicción de Azure a la aplicación</span><span class="sxs-lookup"><span data-stu-id="ed26a-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="ed26a-155">1. Crear una aplicación de LUIS</span><span class="sxs-lookup"><span data-stu-id="ed26a-155">1. Create a LUIS app</span></span>

<span data-ttu-id="ed26a-156">Con la misma cuenta de usuario que usaste para crear el recurso de Azure en la sección anterior, inicia sesión en <a href="https://www.luis.ai" target="_blank">LUIS</a>, selecciona tu país y acepta los términos de uso.</span><span class="sxs-lookup"><span data-stu-id="ed26a-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="ed26a-157">En el paso siguiente, cuando se te pida **vincular la cuenta de Azure**, elige **Continuar usando la clave de prueba** para usar un recurso de creación de Azure en su lugar.</span><span class="sxs-lookup"><span data-stu-id="ed26a-157">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="ed26a-158">Si ya te has registrado en LUIS y ha expirado la clave de prueba de creación, puedes consultar la documentación [Migración a una clave de creación de recursos de Azure](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) para cambiar el recurso de creación de LUIS a Azure.</span><span class="sxs-lookup"><span data-stu-id="ed26a-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="ed26a-159">Una vez iniciada la sesión, desplázate a la página **Mis aplicaciones**, haz clic en **Crear una aplicación** y escribe los valores siguientes en la ventana emergente **Crear una aplicación**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="ed26a-160">En **Nombre**, escribe un nombre adecuado; por ejemplo, *MRTK Tutorials - AzureSpeechServices*.</span><span class="sxs-lookup"><span data-stu-id="ed26a-160">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="ed26a-161">En **Referencia cultural**, selecciona **Inglés**</span><span class="sxs-lookup"><span data-stu-id="ed26a-161">For **Culture**, select **English**</span></span>
* <span data-ttu-id="ed26a-162">En **Descripción**, puedes escribir una descripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="ed26a-162">For **Description**, optionally enter a suitable description</span></span>

<span data-ttu-id="ed26a-163">A continuación, haz clic en el botón **Listo** para crear la aplicación:</span><span class="sxs-lookup"><span data-stu-id="ed26a-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="ed26a-165">Una vez creada la aplicación, se te dirigirá a su página **Panel**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="ed26a-167">2. Crear intenciones</span><span class="sxs-lookup"><span data-stu-id="ed26a-167">2. Create intents</span></span>

<span data-ttu-id="ed26a-168">Desde la página Panel, ve a la página Compilación > Activos de la aplicación > **Intenciones**, haz clic en **Crear intención** y escribe el siguiente valor en la ventana emergente **Crear intención**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="ed26a-169">En **Nombre de la intención**, escribe **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="ed26a-170">A continuación, haz clic en el botón **Listo** para crear la nueva intención:</span><span class="sxs-lookup"><span data-stu-id="ed26a-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="ed26a-172">Para los fines de este tutorial, el proyecto de Unity hará referencia a esta intención por su nombre, "PressButton".</span><span class="sxs-lookup"><span data-stu-id="ed26a-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="ed26a-173">Por lo tanto, es muy importante que asignes exactamente el mismo nombre a la intención.</span><span class="sxs-lookup"><span data-stu-id="ed26a-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="ed26a-174">Una vez creada la intención, se te dirigirá a su página:</span><span class="sxs-lookup"><span data-stu-id="ed26a-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="ed26a-176">3. Crear expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="ed26a-176">3. Create example utterances</span></span>

<span data-ttu-id="ed26a-177">En la lista **Expresión de ejemplo** de la intención **PressButton**, agrega las siguientes expresiones de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="ed26a-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="ed26a-178">activate launch sequence (activar secuencia de lanzamiento)</span><span class="sxs-lookup"><span data-stu-id="ed26a-178">activate launch sequence</span></span>
* <span data-ttu-id="ed26a-179">show me a placement hint (mostrar sugerencia de selección de ubicación)</span><span class="sxs-lookup"><span data-stu-id="ed26a-179">show me a placement hint</span></span>
* <span data-ttu-id="ed26a-180">initiate the launch sequence (iniciar secuencia de lanzamiento)</span><span class="sxs-lookup"><span data-stu-id="ed26a-180">initiate the launch sequence</span></span>
* <span data-ttu-id="ed26a-181">press placement hints button (presionar botón de sugerencias)</span><span class="sxs-lookup"><span data-stu-id="ed26a-181">press placement hints button</span></span>
* <span data-ttu-id="ed26a-182">give me a hint (proporcionar sugerencia)</span><span class="sxs-lookup"><span data-stu-id="ed26a-182">give me a hint</span></span>
* <span data-ttu-id="ed26a-183">push the launch button (presionar botón de lanzamiento)</span><span class="sxs-lookup"><span data-stu-id="ed26a-183">push the launch button</span></span>
* <span data-ttu-id="ed26a-184">i need a hint (necesito una sugerencia)</span><span class="sxs-lookup"><span data-stu-id="ed26a-184">i need a hint</span></span>
* <span data-ttu-id="ed26a-185">press the reset button (presionar botón de restablecimiento)</span><span class="sxs-lookup"><span data-stu-id="ed26a-185">press the reset button</span></span>
* <span data-ttu-id="ed26a-186">time to reset the experience (hora de restablecer la experiencia)</span><span class="sxs-lookup"><span data-stu-id="ed26a-186">time to reset the experience</span></span>
* <span data-ttu-id="ed26a-187">go ahead and launch the rocket (adelante, lanza el cohete)</span><span class="sxs-lookup"><span data-stu-id="ed26a-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="ed26a-188">Una vez agregadas todas las expresiones de ejemplo, la página de la intención PressButton debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="ed26a-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="ed26a-190">Para los fines de este tutorial, el proyecto de Unity hará referencia a las palabras "hint" (sugerencia), "hints" (sugerencias), "reset" (restablecimiento) y "launch" (lanzar).</span><span class="sxs-lookup"><span data-stu-id="ed26a-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="ed26a-191">Por lo tanto, es muy importante que escribas estas palabras exactamente de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="ed26a-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="ed26a-192">4. Crear entidades</span><span class="sxs-lookup"><span data-stu-id="ed26a-192">4. Create entities</span></span>

<span data-ttu-id="ed26a-193">Desde la página de la intención PressButton, ve a la página Compilación > Activos de la aplicación > **Entidades**, haz clic en **Crear una nueva entidad** y escribe los valores siguientes en la ventana emergente **Crear una nueva entidad**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="ed26a-194">En **Nombre de entidad**, escribe **Action**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="ed26a-195">En **Tipo de entidad**, selecciona **Simple**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-195">For **Entity type**, select **Simple**</span></span>

<span data-ttu-id="ed26a-196">A continuación, haz clic en el botón **Listo** para crear la nueva identidad:</span><span class="sxs-lookup"><span data-stu-id="ed26a-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="ed26a-198">**Repite** el paso anterior para crear otra entidad denominada **Target**. De este modo, tendrás dos entidades denominadas Action y Target:</span><span class="sxs-lookup"><span data-stu-id="ed26a-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="ed26a-200">Para los fines de este tutorial, el proyecto de Unity hará referencia a estas entidades por su nombre, "Action" y "Target".</span><span class="sxs-lookup"><span data-stu-id="ed26a-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="ed26a-201">Por lo tanto, es muy importante que asignes exactamente el mismo nombre a las entidades.</span><span class="sxs-lookup"><span data-stu-id="ed26a-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="ed26a-202">5. Asignar entidades a las expresiones de ejemplo</span><span class="sxs-lookup"><span data-stu-id="ed26a-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="ed26a-203">Desde la página Entidades, vuelve a la página de la intención **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="ed26a-204">De vuelta a la página de la intención PressButton, haz clic en la palabra **go** y, después, en la palabra **ahead** y, a continuación, selecciona **Action (Simple)** en el menú contextual para etiquetar **go ahead** como valor de la entidad **Action**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="ed26a-206">Ahora, la frase **go ahead** está definida como un valor de la entidad **Action**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="ed26a-207">Si pasas el ratón por encima del nombre de entidad Action, podrás ver el valor de la entidad Action asociado:</span><span class="sxs-lookup"><span data-stu-id="ed26a-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="ed26a-209">La línea roja que aparece debajo de la etiqueta en la imagen anterior indica que el valor de la entidad no se ha predicho, lo que se resolverá al entrenar el modelo en la siguiente sección.</span><span class="sxs-lookup"><span data-stu-id="ed26a-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="ed26a-210">A continuación, haz clic en la palabra **launch** y selecciona **Target (Simple)** en el menú contextual emergente para etiquetar **launch** como valor de la entidad **Target**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="ed26a-212">Ahora, la palabra **launch** está definida como valor de la entidad **Target**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="ed26a-213">Si pasas el ratón por encima del nombre de la entidad Target, podrás ver el valor de la entidad Target asociado:</span><span class="sxs-lookup"><span data-stu-id="ed26a-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="ed26a-215">Ahora, la expresión de ejemplo de la intención PressButton "go ahead and launch the rocket" (adelante, lanza el cohete) se ha configurado para predecirse como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="ed26a-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="ed26a-216">Intención: PressButton</span><span class="sxs-lookup"><span data-stu-id="ed26a-216">Intent: PressButton</span></span>
* <span data-ttu-id="ed26a-217">Entidad Action: go ahead</span><span class="sxs-lookup"><span data-stu-id="ed26a-217">Action entity: go ahead</span></span>
* <span data-ttu-id="ed26a-218">Entidad Target: launch</span><span class="sxs-lookup"><span data-stu-id="ed26a-218">Target entity: launch</span></span>

<span data-ttu-id="ed26a-219">**Repite** el proceso anterior de dos pasos para asignar una etiqueta de entidad Action y Target a cada una de las expresiones de ejemplo, teniendo en cuenta que las siguientes palabras se deben etiquetar como entidades **Target**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="ed26a-220">**hint** (destinada a HintsButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="ed26a-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="ed26a-221">**hints** (destinada a HintsButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="ed26a-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="ed26a-222">**reset** (destinada a ResetButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="ed26a-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="ed26a-223">**launch** (destinada a LaunchButton en el proyecto de Unity)</span><span class="sxs-lookup"><span data-stu-id="ed26a-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="ed26a-224">Una vez etiquetadas todas las expresiones de ejemplo, la página de la intención PressButton debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="ed26a-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="ed26a-226">Una forma alternativa de comprobar que has asignado las entidades correctas es hacer clic en el menú **Opciones de visualización** y cambiar la vista a **Mostrar valores de entidad**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="ed26a-228">Ahora, con la vista definida para mostrar valores de entidad, puedes pasar el ratón por encima de las palabras y frases etiquetadas para comprobar rápidamente el nombre de entidad asignado:</span><span class="sxs-lookup"><span data-stu-id="ed26a-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="ed26a-230">6. Entrenar, probar y publicar la aplicación</span><span class="sxs-lookup"><span data-stu-id="ed26a-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="ed26a-231">Para entrenar la aplicación, haz clic en el botón **Entrenar** y espera a que se complete el proceso de entrenamiento:</span><span class="sxs-lookup"><span data-stu-id="ed26a-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="ed26a-233">Como puedes ver en la imagen anterior, se han quitado las líneas rojas de todas las etiquetas, lo que indica que se han predicho todos los valores de entidad.</span><span class="sxs-lookup"><span data-stu-id="ed26a-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="ed26a-234">Observa también que el icono de estado situado a la izquierda del botón Entrenar ha cambiado de color rojo a verde.</span><span class="sxs-lookup"><span data-stu-id="ed26a-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="ed26a-235">Cuando se acabe de procesar el entrenamiento, haz clic en el botón **Probar**, escribe **go ahead and launch the rocket** y presiona la tecla Entrar:</span><span class="sxs-lookup"><span data-stu-id="ed26a-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="ed26a-237">Una vez procesada la expresión de prueba, haz clic en **Inspeccionar** para ver el resultado de la prueba:</span><span class="sxs-lookup"><span data-stu-id="ed26a-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="ed26a-238">Intención: PressButton (con una certeza del 98,5 %)</span><span class="sxs-lookup"><span data-stu-id="ed26a-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="ed26a-239">Entidad Action: go ahead</span><span class="sxs-lookup"><span data-stu-id="ed26a-239">Action entity: go ahead</span></span>
* <span data-ttu-id="ed26a-240">Entidad Target: launch</span><span class="sxs-lookup"><span data-stu-id="ed26a-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="ed26a-242">Para publicar la aplicación, haz clic en el botón **Publicar** de la parte superior derecha y, a continuación, en la ventana emergente **Elige el espacio de publicación y la configuración**, selecciona **Producción** y haz clic en el botón **Publicar**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="ed26a-244">Espera hasta que se complete el proceso de publicación:</span><span class="sxs-lookup"><span data-stu-id="ed26a-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="ed26a-246">7. Asignar un recurso de predicción de Azure a la aplicación</span><span class="sxs-lookup"><span data-stu-id="ed26a-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="ed26a-247">Ve a la página Administrar > Configuración de la aplicación > **Recursos de Azure**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="ed26a-249">En la página Recursos de Azure, haz clic en el botón **Agregar recurso de predicción** y selecciona los valores siguientes en la ventana emergente **Asignar un recurso a la aplicación**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="ed26a-250">Para **Nombre de inquilino**, selecciona tu nombre de inquilino.</span><span class="sxs-lookup"><span data-stu-id="ed26a-250">For **Tenant name**, select your tenant name</span></span>
* <span data-ttu-id="ed26a-251">Para **Nombre de suscripción**, selecciona la misma suscripción que usaste anteriormente en [Creación del recurso de Azure Language Understanding](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource).</span><span class="sxs-lookup"><span data-stu-id="ed26a-251">For **Subscription Name**, select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="ed26a-252">Para **Nombre de recurso de LUIS**, selecciona el recurso de predicción que usaste anteriormente en [Creación del recurso de Azure Language Understanding](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource).</span><span class="sxs-lookup"><span data-stu-id="ed26a-252">For **LUIS resource name**, select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="ed26a-253">A continuación, haz clic en el botón **Asignar recurso** para asignar el recurso de predicción de Azure a la aplicación:</span><span class="sxs-lookup"><span data-stu-id="ed26a-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="ed26a-255">Una vez asignado el recurso, la página de recursos de Azure debería tener un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="ed26a-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="ed26a-257">Conexión del proyecto de Unity con la aplicación de LUIS</span><span class="sxs-lookup"><span data-stu-id="ed26a-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="ed26a-258">En la página Administrar > Configuración de la aplicación > **Recursos de Azure**, haz clic en el icono **copiar** para copiar el **Ejemplo de consulta**:</span><span class="sxs-lookup"><span data-stu-id="ed26a-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="ed26a-260">Desde el proyecto de Unity, en la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca el componente **Lunarcom Intent Recognizer (Script)** (Reconocimiento de la intención de Lunarcom [script]) y configúralo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="ed26a-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="ed26a-261">En el campo **LUIS Endpoint** (Punto de conexión de LUIS), después del **Ejemplo de consulta** que copiaste en el paso anterior:</span><span class="sxs-lookup"><span data-stu-id="ed26a-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="ed26a-263">Probar y mejorar el reconocimiento de la intención</span><span class="sxs-lookup"><span data-stu-id="ed26a-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="ed26a-264">Para usar el reconocimiento de la intención directamente en el editor de Unity, debes permitir que el equipo de desarrollo use el dictado.</span><span class="sxs-lookup"><span data-stu-id="ed26a-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="ed26a-265">Para comprobar esta configuración, abre la **Configuración** de Windows, elige **Privacidad** > **Voz** y asegúrate de que el **Reconocimiento de voz en línea** esté activado:</span><span class="sxs-lookup"><span data-stu-id="ed26a-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="ed26a-267">Si ahora entras en el modo de juego, puedes probar el reconocimiento de la intención presionando el botón del cohete:</span><span class="sxs-lookup"><span data-stu-id="ed26a-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="ed26a-268">Después, suponiendo que el equipo tiene micrófono, al decir la primera expresión de ejemplo, **go ahead and launch the rocket** (adelante, lanza el cohete), verás el lanzamiento al espacio de LunarModule:</span><span class="sxs-lookup"><span data-stu-id="ed26a-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="ed26a-270">Prueba todas las **expresiones de ejemplo**, algunas **variaciones de las expresiones de ejemplo** y algunas **expresiones aleatorias**.</span><span class="sxs-lookup"><span data-stu-id="ed26a-270">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="ed26a-271">A continuación, vuelve a <a href="https://www.luis.ai" target="_blank">LUIS</a> y ve a la página Compilación > Mejorar el rendimiento de la aplicación > **Revisar las expresiones de punto de conexión**, usa el botón de **alternancia** para cambiar ente la vista predeterminada de entidades y la de **tokens** y, a continuación, revisa las expresiones:</span><span class="sxs-lookup"><span data-stu-id="ed26a-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="ed26a-272">En la columna **Expresión**, cambia y quita las etiquetas asignadas según sea necesario para alinearlas con tu intención.</span><span class="sxs-lookup"><span data-stu-id="ed26a-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="ed26a-273">En la columna **Intención alineada**, comprueba que la intención sea correcta.</span><span class="sxs-lookup"><span data-stu-id="ed26a-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="ed26a-274">En la columna **Agregar o eliminar**, haz clic en el botón de marca de verificación verde para agregar la expresión o en el botón x rojo para eliminarla.</span><span class="sxs-lookup"><span data-stu-id="ed26a-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="ed26a-275">Cuando haya revisado todas las expresiones que quieras, haz clic en el botón **Entrenar** para volver a entrenar el modelo y, luego, en el botón **Publicar** para volver a publicar la aplicación actualizada:</span><span class="sxs-lookup"><span data-stu-id="ed26a-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="ed26a-277">Si una expresión de punto de conexión no está alineada con la intención de PressButton, pero quieres que el modelo sepa que la expresión no tiene ninguna intención, puedes cambiar la intención alineada a Ninguna.</span><span class="sxs-lookup"><span data-stu-id="ed26a-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="ed26a-278">**Repite** este proceso tantas veces como quieras para mejorar el modelo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ed26a-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ed26a-279">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ed26a-279">Congratulations</span></span>

<span data-ttu-id="ed26a-280">Ahora, el proyecto tiene comandos de voz con tecnología de IA, lo que permite que la aplicación reconozca la intención de los usuarios aunque no usen comandos precisos.</span><span class="sxs-lookup"><span data-stu-id="ed26a-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="ed26a-281">Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="ed26a-281">Run the application on your device to ensure the feature is working properly.</span></span>
