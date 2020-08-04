---
title: 'Tutoriales de la nube de Azure: 5. Integración de Azure Bot Service con LUIS'
description: Complete este curso para aprender a implementar Azure Bot Service y el reconocimiento del lenguaje natural en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens, hololens 2, azure bot service, luis, lenguaje natural, bot de conversación
ms.localizationpriority: high
ms.openlocfilehash: daf97cde1477a84c1776a069ec5b8d1a185b63cc
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376457"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="1bf39-105">5. Integración de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1bf39-105">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="1bf39-106">En este tutorial, aprenderá a usar **Azure Bot Service** en la aplicación de demostración de **HoloLens 2** para agregar el reconocimiento del lenguaje (LUIS) y dejar que el bot ayude al usuario al buscar **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-106">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="1bf39-107">Este es un tutorial de dos partes en el que, en la primera parte, crea el bot con [Bot Composer](https://docs.microsoft.com/composer/introduction) como una solución sin código y echa un vistazo rápido a la función de Azure que alimenta el bot con los datos necesarios.</span><span class="sxs-lookup"><span data-stu-id="1bf39-107">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="1bf39-108">En la segunda parte se usa **BotManager (script)** en el proyecto de Unity para consumir el servicio de bot hospedado.</span><span class="sxs-lookup"><span data-stu-id="1bf39-108">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="1bf39-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="1bf39-109">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="1bf39-110">1ª parte</span><span class="sxs-lookup"><span data-stu-id="1bf39-110">Part 1</span></span>

* <span data-ttu-id="1bf39-111">Aprender los aspectos básicos de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1bf39-111">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="1bf39-112">Aprender a usar Bot Composer para crear un bot</span><span class="sxs-lookup"><span data-stu-id="1bf39-112">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="1bf39-113">Aprender a usar una función de Azure para proporcionar datos de Azure Storage</span><span class="sxs-lookup"><span data-stu-id="1bf39-113">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="1bf39-114">2ª parte</span><span class="sxs-lookup"><span data-stu-id="1bf39-114">Part 2</span></span>

* <span data-ttu-id="1bf39-115">Aprender a configurar la escena para usar Azure Bot Service en este proyecto</span><span class="sxs-lookup"><span data-stu-id="1bf39-115">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="1bf39-116">Aprender a establecer y encontrar objetos conversando con el bot</span><span class="sxs-lookup"><span data-stu-id="1bf39-116">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="1bf39-117">Descripción de Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1bf39-117">Understanding Azure Bot Service</span></span>

<span data-ttu-id="1bf39-118">**Azure Bot Service** permite a los desarrolladores crear bots inteligentes que pueden mantener conversaciones naturales con los usuarios gracias a **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-118">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="1bf39-119">Un bot de conversación es una excelente manera de ampliar las formas de las que un usuario puede interactuar con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-119">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="1bf39-120">Un bot puede actuar como una base de conocimiento con [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) para mantener una conversación sofisticada con la potencia del [reconocimiento del lenguaje (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="1bf39-120">A Bot can act as a knowledge base with a [QnA Marker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp).</span></span>

<span data-ttu-id="1bf39-121">Obtenga más información sobre [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="1bf39-121">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="1bf39-122">1ª parte: creación del bot</span><span class="sxs-lookup"><span data-stu-id="1bf39-122">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="1bf39-123">Antes de poder usar el bot en la aplicación de Unity, debe desarrollarlo, proporcionarle datos y hospedarlo en **Azure**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-123">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="1bf39-124">El objetivo del bot es tener las capacidades para indicar cuántos *objetos con seguimiento* se almacenan en la base de datos, buscar un *objeto con seguimiento* por su nombre y indicar al usuario información básica sobre el mismo.</span><span class="sxs-lookup"><span data-stu-id="1bf39-124">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="1bf39-125">Vista rápida de la función de Azure de objetos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1bf39-125">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="1bf39-126">Está a punto de empezar a crear el bot, pero para que resulte útil, debe proporcionarle un recurso del que pueda extraer datos.</span><span class="sxs-lookup"><span data-stu-id="1bf39-126">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="1bf39-127">Dado que el *bot* podrá contar la cantidad de **objetos con seguimiento**, buscar objetos específicos por nombre e indicar detalles, usará una función de Azure sencilla que tenga acceso al **almacenamiento de tablas de Azure**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-127">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="1bf39-128">Descargue el proyecto de la función de Azure: [Función de Azure de objetos con seguimiento](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span><span class="sxs-lookup"><span data-stu-id="1bf39-128">Download the Azure Function Project: [Tracked Objects Azure Function](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)</span></span>

<span data-ttu-id="1bf39-129">Esta función de Azure tiene dos acciones, **Count** y **Find**, que se pueden invocar a través de llamadas *HTTP* *GET* básicas.</span><span class="sxs-lookup"><span data-stu-id="1bf39-129">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="1bf39-130">Puede inspeccionar el código en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-130">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="1bf39-131">Obtenga más información sobre [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="1bf39-131">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="1bf39-132">La función **Count** consulta en el **almacenamiento de tablas** todos los elementos **TrackedObjects** de la tabla, es muy sencillo.</span><span class="sxs-lookup"><span data-stu-id="1bf39-132">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="1bf39-133">Por otra parte, la función **Find** toma un parámetro de consulta *name* de la solicitud *GET* y consulta en el **almacenamiento de tablas** un elemento **TrackedObject** coincidente y devuelve un DTO como JSON.</span><span class="sxs-lookup"><span data-stu-id="1bf39-133">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="1bf39-134">Puede implementar esta **función de Azure** directamente desde **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-134">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="1bf39-135">Aquí encontrará toda la información relacionada con la [implementación de la función de Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).</span><span class="sxs-lookup"><span data-stu-id="1bf39-135">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).</span></span>

<span data-ttu-id="1bf39-136">Una vez que haya completado la implementación, en el **portal de Azure**, abra el recurso correspondiente y haga clic en **Configuración**, que se encuentra en la sección *Configuración*.</span><span class="sxs-lookup"><span data-stu-id="1bf39-136">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="1bf39-137">En **Configuración de la aplicación** debe proporcionar la *cadena de conexión* a **Azure Storage** donde se almacenan los **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-137">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="1bf39-138">Haga clic en **Nueva configuración de la aplicación** y use para el nombre: **AzureStorageConnectionString** y para el valor proporcione la *cadena de conexión* correcta.</span><span class="sxs-lookup"><span data-stu-id="1bf39-138">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="1bf39-139">Después de ello, haga clic en **Guardar** y la **función de Azure** está lista para hacer funcionar el *bot* que creará a continuación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-139">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="1bf39-140">Creación de un bot de conversación</span><span class="sxs-lookup"><span data-stu-id="1bf39-140">Creating a conversation Bot</span></span>

<span data-ttu-id="1bf39-141">Hay varias maneras de desarrollar un bot de conversación basado en Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="1bf39-141">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="1bf39-142">En esta lección usará la aplicación de escritorio [Bot Framework Composer](https://docs.microsoft.com/composer/), que es un diseñador visual perfecto para el desarrollo rápido.</span><span class="sxs-lookup"><span data-stu-id="1bf39-142">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="1bf39-143">Puede descargar las últimas versiones desde el [repositorio de GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="1bf39-143">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="1bf39-144">Está disponible para Windows, Mac y Linux.</span><span class="sxs-lookup"><span data-stu-id="1bf39-144">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="1bf39-145">Una vez que se haya instalado **Bot Framework Composer**, inicie la aplicación y debería ver esta interfaz:</span><span class="sxs-lookup"><span data-stu-id="1bf39-145">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="1bf39-147">Ha preparado un proyecto de Bot Composer que proporciona los diálogos y desencadenadores necesarios para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="1bf39-147">You have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span>
<span data-ttu-id="1bf39-148">Descargue el proyecto: [Proyecto de Bot Framework Composer](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span><span class="sxs-lookup"><span data-stu-id="1bf39-148">Download the project: [Bot Framework Composer project](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)</span></span>

<span data-ttu-id="1bf39-149">En la barra superior, haga clic en **Abrir** y seleccione el proyecto de Bot Framework que ha descargado, denominado **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-149">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="1bf39-150">Una vez que el proyecto esté totalmente cargado, debería ver el proyecto listo.</span><span class="sxs-lookup"><span data-stu-id="1bf39-150">After the project is fully loaded, you should see the project ready.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="1bf39-152">Vamos a centrarnos en el lado izquierdo, en el que puede ver el **panel Diálogos**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-152">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="1bf39-153">Allí hay un diálogo denominado **TrackedObjectsBot** en el que puede ver varios **desencadenadores**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-153">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="1bf39-154">Obtenga más información acerca de los [conceptos de Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="1bf39-154">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="1bf39-155">Estos desencadenadores hacen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1bf39-155">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="1bf39-156">Saludo</span><span class="sxs-lookup"><span data-stu-id="1bf39-156">Greeting</span></span>

<span data-ttu-id="1bf39-157">Este es el punto de entrada del *bot* de chat cuando un *usuario* inicia una conversación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-157">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="1bf39-159">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="1bf39-159">AskingForCount</span></span>

<span data-ttu-id="1bf39-160">Este diálogo se desencadena cuando el *usuario* pide el recuento de todos los **objetos con seguimiento**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-160">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="1bf39-161">Estas son las frases que lo desencadenan:</span><span class="sxs-lookup"><span data-stu-id="1bf39-161">These are the trigger phrases:</span></span>

>* <span data-ttu-id="1bf39-162">contar todo</span><span class="sxs-lookup"><span data-stu-id="1bf39-162">count me all</span></span>
>* <span data-ttu-id="1bf39-163">cuántos se almacenan</span><span class="sxs-lookup"><span data-stu-id="1bf39-163">how many are stored</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="1bf39-165">Gracias a [LUIS](https://docs.microsoft.com/composer/how-to-use-luis), el *usuario* no tiene que formular las frases de la manera exacta, lo que permite una conversación natural para el *usuario*.</span><span class="sxs-lookup"><span data-stu-id="1bf39-165">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="1bf39-166">En este diálogo, el *bot* también se comunicará con la función de Azure **Count**, lo que de detallará más adelante.</span><span class="sxs-lookup"><span data-stu-id="1bf39-166">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="1bf39-167">Intención desconocida</span><span class="sxs-lookup"><span data-stu-id="1bf39-167">Unknown Intent</span></span>

<span data-ttu-id="1bf39-168">Este diálogo se desencadena si la entrada del *usuario* no se ajusta a ninguna otra condición desencadenadora y responde al usuario que intente de nuevo su pregunta.</span><span class="sxs-lookup"><span data-stu-id="1bf39-168">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="1bf39-170">FindEntity</span><span class="sxs-lookup"><span data-stu-id="1bf39-170">FindEntity</span></span>

<span data-ttu-id="1bf39-171">El último diálogo es más complejo, ya que contiene bifurcaciones y almacena datos en la memoria de *bots*.</span><span class="sxs-lookup"><span data-stu-id="1bf39-171">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="1bf39-172">Solicita al usuario el *nombre* del **objeto con seguimiento** del que quiere saber más información, realiza una consulta a la función de Azure **Find** y usa la respuesta para continuar con la conversación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-172">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="1bf39-174">Si no se encuentra el **objeto con seguimiento**, se informa al usuario y finaliza la conversación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-174">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="1bf39-175">Cuando se encuentra el **objeto con seguimiento** en cuestión, el bot comprobará qué propiedades están disponibles e informará sobre ellas.</span><span class="sxs-lookup"><span data-stu-id="1bf39-175">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="1bf39-176">Adaptación del bot</span><span class="sxs-lookup"><span data-stu-id="1bf39-176">Adapting the Bot</span></span>

<span data-ttu-id="1bf39-177">Los desencadenadores **AskingForCount** y **FindEntity** deben comunicarse con el back-end, lo que significa que tiene que agregar la dirección URL correcta de la **función de Azure** que implementó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1bf39-177">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="1bf39-178">En el panel de diálogos, haga clic en **AskingForCount** y busque la acción *Enviar una solicitud HTTP*; aquí puede ver el campo **URL** que necesita para cambiar la URL correcta para el punto de conexión de la función **Count**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-178">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="1bf39-180">Por último, busque el desencadenador **FindEntity** y busque la acción *Enviar una solicitud HTTP*; en el campo **URL**, cambie la dirección URL por el punto de conexión de la función **Find**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-180">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="1bf39-182">Con todo definido, ya está listo para implementar el bot.</span><span class="sxs-lookup"><span data-stu-id="1bf39-182">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="1bf39-183">Puesto que tiene Bot Framework Composer instalado, puede publicarlo directamente desde allí.</span><span class="sxs-lookup"><span data-stu-id="1bf39-183">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="1bf39-184">Obtenga más información sobre cómo [publicar un bot desde Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="1bf39-184">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="1bf39-185">No dude en experimentar con el bot agregando más frases desencadenadoras, nuevas respuestas o bifurcaciones de conversación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-185">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="1bf39-186">Parte 2: configuración de todo en Unity</span><span class="sxs-lookup"><span data-stu-id="1bf39-186">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="1bf39-187">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="1bf39-187">Preparing the scene</span></span>

<span data-ttu-id="1bf39-188">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-188">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="1bf39-190">Desde ahí, mueva el elemento prefabricado **ChatBotManager** a la jerarquía de la escena.</span><span class="sxs-lookup"><span data-stu-id="1bf39-190">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="1bf39-191">Una vez que agregue ChatBotManager a la escena, haga clic en el componente **Chat Bot Manager** (Administrador de bot de chat).</span><span class="sxs-lookup"><span data-stu-id="1bf39-191">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="1bf39-192">En el inspector verá que hay un campo **Direct Line Secret Key** (Clave secreta de línea directa) que debe rellenar.</span><span class="sxs-lookup"><span data-stu-id="1bf39-192">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="1bf39-193">Puede recuperar la *clave secreta* del portal de Azure; para ello, busque el recurso del tipo **Registro de canales de bots** que ha creado en la primera parte de este tutorial.</span><span class="sxs-lookup"><span data-stu-id="1bf39-193">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="1bf39-195">Ahora, conectará el objeto **ChatBotManager** con el componente **ChatBotController** adjunto al objeto **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="1bf39-195">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="1bf39-196">En la jerarquía, seleccione **ChatBotPanel** y verá un campo vacío **Chat Bot Manager** (Administrador de bots de chat); arrastre desde la jerarquía el objeto **ChatBotManager** al campo **Chat Bot Manager** (Administrador de bots de chat).</span><span class="sxs-lookup"><span data-stu-id="1bf39-196">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="1bf39-198">A continuación, necesita una manera de abrir **ChatBotPanel** para que el usuario pueda interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="1bf39-198">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="1bf39-199">En la ventana Scene (Escena) es posible que haya observado que hay un botón secundario *Chat bot* (Bot de chat) en el objeto **MainMenu**, que usará para resolver este problema.</span><span class="sxs-lookup"><span data-stu-id="1bf39-199">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="1bf39-200">En la jerarquía, busque **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** y busque en el Inspector el script *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="1bf39-200">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="1bf39-201">Allí verá una ranura vacía en la devolución de llamada del evento **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="1bf39-201">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="1bf39-202">Arrastre y coloque **ChatBotPanel** en la ranura del evento, en la lista desplegable vaya a *GameObject*, seleccione en el submenú *SetActive (bool)* y active la casilla.</span><span class="sxs-lookup"><span data-stu-id="1bf39-202">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="1bf39-204">Ahora el bot de chat puede iniciarse desde el menú principal, por lo que la escena está lista para su uso.</span><span class="sxs-lookup"><span data-stu-id="1bf39-204">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="1bf39-205">Puesta a prueba del bot</span><span class="sxs-lookup"><span data-stu-id="1bf39-205">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="1bf39-206">Pregunta sobre la cantidad de objetos con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1bf39-206">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="1bf39-207">En primer lugar, realice una prueba en la que pida al bot cuántos **objetos con seguimiento** se almacenan en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="1bf39-207">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="1bf39-208">Esta vez debe ejecutar la aplicación desde HoloLens 2 porque es posible que servicios como *texto a voz* no estén disponibles en el sistema.</span><span class="sxs-lookup"><span data-stu-id="1bf39-208">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="1bf39-209">Ejecute la aplicación en HoloLens 2 y haga clic en el botón *Bot de chat* situado junto al menú principal.</span><span class="sxs-lookup"><span data-stu-id="1bf39-209">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="1bf39-210">El bot le saludará. Pregunte **¿cuántos objetos tenemos?**</span><span class="sxs-lookup"><span data-stu-id="1bf39-210">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="1bf39-211">Debe indicarle la cantidad y finalizar la conversación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-211">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="1bf39-212">Pregunta sobre un objeto con seguimiento</span><span class="sxs-lookup"><span data-stu-id="1bf39-212">Asking about a tracked object</span></span>

<span data-ttu-id="1bf39-213">Vuelva a ejecutar la aplicación y, esta vez, pregunte **busca un objeto con seguimiento**; el bot le pedirá el nombre, al que debe responder con "coche" o el nombre de otro *objeto con seguimiento* que sepa que existe en la base de datos.</span><span class="sxs-lookup"><span data-stu-id="1bf39-213">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="1bf39-214">El bot le indicará detalles como la descripción y si tiene un anclaje espacial asignado.</span><span class="sxs-lookup"><span data-stu-id="1bf39-214">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="1bf39-215">Pruebe de preguntar por un **objeto con seguimiento** que no exista y escuche cómo responde el bot.</span><span class="sxs-lookup"><span data-stu-id="1bf39-215">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="1bf39-216">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="1bf39-216">Congratulations</span></span>

<span data-ttu-id="1bf39-217">En este tutorial ha aprendido cómo se puede usar Azure Bot Framework para interactuar con la aplicación mediante la conversación con lenguaje natural.</span><span class="sxs-lookup"><span data-stu-id="1bf39-217">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="1bf39-218">Ha aprendido a desarrollar su propio bot y cuáles son las piezas necesarias para que funcione.</span><span class="sxs-lookup"><span data-stu-id="1bf39-218">You learned how to develope your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="1bf39-219">Conclusión</span><span class="sxs-lookup"><span data-stu-id="1bf39-219">Conclusion</span></span>

<span data-ttu-id="1bf39-220">A lo largo de esta serie de tutoriales, ha experimentado cómo **Azure Cloud Services** ha incorporado características nuevas y emocionantes a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1bf39-220">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="1bf39-221">Ahora puede almacenar datos e imágenes en la nube con **Azure Storage**, usar **Azure Custom Vision** para asociar imágenes y entrenar un modelo, incorporar objetos a un contexto local con **anclajes espaciales de Azure** e implementar **Azure Bot Framework con tecnología de LUIS** para agregar un bot de conversación para un patrón de interacción nuevo y natural.</span><span class="sxs-lookup"><span data-stu-id="1bf39-221">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
